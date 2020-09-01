---
description: -recurse（C# 编译器选项）
title: -recurse（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 3edd7e23358bc0569dae6204d519209df1ade290
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124820"
---
# <a name="-recurse-c-compiler-options"></a>-recurse（C# 编译器选项）
通过 -recurse 选项，可在指定目录 (dir) 的所有子目录中，或项目目录的所有子目录中编译源代码文件。  
  
## <a name="syntax"></a>语法  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>自变量  
 `dir`（可选）  
 希望从中开始搜索的目录。 如未指定目录，搜索将从项目目录开始。  
  
 `file`  
 要搜索的文件。 允许通配符。  
  
## <a name="remarks"></a>备注  
 通过 -recurse 选项，可在指定目录 (`dir`) 的所有子目录中，或项目目录的所有子目录中编译源代码文件****。  
  
 可在文件名中使用通配符，对项目目录中的所有匹配文件进行编译，而无需使用 -recurse****。  
  
 此编译器选项在 Visual Studio 中不可用，并且无法以编程方式更改。  
  
## <a name="example"></a>示例  
 在当前目录中编译所有 C# 文件：  
  
```console  
csc *.cs  
```  
  
 编译 dir1\dir2 目录及其下的任何目录中的所有 C# 文件，并生成 dir2.dll：  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>另请参阅

- [C# 编译器选项](./index.md)
- [管理项目和解决方案属性](/visualstudio/ide/managing-project-and-solution-properties)
