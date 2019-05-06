(2019/03/08)

建置 [[OVMF]]是相當容易的一旦你已經安裝了一個小的先決條件 (pre-requisties) 後。然而,請注意假如你只是對 [運行 OVMF](How-to-run-OVMF) "wikilink") 有興趣，你不需要建置 OVMF，因為我們已經提供了預先建置好的 OVMF 二元檔。

建置先決條件 (Pre-requisites)
---------------------------

- 一個能夠建置 UEFI 映像檔的 edk2 建置樹
  - 假如你是一個 edk2 建置的新手，那麼這些 [開始](Getting-Started-with-EDK-II) 指令很有幫助。
- 一個 ASL 編譯器 被設定組態在你的 edk2 建置樹 (edk2 build tree)
  - 能使用 ISAL 編譯器 或 Microsoft ASL 編譯器
    - 對 Unix-like 作業系統而言，IASL 是唯一的選項:
      - 對較新的 Linux 發行版而言， 你應該能夠透過發行套件管理系統來安裝 iasl。 (這 [頁](Using-EDK-II-with-Native-GCC) 可能有幫助)
      - 或者，[Unix-like 系統開始指導手冊](Unix-like-systems) 也包含詳細的安裝 IASL 說明。
    - 對 Windows 而言，你能下載 IASL 編譯器的預先建置完成的版本從 <http://www.acpica.org>。
    - 對 Windows 而言，你也能下載 Microsoft ASL 編譯器的預先建置完成的版本從 <http://www.acpi.info>。

選擇 OVMF 的版本來建置
---------------------

最先，選擇你要建置的 OVMF 版本。你能選擇建置一個 IA32 處理器架構 和/或 X64 處理器架構。你應該考慮到你的工具鏈 (toolchain)能夠建置的處理器架構。依據你所選擇的，你應該修改在 Conf/target.txt 裡的 ACTIVE\_PLATFORM 和 TARGET\_ARCH。

| ACTIVE\_PLATFORM           | TARGET\_ARCH | PEI code | DXE/UEFI code |
|----------------------------|--------------|----------|---------------|
| OvmfPkg/OvmfPkgIa32.dsc    | IA32         | IA32     | IA32          |
| OvmfPkg/OvmfPkgIa32X64.dsc | IA32 X64     | IA32     | X64           |
| OvmfPkg/OvmfPkgX64.dsc     | X64          | X64      | X64           |

例如: <code>Conf/target.txt</code> 的值對應使用 GCC5 編譯器給 OVMF 去建構 X64 UEFI 映像檔:

<pre>
ACTIVE_PLATFORM       = OvmfPkg/OvmfPkgX64.dsc
TARGET_ARCH           = X64
TOOL_CHAIN_TAG        = GCC5
</pre>

一旦你已經修改好 Conf/target.txt，你就能運行建置的命令。

    bash$ build

假如成功了，你現在將有一個 OVMF.fd 檔在 Build 子目錄下。在 Build 目錄下的精準的目錄(名)將根據你的工具鏈，dsc 和處理器架構。

你能使用 OVMF.fd 到 [運行 OVMF](How-to-run-OVMF "wikilink")。

也可看看
-------

-   <https://github.com/tianocore/edk2/blob/master/OvmfPkg/README>

=原文=

Building [[OVMF]] is fairly easy once you have installed a few pre-requisites. Please note, however, that building OVMF is not required if you are only interested in [running OVMF](How-to-run-OVMF "wikilink"), since we have provided pre-built binaries of OVMF.

Build Pre-requisites
--------------------

-   A edk2 build tree capable of building UEFI images
    -   If you are new to edk2 building then these [getting started](Getting-Started-with-EDK-II) instructions may be helpful.
-   An ASL compiler configured in your edk2 build tree
    -   Either the IASL compiler or the Microsoft ASL compiler can be used
        -   For Unix-like operating systems, IASL is the only option:
            -   For newer Linux distributions, you should be able to install iasl via the distribution's package management system. (This [page](Using-EDK-II-with-Native-GCC) may help.)
            -   Or, the [Unix-like systems getting started guide](Unix-like-systems) includes details for installing IASL as well.
        -   For Windows, you can download pre-built version of IASL compiler from <http://www.acpica.org>.
        -   For Windows, you can also download a pre-built version of the Microsoft ASL compiler from <http://www.acpi.info>.

Choosing which version of OVMF to build
---------------------------------------

First decide which version of OVMF you will build. You can choose to build the IA32 processor architecture and/or the X64 processor architecture. You should take into account the processor architectures which your toolchain is capable of building. Depending upon which you select, you should modify the ACTIVE\_PLATFORM and TARGET\_ARCH in Conf/target.txt.

| ACTIVE\_PLATFORM           | TARGET\_ARCH | PEI code | DXE/UEFI code |
|----------------------------|--------------|----------|---------------|
| OvmfPkg/OvmfPkgIa32.dsc    | IA32         | IA32     | IA32          |
| OvmfPkg/OvmfPkgIa32X64.dsc | IA32 X64     | IA32     | X64           |
| OvmfPkg/OvmfPkgX64.dsc     | X64          | X64      | X64           |

Example: <code>Conf/target.txt</code> values to build x64 UEFI image for OVMF using GCC5 compiler:

<pre>
ACTIVE_PLATFORM       = OvmfPkg/OvmfPkgX64.dsc
TARGET_ARCH           = X64
TOOL_CHAIN_TAG        = GCC5
</pre>

Once you have modified Conf/target.txt, you can run the build command.

    bash$ build

If successful, you should now have a OVMF.Fd file under the Build sub-directory. The exact directory under the Build directory will depend upon the toolchain, dsc and processor architecture.

You can use OVMF.Fd to [run OVMF](How-to-run-OVMF "wikilink").

See Also
--------

-   <https://github.com/tianocore/edk2/blob/master/OvmfPkg/README>
