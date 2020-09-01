---
description: into - C# 参考
title: into - C# 参考
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: 4712a6906195c5d8bc09c7b734dba0df4d2b08c8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134518"
---
# <a name="into-c-reference"></a><span data-ttu-id="3ba0c-103">into（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="3ba0c-103">into (C# Reference)</span></span>

<span data-ttu-id="3ba0c-104">可使用 `into` 上下文关键字创建临时标识符，将 [group](group-clause.md)、[join](join-clause.md) 或 [select](select-clause.md) 子句的结果存储至新标识符。</span><span class="sxs-lookup"><span data-stu-id="3ba0c-104">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="3ba0c-105">此标识符本身可以是附加查询命令的生成器。</span><span class="sxs-lookup"><span data-stu-id="3ba0c-105">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="3ba0c-106">有时称在 `group` 或 `select` 子句中使用新标识符为“延续”\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ba0c-106">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="3ba0c-107">示例</span><span class="sxs-lookup"><span data-stu-id="3ba0c-107">Example</span></span>

<span data-ttu-id="3ba0c-108">下面的示例演示使用 `into` 关键字来启用具有推断类型 `IGrouping` 的临时标识符 `fruitGroup`。</span><span class="sxs-lookup"><span data-stu-id="3ba0c-108">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="3ba0c-109">通过使用该标识符，可对每个组调用 <xref:System.Linq.Enumerable.Count%2A> 方法，并且仅选择那些包含两个或更多个单词的组。</span><span class="sxs-lookup"><span data-stu-id="3ba0c-109">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="3ba0c-110">仅当希望对每个组执行附加查询操作时，才需在 `group` 子句中使用 `into`。</span><span class="sxs-lookup"><span data-stu-id="3ba0c-110">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="3ba0c-111">有关详细信息，请参阅 [group 子句](group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba0c-111">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="3ba0c-112">有关在 `join` 子句中使用 `into` 的示例，请参见 [join 子句](join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba0c-112">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ba0c-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ba0c-113">See also</span></span>

- [<span data-ttu-id="3ba0c-114">查询关键字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="3ba0c-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="3ba0c-115">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="3ba0c-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="3ba0c-116">group 子句</span><span class="sxs-lookup"><span data-stu-id="3ba0c-116">group clause</span></span>](group-clause.md)
