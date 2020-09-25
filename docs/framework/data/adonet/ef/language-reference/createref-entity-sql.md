---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: c2a57116f56abf4db3caabcfe3acd0d8afbcf4eb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201052"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="36666-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="36666-102">CREATEREF (Entity SQL)</span></span>

<span data-ttu-id="36666-103">创建对实体集中的实体的引用。</span><span class="sxs-lookup"><span data-stu-id="36666-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36666-104">语法</span><span class="sxs-lookup"><span data-stu-id="36666-104">Syntax</span></span>  
  
```sql  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="36666-105">参数</span><span class="sxs-lookup"><span data-stu-id="36666-105">Arguments</span></span>  

 `entityset_identifier`  
 <span data-ttu-id="36666-106">实体集标识符，不是字符串文本。</span><span class="sxs-lookup"><span data-stu-id="36666-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="36666-107">对应于实体类型的键属性的行类型化表达式。</span><span class="sxs-lookup"><span data-stu-id="36666-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36666-108">备注</span><span class="sxs-lookup"><span data-stu-id="36666-108">Remarks</span></span>  

 <span data-ttu-id="36666-109">`row_typed_expression` 必须在结构上等效于实体的键类型。</span><span class="sxs-lookup"><span data-stu-id="36666-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="36666-110">即，其字段的数目和类型以及顺序必须与实体键相同。</span><span class="sxs-lookup"><span data-stu-id="36666-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="36666-111">在下面的示例中，Orders 和 BadOrders 都是类型 Order 的实体集，而假定 Id 为 Order 的单个键属性。</span><span class="sxs-lookup"><span data-stu-id="36666-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="36666-112">该示例演示如何生成对 BadOrders 中的实体的引用。</span><span class="sxs-lookup"><span data-stu-id="36666-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="36666-113">请注意，该引用可以是无关联引用。</span><span class="sxs-lookup"><span data-stu-id="36666-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="36666-114">即，该引用可以不真正标识特定实体。</span><span class="sxs-lookup"><span data-stu-id="36666-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="36666-115">在这种情况下，对该引用的 `DEREF` 操作会返回 Null。</span><span class="sxs-lookup"><span data-stu-id="36666-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```sql  
SELECT CreateRef(LOB.BadOrders, row(o.Id))
FROM LOB.Orders AS o
```  
  
## <a name="example"></a><span data-ttu-id="36666-116">示例</span><span class="sxs-lookup"><span data-stu-id="36666-116">Example</span></span>  

 <span data-ttu-id="36666-117">下面的 Entity SQL 查询使用 CREATEREF 运算符创建对实体集中的实体的引用。</span><span class="sxs-lookup"><span data-stu-id="36666-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="36666-118">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="36666-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="36666-119">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="36666-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="36666-120">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="36666-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="36666-121">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="36666-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CREATEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="36666-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="36666-122">See also</span></span>

- [<span data-ttu-id="36666-123">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="36666-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="36666-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="36666-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="36666-125">KEY</span><span class="sxs-lookup"><span data-stu-id="36666-125">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="36666-126">REF</span><span class="sxs-lookup"><span data-stu-id="36666-126">REF</span></span>](ref-entity-sql.md)
