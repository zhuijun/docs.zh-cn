---
title: 比较语义 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 9a36fcc4476c25d64fed670e857f339fb20043d8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197828"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="02abf-102">比较语义 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="02abf-102">Comparison Semantics (Entity SQL)</span></span>

<span data-ttu-id="02abf-103">执行下列任一 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 运算符时都涉及类型实例的比较：</span><span class="sxs-lookup"><span data-stu-id="02abf-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="02abf-104">显式比较</span><span class="sxs-lookup"><span data-stu-id="02abf-104">Explicit comparison</span></span>  

 <span data-ttu-id="02abf-105">相等运算：</span><span class="sxs-lookup"><span data-stu-id="02abf-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="02abf-106">!=</span><span class="sxs-lookup"><span data-stu-id="02abf-106">!=</span></span>  
  
 <span data-ttu-id="02abf-107">排序运算：</span><span class="sxs-lookup"><span data-stu-id="02abf-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="02abf-108">判断是否可为 Null 的运算：</span><span class="sxs-lookup"><span data-stu-id="02abf-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="02abf-109">为 NULL</span><span class="sxs-lookup"><span data-stu-id="02abf-109">IS NULL</span></span>  
  
- <span data-ttu-id="02abf-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="02abf-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="02abf-111">显式区别</span><span class="sxs-lookup"><span data-stu-id="02abf-111">Explicit distinction</span></span>  

 <span data-ttu-id="02abf-112">相等区别：</span><span class="sxs-lookup"><span data-stu-id="02abf-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="02abf-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="02abf-113">DISTINCT</span></span>  
  
- <span data-ttu-id="02abf-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="02abf-114">GROUP BY</span></span>  
  
 <span data-ttu-id="02abf-115">排序区别：</span><span class="sxs-lookup"><span data-stu-id="02abf-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="02abf-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="02abf-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="02abf-117">隐式区别</span><span class="sxs-lookup"><span data-stu-id="02abf-117">Implicit distinction</span></span>  

 <span data-ttu-id="02abf-118">集运算和谓词（相等）：</span><span class="sxs-lookup"><span data-stu-id="02abf-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="02abf-119">UNION</span><span class="sxs-lookup"><span data-stu-id="02abf-119">UNION</span></span>  
  
- <span data-ttu-id="02abf-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="02abf-120">INTERSECT</span></span>  
  
- <span data-ttu-id="02abf-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="02abf-121">EXCEPT</span></span>  
  
- <span data-ttu-id="02abf-122">SET</span><span class="sxs-lookup"><span data-stu-id="02abf-122">SET</span></span>  
  
- <span data-ttu-id="02abf-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="02abf-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="02abf-124">项谓词（相等）：</span><span class="sxs-lookup"><span data-stu-id="02abf-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="02abf-125">IN</span><span class="sxs-lookup"><span data-stu-id="02abf-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="02abf-126">支持的组合</span><span class="sxs-lookup"><span data-stu-id="02abf-126">Supported Combinations</span></span>  

 <span data-ttu-id="02abf-127">下表说明了每种类型的比较运算符的所有受支持的组合：</span><span class="sxs-lookup"><span data-stu-id="02abf-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="02abf-128">**类型**</span><span class="sxs-lookup"><span data-stu-id="02abf-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="02abf-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="02abf-129">**!=**</span></span>|<span data-ttu-id="02abf-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="02abf-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="02abf-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="02abf-131">**DISTINCT**</span></span>|<span data-ttu-id="02abf-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="02abf-132">**UNION**</span></span><br /><br /> <span data-ttu-id="02abf-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="02abf-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="02abf-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="02abf-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="02abf-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="02abf-135">**SET**</span></span><br /><br /> <span data-ttu-id="02abf-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="02abf-136">**OVERLAPS**</span></span>|<span data-ttu-id="02abf-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="02abf-137">**IN**</span></span>|<span data-ttu-id="02abf-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="02abf-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="02abf-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="02abf-139">**>   >=**</span></span>|<span data-ttu-id="02abf-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="02abf-140">**ORDER BY**</span></span>|<span data-ttu-id="02abf-141">**为 NULL**</span><span class="sxs-lookup"><span data-stu-id="02abf-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="02abf-142">**不为 NULL**</span><span class="sxs-lookup"><span data-stu-id="02abf-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="02abf-143">实体类型</span><span class="sxs-lookup"><span data-stu-id="02abf-143">Entity type</span></span>|<span data-ttu-id="02abf-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="02abf-145">所有属性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="02abf-146">所有属性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="02abf-147">所有属性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="02abf-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="02abf-151">复杂类型</span><span class="sxs-lookup"><span data-stu-id="02abf-151">Complex type</span></span>|<span data-ttu-id="02abf-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="02abf-159">行</span><span class="sxs-lookup"><span data-stu-id="02abf-159">Row</span></span>|<span data-ttu-id="02abf-160">所有属性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="02abf-161">所有属性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="02abf-162">所有属性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="02abf-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-165">所有属性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="02abf-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="02abf-167">基元类型</span><span class="sxs-lookup"><span data-stu-id="02abf-167">Primitive type</span></span>|<span data-ttu-id="02abf-168">特定于提供程序</span><span class="sxs-lookup"><span data-stu-id="02abf-168">Provider-specific</span></span>|<span data-ttu-id="02abf-169">特定于提供程序</span><span class="sxs-lookup"><span data-stu-id="02abf-169">Provider-specific</span></span>|<span data-ttu-id="02abf-170">特定于提供程序</span><span class="sxs-lookup"><span data-stu-id="02abf-170">Provider-specific</span></span>|<span data-ttu-id="02abf-171">特定于提供程序</span><span class="sxs-lookup"><span data-stu-id="02abf-171">Provider-specific</span></span>|<span data-ttu-id="02abf-172">特定于提供程序</span><span class="sxs-lookup"><span data-stu-id="02abf-172">Provider-specific</span></span>|<span data-ttu-id="02abf-173">特定于提供程序</span><span class="sxs-lookup"><span data-stu-id="02abf-173">Provider-specific</span></span>|<span data-ttu-id="02abf-174">特定于提供程序</span><span class="sxs-lookup"><span data-stu-id="02abf-174">Provider-specific</span></span>|  
