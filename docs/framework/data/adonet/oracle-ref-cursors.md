---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: cbf330ba381a825c2d16038c01d7bdc52bc8f482
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180876"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="0bf42-102">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="0bf42-102">Oracle REF CURSORs</span></span>

<span data-ttu-id="0bf42-103">用于 Oracle 的 .NET Framework 数据提供程序支持 Oracle **REF CURSOR** 数据类型。</span><span class="sxs-lookup"><span data-stu-id="0bf42-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="0bf42-104">在通过数据提供程序使用 Oracle REF CURSOR 时，应考虑下列行为。</span><span class="sxs-lookup"><span data-stu-id="0bf42-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0bf42-105">有些行为与 Microsoft Oracle OLE DB 提供程序 (MSDAORA) 的行为不同。</span><span class="sxs-lookup"><span data-stu-id="0bf42-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
- <span data-ttu-id="0bf42-106">出于性能方面的考虑，Oracle 的数据提供程序不会自动绑定 **REF CURSOR** 数据类型（如 MSDAORA），除非显式指定它们。</span><span class="sxs-lookup"><span data-stu-id="0bf42-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
- <span data-ttu-id="0bf42-107">数据提供程序不支持任何 ODBC 转义序列，包括用于指定 REF CURSOR 参数的 {resultset} 转义。</span><span class="sxs-lookup"><span data-stu-id="0bf42-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
- <span data-ttu-id="0bf42-108">若要执行返回 REF cursor 的存储过程，必须在中定义 <xref:System.Data.OracleClient.OracleParameterCollection> 带有 <xref:System.Data.OracleClient.OracleType> **Cursor** 和 <xref:System.Data.OracleClient.OracleParameter.Direction%2A> **Output**的参数。</span><span class="sxs-lookup"><span data-stu-id="0bf42-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="0bf42-109">数据提供程序只支持作为输出参数绑定 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="0bf42-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="0bf42-110">提供程序不支持 REF CURSOR 作为输入参数。</span><span class="sxs-lookup"><span data-stu-id="0bf42-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
- <span data-ttu-id="0bf42-111">不支持从参数值获取 <xref:System.Data.OracleClient.OracleDataReader>。</span><span class="sxs-lookup"><span data-stu-id="0bf42-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="0bf42-112">在执行命令后，值属于 <xref:System.DBNull> 类型。</span><span class="sxs-lookup"><span data-stu-id="0bf42-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
- <span data-ttu-id="0bf42-113">仅当调用) 为 CloseConnection 时，才 (使用 REF 游标的唯一**CommandBehavior**枚举值 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> ; 将忽略所有其他枚举值。 **CloseConnection**</span><span class="sxs-lookup"><span data-stu-id="0bf42-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
- <span data-ttu-id="0bf42-114">**OracleDataReader**中 REF 游标的顺序取决于**OracleParameterCollection**中参数的顺序。</span><span class="sxs-lookup"><span data-stu-id="0bf42-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="0bf42-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> 属性被忽略。</span><span class="sxs-lookup"><span data-stu-id="0bf42-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
- <span data-ttu-id="0bf42-116">PL/SQL **表** 数据类型不受支持。</span><span class="sxs-lookup"><span data-stu-id="0bf42-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="0bf42-117">但是，REF CURSOR 的效率更高。</span><span class="sxs-lookup"><span data-stu-id="0bf42-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="0bf42-118">如果必须使用 **表** 数据类型，请使用 MSDAORA OLE DB 的 .Net 数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="0bf42-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0bf42-119">本节内容</span><span class="sxs-lookup"><span data-stu-id="0bf42-119">In This Section</span></span>  

 [<span data-ttu-id="0bf42-120">REF CURSOR 示例</span><span class="sxs-lookup"><span data-stu-id="0bf42-120">REF CURSOR Examples</span></span>](ref-cursor-examples.md)  
 <span data-ttu-id="0bf42-121">包含三个示例，演示如何使用 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="0bf42-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="0bf42-122">OracleDataReader 中的 REF CURSOR 参数</span><span class="sxs-lookup"><span data-stu-id="0bf42-122">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="0bf42-123">演示如何执行一个 PL/SQL 存储过程，该存储过程返回 REF CURSOR 参数，并以 **OracleDataReader**的形式读取该值。</span><span class="sxs-lookup"><span data-stu-id="0bf42-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="0bf42-124">使用 OracleDataReader 从多个 REF CURSOR 中检索数据</span><span class="sxs-lookup"><span data-stu-id="0bf42-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="0bf42-125">演示如何执行一个 PL/SQL 存储过程，该存储过程返回两个 REF CURSOR 参数，并使用 **OracleDataReader**读取值。</span><span class="sxs-lookup"><span data-stu-id="0bf42-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="0bf42-126">使用一个或多个 REF CURSOR 填充数据集</span><span class="sxs-lookup"><span data-stu-id="0bf42-126">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="0bf42-127">演示如何执行一个 PL/SQL 存储过程，返回两个 REF CURSOR 参数，并使用返回的行填充 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="0bf42-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf42-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="0bf42-128">See also</span></span>

- [<span data-ttu-id="0bf42-129">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0bf42-129">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="0bf42-130">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="0bf42-130">ADO.NET Overview</span></span>](ado-net-overview.md)
