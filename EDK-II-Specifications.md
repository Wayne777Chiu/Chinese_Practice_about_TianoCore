(2019/03/08)

# **EDK II 規範**
本頁包含透過 [Gitbook](https://legacy.gitbook.com/)公開發表的 EDK II 規範的發行版本。 <br>
* 最新的 EDK II 規範草稿版本能在此頁 [[EDK II 規範草稿版|EDK II Draft Specification]] 找到。
* EDK II 規範的之前版本能於此頁 [[EDK II 規範存檔|EDK II Speciificaitons Archived]] 找到。

為了基本的認知建立和了解如何使用 EDK II 規範裡的檔案 [.DEC](#dec),[.DSC](#dsc) 和 [.INF](#inf) 的範例，可參考 wiki 頁面 [[建置描述檔|Build Description Files]] 。<Br>

_EDK II 樣板規範 (Template Specification)_ 是一個使用來給一個新文件當成樣板的範例文件。關於如何協助 TianoCore 文件的完整內容，請看 [這裡](https://github.com/tianocore-docs/edk2-TemplateSpecification/wiki) 的資訊

**_每種規範的描述詳列於下_**

| EDK II 規範 | 校訂版本 | 日期 | 下載|
| ---------------------| --------- | ---- |---------------------------------------------|
|[建置](#建置)|v1.28   | April 2018   | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-build-specification/content/v/release/1.28/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-build-specification/v/release/1.28), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-build-specification/v/release/1.28), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-build-specification/v/release/1.28), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-build-specification), [Github ](https://github.com/tianocore-docs/edk2-BuildSpecification/tree/release/1.28) |
|[DEC](#dec)     |v1.27   | April 2018 |[HTML   ](https://edk2-docs.gitbooks.io/edk-ii-dec-specification/content/v/release/1.27/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-dec-specification/v/release/1.27), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-dec-specification/v/release/1.27), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-dec-specification/v/release/1.27), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-dec-specification), [Github ](https://github.com/tianocore-docs/edk2-DecSpecification/tree/release/1.27)|
|[DSC](#dsc)     |v1.28   | April 2018  | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-dsc-specification/content/v/release/1.28/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-dsc-specification/v/release/1.28), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-dsc-specification/v/release/1.28), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-dsc-specification/v/release/1.28), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-dsc-specification/details), [Github ](https://github.com/tianocore-docs/edk2-DscSpecification/tree/release/1.28)|
|[FDF](#fdf)     |v1.28   | June 2017  | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-fdf-specification/content/v/release/1.28/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-fdf-specification/v/release/1.28), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-fdf-specification/v/release/1.28), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-fdf-specification/v/release/1.28), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-fdf-specification), [Github ](https://github.com/tianocore-docs/edk2-FdfSpecification/tree/release/1.28)|
|[IDF](#idf)     |v1.0    | April 2017 | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-idf-specification/content/v/release/1.00/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-idf-specification/v/release/1.00), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-idf-specification/v/release/1.00), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-idf-specification/v/release/1.00), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-idf-specification), [Github ](https://github.com/tianocore-docs/edk2-IdfSpecification/tree/release/1.00) |
|[INF](#inf)     |v1.27   | April 2018   | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-inf-specification/content/v/release/1.27/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-inf-specification/v/release/1.27), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-inf-specification/v/release/1.27), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-inf-specification/v/release/1.27), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-inf-specification), [Github ](https://github.com/tianocore-docs/edk2-InfSpecification/tree/release/1.27) |
|[Meta-Data](#meta-data)  | v1.20      | April 2017 | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-meta-data-expression-syntax-specification/content/v/release/1.20/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification/v/release/1.20), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification/v/release/1.20), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification/v/releas/1.20), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification), [Github ](https://github.com/tianocore-docs/edk2-MetaDataExpressionSyntaxSpecification/tree/release/1.20) |
|[PCD](#pcd)     | v0.56  | April 2017 | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-pcd-specification/content/v/release/0.56/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-pcd-specification/v/release/0.56), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-pcd-specification/v/release/0.56), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-pcd-specification/v/release/0.56), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-pcd-specification), [Github ](https://github.com/tianocore-docs/edk2-PcdSpecification/tree/release/0.56) |
|[UNI](#uni)     | v1.4   | May 2017   | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-uni-specification/content/v/release/1.40/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-uni-specification/v/release/1.40), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-uni-specification/v/release/1.40), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-uni-specification/v/release/1.40), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-uni-specification), [Github ](https://github.com/tianocore-docs/edk2-UniSpecification/tree/release/1.40) |
|[VFR](#vfr)     | v1.92  | April 2018 |[HTML   ](https://edk2-docs.gitbooks.io/edk-ii-vfr-specification/content/v/release/1.92/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-vfr-specification/v/release/1.92), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-vfr-specification/v/release/1.92), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-vfr-specification/v/release/1.92), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-vfr-specification), [Github ](https://github.com/tianocore-docs/edk2-VfrSpecification/tree/release/1.92) |
| [C 編碼標準](#c-編碼標準) | v 2.2 | June 2017 | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-c-coding-standards-specification/content/v/release/2.20/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-c-coding-standards-specification/v/release/2.20), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-c-coding-standards-specification/v/release/2.20), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-c-coding-standards-specification/v/release/2.20), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-c-coding-standards-specification), [Github ](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/tree/release/2.20)|







---

## 建置 
建置規範 -\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-build-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-build-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-build-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-build-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-build-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-BuildSpecification)
\] - 這文件描述 EDK II 建置架構。 規範被設計來支援新的建置需求給建置 EDK II 模組和 EDK 元件在 EDK II 建置基礎架構下和產生二元韌體映像檔和統一可延伸韌體介面 (UEFI) 應用程式。

## DEC
宣告檔格式-\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-dec-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-dec-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-dec-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-dec-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-dec-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-DecSpecification)
\] - 該文件描述 EDK II 宣告檔 (DEC) 格式。 這格式被設計來支援建置套件和 EDK II 模組的布局，以及使用 EDK II 建置基礎架構下給建置平台和模組。 EDK II 宣告檔可能在遵循 UEFI 平台初始化發行套件規範下的發行版的安裝中被創建出來。他們也可以被手動創建。 EDK II 基礎架構支援產生 UEFI 2.5 和 PI 1.4 (Unified EFI, Inc.) 相容的二元映像檔。

## DSC
平台組態描述檔格式 -\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-dsc-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-dsc-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-dsc-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-dsc-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-dsc-specification/details),
[GitHub ](https://github.com/tianocore-docs/edk2-DscSpecification)
\] - 該文件描述 EDK II 平台組態描述檔 (DSC) 格式。 EDK 建置工具 (Build Tools)被涵蓋成 EDK II 相容性套件的一部分。為了要使用 EDK II 模組或 EDK II 建置工具，一個 EDK II DSC 和 FDF 檔必須使用。 EDK II 使用 INI 風格文本基底的檔案去描述元件，平台和韌體冊 (Firmware Volumes)。 雖然相似 EDK DSC 檔，這 EDK II 建置格式是不同的，且新的套裝軟體已經被提供去處理 (process) 這些檔案。 EDK II 建置基礎結構支援實現 Unified EFI (UEFI) 2.5 和 平台基礎結構 (PI) 1.4 規範下的二元映像檔創建。


## FDF
刷錄描述檔格式 - \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-fdf-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-fdf-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-fdf-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-fdf-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-fdf-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-FdfSpecification)
\] - 這文件描述 EDK II 刷錄描述檔格式。這格式被設計用來支援在 EDK 和 EDK II 建置基礎架構裡建置 EDK 和 EDK II 模組的新的建置需求。 EDK II 建置基礎架構支援產生目前 Unified EFI, Inc. (UEFI 2.5 和 PI 1.4) 相容的二元映像檔。這 FDF 檔被使用來描述二進制映像檔布局的內容。在檔案裡的二進制映像檔描述可能是任何組合- 開機映像檔，膠囊映像檔或 PCI 選擇 ROMs。

## IDF
映像定義檔 (IDF) 格式規範 -  \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-idf-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-idf-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-idf-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-idf-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-idf-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-IdfSpecification)
\] -
這文件描述檔案格式給映像描述檔使用來創造 在統一延伸韌體介面規範，版本 2.1 裡被介紹的 HII 映像檔套件。 

## INF
資訊檔格式 - \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-inf-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-inf-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-inf-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-inf-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-inf-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-InfSpecification)
\] - 這個文件描述 EDK II 建置資訊 (INF) 檔案格式。這個格式支援在 EDK II 建置基礎架構下建置 EDK 元件和 EDK II 模組的新建置需求。  EDK II 建置基礎結構支援實現 Unified EFI (UEFI) 2.5 和 平台基礎結構 (PI) 1.4 規範下的二元映像檔創建。

## Meta-Data
後設資料表達式語法規範 -\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-MetaDataExpressionSyntaxSpecification)
\] - 這文件描述表達式陳述的語法給 EDK II 後設資料檔在資料欄位 (data field)，功能旗標表達式和狀態指示陳述句上。

## PCD
EDK II 平台配置資料庫 (PCD) 規範 -\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-pcd-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-pcd-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-pcd-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-pcd-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-pcd-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-PcdSpecification)
\] - 這文件討論讓其變得更容易去編碼在可移植的矽模組上和更容易去移植 (port) 框架從平台到平台間的機制和組態條目。


