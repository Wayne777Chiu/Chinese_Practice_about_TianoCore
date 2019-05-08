(2019/03/08)
# Nasm

## 下載 NASM

NASM 組譯器可找到於: http://www.nasm.us/

NASM 最新的(版本) 2.12  的發佈公告連結在: http://www.nasm.us/doc/nasmdocc.html

NASM 2.12 新增了 Codeview 版本 8 (cv8) 的支援，其允許 NASM 源碼的源碼等級偵錯當 EDK II 源碼是透過 Microsoft Visual Studio* 20xx 工具鏈建置下。

## Nasm 字首綴詞
Nasm 環境變數被使用來給 EDK II Build
假如組合源碼 (assembly code) 被模組使用了且使用 NASM 組譯器(來組譯)，這系統環境變數, NASM_PREFIX 一定要被設定且必須涵蓋伴隨的反斜線，如以下展示的:
<pre>
	C:\edk2\> set NASM_PREFIX =C:\nasm\
</pre>


# 原文
# Nasm

## Download Nasm
The NASM assembler is available from: 	http://www.nasm.us/

The link to the release notes for what is new in NASM 2.12 is at:  http://www.nasm.us/doc/nasmdocc.html

NASM 2.12 adds support for Codeview version 8 (cv8) which allows for source level debug of NASM sources when EDK II sources are built using Microsoft Visual Studio* 20xx tool chains  

## Nasm Prefix 
Nasm environment variable is used for the EDK II Build
If assembly code is used by the modules and the NASM assembler is used, the system environment variable, NASM_PREFIX must be set as shown below and must include the trailing backslash character:
<pre>
  C:\edk2\> set NASM_PREFIX =C:\nasm\
</pre>