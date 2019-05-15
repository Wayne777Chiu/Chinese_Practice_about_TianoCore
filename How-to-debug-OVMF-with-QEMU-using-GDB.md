(2019/03/08)
# 用 QEMU 和 Linux GDB 來偵錯 使用 OvmfPkg的EDK II
這個例子將展示如何去偵錯一個使用OvmfPkg建置然後使用 QEMU 和 GDB 去偵錯 UEFI 應用程式的簡單應用程式。

### 以下將使用 UEFI_APPLICATION SampleApp.c 當成例子:
1. 新增你的 UEFI 應用程式到 OvmfPkgIa32.dsc (使用 IA32) 例子:(新增) `SampleApp/SampleApp.inf` 在OvmfPkgIa32.dsc 檔案裡的 `[Components]` 區域的最後。
2. 建置 OVMF 於 IA32 (架構): ` bash$ build -a IA32 -p OvmfPkg/OvmfPkgIa32.dsc -t GCC5` 
3. 複製 SampleApp 的輸出到 `hda-contents` 目錄如同在 [[How-to-run-OVMF|如何運行 OVMF]] 裡展示的設定 QEMU 用檔案系統一樣。這將是以下的類似目錄裡: `/home/u-mypc/src/edk2/Build/OvmfIa32/DeEBUG_GCC5/IA32`
```
    SampleApp.efi
    SampleApp.debug
    SampleApp (目錄)
```
4. 在 `run-ovmf` 目錄下開啟終端提示視窗(1)就與在 [[How-to-run-OVMF|如何運行 OVMF]] 裡展示(關於)用 ovmf.fd 檔 複製到 bios.bin 檔一樣。
5. 調用 QEMU 用以下的命令:
```
bash$ qemu-system-i386 -s -pflash bios.bin -hda fat:rw:hda-contents -net none -debugcon file:debug.log -global isa-debugcon.iobase=0x402
```
6. QEMU 將讀取和開機到一個 UEFI Shell 提示

### 在 QEMU 視窗裡
調用你的應用程式。
```
Shell> fs0:
Fs0:\> SampleApp.efi
```
在 `run-ovmf` 目錄下開啟終端提示視窗(2)和查驗 debug.log 檔
`bash$ cat debug.log`
```
5B1B31A1-9562-11D2-8E3F-00A0C969723B 6F0F028
Loading driver at 0x00006AEE000 EntryPoint=0x00006AEE756 SampleApp.efi
InstallProtocolInterface: BC62157E-3E33-4FEC-9920-2D3B36D750DF 6F0FF10

```
看這部分 `Loading driver at 0x00006AEE000` 是 UEFI 應用程式被載入的記憶體位置。
記好這個位址。
另外你可能會增加一段 DEBUG 段落給你的應用程式，就像下面(例子)獲得你的源碼的進入點。 :
```
    DEBUG ((EFI_D_INFO, "My Entry point: 0x%08x\r\n", (CHAR16*)UefiMainMySampleAPP )  );
```
那麼當你 `bash$ cat debug.log` 你也將得到進入點 (Entry Point) 在你的應用程式上。以這個例子這個進入點是 `UefiMainMySampleApp`。

```
我的進入點: 0x06AEE496
```
這是很有用的去雙重檢查你的字符(號)被修正成你的原始碼裡的正確行號。 否則，你在GDB裡所看到的原始碼可能就不是正在執行的原始碼。

### 調用 GDB
終端提示視窗(2)裡
1. 切換目錄到 `hda-contents`所在的目錄
2. 用源碼佈局視窗下(命令) `bash$ gdb --tui` 調用 GDB。 第一次(使用)在源碼視窗視窗上沒有任何顯示。
3. 用 `file` 命令讀取你的 UEFI 應用程式 SampleApp.efi。
```
(gdb) file SampleApp.efi
Reading symbols from SampleApp.efi...(no debugging symbols found)...done.
```
4. 利用`info files` 命令來檢查 .text 和 .data 的偏移量的所在。
```
(gdb) info files
Symbols from "/home/u-mypc/run-ovmf/hda-contents/SampleApp.efi".
Local exec file:
        `/home/u-mypc/run-ovmf/hda-contents/SampleApp.efi',
        file type pei-i386.
        Entry point: 0x756
        0x00000240 - 0x000028c0 is .text
        0x000028c0 - 0x00002980 is .data
        0x00002980 - 0x00002b00 is .reloc