## UNI
單一碼格式檔案規範 -  \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-uni-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-uni-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-uni-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-uni-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-uni-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-UniSpecification)
\] - 這文件描述多字串建置資訊 (UNI) 檔格式。詳細內容參見文件內校訂版本歷史。

## VFR
虛擬表單呈現規範 -\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-vfr-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-vfr-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-vfr-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-vfr-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-vfr-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-VfrSpecification)
\] - 為了簡化內部表單展現的設計，一個高階虛擬表單展現語言在這文件描述。使用這個語言語法，編譯器能被設計去抓取傳統文本檔案包含 VFR 當輸入，和輸出 IFR 給使用者的程式來使用。 有各式各樣的方法去定義 VFR 語言。


## C 編碼標準
EDK II C 編碼標準規範 - \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-c-coding-standards-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-c-coding-standards-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-c-coding-standards-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-c-coding-standards-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-c-coding-standards-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification)
\] - EDK II C 編碼標準規範建立一個規矩叢，不是打算用來限制而是當成實行原理用來:
  * 建立單一性風格。
  * 設立最小資訊內容的需求。
  * 允許所有程式設計師更容易理解原始碼。
  * 藉著建立單一慣例加強支援任務。
  * 利用源碼裡嵌入設計文件來簡化文件工作。
  * 提供精準的源碼文件和單一風格減輕客戶和新進員工學習曲線。
 
  這些規則適用所有的開發源碼。

