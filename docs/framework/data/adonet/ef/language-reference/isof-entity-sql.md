---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3cbbc9b6feda1bde104ed2c95d4dca274b090028
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202274"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="3743a-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3743a-102">ISOF (Entity SQL)</span></span>

<span data-ttu-id="3743a-103">确定表达式的类型是否为指定类型或指定类型的某个子类型。</span><span class="sxs-lookup"><span data-stu-id="3743a-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3743a-104">语法</span><span class="sxs-lookup"><span data-stu-id="3743a-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="3743a-105">参数</span><span class="sxs-lookup"><span data-stu-id="3743a-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="3743a-106">要确定其类型的任何有效查询表达式。</span><span class="sxs-lookup"><span data-stu-id="3743a-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="3743a-107">NOT</span><span class="sxs-lookup"><span data-stu-id="3743a-107">NOT</span></span>  
 <span data-ttu-id="3743a-108">对 IS OF 的 EDM.Boolean 结果取反。</span><span class="sxs-lookup"><span data-stu-id="3743a-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="3743a-109">ONLY</span><span class="sxs-lookup"><span data-stu-id="3743a-109">ONLY</span></span>  
 <span data-ttu-id="3743a-110">指定仅当 `true` 的类型为 `expression`，而不是其任何子类型时，IS OF 才返回 `type`。</span><span class="sxs-lookup"><span data-stu-id="3743a-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="3743a-111">要针对其测试 `expression` 的类型。</span><span class="sxs-lookup"><span data-stu-id="3743a-111">The type to test `expression` against.</span></span> <span data-ttu-id="3743a-112">该类型必须由命名空间进行限定。</span><span class="sxs-lookup"><span data-stu-id="3743a-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3743a-113">返回值</span><span class="sxs-lookup"><span data-stu-id="3743a-113">Return Value</span></span>  

 <span data-ttu-id="3743a-114">如果 `true` 的类型为 T 且 T 为基类型或 `expression` 的派生类型，则返回 `type`；如果 `expression` 在运行时为 null，则返回 null；否则返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="3743a-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3743a-115">备注</span><span class="sxs-lookup"><span data-stu-id="3743a-115">Remarks</span></span>  

 <span data-ttu-id="3743a-116">表达式 `expression IS NOT OF (type)` 和 `expression IS NOT OF (ONLY type)` 在语法 `NOT (expression IS OF (type))` 上分别等效于和 `NOT (expression IS OF (ONLY type))` 。</span><span class="sxs-lookup"><span data-stu-id="3743a-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="3743a-117">下表显示了 `IS OF` 运算符在某些典型和非常见模式下的行为。</span><span class="sxs-lookup"><span data-stu-id="3743a-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="3743a-118">所有异常都在调用提供程序之前从客户端引发：</span><span class="sxs-lookup"><span data-stu-id="3743a-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="3743a-119">模式</span><span class="sxs-lookup"><span data-stu-id="3743a-119">Pattern</span></span>|<span data-ttu-id="3743a-120">行为</span><span class="sxs-lookup"><span data-stu-id="3743a-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="3743a-121">null IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="3743a-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="3743a-122">引发</span><span class="sxs-lookup"><span data-stu-id="3743a-122">Throws</span></span>|  
|<span data-ttu-id="3743a-123">null IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="3743a-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="3743a-124">引发</span><span class="sxs-lookup"><span data-stu-id="3743a-124">Throws</span></span>|  
|<span data-ttu-id="3743a-125">null IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="3743a-125">null IS OF (RowType)</span></span>|<span data-ttu-id="3743a-126">引发</span><span class="sxs-lookup"><span data-stu-id="3743a-126">Throws</span></span>|  
|<span data-ttu-id="3743a-127">TREAT (null AS EntityType) IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="3743a-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="3743a-128">返回 DBNull。</span><span class="sxs-lookup"><span data-stu-id="3743a-128">Returns DBNull</span></span>|  
|<span data-ttu-id="3743a-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="3743a-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="3743a-130">引发</span><span class="sxs-lookup"><span data-stu-id="3743a-130">Throws</span></span>|  
|<span data-ttu-id="3743a-131">TREAT (null AS RowType) IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="3743a-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="3743a-132">引发</span><span class="sxs-lookup"><span data-stu-id="3743a-132">Throws</span></span>|  
|<span data-ttu-id="3743a-133">EntityType IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="3743a-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="3743a-134">返回 true/false</span><span class="sxs-lookup"><span data-stu-id="3743a-134">Returns true/false</span></span>|  
|<span data-ttu-id="3743a-135">ComplexType IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="3743a-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="3743a-136">引发</span><span class="sxs-lookup"><span data-stu-id="3743a-136">Throws</span></span>|  
|<span data-ttu-id="3743a-137">RowType IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="3743a-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="3743a-138">引发</span><span class="sxs-lookup"><span data-stu-id="3743a-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3743a-139">示例</span><span class="sxs-lookup"><span data-stu-id="3743a-139">Example</span></span>  

 <span data-ttu-id="3743a-140">下面的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询使用 IS OF 运算符确定一个查询表达式的类型，然后使用 TREAT 运算符将一个类型为 Course 的对象转换为类型为 OnsiteCourse 的对象的集合。</span><span class="sxs-lookup"><span data-stu-id="3743a-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="3743a-141">该查询基于 [School 模型](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="3743a-141">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 <span data-ttu-id="3743a-142">[！ code-sql [DP EntityServices 概念 # TREAT_ISOF] ~/samples/snippets/tsql/VS_Snippets_Data/dp EntityServices 概念/tsql/entitysql # treat_isof) ]</span><span class="sxs-lookup"><span data-stu-id="3743a-142">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3743a-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="3743a-143">See also</span></span>

- [<span data-ttu-id="3743a-144">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="3743a-144">Entity SQL Reference</span></span>](entity-sql-reference.md)
