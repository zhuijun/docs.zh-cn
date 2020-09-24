---
title: System.TimeSpan 方法
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: 15b6c8bd5c9cce8e6d1bac030c6b7f6b40df6cd4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155583"
---
# <a name="systemtimespan-methods"></a><span data-ttu-id="b1bd6-102">System.TimeSpan 方法</span><span class="sxs-lookup"><span data-stu-id="b1bd6-102">System.TimeSpan Methods</span></span>

<span data-ttu-id="b1bd6-103">对 <xref:System.TimeSpan?displayProperty=nameWithType> 的成员支持在很大程度上取决于您正在使用的 .NET Framework 和 Microsoft SQL Server 的版本。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-103">Member support for <xref:System.TimeSpan?displayProperty=nameWithType> greatly depends on the versions of the .NET Framework and Microsoft SQL Server that you are using.</span></span>  
  
 <span data-ttu-id="b1bd6-104">当某个方法、运算符或属性不受支持时；这意味着 LINQ to SQL 将无法转换成员以在 SQL Server 上执行。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-104">When a method, operator, or property is unsupported; it means that LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="b1bd6-105">你可能仍可以在代码中使用这些成员。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-105">You may still be able to use these members in your code.</span></span> <span data-ttu-id="b1bd6-106">不过，在将查询转换为 Transact-SQL 之前或在已经从数据库中检索结果之后，必须对这些成员进行计算。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-106">However, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="previous-limitations"></a><span data-ttu-id="b1bd6-107">以前的限制</span><span class="sxs-lookup"><span data-stu-id="b1bd6-107">Previous Limitations</span></span>  

 <span data-ttu-id="b1bd6-108">将 LINQ to SQL 与 .NET Framework 3.5 SP1 之前的 .NET Framework 版本一起使用时，您无法将 SQL Server 数据库字段映射到 <xref:System.TimeSpan?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-108">When using LINQ to SQL with versions of the .NET Framework prior to .NET Framework 3.5 SP1, you cannot map SQL Server database fields to <xref:System.TimeSpan?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b1bd6-109">但是，支持对 <xref:System.TimeSpan> 的操作，原因是可以通过 <xref:System.TimeSpan> 减法运算返回 <xref:System.DateTime> 值或将这些值作为文本或绑定变量引入表达式。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-109">However, operations on <xref:System.TimeSpan> are supported because <xref:System.TimeSpan> values can be returned from <xref:System.DateTime> subtraction or introduced into an expression as a literal or bound variable.</span></span>  
  
## <a name="supported-systemtimespan-member-support"></a><span data-ttu-id="b1bd6-110">支持的 TimeSpan 成员支持</span><span class="sxs-lookup"><span data-stu-id="b1bd6-110">Supported System.TimeSpan member support</span></span>

 <span data-ttu-id="b1bd6-111">以下受 LINQ to SQL 支持的方法、运算符和属性可供您在 LINQ to SQL 查询中使用。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-111">The following LINQ to SQL-supported methods, operators, and properties are available for you to use in your LINQ to SQL queries.</span></span> <span data-ttu-id="b1bd6-112">在对象模型或外部映射文件中进行映射后，LINQ to SQL 允许您从 LINQ to SQL 查询内调用许多 <xref:System.TimeSpan?displayProperty=nameWithType> 成员。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-112">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call many of the <xref:System.TimeSpan?displayProperty=nameWithType> members inside your LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="b1bd6-113">支持的 <xref:System.TimeSpan> 方法</span><span class="sxs-lookup"><span data-stu-id="b1bd6-113">Supported <xref:System.TimeSpan> Methods</span></span>|<span data-ttu-id="b1bd6-114">支持的 <xref:System.TimeSpan> 运算符</span><span class="sxs-lookup"><span data-stu-id="b1bd6-114">Supported <xref:System.TimeSpan> Operators</span></span>|<span data-ttu-id="b1bd6-115">支持的 <xref:System.TimeSpan> 属性</span><span class="sxs-lookup"><span data-stu-id="b1bd6-115">Supported <xref:System.TimeSpan> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
> <span data-ttu-id="b1bd6-116">需要安装 .NET Framework 3.5 SP1 和更高版本，才能使用 LINQ to SQL 将 <xref:System.TimeSpan?displayProperty=nameWithType> 映射到 SQL `TIME` 列。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-116">The ability to map <xref:System.TimeSpan?displayProperty=nameWithType> to a SQL `TIME` column with LINQ to SQL requires the .NET Framework 3.5 SP1 and beyond.</span></span> <span data-ttu-id="b1bd6-117">SQL `TIME` 数据类型仅在 Microsoft SQL Server 2008 和更高版本中提供。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-117">The SQL `TIME` data type is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
### <a name="addition-and-subtraction"></a><span data-ttu-id="b1bd6-118">加法和减法</span><span class="sxs-lookup"><span data-stu-id="b1bd6-118">Addition and Subtraction</span></span>  

 <span data-ttu-id="b1bd6-119">尽管 CLR <xref:System.TimeSpan?displayProperty=nameWithType> 类型支持加减运算，但 SQL `TIME` 类型不支持。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-119">Although the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type does support addition and subtraction, the SQL `TIME` type does not.</span></span> <span data-ttu-id="b1bd6-120">因此，将 LINQ to SQL 查询映射到 SQL `TIME` 类型后，如果这些查询尝试执行加减运算，则将生成错误。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-120">Because of this, your LINQ to SQL queries will generate errors if they attempt addition and subtraction when they are mapped to the SQL `TIME` type.</span></span> <span data-ttu-id="b1bd6-121">在 [sql-CLR 类型映射](sql-clr-type-mapping.md)中，可以找到有关使用 sql 日期和时间类型的其他注意事项。</span><span class="sxs-lookup"><span data-stu-id="b1bd6-121">You can find other considerations for working with SQL date and time types in [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bd6-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="b1bd6-122">See also</span></span>

- [<span data-ttu-id="b1bd6-123">查询概念</span><span class="sxs-lookup"><span data-stu-id="b1bd6-123">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="b1bd6-124">创建对象模型</span><span class="sxs-lookup"><span data-stu-id="b1bd6-124">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="b1bd6-125">SQL-CLR 类型映射</span><span class="sxs-lookup"><span data-stu-id="b1bd6-125">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="b1bd6-126">数据类型和函数</span><span class="sxs-lookup"><span data-stu-id="b1bd6-126">Data Types and Functions</span></span>](data-types-and-functions.md)
