---
title: 如何：检索实体冲突信息
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: e8c548ac632454d9c488ebd5f7b471f6759418fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155869"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="c7388-102">如何：检索实体冲突信息</span><span class="sxs-lookup"><span data-stu-id="c7388-102">How to: Retrieve Entity Conflict Information</span></span>

<span data-ttu-id="c7388-103">您可以使用 <xref:System.Data.Linq.ObjectChangeConflict> 类的对象来提供有关 <xref:System.Data.Linq.ChangeConflictException> 异常指出的冲突的信息。</span><span class="sxs-lookup"><span data-stu-id="c7388-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="c7388-104">有关详细信息，请参阅 [乐观 Concurrency：概述](optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c7388-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7388-105">示例</span><span class="sxs-lookup"><span data-stu-id="c7388-105">Example</span></span>  

 <span data-ttu-id="c7388-106">下面的示例循环访问累积冲突的列表。</span><span class="sxs-lookup"><span data-stu-id="c7388-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c7388-107">请参阅</span><span class="sxs-lookup"><span data-stu-id="c7388-107">See also</span></span>

- [<span data-ttu-id="c7388-108">如何：管理更改冲突</span><span class="sxs-lookup"><span data-stu-id="c7388-108">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