|<span data-ttu-id="02abf-175">多集</span><span class="sxs-lookup"><span data-stu-id="02abf-175">Multiset</span></span>|<span data-ttu-id="02abf-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="02abf-183">引用</span><span class="sxs-lookup"><span data-stu-id="02abf-183">Ref</span></span>|<span data-ttu-id="02abf-184">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="02abf-185">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="02abf-186">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="02abf-187">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="02abf-188">Throw</span><span class="sxs-lookup"><span data-stu-id="02abf-188">Throw</span></span>|<span data-ttu-id="02abf-189">Throw</span><span class="sxs-lookup"><span data-stu-id="02abf-189">Throw</span></span>|<span data-ttu-id="02abf-190">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="02abf-191">关联</span><span class="sxs-lookup"><span data-stu-id="02abf-191">Association</span></span><br /><br /> <span data-ttu-id="02abf-192">type</span><span class="sxs-lookup"><span data-stu-id="02abf-192">type</span></span>|<span data-ttu-id="02abf-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-194">Throw</span><span class="sxs-lookup"><span data-stu-id="02abf-194">Throw</span></span>|<span data-ttu-id="02abf-195">Throw</span><span class="sxs-lookup"><span data-stu-id="02abf-195">Throw</span></span>|<span data-ttu-id="02abf-196">Throw</span><span class="sxs-lookup"><span data-stu-id="02abf-196">Throw</span></span>|<span data-ttu-id="02abf-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="02abf-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="02abf-200"><sup>1</sup>给定实体类型实例的引用将被隐式比较，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="02abf-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="02abf-201">不能将实体实例与显式引用进行比较。</span><span class="sxs-lookup"><span data-stu-id="02abf-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="02abf-202">如果试图这么做，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="02abf-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="02abf-203">例如，以下查询将引发异常：</span><span class="sxs-lookup"><span data-stu-id="02abf-203">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="02abf-204"><sup>2</sup>在将复杂类型发送到存储区之前，会将其属性展开，因此只要它们的所有属性都是可比较的) ，它们就会变得可比较 (。</span><span class="sxs-lookup"><span data-stu-id="02abf-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="02abf-205">另请参阅 <sup>4。</sup></span><span class="sxs-lookup"><span data-stu-id="02abf-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="02abf-206"><sup>3</sup>实体框架运行时检测不受支持的情况，并引发有意义的异常，而不参与提供程序/存储。</span><span class="sxs-lookup"><span data-stu-id="02abf-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="02abf-207"><sup>4</sup>尝试比较所有属性。</span><span class="sxs-lookup"><span data-stu-id="02abf-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="02abf-208">如果某个属性的类型不可比较，例如 text、ntext 或 image，则可能引发服务器异常。</span><span class="sxs-lookup"><span data-stu-id="02abf-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="02abf-209"><sup>5</sup>将对引用的所有单个元素进行比较 (这包括实体类型的实体集名称和) 的所有键属性。</span><span class="sxs-lookup"><span data-stu-id="02abf-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02abf-210">请参阅</span><span class="sxs-lookup"><span data-stu-id="02abf-210">See also</span></span>

- [<span data-ttu-id="02abf-211">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="02abf-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
