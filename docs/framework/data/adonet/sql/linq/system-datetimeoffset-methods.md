---
title: System.DateTimeOffset 方法
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: ae588b88ca592ce422202d5231b34060ccc22024
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203470"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="cf3ec-102">System.DateTimeOffset 方法</span><span class="sxs-lookup"><span data-stu-id="cf3ec-102">System.DateTimeOffset Methods</span></span>

<span data-ttu-id="cf3ec-103">在对象模型或外部映射文件中进行映射后，LINQ to SQL 允许您从 LINQ to SQL 查询内调用大部分的 <xref:System.DateTimeOffset?displayProperty=nameWithType> 方法、运算符和属性。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="cf3ec-104">不支持的方法仅包括那些继承自 <xref:System.Object?displayProperty=nameWithType> 的方法，这些方法在 LINQ to SQL 查询的上下文中没有意义，例如：`Finalize`、`GetHashCode`、`GetType` 和 `MemberwiseClone`。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="cf3ec-105">这些方法不受支持的原因是 LINQ to SQL 无法转换它们以在 SQL Server 上执行。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf3ec-106">若要能够使用公共语言运行库 (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> 结构并通过 LINQ to SQL 将其映射到 SQL `DATETIMEOFFSET` 列，必须安装 .NET Framework 3.5 SP1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="cf3ec-107">SQL `DATETIMEOFFSET` 列仅在 Microsoft SQL Server 2008 和更高版本中提供。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="cf3ec-108">SQLMethods 日期和时间方法</span><span class="sxs-lookup"><span data-stu-id="cf3ec-108">SQLMethods Date and Time Methods</span></span>  

 <span data-ttu-id="cf3ec-109">除了 <xref:System.DateTimeOffset> 结构提供的方法，LINQ to SQL 还提供下表列出的来自 <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> 类的方法，以便与日期和时间一起使用。</span><span class="sxs-lookup"><span data-stu-id="cf3ec-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="cf3ec-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="cf3ec-110">See also</span></span>

- [<span data-ttu-id="cf3ec-111">查询概念</span><span class="sxs-lookup"><span data-stu-id="cf3ec-111">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="cf3ec-112">创建对象模型</span><span class="sxs-lookup"><span data-stu-id="cf3ec-112">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="cf3ec-113">SQL-CLR 类型映射</span><span class="sxs-lookup"><span data-stu-id="cf3ec-113">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
