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
 