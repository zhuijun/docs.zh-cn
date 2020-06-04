---
title: 特性“<attributename>”不能应用多次
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 14145f165adf5ccd20298a70ca5596488b488b0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409954"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>特性“\<attributename>”不能应用多次

特性只能应用一次。 `AttributeUsage`特性确定特性是否可以应用多次。  
  
 **错误 ID：** BC30663  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 请确保属性仅应用一次。  
  
2. 如果使用的是你开发的自定义特性，请考虑将其 `AttributeUsage` 特性更改为允许使用多种特性，如下面的示例所示。  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.AttributeUsageAttribute>
- [创建自定义特性](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../programming-guide/concepts/attributes/attributeusage.md)
