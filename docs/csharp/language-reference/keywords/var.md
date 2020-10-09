---
description: var - C# 参考
title: var - C# 参考
ms.date: 10/02/2020
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: d04bea9bcf5be726d3e81a1a53abed31f59330a0
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608707"
---
# <a name="var-c-reference"></a><span data-ttu-id="fb741-103">var（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="fb741-103">var (C# reference)</span></span>

<span data-ttu-id="fb741-104">从 C# 3.0 开始，在方法范围内声明的变量可以具有隐式“类型”`var`。</span><span class="sxs-lookup"><span data-stu-id="fb741-104">Beginning with C# 3, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="fb741-105">隐式类型本地变量为强类型，就像用户已经自行声明该类型，但编译器决定类型一样。</span><span class="sxs-lookup"><span data-stu-id="fb741-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="fb741-106">`i` 的以下两个声明在功能上是等效的：</span><span class="sxs-lookup"><span data-stu-id="fb741-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> <span data-ttu-id="fb741-107">在启用[可为空引用类型](../builtin-types/nullable-reference-types.md)的情况下使用 `var` 时，即使表达式类型不可为空，也始终表示可为空引用类型。</span><span class="sxs-lookup"><span data-stu-id="fb741-107">When `var` is used with [nullable reference types](../builtin-types/nullable-reference-types.md) enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

<span data-ttu-id="fb741-108">`var` 关键字的常见用途是用于构造函数调用表达式。</span><span class="sxs-lookup"><span data-stu-id="fb741-108">A common use of the `var` keyword is with constructor invocation expressions.</span></span> <span data-ttu-id="fb741-109">使用 `var`则不能在变量声明和对象实例化中重复类型名称，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="fb741-109">The use of `var` allows you to not repeat a type name in a variable declaration and object instantiation, as the following example shows:</span></span>

```csharp
var xs = new List<int>();
```

<span data-ttu-id="fb741-110">从 C# 9.0 开始，可以使用由目标确定类型的 [`new` 表达式](../operators/new-operator.md)作为替代方法：</span><span class="sxs-lookup"><span data-stu-id="fb741-110">Beginning with C# 9.0, you can use a target-typed [`new` expression](../operators/new-operator.md) as an alternative:</span></span>

```csharp
List<int> xs = new();
List<int>? ys = new();
```

## <a name="example"></a><span data-ttu-id="fb741-111">示例</span><span class="sxs-lookup"><span data-stu-id="fb741-111">Example</span></span>

<span data-ttu-id="fb741-112">下面的示例演示两个查询表达式。</span><span class="sxs-lookup"><span data-stu-id="fb741-112">The following example shows two query expressions.</span></span> <span data-ttu-id="fb741-113">在第一个表达式中，`var` 的使用是允许的，但不是必需的，因为查询结果的类型可以明确表述为 `IEnumerable<string>`。</span><span class="sxs-lookup"><span data-stu-id="fb741-113">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="fb741-114">不过，在第二个表达式中，`var` 允许结果是一系列匿名类型，且相应类型的名称只可供编译器本身访问。</span><span class="sxs-lookup"><span data-stu-id="fb741-114">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="fb741-115">如果使用 `var`，便无法为结果新建类。</span><span class="sxs-lookup"><span data-stu-id="fb741-115">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="fb741-116">请注意，在示例 #2 中，`foreach` 迭代变量 `item` 必须也为隐式类型。</span><span class="sxs-lookup"><span data-stu-id="fb741-116">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="fb741-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="fb741-117">See also</span></span>

- [<span data-ttu-id="fb741-118">C# 参考</span><span class="sxs-lookup"><span data-stu-id="fb741-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fb741-119">隐式类型本地变量</span><span class="sxs-lookup"><span data-stu-id="fb741-119">Implicitly typed local variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="fb741-120">LINQ 查询操作中的类型关系</span><span class="sxs-lookup"><span data-stu-id="fb741-120">Type relationships in LINQ query operations</span></span>](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