```
5. 我們需要計算我們的位址關於 .text 和 .data 部分。 應用程式被載入在 `0x00006AEE000` 之下(載入驅動程式點 - **不是** **進入點**) 和 我們已知的 text 和 data 偏移量。
```
 text = 0x00006AEE000 + 0x00000240 = 0x06AEE240
 data = 0x00006AEE000 + 0x00000240 + 0x000028c0 = 0x06AF0B00
```
6. 卸載 .efi 檔
```
(gdb) file
No executable file now.
No symbol file now.
```
7. 使用你的應用程式輸出 .debug 檔來載入有已修正位址的字符(號)
```
(gdb) add-symbol-file SampleApp.debug 0x06AEE240 -s .data 0x06AF0B00
add symbol table from file "SampleApp.debug" at

        .text_addr = 0x6aee240
        .data_addr = 0x6af0b00
(y or n) y
Reading symbols from SampleApp.debug...done
```
8. 設定中斷點 (break point)。 在 .inf 檔，我們設立成進入點: `UefiMainMySampleApp`
```
(gdb) break UefiMainMySampleApp
Breakpoint 1 at 0x6aee496: file /home/u-uefi/src/edk2/SampleApp/SampleApp.c, line 40.
```
9. 附加 GDB 偵錯器到 QEMU:
```
(gdb) target remote localhost:1234
Remote debugging using localhost:1234
0x07df6ba4 in ?? ()
```
10. 繼續在 GDB 裡
```
(gdb) c
Continuing.
```

### 在 QEMU 視窗上再次調用你的應用程式
```
Shell> fs0:
Fs0J:\> SampleApp.efi
```

GDB 將觸及你的 UEFI 應用程式的進入點的中斷點且你能夠開始用源碼偵錯的方式偵錯。

你能設定更多的中斷點在你的源碼裡: `(gdb) break SampleApp.c:nn` : _nn_ 是你的 .c 檔的行號

你的 GDB 將看起來像這樣(記得 `B+>` 在你的源碼上的行數 #40 上的就是你的進入點)

![](https://github.com/tianocore/tianocore.github.io/blob/master/images/GDB_QEMU.JPG)

在設定一些中斷點後，使用 `(gdb) c` 去繼續執行在你的 QEMU 視窗裡直到下一個中斷點被觸及。 然後回到 GDB 視窗去下一步，檢視區域變數和繼續偵錯。

使用 `(gdb) info locals` 來檢視區域變數

# 原文
# Debugging EDK II using OvmfPkg with QEMU and Linux GDB
This example will show how to debug a simple application built with OvmfPkg then using the QEMU and GDB to debug the UEFI Application.

### The following will use a UEFI_APPLICATION SampleApp.c as an example: 
1. Add your UEFI application to the OvmfPkgIa32.dsc (using IA32 )  example: `SampleApp/SampleApp.inf`  at the end of the `[Components]` section in the OvmfPkgIa32.dsc file.
2. Build OVMF for IA32 :  ` bash$ build -a IA32 -p OvmfPkg/OvmfPkgIa32.dsc -t GCC5`
3. Copy the output of SampleApp to the `hda-contents` directory similarly as shown in [[How-to-run-OVMF]] as a file system for QEMU.  This will be in a similar directory to the following : `/home/u-mypc/src/edk2/Build/OvmfIa32/DEBUG_GCC5/IA32`
```
   SampleApp.efi
   SampleApp.debug
   SampleApp (Directory)
```
4. Open a terminal(1) prompt in the `run-ovmf` directory as shown in [[How-to-run-OVMF]] with the ovmf.fd file copied to bios.bin.
5. invoke QEMU with the following command:
```
bash$ qemu-system-i386 -s  -pflash bios.bin -hda fat:rw:hda-contents -net none -debugcon file:debug.log -global isa-debugcon.iobase=0x402 
```
6. QEMU will load and boot to  a UEFI Shell prompt


### In the QEMU Window
Invoke your application.
```
Shell> fs0:
Fs0:\> SampleApp.efi
```
Open another terminal(2) prompt in the `run-ovmf` directory and check out the debug.log file. 
`bash$ cat debug.log`
```
InstallProtocolInterface: 5B1B31A1-9562-11D2-8E3F-00A0C969723B 6F0F028
Loading driver at 0x00006AEE000 EntryPoint=0x00006AEE756 SampleApp.efi
InstallProtocolInterface: BC62157E-3E33-4FEC-9920-2D3B36D750DF 6F0FF10

