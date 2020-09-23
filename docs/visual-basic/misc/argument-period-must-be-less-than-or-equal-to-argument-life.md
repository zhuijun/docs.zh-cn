---
title: 自变量“Period”必须小于或等于自变量“Life”
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_PeriodLELife
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
ms.openlocfilehash: 844192f1168e6fef7906ffc133dcc3b5ba40b42c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087032"
---
# <a name="argument-period-must-be-less-than-or-equal-to-argument-life"></a><span data-ttu-id="3a384-102">自变量“Period”必须小于或等于自变量“Life”</span><span class="sxs-lookup"><span data-stu-id="3a384-102">Argument 'Period' must be less than or equal to argument 'Life'</span></span>

<span data-ttu-id="3a384-103">`Period` 参数的值（指定计算资产折旧的时期）大于 `Life` 参数的值。</span><span class="sxs-lookup"><span data-stu-id="3a384-103">The value of the `Period` argument, which specifies the period for which asset depreciation is calculated, is greater than the value of the `Life` argument.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3a384-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="3a384-104">To correct this error</span></span>  
  
- <span data-ttu-id="3a384-105">确保 `Life` 和 `Period` 参数以相同的单位表示。</span><span class="sxs-lookup"><span data-stu-id="3a384-105">Ensure that the `Life` and `Period` arguments are expressed in the same units.</span></span> <span data-ttu-id="3a384-106">例如，如果 `Life` 以月为单位，则 `Period` 也应以月为单位。</span><span class="sxs-lookup"><span data-stu-id="3a384-106">For example, if `Life` is measured in months, `Period` should be as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a384-107">请参阅</span><span class="sxs-lookup"><span data-stu-id="3a384-107">See also</span></span>

- [<span data-ttu-id="3a384-108">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="3a384-108">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
