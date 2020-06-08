---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 405b557568a736de3ddc3b51e265261222613131
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403026"
---
# <a name="-verbose"></a>-verbose
导致编译器生成详细状态和错误消息。  
  
## <a name="syntax"></a>语法  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>自变量  
 `+` &#124; `-`  
 可选。 指定 `-verbose` 与指定 `-verbose+` 相同，这将导致编译器发出详细消息。 此选项的默认值为 `-verbose-`。  
  
## <a name="remarks"></a>备注  
 `-verbose` 选项显示编译器发出的错误总数的相关信息，报告模块正在加载的程序集，并显示当前正在编译的文件。  
  
> [!NOTE]
> `-verbose` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。  
  
## <a name="example"></a>示例  
 下面的代码编译 `In.vb`，并指示编译器显示详细状态信息。  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](index.md)
- [示例编译命令行](sample-compilation-command-lines.md)
