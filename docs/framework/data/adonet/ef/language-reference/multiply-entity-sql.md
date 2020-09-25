---
title: '*  (乘)  (实体 SQL) '
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 3dd77270e6765a0431dc473bbbcadeb6481a4699
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175650"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="eadf6-102">\*（乘）(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="eadf6-102">\* (Multiply) (Entity SQL)</span></span>

<span data-ttu-id="eadf6-103">将两个表达式相乘。</span><span class="sxs-lookup"><span data-stu-id="eadf6-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eadf6-104">语法</span><span class="sxs-lookup"><span data-stu-id="eadf6-104">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="eadf6-105">参数</span><span class="sxs-lookup"><span data-stu-id="eadf6-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="eadf6-106">任何一种数值数据类型的任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="eadf6-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="eadf6-107">结果类型</span><span class="sxs-lookup"><span data-stu-id="eadf6-107">Result Types</span></span>  

 <span data-ttu-id="eadf6-108">对这两个参数进行隐式类型提升而产生的数据类型。</span><span class="sxs-lookup"><span data-stu-id="eadf6-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="eadf6-109">有关隐式类型升级的详细信息，请参阅 [类型系统](type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="eadf6-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eadf6-110">示例</span><span class="sxs-lookup"><span data-stu-id="eadf6-110">Example</span></span>  

 <span data-ttu-id="eadf6-111">以下 Entity SQL 查询使用 \* 算术运算符将两个数字相乘。</span><span class="sxs-lookup"><span data-stu-id="eadf6-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="eadf6-112">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="eadf6-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="eadf6-113">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="eadf6-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="eadf6-114">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="eadf6-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="eadf6-115">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="eadf6-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="eadf6-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="eadf6-116">See also</span></span>

- [<span data-ttu-id="eadf6-117">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="eadf6-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
