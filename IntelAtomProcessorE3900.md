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