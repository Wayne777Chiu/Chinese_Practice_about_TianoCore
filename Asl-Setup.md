(2019/03/08)
# ACPI 源碼語言 (ASL) 編譯器設定

EDK II 使用 ACPI 去描述平台配置和電源管理方法給作業系統。這些方法透過使用 ASL-需要額外的編譯系-去描述。

[ACPI 元件架構 (ACPICA) 下載](https//acpica.org/downloads)

[ASL 2.0 介紹和概觀 (白皮書 @ acpica.org)](https://acpica.org/sites/acpica/files/ASL2.0Overview.pdf)

## Windows
透過下載 [Windows Binary Tools](https://acpica.org/downloads/binary-tools)發行套裝軟體來下載安裝 iasl 編譯器。 請檢查是否你的專愛需要一個特定 ACPICA 工具版本。 放置解壓縮後的內容 ("iasl.exe")到 "C:\ASL" 目錄裡在你的硬碟裡 (假如不存在(該目錄)，創造一個 "C:\ASL" 目錄)。

## Linux 
安裝 [iasl](http://packages.ubuntu.com/search?keywords=iasl) 或 [acpica-tools](http://packages.ubuntu.com/yakkety/acpica-tools)套件，根據你的Linux 發行版。 Debian/Ubuntu 的例子:

    bash$ sudo apt-get install iasl

# 原文
# ACPI Source Language (ASL) Compiler Setup

EDK II uses ACPI to describe platform configuration and power management methods to the operating system. These methods are described using ASL, which requires an additional compiler.

[ACPI Component Architecture (ACPICA) Downloads](https://acpica.org/downloads)

[ASL 2.0 Introduction and Overview (whitepaper @ acpica.org)](https://acpica.org/sites/acpica/files/ASL2.0Overview.pdf)

## Windows
Download and install the iasl compiler by downloading the [Windows Binary Tools](https://acpica.org/downloads/binary-tools) release package. Please check to see if your project requires a specific ACPICA tools version. Place the unzipped content ("iasl.exe") into the directory "C:\ASL" on your local hard drive (create the folder "C:\ASL" if it does not exist).

## Linux

Install the [iasl](http://packages.ubuntu.com/search?keywords=iasl) or [acpica-tools](http://packages.ubuntu.com/yakkety/acpica-tools) package, depending on your Linux distribution. Example for Debian/Ubuntu:

    bash$ sudo apt-get install iasl
