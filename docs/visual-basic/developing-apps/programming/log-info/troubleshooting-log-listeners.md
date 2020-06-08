---
title: 疑难解答：日志侦听器
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 8d2d8294d9e9bb42d72fe4f6c37bf846bd644907
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398313"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="f8fb5-102">疑难解答：日志侦听器 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8fb5-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="f8fb5-103">可以使用 `My.Application.Log` 和 `My.Log` 对象来记录有关应用程序中所发生事件的信息。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="f8fb5-104">若要确定接收这些消息的日志侦听器，请参阅[演练：确定 My.Application.Log 写入信息的位置](walkthrough-determining-where-my-application-log-writes-information.md)。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="f8fb5-105">`Log` 对象可以使用日志筛选来限制其记录的信息量。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="f8fb5-106">如果筛选器配置错误，则日志可能包含错误信息。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="f8fb5-107">有关筛选的详细信息，请参阅[演练：筛选 My.Application.Log 输出](walkthrough-filtering-my-application-log-output.md)。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="f8fb5-108">但是，如果日志配置不正确，则可能需要有关其当前配置的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="f8fb5-109">可通过日志的高级 `TraceSource` 属性获取此信息。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="f8fb5-110">若要确定代码中日志对象的日志侦听器</span><span class="sxs-lookup"><span data-stu-id="f8fb5-110">To determine the log listeners for the Log object in code</span></span>  
  
1. <span data-ttu-id="f8fb5-111">在代码文件的开头导入 <xref:System.Diagnostics> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="f8fb5-112">有关详细信息，请参阅 [Imports 语句（.NET 命名空间和类型）](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. <span data-ttu-id="f8fb5-113">创建一个函数，该函数返回由每个日志侦听器的信息组成的字符串。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. <span data-ttu-id="f8fb5-114">将日志跟踪侦听器的集合传递到 `GetListeners` 函数，并显示返回值。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="f8fb5-115">有关详细信息，请参阅 <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>。</span><span class="sxs-lookup"><span data-stu-id="f8fb5-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8fb5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8fb5-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="f8fb5-117">使用应用程序日志</span><span class="sxs-lookup"><span data-stu-id="f8fb5-117">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="f8fb5-118">演练：确定 My.Application.Log 写入信息的位置</span><span class="sxs-lookup"><span data-stu-id="f8fb5-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
