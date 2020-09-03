---
description: var - C# 参考
title: var - C# 参考
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 303a880a54a79e50515060e0ea28e8d021fa1b76
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141707"
---
# <a name="var-c-reference"></a><span data-ttu-id="bb8fc-103">var（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="bb8fc-103">var (C# Reference)</span></span>

<span data-ttu-id="bb8fc-104">从 Visual C# 3.0 开始，在方法范围内声明的变量可以具有隐式“类型”`var`。</span><span class="sxs-lookup"><span data-stu-id="bb8fc-104">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="bb8fc-105">隐式类型本地变量为强类型，就像用户已经自行声明该类型，但编译器决定类型一样。</span><span class="sxs-lookup"><span data-stu-id="bb8fc-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="bb8fc-106">`i` 的以下两个声明在功能上是等效的：</span><span class="sxs-lookup"><span data-stu-id="bb8fc-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="bb8fc-107">有关详细信息，请参阅[隐式类型的局部变量](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)和 [LINQ 查询操作中的类型关系](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="bb8fc-107">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bb8fc-108">在启用可为空引用类型的情况下使用 `var` 时，即使表达式类型不可为空，也始终表示可为空引用类型。</span><span class="sxs-lookup"><span data-stu-id="bb8fc-108">When `var` is used with nullable reference types enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

## <a name="example"></a><span data-ttu-id="bb8fc-109">示例</span><span class="sxs-lookup"><span data-stu-id="bb8fc-109">Example</span></span>

<span data-ttu-id="bb8fc-110">下面的示例演示两个查询表达式。</span><span class="sxs-lookup"><span data-stu-id="bb8fc-110">The following example shows two query expressions.</span></span> <span data-ttu-id="bb8fc-111">在第一个表达式中，`var` 的使用是允许的，但不是必需的，因为查询结果的类型可以明确表述为 `IEnumerable<string>`。</span><span class="sxs-lookup"><span data-stu-id="bb8fc-111">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="bb8fc-112">不过，在第二个表达式中，`var` 允许结果是一系列匿名类型，且相应类型的名称只可供编译器本身访问。</span><span class="sxs-lookup"><span data-stu-id="bb8fc-112">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="bb8fc-113">如果使用 `var`，便无法为结果新建类。</span><span class="sxs-lookup"><span data-stu-id="bb8fc-113">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="bb8fc-114">请注意，在示例 #2 中，`foreach` 迭代变量 `item` 必须也为隐式类型。</span><span class="sxs-lookup"><span data-stu-id="bb8fc-114">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="bb8fc-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="bb8fc-115">See also</span></span>

- [<span data-ttu-id="bb8fc-116">C# 参考</span><span class="sxs-lookup"><span data-stu-id="bb8fc-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bb8fc-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="bb8fc-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bb8fc-118">隐式类型的局部变量</span><span class="sxs-lookup"><span data-stu-id="bb8fc-118">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
