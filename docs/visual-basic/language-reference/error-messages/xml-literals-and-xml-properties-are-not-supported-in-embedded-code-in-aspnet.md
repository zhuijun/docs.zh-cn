---
title: ASP.NET 中的嵌入式代码不支持 XML 文本和 XML 属性
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 861677636f9a73015b26efec30df728d07fbdf72
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870205"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>ASP.NET 中的嵌入式代码不支持 XML 文本和 XML 属性

ASP.NET 中的嵌入式代码不支持 XML 文本和 XML 属性。 若要使用 XML 功能，请将代码移到代码隐藏。  
  
 在嵌入代码中定义 XML 文本或 XML 轴属性， (`<%= =>` 在 ASP.NET 文件中) 。  
  
 **错误 ID：** BC31200  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 将包括 XML 文本或 XML 轴属性的代码移到 ASP.NET 代码隐藏文件中。  
  
## <a name="see-also"></a>另请参阅

- [XML 文本](../xml-literals/index.md)
- [XML 轴属性](../xml-axis/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
