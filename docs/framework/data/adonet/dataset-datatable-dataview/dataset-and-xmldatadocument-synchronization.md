---
title: 数据集和 XmlDataDocument 同步
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: 2790f0a9edd5bfde96683e00725dd04555379adf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153295"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="77752-102">数据集和 XmlDataDocument 同步</span><span class="sxs-lookup"><span data-stu-id="77752-102">DataSet and XmlDataDocument Synchronization</span></span>

<span data-ttu-id="77752-103">ADO.NET <xref:System.Data.DataSet> 为您提供了数据的关系表示形式。</span><span class="sxs-lookup"><span data-stu-id="77752-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="77752-104">若要实现分层数据访问，可以使用 .NET Framework 中的可用 XML 类。</span><span class="sxs-lookup"><span data-stu-id="77752-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="77752-105">以前，数据的这两种表示形式是单独使用的。</span><span class="sxs-lookup"><span data-stu-id="77752-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="77752-106">不过，.NET Framework 通过分别通过 **DataSet** 对象和对象实现对数据的关系和分层表示形式的实时同步访问 <xref:System.Xml.XmlDataDocument> 。</span><span class="sxs-lookup"><span data-stu-id="77752-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="77752-107">如果 **数据集** 与 **XmlDataDocument**同步，则这两个对象使用单个数据集。</span><span class="sxs-lookup"><span data-stu-id="77752-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="77752-108">这意味着，如果对 **数据集**进行了更改，则所做的更改将反映在 **XmlDataDocument**中，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="77752-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="77752-109">**数据集**和**XmlDataDocument**之间的关系通过允许单个应用程序、使用单个数据集，访问围绕**数据集**构建的整个服务套件 (例如 Web 窗体和 Windows 窗体控件以及 Visual Studio .NET 设计器) ，以及 Xml 服务套件，包括可扩展样式表语言 (XSL) 、XSL 转换 (XSLT) 和 XML 路径语言 (XPath) 。</span><span class="sxs-lookup"><span data-stu-id="77752-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="77752-110">您不必选择使应用程序以哪一组服务为目标，这两组服务都可用。</span><span class="sxs-lookup"><span data-stu-id="77752-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="77752-111">可以通过多种方式将 **数据集** 与 **XmlDataDocument**同步。</span><span class="sxs-lookup"><span data-stu-id="77752-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="77752-112">您可以：</span><span class="sxs-lookup"><span data-stu-id="77752-112">You can:</span></span>  
  
- <span data-ttu-id="77752-113">使用架构 (（即关系结构) 和数据）填充 **数据集** ，然后将其与新的 **XmlDataDocument**同步。</span><span class="sxs-lookup"><span data-stu-id="77752-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="77752-114">这将提供现有关系数据的分层视图。</span><span class="sxs-lookup"><span data-stu-id="77752-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="77752-115">例如：</span><span class="sxs-lookup"><span data-stu-id="77752-115">For example:</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
- <span data-ttu-id="77752-116">使用仅限架构 (（如强类型化**数据集**) ）填充**数据集**，并将其与**XMLDATADOCUMENT**同步，然后从 XML 文档加载**XmlDataDocument** 。</span><span class="sxs-lookup"><span data-stu-id="77752-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="77752-117">这将提供现有分层数据的关系视图。</span><span class="sxs-lookup"><span data-stu-id="77752-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="77752-118">**数据集**架构中的表名和列名必须与要与其同步的 XML 元素的名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="77752-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="77752-119">该匹配区分大小写。</span><span class="sxs-lookup"><span data-stu-id="77752-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="77752-120">请注意，该 **数据集** 的架构只需要匹配您要在关系视图中公开的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="77752-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="77752-121">这样，就可以具有非常大的 XML 文档，而该文档上可以有非常小的关系“窗口”。</span><span class="sxs-lookup"><span data-stu-id="77752-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="77752-122">即使**数据集**只公开其中的一小部分， **XmlDataDocument**仍保留整个 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="77752-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="77752-123"> (有关此情况的详细示例，请参阅 [使用 XmlDataDocument 同步数据集](synchronizing-a-dataset-with-an-xmldatadocument.md)。 ) </span><span class="sxs-lookup"><span data-stu-id="77752-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="77752-124">下面的代码示例演示了创建 **数据集** 并填充其架构，然后将其与 **XmlDataDocument**同步的步骤。</span><span class="sxs-lookup"><span data-stu-id="77752-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="77752-125">请注意， **DataSet** 架构只需要与 **XmlDataDocument** 中要使用 **数据集**公开的元素匹配。</span><span class="sxs-lookup"><span data-stu-id="77752-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     <span data-ttu-id="77752-126">如果 **XmlDataDocument** 与包含数据的 **数据集** 同步，则无法加载它。</span><span class="sxs-lookup"><span data-stu-id="77752-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="77752-127">否则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="77752-127">An exception will be thrown.</span></span>  
  
