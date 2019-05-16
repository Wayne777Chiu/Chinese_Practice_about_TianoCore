(2019/03/08)
 
## EDK II 平台

注意: 新的平台正被開發在 [edk2-platforms](https://github.com/tianocore/edk2-platforms) 倉儲。一些舊的平台仍放置在主 [edk2](https://github.com/tianocore/edk2) 倉儲。

### 虛擬/模擬 平台

* [[OVMF]] - UEFI 韌體支援 [QEMU](https://www.qemu.org/) 開源式機器模擬(虛擬)器.
* [[Nt32Pkg]] - 啟用 UEFI 應用程式開發在 Microsoft* Windows 環境。
* [[EmulatorPkg]] - 啟動 UEFI 模擬在一個 OS 環境裡。
* [[ArmVirtPkg]] - UEFI 模擬 ARM 處理器。

### Intel® 處理器平台

* [[Intel Atom® 處理器 E3900 系列|IntelAtomProcessorE3900]] - 使用 [Intel Atom® 處理器 E3900 系列](https://www.intel.com/content/www/us/en/embedded/products/apollo-lake/overview.html) (前身 Apollo Lake) 的專用平台. 包括 the Leaf Hill CRB, Up Squared, and MinnowBoard 3 Module.
* [[MinnowBoard Max/Turbot|MinnowBoardMax]] - 開源 UEFI 韌體的開放硬體平台, 基於 the Intel® Atom™ E3800 系列處理器。
* [[專案 Olympus (Purley MinPlatform)|Purley MinPlatform]] - EDK II 平台韌體 給 開放伺服器計畫(OCP) [Intel XSP Motherboard](http://www.opencompute.org/wiki/Server/ProjectOlympus#Project_Olympus_Server_Motherboards).
* [[Kaby Lake MinPlatform]] - EDK II 平台韌體 用於第七代 Intel® Core™ 處理器和晶片組 (前身 [Kaby Lake](https://ark.intel.com/products/codename/82879/Kaby-Lake) 平台).
* [[Intel® Galileo Gen 2|Galileo]] - Arduino* 認證,  Intel® Quark™ 處理器,建置全開放硬體。
* [UEFI 韌體 為 N系列 (N-Series) Intel® Pentium® Processor and Intel® Celeron® 處理器家族](https://firmware.intel.com/projects/braswell-uefi) (IA32 & x64)
* [[MinnowBoard]] - Intel® Atom™ E640 處理器 w/ IA32 UEFI 韌體 (棄置 deprecated)

### ARM 處理器平台

* [[Beagle Board|Beagle Board Wiki]] -  低耗電開源式單板硬體型的個人電腦，由 Texas Instruments 生產。
* [[Omap35xxPkg]] 以Texas Instruments OMAP35xx 基礎的平台提供 UEFI 支援。

# 原文
## EDK II Platforms

Note: new platforms are being developed in the [edk2-platforms](https://github.com/tianocore/edk2-platforms) repository. Some older platforms still reside in the main [edk2](https://github.com/tianocore/edk2) repository.

### Virtual/Simulated Platforms

* [[OVMF]] - UEFI firmware support for the [QEMU](https://www.qemu.org/) open source machine emulator and virtualizer.
* [[Nt32Pkg]] - enabling UEFI application development in a Microsoft* Windows environment.
* [[EmulatorPkg]] - enable UEFI emulation within an OS environment.
* [[ArmVirtPkg]] - UEFI emulation for ARM processors.

### Intel® Processor Platforms

* [[Intel Atom® Processor E3900 Series|IntelAtomProcessorE3900]] - Designed for platforms using the [Intel Atom® Processor E3900 Series](https://www.intel.com/content/www/us/en/embedded/products/apollo-lake/overview.html) (formerly Apollo Lake). Includes the Leaf Hill CRB, Up Squared, and MinnowBoard 3 Module.
* [[MinnowBoard Max/Turbot|MinnowBoardMax]] - Open hardware platform with open source UEFI firmware, based on the Intel® Atom™ E3800 Series processor.
* [[Project Olympus (Purley MinPlatform)|Purley MinPlatform]] - EDK II platform firmware for the Open Compute Project (OCP) [Intel XSP Motherboard](http://www.opencompute.org/wiki/Server/ProjectOlympus#Project_Olympus_Server_Motherboards).
* [[Kaby Lake MinPlatform]] - EDK II platform firmware on 7th Generation Intel® Core™ Processors and chipsets (formerly [Kaby Lake](https://ark.intel.com/products/codename/82879/Kaby-Lake) platforms).
* [[Intel® Galileo Gen 2|Galileo]] - Arduino* certified,  Intel® Quark™ processor, built on fully open-source hardware 
* [UEFI firmware for N-series Intel® Pentium® Processor and Intel® Celeron® Processor Families](https://firmware.intel.com/projects/braswell-uefi) (IA32 & x64)
* [[MinnowBoard]] - Intel® Atom™ E640 processor w/ IA32 UEFI firmware (deprecated)

### ARM Processor Platforms

* [[Beagle Board|Beagle Board Wiki]] -  low-power open-source hardware single-board computer produced by Texas Instruments.
* [[Omap35xxPkg]] provides UEFI support For Texas Instruments OMAP35xx based platforms.
