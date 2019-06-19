(2019/03/08)

本頁針對 [OVMF](http://www.tianocore.org/ovmf/) 提供一個高階的啟動流程概論。

安全性 (SEC) 
===

-   UefiCpuPkg/ResetVector/Vtf0
    -   Ia16/ResetVectorVtf0.asm: 開始在重置向量 (resetVector)
    -   Ia16/Real16ToFlat32.asm: 切換模式: Real =&gt; 32-bit Flat
    -   Ia32/SearchForBfvBase.asm: 找到啟動韌體冊(Boot FirmwareVolume) (BFV)
    -   Ia32/SearchForSecEntry.asm: 用 BFV 找到安全性核心 (SEC Core)
    -   Ia32/Flat32ToFlat64.asm: 假如是64位元 (64-bit) 韌體前初始化 (PEI), 那麼切換模式: 32-bit Flat to 64-bit Long
-   安全性核心 (SEC Core): OvmfPkg/Sec
    -   OvmfPkg/Sec/SecMain.c: 找到韌體前初始化核心 (PEI Core)

韌體前初始化 (PEI)
===

韌體前初始化(Pre-EFI Initialization)

-   韌體前初始化核心 (PEI Core): MdeModulePkg/Core/Pei
    -   現在運行各式各樣的韌體前初始化驅動程式 (PEI drivers)
-   驅動程式執行環境初始程式載入 (DXE IPL(驅動程式執行環境核心載入器))
    -   找尋驅動程式執行環境核心 (DXE Core)
    -   假如韌體前初始化 (PEI) 是32位元(32-bit) 和 驅動程式執行環境 (DXE) 是64位元 (64-bit)，那麼切換模式: 32-bit Flat to 64-bit Long
    -   跳到驅動程式執行環境核心

驅動程式執行環境 (DXE)
===

驅動程式執行環境 (Driver Execution Environment)

-   驅動程式執行環境核心: MdeModulePkg/Core/Dxe
    -   現在運行各式各樣的 DXE/UEFI 驅動程式
    -   在所有的驅動程式執行環境 (DXE) 建構的協定都可用後，啟動裝置選擇 (BDS) 被運行

啟動裝置選擇 (BDS)
===

啟動裝置選擇 (Boot Device Selection)

-   啟動裝置選擇 (BDS): IntelFrameworkModulePkg/Universal/BdsDxe + IntelFrameworkModulePkg/Library/GenericBdsLib
    -   OvmfPkg/Library/PlatformBdsLib 在平台特定行為上引導啟動裝置選擇 (BDS)
-   啟動裝置選擇著墨要啟用的是甚麼和開啟裝置去啟用這次的啟動 (boot) 
    -   假如這 (EFI shell) 在系統韌體檔案系統裏存在的話，啟動裝置選擇能夠可以去載入 EFI 殼層 (EFI shell)


原文
===

This page provides a high-level overview of the boot process for [OVMF](http://www.tianocore.org/ovmf/).

SEC
===

-   UefiCpuPkg/ResetVector/Vtf0
    -   Ia16/ResetVectorVtf0.asm: Starts at resetVector
    -   Ia16/Real16ToFlat32.asm: Mode Switch: Real =&gt; 32-bit Flat
    -   Ia32/SearchForBfvBase.asm: Locates the Boot FirmwareVolume (BFV)
    -   Ia32/SearchForSecEntry.asm: Locates the SEC Core with BFV
    -   Ia32/Flat32ToFlat64.asm: If 64-bit PEI, then Mode Switch: 32-bit Flat to 64-bit Long
-   SEC Core: OvmfPkg/Sec
    -   OvmfPkg/Sec/SecMain.c: Finds PEI Core

PEI
===

Pre-EFI Initialization

-   PEI Core: MdeModulePkg/Core/Pei
    -   Various PEI drivers now run
-   DXE IPL (Loader for the DXE Core)
    -   Finds DXE Core
    -   If PEI is 32-bit and DXE is 64-bit, then Mode Switch: 32-bit Flat to 64-bit Long
    -   Jumps to DXE Core

DXE
===

Driver Execution Environment

-   DXE Core: MdeModulePkg/Core/Dxe
    -   Various DXE/UEFI drivers now run
    -   BDS is run after all DXE architectural protocols are available

BDS
===

Boot Device Selection

-   BDS: IntelFrameworkModulePkg/Universal/BdsDxe + IntelFrameworkModulePkg/Library/GenericBdsLib
    -   OvmfPkg/Library/PlatformBdsLib guides BDS in a platform specific manner
-   BDS figures out what to boot, and starts devices to enable the boot
    -   BDS may be able to load the EFI shell if it is present in the system firmware file system
