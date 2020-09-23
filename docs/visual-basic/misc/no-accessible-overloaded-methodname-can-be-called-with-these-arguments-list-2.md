---
title: 无 <methodname> 需收缩转换即可用这些参数调用可访问的重载 ""： <list>
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall2
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
ms.openlocfilehash: 0c39f3eab77bd58d4f1f81cd8e7f1c95b0753c7f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079030"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion-list"></a><span data-ttu-id="a414a-102">无 \<methodname> 需收缩转换即可用这些参数调用可访问的重载 ""： \<list></span><span class="sxs-lookup"><span data-stu-id="a414a-102">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion: \<list></span></span>

<span data-ttu-id="a414a-103">调用了重载方法，但是该方法必须进行缩放转换才能与提供的参数列表匹配。</span><span class="sxs-lookup"><span data-stu-id="a414a-103">An overloaded method was called, but the method cannot be matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a414a-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="a414a-104">To correct this error</span></span>  
  
1. <span data-ttu-id="a414a-105">指定 `Option Strict Off`。</span><span class="sxs-lookup"><span data-stu-id="a414a-105">Specify `Option Strict Off`.</span></span>
  
2. <span data-ttu-id="a414a-106">更改参数以匹配重载方法的签名。</span><span class="sxs-lookup"><span data-stu-id="a414a-106">Change the arguments to match a signature of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a414a-107">请参阅</span><span class="sxs-lookup"><span data-stu-id="a414a-107">See also</span></span>

- [<span data-ttu-id="a414a-108">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="a414a-108">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="a414a-109">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="a414a-109">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
