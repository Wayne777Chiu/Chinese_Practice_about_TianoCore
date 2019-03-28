[[EDK II 平台 | EDK II Platforms]] | [Intel® 處理器平台](https://github.com/Wayne777Chiu/Chinese_Practice_about_TianoCore/wiki/EDK-II-Platforms#intel-processor-platforms)

***

(2019/03/08)

## MinnowBoard Max/Turbot

<img src="https://minnowboard.org/wp-content/uploads/2017/10/MBTurbot-dual-core-Top-0001-171002-1.png" width="20%" height="20%" >

對想在開放性環境開發的硬體、軟體、韌體開發者而言，MinnowBoard Max & Turbot　是低成本，可購買的參考平台。 設計規範和材料已經提供給開放社群，來鼓勵平台實驗和衍伸設計。

本專案基於 Intel® Atom™ 處理器。 技術性的詳細資料、線路和擴充板資料 (Lures) 能在此找到 http://minnowboard.org 

目前支援的板子和價格列表位於: https://minnowboard.org 之下的 "[板子](https://minnowboard.org/compare-boards)" 分頁面。

### UEFI Firmwre

文件，二進制映像檔，和原始碼建置說明 位於 http://firmware.intel.com/projects/minnowboard-max

* 二進制韌體映像檔 ("UEFI BIOS"): 32-bit 和 64-bit UEFI 建置，有偵錯版和發佈版映像檔。包含燒錄更新套件和發佈公告。
* 二進制物件模組的原始碼是不能提供，原因是Intel 矽合物(處理器與晶片組)和第三方元件的智慧產權。
* 如何整合 EDK II 原始樹 (BSD License) 和二進制物件模組去建置韌體的建制說明。 詳看最新的 **發佈公告檔(Release Note .txt)** 位於 [firmware.intel.com/projects/Minnowboard-max Firmware Releases](http://firmware.intel.com/projects/minnowboard-max#Releases:)
   * 如何用 FSP 建置
   * 如何設定記憶體參數
   * 如何啟動 fTPM 功能
* 開放源碼韌體專案可透過 TianoCore GitHub:
   * https://github.com/tianocore/edk2-platforms/tree/devel-MinnowBoardMax-UDK2017

# 原文

[[EDK II Platforms]] | [Intel® Processor Platforms](https://github.com/tianocore/tianocore.github.io/wiki/EDK-II-Platforms#intel-processor-platforms)

***

## MinnowBoard Max/Turbot

<img src="https://minnowboard.org/wp-content/uploads/2017/10/MBTurbot-dual-core-Top-0001-171002-1.png" width="20%" height="20%" >


MinnowBoard Max & Turbot are low cost, commercially available, reference platforms for hardware, software and firmware developers who wish to work within an open environment. Design specifications and materials have been provided to the open community, encouraging platform experimentation and derivative designs.

The project is based on Intel® Atom™ processors. Technical details, schematics, and information on expansion boards (Lures) can be found at http://minnowboard.org 

A list of currently supported boards and prices can be found at: https://minnowboard.org under the "[Boards](https://minnowboard.org/compare-boards)" tab

### UEFI Firmware

Documentation, binary images, and source build instructions are at http://firmware.intel.com/projects/minnowboard-max

* Binary Firmware Images ("UEFI BIOS"): 32-bit and 64-bit UEFI builds, with Debug and Release images. Includes flash update utilities and release notes.
* Binary Object Modules for which source code is not available due to the Intellectual property for both Intel silicon (microprocessor and chipset) and third party components.
* How to build Instructions for integrating the EDK II source tree (BSD license) with the Binary Object Modules to build firmware. See the latest **Release Notes .txt** file at [firmware.intel.com/projects/Minnowboard-max Firmware Releases](http://firmware.intel.com/projects/minnowboard-max#Releases:)
   * How to build with FSP
   * How to configure Memory Parameters
   * How to enable fTPM feature
* The open source firmware project is available from the TianoCore GitHub:
   * https://github.com/tianocore/edk2-platforms/tree/devel-MinnowBoardMax-UDK2017