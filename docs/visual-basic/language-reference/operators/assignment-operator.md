---
title: = 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: eccea0b43564a4980778c9d1a5b8f9a8c2a9207d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874820"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="33d32-102">= 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d32-102">= Operator (Visual Basic)</span></span>

<span data-ttu-id="33d32-103">为变量或属性赋值。</span><span class="sxs-lookup"><span data-stu-id="33d32-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33d32-104">语法</span><span class="sxs-lookup"><span data-stu-id="33d32-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="33d32-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="33d32-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="33d32-106">任何可写的变量或任何属性。</span><span class="sxs-lookup"><span data-stu-id="33d32-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="33d32-107">任何文本、常量或表达式。</span><span class="sxs-lookup"><span data-stu-id="33d32-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33d32-108">备注</span><span class="sxs-lookup"><span data-stu-id="33d32-108">Remarks</span></span>  

 <span data-ttu-id="33d32-109">等于符号 () 左侧的元素 `=` 可以是简单的标量变量、属性或数组元素。</span><span class="sxs-lookup"><span data-stu-id="33d32-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="33d32-110">变量或属性不能是 [只读](../modifiers/readonly.md)的。</span><span class="sxs-lookup"><span data-stu-id="33d32-110">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="33d32-111">`=`运算符将其右侧的值赋值给其左侧的变量或属性。</span><span class="sxs-lookup"><span data-stu-id="33d32-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33d32-112">`=`运算符也用作比较运算符。</span><span class="sxs-lookup"><span data-stu-id="33d32-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="33d32-113">有关详细信息，请参阅 [比较运算符](comparison-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="33d32-113">For details, see [Comparison Operators](comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="33d32-114">重载</span><span class="sxs-lookup"><span data-stu-id="33d32-114">Overloading</span></span>  

 <span data-ttu-id="33d32-115">`=`运算符只能作为关系比较运算符重载，而不能作为赋值运算符重载。</span><span class="sxs-lookup"><span data-stu-id="33d32-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="33d32-116">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="33d32-116">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33d32-117">示例</span><span class="sxs-lookup"><span data-stu-id="33d32-117">Example</span></span>  

 <span data-ttu-id="33d32-118">下面的示例演示了赋值运算符。</span><span class="sxs-lookup"><span data-stu-id="33d32-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="33d32-119">右侧的值将分配给左侧的变量。</span><span class="sxs-lookup"><span data-stu-id="33d32-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="33d32-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33d32-120">See also</span></span>

- [<span data-ttu-id="33d32-121">&= 运算符</span><span class="sxs-lookup"><span data-stu-id="33d32-121">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="33d32-122">\* = 运算符</span><span class="sxs-lookup"><span data-stu-id="33d32-122">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="33d32-123">+ = 运算符</span><span class="sxs-lookup"><span data-stu-id="33d32-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="33d32-124">-= 运算符 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="33d32-124">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="33d32-125">/= 运算符 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="33d32-125">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="33d32-126">\\= 运算符</span><span class="sxs-lookup"><span data-stu-id="33d32-126">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="33d32-127">^ = 运算符</span><span class="sxs-lookup"><span data-stu-id="33d32-127">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="33d32-128">语句</span><span class="sxs-lookup"><span data-stu-id="33d32-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="33d32-129">比较运算符</span><span class="sxs-lookup"><span data-stu-id="33d32-129">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="33d32-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="33d32-130">ReadOnly</span></span>](../modifiers/readonly.md)
- [<span data-ttu-id="33d32-131">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="33d32-131">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
