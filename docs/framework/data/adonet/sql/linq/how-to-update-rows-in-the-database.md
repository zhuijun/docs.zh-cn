---
title: 如何：更新数据库中的行
description: 了解如何通过修改与表相关的集合中的 LINQ to SQL 对象来更新数据库中的行。 LINQ to SQL 将添加内容转换为 SQL UPDATE 命令。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: f25efb91fb5a83fb1c7c109bd018c8210edaec8b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286334"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="fd767-104">如何：更新数据库中的行</span><span class="sxs-lookup"><span data-stu-id="fd767-104">How to: Update Rows in the Database</span></span>

<span data-ttu-id="fd767-105">您可以通过修改与集合关联的对象的成员值 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> ，然后将更改提交到数据库来更新数据库中的行。</span><span class="sxs-lookup"><span data-stu-id="fd767-105">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="fd767-106">将所做的更改转换为相应的 SQL `UPDATE` 命令。</span><span class="sxs-lookup"><span data-stu-id="fd767-106">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="fd767-107">您可以重写 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、`Insert` 和 `Update` 数据库操作的 `Delete` 默认方法。</span><span class="sxs-lookup"><span data-stu-id="fd767-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="fd767-108">有关详细信息，请参阅[自定义插入、更新和删除操作](customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="fd767-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="fd767-109">使用 Visual Studio 的开发人员可以使用对象关系设计器来开发用于实现相同目的的存储过程。</span><span class="sxs-lookup"><span data-stu-id="fd767-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="fd767-110">以下步骤假定您已通过有效的 <xref:System.Data.Linq.DataContext> 连接到 Northwind 数据库。</span><span class="sxs-lookup"><span data-stu-id="fd767-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="fd767-111">有关详细信息，请参阅[如何：连接到数据库](how-to-connect-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="fd767-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="fd767-112">更新数据库中的行</span><span class="sxs-lookup"><span data-stu-id="fd767-112">To update a row in the database</span></span>

1. <span data-ttu-id="fd767-113">查询数据库中要更新的行。</span><span class="sxs-lookup"><span data-stu-id="fd767-113">Query the database for the row to be updated.</span></span>

2. <span data-ttu-id="fd767-114">对得到的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 对象中的成员值进行所需的更改。</span><span class="sxs-lookup"><span data-stu-id="fd767-114">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>

3. <span data-ttu-id="fd767-115">将更改提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="fd767-115">Submit the changes to the database.</span></span>

## <a name="example"></a><span data-ttu-id="fd767-116">示例</span><span class="sxs-lookup"><span data-stu-id="fd767-116">Example</span></span>

<span data-ttu-id="fd767-117">下面的示例查询数据库中编号为 11000 的订单，然后更改所得到的 `ShipName` 对象中的 `ShipVia` 和 `Order` 值。</span><span class="sxs-lookup"><span data-stu-id="fd767-117">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="fd767-118">最后，对这些成员值的更改将作为对 `ShipName` 和 `ShipVia` 列的更改提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="fd767-118">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="fd767-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd767-119">See also</span></span>

- [<span data-ttu-id="fd767-120">如何：管理更改冲突</span><span class="sxs-lookup"><span data-stu-id="fd767-120">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="fd767-121">如何：分配存储流程来执行更新、插入和删除操作（O/R 设计器）</span><span class="sxs-lookup"><span data-stu-id="fd767-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="fd767-122">进行和提交数据更改</span><span class="sxs-lookup"><span data-stu-id="fd767-122">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
