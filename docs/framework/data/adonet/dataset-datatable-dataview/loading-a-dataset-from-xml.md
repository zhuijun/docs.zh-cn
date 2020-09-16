---
title: 从 XML 加载数据集
description: 了解如何从 XML 将内容添加到 ADO.NET 数据集。 .NET Framework 提供了对要加载的内容和数据集结构的灵活性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 77715913c24423c1dc95478977f4e3821e4c247b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545306"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="7ecad-104">从 XML 加载数据集</span><span class="sxs-lookup"><span data-stu-id="7ecad-104">Loading a DataSet from XML</span></span>
<span data-ttu-id="7ecad-105">ADO.NET <xref:System.Data.DataSet> 的内容可以从 XML 流或文档创建。</span><span class="sxs-lookup"><span data-stu-id="7ecad-105">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="7ecad-106">此外，利用 .NET Framework，您可以相当灵活地控制从 XML 中加载哪些信息以及如何创建 <xref:System.Data.DataSet> 的架构（即关系结构）。</span><span class="sxs-lookup"><span data-stu-id="7ecad-106">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="7ecad-107">若要使用 <xref:System.Data.DataSet> XML 中的数据填充，请使用对象的 **ReadXml** 方法 <xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="7ecad-107">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="7ecad-108">**ReadXml**方法从文件、流或**XmlReader**中进行读取，并将 XML 的源以及可选的**XmlReadMode**参数作为参数。</span><span class="sxs-lookup"><span data-stu-id="7ecad-108">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="7ecad-109">有关 **XmlReader**的详细信息，请参阅 [用 XmlTextReader 读取 XML 数据](/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="7ecad-109">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="7ecad-110">**ReadXml**方法读取 XML 流或文档的内容，并加载 <xref:System.Data.DataSet> 带有数据的。</span><span class="sxs-lookup"><span data-stu-id="7ecad-110">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="7ecad-111">它还会根据指定的 XmlReadMode 创建的关系架构 <xref:System.Data.DataSet> ， **XmlReadMode**以及关系架构是否已存在。</span><span class="sxs-lookup"><span data-stu-id="7ecad-111">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="7ecad-112">下表描述了 **XmlReadMode** 参数的选项。</span><span class="sxs-lookup"><span data-stu-id="7ecad-112">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="7ecad-113">选项</span><span class="sxs-lookup"><span data-stu-id="7ecad-113">Option</span></span>|<span data-ttu-id="7ecad-114">说明</span><span class="sxs-lookup"><span data-stu-id="7ecad-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7ecad-115">**Auto**</span><span class="sxs-lookup"><span data-stu-id="7ecad-115">**Auto**</span></span>|<span data-ttu-id="7ecad-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="7ecad-116">This is the default.</span></span> <span data-ttu-id="7ecad-117">检查 XML 并按如下顺序选择最适合的选项：</span><span class="sxs-lookup"><span data-stu-id="7ecad-117">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="7ecad-118">-如果 XML 为 DiffGram，则使用 **diffgram** 。</span><span class="sxs-lookup"><span data-stu-id="7ecad-118">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="7ecad-119">-如果 <xref:System.Data.DataSet> 包含架构或 XML 包含内联架构，则使用 **ReadSchema** 。</span><span class="sxs-lookup"><span data-stu-id="7ecad-119">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="7ecad-120">-如果不 <xref:System.Data.DataSet> 包含架构并且 XML 不包含内联架构，则使用 **InferSchema** 。</span><span class="sxs-lookup"><span data-stu-id="7ecad-120">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="7ecad-121">如果知道要读取的 XML 的格式，则为了获得最佳性能，建议设置显式 **XmlReadMode**，而不是接受 **自动** 默认值。</span><span class="sxs-lookup"><span data-stu-id="7ecad-121">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="7ecad-122">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="7ecad-122">**ReadSchema**</span></span>|<span data-ttu-id="7ecad-123">读取内联架构并加载数据和架构。</span><span class="sxs-lookup"><span data-stu-id="7ecad-123">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="7ecad-124">如果 <xref:System.Data.DataSet> 已包含架构，则新表将从内联架构添加到 <xref:System.Data.DataSet> 中的现有架构。</span><span class="sxs-lookup"><span data-stu-id="7ecad-124">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7ecad-125">如果 <xref:System.Data.DataSet> 中已存在内联架构中的任何表，则将引发异常。</span><span class="sxs-lookup"><span data-stu-id="7ecad-125">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="7ecad-126">您将不能使用 **XmlReadMode**修改现有表的架构。</span><span class="sxs-lookup"><span data-stu-id="7ecad-126">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="7ecad-127">如果 <xref:System.Data.DataSet> 不包含架构，并且没有内联架构，则不会读取任何数据。</span><span class="sxs-lookup"><span data-stu-id="7ecad-127">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="7ecad-128">内联架构可以使用 XML 架构定义语言 (XSD) 架构来定义。</span><span class="sxs-lookup"><span data-stu-id="7ecad-128">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="7ecad-129">有关将内联架构作为 XML 架构写入的详细信息，请参阅 [从 Xml 架构派生数据集关系结构 (XSD) ](deriving-dataset-relational-structure-from-xml-schema-xsd.md)。</span><span class="sxs-lookup"><span data-stu-id="7ecad-129">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="7ecad-130">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="7ecad-130">**IgnoreSchema**</span></span>|<span data-ttu-id="7ecad-131">忽略任何内联架构并将数据加载到现有的 <xref:System.Data.DataSet> 架构中。</span><span class="sxs-lookup"><span data-stu-id="7ecad-131">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="7ecad-132">任何与现有架构不匹配的数据都将被丢弃。</span><span class="sxs-lookup"><span data-stu-id="7ecad-132">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="7ecad-133">如果 <xref:System.Data.DataSet> 中不存在任何架构，则不会加载任何数据。</span><span class="sxs-lookup"><span data-stu-id="7ecad-133">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="7ecad-134">如果数据为 DiffGram，则**IgnoreSchema**具有与 diffgram 相同的功能**DiffGram** *。*</span><span class="sxs-lookup"><span data-stu-id="7ecad-134">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="7ecad-135">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="7ecad-135">**InferSchema**</span></span>|<span data-ttu-id="7ecad-136">忽略任何内联架构并按照 XML 数据的结构推断架构，然后加载数据。</span><span class="sxs-lookup"><span data-stu-id="7ecad-136">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="7ecad-137">如果 <xref:System.Data.DataSet> 已经包含架构，则会通过向现有表中添加列来扩展当前架构。</span><span class="sxs-lookup"><span data-stu-id="7ecad-137">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="7ecad-138">如果不存在表，则不会添加其他表。</span><span class="sxs-lookup"><span data-stu-id="7ecad-138">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="7ecad-139">如果已存在具有不同命名空间的推断表或者任何推断表与现有列发生冲突，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="7ecad-139">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="7ecad-140">有关 **ReadXmlSchema** 如何从 xml 文档推断架构的详细信息，请参阅 [从 Xml 推断数据集关系结构](inferring-dataset-relational-structure-from-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="7ecad-140">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="7ecad-141">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="7ecad-141">**DiffGram**</span></span>|<span data-ttu-id="7ecad-142">读取 DiffGram 并将数据添加到当前架构中。</span><span class="sxs-lookup"><span data-stu-id="7ecad-142">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="7ecad-143">**DiffGram** 合并具有唯一标识符值匹配的现有行的新行。</span><span class="sxs-lookup"><span data-stu-id="7ecad-143">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="7ecad-144">请参见本主题末尾的“合并 XML 中的数据”。</span><span class="sxs-lookup"><span data-stu-id="7ecad-144">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="7ecad-145">有关 Diffgram 的详细信息，请参阅 [diffgram](diffgrams.md)。</span><span class="sxs-lookup"><span data-stu-id="7ecad-145">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="7ecad-146">**Fragment**</span><span class="sxs-lookup"><span data-stu-id="7ecad-146">**Fragment**</span></span>|<span data-ttu-id="7ecad-147">持续读取多个 XML 片断，直至到达流的末尾。</span><span class="sxs-lookup"><span data-stu-id="7ecad-147">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="7ecad-148">与 <xref:System.Data.DataSet> 架构匹配的片断会追加到相应的表。</span><span class="sxs-lookup"><span data-stu-id="7ecad-148">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="7ecad-149">与 <xref:System.Data.DataSet> 架构不匹配的片断将被丢弃。</span><span class="sxs-lookup"><span data-stu-id="7ecad-149">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="7ecad-150">如果将 **XmlReader** 传递给 **ReadXml** ，并且将其定位到 XML 文档中，则 **ReadXml** 将读取到下一个元素节点，并将其视为根元素，一直读取到元素节点的末尾。</span><span class="sxs-lookup"><span data-stu-id="7ecad-150">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="7ecad-151">如果指定 **XmlReadMode**，则此功能不适用。</span><span class="sxs-lookup"><span data-stu-id="7ecad-151">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="7ecad-152">DTD 实体</span><span class="sxs-lookup"><span data-stu-id="7ecad-152">DTD Entities</span></span>  
 <span data-ttu-id="7ecad-153">如果 XML 包含在文档类型定义 (DTD) 架构中定义的实体，则当您尝试 <xref:System.Data.DataSet> 通过将文件名、流或非验证 **XmlReader** 传递到 **ReadXml**来加载时，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="7ecad-153">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="7ecad-154">相反，必须创建 **XmlValidatingReader**，并将 **EntityHandling** 设置为 **entityhandling.expandentities**，并将 **XmlValidatingReader** 传递到 **ReadXml**。</span><span class="sxs-lookup"><span data-stu-id="7ecad-154">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="7ecad-155">在读取实体之前， **XmlValidatingReader** 会将其展开 <xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="7ecad-155">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="7ecad-156">以下代码示例显示如何从 XML 流中加载 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="7ecad-156">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="7ecad-157">第一个示例显示了传递给 **ReadXml** 方法的文件名。</span><span class="sxs-lookup"><span data-stu-id="7ecad-157">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="7ecad-158">第二个示例显示一个字符串，包含使用 <xref:System.IO.StringReader> 加载的 XML。</span><span class="sxs-lookup"><span data-stu-id="7ecad-158">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
> <span data-ttu-id="7ecad-159">如果调用 **ReadXml** 来加载非常大的文件，则可能会遇到性能下降的情况。</span><span class="sxs-lookup"><span data-stu-id="7ecad-159">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="7ecad-160">若要确保 **ReadXml**的最佳性能，请在大文件上 <xref:System.Data.DataTable.BeginLoadData%2A> 为中的每个表调用方法， <xref:System.Data.DataSet> 然后调用 **ReadXml**。</span><span class="sxs-lookup"><span data-stu-id="7ecad-160">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="7ecad-161">最后，为 <xref:System.Data.DataTable.EndLoadData%2A> 中的每个表调用 <xref:System.Data.DataSet>，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="7ecad-161">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
> <span data-ttu-id="7ecad-162">如果的 XSD 架构 <xref:System.Data.DataSet> 包含 **targetNamespace**，则数据可能不会被读取，并且你可能会在调用 **ReadXml** 以加载 <xref:System.Data.DataSet> 包含无限定命名空间的元素的 XML 时遇到异常。</span><span class="sxs-lookup"><span data-stu-id="7ecad-162">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="7ecad-163">若要在这种情况下读取未限定的元素，请在 XSD 架构中将 **elementFormDefault** 设置为等于 "合格的"。</span><span class="sxs-lookup"><span data-stu-id="7ecad-163">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="7ecad-164">例如：</span><span class="sxs-lookup"><span data-stu-id="7ecad-164">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="7ecad-165">合并 XML 中的数据</span><span class="sxs-lookup"><span data-stu-id="7ecad-165">Merging Data from XML</span></span>  
 <span data-ttu-id="7ecad-166">如果 <xref:System.Data.DataSet> 已经包含数据，则会向已存在于 <xref:System.Data.DataSet> 中的数据添加 XML 中的新数据。</span><span class="sxs-lookup"><span data-stu-id="7ecad-166">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7ecad-167">**ReadXml** 不会从 XML 合并到 <xref:System.Data.DataSet> 具有匹配主键的任何行信息。</span><span class="sxs-lookup"><span data-stu-id="7ecad-167">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="7ecad-168">若要使用 XML 中的新信息覆盖现有行信息，请使用 **ReadXml** 创建新的 <xref:System.Data.DataSet> ，然后将 <xref:System.Data.DataSet.Merge%2A> 新的 <xref:System.Data.DataSet> 引入现有 <xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="7ecad-168">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7ecad-169">请注意，使用**ReadXML**和**diffgram**的**XmlReadMode**加载 diffgram 将合并具有相同唯一标识符的行。</span><span class="sxs-lookup"><span data-stu-id="7ecad-169">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ecad-170">请参阅</span><span class="sxs-lookup"><span data-stu-id="7ecad-170">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7ecad-171">在数据集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="7ecad-171">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="7ecad-172">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="7ecad-172">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="7ecad-173">从 XML 架构派生数据集关系结构 (XSD)</span><span class="sxs-lookup"><span data-stu-id="7ecad-173">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="7ecad-174">从 XML 推断数据集关系结构</span><span class="sxs-lookup"><span data-stu-id="7ecad-174">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="7ecad-175">从 XML 加载数据集架构信息</span><span class="sxs-lookup"><span data-stu-id="7ecad-175">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="7ecad-176">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="7ecad-176">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="7ecad-177">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="7ecad-177">ADO.NET Overview</span></span>](../ado-net-overview.md)
