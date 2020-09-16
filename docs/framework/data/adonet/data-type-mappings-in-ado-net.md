---
title: 数据类型映射
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 065a9dcb5e03c784c5dec9ffbe6a3153aead9e3c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554705"
---
# <a name="data-type-mappings-in-adonet"></a><span data-ttu-id="27596-102">ADO.NET 中的数据类型映射</span><span class="sxs-lookup"><span data-stu-id="27596-102">Data Type Mappings in ADO.NET</span></span>
<span data-ttu-id="27596-103">.NET Framework 基于用于定义如何在运行时声明、使用和管理类型的通用类型系统。</span><span class="sxs-lookup"><span data-stu-id="27596-103">The .NET Framework is based on the common type system, which defines how types are declared, used, and managed in the runtime.</span></span> <span data-ttu-id="27596-104">它由值类型和引用类型组成，这两种类型均派生自 <xref:System.Object> 基类型。</span><span class="sxs-lookup"><span data-stu-id="27596-104">It consists of both value types and reference types, which all derive from the <xref:System.Object> base type.</span></span> <span data-ttu-id="27596-105">使用数据源时，如果未显式指定数据类型，则从数据提供程序推断出它。</span><span class="sxs-lookup"><span data-stu-id="27596-105">When working with a data source, the data type is inferred from the data provider if it is not explicitly specified.</span></span> <span data-ttu-id="27596-106">例如，<xref:System.Data.DataSet> 对象独立于任何特定的数据源。</span><span class="sxs-lookup"><span data-stu-id="27596-106">For example, a <xref:System.Data.DataSet> object is independent of any specific data source.</span></span> <span data-ttu-id="27596-107">`DataSet` 中的数据从数据源中进行检索，而更改则会使用 `DataAdapter` 持久保存回数据源。</span><span class="sxs-lookup"><span data-stu-id="27596-107">Data in a `DataSet` is retrieved from a data source, and changes are persisted back to the data source by using a `DataAdapter`.</span></span> <span data-ttu-id="27596-108">这意味着当 `DataAdapter` <xref:System.Data.DataTable> 使用数据源中的值填充中的时 `DataSet` ，中列的结果数据类型 `DataTable` 为 .NET Framework 类型，而不是特定于用于连接到数据源的 .NET Framework 数据提供程序的类型。</span><span class="sxs-lookup"><span data-stu-id="27596-108">This means that when a `DataAdapter` fills a <xref:System.Data.DataTable> in a `DataSet` with values from a data source, the resulting data types of the columns in the `DataTable` are .NET Framework types, instead of types specific to the .NET Framework data provider that is used to connect to the data source.</span></span>  
  
 <span data-ttu-id="27596-109">同样，当 `DataReader` 从数据源返回值时，生成的值将存储在具有 .NET Framework 类型的局部变量中。</span><span class="sxs-lookup"><span data-stu-id="27596-109">Likewise, when a `DataReader` returns a value from a data source, the resulting value is stored in a local variable that has a .NET Framework type.</span></span> <span data-ttu-id="27596-110">对于的 `Fill` 操作 `DataAdapter` 和的 `Get` 方法，将 `DataReader` 从 .NET Framework 数据提供程序返回的值推断 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="27596-110">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the value returned from the .NET Framework data provider.</span></span>  
  
 <span data-ttu-id="27596-111">当所返回值的特定类型已知时，可以使用 `DataReader` 的类型化访问器方法，而不是依靠推断出的数据类型。</span><span class="sxs-lookup"><span data-stu-id="27596-111">Instead of relying on the inferred data type, you can use the typed accessor methods of the `DataReader` when you know the specific type of the value being returned.</span></span> <span data-ttu-id="27596-112">类型化访问器方法通过以特定 .NET Framework 类型返回值来提高性能，从而无需额外的类型转换。</span><span class="sxs-lookup"><span data-stu-id="27596-112">Typed accessor methods give you better performance by returning a value as a specific .NET Framework type, which eliminates the need for additional type conversion.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27596-113">.NET Framework 数据提供程序数据类型的 Null 值由表示 `DBNull.Value` 。</span><span class="sxs-lookup"><span data-stu-id="27596-113">Null values for .NET Framework data provider data types are represented by `DBNull.Value`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27596-114">本节内容</span><span class="sxs-lookup"><span data-stu-id="27596-114">In This Section</span></span>  
 [<span data-ttu-id="27596-115">SQL Server 数据类型映射</span><span class="sxs-lookup"><span data-stu-id="27596-115">SQL Server Data Type Mappings</span></span>](sql-server-data-type-mappings.md)  
 <span data-ttu-id="27596-116">列出针对 <xref:System.Data.SqlClient> 的推断数据类型映射和数据访问器方法。</span><span class="sxs-lookup"><span data-stu-id="27596-116">Lists inferred data type mappings and data accessor methods for <xref:System.Data.SqlClient>.</span></span>  
  
 [<span data-ttu-id="27596-117">OLE DB 数据类型映射</span><span class="sxs-lookup"><span data-stu-id="27596-117">OLE DB Data Type Mappings</span></span>](ole-db-data-type-mappings.md)  
 <span data-ttu-id="27596-118">列出针对 <xref:System.Data.OleDb> 的推断数据类型映射和数据访问器方法。</span><span class="sxs-lookup"><span data-stu-id="27596-118">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OleDb>.</span></span>  
  
 [<span data-ttu-id="27596-119">ODBC 数据类型映射</span><span class="sxs-lookup"><span data-stu-id="27596-119">ODBC Data Type Mappings</span></span>](odbc-data-type-mappings.md)  
 <span data-ttu-id="27596-120">列出针对 <xref:System.Data.Odbc> 的推断数据类型映射和数据访问器方法。</span><span class="sxs-lookup"><span data-stu-id="27596-120">Lists inferred data type mappings and data accessor methods for <xref:System.Data.Odbc>.</span></span>  
  
 [<span data-ttu-id="27596-121">Oracle 数据类型映射</span><span class="sxs-lookup"><span data-stu-id="27596-121">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="27596-122">列出针对 <xref:System.Data.OracleClient> 的推断数据类型映射和数据访问器方法。</span><span class="sxs-lookup"><span data-stu-id="27596-122">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OracleClient>.</span></span>  
  
 [<span data-ttu-id="27596-123">浮点数</span><span class="sxs-lookup"><span data-stu-id="27596-123">Floating-Point Numbers</span></span>](floating-point-numbers.md)  
 <span data-ttu-id="27596-124">描述开发人员在使用浮点数时经常遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="27596-124">Describes issues that developers frequently encounter when working with floating-point numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27596-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="27596-125">See also</span></span>

- [<span data-ttu-id="27596-126">SQL Server 数据类型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="27596-126">SQL Server Data Types and ADO.NET</span></span>](./sql/sql-server-data-types.md)
- [<span data-ttu-id="27596-127">配置参数和参数数据类型</span><span class="sxs-lookup"><span data-stu-id="27596-127">Configuring Parameters and Parameter Data Types</span></span>](configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="27596-128">检索数据库架构信息</span><span class="sxs-lookup"><span data-stu-id="27596-128">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="27596-129">常规类型系统</span><span class="sxs-lookup"><span data-stu-id="27596-129">Common Type System</span></span>](../../../standard/base-types/common-type-system.md)
- <span data-ttu-id="27596-130">[转换类型](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="27596-130">[Converting Types](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))</span></span>
- [<span data-ttu-id="27596-131">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="27596-131">ADO.NET Overview</span></span>](ado-net-overview.md)
