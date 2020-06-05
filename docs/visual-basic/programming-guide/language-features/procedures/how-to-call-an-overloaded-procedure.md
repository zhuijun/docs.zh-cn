---
title: 如何：调用重载过程
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: de101309fa1edaaddc3defc5759d9293fbef684c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388538"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="588e2-102">如何：调用重载过程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="588e2-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="588e2-103">重载过程的优点是调用的灵活性。</span><span class="sxs-lookup"><span data-stu-id="588e2-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="588e2-104">调用代码可以获取它需要传递给过程的信息，然后调用单个过程名称，无论它传递了哪些参数。</span><span class="sxs-lookup"><span data-stu-id="588e2-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="588e2-105">调用具有多个定义版本的过程</span><span class="sxs-lookup"><span data-stu-id="588e2-105">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="588e2-106">在调用代码中，确定要传递给过程的数据。</span><span class="sxs-lookup"><span data-stu-id="588e2-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="588e2-107">以正常方式编写过程调用，并在参数列表中显示数据。</span><span class="sxs-lookup"><span data-stu-id="588e2-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="588e2-108">请确保参数与为该过程定义的版本之一中的参数列表匹配。</span><span class="sxs-lookup"><span data-stu-id="588e2-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="588e2-109">您不必确定要调用的过程的版本。</span><span class="sxs-lookup"><span data-stu-id="588e2-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="588e2-110">Visual Basic 将控制传递到与参数列表匹配的版本。</span><span class="sxs-lookup"><span data-stu-id="588e2-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="588e2-111">下面的示例调用 `post` [如何：定义过程的多个版本](./how-to-define-multiple-versions-of-a-procedure.md)中声明的过程。</span><span class="sxs-lookup"><span data-stu-id="588e2-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="588e2-112">它获取客户标识，确定它是 `String` 还是 `Integer` ，然后在任一情况下都调用相同的过程。</span><span class="sxs-lookup"><span data-stu-id="588e2-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="588e2-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="588e2-113">See also</span></span>

- [<span data-ttu-id="588e2-114">过程</span><span class="sxs-lookup"><span data-stu-id="588e2-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="588e2-115">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="588e2-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="588e2-116">过程重载</span><span class="sxs-lookup"><span data-stu-id="588e2-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="588e2-117">过程疑难解答</span><span class="sxs-lookup"><span data-stu-id="588e2-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="588e2-118">如何：定义一个过程的多个版本</span><span class="sxs-lookup"><span data-stu-id="588e2-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="588e2-119">如何：重载带有可选参数的过程</span><span class="sxs-lookup"><span data-stu-id="588e2-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="588e2-120">如何：重载参数数量不确定的过程</span><span class="sxs-lookup"><span data-stu-id="588e2-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="588e2-121">重载过程注意事项</span><span class="sxs-lookup"><span data-stu-id="588e2-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="588e2-122">重载决策</span><span class="sxs-lookup"><span data-stu-id="588e2-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="588e2-123">重载</span><span class="sxs-lookup"><span data-stu-id="588e2-123">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
