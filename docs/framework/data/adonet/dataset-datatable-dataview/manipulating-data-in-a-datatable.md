---
title: 操作数据表中的数据
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: 3f98832b4aa9361346d06830f2f004fa374222ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201325"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="4e59b-102">操作数据表中的数据</span><span class="sxs-lookup"><span data-stu-id="4e59b-102">Manipulating Data in a DataTable</span></span>

<span data-ttu-id="4e59b-103">在 <xref:System.Data.DataTable> 中创建 <xref:System.Data.DataSet> 之后，您执行的活动可以与使用数据库中的表时执行的活动相同。</span><span class="sxs-lookup"><span data-stu-id="4e59b-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="4e59b-104">您可以添加、查看、编辑和删除表中的数据；可以监视错误和事件；并且可以查询表中的数据。</span><span class="sxs-lookup"><span data-stu-id="4e59b-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="4e59b-105">在修改 **DataTable**中的数据时，还可以验证这些更改是否准确，并确定是否以编程方式接受或拒绝更改。</span><span class="sxs-lookup"><span data-stu-id="4e59b-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e59b-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="4e59b-106">In This Section</span></span>  

 [<span data-ttu-id="4e59b-107">将数据添加到数据表中</span><span class="sxs-lookup"><span data-stu-id="4e59b-107">Adding Data to a DataTable</span></span>](adding-data-to-a-datatable.md)  
 <span data-ttu-id="4e59b-108">说明如何创建新行并将它们添加到表中。</span><span class="sxs-lookup"><span data-stu-id="4e59b-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="4e59b-109">查看数据表中的数据</span><span class="sxs-lookup"><span data-stu-id="4e59b-109">Viewing Data in a DataTable</span></span>](viewing-data-in-a-datatable.md)  
 <span data-ttu-id="4e59b-110">说明如何访问行中的数据，包括数据的原始版本和当前版本。</span><span class="sxs-lookup"><span data-stu-id="4e59b-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="4e59b-111">加载方法</span><span class="sxs-lookup"><span data-stu-id="4e59b-111">The Load Method</span></span>](the-load-method.md)  
 <span data-ttu-id="4e59b-112">介绍如何使用 **Load** 方法来填充包含行的 **DataTable** 。</span><span class="sxs-lookup"><span data-stu-id="4e59b-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="4e59b-113">数据表编辑</span><span class="sxs-lookup"><span data-stu-id="4e59b-113">DataTable Edits</span></span>](datatable-edits.md)  
 <span data-ttu-id="4e59b-114">说明如何修改行中的数据，包括挂起对行的更改，直至验证并接受了建议的更改。</span><span class="sxs-lookup"><span data-stu-id="4e59b-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="4e59b-115">行状态和行版本</span><span class="sxs-lookup"><span data-stu-id="4e59b-115">Row States and Row Versions</span></span>](row-states-and-row-versions.md)  
 <span data-ttu-id="4e59b-116">提供有关行的不同状态的信息。</span><span class="sxs-lookup"><span data-stu-id="4e59b-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="4e59b-117">DataRow 删除</span><span class="sxs-lookup"><span data-stu-id="4e59b-117">DataRow Deletion</span></span>](datarow-deletion.md)  
 <span data-ttu-id="4e59b-118">说明如何从表中移除行。</span><span class="sxs-lookup"><span data-stu-id="4e59b-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="4e59b-119">行错误信息</span><span class="sxs-lookup"><span data-stu-id="4e59b-119">Row Error Information</span></span>](row-error-information.md)  
 <span data-ttu-id="4e59b-120">说明如何插入每行的错误信息，帮助解决应用程序中的数据问题。</span><span class="sxs-lookup"><span data-stu-id="4e59b-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="4e59b-121">AcceptChange 和 RejectChange</span><span class="sxs-lookup"><span data-stu-id="4e59b-121">AcceptChanges and RejectChanges</span></span>](acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="4e59b-122">说明如何接受或拒绝对行的更改。</span><span class="sxs-lookup"><span data-stu-id="4e59b-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e59b-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="4e59b-123">See also</span></span>

- [<span data-ttu-id="4e59b-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="4e59b-124">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="4e59b-125">处理数据表事件</span><span class="sxs-lookup"><span data-stu-id="4e59b-125">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="4e59b-126">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="4e59b-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
