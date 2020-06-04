---
title: 范围变量 <variable> 隐藏封闭块中的变量、以前定义的范围变量或在查询表达式中隐式声明的变量
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 290ca81dea500558ed73956c91bdf7bfec312014
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400391"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="8a88e-102">范围变量 \<variable> 隐藏封闭块中的变量、以前定义的范围变量或在查询表达式中隐式声明的变量</span><span class="sxs-lookup"><span data-stu-id="8a88e-102">Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="8a88e-103">在、、或子句中指定的范围变量名称会 `Select` `From` `Aggregate` `Let` 复制以前在查询中指定的范围变量的名称，或查询隐式声明的变量的名称，例如字段名称或聚合函数的名称。</span><span class="sxs-lookup"><span data-stu-id="8a88e-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="8a88e-104">**错误 ID：** BC36633</span><span class="sxs-lookup"><span data-stu-id="8a88e-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8a88e-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="8a88e-105">To correct this error</span></span>  
  
- <span data-ttu-id="8a88e-106">确保特定查询范围内的所有范围变量都具有唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="8a88e-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="8a88e-107">可以将查询括在括号中，以确保嵌套查询具有唯一的作用域。</span><span class="sxs-lookup"><span data-stu-id="8a88e-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a88e-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8a88e-108">See also</span></span>

- [<span data-ttu-id="8a88e-109">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="8a88e-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="8a88e-110">From 子句</span><span class="sxs-lookup"><span data-stu-id="8a88e-110">From Clause</span></span>](../queries/from-clause.md)
- [<span data-ttu-id="8a88e-111">Let 子句</span><span class="sxs-lookup"><span data-stu-id="8a88e-111">Let Clause</span></span>](../queries/let-clause.md)
- [<span data-ttu-id="8a88e-112">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="8a88e-112">Aggregate Clause</span></span>](../queries/aggregate-clause.md)
- [<span data-ttu-id="8a88e-113">Select 子句</span><span class="sxs-lookup"><span data-stu-id="8a88e-113">Select Clause</span></span>](../queries/select-clause.md)
