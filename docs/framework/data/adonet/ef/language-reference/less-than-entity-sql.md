---
title: '< (小于)  (实体 SQL) '
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 389c50a697c90dadb075369fe696f7382caf3cff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161914"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="0c05b-102">\<（小于）(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0c05b-102">\< (Less Than) (Entity SQL)</span></span>

<span data-ttu-id="0c05b-103">比较两个表达式以确定左侧表达式的值是否小于右侧表达式的值。</span><span class="sxs-lookup"><span data-stu-id="0c05b-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c05b-104">语法</span><span class="sxs-lookup"><span data-stu-id="0c05b-104">Syntax</span></span>  
  
```sql  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0c05b-105">参数</span><span class="sxs-lookup"><span data-stu-id="0c05b-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="0c05b-106">任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="0c05b-106">Any valid expression.</span></span> <span data-ttu-id="0c05b-107">两个表达式都必须包含可隐式转换的数据类型。</span><span class="sxs-lookup"><span data-stu-id="0c05b-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0c05b-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="0c05b-108">Result Types</span></span>  

 <span data-ttu-id="0c05b-109">如果左侧表达式的值小于右侧表达式的值，则为`true` ；否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="0c05b-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c05b-110">示例</span><span class="sxs-lookup"><span data-stu-id="0c05b-110">Example</span></span>  

 <span data-ttu-id="0c05b-111">下面的 Entity SQL 查询使用 < 比较运算符比较两个表达式，以确定左侧表达式的值是否小于右侧表达式的值。</span><span class="sxs-lookup"><span data-stu-id="0c05b-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="0c05b-112">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="0c05b-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0c05b-113">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="0c05b-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0c05b-114">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="0c05b-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0c05b-115">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="0c05b-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="0c05b-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="0c05b-116">See also</span></span>

- [<span data-ttu-id="0c05b-117">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="0c05b-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
