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
ms.openlocfilehash: 452a8392b46f0c25b6ad2a8a30c51071f2ae1d93
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071711"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="4733e-102">如何：计算数值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4733e-102">How to: Calculate Numeric Values (Visual Basic)</span></span>

<span data-ttu-id="4733e-103">您可以通过使用数值表达式来计算数字值。</span><span class="sxs-lookup"><span data-stu-id="4733e-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="4733e-104">*数值表达式*是一种表达式，其中包含表示数值的文本、常量和变量，以及对这些值进行操作的运算符。</span><span class="sxs-lookup"><span data-stu-id="4733e-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="4733e-105">计算数值</span><span class="sxs-lookup"><span data-stu-id="4733e-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="4733e-106">计算数值</span><span class="sxs-lookup"><span data-stu-id="4733e-106">To calculate a numeric value</span></span>  
  
- <span data-ttu-id="4733e-107">将一个或多个数值文本、常量和变量合并为数值表达式。</span><span class="sxs-lookup"><span data-stu-id="4733e-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="4733e-108">下面的示例显示了一些有效的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="4733e-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="4733e-109">前三行显示文本、常量和变量。</span><span class="sxs-lookup"><span data-stu-id="4733e-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="4733e-110">每个窗体本身构成有效的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="4733e-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="4733e-111">最后一行显示了包含两个文字的变量的组合。</span><span class="sxs-lookup"><span data-stu-id="4733e-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="4733e-112">请注意，数值表达式本身不能构成完整的 Visual Basic 语句。</span><span class="sxs-lookup"><span data-stu-id="4733e-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="4733e-113">必须使用表达式作为完整语句的一部分。</span><span class="sxs-lookup"><span data-stu-id="4733e-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="4733e-114">存储数值</span><span class="sxs-lookup"><span data-stu-id="4733e-114">To store a numeric value</span></span>  
  
- <span data-ttu-id="4733e-115">可以使用赋值语句将数值表达式表示的值分配给变量，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="4733e-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     <span data-ttu-id="4733e-116">在前面的示例中，相等运算符 () 右侧的表达式的值 `=` 将分配给 `j` 运算符左侧的变量，因此 `j` 计算结果为276。</span><span class="sxs-lookup"><span data-stu-id="4733e-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="4733e-117">有关详细信息，请参阅[语句](../../../language-reference/statements/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4733e-117">For more information, see [Statements](../../../language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="4733e-118">多个运算符</span><span class="sxs-lookup"><span data-stu-id="4733e-118">Multiple Operators</span></span>  

 <span data-ttu-id="4733e-119">如果数值表达式包含多个运算符，则计算它们的顺序取决于运算符优先级的规则。</span><span class="sxs-lookup"><span data-stu-id="4733e-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="4733e-120">若要覆盖运算符优先级的规则，请将表达式括在括号中，如上面的示例所示：首先计算括起来的表达式。</span><span class="sxs-lookup"><span data-stu-id="4733e-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="4733e-121">覆盖普通运算符优先级</span><span class="sxs-lookup"><span data-stu-id="4733e-121">To override normal operator precedence</span></span>  
  
- <span data-ttu-id="4733e-122">使用括号将首先要执行的操作括起来。</span><span class="sxs-lookup"><span data-stu-id="4733e-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="4733e-123">下面的示例显示了两个不同的结果，它们具有相同的操作数和运算符。</span><span class="sxs-lookup"><span data-stu-id="4733e-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     <span data-ttu-id="4733e-124">在前面的示例中，的计算 `j` 首先 () 执行加法运算符 `+` ，因为围绕 `(67 + i)` 替代普通优先级，赋给的值 `j` 为 276 (4 次 69) 。</span><span class="sxs-lookup"><span data-stu-id="4733e-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="4733e-125">的计算 `k` 在) 之前以其正常优先级 (执行 `*` 运算符 `+` ，并且分配给的值 `k` 为 270 (268 + 2) 。</span><span class="sxs-lookup"><span data-stu-id="4733e-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="4733e-126">有关详细信息，请参阅 [Visual Basic 中的运算符优先级](../../../language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="4733e-126">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4733e-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="4733e-127">See also</span></span>

- [<span data-ttu-id="4733e-128">运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="4733e-128">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="4733e-129">值的比较</span><span class="sxs-lookup"><span data-stu-id="4733e-129">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="4733e-130">语句</span><span class="sxs-lookup"><span data-stu-id="4733e-130">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="4733e-131">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="4733e-131">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="4733e-132">算术运算符</span><span class="sxs-lookup"><span data-stu-id="4733e-132">Arithmetic Operators</span></span>](../../../language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="4733e-133">运算符的有效组合</span><span class="sxs-lookup"><span data-stu-id="4733e-133">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
