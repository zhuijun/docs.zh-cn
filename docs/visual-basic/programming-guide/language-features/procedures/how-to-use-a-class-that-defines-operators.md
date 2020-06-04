---
title: 如何：使用定义运算符的类
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: fe15e976e6a5469f2a9d1b3521a70a3e1860fdd3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414345"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>如何：使用定义运算符的类 (Visual Basic)
如果你使用的是定义其自己的运算符的类或结构，则可以从 Visual Basic 访问这些运算符。  
  
 在类或结构上定义运算符也称为*重载*运算符。  
  
## <a name="example"></a>示例  
 下面的示例访问 SQL 结构 <xref:System.Data.SqlTypes.SqlString> ，它在 sql 字符串与 Visual Basic 字符串之间的两个方向定义转换运算符（[CType 函数](../../../language-reference/functions/ctype-function.md)）。 使用 `CType(` *sql 字符串表达式*，将 `String)` sql 字符串转换为 Visual Basic 字符串，将 `CType(` *Visual Basic 字符串表达式*转换为 <xref:System.Data.SqlTypes.SqlString> `)` 其他方向。  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString>结构定义了从到的转换运算符（[CType 函数](../../../language-reference/functions/ctype-function.md)），并定义了从到的 `String` <xref:System.Data.SqlTypes.SqlString> 另一个 <xref:System.Data.SqlTypes.SqlString> `String` 。 赋值的语句 `title` `jobTitle` 使用第一个运算符，而 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函数调用使用第二个运算符。  
  
## <a name="compile-the-code"></a>编译代码  
 请确保所用的类或结构定义要使用的运算符。 不要假设类或结构已定义每个可用于重载的运算符。 有关可用运算符的列表，请参阅[Operator 语句](../../../language-reference/statements/operator-statement.md)。  
  
 在 `Imports` 源文件开头包含 SQL 字符串的相应语句（在本例中为 <xref:System.Data.SqlTypes> ）。  
  
 你的项目必须引用了 System.web 和 System.object。  
  
## <a name="see-also"></a>另请参阅

- [运算符过程](./operator-procedures.md)
- [如何：定义运算符](./how-to-define-an-operator.md)
- [如何：定义转换运算符](./how-to-define-a-conversion-operator.md)
- [如何：调用运算符过程](./how-to-call-an-operator-procedure.md)
- [Widening](../../../language-reference/modifiers/widening.md)
- [Narrowing](../../../language-reference/modifiers/narrowing.md)
- [Structure 语句](../../../language-reference/statements/structure-statement.md)
- [如何：声明结构](../data-types/how-to-declare-a-structure.md)
- [隐式转换和显式转换](../data-types/implicit-and-explicit-conversions.md)
- [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)
