---
title: 从 XML 加载数据集架构信息
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: b084590d7158024227a9f12da759b56ae2031373
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201338"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="55120-102">从 XML 加载数据集架构信息</span><span class="sxs-lookup"><span data-stu-id="55120-102">Loading DataSet Schema Information from XML</span></span>

<span data-ttu-id="55120-103"><xref:System.Data.DataSet>可以通过编程方式定义 (其表、列、关系和约束) 的架构，也可以通过的**Fill**或**FillSchema**方法创建 <xref:System.Data.Common.DataAdapter> ，或从 XML 文档加载。</span><span class="sxs-lookup"><span data-stu-id="55120-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="55120-104">若要从 XML 文档加载**数据集**架构信息，可以使用**数据集**的**ReadXmlSchema**或**InferXmlSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="55120-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="55120-105">通过**ReadXmlSchema** ，您可以从包含 XML 架构定义语言 (XSD) 架构的文档或使用内联 xml 架构的 xml 文档中加载或推断**数据集**架构信息。</span><span class="sxs-lookup"><span data-stu-id="55120-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="55120-106">**InferXmlSchema** 允许从 xml 文档推断架构，同时忽略指定的某些 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="55120-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55120-107">使用 Web 服务或 XML 序列化传输在内存中创建的**数据集**时，可能不会保留**数据集中**的表排序 (如嵌套关系) 。</span><span class="sxs-lookup"><span data-stu-id="55120-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="55120-108">因此，在这种情况下， **数据集** 的接收方不应依赖于表排序。</span><span class="sxs-lookup"><span data-stu-id="55120-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="55120-109">但是，如果要传输的 **数据集** 的架构是从 XSD 文件中读取的，而不是在内存中创建的，则始终保留表排序。</span><span class="sxs-lookup"><span data-stu-id="55120-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="55120-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="55120-110">ReadXmlSchema</span></span>  

 <span data-ttu-id="55120-111">若要从 XML 文档加载数据**集**的架构而不加载任何数据，则可以使用该**数据集**的**ReadXmlSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="55120-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="55120-112">**ReadXmlSchema** 创建使用 XML 架构定义语言 (XSD) 架构定义的 **数据集** 架构。</span><span class="sxs-lookup"><span data-stu-id="55120-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="55120-113">**ReadXmlSchema**方法获取文件名、流或包含要加载的 XML 文档的**XmlReader**的单个自变量。</span><span class="sxs-lookup"><span data-stu-id="55120-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="55120-114">XML 文档可以仅包含架构，也可以包含与包含数据的 XML 元素内联的架构。</span><span class="sxs-lookup"><span data-stu-id="55120-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="55120-115">有关将内联架构作为 XML 架构写入的详细信息，请参阅 [从 Xml 架构派生数据集关系结构 (XSD) ](deriving-dataset-relational-structure-from-xml-schema-xsd.md)。</span><span class="sxs-lookup"><span data-stu-id="55120-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="55120-116">如果传递到 **ReadXmlSchema** 的 XML 文档不包含内联架构信息，则 **READXMLSCHEMA** 将从 XML 文档中的元素推断架构。</span><span class="sxs-lookup"><span data-stu-id="55120-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="55120-117">如果 **数据集** 已包含架构，则将通过添加新表来扩展当前架构（如果它们尚不存在）。</span><span class="sxs-lookup"><span data-stu-id="55120-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="55120-118">不会将新列添加到现有表中。</span><span class="sxs-lookup"><span data-stu-id="55120-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="55120-119">如果要添加的列已存在于 **数据集中** ，但其类型与 XML 中的列不兼容，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="55120-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="55120-120">有关 **ReadXmlSchema** 如何从 xml 文档推断架构的详细信息，请参阅 [从 Xml 推断数据集关系结构](inferring-dataset-relational-structure-from-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="55120-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="55120-121">尽管**ReadXmlSchema**只加载或推断**数据集**的架构，但**数据集**的**ReadXml**方法会加载或推断 XML 文档中包含的架构和数据。</span><span class="sxs-lookup"><span data-stu-id="55120-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="55120-122">有关详细信息，请参阅 [从 XML 加载数据集](loading-a-dataset-from-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="55120-122">For more information, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="55120-123">下面的代码示例演示如何从 XML 文档或流加载 **数据集** 架构。</span><span class="sxs-lookup"><span data-stu-id="55120-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="55120-124">第一个示例显示了传递给 **ReadXmlSchema** 方法的 XML 架构文件名。</span><span class="sxs-lookup"><span data-stu-id="55120-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="55120-125">第二个示例显示了 **StreamReader**。</span><span class="sxs-lookup"><span data-stu-id="55120-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a><span data-ttu-id="55120-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="55120-126">InferXmlSchema</span></span>  

 <span data-ttu-id="55120-127">你还可以使用**dataset**的**InferXmlSchema**方法来指示**数据集**从 XML 文档推断其架构。</span><span class="sxs-lookup"><span data-stu-id="55120-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="55120-128">**InferXmlSchema** 的功能与 **ReadXml** 的 **XmlReadMode** 相同， **它 (加载** 数据，并推导架构) ，如果读取的文档不包含内联架构，则为 **ReadXmlSchema** 。</span><span class="sxs-lookup"><span data-stu-id="55120-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="55120-129">但是， **InferXmlSchema** 提供了额外的功能，使您可以指定在推断架构时要忽略的特定 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="55120-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="55120-130">**InferXmlSchema** 采用两个必需的参数： XML 文档的位置，由文件名、流或 **XmlReader**指定;和要由操作忽略的 XML 命名空间的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="55120-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="55120-131">例如，考虑以下 XML：</span><span class="sxs-lookup"><span data-stu-id="55120-131">For example, consider the following XML:</span></span>  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>
  <Description od:adotype="203">Soft drinks and teas</Description>
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>
  <ReorderLevel od:adotype="3">10</ReorderLevel>
  <Discontinued od:adotype="11">0</Discontinued>
