---
title: 如何：调用不返回值的过程
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 514d6e576b9b782387840ae04dcefa00de876aa9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388733"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="4271c-102">如何：调用不返回值的过程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4271c-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="4271c-103">`Sub`过程不会将值返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="4271c-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="4271c-104">您可以使用独立的调用语句显式调用它。</span><span class="sxs-lookup"><span data-stu-id="4271c-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="4271c-105">不能只是在表达式中使用其名称来调用它。</span><span class="sxs-lookup"><span data-stu-id="4271c-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="4271c-106">调用 Sub 过程</span><span class="sxs-lookup"><span data-stu-id="4271c-106">To call a Sub procedure</span></span>  
  
1. <span data-ttu-id="4271c-107">指定过程的名称 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="4271c-107">Specify the name of the `Sub` procedure.</span></span>  
  
2. <span data-ttu-id="4271c-108">在过程名称后面加上括号，以将参数列表括起来。</span><span class="sxs-lookup"><span data-stu-id="4271c-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="4271c-109">如果没有参数，则可以选择省略括号。</span><span class="sxs-lookup"><span data-stu-id="4271c-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="4271c-110">不过，使用括号可使代码更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="4271c-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="4271c-111">将参数置于括号中的参数列表内，用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="4271c-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="4271c-112">请确保以 `Sub` 过程定义相应参数的相同顺序提供参数。</span><span class="sxs-lookup"><span data-stu-id="4271c-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="4271c-113">下面的示例调用 Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 函数来激活应用程序窗口。</span><span class="sxs-lookup"><span data-stu-id="4271c-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="4271c-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>使用窗口标题作为其唯一参数。</span><span class="sxs-lookup"><span data-stu-id="4271c-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="4271c-115">它不会将值返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="4271c-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="4271c-116">如果记事本进程未运行，则该示例引发 <xref:System.ArgumentException> 。</span><span class="sxs-lookup"><span data-stu-id="4271c-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="4271c-117">此 `Shell` 过程假定应用程序位于指定的路径中。</span><span class="sxs-lookup"><span data-stu-id="4271c-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="4271c-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4271c-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [<span data-ttu-id="4271c-119">过程</span><span class="sxs-lookup"><span data-stu-id="4271c-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="4271c-120">Sub 过程</span><span class="sxs-lookup"><span data-stu-id="4271c-120">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="4271c-121">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="4271c-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="4271c-122">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="4271c-122">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="4271c-123">如何：创建过程</span><span class="sxs-lookup"><span data-stu-id="4271c-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="4271c-124">如何：调用返回值的过程</span><span class="sxs-lookup"><span data-stu-id="4271c-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="4271c-125">如何：在 Visual Basic 中调用事件处理程序</span><span class="sxs-lookup"><span data-stu-id="4271c-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
