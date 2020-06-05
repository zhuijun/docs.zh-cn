---
title: 已禁用函数求值，因为前一个函数求值超时
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 7b0113e9c1018772da6dc180f7fc5beb0e922917
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402948"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="86098-102">已禁用函数求值，因为前一个函数求值超时</span><span class="sxs-lookup"><span data-stu-id="86098-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="86098-103">已禁用函数求值，因为上一个函数求值超时。若要重新启用函数求值，请再次单步执行或重新启动调试。</span><span class="sxs-lookup"><span data-stu-id="86098-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="86098-104">在 Visual Studio 调试器中，表达式指定了一个过程调用，但另一个计算已超时。</span><span class="sxs-lookup"><span data-stu-id="86098-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="86098-105">过程调用超时的可能原因包括无限循环或*无限循环*。</span><span class="sxs-lookup"><span data-stu-id="86098-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="86098-106">有关详细信息，请参阅[For .。。下一语句](../statements/for-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="86098-106">For more information, see [For...Next Statement](../statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="86098-107">无限循环的一种特殊情况是 "*递归*"。</span><span class="sxs-lookup"><span data-stu-id="86098-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="86098-108">有关详细信息，请参阅[递归过程](../../programming-guide/language-features/procedures/recursive-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="86098-108">For more information, see [Recursive Procedures](../../programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="86098-109">**错误 ID：** BC30957</span><span class="sxs-lookup"><span data-stu-id="86098-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="86098-110">更正此错误</span><span class="sxs-lookup"><span data-stu-id="86098-110">To correct this error</span></span>  
  
1. <span data-ttu-id="86098-111">如果可能，请确定以前的函数求值以及导致其超时的原因。否则，可能会再次遇到此错误。</span><span class="sxs-lookup"><span data-stu-id="86098-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2. <span data-ttu-id="86098-112">再次单步执行调试器，或终止并重新启动调试。</span><span class="sxs-lookup"><span data-stu-id="86098-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86098-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="86098-113">See also</span></span>

- [<span data-ttu-id="86098-114">在 Visual Studio 中进行调试</span><span class="sxs-lookup"><span data-stu-id="86098-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="86098-115">使用调试器浏览代码</span><span class="sxs-lookup"><span data-stu-id="86098-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
