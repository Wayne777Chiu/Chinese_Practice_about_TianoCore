(2019/03/08)
## 平台初始化 (PI)

UEFI 平台初始化(PI) 描述開機執行面到周圍[[UEFI]]支援的協定和服務等。 PI從遵循EFI規範的原始Intel®平台創新韌體發展而來。當UEFI主要針對韌體與作業系統之間的介面層，PI則專注於低階韌體元件介面層之間。

UEFI論壇的[平台初始化工作群組(PLATFORM INITIALIZATION WORK GROUP)](http://uefi.org/workinggroups)(PIWG)管理規範開發。



# 原文

## Platform Initialization (PI)

UEFI Platform Initialization (PI) describes the boot execution phases to encompass [[UEFI]] supported protocols and services. PI evolved from the original Intel® Platform Innovation Firmware for EFI Specification. While UEFI primarily focuses on the interface between firmware and the operating system, PI focuses on interfaces between low-level firmware components.

The [PLATFORM INITIALIZATION WORK GROUP](http://uefi.org/workinggroups) (PIWG) of the UEFI Forum manages specification development.

> "The PEI and DXE specifications authored by Intel and other related specifications as mutually agreed to by a majority of the work group. Implementations of these specifications are intended to serve as firmware for initializing a computer system and are intended to be implementations below the interface layer presented by the UEFI Specification. Implementations of PEI and DXE would not be required for UEFI compliance." - http://uefi.org/workinggroups

More information: [[UEFI & PI FAQ|UEFI PI_FAQ]] | [[PI Boot Flow]] | [PI Boot Phases](https://raw.githubusercontent.com/tianocore/tianocore.github.io/master/images/PI_Boot_Phases.JPG)

![UEFI vs PI](https://raw.githubusercontent.com/tianocore/tianocore.github.io/master/images/UEFI_vs__PI_Spec.jpg)