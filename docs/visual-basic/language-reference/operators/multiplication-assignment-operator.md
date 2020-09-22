---
title: '*= 运算符'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 4e2f18fb2b8110d97390390b3934d3c1761baa35
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866732"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e6300-102">\*= 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6300-102">\*= Operator (Visual Basic)</span></span>

<span data-ttu-id="e6300-103">将变量或属性的值乘以表达式的值，并将结果赋给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="e6300-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6300-104">语法</span><span class="sxs-lookup"><span data-stu-id="e6300-104">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="e6300-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="e6300-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="e6300-106">必需。</span><span class="sxs-lookup"><span data-stu-id="e6300-106">Required.</span></span> <span data-ttu-id="e6300-107">任何数值变量或属性。</span><span class="sxs-lookup"><span data-stu-id="e6300-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="e6300-108">必需。</span><span class="sxs-lookup"><span data-stu-id="e6300-108">Required.</span></span> <span data-ttu-id="e6300-109">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="e6300-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6300-110">备注</span><span class="sxs-lookup"><span data-stu-id="e6300-110">Remarks</span></span>  

 <span data-ttu-id="e6300-111">运算符左侧的元素 `*=` 可以是简单的标量变量、属性或数组的元素。</span><span class="sxs-lookup"><span data-stu-id="e6300-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="e6300-112">变量或属性不能是 [只读](../modifiers/readonly.md)的。</span><span class="sxs-lookup"><span data-stu-id="e6300-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="e6300-113">`*=`运算符首先将运算符右侧 (的表达式的值乘以运算符) 左侧的变量或属性 (的值) 的值进行乘运算。</span><span class="sxs-lookup"><span data-stu-id="e6300-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="e6300-114">然后，运算符将该操作的结果赋给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="e6300-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e6300-115">重载</span><span class="sxs-lookup"><span data-stu-id="e6300-115">Overloading</span></span>  

 <span data-ttu-id="e6300-116">[\* 运算符](multiplication-operator.md)可*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="e6300-116">The [\* Operator](multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e6300-117">重载 `*` 运算符会影响运算符的行为 `*=` 。</span><span class="sxs-lookup"><span data-stu-id="e6300-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="e6300-118">如果你的代码 `*=` 在重载的类或结构上使用 `*` ，请确保你了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="e6300-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e6300-119">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="e6300-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6300-120">示例</span><span class="sxs-lookup"><span data-stu-id="e6300-120">Example</span></span>  

 <span data-ttu-id="e6300-121">下面的示例使用 `*=` 运算符将一个变量乘以 `Integer` 第二个变量，并将结果赋给第一个变量。</span><span class="sxs-lookup"><span data-stu-id="e6300-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e6300-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6300-122">See also</span></span>

- [<span data-ttu-id="e6300-123">\* 运算符</span><span class="sxs-lookup"><span data-stu-id="e6300-123">\* Operator</span></span>](multiplication-operator.md)
- [<span data-ttu-id="e6300-124">赋值运算符</span><span class="sxs-lookup"><span data-stu-id="e6300-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="e6300-125">算术运算符</span><span class="sxs-lookup"><span data-stu-id="e6300-125">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="e6300-126">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="e6300-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="e6300-127">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="e6300-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="e6300-128">语句</span><span class="sxs-lookup"><span data-stu-id="e6300-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
