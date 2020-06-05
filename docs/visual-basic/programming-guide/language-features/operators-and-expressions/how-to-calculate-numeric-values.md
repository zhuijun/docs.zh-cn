---
title: 如何：计算数值
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: 94b02693f308dcfcfa6983f2750a26d9d419f7be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403454"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>如何：计算数值 (Visual Basic)
您可以通过使用数值表达式来计算数字值。 *数值表达式*是一种表达式，其中包含表示数值的文本、常量和变量，以及对这些值进行操作的运算符。  
  
## <a name="calculating-numeric-values"></a>计算数值  
  
#### <a name="to-calculate-a-numeric-value"></a>计算数值  
  
- 将一个或多个数值文本、常量和变量合并为数值表达式。 下面的示例显示了一些有效的数值表达式。  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     前三行显示文本、常量和变量。 每个窗体本身构成有效的数值表达式。 最后一行显示了包含两个文字的变量的组合。  
  
     请注意，数值表达式本身不能构成完整的 Visual Basic 语句。 必须使用表达式作为完整语句的一部分。  
  
#### <a name="to-store-a-numeric-value"></a>存储数值  
  
- 可以使用赋值语句将数值表达式表示的值分配给变量，如下例所示。  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     在前面的示例中，相等运算符（）右侧的表达式的值 `=` 被分配给 `j` 运算符左侧的变量，因此 `j` 计算结果为276。  
  
     有关详细信息，请参阅[语句](../../../language-reference/statements/index.md)。  
  
## <a name="multiple-operators"></a>多个运算符  
 如果数值表达式包含多个运算符，则计算它们的顺序取决于运算符优先级的规则。 若要覆盖运算符优先级的规则，请将表达式括在括号中，如上面的示例所示：首先计算括起来的表达式。  
  
#### <a name="to-override-normal-operator-precedence"></a>覆盖普通运算符优先级  
  
- 使用括号将首先要执行的操作括起来。 下面的示例显示了两个不同的结果，它们具有相同的操作数和运算符。  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     在前面的示例中，的计算 `j` 首先执行加法运算符（ `+` ），这是因为绕 `(67 + i)` 重写 normal 优先级，赋给的值 `j` 为276（4倍69）。 的计算 `k` 按其正常优先级（之前）执行运算符 `*` `+` ，分配给的值 `k` 为270（268 + 2）。  
  
     有关详细信息，请参阅[Visual Basic 中的运算符优先级](../../../language-reference/operators/operator-precedence.md)。  
  
## <a name="see-also"></a>另请参阅

- [运算符和表达式](index.md)
- [值的比较](value-comparisons.md)
- [语句](../../../language-reference/statements/index.md)
- [Visual Basic 中的运算符优先级](../../../language-reference/operators/operator-precedence.md)
- [算术运算符](../../../language-reference/operators/arithmetic-operators.md)
- [运算符的有效组合](efficient-combination-of-operators.md)
