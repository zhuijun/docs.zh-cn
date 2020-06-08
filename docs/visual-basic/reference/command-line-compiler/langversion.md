---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 271606ac021e6afcb28fdac3e1bc86e1aaba7d2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408533"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
使编译器仅接受包含在指定 Visual Basic 语言版本中的语法。  
  
## <a name="syntax"></a>语法  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>自变量  
 `version`  
 必需。 要在编译过程中使用的语言版本。 接受的值为 `9`、`10`、`11`、`12`、`14`、`15`、`15.3`、`15.5`、`default` 和 `latest`。

 还可以使用 `.0` 作为次要版本来指定任何整数，例如 `11.0`。

 通过在命令行上指定 `-langversion:?`，可以查看所有可能值的列表。  
  
## <a name="remarks"></a>备注  
 `-langversion` 选项指定编译器接受的语法。 例如，如果指定语言版本为 9.0，则编译器将生成仅在 10.0 及更高版本中有效的语法错误。  
  
 在开发面向不同 .NET Framework 版本的应用程序时，可以使用此选项。 例如，如果面向的是 .NET Framework 3.5，则可以使用此选项来确保不使用语言版本 10.0 中的语法。  
  
 只能使用命令行直接设置 `-langversion`。 有关详细信息，请参阅[面向特定的 .NET Framework 版本](/visualstudio/ide/visual-studio-multi-targeting-overview)。  
  
## <a name="example"></a>示例  
 以下代码为 Visual Basic 9.0 编译 `sample.vb`。  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](index.md)
- [示例编译命令行](sample-compilation-command-lines.md)
- [面向特定的 .NET Framework 版本](/visualstudio/ide/visual-studio-multi-targeting-overview)
