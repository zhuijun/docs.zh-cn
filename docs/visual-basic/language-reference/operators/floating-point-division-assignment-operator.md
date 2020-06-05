---
title: /= 运算符
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 48ae78630aa66ad804d539f88524c456cf805889
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371240"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="05239-102">/= 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05239-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="05239-103">将变量或属性的值除以表达式的值，并将浮点结果赋给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="05239-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05239-104">语法</span><span class="sxs-lookup"><span data-stu-id="05239-104">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="05239-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="05239-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="05239-106">必需。</span><span class="sxs-lookup"><span data-stu-id="05239-106">Required.</span></span> <span data-ttu-id="05239-107">任何数值变量或属性。</span><span class="sxs-lookup"><span data-stu-id="05239-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="05239-108">必需。</span><span class="sxs-lookup"><span data-stu-id="05239-108">Required.</span></span> <span data-ttu-id="05239-109">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="05239-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05239-110">备注</span><span class="sxs-lookup"><span data-stu-id="05239-110">Remarks</span></span>  
 <span data-ttu-id="05239-111">运算符左侧的元素 `/=` 可以是简单的标量变量、属性或数组的元素。</span><span class="sxs-lookup"><span data-stu-id="05239-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="05239-112">变量或属性不能是[只读](../modifiers/readonly.md)的。</span><span class="sxs-lookup"><span data-stu-id="05239-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="05239-113">`/=`运算符首先将变量或属性（位于运算符左侧）的值除以表达式的值（在运算符的右侧），这就是。</span><span class="sxs-lookup"><span data-stu-id="05239-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="05239-114">然后，运算符将该操作的浮点结果分配给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="05239-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="05239-115">此语句将值赋 `Double` 给左侧的变量或属性。</span><span class="sxs-lookup"><span data-stu-id="05239-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="05239-116">如果 `Option Strict` 为 `On` ，则 `variableorproperty` 必须为 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="05239-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="05239-117">如果 `Option Strict` 为 `Off` ，Visual Basic 将执行隐式转换，并将生成的值分配给 `variableorproperty` ，并在运行时出现错误。</span><span class="sxs-lookup"><span data-stu-id="05239-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="05239-118">有关详细信息，请参阅[扩大和收缩转换](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和[Option Strict 语句](../statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="05239-118">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="05239-119">重载</span><span class="sxs-lookup"><span data-stu-id="05239-119">Overloading</span></span>  
 <span data-ttu-id="05239-120">[/运算符（Visual Basic）](floating-point-division-operator.md)可以*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="05239-120">The [/ Operator (Visual Basic)](floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="05239-121">重载 `/` 运算符会影响运算符的行为 `/=` 。</span><span class="sxs-lookup"><span data-stu-id="05239-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="05239-122">如果你的代码 `/=` 在重载的类或结构上使用 `/` ，请确保你了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="05239-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="05239-123">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="05239-123">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05239-124">示例</span><span class="sxs-lookup"><span data-stu-id="05239-124">Example</span></span>  
 <span data-ttu-id="05239-125">下面的示例使用 `/=` 运算符将一个变量除以 `Integer` 第二个变量，并将商赋给第一个变量。</span><span class="sxs-lookup"><span data-stu-id="05239-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="05239-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05239-126">See also</span></span>

- [<span data-ttu-id="05239-127">/ 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05239-127">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="05239-128">\\= 运算符</span><span class="sxs-lookup"><span data-stu-id="05239-128">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="05239-129">赋值运算符</span><span class="sxs-lookup"><span data-stu-id="05239-129">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="05239-130">算术运算符</span><span class="sxs-lookup"><span data-stu-id="05239-130">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="05239-131">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="05239-131">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="05239-132">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="05239-132">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="05239-133">语句</span><span class="sxs-lookup"><span data-stu-id="05239-133">Statements</span></span>](../../programming-guide/language-features/statements.md)
