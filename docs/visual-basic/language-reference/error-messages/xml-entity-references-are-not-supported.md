---
title: 不支持 XML 实体引用
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: ae997d853a93999a3b29215ea1257da7a1d48c84
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406451"
---
# <a name="xml-entity-references-are-not-supported"></a>不支持 XML 实体引用
`©`Xml 1.0 规范中未定义的实体引用（例如，）作为 xml 文本值包含在内。 `&` `"` `<` `>` Xml 文本中仅支持、、、和 `'` xml 实体引用。  
  
 **错误 ID：** BC31180  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 删除不受支持的实体引用。  
  
## <a name="see-also"></a>另请参阅

- [XML 文本和 XML 1.0 规范](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [XML 文本](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
