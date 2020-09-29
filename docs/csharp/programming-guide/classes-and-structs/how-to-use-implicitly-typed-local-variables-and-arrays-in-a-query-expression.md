---
title: 如何在查询表达式中使用隐式类型的局部变量和数组（C# 编程指南）
description: 使用 C# 中的隐式类型本地变量，让编译器确定本地变量的类型。 必须使用它们来存储匿名类型。
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: fcfb154f6abd90033ae57bb1543d0c891f6c5999
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174194"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a><span data-ttu-id="adb11-104">如何在查询表达式中使用隐式类型的局部变量和数组（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="adb11-104">How to use implicitly typed local variables and arrays in a query expression (C# Programming Guide)</span></span>

<span data-ttu-id="adb11-105">每当需要编译器确定本地变量类型时，均可使用隐式类型本地变量。</span><span class="sxs-lookup"><span data-stu-id="adb11-105">You can use implicitly typed local variables whenever you want the compiler to determine the type of a local variable.</span></span> <span data-ttu-id="adb11-106">必须使用隐式类型本地变量来存储匿名类型，匿名类型通常用于查询表达式中。</span><span class="sxs-lookup"><span data-stu-id="adb11-106">You must use implicitly typed local variables to store anonymous types, which are often used in query expressions.</span></span> <span data-ttu-id="adb11-107">以下示例说明了在查询中可以使用和必须使用隐式类型本地变量的情况。</span><span class="sxs-lookup"><span data-stu-id="adb11-107">The following examples illustrate both optional and required uses of implicitly typed local variables in queries.</span></span>  
  
 <span data-ttu-id="adb11-108">隐式类型本地变量使用 [var](../../language-reference/keywords/var.md) 上下文关键字进行声明。</span><span class="sxs-lookup"><span data-stu-id="adb11-108">Implicitly typed local variables are declared by using the [var](../../language-reference/keywords/var.md) contextual keyword.</span></span> <span data-ttu-id="adb11-109">有关详细信息，请参阅[隐式类型本地变量](./implicitly-typed-local-variables.md)和[隐式类型数组](../arrays/implicitly-typed-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="adb11-109">For more information, see [Implicitly Typed Local Variables](./implicitly-typed-local-variables.md) and [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="adb11-110">示例</span><span class="sxs-lookup"><span data-stu-id="adb11-110">Example</span></span>  

 <span data-ttu-id="adb11-111">以下示例演示必须使用 `var` 关键字的常见情景：用于生成一系列匿名类型的查询表达式。</span><span class="sxs-lookup"><span data-stu-id="adb11-111">The following example shows a common scenario in which the `var` keyword is required: a query expression that produces a sequence of anonymous types.</span></span> <span data-ttu-id="adb11-112">在此情景中，必须使用 `var` 隐式类型化 `foreach` 语句中的查询变量和迭代变量，因为你无权访问匿名类型的类型名称。</span><span class="sxs-lookup"><span data-stu-id="adb11-112">In this scenario, both the query variable and the iteration variable in the `foreach` statement must be implicitly typed by using `var` because you do not have access to a type name for the anonymous type.</span></span> <span data-ttu-id="adb11-113">有关匿名类型的详细信息，请参阅[匿名类型](./anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="adb11-113">For more information about anonymous types, see [Anonymous Types](./anonymous-types.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="adb11-114">示例</span><span class="sxs-lookup"><span data-stu-id="adb11-114">Example</span></span>  

 <span data-ttu-id="adb11-115">虽然以下示例在类似的情景中使用 `var` 关键字，但使用 `var` 是可选项。</span><span class="sxs-lookup"><span data-stu-id="adb11-115">The following example uses the `var` keyword in a situation that is similar, but in which the use of `var` is optional.</span></span> <span data-ttu-id="adb11-116">因为 `student.LastName` 是字符串，所以执行查询将返回一系列字符串。</span><span class="sxs-lookup"><span data-stu-id="adb11-116">Because `student.LastName` is a string, execution of the query returns a sequence of strings.</span></span> <span data-ttu-id="adb11-117">因此，`queryID` 的类型可声明为 `System.Collections.Generic.IEnumerable<string>`，而不是 `var`。</span><span class="sxs-lookup"><span data-stu-id="adb11-117">Therefore, the type of `queryID` could be declared as `System.Collections.Generic.IEnumerable<string>` instead of `var`.</span></span> <span data-ttu-id="adb11-118">为方便起见，请使用关键字 `var`。</span><span class="sxs-lookup"><span data-stu-id="adb11-118">Keyword `var` is used for convenience.</span></span> <span data-ttu-id="adb11-119">在示例中，虽然 `foreach` 语句中的迭代变量被显式类型化为字符串，但可改为使用 `var` 对其进行声明。</span><span class="sxs-lookup"><span data-stu-id="adb11-119">In the example, the iteration variable in the `foreach` statement is explicitly typed as a string, but it could instead be declared by using `var`.</span></span> <span data-ttu-id="adb11-120">因为迭代变量的类型不是匿名类型，因此使用 `var` 是可选项，而不是必需项。</span><span class="sxs-lookup"><span data-stu-id="adb11-120">Because the type of the iteration variable is not an anonymous type, the use of `var` is an option, not a requirement.</span></span> <span data-ttu-id="adb11-121">请记住，`var` 本身不是类型，而是发送给编译器用于推断和分配类型的指令。</span><span class="sxs-lookup"><span data-stu-id="adb11-121">Remember, `var` itself is not a type, but an instruction to the compiler to infer and assign the type.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a><span data-ttu-id="adb11-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="adb11-122">See also</span></span>

- [<span data-ttu-id="adb11-123">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="adb11-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="adb11-124">扩展方法</span><span class="sxs-lookup"><span data-stu-id="adb11-124">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="adb11-125">LINQ（语言集成查询）</span><span class="sxs-lookup"><span data-stu-id="adb11-125">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="adb11-126">var</span><span class="sxs-lookup"><span data-stu-id="adb11-126">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="adb11-127">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="adb11-127">LINQ in C#</span></span>](../../linq/index.md)
