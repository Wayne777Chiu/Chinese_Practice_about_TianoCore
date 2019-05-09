(2019/03/08)
# EDK II 偵錯

## 基本概念

EDK II 偵錯的方法是啟動以下的偵錯技術:
* 使用 `DEBUG` 巨集 替換 inline Print() 函數來得到偵錯訊息
* 使用 `ASSERT` 巨集 去中斷程式碼執行在緊急問題 (critical issues)上
* 使用 [[軟體偵錯|SourceLevelDebugPkg]] \(COM/USB\)
* 使用 硬體偵錯 (JTAG/XDB)

EDK II 偵錯函式庫 (`MdePkg\Include\Library\DebugLib.h`) 是一個可移植函式庫，支援DEBUG and ASSERT 巨集，在 `target.txt` 編譯過程中可開啟或關閉。 這些被設計來用第二台電腦觀察一個 ASCII 偵錯紀錄 (debug log) 在終端視窗上。

## Debug 巨集

* DEBUG (Expression)|DEBUG
* DEBUG_CODE (Expression)|DEBUG_CODE
* DEBUG_CODE_BEGIN() & DEBUG_CODE_END()|DEBUG_CODE_BEGIN/END
* DEBUG_CLEAR_MEMORY(...)|DEBUG_CLEAR_MEMORY

## Assert 巨集

* ASSERT (Expression)|ASSERT
* ASSERT_EFI_ERROR (StatusParameter)|ASSERT_EFI_ERROR
* ASSERT_PROTOCOL_ALREADY_INSTALLED(...)|ASSERT_PROTOCOL_ALREADY_INSTALLED

## 平台配置資料庫 (PCDs) 到設定配置 DebugLib

MdePkg 偵錯函式庫物件定義了兩個 平台配置資料庫(PCDs)
* `PcdDebugPropertyMask` - Bit mask 決定特徵是 on/off
* `PcdDebugPrintErrorLevel` - 訊息產出的種類

來自 `Nt32Pkg.dsc` 的例子:

    [PcdsFixedAtBuild.IA32]
     . . .
      gEfiMdePkgTokenSpaceGuid.PcdDebugPropertyMask|0x1f
      gEfiMdePkgTokenSpaceGuid.PcdDebugPrintErrorLevel|0x80000040

 `PcdDebugPropertyMask` bitmask 位元區段定義:

    #define DEBUG_PROPERTY_DEBUG_ASSERT_ENABLED       0x01
    #define DEBUG_PROPERTY_DEBUG_PRINT_ENABLED        0x02
    #define DEBUG_PROPERTY_DEBUG_CODE_ENABLED         0x04
    #define DEBUG_PROPERTY_CLEAR_MEMORY_ENABLED       0x08
    #define DEBUG_PROPERTY_ASSERT_BREAKPOINT_ENABLED  0x10
    #define DEBUG_PROPERTY_ASSERT_DEADLOOP_ENABLED    0x20

`PcdDebugPrintErrorLevel` bitmask 位元區段定義(根據 DebugLib.h):

    #define DEBUG_INIT      0x00000001  // Initialization
    #define DEBUG_WARN      0x00000002  // Warnings
    #define DEBUG_LOAD      0x00000004  // Load events
    #define DEBUG_FS        0x00000008  // EFI File system
    #define DEBUG_POOL      0x00000010  // Alloc & Free's  Pool
    #define DEBUG_PAGE      0x00000020  // Alloc & Free's  Page
    #define DEBUG_INFO      0x00000040  // Verbose
    #define DEBUG_DISPATCH  0x00000080  // PEI/DXE Dispatchers
    #define DEBUG_VARIABLE  0x00000100  // Variable
    #define DEBUG_BM        0x00000400  // Boot Manager
    #define DEBUG_BLKIO     0x00001000  // BlkIo Driver
    #define DEBUG_NET       0x00004000  // SNP / Network Io Driver
    #define DEBUG_UNDI      0x00010000  // UNDI Driver
    #define DEBUG_LOADFILE  0x00020000  // Load File 
    #define DEBUG_EVENT     0x00080000  // Event messages
    #define DEBUG_GCD       0x00100000  // Global Coherency Database changes
    #define DEBUG_CACHE     0x00200000  // Memory range cache-ability changes
    #define DEBUG_VERBOSE   0x00400000  // Detailed debug messages that may
                                        // significantly impact boot performance
    #define DEBUG_ERROR     0x80000000  // Error

