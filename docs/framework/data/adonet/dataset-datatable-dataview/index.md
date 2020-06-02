---
title: 数据集、数据表和数据视图
description: 了解使用 ADO.NET 数据集（提供一致的关系编程模型的数据的内存驻留表示形式）的几种方法。
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: f6562452261cbc1f7ee36fb264b858646a42e4f5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286891"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="6d751-103">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="6d751-103">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="6d751-104">ADO.NET <xref:System.Data.DataSet> 是数据的一种内存驻留表示形式，无论它包含的数据来自什么数据源，都会提供一致的关系编程模型。</span><span class="sxs-lookup"><span data-stu-id="6d751-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="6d751-105"><xref:System.Data.DataSet> 表示整个数据集，其中包含对数据进行包含、排序和约束的表以及表间的关系。</span><span class="sxs-lookup"><span data-stu-id="6d751-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="6d751-106">使用 <xref:System.Data.DataSet> 的方法有若干种，这些方法可以单独应用，也可以结合应用。</span><span class="sxs-lookup"><span data-stu-id="6d751-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="6d751-107">方法：</span><span class="sxs-lookup"><span data-stu-id="6d751-107">You can:</span></span>  
  
- <span data-ttu-id="6d751-108">以编程方式在 <xref:System.Data.DataTable> 中创建 <xref:System.Data.DataRelation>、<xref:System.Data.Constraint> 和 <xref:System.Data.DataSet>，并使用数据填充表。</span><span class="sxs-lookup"><span data-stu-id="6d751-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="6d751-109">通过 <xref:System.Data.DataSet> 用现有关系数据源中的数据表填充 `DataAdapter`。</span><span class="sxs-lookup"><span data-stu-id="6d751-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="6d751-110">使用 XML 加载和保持 <xref:System.Data.DataSet> 内容。</span><span class="sxs-lookup"><span data-stu-id="6d751-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="6d751-111">有关详细信息，请参阅[在数据集中使用 XML](using-xml-in-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="6d751-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="6d751-112">强类型化的 <xref:System.Data.DataSet> 也可以使用 XML Web services 来进行传输。</span><span class="sxs-lookup"><span data-stu-id="6d751-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="6d751-113"><xref:System.Data.DataSet> 的设计使其成为使用 XML Web services 传输数据的理想选择。</span><span class="sxs-lookup"><span data-stu-id="6d751-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="6d751-114">有关 XML Web service 的概述，请参阅 [XML Web service 概述](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="6d751-114">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="6d751-115">有关通过 XML Web service 使用 <xref:System.Data.DataSet> 的示例，请参阅[通过 XML Web service 使用数据集](consuming-a-dataset-from-an-xml-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="6d751-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d751-116">本节内容</span><span class="sxs-lookup"><span data-stu-id="6d751-116">In This Section</span></span>  
 [<span data-ttu-id="6d751-117">创建数据集</span><span class="sxs-lookup"><span data-stu-id="6d751-117">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="6d751-118">描述创建 <xref:System.Data.DataSet> 实例的语法。</span><span class="sxs-lookup"><span data-stu-id="6d751-118">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="6d751-119">将数据表添加到数据集中</span><span class="sxs-lookup"><span data-stu-id="6d751-119">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="6d751-120">描述如何创建表和列并将其添加到 <xref:System.Data.DataSet> 中。</span><span class="sxs-lookup"><span data-stu-id="6d751-120">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="6d751-121">添加 DataRelation</span><span class="sxs-lookup"><span data-stu-id="6d751-121">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="6d751-122">描述如何创建 <xref:System.Data.DataSet> 中表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="6d751-122">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="6d751-123">导航 DataRelation</span><span class="sxs-lookup"><span data-stu-id="6d751-123">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="6d751-124">描述如何使用 <xref:System.Data.DataSet> 中表之间的关系来返回具有父子关系的子行或父行。</span><span class="sxs-lookup"><span data-stu-id="6d751-124">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="6d751-125">合并数据集内容</span><span class="sxs-lookup"><span data-stu-id="6d751-125">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="6d751-126">描述如何将一个 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 数组的内容合并到另一个 <xref:System.Data.DataSet> 中。</span><span class="sxs-lookup"><span data-stu-id="6d751-126">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="6d751-127">复制数据集内容</span><span class="sxs-lookup"><span data-stu-id="6d751-127">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="6d751-128">描述如何创建可包含架构和指定数据的 <xref:System.Data.DataSet> 副本。</span><span class="sxs-lookup"><span data-stu-id="6d751-128">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="6d751-129">处理数据集事件</span><span class="sxs-lookup"><span data-stu-id="6d751-129">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="6d751-130">描述 <xref:System.Data.DataSet> 的事件并说明如何使用这些事件。</span><span class="sxs-lookup"><span data-stu-id="6d751-130">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="6d751-131">类型化数据集</span><span class="sxs-lookup"><span data-stu-id="6d751-131">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="6d751-132">描述类型化 <xref:System.Data.DataSet> 的定义并说明如何创建和使用。</span><span class="sxs-lookup"><span data-stu-id="6d751-132">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="6d751-133">DataTables</span><span class="sxs-lookup"><span data-stu-id="6d751-133">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="6d751-134">描述如何创建 <xref:System.Data.DataTable>、定义架构和处理数据。</span><span class="sxs-lookup"><span data-stu-id="6d751-134">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="6d751-135">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="6d751-135">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="6d751-136">描述如何创建和使用 <xref:System.Data.DataTableReader>。</span><span class="sxs-lookup"><span data-stu-id="6d751-136">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="6d751-137">DataView</span><span class="sxs-lookup"><span data-stu-id="6d751-137">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="6d751-138">描述如何创建和使用 `DataViews` 以及如何使用 <xref:System.Data.DataView> 事件。</span><span class="sxs-lookup"><span data-stu-id="6d751-138">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="6d751-139">在数据集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="6d751-139">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="6d751-140">描述 <xref:System.Data.DataSet> 如何作为数据源与 XML 进行交互（包括以 XML 数据的形式加载和保持 <xref:System.Data.DataSet> 的内容）。</span><span class="sxs-lookup"><span data-stu-id="6d751-140">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="6d751-141">通过 XML Web 服务使用数据集</span><span class="sxs-lookup"><span data-stu-id="6d751-141">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="6d751-142">描述如何创建使用 <xref:System.Data.DataSet> 来传输数据的 XML Web services。</span><span class="sxs-lookup"><span data-stu-id="6d751-142">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6d751-143">相关章节</span><span class="sxs-lookup"><span data-stu-id="6d751-143">Related Sections</span></span>  
 [<span data-ttu-id="6d751-144">ADO.NET 新增功能</span><span class="sxs-lookup"><span data-stu-id="6d751-144">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="6d751-145">介绍 ADO.NET 中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="6d751-145">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="6d751-146">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="6d751-146">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="6d751-147">提供对 ADO.NET 设计和组件的介绍。</span><span class="sxs-lookup"><span data-stu-id="6d751-147">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="6d751-148">从 DataAdapter 填充数据集</span><span class="sxs-lookup"><span data-stu-id="6d751-148">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="6d751-149">描述如何从数据源加载包含数据的**数据集**。</span><span class="sxs-lookup"><span data-stu-id="6d751-149">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="6d751-150">使用 DataAdapter 更新数据源</span><span class="sxs-lookup"><span data-stu-id="6d751-150">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="6d751-151">描述如何将对**数据集**中的数据的更改解析回数据源。</span><span class="sxs-lookup"><span data-stu-id="6d751-151">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="6d751-152">将现有约束添加到数据集</span><span class="sxs-lookup"><span data-stu-id="6d751-152">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="6d751-153">描述如何使用数据源中的主键信息填充**数据集**。</span><span class="sxs-lookup"><span data-stu-id="6d751-153">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d751-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d751-154">See also</span></span>

- [<span data-ttu-id="6d751-155">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6d751-155">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="6d751-156">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="6d751-156">ADO.NET Overview</span></span>](../ado-net-overview.md)
