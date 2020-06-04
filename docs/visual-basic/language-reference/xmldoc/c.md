---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: c8ba03d9cc01c4751d15c01530c6cbf7d499dc3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400158"
---
# <a name="c-visual-basic"></a>\<c> (Visual Basic)
指示说明中的文本为代码。  
  
## <a name="syntax"></a>语法  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>参数  
  
|参数|说明|  
|---|---|  
|`text`|要指示为代码的文本。|  
  
## <a name="remarks"></a>备注  
 `<c>`标记提供了一种方法，用于指示应将说明中的文本标记为代码。 用于将 [\<code>](code.md) 多行指示为代码。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 此示例使用 " `<c>` 摘要" 部分中的标记指示该 `Counter` 为代码。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另请参阅

- [XML 注释标记](index.md)
