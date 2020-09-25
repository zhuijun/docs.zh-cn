---
title: （取模）（实体 SQL）
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 25bd34db3a627fa708e1ab9a3f0e237426487bcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175702"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="03a19-102">（取模）（实体 SQL）</span><span class="sxs-lookup"><span data-stu-id="03a19-102">(Modulo) (Entity SQL)</span></span>

<span data-ttu-id="03a19-103">返回两个表达式相除后的余数。</span><span class="sxs-lookup"><span data-stu-id="03a19-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a19-104">语法</span><span class="sxs-lookup"><span data-stu-id="03a19-104">Syntax</span></span>  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="03a19-105">参数</span><span class="sxs-lookup"><span data-stu-id="03a19-105">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="03a19-106">被除数的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="03a19-106">The numeric expression to divide.</span></span> <span data-ttu-id="03a19-107">`dividend` 为任何一种数值数据类型的任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="03a19-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="03a19-108">除数的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="03a19-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="03a19-109">`divisor` 为任何一种数值数据类型的任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="03a19-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="03a19-110">结果类型</span><span class="sxs-lookup"><span data-stu-id="03a19-110">Result Types</span></span>  

 <span data-ttu-id="03a19-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="03a19-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a19-112">示例</span><span class="sxs-lookup"><span data-stu-id="03a19-112">Example</span></span>  

 <span data-ttu-id="03a19-113">以下 Entity SQL 查询使用 % 算数运算符以返回两个表达式相除后的余数。</span><span class="sxs-lookup"><span data-stu-id="03a19-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="03a19-114">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="03a19-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="03a19-115">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="03a19-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="03a19-116">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="03a19-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="03a19-117">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="03a19-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="03a19-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="03a19-118">See also</span></span>

- [<span data-ttu-id="03a19-119">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="03a19-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
