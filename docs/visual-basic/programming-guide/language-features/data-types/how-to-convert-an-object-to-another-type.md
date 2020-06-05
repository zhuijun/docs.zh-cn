---
title: 如何：将一个对象转换为其他类型
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: cdb78bc66867ce27076d7b7e42de6a2880cb3a8c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393956"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>如何：在 Visual Basic 中将一个对象转换为其他类型
您可以 `Object` 使用转换关键字（如[CType 函数](../../../language-reference/functions/ctype-function.md)）将变量转换为另一种数据类型。  
  
## <a name="example"></a>示例  
 下面的示例将 `Object` 变量转换为 `Integer` 和 `String` 。  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 如果知道变量的内容属于 `Object` 特定的数据类型，最好将该变量转换为该数据类型。 如果继续使用该 `Object` 变量，则会产生*装箱*和*取消装箱*（对于值类型）或*后期绑定*（对于引用类型）。 这些操作都需要额外的执行时间，并使性能更慢。  
  
## <a name="compile-the-code"></a>编译代码  
 此示例需要：  
  
- 对 <xref:System?displayProperty=nameWithType> 命名空间的引用。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Object>
- [Visual Basic 中的类型转换](type-conversions.md)
- [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md)
- [隐式转换和显式转换](implicit-and-explicit-conversions.md)
- [字符串和其他类型之间的转换](conversions-between-strings-and-other-types.md)
- [数组转换](array-conversions.md)
- [结构](structures.md)
- [数据类型](../../../language-reference/data-types/index.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
