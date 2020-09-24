---
title: Null 语义
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: 739ee95be45d7d64a4ad1678837b9706a533f07d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147536"
---
# <a name="null-semantics"></a><span data-ttu-id="73b7d-102">Null 语义</span><span class="sxs-lookup"><span data-stu-id="73b7d-102">Null Semantics</span></span>

<span data-ttu-id="73b7d-103">下表提供了文档的各个部分的链接， [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 其中 `null` `Nothing` 讨论了 Visual Basic) 问题 (。</span><span class="sxs-lookup"><span data-stu-id="73b7d-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="73b7d-104">主题</span><span class="sxs-lookup"><span data-stu-id="73b7d-104">Topic</span></span>|<span data-ttu-id="73b7d-105">描述</span><span class="sxs-lookup"><span data-stu-id="73b7d-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="73b7d-106">SQL-CLR 类型不匹配</span><span class="sxs-lookup"><span data-stu-id="73b7d-106">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="73b7d-107">本主题的 "Null 语义" 部分包括以下内容的讨论：三态 SQL Boolean 与两态公共语言运行时 (CLR) <xref:System.Boolean> 、文本 `Nothing` (Visual Basic) 和 `null` (c # ) ，以及其他类似问题。</span><span class="sxs-lookup"><span data-stu-id="73b7d-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="73b7d-108">标准查询运算符转换</span><span class="sxs-lookup"><span data-stu-id="73b7d-108">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="73b7d-109">本主题的“Null 语义”部分介绍 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中的 null 比较语义。</span><span class="sxs-lookup"><span data-stu-id="73b7d-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="73b7d-110">System.String 方法</span><span class="sxs-lookup"><span data-stu-id="73b7d-110">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="73b7d-111">本主题的“与 .NET 的差异”部分说明从 <xref:System.String.LastIndexOf%2A> 返回 0 为何意味着字符串为 null 或找到的位置为 0。</span><span class="sxs-lookup"><span data-stu-id="73b7d-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="73b7d-112">计算数值序列中值的和</span><span class="sxs-lookup"><span data-stu-id="73b7d-112">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="73b7d-113">描述运算符如何 <xref:System.Linq.Enumerable.Sum%2A> 计算 `null` (`Nothing` 在 Visual Basic) 而不是0（对于仅包含 null 值或空序列的序列）。</span><span class="sxs-lookup"><span data-stu-id="73b7d-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73b7d-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="73b7d-114">See also</span></span>

- [<span data-ttu-id="73b7d-115">数据类型和函数</span><span class="sxs-lookup"><span data-stu-id="73b7d-115">Data Types and Functions</span></span>](data-types-and-functions.md)
