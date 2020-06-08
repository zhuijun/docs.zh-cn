---
title: 如何：注册取消请求的回调
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: 0482d43925f4f547114119a95909501cbf09eedb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279357"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="dd130-102">如何：注册取消请求的回调</span><span class="sxs-lookup"><span data-stu-id="dd130-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="dd130-103">下面的示例展示了如何注册委托，以在 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 属性因对创建令牌的对象调用 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 而变为 True 时调用。</span><span class="sxs-lookup"><span data-stu-id="dd130-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="dd130-104">使用此技术可取消本地不支持统一取消框架的异步操作，也可取消阻止可能等待异步操作结束的方法。</span><span class="sxs-lookup"><span data-stu-id="dd130-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd130-105">某些情况下，当启用“仅我的代码”后，Visual Studio 会在引发异常的行中断运行并显示一条错误消息，该消息显示“用户代码未处理异常”。</span><span class="sxs-lookup"><span data-stu-id="dd130-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="dd130-106">此错误是良性的。</span><span class="sxs-lookup"><span data-stu-id="dd130-106">This error is benign.</span></span> <span data-ttu-id="dd130-107">可以按 F5 继续运行，并请参阅下面示例中所示的异常处理行为。</span><span class="sxs-lookup"><span data-stu-id="dd130-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="dd130-108">为了阻止 Visual Studio 在第一个错误出现时中断，只需依次转到“工具”、“选项”、“调试”、“常规”  下，取消选中“仅我的代码”复选框即可。</span><span class="sxs-lookup"><span data-stu-id="dd130-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd130-109">示例</span><span class="sxs-lookup"><span data-stu-id="dd130-109">Example</span></span>  
 <span data-ttu-id="dd130-110">在下面的示例中，<xref:System.Net.WebClient.CancelAsync%2A> 方法注册为在通过取消标记请求取消时要调用的方法。</span><span class="sxs-lookup"><span data-stu-id="dd130-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="dd130-111">如果注册回调时已经请求了取消，那么仍然要保证调用回调。</span><span class="sxs-lookup"><span data-stu-id="dd130-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="dd130-112">在此特定情况下，如果当前未执行异步操作，则 <xref:System.Net.WebClient.CancelAsync%2A> 方法将不进行任何操作，因此调用此方法始终是安全的。</span><span class="sxs-lookup"><span data-stu-id="dd130-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd130-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd130-113">See also</span></span>

- [<span data-ttu-id="dd130-114">托管线程中的取消</span><span class="sxs-lookup"><span data-stu-id="dd130-114">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
