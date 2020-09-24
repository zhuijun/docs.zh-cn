---
title: '>=（大于或等于）(Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 02e03d6d2da321bd02ea2b14e45a910853d39c4d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158417"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="07705-102">>= (大于或等于)  (实体 SQL) </span><span class="sxs-lookup"><span data-stu-id="07705-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>

<span data-ttu-id="07705-103">比较两个表达式以确定左侧表达式的值是否大于或等于右侧表达式的值。</span><span class="sxs-lookup"><span data-stu-id="07705-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07705-104">语法</span><span class="sxs-lookup"><span data-stu-id="07705-104">Syntax</span></span>  
  
```sql  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="07705-105">参数</span><span class="sxs-lookup"><span data-stu-id="07705-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="07705-106">任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="07705-106">Any valid expression.</span></span> <span data-ttu-id="07705-107">两个表达式都必须包含可隐式转换的数据类型。</span><span class="sxs-lookup"><span data-stu-id="07705-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="07705-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="07705-108">Result Types</span></span>  

 <span data-ttu-id="07705-109">如果左侧表达式的值大于或等于右侧表达式的值，则为`true` ；否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="07705-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07705-110">示例</span><span class="sxs-lookup"><span data-stu-id="07705-110">Example</span></span>  

 <span data-ttu-id="07705-111">下面的 Entity SQL 查询使用 >= 比较运算符比较两个表达式，以确定左侧表达式的值是否大于或等于右侧表达式的值。</span><span class="sxs-lookup"><span data-stu-id="07705-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="07705-112">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="07705-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="07705-113">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="07705-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="07705-114">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="07705-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="07705-115">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="07705-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="07705-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="07705-116">See also</span></span>

- [<span data-ttu-id="07705-117">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="07705-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
