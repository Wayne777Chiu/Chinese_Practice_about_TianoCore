(2019/03/08)
# UEFI 開發套件組合 (UDK)
UEFI開發套件組合式一個 EDK II 一部分的穩定發行版。UDK 發行版在 Intel 架構平台上測試過，和省略無法在這些配置上驗證的元件。

## 目前發行版: [[UDK2018]] (Mar 2018)

## 過去發行版: [[UDK2017]] / [[UDK2015]] / [[UDK2014]] / [[UDK2010]] / [UDK2008](https://github.com/tianocore/edk2/tree/UDK2008)

## UDK 與 EDK II 的不同

[[EDK II]] 是開源專案由自願者參與開發。 該項目的提示是不斷更新來修復和增強。

[[UDK]] 發行版代表了一個 [[EDK II]]源碼的特定修訂版的完整驗證實現，經由Intel 架構平台上測試過。因為不是所以套件能被驗證在 Intel 平台上，一個 UDK 發行版是一個可行的 EDK II 套件的子集合。 每一個 UDK 發行板會列上相對應的 EWDK II 版本在發佈公告上。每個發行是以 ZIP 檔方式，被對映在一個 EDK II github 專案的分支上 (例如: https://github.com/tianocore/edk2/tree/UDK2017 對 [[UDK2017]])

# 原文
# UEFI Development Kit (UDK)

The UEFI Development Kit (UDK) is a stable release of portions of [[EDK II]]. UDK releases are tested against Intel architecture platforms, and omits components that cannot be validated on those configurations.

## Current Release: [[UDK2018]] (Mar 2018)

## Past Releases: [[UDK2017]] / [[UDK2015]] / [[UDK2014]] / [[UDK2010]] / [UDK2008](https://github.com/tianocore/edk2/tree/UDK2008)

## Differences Between UDK and EDK II

[[EDK II]] is the open source project for which volunteers participate in development. The tip of this project is constantly updated for fixes and enhancements.

[[UDK]] releases represent a fully validated implementation of a specific revision of [[EDK II]] source, tested against Intel Architecture platforms. A UDK release is a subset of available EDK II packages, since not all packages can be validated on Intel platforms. Each UDK release lists the corresponding EDK II version in the release notes. Each release is available as a ZIP file, and is mapped to a branch of the EDK II github project (example: https://github.com/tianocore/edk2/tree/UDK2017 for [[UDK2017]]).