</Products>  
</NewDataSet>  
```  
  
 <span data-ttu-id="55120-132">由于为前面的 XML 文档中的元素指定了属性， **ReadXmlSchema**方法和**XmlReadMode**为**InferSchema**的**ReadXml**方法将为文档中的每个元素创建表：**类别、类别**名称、**类别**、**说明**、**产品**、 **ProductID** **、** **ReorderLevel**和**废止**。</span><span class="sxs-lookup"><span data-stu-id="55120-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="55120-133"> (有关详细信息，请参阅[从 XML 推断数据集关系结构](inferring-dataset-relational-structure-from-xml.md)。 ) 不过，更合适的结构是仅创建 "**类别**" 和 "**产品**" 表，然后在 "类别" 表中创建 "**类别** **id**"、"类别" 和 "**说明** **" 列**，在**Products**表中创建**ProductID**、 **ReorderLevel**和**废止**列。</span><span class="sxs-lookup"><span data-stu-id="55120-133">(For more information, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="55120-134">若要确保推断的架构忽略 XML 元素中指定的属性，请使用 **InferXmlSchema** 方法并指定要忽略的 **officedata** 的 XML 命名空间，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="55120-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="55120-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="55120-135">See also</span></span>

- [<span data-ttu-id="55120-136">在数据集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="55120-136">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="55120-137">从 XML 架构派生数据集关系结构 (XSD)</span><span class="sxs-lookup"><span data-stu-id="55120-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="55120-138">从 XML 推断数据集关系结构</span><span class="sxs-lookup"><span data-stu-id="55120-138">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="55120-139">从 XML 加载数据集</span><span class="sxs-lookup"><span data-stu-id="55120-139">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="55120-140">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="55120-140">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="55120-141">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="55120-141">ADO.NET Overview</span></span>](../ado-net-overview.md)
