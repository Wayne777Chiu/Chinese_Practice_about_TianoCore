(2019/03/08)

# Nt32Pkg

Nt32Pkg 實作 [[NT32]]，是 Microsoft 視窗介面系統的 [[UEFI]] 模擬環境。 不像 [[OVMF]]， [[NT32]] 不支援平台模擬或載入一個作業系統。 NT32 主要是用來當成 UEFI 前置OS 應用程式原型和開發者訓練用。

NT32 提供開機和運行時間服務給應用程式開發來對應 UEFI 函數到 Windows APIs。在 NT32 裡開機過程服務是不能中斷的。

Nt32Pkg 平台的目標和功能是類似於 [[UnixPkg]] 和 [[EmulatorPkg]] 。 我們的長程目標是平台開發導入 [[EmulatorPkg]] 到 Microsoft Windows 並捨棄 Nt32Pkg 。

在 Windows 上使用 NT32 模擬器:
* 建置 Nt32Pkg 在 Windows 上，參考: 如何建置去使用 [Windows Systems]( Windows-systems#build)
* t
* t
 
# 原文

# Nt32Pkg

Nt32Pkg implements [[NT32]], a [[UEFI]] simulation environment for Microsoft Windows. Unlike [[OVMF]], [[NT32]] does not support platform emulation or loading an operating system. NT32 is primarily used for UEFI pre-OS application prototyping and developer training.

NT32 will provide boot and runtime services for application development, mapping UEFI functions to Windows APIs. Boot services cannot be terminated in NT32.

The goals and features of the Nt32Pkg platform are similar to [[UnixPkg]] and [[EmulatorPkg]]. Our long term goal is to port [[EmulatorPkg]] to Microsoft Windows and retire Nt32Pkg.

Using NT32 emulation with Windows:
* To build Nt32pkg in Windows see: How to build using [Windows Systems]( Windows-systems#build)
* To Run the NT32 Emulation, 
   - after building the Nt32Pkg successfully` >Build -p Nt32Pkg/Nt32Pkg.dsc`
   - at the Command prompt type: `>Build Run`
* The NT32 emulation will then display 2 UGA Windows with the UEFI Shell environment.

Source Repository: https://github.com/tianocore/edk2/tree/master/Nt32Pkg 
