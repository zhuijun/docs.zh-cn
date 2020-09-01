---
description: let 子句 - C# 参考
title: let 子句 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3767b9745cccd9802374a8100de19f286c9b55ea
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139588"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="29cf0-103">let 子句（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="29cf0-103">let clause (C# Reference)</span></span>

<span data-ttu-id="29cf0-104">在查询表达式中，存储子表达式的结果有时很有帮助，可在后续子句中使用。</span><span class="sxs-lookup"><span data-stu-id="29cf0-104">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="29cf0-105">可以通过 `let` 关键字执行此操作，该关键字创建一个新的范围变量并通过提供的表达式结果初始化该变量。</span><span class="sxs-lookup"><span data-stu-id="29cf0-105">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="29cf0-106">使用值进行初始化后，范围变量不能用于存储另一个值。</span><span class="sxs-lookup"><span data-stu-id="29cf0-106">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="29cf0-107">但是，如果范围变量持有可查询类型，则可以查询该变量。</span><span class="sxs-lookup"><span data-stu-id="29cf0-107">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="29cf0-108">示例</span><span class="sxs-lookup"><span data-stu-id="29cf0-108">Example</span></span>

<span data-ttu-id="29cf0-109">以两种方式使用以下示例 `let`：</span><span class="sxs-lookup"><span data-stu-id="29cf0-109">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="29cf0-110">创建一个可以查询其自身的可枚举类型。</span><span class="sxs-lookup"><span data-stu-id="29cf0-110">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="29cf0-111">使查询仅调用一次范围变量 `word` 上的 `ToLower`。</span><span class="sxs-lookup"><span data-stu-id="29cf0-111">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="29cf0-112">如果不使用 `let`，则不得不调用 `where` 子句中的每个谓词的 `ToLower`。</span><span class="sxs-lookup"><span data-stu-id="29cf0-112">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="29cf0-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="29cf0-113">See also</span></span>

- [<span data-ttu-id="29cf0-114">C# 参考</span><span class="sxs-lookup"><span data-stu-id="29cf0-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="29cf0-115">查询关键字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="29cf0-115">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="29cf0-116">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="29cf0-116">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="29cf0-117">语言集成查询 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="29cf0-117">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="29cf0-118">在查询表达式中处理异常</span><span class="sxs-lookup"><span data-stu-id="29cf0-118">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
