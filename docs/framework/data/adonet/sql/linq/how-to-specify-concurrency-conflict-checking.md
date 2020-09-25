---
title: 如何：指定并发冲突检查
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: 7adacdccd12c6493ff7c62c0e6a44058a9719d7d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197204"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="76968-102">如何：指定并发冲突检查</span><span class="sxs-lookup"><span data-stu-id="76968-102">How to: Specify Concurrency-Conflict Checking</span></span>

<span data-ttu-id="76968-103">您可以指定在您调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时要检查数据库的哪些列是否发生并发冲突。</span><span class="sxs-lookup"><span data-stu-id="76968-103">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="76968-104">有关详细信息，请参阅 [如何：指定针对并发冲突对哪些成员进行测试](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)。</span><span class="sxs-lookup"><span data-stu-id="76968-104">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76968-105">示例</span><span class="sxs-lookup"><span data-stu-id="76968-105">Example</span></span>  

 <span data-ttu-id="76968-106">下面的代码指定在更新检查期间永远都不应该测试 `HomePage` 成员。</span><span class="sxs-lookup"><span data-stu-id="76968-106">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="76968-107">有关详细信息，请参阅 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。</span><span class="sxs-lookup"><span data-stu-id="76968-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="76968-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="76968-108">See also</span></span>

- [<span data-ttu-id="76968-109">LINQ to SQL 对象模型</span><span class="sxs-lookup"><span data-stu-id="76968-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="76968-110">如何：通过使用代码编辑器自定义实体类</span><span class="sxs-lookup"><span data-stu-id="76968-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