---

* **_EDK II 樣板規範_** \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-template-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-template-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-template-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-template-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-template-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-TemplateSpecification)
\] 這文件是一個樣板能被複製去開始(創造)一個新的 Tianocore Gitbook 文件。它也提供了可在 Tianocore 規範裡找到的一般性風格和格式的範例。
 
# 原文
# **EDK II Specifications**
This page contains the released versions of the EDK II Specifications published using [Gitbook](https://legacy.gitbook.com/).<br>
* The latest draft versions of the EDK II Specification can be found on the [[EDK II Draft Specification]] page.
* The previous versions of the EDK II Specifications can be found on the [[EDK II Specifications Archived]] page.<Br>

For an understanding of the basic setup and to see examples of how to use the EDK II Specification files [.DEC](#dec),[.DSC](#dsc) and [.INF](#inf), see the wiki page [[Build Description Files]].<Br>

The _EDK II Template Specification_ is an example document that may be used as a template 
for a new document.  For complete details on how to contribute to TianoCore documents, please
see the information [here](https://github.com/tianocore-docs/edk2-TemplateSpecification/wiki).

**_Descriptions for each specification is listed below._**

| EDK II Specification | Revision  | Date | Download |
| ---------------------| --------- | ---- |---------------------------------------------|
|[Build](#build) |v1.28   | April 2018   | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-build-specification/content/v/release/1.28/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-build-specification/v/release/1.28), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-build-specification/v/release/1.28), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-build-specification/v/release/1.28), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-build-specification), [Github ](https://github.com/tianocore-docs/edk2-BuildSpecification/tree/release/1.28) |
|[DEC](#dec)     |v1.27   | April 2018 |[HTML   ](https://edk2-docs.gitbooks.io/edk-ii-dec-specification/content/v/release/1.27/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-dec-specification/v/release/1.27), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-dec-specification/v/release/1.27), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-dec-specification/v/release/1.27), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-dec-specification), [Github ](https://github.com/tianocore-docs/edk2-DecSpecification/tree/release/1.27)|
|[DSC](#dsc)     |v1.28   | April 2018  | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-dsc-specification/content/v/release/1.28/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-dsc-specification/v/release/1.28), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-dsc-specification/v/release/1.28), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-dsc-specification/v/release/1.28), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-dsc-specification/details), [Github ](https://github.com/tianocore-docs/edk2-DscSpecification/tree/release/1.28)|
|[FDF](#fdf)     |v1.28   | June 2017  | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-fdf-specification/content/v/release/1.28/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-fdf-specification/v/release/1.28), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-fdf-specification/v/release/1.28), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-fdf-specification/v/release/1.28), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-fdf-specification), [Github ](https://github.com/tianocore-docs/edk2-FdfSpecification/tree/release/1.28)|
|[IDF](#idf)     |v1.0    | April 2017 | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-idf-specification/content/v/release/1.00/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-idf-specification/v/release/1.00), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-idf-specification/v/release/1.00), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-idf-specification/v/release/1.00), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-idf-specification), [Github ](https://github.com/tianocore-docs/edk2-IdfSpecification/tree/release/1.00) |
|[INF](#inf)     |v1.27   | April 2018   | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-inf-specification/content/v/release/1.27/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-inf-specification/v/release/1.27), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-inf-specification/v/release/1.27), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-inf-specification/v/release/1.27), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-inf-specification), [Github ](https://github.com/tianocore-docs/edk2-InfSpecification/tree/release/1.27) |
|[Meta-Data](#meta-data)  | v1.20      | April 2017 | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-meta-data-expression-syntax-specification/content/v/release/1.20/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification/v/release/1.20), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification/v/release/1.20), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification/v/releas/1.20), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification), [Github ](https://github.com/tianocore-docs/edk2-MetaDataExpressionSyntaxSpecification/tree/release/1.20) |
|[PCD](#pcd)     | v0.56  | April 2017 | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-pcd-specification/content/v/release/0.56/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-pcd-specification/v/release/0.56), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-pcd-specification/v/release/0.56), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-pcd-specification/v/release/0.56), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-pcd-specification), [Github ](https://github.com/tianocore-docs/edk2-PcdSpecification/tree/release/0.56) |
|[UNI](#uni)     | v1.4   | May 2017   | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-uni-specification/content/v/release/1.40/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-uni-specification/v/release/1.40), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-uni-specification/v/release/1.40), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-uni-specification/v/release/1.40), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-uni-specification), [Github ](https://github.com/tianocore-docs/edk2-UniSpecification/tree/release/1.40) |
|[VFR](#vfr)     | v1.92  | April 2018 |[HTML   ](https://edk2-docs.gitbooks.io/edk-ii-vfr-specification/content/v/release/1.92/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-vfr-specification/v/release/1.92), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-vfr-specification/v/release/1.92), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-vfr-specification/v/release/1.92), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-vfr-specification), [Github ](https://github.com/tianocore-docs/edk2-VfrSpecification/tree/release/1.92) |
| [C Coding Standards](#c-coding-standards) | v 2.2 | June 2017 | [HTML   ](https://edk2-docs.gitbooks.io/edk-ii-c-coding-standards-specification/content/v/release/2.20/), [PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-c-coding-standards-specification/v/release/2.20), [Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-c-coding-standards-specification/v/release/2.20), [ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-c-coding-standards-specification/v/release/2.20), [Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-c-coding-standards-specification), [Github ](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification/tree/release/2.20)|







---

## Build 
Build Specification -\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-build-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-build-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-build-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-build-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-build-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-BuildSpecification)
\] - This document describes the EDK II Build Architecture. This specification was designed to support new build requirements for building EDK II modules and EDK components within the EDK II build infrastructure as well as to generate binary firmware images and Unified Extensible Firmware Image (UEFI) applications.

## DEC
Declaration file format-\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-dec-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-dec-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-dec-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-dec-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-dec-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-DecSpecification)
\] - This document describes the EDK II Declaration (DEC) file format. This format was designed to support building packaging and distribution of EDK II modules, as well as for building platforms and modules using the EDK II build infrastructure. EDK II declaration files may be created during installation of a distribution that follows the UEFI Platform Initialization Distribution Package Specification. They may also be created manually. The EDK II Build Infrastructure supports generation of UEFI 2.5 and PI 1.4 (Unified EFI, Inc.) compliant binary images.

## DSC
Platform Description file format -\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-dsc-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-dsc-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-dsc-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-dsc-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-dsc-specification/details),
[GitHub ](https://github.com/tianocore-docs/edk2-DscSpecification)
\] -This document describes the EDK II Platform Description file (DSC) format. The EDK Build Tools are included as part of the EDK II compatibility package. In order to use EDK II Modules or the EDK II Build Tools, an EDK II DSC and FDF file must be used. EDK II tools use INI style text based files to describe components, platforms and firmware volumes. While similar to EDK DSC files, the EDK II DSC file format is different, and new utilities have been provided to process these files. The EDK II Build Infrastructure supports creation of binary images that comply with Unified EFI (UEFI) 2.5 and UEFI Platform Infrastructure (PI) 1.4 specifications.


## FDF
Flash Description file format - \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-fdf-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-fdf-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-fdf-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-fdf-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-fdf-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-FdfSpecification)
\] - This document describes the EDK II Flash Description (FDF) file format. This format was designed to support new build requirements of building EDK and EDK II modules within the EDK II build infrastructure. The EDK II Build Infrastructure supports generation of current Unified EFI, Inc. (UEFI 2.5 and PI 1.4) compliant binary images. The FDF file is used to describe the content and layout of binary images. Binary images described in this file may be any combination of boot images, capsule images or PCI Options ROMs.

## IDF
Image Definition IDF File Format Specification -  \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-idf-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-idf-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-idf-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-idf-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-idf-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-IdfSpecification)
\] -
This document describes file format for Image Description files that are used to create HII Image Packages introduced in the Unified Extensible Firmware Interface Specification, Version 2.1.

## INF
information file format - \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-inf-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-inf-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-inf-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-inf-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-inf-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-InfSpecification)
\] - This document describes the EDK II build information (INF) file format. This format supports the new build requirements of build EDK components and EDK II modules within the EDK II build infrastructure. The EDK II Build Infrastructure supports creation of binary images that comply with Unified EFI (UEFI) 2.5 and UEFI Platform Infrastructure (PI) 1.4 specifications.

## Meta-Data
Meta-Data Expression Syntax Specification -\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-meta-data-expression-syntax-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-MetaDataExpressionSyntaxSpecification)
\] - This document describes the syntax of expression statements for EDK II Meta-data files used in data fields, feature flag expressions and conditional directive statements.

## PCD
EDK II PCD Specification -\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-pcd-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-pcd-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-pcd-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-pcd-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-pcd-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-PcdSpecification)
\] - This document discusses the mechanisms and configuration entries required to make it easy to write portable silicon modules and to port the Framework from platform to platform.


