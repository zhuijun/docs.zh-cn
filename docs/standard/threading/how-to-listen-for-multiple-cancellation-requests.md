---
title: 如何：侦听多个取消请求
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
ms.openlocfilehash: 3f92d1d9e8fec91475886e8bd7bffbc97bb632a0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279390"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="9de74-102">如何：侦听多个取消请求</span><span class="sxs-lookup"><span data-stu-id="9de74-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="9de74-103">此示例展示了如何同时侦听两个取消令牌，以便在其中任意一个令牌发出请求时取消操作。</span><span class="sxs-lookup"><span data-stu-id="9de74-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9de74-104">某些情况下，当启用“仅我的代码”后，Visual Studio 会在引发异常的行中断运行并显示一条错误消息，该消息显示“用户代码未处理异常”。</span><span class="sxs-lookup"><span data-stu-id="9de74-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="9de74-105">此错误是良性的。</span><span class="sxs-lookup"><span data-stu-id="9de74-105">This error is benign.</span></span> <span data-ttu-id="9de74-106">可以按 F5 继续运行，并请参阅下面示例中所示的异常处理行为。</span><span class="sxs-lookup"><span data-stu-id="9de74-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="9de74-107">为了阻止 Visual Studio 在第一个错误出现时中断，只需依次转到“工具”、“选项”、“调试”、“常规”  下，取消选中“仅我的代码”复选框即可。</span><span class="sxs-lookup"><span data-stu-id="9de74-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9de74-108">示例</span><span class="sxs-lookup"><span data-stu-id="9de74-108">Example</span></span>  
 <span data-ttu-id="9de74-109">在下面的示例中，<xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> 方法用于将两个令牌联接为一个令牌。</span><span class="sxs-lookup"><span data-stu-id="9de74-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="9de74-110">这样一来，可以将此令牌传递到只需要使用一个取消令牌作为参数的方法中。</span><span class="sxs-lookup"><span data-stu-id="9de74-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="9de74-111">此示例展示了以下常见方案：方法必须同时观察从类外部传入的令牌和类内部生成的令牌。</span><span class="sxs-lookup"><span data-stu-id="9de74-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="9de74-112">如果链接令牌抛出 <xref:System.OperationCanceledException>，传递到异常的令牌是链接令牌，而不是任意前置任务令牌。</span><span class="sxs-lookup"><span data-stu-id="9de74-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="9de74-113">若要确定取消的是哪个令牌，请直接查看前置任务令牌的状态。</span><span class="sxs-lookup"><span data-stu-id="9de74-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="9de74-114">虽然 <xref:System.AggregateException> 不得抛出，但此示例捕获到它的原因是，在实际情况下，任务委托抛出的除 <xref:System.OperationCanceledException> 外其他任何异常都包装在 <xref:System.AggregateException> 中。</span><span class="sxs-lookup"><span data-stu-id="9de74-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9de74-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9de74-115">See also</span></span>

- [<span data-ttu-id="9de74-116">托管线程中的取消</span><span class="sxs-lookup"><span data-stu-id="9de74-116">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
