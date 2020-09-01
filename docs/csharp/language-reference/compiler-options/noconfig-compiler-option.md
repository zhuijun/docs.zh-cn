---
description: -noconfig（C# 编译器选项）
title: -noconfig（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 26d0680743ccc3af26a0e81eeec9cd2fc0d693af
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125223"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig（C# 编译器选项）
-noconfig 选项告知编译器不要在 csc.rsp 文件中编译，该文件的位置和加载位置是与 csc.exe 文件相同的目录****。  
  
## <a name="syntax"></a>语法  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>备注  
 csc.rsp 文件引用 .NET Framework 随附的所有程序集。 Visual Studio .NET 开发环境包括的实际引用取决于项目类型。  
  
 可以修改 csc.rsp 文件并使用 csc.exe 的命令行指定每个编译中应包含的其他编译器选项（-noconfig 选项外）****。  
  
 编译器将处理最后传递给 csc 命令的选项****。 因此，命令行中的任何选项都将替代 csc.rsp 文件中相同选项的设置。  
  
 如果不希望编译器查询和使用 csc.rsp 文件中的设置，请指定 -noconfig****。  
  
 此编译器选项在 Visual Studio 中不可用，并且无法以编程方式更改。  
  
## <a name="see-also"></a>另请参阅

- [C# 编译器选项](./index.md)
- [管理项目和解决方案属性](/visualstudio/ide/managing-project-and-solution-properties)
