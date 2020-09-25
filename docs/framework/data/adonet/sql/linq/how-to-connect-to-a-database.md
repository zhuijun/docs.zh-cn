---
title: 如何：连接到数据库
description: 了解如何使用 DataContext 连接到 LINQ to SQL 中的数据库。 请参阅以下示例，使用 DataContext 连接到数据库和获取行。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: ebd45b92abf3bf300fa5fa06dbb4e92354fac3c9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173492"
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="e6825-104">如何：连接到数据库</span><span class="sxs-lookup"><span data-stu-id="e6825-104">How to: Connect to a Database</span></span>

<span data-ttu-id="e6825-105"><xref:System.Data.Linq.DataContext> 是用来连接到数据库、从中检索对象以及将更改提交回数据库的主要渠道。</span><span class="sxs-lookup"><span data-stu-id="e6825-105">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="e6825-106">使用的 <xref:System.Data.Linq.DataContext> 方式与使用 ADO.NET 时相同 <xref:System.Data.SqlClient.SqlConnection> 。</span><span class="sxs-lookup"><span data-stu-id="e6825-106">You use the <xref:System.Data.Linq.DataContext> just as you would use an ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="e6825-107">事实上，<xref:System.Data.Linq.DataContext> 是用您提供的连接或连接字符串初始化的。</span><span class="sxs-lookup"><span data-stu-id="e6825-107">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="e6825-108">有关详细信息，请参阅 [DataContext 方法 (O/R Designer) ](/visualstudio/data-tools/datacontext-methods-o-r-designer)。</span><span class="sxs-lookup"><span data-stu-id="e6825-108">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="e6825-109"><xref:System.Data.Linq.DataContext> 的用途是将您对对象的请求转换成要对数据库执行的 SQL 查询，然后将查询结果汇编成对象。</span><span class="sxs-lookup"><span data-stu-id="e6825-109">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="e6825-110"><xref:System.Data.Linq.DataContext>通过实现与标准查询运算符（如和）相同的运算符模式， (LINQ) 启用语言集成查询 `Where` `Select` 。</span><span class="sxs-lookup"><span data-stu-id="e6825-110">The <xref:System.Data.Linq.DataContext> enables Language-Integrated Query (LINQ) by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e6825-111">维护安全连接最为重要。</span><span class="sxs-lookup"><span data-stu-id="e6825-111">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="e6825-112">有关详细信息，请参阅 [LINQ to SQL 中的安全性](security-in-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="e6825-112">For more information, see [Security in LINQ to SQL](security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6825-113">示例</span><span class="sxs-lookup"><span data-stu-id="e6825-113">Example</span></span>  

 <span data-ttu-id="e6825-114">在下面的示例中，使用 <xref:System.Data.Linq.DataContext> 连接到 Northwind 示例数据库并检索所在城市为伦敦的客户行。</span><span class="sxs-lookup"><span data-stu-id="e6825-114">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="e6825-115">每个数据库表表示为一个可借助 `Table` 方法（通过使用实体类来标识它）使用的 <xref:System.Data.Linq.DataContext.GetTable%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="e6825-115">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6825-116">示例</span><span class="sxs-lookup"><span data-stu-id="e6825-116">Example</span></span>  

 <span data-ttu-id="e6825-117">最佳的做法是声明一个强类型化的 <xref:System.Data.Linq.DataContext>，而不是依靠基本 <xref:System.Data.Linq.DataContext> 类和 <xref:System.Data.Linq.DataContext.GetTable%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e6825-117">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="e6825-118">强类型化的 <xref:System.Data.Linq.DataContext> 将所有 `Table` 集合声明为上下文的成员，如下例中所示。</span><span class="sxs-lookup"><span data-stu-id="e6825-118">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="e6825-119">然后您就可以更加简单地将对来自伦敦的客户的查询表达成：</span><span class="sxs-lookup"><span data-stu-id="e6825-119">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e6825-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="e6825-120">See also</span></span>

- [<span data-ttu-id="e6825-121">与数据库通信</span><span class="sxs-lookup"><span data-stu-id="e6825-121">Communicating with the Database</span></span>](communicating-with-the-database.md)
