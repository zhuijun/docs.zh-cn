---
title: 不支持 XML 实体引用
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: 470e5577654ce8b6bbc2732a41c130a85ddc96e5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874990"
---
# <a name="xml-entity-references-are-not-supported"></a>不支持 XML 实体引用

例如，在 `©` xml 1.0 规范中未定义的)  (实体引用包含为 xml 文本值。 `&` `"` `<` `>` Xml 文本中仅支持、、、和 `'` xml 实体引用。  
  
 **错误 ID：** BC31180  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 删除不受支持的实体引用。  
  
## <a name="see-also"></a>另请参阅

- [XML 文本和 XML 1.0 规范](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [XML 文本](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
