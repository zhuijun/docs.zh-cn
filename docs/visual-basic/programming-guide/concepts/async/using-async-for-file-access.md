---
title: 使用 Async 以进行文件访问
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: 2e7fa4a78363a08f2ff25e6a961868e85994e200
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077353"
---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="c5051-102">使用异步进行文件访问 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5051-102">Using Async for File Access (Visual Basic)</span></span>

<span data-ttu-id="c5051-103">可以使用 Async 功能访问文件。</span><span class="sxs-lookup"><span data-stu-id="c5051-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="c5051-104">通过使用异步功能，你可以调用异步方法而无需使用回调，也不需要跨多个方法或 Lambda 表达式来拆分代码。</span><span class="sxs-lookup"><span data-stu-id="c5051-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="c5051-105">若要使同步代码异步，只需调用异步方法而非同步方法，并向代码中添加几个关键字。</span><span class="sxs-lookup"><span data-stu-id="c5051-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="c5051-106">可能出于以下原因向文件访问调用中添加异步：</span><span class="sxs-lookup"><span data-stu-id="c5051-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="c5051-107">异步使 UI 应用程序响应速度更快，因为启动该操作的 UI 线程可以执行其他操作。</span><span class="sxs-lookup"><span data-stu-id="c5051-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="c5051-108">如果 UI 线程必须执行耗时较长的代码（例如超过 50 毫秒），UI 可能会冻结，直到 I/O 完成，此时 UI 线程可以再次处理键盘和鼠标输入及其他事件。</span><span class="sxs-lookup"><span data-stu-id="c5051-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="c5051-109">异步可减少对线程的需要，进而提高 ASP.NET 和其他基于服务器的应用程序的可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="c5051-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="c5051-110">如果应用程序对每次响应都使用专用线程，同时处理 1000 个请求时，则需要 1000 个线程。</span><span class="sxs-lookup"><span data-stu-id="c5051-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="c5051-111">异步操作在等待期间通常不需要使用线程。</span><span class="sxs-lookup"><span data-stu-id="c5051-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="c5051-112">异步操作仅需在结束时短暂使用现有 I/O 完成线程。</span><span class="sxs-lookup"><span data-stu-id="c5051-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="c5051-113">当前条件下，文件访问操作的延迟可能非常低，但以后可能大幅增加。</span><span class="sxs-lookup"><span data-stu-id="c5051-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="c5051-114">例如，文件可能会移动到覆盖全球的服务器。</span><span class="sxs-lookup"><span data-stu-id="c5051-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="c5051-115">使用异步功能所增加的开销很小。</span><span class="sxs-lookup"><span data-stu-id="c5051-115">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="c5051-116">异步任务可以轻松地并行运行。</span><span class="sxs-lookup"><span data-stu-id="c5051-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="c5051-117">运行示例</span><span class="sxs-lookup"><span data-stu-id="c5051-117">Running the Examples</span></span>  

 <span data-ttu-id="c5051-118">若要运行本主题中的示例，可创建“WPF 应用程序”或“Windows 窗体应用程序”，然后添加一个“按钮”。</span><span class="sxs-lookup"><span data-stu-id="c5051-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="c5051-119">在按钮的 `Click` 事件中，添加对每个示例的第一个方法的调用。</span><span class="sxs-lookup"><span data-stu-id="c5051-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="c5051-120">在下面的示例中，包括以下 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="c5051-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="c5051-121">使用 FileStream 类</span><span class="sxs-lookup"><span data-stu-id="c5051-121">Use of the FileStream Class</span></span>  

 <span data-ttu-id="c5051-122">本主题中的示例使用 <xref:System.IO.FileStream> 类，该类包含可导致在操作系统级别出现异步 I/O 的选项。</span><span class="sxs-lookup"><span data-stu-id="c5051-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="c5051-123">使用此选项可避免在许多情况下阻止 ThreadPool 线程。</span><span class="sxs-lookup"><span data-stu-id="c5051-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="c5051-124">若要启用此选项，可在构造函数调用中指定 `useAsync=true` 或 `options=FileOptions.Asynchronous` 参数。</span><span class="sxs-lookup"><span data-stu-id="c5051-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="c5051-125">如果通过指定文件路径直接打开 <xref:System.IO.StreamReader> 和 <xref:System.IO.StreamWriter>，则无法将此选项与这二者配合使用。</span><span class="sxs-lookup"><span data-stu-id="c5051-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="c5051-126">但是，如果为二者提供已由 <xref:System.IO.FileStream> 类打开的 <xref:System.IO.Stream>，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="c5051-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="c5051-127">请注意，即使 ThreadPool 线程受到阻止，UI 应用中的异步调用仍然更快，因为 UI 线程在等待期间不会受到阻止。</span><span class="sxs-lookup"><span data-stu-id="c5051-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="c5051-128">编写文本</span><span class="sxs-lookup"><span data-stu-id="c5051-128">Writing Text</span></span>  

 <span data-ttu-id="c5051-129">下面的示例将文本写入文件。</span><span class="sxs-lookup"><span data-stu-id="c5051-129">The following example writes text to a file.</span></span> <span data-ttu-id="c5051-130">在每个 await 语句中，该方法会立即退出。</span><span class="sxs-lookup"><span data-stu-id="c5051-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="c5051-131">文件 I/O 完成后，该方法将在 await 语句后面的语句中继续。</span><span class="sxs-lookup"><span data-stu-id="c5051-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="c5051-132">请注意，async 修饰符在使用 await 语句的方法的定义中。</span><span class="sxs-lookup"><span data-stu-id="c5051-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 <span data-ttu-id="c5051-133">原始示例包含 `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)` 语句，它是下面两个语句的缩写式：</span><span class="sxs-lookup"><span data-stu-id="c5051-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="c5051-134">第一条语句返回任务，并会导致文件处理启动。</span><span class="sxs-lookup"><span data-stu-id="c5051-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="c5051-135">具有 await 的第二条语句将使方法立即退出并返回一个不同的任务。</span><span class="sxs-lookup"><span data-stu-id="c5051-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="c5051-136">文件处理稍后完成后，执行将返回到 await 后面的语句中。</span><span class="sxs-lookup"><span data-stu-id="c5051-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="c5051-137">有关详细信息，请参阅  [异步程序中的控制流 (Visual Basic) ](control-flow-in-async-programs.md)。</span><span class="sxs-lookup"><span data-stu-id="c5051-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="c5051-138">读取文本</span><span class="sxs-lookup"><span data-stu-id="c5051-138">Reading Text</span></span>  

 <span data-ttu-id="c5051-139">下面的示例读取文件中的文本。</span><span class="sxs-lookup"><span data-stu-id="c5051-139">The following example reads text from a file.</span></span> <span data-ttu-id="c5051-140">将会缓冲文本，并且在此情况下，会将其放入 <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="c5051-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="c5051-141">与前一示例不同，await 的计算将生成一个值。</span><span class="sxs-lookup"><span data-stu-id="c5051-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="c5051-142"><xref:System.IO.Stream.ReadAsync%2A> 方法返回 <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>，因此在操作完成后 await 的评估会得出 `Int32` 值 (`numRead`)。</span><span class="sxs-lookup"><span data-stu-id="c5051-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="c5051-143">有关详细信息，请参阅 [异步返回类型 (Visual Basic) ](async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c5051-143">For more information, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="c5051-144">并行异步 I/O</span><span class="sxs-lookup"><span data-stu-id="c5051-144">Parallel Asynchronous I/O</span></span>  

 <span data-ttu-id="c5051-145">下面的示例通过编写 10 个文本文件来演示并行处理。</span><span class="sxs-lookup"><span data-stu-id="c5051-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="c5051-146">对于每个文件，<xref:System.IO.Stream.WriteAsync%2A> 方法将返回一个任务，此任务随后将添加到任务列表中。</span><span class="sxs-lookup"><span data-stu-id="c5051-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="c5051-147">`Await Task.WhenAll(tasks)` 语句将退出该方法，并在所有任务的文件处理完成时在此方法中继续。</span><span class="sxs-lookup"><span data-stu-id="c5051-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="c5051-148">该示例将在任务完成后关闭 `Finally` 块中的所有 <xref:System.IO.FileStream> 实例。</span><span class="sxs-lookup"><span data-stu-id="c5051-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="c5051-149">如果每个 `FileStream` 均已在 `Imports` 语句中创建，则可能在任务完成前释放 `FileStream`。</span><span class="sxs-lookup"><span data-stu-id="c5051-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="c5051-150">请注意，性能提升几乎完全来自并行处理而不是异步处理。</span><span class="sxs-lookup"><span data-stu-id="c5051-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="c5051-151">异步的优点在于它不会占用多个线程，也不会占用用户界面线程。</span><span class="sxs-lookup"><span data-stu-id="c5051-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="c5051-152">当使用 <xref:System.IO.Stream.WriteAsync%2A> 和 <xref:System.IO.Stream.ReadAsync%2A> 方法时，可以指定可用于取消操作中间流的 <xref:System.Threading.CancellationToken>。</span><span class="sxs-lookup"><span data-stu-id="c5051-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="c5051-153">有关详细信息，请参阅[在托管线程中](../../../../standard/threading/cancellation-in-managed-threads.md) [ (Visual Basic) 和取消来微调异步应用程序](fine-tuning-your-async-application.md)。</span><span class="sxs-lookup"><span data-stu-id="c5051-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5051-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="c5051-154">See also</span></span>

- [<span data-ttu-id="c5051-155">使用 Async 和 Await 的异步编程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5051-155">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="c5051-156">异步返回类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5051-156">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="c5051-157">异步程序中的控制流 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5051-157">Control Flow in Async Programs (Visual Basic)</span></span>](control-flow-in-async-programs.md)
