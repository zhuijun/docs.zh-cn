---
title: 如何：将行插入数据库中
description: 了解如何通过将 LINQ to SQL 对象添加到与表相关的集合，将行插入到数据库中。 LINQ to SQL 将添加内容转换为 SQL INSERT 命令。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 39eee6edf59d2adb7de41efd88899050fbe69fd8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286347"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="8c852-104">如何：将行插入数据库中</span><span class="sxs-lookup"><span data-stu-id="8c852-104">How to: Insert Rows Into the Database</span></span>

<span data-ttu-id="8c852-105">您可以通过将对象添加到关联的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> 集合，然后将更改提交到数据库，将这些行插入到数据库中。</span><span class="sxs-lookup"><span data-stu-id="8c852-105">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8c852-106">将所做的更改转换为相应的 SQL `INSERT` 命令。</span><span class="sxs-lookup"><span data-stu-id="8c852-106">translates your changes into the appropriate SQL `INSERT` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="8c852-107">您可以重写 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、`Insert` 和 `Update` 数据库操作的 `Delete` 默认方法。</span><span class="sxs-lookup"><span data-stu-id="8c852-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="8c852-108">有关详细信息，请参阅[自定义插入、更新和删除操作](customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="8c852-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="8c852-109">使用 Visual Studio 的开发人员可以使用对象关系设计器来开发用于实现相同目的的存储过程。</span><span class="sxs-lookup"><span data-stu-id="8c852-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="8c852-110">以下步骤假定您已通过有效的 <xref:System.Data.Linq.DataContext> 连接到 Northwind 数据库。</span><span class="sxs-lookup"><span data-stu-id="8c852-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="8c852-111">有关详细信息，请参阅[如何：连接到数据库](how-to-connect-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="8c852-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="8c852-112">向数据库中插入行</span><span class="sxs-lookup"><span data-stu-id="8c852-112">To insert a row into the database</span></span>

1. <span data-ttu-id="8c852-113">创建一个包含要提交的列数据的新对象。</span><span class="sxs-lookup"><span data-stu-id="8c852-113">Create a new object that includes the column data to be submitted.</span></span>

2. <span data-ttu-id="8c852-114">将新对象添加到 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` 与数据库中的目标表关联的集合中。</span><span class="sxs-lookup"><span data-stu-id="8c852-114">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>

3. <span data-ttu-id="8c852-115">将更改提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="8c852-115">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="8c852-116">示例</span><span class="sxs-lookup"><span data-stu-id="8c852-116">Example</span></span>

<span data-ttu-id="8c852-117">下面的代码示例创建一个类型为 `Order` 的新对象，并用相应的值填充此对象。</span><span class="sxs-lookup"><span data-stu-id="8c852-117">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="8c852-118">然后，它将这个新对象添加到 `Order` 集合中。</span><span class="sxs-lookup"><span data-stu-id="8c852-118">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="8c852-119">最后，它将所做的更改提交到数据库中，使之成为 `Orders` 表中的一个新行。</span><span class="sxs-lookup"><span data-stu-id="8c852-119">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="8c852-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c852-120">See also</span></span>

- [<span data-ttu-id="8c852-121">如何：管理更改冲突</span><span class="sxs-lookup"><span data-stu-id="8c852-121">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="8c852-122">DataContext 方法（O/R 设计器）</span><span class="sxs-lookup"><span data-stu-id="8c852-122">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="8c852-123">如何：分配存储流程来执行更新、插入和删除操作（O/R 设计器）</span><span class="sxs-lookup"><span data-stu-id="8c852-123">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="8c852-124">进行和提交数据更改</span><span class="sxs-lookup"><span data-stu-id="8c852-124">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
