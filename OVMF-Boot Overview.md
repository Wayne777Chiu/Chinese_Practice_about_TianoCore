(2019/03/08)

本頁針對 [OVMF](http://www.tianocore.org/ovmf/) 提供一個高階的啟動流程概論。

SEC
===

-   UefiCpuPkg/ResetVector/Vtf0
    -   Ia16/ResetVectorVtf0.asm: 開始在重置向量 (resetVector)
    -   Ia16/Real16ToFlat32.asm: 切換模式: Real =&gt; 32-bit Flat
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
