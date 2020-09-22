---
title: ^= 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: a956ffdaa3456ed09443f25c3383b6aab52fb5bf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867055"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="34d3e-102">^= 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34d3e-102">^= Operator (Visual Basic)</span></span>

<span data-ttu-id="34d3e-103">将变量或属性的值提升为表达式的幂，并将结果赋回给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="34d3e-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34d3e-104">语法</span><span class="sxs-lookup"><span data-stu-id="34d3e-104">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="34d3e-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="34d3e-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="34d3e-106">必需。</span><span class="sxs-lookup"><span data-stu-id="34d3e-106">Required.</span></span> <span data-ttu-id="34d3e-107">任何数值变量或属性。</span><span class="sxs-lookup"><span data-stu-id="34d3e-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="34d3e-108">必需。</span><span class="sxs-lookup"><span data-stu-id="34d3e-108">Required.</span></span> <span data-ttu-id="34d3e-109">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="34d3e-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34d3e-110">备注</span><span class="sxs-lookup"><span data-stu-id="34d3e-110">Remarks</span></span>  

 <span data-ttu-id="34d3e-111">运算符左侧的元素 `^=` 可以是简单的标量变量、属性或数组的元素。</span><span class="sxs-lookup"><span data-stu-id="34d3e-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="34d3e-112">变量或属性不能是 [只读](../modifiers/readonly.md)的。</span><span class="sxs-lookup"><span data-stu-id="34d3e-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="34d3e-113">`^=`运算符首先在运算符的左侧引发变量或属性 (的值) ，以使运算符) 右侧 (表达式的值的的值的幂。</span><span class="sxs-lookup"><span data-stu-id="34d3e-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="34d3e-114">然后，运算符将该操作的结果赋给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="34d3e-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="34d3e-115">Visual Basic 总是对 [Double 数据类型](../data-types/double-data-type.md)执行幂运算。</span><span class="sxs-lookup"><span data-stu-id="34d3e-115">Visual Basic always performs exponentiation in the [Double Data Type](../data-types/double-data-type.md).</span></span> <span data-ttu-id="34d3e-116">将任意不同类型的操作数转换为 `Double` ，并且结果始终为 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="34d3e-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="34d3e-117">的值 `expression` 可以是小数、负数或同时为两者。</span><span class="sxs-lookup"><span data-stu-id="34d3e-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="34d3e-118">重载</span><span class="sxs-lookup"><span data-stu-id="34d3e-118">Overloading</span></span>  

 <span data-ttu-id="34d3e-119">[^ 运算符](exponentiation-operator.md)可*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="34d3e-119">The [^ Operator](exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="34d3e-120">重载 `^` 运算符会影响运算符的行为 `^=` 。</span><span class="sxs-lookup"><span data-stu-id="34d3e-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="34d3e-121">如果你的代码 `^=` 在重载的类或结构上使用 `^` ，请确保你了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="34d3e-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="34d3e-122">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="34d3e-122">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34d3e-123">示例</span><span class="sxs-lookup"><span data-stu-id="34d3e-123">Example</span></span>  

 <span data-ttu-id="34d3e-124">下面的示例使用 `^=` 运算符将一个变量的值提升 `Integer` 为第二个变量的幂，并将结果赋给第一个变量。</span><span class="sxs-lookup"><span data-stu-id="34d3e-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="34d3e-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34d3e-125">See also</span></span>

- [<span data-ttu-id="34d3e-126">^ 运算符</span><span class="sxs-lookup"><span data-stu-id="34d3e-126">^ Operator</span></span>](exponentiation-operator.md)
- [<span data-ttu-id="34d3e-127">赋值运算符</span><span class="sxs-lookup"><span data-stu-id="34d3e-127">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="34d3e-128">算术运算符</span><span class="sxs-lookup"><span data-stu-id="34d3e-128">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="34d3e-129">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="34d3e-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="34d3e-130">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="34d3e-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="34d3e-131">语句</span><span class="sxs-lookup"><span data-stu-id="34d3e-131">Statements</span></span>](../../programming-guide/language-features/statements.md)
