---
title: DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: fe6adac35c157b454f5e33d3526196d4f408fd89
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546863"
---
# <a name="dataviews"></a><span data-ttu-id="1ae47-102">DataView</span><span class="sxs-lookup"><span data-stu-id="1ae47-102">DataViews</span></span>
<span data-ttu-id="1ae47-103">您可以利用 <xref:System.Data.DataView> 创建存储在 <xref:System.Data.DataTable>（一种通常在数据绑定应用程序中使用的功能）中的数据的不同视图。</span><span class="sxs-lookup"><span data-stu-id="1ae47-103">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="1ae47-104">使用 **DataView**，你可以使用不同的排序顺序公开表中的数据，并且可以按行状态或基于筛选器表达式来筛选数据。</span><span class="sxs-lookup"><span data-stu-id="1ae47-104">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>

 <span data-ttu-id="1ae47-105">**DataView**提供基础**DataTable**中的数据的动态视图：内容、排序和成员身份在更改发生时反映更改。</span><span class="sxs-lookup"><span data-stu-id="1ae47-105">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="1ae47-106">此行为不同于**DataTable**的**Select**方法，该方法 <xref:System.Data.DataRow> 根据特定筛选器和/或排序顺序从表返回数组：此内容反映了对基础表的更改，但其成员资格和顺序保持静态。</span><span class="sxs-lookup"><span data-stu-id="1ae47-106">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: this content reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="1ae47-107">**DataView**的动态功能使其成为数据绑定应用程序的理想之选。</span><span class="sxs-lookup"><span data-stu-id="1ae47-107">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>

 <span data-ttu-id="1ae47-108">数据 **视图为您提供了** 一组数据的动态视图，这与数据库视图非常类似，您可以将不同的排序和筛选条件应用于该视图。</span><span class="sxs-lookup"><span data-stu-id="1ae47-108">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="1ae47-109">但是，与数据库视图不同， **DataView** 不能被视为表，也不能提供联接的表的视图。</span><span class="sxs-lookup"><span data-stu-id="1ae47-109">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="1ae47-110">还不能排除源表中存在的列，也不能追加源表中不存在的列，如计算列。</span><span class="sxs-lookup"><span data-stu-id="1ae47-110">You also cannot exclude columns that exist in the source table or append columns that do not exist in the source table, such as computational columns.</span></span>

 <span data-ttu-id="1ae47-111">您可以使用 <xref:System.Data.DataView.DataViewManager%2A> 来管理 **数据集中**所有表的视图设置。</span><span class="sxs-lookup"><span data-stu-id="1ae47-111">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="1ae47-112">**DataViewManager**为你提供了一种方便的方法来管理每个表的默认视图设置。</span><span class="sxs-lookup"><span data-stu-id="1ae47-112">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="1ae47-113">将控件绑定到 **数据集**的多个表时，绑定到 **DataViewManager** 是理想的选择。</span><span class="sxs-lookup"><span data-stu-id="1ae47-113">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1ae47-114">本节内容</span><span class="sxs-lookup"><span data-stu-id="1ae47-114">In This Section</span></span>
 <span data-ttu-id="1ae47-115">[创建 DataView](creating-a-dataview.md)介绍如何为**DataTable**创建**DataView** 。</span><span class="sxs-lookup"><span data-stu-id="1ae47-115">[Creating a DataView](creating-a-dataview.md) Describes how to create a **DataView** for a **DataTable**.</span></span>

 <span data-ttu-id="1ae47-116">[排序和筛选数据](sorting-and-filtering-data.md) 描述如何设置 **DataView** 的属性以返回满足特定筛选条件的数据行子集，或返回按特定排序顺序返回的数据。</span><span class="sxs-lookup"><span data-stu-id="1ae47-116">[Sorting and Filtering Data](sorting-and-filtering-data.md) Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>

 <span data-ttu-id="1ae47-117">[Datarow 和 datarowview](datarows-and-datarowviews.md) 描述如何访问由 **DataView**公开的数据。</span><span class="sxs-lookup"><span data-stu-id="1ae47-117">[DataRows and DataRowViews](datarows-and-datarowviews.md) Describes how to access the data exposed by the **DataView**.</span></span>

 <span data-ttu-id="1ae47-118">[查找行](finding-rows.md) 介绍如何在 **DataView**中查找特定的行。</span><span class="sxs-lookup"><span data-stu-id="1ae47-118">[Finding Rows](finding-rows.md) Describes how to find a particular row in a **DataView**.</span></span>

 <span data-ttu-id="1ae47-119">[Childview 和关系](childviews-and-relations.md) 介绍如何使用 **DataView**创建父子关系中的数据视图。</span><span class="sxs-lookup"><span data-stu-id="1ae47-119">[ChildViews and Relations](childviews-and-relations.md) Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>

 <span data-ttu-id="1ae47-120">[修改 dataview](modifying-dataviews.md)介绍如何通过**DataView**修改基础**DataTable**中的数据，包括启用或禁用更新。</span><span class="sxs-lookup"><span data-stu-id="1ae47-120">[Modifying DataViews](modifying-dataviews.md) Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>

 <span data-ttu-id="1ae47-121">[处理 DataView 事件](handling-dataview-events.md) 介绍如何使用 **ListChanged** 事件在更新 **DataView** 的内容或顺序时接收通知。</span><span class="sxs-lookup"><span data-stu-id="1ae47-121">[Handling DataView Events](handling-dataview-events.md) Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>

 <span data-ttu-id="1ae47-122">[管理 dataview](managing-dataviews.md)介绍如何使用**DataViewManager**来管理**数据集中**每个表的**DataView**设置。</span><span class="sxs-lookup"><span data-stu-id="1ae47-122">[Managing DataViews](managing-dataviews.md) Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1ae47-123">相关章节</span><span class="sxs-lookup"><span data-stu-id="1ae47-123">Related Sections</span></span>
 <span data-ttu-id="1ae47-124">[ASP.NET Web 应用程序](/previous-versions/655cec97(v=vs.100)) 提供有关创建 ASP.NET 应用程序、Web 窗体和 Web 服务的概述和详细的分步过程。</span><span class="sxs-lookup"><span data-stu-id="1ae47-124">[ASP.NET Web Applications](/previous-versions/655cec97(v=vs.100)) Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>

 <span data-ttu-id="1ae47-125">[Windows 应用程序](/previous-versions/ms184421(v=vs.100)) 提供有关使用 Windows 窗体和控制台应用程序的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1ae47-125">[Windows Applications](/previous-versions/ms184421(v=vs.100)) Provides detailed information about working with Windows Forms and console applications.</span></span>

 <span data-ttu-id="1ae47-126">[数据集、数据表和 dataview](index.md) 介绍 **DataSet** 对象以及如何使用它来管理应用程序数据。</span><span class="sxs-lookup"><span data-stu-id="1ae47-126">[DataSets, DataTables, and DataViews](index.md) Describes the **DataSet** object and how you can use it to manage application data.</span></span>

 <span data-ttu-id="1ae47-127">[数据表](datatables.md) 介绍 **DataTable** 对象，以及如何使用它来管理应用程序数据或将其作为 **数据集**的一部分。</span><span class="sxs-lookup"><span data-stu-id="1ae47-127">[DataTables](datatables.md) Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>

 <span data-ttu-id="1ae47-128">[ADO.NET](../index.md) 介绍 ADO.NET 的体系结构和组件，以及如何使用 ADO.NET 来访问现有的数据源和管理应用程序数据。</span><span class="sxs-lookup"><span data-stu-id="1ae47-128">[ADO.NET](../index.md) Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ae47-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="1ae47-129">See also</span></span>

- [<span data-ttu-id="1ae47-130">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="1ae47-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
