---
title: 注册取消请求的回叫
ms.date: 08/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: faa8dada5779f6eaee7a60e6210ec604f5fb4680
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608450"
---
# <a name="register-callbacks-for-cancellation-requests"></a><span data-ttu-id="000d2-102">注册取消请求的回叫</span><span class="sxs-lookup"><span data-stu-id="000d2-102">Register callbacks for cancellation requests</span></span>

<span data-ttu-id="000d2-103">了解如何注册当 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 属性为 true 时调用的委托。</span><span class="sxs-lookup"><span data-stu-id="000d2-103">Learn how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true.</span></span> <span data-ttu-id="000d2-104">对创建令牌的对象调用 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 时，值将从 false 更改为 true。</span><span class="sxs-lookup"><span data-stu-id="000d2-104">The value changes from false to true when a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token is made.</span></span> <span data-ttu-id="000d2-105">使用此技术可取消本地不支持统一取消框架的异步操作，也可取消阻止可能等待异步操作结束的方法。</span><span class="sxs-lookup"><span data-stu-id="000d2-105">Use this technique for canceling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="000d2-106">某些情况下，当启用“仅我的代码”后，Visual Studio 会在引发异常的行中断运行并显示一条错误消息，该消息显示“用户代码未处理异常”。</span><span class="sxs-lookup"><span data-stu-id="000d2-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="000d2-107">此错误是良性的。</span><span class="sxs-lookup"><span data-stu-id="000d2-107">This error is benign.</span></span> <span data-ttu-id="000d2-108">可以按 <kbd>F5</kbd> 继续运行，并查看下面示例中所示的异常处理行为。</span><span class="sxs-lookup"><span data-stu-id="000d2-108">You can press <kbd>F5</kbd> to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="000d2-109">为了阻止 Visual Studio 在第一个错误出现时中断，只需依次转到“工具”、“选项”、“调试”、“常规”下，取消选中“仅我的代码”复选框即可。</span><span class="sxs-lookup"><span data-stu-id="000d2-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>

## <a name="example"></a><span data-ttu-id="000d2-110">示例</span><span class="sxs-lookup"><span data-stu-id="000d2-110">Example</span></span>

<span data-ttu-id="000d2-111">在下面的示例中，<xref:System.Net.WebClient.CancelAsync%2A> 方法注册为在通过取消标记请求取消时要调用的方法。</span><span class="sxs-lookup"><span data-stu-id="000d2-111">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

<span data-ttu-id="000d2-112">如果注册回调时已经请求了取消，那么仍然要保证调用回调。</span><span class="sxs-lookup"><span data-stu-id="000d2-112">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="000d2-113">在此特定情况下，如果当前未执行异步操作，则 <xref:System.Net.WebClient.CancelAsync%2A> 方法将不进行任何操作，因此调用此方法始终是安全的。</span><span class="sxs-lookup"><span data-stu-id="000d2-113">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>

## <a name="see-also"></a><span data-ttu-id="000d2-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="000d2-114">See also</span></span>

- [<span data-ttu-id="000d2-115">托管线程中的取消</span><span class="sxs-lookup"><span data-stu-id="000d2-115">Cancellation in managed threads</span></span>](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