# 原文
# EDK II Debugging

## Basic Concepts

EDK II Debug methods enable the following debug techniques:
* Use `DEBUG` macros instead of inline Print() functions for debug messages
* Use `ASSERT` macros to halt code execution on critical issues
* Use a [[software debugger|SourceLevelDebugPkg]] (COM/USB)
* Use a hardware debugger (JTAG/XDB)

The EDK II Debug Library (`MdePkg\Include\Library\DebugLib.h`) is a portable library supporting DEBUG and ASSERT macros, which can be enabled/disabled during compilation in `target.txt`. These are designed to work with a second computer attached as a terminal to observe an ASCII debug log.

## Debug Macros

* DEBUG (Expression)|DEBUG
* DEBUG_CODE (Expression)|DEBUG_CODE
* DEBUG_CODE_BEGIN() & DEBUG_CODE_END()|DEBUG_CODE_BEGIN/END
* DEBUG_CLEAR_MEMORY(...)|DEBUG_CLEAR_MEMORY

## Assert Macros

* ASSERT (Expression)|ASSERT
* ASSERT_EFI_ERROR (StatusParameter)|ASSERT_EFI_ERROR
* ASSERT_PROTOCOL_ALREADY_INSTALLED(...)|ASSERT_PROTOCOL_ALREADY_INSTALLED

## PCDs to configure DebugLib

The MdePkg Debug Library Class defines two PCDs
* `PcdDebugPropertyMask` - Bit mask to determine which features are on/off
* `PcdDebugPrintErrorLevel` - Types of messages produced

Example from `Nt32Pkg.dsc`:

    [PcdsFixedAtBuild.IA32]
     . . .
      gEfiMdePkgTokenSpaceGuid.PcdDebugPropertyMask|0x1f
      gEfiMdePkgTokenSpaceGuid.PcdDebugPrintErrorLevel|0x80000040

Definition of `PcdDebugPropertyMask` bitmask field:

    #define DEBUG_PROPERTY_DEBUG_ASSERT_ENABLED       0x01
    #define DEBUG_PROPERTY_DEBUG_PRINT_ENABLED        0x02
    #define DEBUG_PROPERTY_DEBUG_CODE_ENABLED         0x04
    #define DEBUG_PROPERTY_CLEAR_MEMORY_ENABLED       0x08
    #define DEBUG_PROPERTY_ASSERT_BREAKPOINT_ENABLED  0x10
    #define DEBUG_PROPERTY_ASSERT_DEADLOOP_ENABLED    0x20

Definition of `PcdDebugPrintErrorLevel` bitmask field (according to  DebugLib.h):

    #define DEBUG_INIT      0x00000001  // Initialization
    #define DEBUG_WARN      0x00000002  // Warnings
    #define DEBUG_LOAD      0x00000004  // Load events
    #define DEBUG_FS        0x00000008  // EFI File system
    #define DEBUG_POOL      0x00000010  // Alloc & Free's  Pool
    #define DEBUG_PAGE      0x00000020  // Alloc & Free's  Page
    #define DEBUG_INFO      0x00000040  // Verbose
    #define DEBUG_DISPATCH  0x00000080  // PEI/DXE Dispatchers
    #define DEBUG_VARIABLE  0x00000100  // Variable
    #define DEBUG_BM        0x00000400  // Boot Manager
    #define DEBUG_BLKIO     0x00001000  // BlkIo Driver
    #define DEBUG_NET       0x00004000  // SNP / Network Io Driver
    #define DEBUG_UNDI      0x00010000  // UNDI Driver
    #define DEBUG_LOADFILE  0x00020000  // Load File 
    #define DEBUG_EVENT     0x00080000  // Event messages
    #define DEBUG_GCD       0x00100000  // Global Coherency Database changes
    #define DEBUG_CACHE     0x00200000  // Memory range cache-ability changes
    #define DEBUG_VERBOSE   0x00400000  // Detailed debug messages that may
                                        // significantly impact boot performance
    #define DEBUG_ERROR     0x80000000  // Error