- <span data-ttu-id="77752-128">创建新的**XmlDataDocument**并从 XML 文档加载它，然后使用**XmlDataDocument**的**DataSet**属性访问数据的关系视图。</span><span class="sxs-lookup"><span data-stu-id="77752-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="77752-129">你需要设置**数据集**的架构，然后才能使用**dataset**查看**XmlDataDocument**中的任何数据。</span><span class="sxs-lookup"><span data-stu-id="77752-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="77752-130">同样， **数据集** 架构中的表名和列名必须与要与其同步的 XML 元素的名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="77752-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="77752-131">该匹配区分大小写。</span><span class="sxs-lookup"><span data-stu-id="77752-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="77752-132">下面的代码示例演示如何访问 **XmlDataDocument**中数据的关系视图。</span><span class="sxs-lookup"><span data-stu-id="77752-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 <span data-ttu-id="77752-133">同步 **XmlDataDocument** 与 **数据集** 的另一个优点是，XML 文档的保真度得以保留。</span><span class="sxs-lookup"><span data-stu-id="77752-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="77752-134">如果使用**ReadXml**从 xml 文档填充数据**集**，则当使用**WRITEXML**将数据写回 xml 文档时，它可能会与原始 XML 文档有很大差异。</span><span class="sxs-lookup"><span data-stu-id="77752-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="77752-135">这是因为 **数据集** 不会保留 XML 文档中的格式设置，如空白或层次结构信息（例如元素顺序）。</span><span class="sxs-lookup"><span data-stu-id="77752-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="77752-136">**数据集**还不包含 XML 文档中的元素，因为这些元素与**DataSet**的架构不匹配。</span><span class="sxs-lookup"><span data-stu-id="77752-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="77752-137">将 **XmlDataDocument** 与 **数据集** 同步，可以在 **XmlDataDocument**中维护原始 XML 文档的格式设置和分层元素结构，而 **数据集** 只包含适用于该数据 **集**的数据和架构信息。</span><span class="sxs-lookup"><span data-stu-id="77752-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="77752-138">将 **数据集** 与 **XmlDataDocument**同步时，结果可能会有所不同，具体取决于是否嵌套了您的 <xref:System.Data.DataRelation> 对象。</span><span class="sxs-lookup"><span data-stu-id="77752-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="77752-139">有关详细信息，请参阅 [嵌套 datarelation](nesting-datarelations.md)。</span><span class="sxs-lookup"><span data-stu-id="77752-139">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77752-140">本节内容</span><span class="sxs-lookup"><span data-stu-id="77752-140">In This Section</span></span>  

 [<span data-ttu-id="77752-141">将数据集和 XmlDataDocument 同步</span><span class="sxs-lookup"><span data-stu-id="77752-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="77752-142">演示如何使用**XmlDataDocument**将强类型化**数据集**与最小架构同步。</span><span class="sxs-lookup"><span data-stu-id="77752-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="77752-143">对数据集执行 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="77752-143">Performing an XPath Query on a DataSet</span></span>](performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="77752-144">演示如何对 **数据集**的内容执行 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="77752-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="77752-145">将 XSLT 转换应用于 DataSet</span><span class="sxs-lookup"><span data-stu-id="77752-145">Applying an XSLT Transform to a DataSet</span></span>](applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="77752-146">演示如何将 XSLT 转换应用于 **数据集**的内容。</span><span class="sxs-lookup"><span data-stu-id="77752-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="77752-147">相关章节</span><span class="sxs-lookup"><span data-stu-id="77752-147">Related Sections</span></span>  

 [<span data-ttu-id="77752-148">在数据集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="77752-148">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="77752-149">介绍如何将数据 **集** 与 xml 作为数据源进行交互，包括将 **数据集** 的内容作为 XML 数据进行加载和保存。</span><span class="sxs-lookup"><span data-stu-id="77752-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="77752-150">嵌套 DataRelation</span><span class="sxs-lookup"><span data-stu-id="77752-150">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="77752-151">讨论嵌套的 **DataRelation** 对象在以 XML 数据形式表示 **数据集** 的内容时的重要性，并描述如何创建这些关系。</span><span class="sxs-lookup"><span data-stu-id="77752-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="77752-152">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="77752-152">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="77752-153">介绍 **数据集** ，以及如何使用它来管理应用程序数据以及与包括关系数据库和 XML 在内的数据源进行交互。</span><span class="sxs-lookup"><span data-stu-id="77752-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="77752-154">包含有关 **XmlDataDocument** 类的参考信息。</span><span class="sxs-lookup"><span data-stu-id="77752-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77752-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="77752-155">See also</span></span>

- [<span data-ttu-id="77752-156">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="77752-156">ADO.NET Overview</span></span>](../ado-net-overview.md)
