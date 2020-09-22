---
title: DirectCast 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 7b070b8eba240440821f7984a9336c2ecaf61706
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867089"
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="2839c-102">DirectCast 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2839c-102">DirectCast Operator (Visual Basic)</span></span>

<span data-ttu-id="2839c-103">引入基于继承或实现的类型转换操作。</span><span class="sxs-lookup"><span data-stu-id="2839c-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2839c-104">备注</span><span class="sxs-lookup"><span data-stu-id="2839c-104">Remarks</span></span>  

 <span data-ttu-id="2839c-105">`DirectCast` 不使用 Visual Basic 运行时帮助器例程进行转换，因此，它可以提供比 `CType` 转换到数据类型和从数据类型转换时更好的性能 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="2839c-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="2839c-106">关键字的使用 `DirectCast` 方式类似于使用 [CType 函数](../functions/ctype-function.md) 和 [TryCast 运算符](trycast-operator.md) 关键字。</span><span class="sxs-lookup"><span data-stu-id="2839c-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../functions/ctype-function.md) and the [TryCast Operator](trycast-operator.md) keyword.</span></span> <span data-ttu-id="2839c-107">提供表达式作为第一个参数，并提供一个类型以将其转换为第二个参数。</span><span class="sxs-lookup"><span data-stu-id="2839c-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="2839c-108">`DirectCast` 需要两个自变量的数据类型之间的继承关系或实现关系。</span><span class="sxs-lookup"><span data-stu-id="2839c-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="2839c-109">这意味着一个类型必须从继承或实现另一个类型。</span><span class="sxs-lookup"><span data-stu-id="2839c-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="2839c-110">错误和失败</span><span class="sxs-lookup"><span data-stu-id="2839c-110">Errors and Failures</span></span>  

 <span data-ttu-id="2839c-111">`DirectCast` 如果检测到不存在继承或实现关系，则会生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="2839c-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="2839c-112">但缺少编译器错误并不能保证成功转换。</span><span class="sxs-lookup"><span data-stu-id="2839c-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="2839c-113">如果所需的转换是收缩转换，则可能会在运行时失败。</span><span class="sxs-lookup"><span data-stu-id="2839c-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="2839c-114">如果发生这种情况，运行时会引发 <xref:System.InvalidCastException> 错误。</span><span class="sxs-lookup"><span data-stu-id="2839c-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="2839c-115">转换关键字</span><span class="sxs-lookup"><span data-stu-id="2839c-115">Conversion Keywords</span></span>  

 <span data-ttu-id="2839c-116">下面是类型转换关键字的比较。</span><span class="sxs-lookup"><span data-stu-id="2839c-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="2839c-117">关键字</span><span class="sxs-lookup"><span data-stu-id="2839c-117">Keyword</span></span>|<span data-ttu-id="2839c-118">数据类型</span><span class="sxs-lookup"><span data-stu-id="2839c-118">Data types</span></span>|<span data-ttu-id="2839c-119">参数关系</span><span class="sxs-lookup"><span data-stu-id="2839c-119">Argument relationship</span></span>|<span data-ttu-id="2839c-120">运行时失败</span><span class="sxs-lookup"><span data-stu-id="2839c-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="2839c-121">CType Function</span><span class="sxs-lookup"><span data-stu-id="2839c-121">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="2839c-122">任何数据类型</span><span class="sxs-lookup"><span data-stu-id="2839c-122">Any data types</span></span>|<span data-ttu-id="2839c-123">必须在这两种数据类型之间定义扩大转换或收缩转换</span><span class="sxs-lookup"><span data-stu-id="2839c-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="2839c-124">却 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="2839c-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="2839c-125">任何数据类型</span><span class="sxs-lookup"><span data-stu-id="2839c-125">Any data types</span></span>|<span data-ttu-id="2839c-126">一个类型必须继承自或实现另一个类型</span><span class="sxs-lookup"><span data-stu-id="2839c-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="2839c-127">却 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="2839c-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="2839c-128">TryCast 运算符</span><span class="sxs-lookup"><span data-stu-id="2839c-128">TryCast Operator</span></span>](trycast-operator.md)|<span data-ttu-id="2839c-129">仅引用类型</span><span class="sxs-lookup"><span data-stu-id="2839c-129">Reference types only</span></span>|<span data-ttu-id="2839c-130">一个类型必须继承自或实现另一个类型</span><span class="sxs-lookup"><span data-stu-id="2839c-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="2839c-131">不返回 [任何内容](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="2839c-131">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2839c-132">示例</span><span class="sxs-lookup"><span data-stu-id="2839c-132">Example</span></span>  

 <span data-ttu-id="2839c-133">下面的示例演示了的两个用法 `DirectCast` ，一个在运行时失败，另一个成功。</span><span class="sxs-lookup"><span data-stu-id="2839c-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 <span data-ttu-id="2839c-134">在前面的示例中，的运行时类型 `q` 为 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="2839c-134">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="2839c-135">`CType` 成功 `Double` ，因为可以转换为 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="2839c-135">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="2839c-136">但是，第一次 `DirectCast` 在运行时失败，因为的运行时类型 `Double` 与没有继承关系 `Integer` ，即使存在转换也是如此。</span><span class="sxs-lookup"><span data-stu-id="2839c-136">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="2839c-137">第二个 `DirectCast` 成功，因为它从类型转换 <xref:System.Windows.Forms.Form> 为类型 <xref:System.Windows.Forms.Control> ，后者 <xref:System.Windows.Forms.Form> 继承自。</span><span class="sxs-lookup"><span data-stu-id="2839c-137">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2839c-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2839c-138">See also</span></span>

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2839c-139">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="2839c-139">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="2839c-140">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="2839c-140">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
