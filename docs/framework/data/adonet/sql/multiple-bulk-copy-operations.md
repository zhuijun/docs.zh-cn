---
title: 多个批量复制操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: d447f09fcbfe108346b81a2bced44cf305e2844b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172666"
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="483c7-102">多个批量复制操作</span><span class="sxs-lookup"><span data-stu-id="483c7-102">Multiple Bulk Copy Operations</span></span>

<span data-ttu-id="483c7-103">可以使用 <xref:System.Data.SqlClient.SqlBulkCopy> 类的单个实例执行多次大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="483c7-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="483c7-104">如果在两个副本之间 (的操作参数发生变化（例如，目标表的名称) ），则必须在对任何 **WriteToServer** 方法进行任何后续调用之前更新这些参数，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="483c7-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="483c7-105">除非已明确更改，否则将所有属性值保持为与给定实例的较早大容量复制上的属性值相同。</span><span class="sxs-lookup"><span data-stu-id="483c7-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="483c7-106">与每个操作使用单独实例相比，使用 <xref:System.Data.SqlClient.SqlBulkCopy> 的同一实例执行多次大容量复制操作通常效率更高。</span><span class="sxs-lookup"><span data-stu-id="483c7-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="483c7-107">在使用同一 <xref:System.Data.SqlClient.SqlBulkCopy> 对象执行多次大容量复制操作时，对于每个操作中的源信息或目标信息相同与否没有限制。</span><span class="sxs-lookup"><span data-stu-id="483c7-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="483c7-108">但是，必须确保每次写入服务器时正确设置列关联信息。</span><span class="sxs-lookup"><span data-stu-id="483c7-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="483c7-109">除非已按照 [大容量复制示例设置](bulk-copy-example-setup.md)中所述创建了工作表，否则此示例将不会运行。</span><span class="sxs-lookup"><span data-stu-id="483c7-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](bulk-copy-example-setup.md).</span></span> <span data-ttu-id="483c7-110">提供此代码是为了演示仅使用 SqlBulkCopy 时的语法。</span><span class="sxs-lookup"><span data-stu-id="483c7-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="483c7-111">如果源表和目标表位于同一 SQL Server 实例中，可以更便捷地使用 Transact-SQL `INSERT … SELECT` 语句复制数据。</span><span class="sxs-lookup"><span data-stu-id="483c7-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="483c7-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="483c7-112">See also</span></span>

- [<span data-ttu-id="483c7-113">SQL Server 中的批量复制操作</span><span class="sxs-lookup"><span data-stu-id="483c7-113">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="483c7-114">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="483c7-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
