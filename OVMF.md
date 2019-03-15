(2019/03/08)

OVMF(The Open Virtual Machine Firmware) 是一個基於 [[EDK II]]的專題，能夠使 [[UEFI]] 支援虛擬機器。 OVMF 包含簡單的 UEFI 韌體給 [QEMU](http://www.qemu-project.org/) and [KVM](http://www.linux-kvm.org/) 使用。

授權: [[BSD|BSD License]]

更多資訊: [[OVMF FAQ]], [[如何建置OVMF|How to build OVMF]], [[Boot 概論|OVMF-Boot Overview]], [[edk2-devel]]

源碼 repository: https://github.com/tianocore/edk2/tree/master/OvmfPkg

更多資訊

* http://www.linux-kvm.org/page/OVMF
* http://wiki.xen.org/wiki/OVMF
* Gerd Hoffmann’s OVMF builds: https://www.kraxel.org/repos/
  * 這些映像檔是自動化建置並追蹤最新OVMF源碼在 EDK II 樹。
  * 其中一些可建置包含一個 [seabios](https://www.seabios.org/SeaBIOS) CSM (SeaBIOS Compatibility Support Module)，且能開機成非 UEFI "legacy" 作業系統 (Note: seabios 屬於 GPLv3 授權。)
  * 假如你的作業系統無法使用 RPM repositories, 那麼你需要手動下載和解壓縮 RPM 檔案在 jenkins/edk2。

# 原文

OVMF is an [[EDK II]] based project to enable [[UEFI]] support for Virtual Machines. OVMF contains sample UEFI firmware for [QEMU](http://www.qemu-project.org/) and [KVM](http://www.linux-kvm.org/).

License: [[BSD|BSD License]]

More information: [[OVMF FAQ]], [[How to build OVMF]], [[Boot Overview|OVMF-Boot Overview]], [[edk2-devel]]

Source repository: https://github.com/tianocore/edk2/tree/master/OvmfPkg

Additional Information

* http://www.linux-kvm.org/page/OVMF
* http://wiki.xen.org/wiki/OVMF
* Gerd Hoffmann’s OVMF builds: https://www.kraxel.org/repos/
  * These images are automatically built and track the latest OVMF code in the EDK II tree.
  * Some of these builds include a seabios CSM and can boot non-UEFI “legacy” operating systems. (Note: seabios is GPLv3 licensed.)
  * If your OS doesn’t work with RPM repositories, then you can manually download and decompress the RPM files under jenkins/edk2