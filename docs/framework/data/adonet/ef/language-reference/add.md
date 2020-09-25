---
title: + （加）
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: b86d273658362c3bb204d5220ff5e9db1f8de9fe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198049"
---
# <a name="-add"></a><span data-ttu-id="ac3fc-102">+（添加）</span><span class="sxs-lookup"><span data-stu-id="ac3fc-102">+ (Add)</span></span>

<span data-ttu-id="ac3fc-103">两个数相加。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac3fc-104">语法</span><span class="sxs-lookup"><span data-stu-id="ac3fc-104">Syntax</span></span>  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac3fc-105">参数</span><span class="sxs-lookup"><span data-stu-id="ac3fc-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="ac3fc-106">任何一种数值数据类型的任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ac3fc-107">结果类型</span><span class="sxs-lookup"><span data-stu-id="ac3fc-107">Result Types</span></span>  

 <span data-ttu-id="ac3fc-108">对这两个参数进行隐式类型提升而产生的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="ac3fc-109">有关隐式类型升级的详细信息，请参阅 [类型系统](type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac3fc-110">备注</span><span class="sxs-lookup"><span data-stu-id="ac3fc-110">Remarks</span></span>  

 <span data-ttu-id="ac3fc-111">对于 EDM.String 类型，加法指的是串联。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac3fc-112">示例</span><span class="sxs-lookup"><span data-stu-id="ac3fc-112">Example</span></span>  

 <span data-ttu-id="ac3fc-113">以下 Entity SQL 查询使用 + 算术运算符将两个数值相加。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="ac3fc-114">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ac3fc-115">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="ac3fc-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ac3fc-116">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ac3fc-117">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="ac3fc-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="ac3fc-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="ac3fc-118">See also</span></span>

- [<span data-ttu-id="ac3fc-119">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="ac3fc-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ac3fc-120">概念模型类型 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="ac3fc-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
