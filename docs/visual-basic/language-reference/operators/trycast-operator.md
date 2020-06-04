---
title: TryCast 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 8f0d4f612cd5a96e0b0ab7305c41e00790613cc8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406370"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="48b43-102">TryCast 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48b43-102">TryCast Operator (Visual Basic)</span></span>
<span data-ttu-id="48b43-103">引入不引发异常的类型转换操作。</span><span class="sxs-lookup"><span data-stu-id="48b43-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48b43-104">备注</span><span class="sxs-lookup"><span data-stu-id="48b43-104">Remarks</span></span>  
 <span data-ttu-id="48b43-105">如果尝试的转换失败，则会 `CType` `DirectCast` 引发 <xref:System.InvalidCastException> 错误。</span><span class="sxs-lookup"><span data-stu-id="48b43-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="48b43-106">这会对应用程序的性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="48b43-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="48b43-107">`TryCast`不返回[任何内容](../nothing.md)，因此只需测试返回的结果，而无需处理可能出现的异常 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="48b43-107">`TryCast` returns [Nothing](../nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="48b43-108">`TryCast`关键字的使用方式与使用[CType 函数](../functions/ctype-function.md)和[DirectCast 运算符](directcast-operator.md)关键字相同。</span><span class="sxs-lookup"><span data-stu-id="48b43-108">You use the `TryCast` keyword the same way you use the [CType Function](../functions/ctype-function.md) and the [DirectCast Operator](directcast-operator.md) keyword.</span></span> <span data-ttu-id="48b43-109">提供表达式作为第一个参数，并提供一个类型以将其转换为第二个参数。</span><span class="sxs-lookup"><span data-stu-id="48b43-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="48b43-110">`TryCast`仅对引用类型（如类和接口）进行操作。</span><span class="sxs-lookup"><span data-stu-id="48b43-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="48b43-111">它需要这两个类型之间的继承关系或实现关系。</span><span class="sxs-lookup"><span data-stu-id="48b43-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="48b43-112">这意味着一个类型必须从继承或实现另一个类型。</span><span class="sxs-lookup"><span data-stu-id="48b43-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="48b43-113">错误和失败</span><span class="sxs-lookup"><span data-stu-id="48b43-113">Errors and Failures</span></span>  
 <span data-ttu-id="48b43-114">`TryCast`如果检测到不存在继承或实现关系，则会生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="48b43-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="48b43-115">但缺少编译器错误并不能保证成功转换。</span><span class="sxs-lookup"><span data-stu-id="48b43-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="48b43-116">如果所需的转换是收缩转换，则可能会在运行时失败。</span><span class="sxs-lookup"><span data-stu-id="48b43-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="48b43-117">如果发生这种情况，则不 `TryCast` 返回[任何内容](../nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="48b43-117">If this happens, `TryCast` returns [Nothing](../nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="48b43-118">转换关键字</span><span class="sxs-lookup"><span data-stu-id="48b43-118">Conversion Keywords</span></span>  
 <span data-ttu-id="48b43-119">下面是类型转换关键字的比较。</span><span class="sxs-lookup"><span data-stu-id="48b43-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="48b43-120">关键字</span><span class="sxs-lookup"><span data-stu-id="48b43-120">Keyword</span></span>|<span data-ttu-id="48b43-121">数据类型</span><span class="sxs-lookup"><span data-stu-id="48b43-121">Data types</span></span>|<span data-ttu-id="48b43-122">参数关系</span><span class="sxs-lookup"><span data-stu-id="48b43-122">Argument relationship</span></span>|<span data-ttu-id="48b43-123">运行时失败</span><span class="sxs-lookup"><span data-stu-id="48b43-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="48b43-124">CType Function</span><span class="sxs-lookup"><span data-stu-id="48b43-124">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="48b43-125">任何数据类型</span><span class="sxs-lookup"><span data-stu-id="48b43-125">Any data types</span></span>|<span data-ttu-id="48b43-126">必须在这两种数据类型之间定义扩大转换或收缩转换</span><span class="sxs-lookup"><span data-stu-id="48b43-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="48b43-127">却<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="48b43-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="48b43-128">DirectCast 运算符</span><span class="sxs-lookup"><span data-stu-id="48b43-128">DirectCast Operator</span></span>](directcast-operator.md)|<span data-ttu-id="48b43-129">任何数据类型</span><span class="sxs-lookup"><span data-stu-id="48b43-129">Any data types</span></span>|<span data-ttu-id="48b43-130">一个类型必须继承自或实现另一个类型</span><span class="sxs-lookup"><span data-stu-id="48b43-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="48b43-131">却<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="48b43-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="48b43-132">仅引用类型</span><span class="sxs-lookup"><span data-stu-id="48b43-132">Reference types only</span></span>|<span data-ttu-id="48b43-133">一个类型必须继承自或实现另一个类型</span><span class="sxs-lookup"><span data-stu-id="48b43-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="48b43-134">不返回[任何内容](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="48b43-134">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="48b43-135">示例</span><span class="sxs-lookup"><span data-stu-id="48b43-135">Example</span></span>  
 <span data-ttu-id="48b43-136">下面的示例说明如何使用 `TryCast`。</span><span class="sxs-lookup"><span data-stu-id="48b43-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="48b43-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48b43-137">See also</span></span>

- [<span data-ttu-id="48b43-138">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="48b43-138">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="48b43-139">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="48b43-139">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
