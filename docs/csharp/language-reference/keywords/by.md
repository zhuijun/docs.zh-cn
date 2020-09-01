---
description: by 上下文关键字 - C# 参考
title: by 上下文关键字 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- by
- by_CSharpKeyword
helpviewer_keywords:
- by keyword [C#]
ms.assetid: efe6f0e3-be40-4df2-a144-c7db968ae052
ms.openlocfilehash: 2bc62f6f7f9e8a6d434ea254d5b04e563c41bc26
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134687"
---
# <a name="by-c-reference"></a><span data-ttu-id="e92dc-103">by（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="e92dc-103">by (C# Reference)</span></span>

<span data-ttu-id="e92dc-104">`by` 上下文关键字用于在查询表达式的 `group` 子句中指定应返回项的分组方式。</span><span class="sxs-lookup"><span data-stu-id="e92dc-104">The `by` contextual keyword is used in the `group` clause in a query expression to specify how the returned items should be grouped.</span></span> <span data-ttu-id="e92dc-105">有关详细信息，请参阅 [group 子句](./group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e92dc-105">For more information, see [group clause](./group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="e92dc-106">示例</span><span class="sxs-lookup"><span data-stu-id="e92dc-106">Example</span></span>

<span data-ttu-id="e92dc-107">下面的示例演示在 `group` 字句中使用 `by` 关键字指定应根据每个学生的姓氏首字母对学生分组。</span><span class="sxs-lookup"><span data-stu-id="e92dc-107">The following example shows the use of the `by` contextual keyword in a `group` clause to specify that the students should be grouped according to the first letter of the last name of each student.</span></span>

[!code-csharp[csrefKeywordsContextual#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#10)]

## <a name="see-also"></a><span data-ttu-id="e92dc-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e92dc-108">See also</span></span>

- [<span data-ttu-id="e92dc-109">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="e92dc-109">LINQ in C#</span></span>](../../linq/index.md)