## UNI
Unicode Format File Specification -  \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-uni-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-uni-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-uni-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-uni-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-uni-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-UniSpecification)
\] - This document describes the Multi-String build information (UNI) file format . See details in the Revision History in the document for more details.

## VFR
Visual Form Representation Specification -\[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-vfr-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-vfr-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-vfr-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-vfr-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-vfr-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-VfrSpecification)
\] - To simplify the creation of Internal Forms Representation (IFR), a high-level Visual Forms Representation (VFR) language is described in this document. Using this language syntax, a compiler can be designed to take an ordinary text file containing VFR as an input, and output IFR for use in a user’s program. There are various methods to define the VFR language.


## C Coding Standards
EDK II C Coding Standards Specification - \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-c-coding-standards-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-c-coding-standards-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-c-coding-standards-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-c-coding-standards-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-c-coding-standards-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-CCodingStandardsSpecification)
\] - The EDK II C Coding Standards Specification establishes a set of rules intended not as
a constraint, but as an enabling philosophy which will:
  * Establish uniformity of style.
  * Set minimum information content requirements.
  * Allow all programmers to easily understand the code.
  * Facilitate support tasks by establishing uniform conventions.
  * Ease documentation efforts by embedding the design documentation in the code.
  * Reduce customer and new employee learning curves by providing accurate code documentation and uniform style.

  These rules apply to all code developed.

---

* **_EDK II Template Specification_** \[
[HTML   ](https://www.gitbook.com/read/book/edk2-docs/edk-ii-template-specification),
[PDF    ](https://www.gitbook.com/download/pdf/book/edk2-docs/edk-ii-template-specification),
[Mobi   ](https://www.gitbook.com/download/mobi/book/edk2-docs/edk-ii-template-specification),
[ePub   ](https://www.gitbook.com/download/epub/book/edk2-docs/edk-ii-template-specification),
[Gitbook](https://www.gitbook.com/book/edk2-docs/edk-ii-template-specification),
[GitHub ](https://github.com/tianocore-docs/edk2-TemplateSpecification)
\] This document is a template that can be copied to start a new Tianocore Gitbook document. It also provides examples for styles and formats commonly found in Tianocore specifications.

