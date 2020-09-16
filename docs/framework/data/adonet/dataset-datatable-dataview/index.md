---
title: 数据集、数据表和数据视图
description: 了解使用 ADO.NET 数据集（提供一致的关系编程模型的数据的内存驻留表示形式）的几种方法。
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 4e1c0ea5f1de1715ad8e862e6a3ed7370b53c6ce
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555859"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="0ce4d-103">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="0ce4d-103">DataSets, DataTables, and DataViews</span></span>

<span data-ttu-id="0ce4d-104">ADO.NET <xref:System.Data.DataSet> 是数据的一种内存驻留表示形式，无论它包含的数据来自什么数据源，都会提供一致的关系编程模型。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="0ce4d-105"><xref:System.Data.DataSet> 表示整个数据集，其中包含对数据进行包含、排序和约束的表以及表间的关系。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
<span data-ttu-id="0ce4d-106">使用 <xref:System.Data.DataSet> 的方法有若干种，这些方法可以单独应用，也可以结合应用。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="0ce4d-107">你可以：</span><span class="sxs-lookup"><span data-stu-id="0ce4d-107">You can:</span></span>  
  
- <span data-ttu-id="0ce4d-108">以编程方式在 <xref:System.Data.DataTable> 中创建 <xref:System.Data.DataRelation>、<xref:System.Data.Constraint> 和 <xref:System.Data.DataSet>，并使用数据填充表。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="0ce4d-109">通过 <xref:System.Data.DataSet> 用现有关系数据源中的数据表填充 `DataAdapter`。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="0ce4d-110">使用 XML 加载和保持 <xref:System.Data.DataSet> 内容。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="0ce4d-111">有关详细信息，请参阅[在数据集中使用 XML](using-xml-in-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
<span data-ttu-id="0ce4d-112">强类型化的 <xref:System.Data.DataSet> 也可以使用 XML Web services 来进行传输。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="0ce4d-113"><xref:System.Data.DataSet> 的设计使其成为使用 XML Web services 传输数据的理想选择。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="0ce4d-114">有关 XML Web service 的概述，请参阅 [XML Web service 概述](/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-114">For an overview of XML Web services, see [XML Web Services Overview](/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="0ce4d-115">有关通过 XML Web service 使用 <xref:System.Data.DataSet> 的示例，请参阅[通过 XML Web service 使用数据集](consuming-a-dataset-from-an-xml-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ce4d-116">在本节中</span><span class="sxs-lookup"><span data-stu-id="0ce4d-116">In this section</span></span>

 [<span data-ttu-id="0ce4d-117">安全指南</span><span class="sxs-lookup"><span data-stu-id="0ce4d-117">Security guidance</span></span>](security-guidance.md)  
 <span data-ttu-id="0ce4d-118">提供和的安全 <xref:System.Data.DataSet> 指南 <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-118">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="0ce4d-119">创建数据集</span><span class="sxs-lookup"><span data-stu-id="0ce4d-119">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="0ce4d-120">描述创建 <xref:System.Data.DataSet> 实例的语法。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-120">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="0ce4d-121">将数据表添加到数据集中</span><span class="sxs-lookup"><span data-stu-id="0ce4d-121">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="0ce4d-122">描述如何创建表和列并将其添加到 <xref:System.Data.DataSet> 中。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-122">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="0ce4d-123">添加 DataRelation</span><span class="sxs-lookup"><span data-stu-id="0ce4d-123">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="0ce4d-124">描述如何创建 <xref:System.Data.DataSet> 中表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-124">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="0ce4d-125">导航 DataRelation</span><span class="sxs-lookup"><span data-stu-id="0ce4d-125">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="0ce4d-126">描述如何使用 <xref:System.Data.DataSet> 中表之间的关系来返回具有父子关系的子行或父行。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-126">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="0ce4d-127">合并数据集内容</span><span class="sxs-lookup"><span data-stu-id="0ce4d-127">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="0ce4d-128">描述如何将一个 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 数组的内容合并到另一个 <xref:System.Data.DataSet> 中。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-128">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="0ce4d-129">复制数据集内容</span><span class="sxs-lookup"><span data-stu-id="0ce4d-129">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="0ce4d-130">描述如何创建可包含架构和指定数据的 <xref:System.Data.DataSet> 副本。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-130">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="0ce4d-131">处理数据集事件</span><span class="sxs-lookup"><span data-stu-id="0ce4d-131">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="0ce4d-132">描述 <xref:System.Data.DataSet> 的事件并说明如何使用这些事件。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-132">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="0ce4d-133">类型化数据集</span><span class="sxs-lookup"><span data-stu-id="0ce4d-133">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="0ce4d-134">描述类型化 <xref:System.Data.DataSet> 的定义并说明如何创建和使用。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-134">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="0ce4d-135">DataTables</span><span class="sxs-lookup"><span data-stu-id="0ce4d-135">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="0ce4d-136">描述如何创建 <xref:System.Data.DataTable>、定义架构和处理数据。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-136">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="0ce4d-137">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="0ce4d-137">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="0ce4d-138">描述如何创建和使用 <xref:System.Data.DataTableReader>。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-138">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="0ce4d-139">DataView</span><span class="sxs-lookup"><span data-stu-id="0ce4d-139">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="0ce4d-140">描述如何创建和使用 `DataViews` 以及如何使用 <xref:System.Data.DataView> 事件。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-140">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="0ce4d-141">在数据集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="0ce4d-141">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="0ce4d-142">描述 <xref:System.Data.DataSet> 如何作为数据源与 XML 进行交互（包括以 XML 数据的形式加载和保持 <xref:System.Data.DataSet> 的内容）。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-142">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="0ce4d-143">通过 XML Web 服务使用数据集</span><span class="sxs-lookup"><span data-stu-id="0ce4d-143">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="0ce4d-144">描述如何创建使用 <xref:System.Data.DataSet> 来传输数据的 XML Web services。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-144">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0ce4d-145">相关章节</span><span class="sxs-lookup"><span data-stu-id="0ce4d-145">Related sections</span></span>

 [<span data-ttu-id="0ce4d-146">ADO.NET 新增功能</span><span class="sxs-lookup"><span data-stu-id="0ce4d-146">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="0ce4d-147">介绍 ADO.NET 中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-147">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="0ce4d-148">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="0ce4d-148">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="0ce4d-149">提供对 ADO.NET 设计和组件的介绍。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-149">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="0ce4d-150">从 DataAdapter 填充数据集</span><span class="sxs-lookup"><span data-stu-id="0ce4d-150">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="0ce4d-151">描述如何从数据源加载包含数据的**数据集**。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-151">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="0ce4d-152">使用 DataAdapter 更新数据源</span><span class="sxs-lookup"><span data-stu-id="0ce4d-152">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="0ce4d-153">描述如何将对**数据集**中的数据的更改解析回数据源。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-153">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="0ce4d-154">将现有约束添加到数据集</span><span class="sxs-lookup"><span data-stu-id="0ce4d-154">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="0ce4d-155">描述如何使用数据源中的主键信息填充**数据集**。</span><span class="sxs-lookup"><span data-stu-id="0ce4d-155">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce4d-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="0ce4d-156">See also</span></span>

- [<span data-ttu-id="0ce4d-157">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0ce4d-157">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="0ce4d-158">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="0ce4d-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
