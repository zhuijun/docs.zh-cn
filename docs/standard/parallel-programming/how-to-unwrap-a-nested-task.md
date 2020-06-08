---
title: 如何：解除嵌套任务的包装
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: 9a69fa42da41ee4a071a6571042fd96fb5a009d2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288025"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="520ce-102">如何：解除嵌套任务的包装</span><span class="sxs-lookup"><span data-stu-id="520ce-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="520ce-103">可以从方法返回任务，再等待或继续执行此任务，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="520ce-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="520ce-104">在上面的示例中，<xref:System.Threading.Tasks.Task%601.Result%2A> 属性的类型为 `string`（Visual Basic 中的 `String`）。</span><span class="sxs-lookup"><span data-stu-id="520ce-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="520ce-105">不过，在某些情况下，建议在另一个任务中创建任务，再返回嵌套任务。</span><span class="sxs-lookup"><span data-stu-id="520ce-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="520ce-106">在这种情况下，封闭任务的 `TResult` 本身就是任务。</span><span class="sxs-lookup"><span data-stu-id="520ce-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="520ce-107">在下面的示例中，Result 属性是 C# 中的 `Task<Task<string>>` 或 Visual Basic 中的 `Task(Of Task(Of String))`。</span><span class="sxs-lookup"><span data-stu-id="520ce-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="520ce-108">虽然可以编写代码来取消包装外部任务并检索原始任务及其 <xref:System.Threading.Tasks.Task%601.Result%2A> 属性，但此类代码不易编写，因为必须处理异常和取消请求。</span><span class="sxs-lookup"><span data-stu-id="520ce-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="520ce-109">在这种情况下，建议使用 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 扩展方法之一，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="520ce-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="520ce-110"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 方法可用于将任何 `Task<Task>` 或 `Task<Task<TResult>>`（Visual Basic 中的 `Task(Of Task)` 或 `Task(Of Task(Of TResult))`）转换为 `Task` 或 `Task<TResult>`（Visual Basic 中的 `Task(Of TResult)`）。</span><span class="sxs-lookup"><span data-stu-id="520ce-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="520ce-111">新任务完全表示内部嵌套任务，并包含取消状态和所有异常。</span><span class="sxs-lookup"><span data-stu-id="520ce-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="520ce-112">示例</span><span class="sxs-lookup"><span data-stu-id="520ce-112">Example</span></span>  
 <span data-ttu-id="520ce-113">下面的示例展示了如何使用 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 扩展方法。</span><span class="sxs-lookup"><span data-stu-id="520ce-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="520ce-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="520ce-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="520ce-115">基于任务的异步编程</span><span class="sxs-lookup"><span data-stu-id="520ce-115">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
