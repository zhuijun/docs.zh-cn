---
title: ASP.NET 中的嵌入式代码不支持 XML 文本和 XML 属性
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: bda92b4244631f66142499a94be562854b35437e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406464"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>ASP.NET 中的嵌入式代码不支持 XML 文本和 XML 属性
ASP.NET 中的嵌入式代码不支持 XML 文本和 XML 属性。 若要使用 XML 功能，请将代码移到代码隐藏。  
  
 XML 文本或 XML 轴属性是 `<%= =>` 在 ASP.NET 文件中的嵌入式代码（）中定义的。  
  
 **错误 ID：** BC31200  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 将包括 XML 文本或 XML 轴属性的代码移到 ASP.NET 代码隐藏文件中。  
  
## <a name="see-also"></a>另请参阅

- [XML 文本](../xml-literals/index.md)
- [XML 轴属性](../xml-axis/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
