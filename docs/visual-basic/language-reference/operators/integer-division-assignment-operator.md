---
title: '\= 运算符'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: a546d8b0c9b3852386970f80d3da96794da2351c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370942"
---
# <a name="-operator"></a><span data-ttu-id="e6f66-102">\\= 运算符</span><span class="sxs-lookup"><span data-stu-id="e6f66-102">\\= Operator</span></span>
<span data-ttu-id="e6f66-103">将变量或属性的值除以表达式的值，并将整数结果赋给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="e6f66-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f66-104">语法</span><span class="sxs-lookup"><span data-stu-id="e6f66-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="e6f66-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="e6f66-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="e6f66-106">必需。</span><span class="sxs-lookup"><span data-stu-id="e6f66-106">Required.</span></span> <span data-ttu-id="e6f66-107">任何数值变量或属性。</span><span class="sxs-lookup"><span data-stu-id="e6f66-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="e6f66-108">必需。</span><span class="sxs-lookup"><span data-stu-id="e6f66-108">Required.</span></span> <span data-ttu-id="e6f66-109">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="e6f66-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6f66-110">备注</span><span class="sxs-lookup"><span data-stu-id="e6f66-110">Remarks</span></span>  
 <span data-ttu-id="e6f66-111">运算符左侧的元素 `\=` 可以是简单的标量变量、属性或数组的元素。</span><span class="sxs-lookup"><span data-stu-id="e6f66-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="e6f66-112">变量或属性不能是[只读](../modifiers/readonly.md)的。</span><span class="sxs-lookup"><span data-stu-id="e6f66-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="e6f66-113">`\=`运算符将变量或属性的值除以其右侧的值，并将整数结果分配给其左侧的变量或属性</span><span class="sxs-lookup"><span data-stu-id="e6f66-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="e6f66-114">有关整数除法的详细信息，请参阅[\ 运算符（Visual Basic）](integer-division-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f66-114">For further information on integer division, see [\ Operator (Visual Basic)](integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e6f66-115">重载</span><span class="sxs-lookup"><span data-stu-id="e6f66-115">Overloading</span></span>  
 <span data-ttu-id="e6f66-116">`\`运算符可以*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="e6f66-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e6f66-117">重载 `\` 运算符会影响运算符的行为 `\=` 。</span><span class="sxs-lookup"><span data-stu-id="e6f66-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="e6f66-118">如果你的代码 `\=` 在重载的类或结构上使用 `\` ，请确保你了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="e6f66-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e6f66-119">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f66-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6f66-120">示例</span><span class="sxs-lookup"><span data-stu-id="e6f66-120">Example</span></span>  
 <span data-ttu-id="e6f66-121">下面的示例使用 `\=` 运算符将一个变量除以 `Integer` 第二个变量，并将该整数结果赋给第一个变量。</span><span class="sxs-lookup"><span data-stu-id="e6f66-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="e6f66-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6f66-122">See also</span></span>

- [<span data-ttu-id="e6f66-123">\ 运算符（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e6f66-123">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="e6f66-124">/= 运算符（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e6f66-124">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="e6f66-125">赋值运算符</span><span class="sxs-lookup"><span data-stu-id="e6f66-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="e6f66-126">算术运算符</span><span class="sxs-lookup"><span data-stu-id="e6f66-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="e6f66-127">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="e6f66-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="e6f66-128">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="e6f66-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="e6f66-129">语句</span><span class="sxs-lookup"><span data-stu-id="e6f66-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
