---
title: 错误的 DLL 调用约定
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: a60e44ce92b1805b0a5a6f1d4ce397c295eef202
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409876"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="9300e-102">错误的 DLL 调用约定</span><span class="sxs-lookup"><span data-stu-id="9300e-102">Bad DLL calling convention</span></span>
<span data-ttu-id="9300e-103">传递给动态链接库（DLL）的参数必须与例程所需的参数完全匹配。</span><span class="sxs-lookup"><span data-stu-id="9300e-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="9300e-104">调用约定涉及参数的数字、类型和顺序。</span><span class="sxs-lookup"><span data-stu-id="9300e-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="9300e-105">程序可能正在传递错误类型或参数数目的 DLL 中的例程。</span><span class="sxs-lookup"><span data-stu-id="9300e-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9300e-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="9300e-106">To correct this error</span></span>  
  
1. <span data-ttu-id="9300e-107">请确保所有参数类型都与你要调用的例程声明中指定的类型一致。</span><span class="sxs-lookup"><span data-stu-id="9300e-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="9300e-108">请确保传递的参数数目与要调用的例程声明中指定的参数数目相同。</span><span class="sxs-lookup"><span data-stu-id="9300e-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="9300e-109">如果 DLL 例程需要参数的值，请确保 `ByVal` 在例程的声明中为这些参数指定。</span><span class="sxs-lookup"><span data-stu-id="9300e-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9300e-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9300e-110">See also</span></span>

- [<span data-ttu-id="9300e-111">错误类型</span><span class="sxs-lookup"><span data-stu-id="9300e-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="9300e-112">Call 语句</span><span class="sxs-lookup"><span data-stu-id="9300e-112">Call Statement</span></span>](../statements/call-statement.md)
- [<span data-ttu-id="9300e-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="9300e-113">Declare Statement</span></span>](../statements/declare-statement.md)
