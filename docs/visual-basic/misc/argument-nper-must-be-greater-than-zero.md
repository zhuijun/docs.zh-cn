---
title: 参数“NPer”必须大于零
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: f0185e30cb711472105955f5febf8d7702b29c72
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087136"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="6694d-102">参数“NPer”必须大于零</span><span class="sxs-lookup"><span data-stu-id="6694d-102">Argument 'NPer' must be greater than zero</span></span>

<span data-ttu-id="6694d-103">返回一个指定基于定期固定付款和固定利率的年金的期间数的 `NPer` 的 `Double` 函数要求一个大于零的参数。</span><span class="sxs-lookup"><span data-stu-id="6694d-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6694d-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="6694d-104">To correct this error</span></span>  
  
- <span data-ttu-id="6694d-105">检查表达式中参数的拼写是否正确。</span><span class="sxs-lookup"><span data-stu-id="6694d-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="6694d-106">拼写错误的变量名可能会隐式创建一个初始化为零的数值变量。</span><span class="sxs-lookup"><span data-stu-id="6694d-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="6694d-107">检查之前对表达式中的变量进行的操作，尤其是那些从其他过程作为参数传递给该过程的操作。</span><span class="sxs-lookup"><span data-stu-id="6694d-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6694d-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="6694d-108">See also</span></span>

- [<span data-ttu-id="6694d-109">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="6694d-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
