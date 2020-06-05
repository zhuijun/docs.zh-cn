---
title: 自变量“Life”不能为零
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_LifeNEZero
ms.assetid: c402da97-a2b2-4219-a83a-0cebbfdffef2
ms.openlocfilehash: a737afb8901382d75c3858f84be1b2359338b057
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368161"
---
# <a name="argument-life-cannot-be-zero"></a><span data-ttu-id="e57a1-102">自变量“Life”不能为零</span><span class="sxs-lookup"><span data-stu-id="e57a1-102">Argument 'Life' cannot be zero</span></span>
<span data-ttu-id="e57a1-103">`Life`的参数（必须为指定资产的使用年限的长度的 `Double` ）无效。</span><span class="sxs-lookup"><span data-stu-id="e57a1-103">An argument for `Life`, which must be a `Double` that specifies the length of useful life of the asset, is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e57a1-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="e57a1-104">To correct this error</span></span>  
  
- <span data-ttu-id="e57a1-105">检查表达式中参数的拼写是否正确。</span><span class="sxs-lookup"><span data-stu-id="e57a1-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="e57a1-106">拼写错误的变量名可能会隐式创建一个初始化为零的数值变量。</span><span class="sxs-lookup"><span data-stu-id="e57a1-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="e57a1-107">检查之前对表达式中的变量进行的操作，尤其是那些从其他过程作为参数传递给该过程的操作。</span><span class="sxs-lookup"><span data-stu-id="e57a1-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e57a1-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e57a1-108">See also</span></span>

- [<span data-ttu-id="e57a1-109">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="e57a1-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
