---
title: 如何：直接执行 SQL 查询
description: 了解如何使用 ExecuteQuery 运行查询，并在 LINQ to SQL 查询不足的情况下将结果直接转换为对象。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 59bd404e41f6be1181d6a625c31ee23358db0df3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286360"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="55dd1-103">如何：直接执行 SQL 查询</span><span class="sxs-lookup"><span data-stu-id="55dd1-103">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="55dd1-104">将您编写的查询转换成参数化 SQL 查询（以文本形式），然后将它们发送至 SQL 服务器进行处理。</span><span class="sxs-lookup"><span data-stu-id="55dd1-104">translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="55dd1-105">SQL 无法执行可由您的应用程序在本地使用的各种方法。</span><span class="sxs-lookup"><span data-stu-id="55dd1-105">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="55dd1-106">会设法将这些本地方法转换成在 SQL 环境中可用的等效操作和函数。</span><span class="sxs-lookup"><span data-stu-id="55dd1-106">tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="55dd1-107">.NET Framework 内置类型上的大多数方法和运算符都可以直接翻译到 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="55dd1-107">Most methods and operators on .NET Framework built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="55dd1-108">有些则可以用可用的函数生成。</span><span class="sxs-lookup"><span data-stu-id="55dd1-108">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="55dd1-109">无法生成的那些方法和运算符会产生运行时异常。</span><span class="sxs-lookup"><span data-stu-id="55dd1-109">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="55dd1-110">有关详细信息，请参阅[SQL-CLR 类型映射](sql-clr-type-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="55dd1-110">For more information, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="55dd1-111">如果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查询不足以满足专门任务的需要，你可以使用 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法来执行 SQL 查询，然后将查询的结果直接转换成对象。</span><span class="sxs-lookup"><span data-stu-id="55dd1-111">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55dd1-112">示例</span><span class="sxs-lookup"><span data-stu-id="55dd1-112">Example</span></span>  
 <span data-ttu-id="55dd1-113">在下面的示例中，假定 `Customer` 类的数据分布在两个表（customer1 和 customer2）中。</span><span class="sxs-lookup"><span data-stu-id="55dd1-113">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="55dd1-114">此查询将返回 `Customer` 对象的序列。</span><span class="sxs-lookup"><span data-stu-id="55dd1-114">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="55dd1-115">只要表格结果中的列名与您的实体类的列属性匹配，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 就会为您创建不在任何 SQL 查询范围之内的对象。</span><span class="sxs-lookup"><span data-stu-id="55dd1-115">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55dd1-116">示例</span><span class="sxs-lookup"><span data-stu-id="55dd1-116">Example</span></span>  
 <span data-ttu-id="55dd1-117"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法也允许带有参数。</span><span class="sxs-lookup"><span data-stu-id="55dd1-117">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="55dd1-118">请使用类似如下内容的代码来执行参数化查询。</span><span class="sxs-lookup"><span data-stu-id="55dd1-118">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="55dd1-119">在查询文本中使用 `Console.WriteLine()` 和 `String.Format()` 所用的大括号表示法来表示参数。</span><span class="sxs-lookup"><span data-stu-id="55dd1-119">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="55dd1-120">事实上， `String.Format()` 实际上是在您提供的查询字符串上调用，用生成的参数名（例如 @p0 ， @p1 ...， @p （n））替换大的大括号内参数。</span><span class="sxs-lookup"><span data-stu-id="55dd1-120">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55dd1-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55dd1-121">See also</span></span>

- [<span data-ttu-id="55dd1-122">背景信息</span><span class="sxs-lookup"><span data-stu-id="55dd1-122">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="55dd1-123">查询数据库</span><span class="sxs-lookup"><span data-stu-id="55dd1-123">Querying the Database</span></span>](querying-the-database.md)
