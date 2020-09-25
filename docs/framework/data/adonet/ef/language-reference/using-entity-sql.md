---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: bdab81ed8acae5e757de0a669922dc79d0303ee4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203587"
---
# <a name="using-entity-sql"></a><span data-ttu-id="075a7-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="075a7-102">USING (Entity SQL)</span></span>

<span data-ttu-id="075a7-103">指定查询表达式中使用的命名空间。</span><span class="sxs-lookup"><span data-stu-id="075a7-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="075a7-104">语法</span><span class="sxs-lookup"><span data-stu-id="075a7-104">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="075a7-105">参数</span><span class="sxs-lookup"><span data-stu-id="075a7-105">Arguments</span></span>  

 `alias`  
 <span data-ttu-id="075a7-106">指定用于限定命名空间的较短别名。</span><span class="sxs-lookup"><span data-stu-id="075a7-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="075a7-107">任何有效的命名空间。</span><span class="sxs-lookup"><span data-stu-id="075a7-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="075a7-108">示例</span><span class="sxs-lookup"><span data-stu-id="075a7-108">Example</span></span>  

 <span data-ttu-id="075a7-109">以下 Entity SQL 查询使用 USING 运算符以指定查询表达式中使用的命名空间。</span><span class="sxs-lookup"><span data-stu-id="075a7-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="075a7-110">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="075a7-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="075a7-111">按照 [如何：执行返回 PrimitiveType 结果的查询](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的过程进行操作。</span><span class="sxs-lookup"><span data-stu-id="075a7-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="075a7-112">将以下查询作为参数传递给 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="075a7-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="075a7-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="075a7-113">See also</span></span>

- [<span data-ttu-id="075a7-114">命名空间</span><span class="sxs-lookup"><span data-stu-id="075a7-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="075a7-115">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="075a7-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
