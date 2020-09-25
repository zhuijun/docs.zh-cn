---
title: 写入数据集架构信息作为 XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 7634dfc8415b6f73fc60f2ebe59c92a0c31f83a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173726"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="aa894-102">写入数据集架构信息作为 XSD</span><span class="sxs-lookup"><span data-stu-id="aa894-102">Writing DataSet Schema Information as XSD</span></span>

<span data-ttu-id="aa894-103">您可以用 XML 架构定义语言 (XSD) 架构的形式来编写 <xref:System.Data.DataSet> 的架构，以便在 XML 文档中传输包含或不包含相关数据的架构。</span><span class="sxs-lookup"><span data-stu-id="aa894-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="aa894-104">XML 架构可以写入文件、流、 <xref:System.Xml.XmlWriter> 或字符串; 它可用于生成强类型化 **数据集**。</span><span class="sxs-lookup"><span data-stu-id="aa894-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="aa894-105">有关强类型化 **数据集** 对象的详细信息，请参阅 [类型化数据集](typed-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="aa894-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](typed-datasets.md).</span></span>  
  
 <span data-ttu-id="aa894-106">您可以使用对象的 **ColumnMapping** 属性来指定如何在 XML 架构中表示表的列 <xref:System.Data.DataColumn> 。</span><span class="sxs-lookup"><span data-stu-id="aa894-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="aa894-107">有关详细信息，请参阅以 [Xml 数据形式编写数据集内容](writing-dataset-contents-as-xml-data.md)中的 "将列映射到 xml 元素、属性和文本"。</span><span class="sxs-lookup"><span data-stu-id="aa894-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="aa894-108">若要将**数据集**的架构作为 XML 架构写入文件、流或**XmlWriter**，请使用**DataSet**的**WriteXmlSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="aa894-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="aa894-109">**WriteXmlSchema** 使用一个参数来指定生成的 XML 架构的目标。</span><span class="sxs-lookup"><span data-stu-id="aa894-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="aa894-110">下面的代码示例演示如何通过传递包含文件名和对象的字符串，将 **数据集** 的 XML 架构写入文件 <xref:System.IO.StreamWriter> 。</span><span class="sxs-lookup"><span data-stu-id="aa894-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 <span data-ttu-id="aa894-111">若要获取 **数据集** 的架构并将其作为 XML 架构字符串写入，请使用 **GetXmlSchema** 方法，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="aa894-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa894-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="aa894-112">See also</span></span>

- [<span data-ttu-id="aa894-113">在数据集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="aa894-113">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="aa894-114">写入数据集内容作为 XML 数据</span><span class="sxs-lookup"><span data-stu-id="aa894-114">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)
- [<span data-ttu-id="aa894-115">类型化数据集</span><span class="sxs-lookup"><span data-stu-id="aa894-115">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="aa894-116">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="aa894-116">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="aa894-117">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="aa894-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
