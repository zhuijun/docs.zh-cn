---
title: SQL XML 列值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: cd55e2263d4b71fe62910ac918e331ebe37833eb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177275"
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="e6e4e-102">SQL XML 列值</span><span class="sxs-lookup"><span data-stu-id="e6e4e-102">SQL XML Column Values</span></span>

<span data-ttu-id="e6e4e-103">SQL Server 支持 `xml` 数据类型，开发人员可以使用 <xref:System.Data.SqlClient.SqlCommand> 类的标准行为检索包括此类型的结果集。</span><span class="sxs-lookup"><span data-stu-id="e6e4e-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="e6e4e-104">可以检索 `xml` 列（例如，检索到 <xref:System.Data.SqlClient.SqlDataReader> 中），就像检索任何列一样；但若要以 XML 格式处理列内容，必须使用 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="e6e4e-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6e4e-105">示例</span><span class="sxs-lookup"><span data-stu-id="e6e4e-105">Example</span></span>  

 <span data-ttu-id="e6e4e-106">以下控制台应用程序从 AdventureWorks 数据库的 Sales.Store 表中为 <xref:System.Data.SqlClient.SqlDataReader> 实例选择两行，每行包含一个 `xml` 列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6e4e-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="e6e4e-107">对于每一行，`xml` 列的值是使用 <xref:System.Data.SqlClient.SqlDataReader> 的 <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> 方法进行读取。</span><span class="sxs-lookup"><span data-stu-id="e6e4e-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="e6e4e-108">此值存储在 <xref:System.Xml.XmlReader> 中。</span><span class="sxs-lookup"><span data-stu-id="e6e4e-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="e6e4e-109">请注意，若要将内容设置为 <xref:System.Data.SqlTypes.SqlXml> 变量，必须使用 <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A>，而不是 <xref:System.Data.IDataRecord.GetValue%2A> 方法；<xref:System.Data.IDataRecord.GetValue%2A> 以字符串形式返回 `xml` 列的值。</span><span class="sxs-lookup"><span data-stu-id="e6e4e-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6e4e-110">默认情况下，在安装 SQL Server 时不安装 AdventureWorks 示例数据库\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6e4e-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="e6e4e-111">可以通过运行 SQL Server 安装程序来安装它。</span><span class="sxs-lookup"><span data-stu-id="e6e4e-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e6e4e-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="e6e4e-112">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="e6e4e-113">SQL Server 中的 XML 数据</span><span class="sxs-lookup"><span data-stu-id="e6e4e-113">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)
- [<span data-ttu-id="e6e4e-114">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="e6e4e-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
