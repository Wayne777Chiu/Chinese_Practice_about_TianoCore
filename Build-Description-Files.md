(2019/03/08)

# 建置組態描述檔

理解組態描述檔 .DCS, .DEC, 和 .INF的基本建置。

請檢查最新版本的 [[EDK II 規範|EDK II Specifications]] 。

***

__**內容表格**__
* [[.INF 檔|Build Description Files#INF 檔]] 模組資訊檔 <BR>
  - [[註解|Build Description Files#註解]] - [[\[Defines\]|Build Description Files#defines-]] - [[\[Packages\]|Build Description Files#Packages]] - [[\[Sources\]|Build Description Files#Sources]] - [[\[LibraryClasses\]|Build Description Files#LibraryClasses]] - [[\[Protocols\]|Build Description Files#Protocols]] - [[\[Guids\]|Build Description Files#Guids]] - [[\[BuildOptions\]|Build Description Files#BuildOptions]]
* [[.DEC 檔|Build Description Files#DEC 檔]] 套件宣告檔<BR>
  - [[註解|Build Description Files#註解-1]] - [[\[Defines\]|Build Description Files#defines]] - [[\[includes\]|Build Description Files#includes]] -  [[\[libraryclasses\]|Build Description Files#libraryclasses-1]] -  [[\[Guids\]|Build Description Files#guids-1]] - [[\[Pcds . . .\]|Build Description Files#pcds-----sections]]
* [[.DSC 檔|Build Description Files#DSC 檔]] 平台組態描述檔 <BR>
  - [[\[Defines\]|Build Description Files#defines-1]] -  [[\[libraryclasses\]|Build Description Files#libraryclasses-2]] -  [[\[Pcds . . .\]|Build Description Files#pcds-----sections-1]] - [[\[Components\]|Build Description Files#components]]

***


## .INF 檔

對於規範和描述，參考: [[EDK II 規範|EDK II Specifications]] 頁面上的 [[INF|EDK II Specifications#INF]]<BR>
這個檔案描述如何建置一個模組 (例 驅動程式，函式庫，應用程式等等)。

### 註解
單一井 `#` 字元表示在 (INF) 檔案上的註解。行裡的註解會中斷一行的流程。行註解必須放置在行末，和不能在區段([,])標籤之中。井字元出現在帶引號符號的字串上是被允許的。

注意: _\<使用阻段(Usage Blcok)\>_ 伴隨著雙 `##` 開始(存)在(於)各式各樣的區塊裡，和它 **不是** 當成一個註解而是被已包含在 EDK II 基本建置工具專案裡的 Intel(R) UEFI 套件工具解析使用。在註解阻段裡的使用描述了如何在 C 原始碼裡使用協議(Protocol), PPIS 或 GUID 。

### [Defines] <br>
```
     INF_VERSION            = 1.25 
```
定義 INF 檔支援的 EDK II INF 規範的版本。<br><br>
``` 
    BASE_NAME             = NameOuputWithoutExtension
```
定義在建置完成(生成)最終 .efi 或 .lib 二進制檔後，模組(應用程式，函式庫...等等)的基本輸出名稱。<br><br>
``` 
    MODULE_UNI_FILE        = NameOuput.uni
```
選擇性條目通常用來定位一個統一碼 (Unicode) 檔，該檔用於標頭區段上模組的摘要和描述的在地化。這 .uni 檔必須相對於 INF 檔所在的目錄下。<br><br>
```
     FILE_GUID             = 11111111-2222-3333-4444-555555555555
```
對這個模組而言獨一無二的GUID。 參考 http://www.guidgen.com/ <br><br>
```
     MODULE_TYPE           = USER_DEFINED
```
所建置的模組種類。這涵蓋諸如 UEFI_DRIVER, UEFI_APPLICATION, DXE_DRIVER等;對函式庫，它能是 BASE, USER_DEFINED等...<br><br>
```
       VERSION_STRING      = 1.0
```
你的模組的開發者定義版本，Major "." Minor 數字。<br><br>
```
       ENTRY_POINT         = MainFunctionName
```
假如你的模組不是函式庫，這個變數是定義開始執行的函式。這是相似於 C 裡的 main() 函式。<br><br>
```
       LIBRARY_CLASS  = LibNameToReference | AllowedModuleType1 AllowedModuleType2 Etc . . .
```
假如你的模組是函式庫，這是函式庫在建構系統裡被認知的名稱，函式庫能被其後跟隨垂直條 (Vertical Bar |) 和一串空格 (a list of space) 後的模組種類所使用。<br><br>
```
       CONSTRUCTOR         = LibInitializationFunction
```
假如你的模組是一個函式庫且需要在啟動時初始化，你能用 CONSTRUCTOR 變數去指出在一個模組主要進入點被呼叫前先呼叫的函式名稱。<br><br>

### [Packages]

列(表)出這模組將使用的各種套件。這告訴建置系統經由不同的套件宣告檔 (.DEC) 去哪裡尋找函式庫類別 (給函式庫用的標頭檔)，平台配置資料庫 (PCDs), 全域唯一識別元 (GUIDs), 協議 (Protocols)和 韌體前模組同階介面 (PPIs)。不使用在這個套件下的 ~~.DCS~~.DSC 檔。一般來最低需要的套件是 MdePkg.dec 。
```
      MdePkg/MdePkg.dec
```

### [Sources]

列(表)出建置這個模組所使用的各種源碼和標頭檔。
``` 
      MyFile.h
      MyFile.c
```

### [LibraryClasses]

列出模組使用且應被連結的函式庫。 LibNameToReference 的值被函式庫模組使用在它的 .INF 檔裡。對這個區段裡的每個條目都需要有一個與這個模組相關聯的[LibraryClasses]的條目在 .DSC 檔裡。這是因為在 [Packages] 區段裡(列)的套件是不被用來決定函式庫模組連結的。
例如:
``` 
   LibNameToReference
```
  
### [Protocols]

列出被原始碼使用/需要的協定全域唯一識別元 (GUIDs) 變數名稱。這變數名稱被定義在在 [Packages].DEC 裡之中的一個 [Guids]區段。還列出了這個模組上給協定用的使用阻段 (Usage Block) 定義。<BR>
例如:
``` 
  gEfiDiskInfoProtocolGuid                      ## BY_START
```

這 `## BY_START`  是一個關鍵字代表了這個協定被驅動程式綁定協議開始函式所生成。
 
### [Guids]

列出被原始碼使用/需要的全域唯一識別元 (GUIDs) 變數名稱。這變數名稱被定義在在 [Packages].DEC 裡之中的一個 [Guids]區段。 <BR>
例如:
``` 
    gEfiDiskInfoScsiInterfaceGuid                 ## SOMETIMES_PRODUCES ## UNDEFINED
```
使用阻段 `## SOMETIMES_PRODUCES` 和全域唯一識別元 (guid) 種類 `## UNDEFINED` 代表了這個模組將會生成一個不符合定義為 PROTOCOL 或 PPI 類型的全域唯一識別元 (GUID)。這模組有條件式地生成了有命名的全域唯一識別元 (GUID)。
 
### [BuildOptions]
 
增加建置該模組所需要的編譯器特定選項。
  
***


## .DEC 檔 
對於規範和描述，參考: [[EDK II 規範|EDK II Specifications]] 頁面上的 [[DEC|EDK II Specifications#DEC]]<BR>
這個檔案被使用來宣告在套件裡甚麼可以用，且告訴建置系統去哪裡找到諸如 “Include” 的目錄。它也可以透過一個稱為平台配置資料庫 (PCD) 的機制替換在 .h 檔裡 #define 的值或常數的使用。這個檔案被使用在當一個模組包含這個套件到它的 [Packages] 區段。
### 註解
單一井 `#` 字元表示在 (INF) 檔案上的註解。行裡的註解會中斷一行的流程。行註解必須放置在行末，和不能在區段([,])標籤之中。井字元出現在帶引號符號的字串上是被允許的。

#### 註解阻段條目
一個雙井 `##` 被使用在註解阻段條目上。 無論是標頭檔，一個項目支持的模組種類和其他資訊這都是對註解資訊的推薦格式。
這些註解阻段的一般格式在 [Guids], [Protocols]和 [Ppis] 區段上是:<br>
```
## Path/To/HeaderFile.h
  GUID_C_Name = <GUID> [## <ModuleTypeList>] [# <HelpText>]
```

### [Defines]
```
       DEC_SPECIFICATION   = 1.25
```
定義 DEC 檔支援的 EDK II DEC 規範的版本。<BR><BR>

      PACKAGE_NAME         = NameOfThePackage
      PACKAGE_GUID         = 11111111-2222-3333-4444-555555555555
      PACKAGE_VERSION      = 1.00


上面例子是相似於之前 [[.INF 檔|Build Description Files#INF 檔]] 的例子。<BR>

### [Includes]

這個區段列出給套件和使用這些套件 (.h 檔的搜尋路徑) 的模組用的涵蓋目錄。這個 [Includes] 區段也可透過附加期間和結構名稱方式到涵蓋名稱去按結構方式指示目錄。例如 [Includes.IA32]，[Includes.X64]。這是你的 .C 模組去找 #include <header.h> 檔的地方。<BR>
例如:
```
  [Includes]
    TheIncludesDirectoryForThePackage
```

### [LibraryClasses]

列出在套件裡(提供)和在能找到標頭檔位置上的可用的函式庫。可用的函式庫是指屬於套件的模組是函式庫。可用函式庫的名稱必須符合 LIBRARY_CLASS 名稱，其被給定在屬於套件的各種 .INF 檔裡。這用來建置系統當你的模組 .INF [Packages] 區段包含這個套件 (Package) 和它的 [LibraryClasses] 包含一個 LibNameToReference 。然後建置系統會生成 #include 到標頭檔案在 autogen.h 檔裡，因而你不需要包含 (include) 它在你的源碼模組裡。<BR>
 
例如:
```
  ##  @libraryclass  Name description of library function.
  #   This library does something.
    LibNameToReference | relative/path/to/header.h  
```

### [Guids]

定義各式各樣的 GUIDS 變數/被套件使用。它替換原本在 .h 檔中的 #defines。然而你仍然需要定義一個包含一個對變數名稱的額外參照的一個 .h 檔。 
<BR> 
例如:<BR>
* 記住 關於以下的 `##` 註解當成文件而被建議，但不被建置系統所要求。
```
    ##location/of/extern/header.h
    gSomeVarGuid = {0x11111111, 0x2222, 0x3333, {0x44, 0x44, 0x55, 0x55, 0x55, 0x55, 0x55, 0x55}}
```
<BR><BR>
現在，在一個檔案 /location/of/extern/header.h 裡，我們新增了
```
    extern EFI_GUID gSomeVarGuid;
```

### [Pcds . . .] -Sections
```
   [PcdsFeatureFlag]
   [PcdsFixedAtBuild]
   [PcdsFixedAtBuild,PcdsPatchableInModule]
   [PcdsDynamic,]
```

這些區段呈現一個平台配置資料庫 (PCD) 的創建。實質上這是一個在 .h 檔內替換對使用 #defines, #if defined, 和 靜態常數 (static const variables)。EDK II 的設計者的野望是不鼓勵 #if define() 類型的編碼，此可能導致移植上的困難當嘗試在原始碼上定位常數 (constants) 和 "#define" 變數。 <BR>
相反它使用了編譯器的優化去跳過使用了沒有使用 PCD 的源碼。另外，為了使源碼更具可移植性，建議在 #defines 上使用常數變數當值可能需要以二進制形式上進行修補。<br> 
例如:

```
  [PcdsFixedAtBuild, PcdsPatchableInModule, PcdsDynamic, PcdsDynamicEx]

    . . .

  ## This PCD defines the times to print hello world string.
  #  This PCD is a sample to explain UINT32 PCD usage.
  # @Prompt HellowWorld print times.
  gEfiMdeModulePkgTokenSpaceGuid.PcdHelloWorldPrintTimes|1|UINT32|0x40000005
```

***

 
## .DSC 檔
對於規範和描述，參考: [[EDK II 規範|EDK II Specifications]] 頁面上的 [[DSC|EDK II Specifications#DSC]]<BR>
這個檔案描述如何建置一個套件; 一個套件當成是被提供在一起的元件的集合。注意建置將需要至少一個 .DSC 檔來建置完成。
 
### [Defines]
在此區段裡的值是不言自明的。

      PLATFORM_NAME            = name of the platform
      PLATFORM_GUID            = 11111111-2222-3333-4444-555555555555
      PLATFORM_VERSION         = 1.00
      DSC_SPECIFICATION        = 1.26
      OUTPUT_DIRECTORY         = Build/packagedirectory
      SUPPORTED_ARCHITECTURES  = IA32|IPF|X64|EBC|ARM
      BUILD_TARGETS            = DEBUG|RELEASE
      SKUID_IDENTIFIER         = DEFAULT
 
### [LibraryClasses]

列出各式各樣的這個套件可能使用的函式庫元件。這告訴建置系統要連結的函式庫的所在位置。這模組 .INF 檔指出 LibNameToReference 在它的 [LibraryClasses] 區段裡，和建置系統要看這個區段去找到它。建置系統不使用你在 .INF 檔裡的 [Packages] 區段去找到連結的函式庫；它使用 [Packages] 區段去找到標頭檔的所在位置給套件 .DEC 檔的一個函式庫使用。 這格式是:

    LibNameToReference|Path/To/Library/Inf/File.inf

### [Pcds . . .] -Sections
    [PcdsFeatureFlag]
    [PcdsFixedAtBuild]
    [PcdsFixedAtBuild,PcdsPatchableInModule]
    [PcdsDynamic,]

'''等等......''' 

這些區段呈現在平台配置資料庫 (PCD) 裡的一個特定記號變數的重新定義。這是可選擇性的和只有在專案需要一個不同值當成在 .DEC 檔裡被定義時需要用到。
 
### [Components]
列出當套件 .DSC 檔被建置完成時給這個套件建置用來專門建置的各式元件和模組；而不是當一個套件被一個 .INF 檔的 [Packages] 區段參照時。你也能藉著附加一個期間和結構到元件的後面 (例 [Components.IA32]) 來指定結構特定部分。這個區段也可以用來建置一個參照自 .INF 檔裡的 [Packages] 區段的函式庫。這用來當你要去建置一個分離函式庫，用傳統方式去連結它或為了確保它建置適當而偵錯這個函式庫。 <BR>
至少要有一個 .inf 檔列在元件 (components) 區段裡才能建置成功 <BR>
例如:<BR>
* 記住: 相對位置是從 edk2 基本目錄(開始)而不是套件目錄 (也可參考成工作區目錄(Work Space Directory))
```
  [Components]
     relative/path/to/module.inf
```
 
# 原文
# Build Description Files

Understanding the basic setup of .DCS, .DEC, and .INF build description files. 

Please check for the latest version of the [[EDK II Specifications]]

***

__**Table of Contents**__
* [The .INF File](#the-inf-file) Module Information file <BR>
  - [comments](#comments) - [\[Defines\]](#defines-) - [\[Packages\]](#packages) - [\[Sources\]](#sources) - [\[LibraryClasses\]](#libraryclasses) - [\[Protocols\]](#protocols) - [\[Guids\]](#guids) - [\[BuildOptions\]](#buildoptions)
* [The .DEC File](#the-dec-file) Package Declaration file<BR>
  - [comments](#comments-1) - [\[Defines\]](#defines) - [\[Includes\]](#includes) -  [\[LibraryClasses\]](#libraryclasses-1) -  [\[Guids\]](#guids-1) - [\[Pcds . . .\]](#pcds-----sections)
* [The .DSC File](#the-dsc-file) Platform Description File <BR>
  - [\[Defines\]](#defines-1) -  [\[LibraryClasses\]](#libraryclasses-2) -  [\[Pcds . . .\]](#pcds-----sections-1) - [\[Components\]](##components)

***


## The .INF file

For the Spec and Description see: [INF](EDK-II-Specifications#inf) on the [[EDK II Specifications]] page<BR>
This file describes how to build a module (i.e. a driver, library, application, etc…).

### Comments
The single hash `#` character indicates comments in the (INF) file. In line comments terminate the processing of a line. In line comments must be placed at the end of the line, and may not be placed within the section ([,]) tags. Hash characters appearing within a quoted string are permitted.

Note: The _\<Usage Block\>_ will start with double `##` within the various sections and is **not** a comment and will be parsed for the the Intel(R) UEFI Packaging Tool included in the EDK II base tools project. The usages in the comment block describe how the Protocol, PPIS or GUID  is used in the C code.


### [Defines] <br>
```
     INF_VERSION            = 1.25 
```
Defines the version of the EDK II INF specification the INF file supports. <br><br>
``` 
    BASE_NAME             = NameOuputWithoutExtension
```
Defines the base output name of the module (application, library, etc...) when built resulting in the final .efi or .lib binary.<br><br>
``` 
    MODULE_UNI_FILE        = NameOuput.uni
```
Optional entry used to locate an Unicode file which can be used for localization of the module's Abstract and Description from the header section. The .uni file  must be relative to the directory the INF file .<br><br>
```
     FILE_GUID             = 11111111-2222-3333-4444-555555555555
```
A unique GUID for this module. See  http://www.guidgen.com/ <br><br>
```
     MODULE_TYPE           = USER_DEFINED
```
The type of module being built.  This includes things such as UEFI_DRIVER, UEFI_APPLICATION, DXE_DRIVER, etc… For libraries it can be BASE, USER_DEFINED, etc…<br><br>
```
       VERSION_STRING      = 1.0
```
The developer defined version of your module, Major "." Minor number.<br><br>
```
       ENTRY_POINT         = MainFunctionName
```
If your module is not a library, this variable defines the function to begin execution.  This is similar to the main() function in C.<br><br>
```
       LIBRARY_CLASS  = LibNameToReference | AllowedModuleType1 AllowedModuleType2 Etc . . .
```
If your module is a library, this is the name the library is to be known as within the build system followed by a vertical bar and a list of space delimitated module types this library can be used with.<br><br>
```
       CONSTRUCTOR         = LibInitializationFunction
```
If your module is a library and requires initialization on startup, you can use the CONSTRUCTOR variable to indicate the function name to call prior to a modules main entry point being called.<br><br>
 
### [Packages]
 
List the various packages the module will use.  This tells the build system where to look for library classes (header files for the library), PCDs, GUIDs, Protocols, and PPIs via the different packages .DEC files.    The .DCS file from this package is not used. Typically minimum required package  is the MdePkg.dec 
```
      MdePkg/MdePkg.dec
```

### [Sources]

List the various source and header files used to build the module.
``` 
      MyFile.h
      MyFile.c
```

### [LibraryClasses]

List the various libraries the module uses and should be linked with.  This is the LibNameToReference value the library module used in its .INF file.  For each entry in this section there needs to be an entry [LibraryClasses] sector of the .DSC file this module is associated with.  This is because the packages in the [Packages] section are not used to determine the library module to link with. <BR>
For Example:
``` 
   LibNameToReference
```
  
### [Protocols]
 
List the various protocol GUIDs variable name needed/used by the sources.  The variable name is defined in one of the [Packages].DEC [Guids] section. Also listed are the Usage Block definitions for the protocol for this module <BR>
For Example:
``` 
  gEfiDiskInfoProtocolGuid                      ## BY_START
```

The `## BY_START`  is a key word that means that this protocol is produced by a Driver Binding protocol Start function.
 
### [Guids]
 
List the various GUIDs variable name needed/used by the sources. The variable name is defined in one of the [Packages].DEC [Guids] section. <BR>
For Example:
``` 
    gEfiDiskInfoScsiInterfaceGuid                 ## SOMETIMES_PRODUCES ## UNDEFINED
```
The usage block `## SOMETIMES_PRODUCES` and guide type `## UNDEFINED` Means that the module will produce a GUID that does not fit into the defined PROTOCOL or PPI types. This module conditionally produces the named GUID. 
 
### [BuildOptions]
 
Add compiler specific options needed to build the module.
  
***


## The .DEC file 
For the Spec and Description see: [DEC](EDK-II-Specifications#dec) on the [[EDK II Specifications]] page<BR>
This file is used to declare what is available in the package and tells the build system where to find things such as “Include” directories.  It can also be used to replace the use of #define values or constant variables in .h files though a mechanism called the Platform Configuration Database(PCD).  This file is used when a module includes this package in its [Packages] section.
### Comments
The single hash `#` character indicates comments in the (INF) file. In line comments terminate the processing of a line. In line comments must be placed at the end of the line, and may not be placed within the section ([,]) tags. Hash characters appearing within a quoted string are permitted.

#### Comment Block entries
A double `##` hash is used for comment block entries. This is a recommended format for comment information regarding the header files, module types an item supports and other information. <BR>
The general format of these comment blocks in the [Guids], [Protocols] and [Ppis] sections is:<br>
```
## Path/To/HeaderFile.h
  GUID_C_Name = <GUID> [## <ModuleTypeList>] [# <HelpText>]
```

### [Defines]
```
       DEC_SPECIFICATION   = 1.25
```
Defines the version of the EDK II DEC specification the DEC file supports.<BR><BR>

      PACKAGE_NAME         = NameOfThePackage
      PACKAGE_GUID         = 11111111-2222-3333-4444-555555555555
      PACKAGE_VERSION      = 1.00


The above example are similar to the example for the [.INF File](#the-inf-file)  above.<BR>

### [Includes]

This section lists the include directories for the package and modules that use the package (the search path for .h files).  The [Incudes] section can also indicate directories by Architecture used by appending a period and architecture name to the Includes name.  For example [Includes.IA32], [Includes.X64].   This is where your .C modules look for #include <header.h> files.<BR> 
For example:
```
  [Includes]
    TheIncludesDirectoryForThePackage
```

### [LibraryClasses]

Lists the libraries available in (provided by) the package and where the header file can be found.  The libraries available are the modules that belong to the package which are libraries.  The name of the library available must match the LIBRARY_CLASS names given in the various .INF files that belong to the package.  This is used by the build system when your modules .INF [Packages] section includes this package and its [LibraryClasses] include a LibNameToReference.  The build system then generates the #include to the header file in the autogen.h file so you don’t need to include it in your source modules.<BR>
 
For example:
```
  ##  @libraryclass  Name description of library function.
  #   This library does something.
    LibNameToReference | relative/path/to/header.h  
```

### [Guids]

Defines various GUIDS available / used by the package.  It replaces #defines that would otherwise be in a .h file.  However you still must define a .h file that includes an extern reference to the variable name.  
<BR> 
For Example:<BR>
* note the `## `comment below is recommended for documentation but not required by the build system.
```
    ##location/of/extern/header.h
    gSomeVarGuid = {0x11111111, 0x2222, 0x3333, {0x44, 0x44, 0x55, 0x55, 0x55, 0x55, 0x55, 0x55}}
```
<BR><BR>
Now in a file /location/of/extern/header.h we add
```
    extern EFI_GUID gSomeVarGuid;
```

### [Pcds . . .] -Sections
```
   [PcdsFeatureFlag]
   [PcdsFixedAtBuild]
   [PcdsFixedAtBuild,PcdsPatchableInModule]
   [PcdsDynamic,]
```
 
These sections represent the creation of a Platform Configuration Database (PCD).   Essentially this is a replacement for using #defines, #if defined, and static const variables in .h files.   The desire of the designers of the EDK II was to discourage the use of #if define() type coding which could lead to difficulties in porting when trying to locate the constants and "#define" variables within the source code. <BR>
Instead it uses the compilers optimizations to strip the use of code not used by using PCDs.   Also to make the code more portable, it is recommended to use of const variables over #defines where values may need to be patchable in binary form.<br>
Example:

```
  [PcdsFixedAtBuild, PcdsPatchableInModule, PcdsDynamic, PcdsDynamicEx]

    . . .

  ## This PCD defines the times to print hello world string.
  #  This PCD is a sample to explain UINT32 PCD usage.
  # @Prompt HellowWorld print times.
  gEfiMdeModulePkgTokenSpaceGuid.PcdHelloWorldPrintTimes|1|UINT32|0x40000005
```

***

 
## The .DSC file
For the Spec and Description see: [DSC](EDK-II-Specifications#dsc) on the [[EDK II Specifications]] page<BR>
This file describes how to build a package; a package being a set of components to be provided together. Note the Build will need at least one .DSC file to be successful.
 
### [Defines]
The values in this section are self-explanatory.

      PLATFORM_NAME            = name of the platform
      PLATFORM_GUID            = 11111111-2222-3333-4444-555555555555
      PLATFORM_VERSION         = 1.00
      DSC_SPECIFICATION        = 1.26
      OUTPUT_DIRECTORY         = Build/packagedirectory
      SUPPORTED_ARCHITECTURES  = IA32|IPF|X64|EBC|ARM
      BUILD_TARGETS            = DEBUG|RELEASE
      SKUID_IDENTIFIER         = DEFAULT
 
### [LibraryClasses]

List the various libraries the components of this package may use.  This tells the build system where the library to link with is located.  The modules .INF file indicates the LibNameToReference in its [LibraryClasses] section and the build system looks to this section for how to find it.  The build system does not use your [Packages] section of the .INF to find the library to link with; it uses the [Packages] section to find the location of the header files for a library in a packages .DEC file.  The format is:

    LibNameToReference|Path/To/Library/Inf/File.inf

### [Pcds . . .] -Sections
    [PcdsFeatureFlag]
    [PcdsFixedAtBuild]
    [PcdsFixedAtBuild,PcdsPatchableInModule]
    [PcdsDynamic,]

'''Etc…''' 

These sections represent the redefinition of a particular token variable in the Platform Configuration Database (PCD).  These are optional and only needed if the project needs a different value as defined in the .DEC file.  
 
### [Components]
List the various components or modules to build for this package specifically built as a result of when the package .DSC file is built; not when the package is referenced by the [Packages] section of an .INF file.  You can also specify architecture specific sections by appending a period and architecture to the end of Components (e.g.[Components.IA32]). This section can also be used for building a library referenced in the [Packages] section of an .INF file.    This is used when you want to build a separate library and link to it in a traditional way or for debugging the library to ensure it builds properly. <BR>
There must be at least one .inf file listed in the components section for the build to be successful <BR>
For example:<BR>
* Note: that the relative path is from the edk2  base directory and not the package directory (also referred to as the Work Space Directory)
```
  [Components]
     relative/path/to/module.inf
```
 