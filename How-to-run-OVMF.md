(2019/03/08)

如何運行 [[OVMF]] 用 QEMU 或 KVM。


先決條件 (Pre-requisites)
------------------------

為了要運行 OVMF 在 QEMU，你必須要有 QEMU 版本 0.9.1 或更新的安裝在你的系統上。

在 Debian/Ubuntu上安裝: <code>sudo apt-get qemu</code>

### 得到 OVMF.fd 的一個建置

你能 [建置 OVMF](How_to_build_OVMF "wikilink") 基於最新版的 [[EDK II]]。

預先建置的映像檔是可被找到於 https://www.kraxel.org/repos/
  * 這些映像檔是自動被建置和追蹤在 EDK II樹中的最新版的 OVMF 源碼。
  * 這些建置中的一些包含了一個 seabios CSM 和能開機於非 UEFI “legacy” 作業系統上。(注意: seabios 是 GPLv3 授權)
  * 假如你的作業系統不適用於RPM 套件庫，那麼你要手動下載和解壓縮 RPM 檔在 jenkins/edk2 之下。 

選擇正確的處理器架構
------------------



#原文

How to run [[OVMF]] with QEMU or KVM.

Pre-requisites
--------------

In order to run OVMF with QEMU, you must have QEMU version 0.9.1 or newer installed on your system.

To install on Debian/Ubuntu: <code>sudo apt-get install qemu</code>

### Get a build of OVMF.fd

You can [build OVMF](How_to_build_OVMF "wikilink") based on the latest version of [[EDK II]].

Pre-built images are available at https://www.kraxel.org/repos/
  * These images are automatically built and track the latest OVMF code in the EDK II tree.
  * Some of these builds include a seabios CSM and can boot non-UEFI “legacy” operating systems. Note: seabios is GPLv3 licensed)
  * If your OS doesn’t work with RPM repositories, then you can manually download and decompress the RPM files under jenkins/edk2

Choose the correct processor architecture
-----------------------------------------

Be sure to align the processor architecture for OVMF with the proper processor archtecture of QEMU.

For the IA32 build of OVMF, there is a little more choice, since the X64 processor is also compatible with IA32. Therefore, with the IA32 build of OVMF, you can use the following commands: qemu, qemu-system-i386 or qemu-system-x86\_64.

For the X64 build of OVMF, however, you can only use the qemu-system-x86\_64 command.

Setup a BIOS directory for OVMF QEMU
------------------------------------

To use OVMF with QEMU, we utilize the -L QEMU command line parameter. This paramter takes a directory path, and QEMU will load the bios.bin from this directory.

Create a directory, and cd to the directory
-------------------------------------------

For example:

    bash$ mkdir ~/run-ovmf
    bash$ cd ~/run-ovmf

Next, copy the OVMF.fd file into this directory, but rename OVMF.fd to bios.bin:

    bash$ cp /path/to/ovmf/OVMF.fd bios.bin

Next, create a directory to use as a hard disk image for QEMU
-------------------------------------------------------------

(QEMU can turn the contents of a directory into a disk image 'on-the-fly'):

    bash$ mkdir hda-contents

Run QEMU using OVMF
-------------------

Here is a sample command:

    bash$ qemu-system-x86_64 -L . -hda fat:hda-contents

If everything goes well, you should see a graphic logo, and the UEFI shell should start.

Note: iPXE is enabled on recent builds of QEMU, and may try to network boot if a valid network adapter is detected. To disable iPXE, add <code>-net none</code> to the command line.

Optional: Point directly to UEFI firmware in <code>edk2/Build</code> directory
------------------------------------------------------------------------------

The path to the <code>OVMF.fd</code> image can be directly provided on the command line, rather than copying to another directory. Example for debug image built using GCC5, with iPXE disabled:

<pre>
qemu-system-x86_64 -L . --bios ~/src/edk2/Build/OvmfX64/DEBUG_GCC5/FV/OVMF.fd -net none
</pre>

QEMU with -pflash
----------------
<pre>
qemu-system-x86_64 -pflash bios.bin -hda fat:hda-contents -net none
</pre>

Optional: QEMU with Read/Write Fat file system using a host directory
---------------- 
(Beware that QEMU makes the virtual FAT table once and host could get out of sync and QEMU might get confused)

<pre>
qemu-system-x86_64 -pflash bios.bin -hda fat:rw:hda-contents -net none
</pre>

Potential issues
----------------

### KVM

Although the latest versions of OVMF should now support the latest versions of KVM, there is still a chance that you might encounter issues when using KVM. If OVMF fails to boot on QEMU (with KVM), try disabling KVM.
