---
title: System.DateTime 方法
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: e3bffb1f47c19ccf7ea59151cd3545a15d59f1f2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203483"
---
# <a name="systemdatetime-methods"></a><span data-ttu-id="62810-102">System.DateTime 方法</span><span class="sxs-lookup"><span data-stu-id="62810-102">System.DateTime Methods</span></span>

<span data-ttu-id="62810-103">以下受 LINQ to SQL 支持的方法、运算符和属性可以在 LINQ to SQL 查询中使用。</span><span class="sxs-lookup"><span data-stu-id="62810-103">The following LINQ to SQL-supported methods, operators, and properties are available to use in LINQ to SQL queries.</span></span> <span data-ttu-id="62810-104">当某个方法、运算符或属性不受支持时，LINQ to SQL 将无法转换成员以在 SQL Server 上执行。</span><span class="sxs-lookup"><span data-stu-id="62810-104">When a method, operator or property is unsupported, LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="62810-105">你可以在代码中使用这些成员，但是在将查询转换为 Transact-SQL 之前或在已经从数据库中检索结果之后，必须对这些成员进行计算。</span><span class="sxs-lookup"><span data-stu-id="62810-105">You may use these members in your code, however, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="supported-systemdatetime-members"></a><span data-ttu-id="62810-106">支持的 System.DateTime 成员</span><span class="sxs-lookup"><span data-stu-id="62810-106">Supported System.DateTime Members</span></span>  

 <span data-ttu-id="62810-107">在对象模型或外部映射文件中进行映射后，LINQ to SQL 允许您在 LINQ to SQL 查询内调用下面的 <xref:System.DateTime?displayProperty=nameWithType> 成员。</span><span class="sxs-lookup"><span data-stu-id="62810-107">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call the following <xref:System.DateTime?displayProperty=nameWithType> members inside LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="62810-108">支持的 <xref:System.DateTime> 方法</span><span class="sxs-lookup"><span data-stu-id="62810-108">Supported <xref:System.DateTime> Methods</span></span>|<span data-ttu-id="62810-109">支持的 <xref:System.DateTime> 运算符</span><span class="sxs-lookup"><span data-stu-id="62810-109">Supported <xref:System.DateTime> Operators</span></span>|<span data-ttu-id="62810-110">支持的 <xref:System.DateTime> 属性</span><span class="sxs-lookup"><span data-stu-id="62810-110">Supported <xref:System.DateTime> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a><span data-ttu-id="62810-111">不受 LINQ to SQL 支持的成员</span><span class="sxs-lookup"><span data-stu-id="62810-111">Members Not Supported by LINQ to SQL</span></span>  

 <span data-ttu-id="62810-112">LINQ to SQL 查询中不支持下列成员。</span><span class="sxs-lookup"><span data-stu-id="62810-112">The following members are not supported inside LINQ to SQL queries.</span></span>  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a><span data-ttu-id="62810-113">方法转换示例</span><span class="sxs-lookup"><span data-stu-id="62810-113">Method Translation Example</span></span>  

 <span data-ttu-id="62810-114">在将 LINQ to SQL 支持的所有方法发送给 SQL Server 之前会将其转换为 Transact-SQL。</span><span class="sxs-lookup"><span data-stu-id="62810-114">All methods supported by LINQ to SQL are translated to Transact-SQL before they are sent to   SQL Server.</span></span> <span data-ttu-id="62810-115">例如，考虑如下模式。</span><span class="sxs-lookup"><span data-stu-id="62810-115">For example, consider the following pattern.</span></span>  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 <span data-ttu-id="62810-116">识别以上模式时，会将其转换成对 SQL Server `DATEDIFF` 函数的直接调用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="62810-116">When it is recognized, it is translated into a direct call to the SQL Server `DATEDIFF` function, as follows:</span></span>  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="62810-117">SQLMethods 日期和时间方法</span><span class="sxs-lookup"><span data-stu-id="62810-117">SQLMethods Date and Time Methods</span></span>  

 <span data-ttu-id="62810-118">除了 <xref:System.DateTime> 结构提供的方法，LINQ to SQL 还提供下表列出的来自 <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> 类的方法，以便与日期和时间一起使用。</span><span class="sxs-lookup"><span data-stu-id="62810-118">In addition to the methods offered by the <xref:System.DateTime> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="62810-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="62810-119">See also</span></span>

- [<span data-ttu-id="62810-120">查询概念</span><span class="sxs-lookup"><span data-stu-id="62810-120">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="62810-121">创建对象模型</span><span class="sxs-lookup"><span data-stu-id="62810-121">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="62810-122">SQL-CLR 类型映射</span><span class="sxs-lookup"><span data-stu-id="62810-122">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="62810-123">数据类型和函数</span><span class="sxs-lookup"><span data-stu-id="62810-123">Data Types and Functions</span></span>](data-types-and-functions.md)
