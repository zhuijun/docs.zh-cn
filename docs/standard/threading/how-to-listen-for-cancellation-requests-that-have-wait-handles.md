---
title: 如何：侦听具有等待句柄的取消请求
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: e44b10b88bef61edcf3f547f56b4020740530e26
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279538"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="01ca3-102">如何：侦听具有等待句柄的取消请求</span><span class="sxs-lookup"><span data-stu-id="01ca3-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="01ca3-103">如果方法在等待事件收到信号时受阻止，既无法检查取消令牌的值，也无法及时响应。</span><span class="sxs-lookup"><span data-stu-id="01ca3-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="01ca3-104">第一个示例展示了如何在使用 <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 等不本机支持统一取消框架的事件时解决此问题。</span><span class="sxs-lookup"><span data-stu-id="01ca3-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="01ca3-105">第二个示例展示了一种更简化的方法，即使用确实支持统一取消的 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="01ca3-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01ca3-106">某些情况下，当启用“仅我的代码”后，Visual Studio 会在引发异常的行中断运行并显示一条错误消息，该消息显示“用户代码未处理异常”。</span><span class="sxs-lookup"><span data-stu-id="01ca3-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="01ca3-107">此错误是良性的。</span><span class="sxs-lookup"><span data-stu-id="01ca3-107">This error is benign.</span></span> <span data-ttu-id="01ca3-108">可以按 F5 继续运行，并请参阅下面示例中所示的异常处理行为。</span><span class="sxs-lookup"><span data-stu-id="01ca3-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="01ca3-109">为了阻止 Visual Studio 在第一个错误出现时中断，只需依次转到“工具”、“选项”、“调试”、“常规”  下，取消选中“仅我的代码”复选框即可。</span><span class="sxs-lookup"><span data-stu-id="01ca3-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01ca3-110">示例</span><span class="sxs-lookup"><span data-stu-id="01ca3-110">Example</span></span>  
 <span data-ttu-id="01ca3-111">下面的示例使用 <xref:System.Threading.ManualResetEvent> 展示了如何取消阻止不支持统一取消的等待句柄。</span><span class="sxs-lookup"><span data-stu-id="01ca3-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="01ca3-112">示例</span><span class="sxs-lookup"><span data-stu-id="01ca3-112">Example</span></span>  
 <span data-ttu-id="01ca3-113">下面的示例使用 <xref:System.Threading.ManualResetEventSlim> 展示了如何取消阻止确实支持统一取消的协调基元。</span><span class="sxs-lookup"><span data-stu-id="01ca3-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="01ca3-114">相同的方法可以与其他轻型协调基元（如 <xref:System.Threading.Semaphore>`Slim` 和 <xref:System.Threading.CountdownEvent>）结合使用。</span><span class="sxs-lookup"><span data-stu-id="01ca3-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="01ca3-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01ca3-115">See also</span></span>

- [<span data-ttu-id="01ca3-116">托管线程中的取消</span><span class="sxs-lookup"><span data-stu-id="01ca3-116">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
