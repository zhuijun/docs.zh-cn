---
title: 必须进行收缩转换才能用这些参数调用可访问的重载“<methodname>”：
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousMatch_NarrowingConversion1
ms.assetid: 2fdbadb9-8ef1-404a-a2ed-ce5f5e55cfcb
ms.openlocfilehash: 2d3e2d4864fb454a14e1614c3f278c7042ccf725
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376607"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion"></a><span data-ttu-id="31c96-102">必须进行收缩转换才能用这些参数调用可访问的重载“\<methodname>”：</span><span class="sxs-lookup"><span data-stu-id="31c96-102">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion</span></span>
<span data-ttu-id="31c96-103">调用了重载方法，但是方法不可与所提供的未进行收缩转换的参数列表相匹配。</span><span class="sxs-lookup"><span data-stu-id="31c96-103">An overloaded method was called, but no method was matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="31c96-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="31c96-104">To correct this error</span></span>  
  
1. <span data-ttu-id="31c96-105">指定 `Option Strict Off`。</span><span class="sxs-lookup"><span data-stu-id="31c96-105">Specify `Option Strict Off`.</span></span>  
  
2. <span data-ttu-id="31c96-106">更改参数以匹配重载方法的其中一个签名。</span><span class="sxs-lookup"><span data-stu-id="31c96-106">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c96-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31c96-107">See also</span></span>

- [<span data-ttu-id="31c96-108">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="31c96-108">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="31c96-109">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="31c96-109">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
