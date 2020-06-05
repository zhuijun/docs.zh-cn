---
title: 如何：引用枚举成员
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 66c527bd4ba4721065de8fca8534fe652d0139be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414409"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a>如何：引用枚举成员 (Visual Basic)
枚举提供了一种简便的方法来处理相关常量集，并将常量值与名称相关联。 例如，可以为一组与星期几相关联的整数常量声明一个枚举，然后在代码中使用星期几的名称而不是整数值。  
  
 您可以通过语句避免使用完全限定的名称 `Imports` 。 有关详细信息，请参阅[枚举和名称限定](enumerations-and-name-qualification.md)。  
  
### <a name="to-refer-to-an-enumeration-member"></a>引用枚举成员  
  
- 用枚举限定成员名称。 例如，下面的示例将枚举的 `Saturday` 成员赋 `FirstDayOfWeek` 给该变量 `DayValue` 。  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a>另请参阅

- [如何：声明枚举](how-to-declare-enumerations.md)
- [枚举和名称限定](enumerations-and-name-qualification.md)
- [如何：在 Visual Basic 中循环访问枚举](how-to-iterate-through-an-enumeration.md)
- [如何：确定与枚举值关联的字符串](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [何时使用枚举](when-to-use-an-enumeration.md)
