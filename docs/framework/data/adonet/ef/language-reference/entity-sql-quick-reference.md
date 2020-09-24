---
title: Entity SQL 快速参考
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 7ec3b6fc184b4f169d6f6489bda0ec8fa4abb4f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148135"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="ec89a-102">Entity SQL 快速参考</span><span class="sxs-lookup"><span data-stu-id="ec89a-102">Entity SQL Quick Reference</span></span>

<span data-ttu-id="ec89a-103">本主题提供 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询的快速参考。</span><span class="sxs-lookup"><span data-stu-id="ec89a-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="ec89a-104">本主题中的查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="ec89a-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="ec89a-105">文本</span><span class="sxs-lookup"><span data-stu-id="ec89a-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="ec89a-106">字符串</span><span class="sxs-lookup"><span data-stu-id="ec89a-106">String</span></span>  

 <span data-ttu-id="ec89a-107">字符串分为 Unicode 字符串和非 Unicode 字符串。</span><span class="sxs-lookup"><span data-stu-id="ec89a-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="ec89a-108">Unicode 字符串前面附有 N。例如， `N'hello'` 。</span><span class="sxs-lookup"><span data-stu-id="ec89a-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="ec89a-109">下面是非 Unicode 字符串的示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="ec89a-110">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-110">Output:</span></span>  
  
|<span data-ttu-id="ec89a-111">值</span><span class="sxs-lookup"><span data-stu-id="ec89a-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="ec89a-112">Hello</span><span class="sxs-lookup"><span data-stu-id="ec89a-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="ec89a-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="ec89a-113">DateTime</span></span>  

 <span data-ttu-id="ec89a-114">在日期时间文本中，日期部分和时间部分是必须存在的。</span><span class="sxs-lookup"><span data-stu-id="ec89a-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="ec89a-115">这里没有默认值。</span><span class="sxs-lookup"><span data-stu-id="ec89a-115">There are no default values.</span></span>  
  
 <span data-ttu-id="ec89a-116">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="ec89a-117">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-117">Output:</span></span>  
  
|<span data-ttu-id="ec89a-118">值</span><span class="sxs-lookup"><span data-stu-id="ec89a-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="ec89a-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="ec89a-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="ec89a-120">Integer</span><span class="sxs-lookup"><span data-stu-id="ec89a-120">Integer</span></span>  

 <span data-ttu-id="ec89a-121">整数文本可以为 Int32 (123)、UInt32 (123U)、Int64 (123L) 和 UInt64 (123UL) 类型。</span><span class="sxs-lookup"><span data-stu-id="ec89a-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="ec89a-122">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="ec89a-123">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-123">Output:</span></span>  
  
