---
title: 如何：通过使用事务对数据提交进行分类
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 4d3efedbf15be55fa7a9ab235f881f1c97758953
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161355"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="064f4-102">如何：通过使用事务对数据提交进行分类</span><span class="sxs-lookup"><span data-stu-id="064f4-102">How to: Bracket Data Submissions by Using Transactions</span></span>

<span data-ttu-id="064f4-103">您可以使用 <xref:System.Transactions.TransactionScope> 来封闭您提交到数据库的数据。</span><span class="sxs-lookup"><span data-stu-id="064f4-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="064f4-104">有关详细信息，请参阅 [事务支持](transaction-support.md)。</span><span class="sxs-lookup"><span data-stu-id="064f4-104">For more information, see [Transaction Support](transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="064f4-105">示例</span><span class="sxs-lookup"><span data-stu-id="064f4-105">Example</span></span>  

 <span data-ttu-id="064f4-106">下面的代码将数据库提交数据封闭在 <xref:System.Transactions.TransactionScope> 中。</span><span class="sxs-lookup"><span data-stu-id="064f4-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="064f4-107">请参阅</span><span class="sxs-lookup"><span data-stu-id="064f4-107">See also</span></span>

- [<span data-ttu-id="064f4-108">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="064f4-108">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="064f4-109">进行和提交数据更改</span><span class="sxs-lookup"><span data-stu-id="064f4-109">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="064f4-110">事务支持</span><span class="sxs-lookup"><span data-stu-id="064f4-110">Transaction Support</span></span>](transaction-support.md)
