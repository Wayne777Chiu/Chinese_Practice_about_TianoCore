[[EDK II 平台 | EDK II Platforms]] | [Intel® 處理器平台](https://github.com/Wayne777Chiu/Chinese_Practice_about_TianoCore/wiki/EDK-II-Platforms#intel-processor-platforms)

***

(2019/03/08)

# UEFI Firmware Project for Intel Atom® 處理器 E3900 Series Processor 平台 (Leaf Hill, Up Squared & MinnowBoard 3 Module)

該專案是基於 TianoCore EDK II 源碼基底的開放源碼 UEFI 韌體，給下面基於在 Intel  Atom® Processor E3900 系列處理器的平台。

* Leaf Hill 顧客參照板(Customer Reference Board)(CRB)
* Up Squared by UP-BOARD (商業化型的創客板, 請看以下的"支援平台") 
* MinnowBoard 3 Module (Pre-production Board, ship date TBD)

開發者們可以下載預先建置的韌體映像檔，工具套件，二進制物件模組，和專案發佈公告。 這開放源碼韌體專案是可用的從TianoCore GitHub:

*  https://github.com/tianocore/edk2-platforms/tree/devel-IntelAtomProcessorE3900
*  https://firmware.intel.com/projects/IntelAtomProcessorE3900

## 回報韌體問題

請使用以下的欄位內容來回報任何有關韌體問題於 [TianoCore Bugzilla](https://bugzilla.tianocore.org/)

* Product: EDK2 Platforms
* Component: Minnowboard 3

對於TianoCore Bugzilla 的更多資訊請看 [[回報問題 | Reporting Issues]]

## 支援平台

### Leaf Hill CRB

Leaf Hill 參考自 Intel 顧客參照板 (Customer Reference Board)(CRB) ，使用 [Intel Atom® 處理器系列](https://www.intel.com/content/www/us/en/embedded/products/apollo-lake/overview.html) (前身 Apollo Lake) 。

### Up Squared by UP-BOARD

UP Squared board 的支援被介紹在發佈板 0.71。 預先建置的映像檔和建置說可被找到於 [firmware.intel.com](https://firmware.intel.com/projects/IntelAtomProcessorE3900) 。
請參考 [發佈公告](https://firmware.intel.com/projects/IntelAtomProcessorE3900) 獲取平台上的功能與已知問題的資訊。

_**NOTE:** 由專案提供給 UP Squared 創客板韌體並不是基於官方製造商的韌體。 本專案是為了測試和並不受開發商 (Aaeon) 支援。 在UP Squared 燒錄韌體將使開發商的保修失效。 感謝 Aaeon 的合作與提供平台移植資訊。_

更多資訊:

* [在 UP Squared 燒錄 BIOS](https://wiki.up-community.org/BIOS_chip_flashing_on_UP_Squared) - 使用 SPI 燒錄器去附加新的韌體映像檔的資訊 (工廠映像或客戶映像)
* 產品資訊: http://www.up-board.org/upsquared/ & http://www.up-china.net/

### MinnowBoard 3 模組

MinnowBoard 3 模組是延續自 [[MinnowBoard Max|MinnowBoardMax]] & MinnowBoard Turbot 平台。 MinnowBoard 提供低成本和可商業化的基於Intel 架構的開源硬體給硬體、軟體和韌體開發者。 硬體可用性是待確定。 

MinnowBoard 是一個鼓勵平台測試和衍生設計的的開源硬體倡議者。 專案支持 [開源硬體協會](http://www.oshwa.org/)原則藉由給社群可行的公開設計，因此"所有人能基於此設計來學習、驗證、發送、製造和販賣設計或硬體。"

MinnowBoard 3 模組是基於  Intel Atom® 處理器 E3900 系列平台，初始化  Intel® 韌體支援套裝 (Firmware Support Package)(Intel® FSP) 和 開源 UEFI 從 TianoCore EDK II 專案而來。 

## 公告: 之前的 MinnowBoard 3 源碼基底

Intel Atom® 處理器 E3900 系列平台最初是由 [[MinnowBoard 3]] 源碼基底所支持。 在發行到 0.70 版， 這個源碼基底被更新到去使用 [[UDK2018]] 和移到一個有更廣泛平台支援的新分支。 

# 原文

# UEFI Firmware Project for Intel Atom® Processor E3900 Series Processor Platforms (Leaf Hill, Up Squared & MinnowBoard 3 Module)

This project is open source UEFI firmware, based on the TianoCore EDK II codebase, for the following platforms based on the Intel Atom® Processor E3900 Series processor (formerly Apollo Lake).

* Leaf Hill Customer Reference Board (CRB)
* Up Squared by UP-BOARD (commercially available maker board, see "Supported Platforms" below) 
* MinnowBoard 3 Module (Pre-production Board, ship date TBD)

Developers can download pre-built UEFI firmware images, utilities, binary object modules, and project release notes. The open source firmware project is available from the TianoCore GitHub:

*  https://github.com/tianocore/edk2-platforms/tree/devel-IntelAtomProcessorE3900
*  https://firmware.intel.com/projects/IntelAtomProcessorE3900

## Reporting Firmware Issues

Please report any firmware issues in [TianoCore Bugzilla](https://bugzilla.tianocore.org/) using the following field values:

* Product: EDK2 Platforms
* Component: Minnowboard 3

See [[Reporting Issues]] for more information on TianoCore Bugzilla. 

## Supported Platforms

### Leaf Hill CRB

Leaf Hill refers to an Intel Customer Reference Board (CRB) using the [Intel Atom® Processor E3900 Series](https://www.intel.com/content/www/us/en/embedded/products/apollo-lake/overview.html) (formerly Apollo Lake). 

### Up Squared by UP-BOARD

Support for the UP Squared board was introduced in Release 0.71. Pre-built images and build instructions are available on [firmware.intel.com](https://firmware.intel.com/projects/IntelAtomProcessorE3900). Please refer to the [release notes](https://firmware.intel.com/projects/IntelAtomProcessorE3900) for information on platform features and known issues.

_**NOTE:** The firmware provided by this project for the UP Squared maker board is not based on the official manufacturer's firmware. This project is for experimentation and is not supported by the manufacturer (Aaeon). Flashing this firmware on the UP Squared will void the manufacturer's warranty. Thanks to Aaeon for their cooperation and providing platform porting information._

More Info:
* [BIOS chip flashing on UP Squared](https://wiki.up-community.org/BIOS_chip_flashing_on_UP_Squared) - Information for using a SPI programmer to apply a new firmware image (factory image or custom image)
* Product Info: http://www.up-board.org/upsquared/ & http://www.up-china.net/

### MinnowBoard 3 Module

MinnowBoard 3 Module is the follow-on to the [[MinnowBoard Max|MinnowBoardMax]] & MinnowBoard Turbot platforms. MinnowBoard platforms offer low cost & commercially available open hardware based on Intel Architecture for hardware, software and firmware developers. Hardware availability is TBD.

MinnowBoard is an open source hardware enabler, encouraging platform experimentation and derivative designs. The project supports [Open Source Hardware Association](http://www.oshwa.org/) principles by making designs publicly available for the community so “anyone can study, modify, distribute, make, and sell the design or hardware based on that design.”

MinnowBoard 3 Module is based on the Intel Atom® processor E3900 Series platform, utilizing the Intel® Firmware Support Package (Intel® FSP) and open source UEFI from the TianoCore EDK II project. 

## Note: Previous Codebase for MinnowBoard 3

Intel Atom® Processor E3900 Series Processor Platforms were originally supported by the [[MinnowBoard 3]] codebase. At release 0.70, this codebase was updated to use [[UDK2018]] and moved to a new branch with broader platform support.