```
See that `Loading driver at 0x00006AEE000`  is the memory location where your UEFI Application is loaded. 
Keep this address in mind.
Additionally you might add a DEBUG statement to your application something like the following to get the entry point of your code. :
```
 DEBUG ((EFI_D_INFO, "My Entry point: 0x%08x\r\n", (CHAR16*)UefiMainMySampleApp )  );
```
Then when you `bash$ cat debug.log` you will also get the entry point for your application. In this example the entry point is `UefiMainMySampleApp`.

```
My Entry point: 0x06AEE496 
```
This is useful to double check your symbols are fixed up to the correct line numbers in your source file. Otherwise, the code you see in GDB may not be the code that is executing.

### Invoking GDB
In the terminal(2) prompt 
1. Change to the directory where the `hda-contents` is located
2. Invoke GDB with the source layout window using `bash$ gdb --tui` . At first there will be nothing in the source window.
3. Load your UEFI Application SampleApp.efi with the `file` command.
```
(gdb) file SampleApp.efi
Reading symbols from SampleApp.efi...(no debugging symbols found)...done.
```
4. Check where GDB has for .text and .data offsets with `info files` command.
```
(gdb) info files
Symbols from "/home/u-mypc/run-ovmf/hda-contents/SampleApp.efi".
Local exec file:
        `/home/u-mypc/run-ovmf/hda-contents/SampleApp.efi',
        file type pei-i386.
        Entry point: 0x756
        0x00000240 - 0x000028c0 is .text
        0x000028c0 - 0x00002980 is .data
        0x00002980 - 0x00002b00 is .reloc
```
5. We need to calculate our addresses for .text and .data section. Application is loaded under `0x00006AEE000 ` (loading driver point -  **NOT** **Entrypoint**) and we know text and data offsets. 
```
 text = 0x00006AEE000  +  0x00000240 = 0x06AEE240
 data = 0x00006AEE000  +  0x00000240 + 0x000028c0 = 0x06AF0B00 
```
6. Unload the .efi file 
```
(gdb) file
No executable file now.
No symbol file now.
```
7. Load the symbols with the fixed up address using your applications output .debug file:
```
(gdb) add-symbol-file SampleApp.debug 0x06AEE240 -s .data 0x06AF0B00 
add symbol table from file "SampleApp.debug" at

        .text_addr = 0x6aee240
        .data_addr = 0x6af0b00
(y or n) y
Reading symbols from SampleApp.debug...done.
```
8. Set a break point.  We have our entry point in the .inf file as: `UefiMainMySampleApp`
```
(gdb) break UefiMainMySampleApp 
Breakpoint 1 at 0x6aee496: file /home/u-uefi/src/edk2/SampleApp/SampleApp.c, line 40.
```
9. Attach the GDB debugger to QEMU:
```
(gdb) target remote localhost:1234
Remote debugging using localhost:1234
0x07df6ba4 in ?? ()
``` 
10. Continue in GDB
```
(gdb) c
Continuing.
```

### In the QEMU Window Invoke your application again
```
Shell> fs0:
Fs0:\> SampleApp.efi
```

The GDB will hit your break point in your UEFI application's entry point and you can begin to debug with source code debugging.

You can set more break points in your code with : `(gdb) break SampleApp.c:nn` : where _nn_ is the line of code in your .c file

Your GDB will look similar to this ( notice the `B+>` by line #40 in the source code is the entry point)


![](https://github.com/tianocore/tianocore.github.io/blob/master/images/GDB_QEMU.JPG)

After setting a few break points use `(gdb) c` to continue executing in the QEMU window until the next break point is hit. Then return to the GDB window to step, view local variables and continue debugging.

Use `(gdb) info locals` to view local variables


