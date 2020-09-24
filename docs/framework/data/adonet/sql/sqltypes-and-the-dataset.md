---
title: SqlTypes 和数据集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: 04f95cd7d3f6e52f644f23dd8a32c77d56a5ddda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147503"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="170a5-102">SqlTypes 和数据集</span><span class="sxs-lookup"><span data-stu-id="170a5-102">SqlTypes and the DataSet</span></span>

<span data-ttu-id="170a5-103">ADO.NET 2.0 通过 <xref:System.Data.SqlTypes> 命名空间引入了对 `DataSet` 的增强类型支持。</span><span class="sxs-lookup"><span data-stu-id="170a5-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="170a5-104"><xref:System.Data.SqlTypes> 中的类型旨在提供具有与 SQL Server 数据库中的数据类型相同的语义和精度的数据类型。</span><span class="sxs-lookup"><span data-stu-id="170a5-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="170a5-105"><xref:System.Data.SqlTypes> 中的每个数据类型在 SQL Server 中都具有等效的数据类型，并具有相同的基础数据表示形式。</span><span class="sxs-lookup"><span data-stu-id="170a5-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="170a5-106">使用 SQL Server 数据类型时，直接在 <xref:System.Data.DataSet> 中使用 <xref:System.Data.SqlTypes> 将带来许多好处。</span><span class="sxs-lookup"><span data-stu-id="170a5-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="170a5-107"><xref:System.Data.SqlTypes> 支持与 SQL Server 本机数据类型相同的语义。</span><span class="sxs-lookup"><span data-stu-id="170a5-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="170a5-108">在 <xref:System.Data.DataColumn> 的定义中指定其中一个 <xref:System.Data.SqlTypes> 将消除将十进制或数值数据类型转换为公共语言运行时 (CLR) 数据类型之一时可能出现的精度损失。</span><span class="sxs-lookup"><span data-stu-id="170a5-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="170a5-109">示例</span><span class="sxs-lookup"><span data-stu-id="170a5-109">Example</span></span>  

 <span data-ttu-id="170a5-110">以下代码创建 <xref:System.Data.DataTable> 对象，使用 <xref:System.Data.SqlTypes>（而不是 CLR 类型）显式定义 <xref:System.Data.DataColumn> 数据类型。</span><span class="sxs-lookup"><span data-stu-id="170a5-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="170a5-111">代码用 SQL Server 中 AdventureWorks 数据库的 Sales.SalesOrderDetail 表中的数据填充 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="170a5-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="170a5-112">控制台窗口中显示的输出显示每个列的数据类型以及从 SQL Server 检索的值。</span><span class="sxs-lookup"><span data-stu-id="170a5-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="170a5-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="170a5-113">See also</span></span>

- [<span data-ttu-id="170a5-114">SQL Server 数据类型映射</span><span class="sxs-lookup"><span data-stu-id="170a5-114">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="170a5-115">配置参数和参数数据类型</span><span class="sxs-lookup"><span data-stu-id="170a5-115">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="170a5-116">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="170a5-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
