---
title: 如何：查询信息
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: d45fdfa8b8976e3cdc86b905443bf7bcea578714
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166399"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="32d4b-102">如何：查询信息</span><span class="sxs-lookup"><span data-stu-id="32d4b-102">How to: Query for Information</span></span>

<span data-ttu-id="32d4b-103">中 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的查询使用的语法与 LINQ 中的查询相同。</span><span class="sxs-lookup"><span data-stu-id="32d4b-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in LINQ.</span></span> <span data-ttu-id="32d4b-104">唯一的区别是查询中引用的对象 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 映射到数据库中的元素。</span><span class="sxs-lookup"><span data-stu-id="32d4b-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="32d4b-105">有关详细信息，请参阅 [LINQ 查询简介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="32d4b-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="32d4b-106">将您编写的查询转换成等效的 SQL 查询，然后将它们发送至服务器进行处理。</span><span class="sxs-lookup"><span data-stu-id="32d4b-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="32d4b-107">LINQ 查询的某些功能在应用程序中可能需要特别注意 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="32d4b-107">Some features of LINQ queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="32d4b-108">有关详细信息，请参阅 [查询概念](query-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="32d4b-108">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32d4b-109">示例</span><span class="sxs-lookup"><span data-stu-id="32d4b-109">Example</span></span>  

 <span data-ttu-id="32d4b-110">下面的查询请求来自伦敦的客户的列表。</span><span class="sxs-lookup"><span data-stu-id="32d4b-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="32d4b-111">在此示例中，`Customers` 是 Northwind 示例数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="32d4b-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="32d4b-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="32d4b-112">See also</span></span>

- [<span data-ttu-id="32d4b-113">创建对象模型</span><span class="sxs-lookup"><span data-stu-id="32d4b-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="32d4b-114">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="32d4b-114">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="32d4b-115">查询数据库</span><span class="sxs-lookup"><span data-stu-id="32d4b-115">Querying the Database</span></span>](querying-the-database.md)
