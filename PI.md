(2019/03/08)
## 平台初始化 (PI)

UEFI 平台初始化(PI) 描述開機執行面到周圍[[UEFI]]支援的協定和服務等。 PI從遵循EFI規範的原始Intel®平台創新韌體發展而來。當UEFI主要針對韌體與作業系統之間的介面層，PI則專注於低階韌體元件介面層之間。

由UEFI論壇的[平台初始化工作群組(PLATFORM INITIALIZATION WORK GROUP)](http://uefi.org/workinggroups)(PIWG)管理規範開發。

> " PEI和DXE規範由Intel與相關規範編制者以工作群組多數決來制定。 這些規範實現方式是用來當作初始化電腦系統的韌體以及在UEFI規範的介面層之下的實現。至於實現PEI和DXE不會需要UEFI的承認。" - http://uefi.org/workinggroups

更多資訊: [[UEFI與PI的FAQ|UEFI PI_FAQ]] | [[PI的開機流程|PI Boot Flow]] | [PI 開機階段圖](https://raw.githubusercontent.com/tianocore/tianocore.github.io/master/images/PI_Boot_Phases.JPG)

![UEFI對PI規範範圍圖](https://raw.githubusercontent.com/tianocore/tianocore.github.io/master/images/UEFI_vs__PI_Spec.jpg)

# 原文

## Platform Initialization (PI)

UEFI Platform Initialization (PI) describes the boot execution phases to encompass [[UEFI]] supported protocols and services. PI evolved from the original Intel® Platform Innovation Firmware for EFI Specification. While UEFI primarily focuses on the interface between firmware and the operating system, PI focuses on interfaces between low-level firmware components.

The [PLATFORM INITIALIZATION WORK GROUP](http://uefi.org/workinggroups) (PIWG) of the UEFI Forum manages specification development.

> "The PEI and DXE specifications authored by Intel and other related specifications as mutually agreed to by a majority of the work group. Implementations of these specifications are intended to serve as firmware for initializing a computer system and are intended to be implementations below the interface layer presented by the UEFI Specification. Implementations of PEI and DXE would not be required for UEFI compliance." - http://uefi.org/workinggroups

More information: [[UEFI & PI FAQ|UEFI PI_FAQ]] | [[PI Boot Flow]] | [PI Boot Phases](https://raw.githubusercontent.com/tianocore/tianocore.github.io/master/images/PI_Boot_Phases.JPG)

![UEFI vs PI](https://raw.githubusercontent.com/tianocore/tianocore.github.io/master/images/UEFI_vs__PI_Spec.jpg)