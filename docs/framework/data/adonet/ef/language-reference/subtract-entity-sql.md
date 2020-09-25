---
title: '-  (减去)  (实体 SQL) '
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 17841f336ed186dcbc50b84254048546b15297e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181032"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="06454-102">-（减）(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="06454-102">- (Subtract) (Entity SQL)</span></span>

<span data-ttu-id="06454-103">两个数相减。</span><span class="sxs-lookup"><span data-stu-id="06454-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06454-104">语法</span><span class="sxs-lookup"><span data-stu-id="06454-104">Syntax</span></span>  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="06454-105">参数</span><span class="sxs-lookup"><span data-stu-id="06454-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="06454-106">任何一种数值数据类型的任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="06454-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="06454-107">结果类型</span><span class="sxs-lookup"><span data-stu-id="06454-107">Result Types</span></span>  

 <span data-ttu-id="06454-108">对这两个参数进行隐式类型提升而产生的数据类型。</span><span class="sxs-lookup"><span data-stu-id="06454-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="06454-109">有关隐式类型升级的详细信息，请参阅 [类型系统](type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="06454-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06454-110">示例</span><span class="sxs-lookup"><span data-stu-id="06454-110">Example</span></span>  

 <span data-ttu-id="06454-111">以下 Entity SQL 查询使用 - 算术运算符将两个数字相减。</span><span class="sxs-lookup"><span data-stu-id="06454-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="06454-112">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="06454-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="06454-113">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="06454-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="06454-114">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="06454-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="06454-115">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="06454-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="06454-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="06454-116">See also</span></span>

- [<span data-ttu-id="06454-117">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="06454-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