|<span data-ttu-id="ec89a-124">值</span><span class="sxs-lookup"><span data-stu-id="ec89a-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="ec89a-125">1</span><span class="sxs-lookup"><span data-stu-id="ec89a-125">1</span></span>|  
|<span data-ttu-id="ec89a-126">2</span><span class="sxs-lookup"><span data-stu-id="ec89a-126">2</span></span>|  
|<span data-ttu-id="ec89a-127">3</span><span class="sxs-lookup"><span data-stu-id="ec89a-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="ec89a-128">其他</span><span class="sxs-lookup"><span data-stu-id="ec89a-128">Other</span></span>  

 <span data-ttu-id="ec89a-129">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支持的其他文字为、Guid、二进制、浮点/双精度型、十进制和 `null`。</span><span class="sxs-lookup"><span data-stu-id="ec89a-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="ec89a-130">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的 null 文本视为与概念模型中的每一种其他类型兼容。</span><span class="sxs-lookup"><span data-stu-id="ec89a-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="ec89a-131">类型构造函数</span><span class="sxs-lookup"><span data-stu-id="ec89a-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="ec89a-132">ROW</span><span class="sxs-lookup"><span data-stu-id="ec89a-132">ROW</span></span>  

 <span data-ttu-id="ec89a-133">[ROW](row-entity-sql.md) 构造一个匿名的结构化类型 (记录) 值，如下所示： `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="ec89a-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="ec89a-134">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="ec89a-135">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-135">Output:</span></span>  
  
|<span data-ttu-id="ec89a-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="ec89a-136">ProductID</span></span>|<span data-ttu-id="ec89a-137">名称</span><span class="sxs-lookup"><span data-stu-id="ec89a-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="ec89a-138">1</span><span class="sxs-lookup"><span data-stu-id="ec89a-138">1</span></span>|<span data-ttu-id="ec89a-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="ec89a-139">Adjustable Race</span></span>|  
|<span data-ttu-id="ec89a-140">879</span><span class="sxs-lookup"><span data-stu-id="ec89a-140">879</span></span>|<span data-ttu-id="ec89a-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="ec89a-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="ec89a-142">712</span><span class="sxs-lookup"><span data-stu-id="ec89a-142">712</span></span>|<span data-ttu-id="ec89a-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="ec89a-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="ec89a-144">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-144">...</span></span>|<span data-ttu-id="ec89a-145">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="ec89a-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="ec89a-146">MULTISET</span></span>  

 <span data-ttu-id="ec89a-147">[多重集](multiset-entity-sql.md) 构造集合，例如：</span><span class="sxs-lookup"><span data-stu-id="ec89a-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="ec89a-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="ec89a-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="ec89a-149">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="ec89a-150">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-150">Output:</span></span>  
  
|<span data-ttu-id="ec89a-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="ec89a-151">ProductID</span></span>|<span data-ttu-id="ec89a-152">名称</span><span class="sxs-lookup"><span data-stu-id="ec89a-152">Name</span></span>|<span data-ttu-id="ec89a-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="ec89a-153">ProductNumber</span></span>|<span data-ttu-id="ec89a-154">…</span><span class="sxs-lookup"><span data-stu-id="ec89a-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="ec89a-155">842</span><span class="sxs-lookup"><span data-stu-id="ec89a-155">842</span></span>|<span data-ttu-id="ec89a-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="ec89a-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="ec89a-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="ec89a-157">PA-T100</span></span>|<span data-ttu-id="ec89a-158">…</span><span class="sxs-lookup"><span data-stu-id="ec89a-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="ec89a-159">对象</span><span class="sxs-lookup"><span data-stu-id="ec89a-159">Object</span></span>  

 <span data-ttu-id="ec89a-160">[命名类型构造函数](named-type-constructor-entity-sql.md) 构造 (名) 用户定义对象，例如 `person("abc", 12)` 。</span><span class="sxs-lookup"><span data-stu-id="ec89a-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="ec89a-161">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 <span data-ttu-id="ec89a-162">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-162">Output:</span></span>  
  
|<span data-ttu-id="ec89a-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="ec89a-163">SalesOrderDetailID</span></span>|<span data-ttu-id="ec89a-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="ec89a-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="ec89a-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="ec89a-165">OrderQty</span></span>|<span data-ttu-id="ec89a-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="ec89a-166">ProductID</span></span>|<span data-ttu-id="ec89a-167">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="ec89a-168">1</span><span class="sxs-lookup"><span data-stu-id="ec89a-168">1</span></span>|<span data-ttu-id="ec89a-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="ec89a-169">4911-403C-98</span></span>|<span data-ttu-id="ec89a-170">1</span><span class="sxs-lookup"><span data-stu-id="ec89a-170">1</span></span>|<span data-ttu-id="ec89a-171">776</span><span class="sxs-lookup"><span data-stu-id="ec89a-171">776</span></span>|<span data-ttu-id="ec89a-172">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-172">...</span></span>|  
|<span data-ttu-id="ec89a-173">2</span><span class="sxs-lookup"><span data-stu-id="ec89a-173">2</span></span>|<span data-ttu-id="ec89a-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="ec89a-174">4911-403C-98</span></span>|<span data-ttu-id="ec89a-175">3</span><span class="sxs-lookup"><span data-stu-id="ec89a-175">3</span></span>|<span data-ttu-id="ec89a-176">777</span><span class="sxs-lookup"><span data-stu-id="ec89a-176">777</span></span>|<span data-ttu-id="ec89a-177">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-177">...</span></span>|  
|<span data-ttu-id="ec89a-178">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-178">...</span></span>|<span data-ttu-id="ec89a-179">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-179">...</span></span>|<span data-ttu-id="ec89a-180">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-180">...</span></span>|<span data-ttu-id="ec89a-181">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-181">...</span></span>|<span data-ttu-id="ec89a-182">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="ec89a-183">参考</span><span class="sxs-lookup"><span data-stu-id="ec89a-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="ec89a-184">REF</span><span class="sxs-lookup"><span data-stu-id="ec89a-184">REF</span></span>  

 <span data-ttu-id="ec89a-185">[REF](ref-entity-sql.md) 创建对实体类型实例的引用。</span><span class="sxs-lookup"><span data-stu-id="ec89a-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="ec89a-186">例如，下面的查询返回对 Orders 实体集中每一个 Order 实体的引用：</span><span class="sxs-lookup"><span data-stu-id="ec89a-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="ec89a-187">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-187">Output:</span></span>  
  
|<span data-ttu-id="ec89a-188">值</span><span class="sxs-lookup"><span data-stu-id="ec89a-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="ec89a-189">1</span><span class="sxs-lookup"><span data-stu-id="ec89a-189">1</span></span>|  
|<span data-ttu-id="ec89a-190">2</span><span class="sxs-lookup"><span data-stu-id="ec89a-190">2</span></span>|  
|<span data-ttu-id="ec89a-191">3</span><span class="sxs-lookup"><span data-stu-id="ec89a-191">3</span></span>|  
|<span data-ttu-id="ec89a-192">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-192">...</span></span>|  
  
 <span data-ttu-id="ec89a-193">下面的示例使用属性提取运算符 (.) 访问实体的属性。</span><span class="sxs-lookup"><span data-stu-id="ec89a-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="ec89a-194">在使用属性提取运算符时，引用将自动被反引用。</span><span class="sxs-lookup"><span data-stu-id="ec89a-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="ec89a-195">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="ec89a-196">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-196">Output:</span></span>  
  
|<span data-ttu-id="ec89a-197">值</span><span class="sxs-lookup"><span data-stu-id="ec89a-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="ec89a-198">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="ec89a-198">Adjustable Race</span></span>|  
|<span data-ttu-id="ec89a-199">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="ec89a-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="ec89a-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="ec89a-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="ec89a-201">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="ec89a-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="ec89a-202">DEREF</span></span>  

 <span data-ttu-id="ec89a-203">[DEREF](deref-entity-sql.md) 取消引用一个引用值，并生成该取消引用的结果。</span><span class="sxs-lookup"><span data-stu-id="ec89a-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="ec89a-204">例如，下面的查询生成 Orders 实体集中每一个 Order 的 Order 实体：`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`。</span><span class="sxs-lookup"><span data-stu-id="ec89a-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="ec89a-205">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="ec89a-206">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-206">Output:</span></span>  
  
|<span data-ttu-id="ec89a-207">值</span><span class="sxs-lookup"><span data-stu-id="ec89a-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="ec89a-208">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="ec89a-208">Adjustable Race</span></span>|  
|<span data-ttu-id="ec89a-209">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="ec89a-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="ec89a-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="ec89a-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="ec89a-211">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="ec89a-212">CREATEREF 和 KEY</span><span class="sxs-lookup"><span data-stu-id="ec89a-212">CREATEREF AND KEY</span></span>  

 <span data-ttu-id="ec89a-213">[CREATEREF](createref-entity-sql.md) 创建一个传递密钥的引用。</span><span class="sxs-lookup"><span data-stu-id="ec89a-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="ec89a-214">[KEY](key-entity-sql.md) 提取具有类型引用的表达式的键部分。</span><span class="sxs-lookup"><span data-stu-id="ec89a-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="ec89a-215">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="ec89a-216">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-216">Output:</span></span>  
  
|<span data-ttu-id="ec89a-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="ec89a-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="ec89a-218">980</span><span class="sxs-lookup"><span data-stu-id="ec89a-218">980</span></span>|  
|<span data-ttu-id="ec89a-219">365</span><span class="sxs-lookup"><span data-stu-id="ec89a-219">365</span></span>|  
|<span data-ttu-id="ec89a-220">771</span><span class="sxs-lookup"><span data-stu-id="ec89a-220">771</span></span>|  
|<span data-ttu-id="ec89a-221">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="ec89a-222">函数</span><span class="sxs-lookup"><span data-stu-id="ec89a-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="ec89a-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="ec89a-223">Canonical</span></span>  

 <span data-ttu-id="ec89a-224">[规范函数](canonical-functions.md)的命名空间为 Edm，如中所示 `Edm.Length("string")` 。</span><span class="sxs-lookup"><span data-stu-id="ec89a-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="ec89a-225">您无需指定命名空间，除非导入的另一个命名空间中包含与规范函数同名的函数。</span><span class="sxs-lookup"><span data-stu-id="ec89a-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="ec89a-226">如果两个命名空间有相同的函数，用户应指定完整名称。</span><span class="sxs-lookup"><span data-stu-id="ec89a-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="ec89a-227">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="ec89a-228">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-228">Output:</span></span>  
  
|<span data-ttu-id="ec89a-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="ec89a-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="ec89a-230">6</span><span class="sxs-lookup"><span data-stu-id="ec89a-230">6</span></span>|  
|<span data-ttu-id="ec89a-231">6</span><span class="sxs-lookup"><span data-stu-id="ec89a-231">6</span></span>|  
|<span data-ttu-id="ec89a-232">5</span><span class="sxs-lookup"><span data-stu-id="ec89a-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="ec89a-233">特定于 Microsoft 提供程序</span><span class="sxs-lookup"><span data-stu-id="ec89a-233">Microsoft Provider-Specific</span></span>  

 <span data-ttu-id="ec89a-234">命名空间中有[特定于 Microsoft 提供程序的函数](../sqlclient-for-ef-functions.md) `SqlServer` 。</span><span class="sxs-lookup"><span data-stu-id="ec89a-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="ec89a-235">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="ec89a-236">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-236">Output:</span></span>  
  
|<span data-ttu-id="ec89a-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="ec89a-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="ec89a-238">27</span><span class="sxs-lookup"><span data-stu-id="ec89a-238">27</span></span>|  
|<span data-ttu-id="ec89a-239">27</span><span class="sxs-lookup"><span data-stu-id="ec89a-239">27</span></span>|  
|<span data-ttu-id="ec89a-240">26</span><span class="sxs-lookup"><span data-stu-id="ec89a-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="ec89a-241">命名空间</span><span class="sxs-lookup"><span data-stu-id="ec89a-241">Namespaces</span></span>  

 <span data-ttu-id="ec89a-242">[USING](using-entity-sql.md) 指定查询表达式中使用的命名空间。</span><span class="sxs-lookup"><span data-stu-id="ec89a-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="ec89a-243">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="ec89a-244">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-244">Output:</span></span>  
  
|<span data-ttu-id="ec89a-245">值</span><span class="sxs-lookup"><span data-stu-id="ec89a-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="ec89a-246">aa</span><span class="sxs-lookup"><span data-stu-id="ec89a-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="ec89a-247">分页</span><span class="sxs-lookup"><span data-stu-id="ec89a-247">Paging</span></span>  

 <span data-ttu-id="ec89a-248">可以通过在[ORDER by](order-by-entity-sql.md)子句中声明[SKIP](skip-entity-sql.md)和[LIMIT](limit-entity-sql.md)子子句来表示分页。</span><span class="sxs-lookup"><span data-stu-id="ec89a-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="ec89a-249">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="ec89a-250">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-250">Output:</span></span>  
  
|<span data-ttu-id="ec89a-251">ID</span><span class="sxs-lookup"><span data-stu-id="ec89a-251">ID</span></span>|<span data-ttu-id="ec89a-252">名称</span><span class="sxs-lookup"><span data-stu-id="ec89a-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="ec89a-253">10</span><span class="sxs-lookup"><span data-stu-id="ec89a-253">10</span></span>|<span data-ttu-id="ec89a-254">Adina</span><span class="sxs-lookup"><span data-stu-id="ec89a-254">Adina</span></span>|  
|<span data-ttu-id="ec89a-255">11</span><span class="sxs-lookup"><span data-stu-id="ec89a-255">11</span></span>|<span data-ttu-id="ec89a-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="ec89a-256">Agcaoili</span></span>|  
|<span data-ttu-id="ec89a-257">12</span><span class="sxs-lookup"><span data-stu-id="ec89a-257">12</span></span>|<span data-ttu-id="ec89a-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="ec89a-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="ec89a-259">分组</span><span class="sxs-lookup"><span data-stu-id="ec89a-259">Grouping</span></span>  

 <span data-ttu-id="ec89a-260">[分组依据](group-by-entity-sql.md) 指定由查询返回的对象 ([选择](select-entity-sql.md) 要放置) 表达式的组。</span><span class="sxs-lookup"><span data-stu-id="ec89a-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="ec89a-261">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="ec89a-262">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-262">Output:</span></span>  
  
|<span data-ttu-id="ec89a-263">name</span><span class="sxs-lookup"><span data-stu-id="ec89a-263">name</span></span>|  
|----------|  
|<span data-ttu-id="ec89a-264">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="ec89a-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="ec89a-265">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="ec89a-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="ec89a-266">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="ec89a-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="ec89a-267">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="ec89a-268">导航</span><span class="sxs-lookup"><span data-stu-id="ec89a-268">Navigation</span></span>  

 <span data-ttu-id="ec89a-269">关系导航运算符用于导航从一个实体（起始端）到另一个实体（结束端）的关系。</span><span class="sxs-lookup"><span data-stu-id="ec89a-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="ec89a-270">[导航](navigate-entity-sql.md)采用 \<namespace> 限定为的关系类型。 \<relationship type name></span><span class="sxs-lookup"><span data-stu-id="ec89a-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="ec89a-271">\<T>如果结束端的基数为1，则导航返回 Ref。</span><span class="sxs-lookup"><span data-stu-id="ec89a-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="ec89a-272">如果结束端的基数为 n，将返回<引用> 的集合 \<T> 。</span><span class="sxs-lookup"><span data-stu-id="ec89a-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="ec89a-273">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="ec89a-274">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-274">Output:</span></span>  
  
|<span data-ttu-id="ec89a-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="ec89a-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="ec89a-276">1</span><span class="sxs-lookup"><span data-stu-id="ec89a-276">1</span></span>|  
|<span data-ttu-id="ec89a-277">2</span><span class="sxs-lookup"><span data-stu-id="ec89a-277">2</span></span>|  
|<span data-ttu-id="ec89a-278">3</span><span class="sxs-lookup"><span data-stu-id="ec89a-278">3</span></span>|  
|<span data-ttu-id="ec89a-279">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="ec89a-280">SELECT VALUE 和 SELECT</span><span class="sxs-lookup"><span data-stu-id="ec89a-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="ec89a-281">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="ec89a-281">SELECT VALUE</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="ec89a-282">提供了 SELECT VALUE 子句以跳过隐式行构造。</span><span class="sxs-lookup"><span data-stu-id="ec89a-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="ec89a-283">SELECT VALUE 子句中只能指定一项。</span><span class="sxs-lookup"><span data-stu-id="ec89a-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="ec89a-284">使用此类子句时，将不会围绕 SELECT 子句中的项构造行包装器，并且可生成所需形状的集合，例如： `SELECT VALUE a` 。</span><span class="sxs-lookup"><span data-stu-id="ec89a-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="ec89a-285">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="ec89a-286">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-286">Output:</span></span>  
  
|<span data-ttu-id="ec89a-287">名称</span><span class="sxs-lookup"><span data-stu-id="ec89a-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="ec89a-288">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="ec89a-288">Adjustable Race</span></span>|  
|<span data-ttu-id="ec89a-289">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="ec89a-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="ec89a-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="ec89a-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="ec89a-291">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="ec89a-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="ec89a-292">SELECT</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="ec89a-293">还提供了用于构造任意行的行构造函数。</span><span class="sxs-lookup"><span data-stu-id="ec89a-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="ec89a-294">SELECT 接受投影中的一个或多个元素，并生成含有字段的数据记录，例如：`SELECT a, b, c`。</span><span class="sxs-lookup"><span data-stu-id="ec89a-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="ec89a-295">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-295">Example:</span></span>  
  
 <span data-ttu-id="ec89a-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="ec89a-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="ec89a-297">名称</span><span class="sxs-lookup"><span data-stu-id="ec89a-297">Name</span></span>|<span data-ttu-id="ec89a-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="ec89a-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="ec89a-299">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="ec89a-299">Adjustable Race</span></span>|<span data-ttu-id="ec89a-300">1</span><span class="sxs-lookup"><span data-stu-id="ec89a-300">1</span></span>|  
|<span data-ttu-id="ec89a-301">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="ec89a-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="ec89a-302">879</span><span class="sxs-lookup"><span data-stu-id="ec89a-302">879</span></span>|  
|<span data-ttu-id="ec89a-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="ec89a-303">AWC Logo Cap</span></span>|<span data-ttu-id="ec89a-304">712</span><span class="sxs-lookup"><span data-stu-id="ec89a-304">712</span></span>|  
|<span data-ttu-id="ec89a-305">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-305">...</span></span>|<span data-ttu-id="ec89a-306">...</span><span class="sxs-lookup"><span data-stu-id="ec89a-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="ec89a-307">CASE 表达式</span><span class="sxs-lookup"><span data-stu-id="ec89a-307">CASE EXPRESSION</span></span>  

 <span data-ttu-id="ec89a-308">[Case 表达式](case-entity-sql.md)计算一组布尔表达式的值以确定结果。</span><span class="sxs-lookup"><span data-stu-id="ec89a-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="ec89a-309">示例：</span><span class="sxs-lookup"><span data-stu-id="ec89a-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="ec89a-310">输出：</span><span class="sxs-lookup"><span data-stu-id="ec89a-310">Output:</span></span>  
  
|<span data-ttu-id="ec89a-311">值</span><span class="sxs-lookup"><span data-stu-id="ec89a-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="ec89a-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="ec89a-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec89a-313">请参阅</span><span class="sxs-lookup"><span data-stu-id="ec89a-313">See also</span></span>

- [<span data-ttu-id="ec89a-314">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="ec89a-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ec89a-315">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="ec89a-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
