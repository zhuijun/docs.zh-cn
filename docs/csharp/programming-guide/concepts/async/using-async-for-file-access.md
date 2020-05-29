---
title: 使用异步进行文件访问 (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 8e0a62c2263ed3fd11eb4accb54978ef439ac010
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396960"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="5f7ca-102">使用异步进行文件访问 (C#)</span><span class="sxs-lookup"><span data-stu-id="5f7ca-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="5f7ca-103">可使用异步功能访问文件。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-103">You can use the async feature to access files.</span></span> <span data-ttu-id="5f7ca-104">通过使用异步功能，你可以调用异步方法而无需使用回调，也不需要跨多个方法或 lambda 表达式来拆分代码。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="5f7ca-105">若要使同步代码异步，只需调用异步方法而非同步方法，并向代码中添加几个关键字。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="5f7ca-106">可能出于以下原因向文件访问调用中添加异步：</span><span class="sxs-lookup"><span data-stu-id="5f7ca-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="5f7ca-107">异步使 UI 应用程序响应速度更快，因为启动该操作的 UI 线程可以执行其他操作。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="5f7ca-108">如果 UI 线程必须执行耗时较长的代码（例如超过 50 毫秒），UI 可能会冻结，直到 I/O 完成，此时 UI 线程可以再次处理键盘和鼠标输入及其他事件。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="5f7ca-109">异步可减少对线程的需要，进而提高 ASP.NET 和其他基于服务器的应用程序的可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="5f7ca-110">如果应用程序对每次响应都使用专用线程，同时处理 1000 个请求时，则需要 1000 个线程。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="5f7ca-111">异步操作在等待期间通常不需要使用线程。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="5f7ca-112">异步操作仅需在结束时短暂使用现有 I/O 完成线程。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="5f7ca-113">当前条件下，文件访问操作的延迟可能非常低，但以后可能大幅增加。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="5f7ca-114">例如，文件可能会移动到覆盖全球的服务器。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="5f7ca-115">使用异步功能所增加的开销很小。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-115">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="5f7ca-116">异步任务可以轻松地并行运行。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="5f7ca-117">运行示例</span><span class="sxs-lookup"><span data-stu-id="5f7ca-117">Running the Examples</span></span>  
 <span data-ttu-id="5f7ca-118">若要运行本主题中的示例，可创建“WPF 应用程序”或“Windows 窗体应用程序”，然后添加一个“按钮”。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="5f7ca-119">在按钮的 `Click` 事件中，添加对每个示例的第一个方法的调用。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="5f7ca-120">在下面的示例中，包括以下 `using` 指令。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-120">In the following examples, include the following `using` directives.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="5f7ca-121">使用 FileStream 类</span><span class="sxs-lookup"><span data-stu-id="5f7ca-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="5f7ca-122">本主题中的示例使用 <xref:System.IO.FileStream> 类，该类包含可导致在操作系统级别出现异步 I/O 的选项。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="5f7ca-123">使用此选项可避免在许多情况下阻止 ThreadPool 线程。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="5f7ca-124">若要启用此选项，可在构造函数调用中指定 `useAsync=true` 或 `options=FileOptions.Asynchronous` 参数。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="5f7ca-125">如果通过指定文件路径直接打开 <xref:System.IO.StreamReader> 和 <xref:System.IO.StreamWriter>，则无法将此选项与这二者配合使用。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="5f7ca-126">但是，如果为二者提供已由 <xref:System.IO.FileStream> 类打开的 <xref:System.IO.Stream>，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="5f7ca-127">请注意，即使 ThreadPool 线程受到阻止，UI 应用中的异步调用仍然更快，因为 UI 线程在等待期间不会受到阻止。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="5f7ca-128">编写文本</span><span class="sxs-lookup"><span data-stu-id="5f7ca-128">Writing Text</span></span>  
 <span data-ttu-id="5f7ca-129">下面的示例将文本写入文件。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-129">The following example writes text to a file.</span></span> <span data-ttu-id="5f7ca-130">在每个 await 语句中，该方法会立即退出。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="5f7ca-131">文件 I/O 完成后，该方法将在 await 语句后面的语句中继续。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="5f7ca-132">请注意，async 修饰符在使用 await 语句的方法的定义中。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async Task ProcessWriteAsync()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 <span data-ttu-id="5f7ca-133">原始示例包含 `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);` 语句，它是下面两个语句的缩写式：</span><span class="sxs-lookup"><span data-stu-id="5f7ca-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="5f7ca-134">第一条语句返回任务，并会导致文件处理启动。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="5f7ca-135">具有 await 的第二条语句将使方法立即退出并返回一个不同的任务。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="5f7ca-136">文件处理稍后完成后，执行将返回到 await 后面的语句中。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="5f7ca-137">有关详细信息，请参阅[异步程序中的控制流 (C#)](./control-flow-in-async-programs.md)。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-137">For more information, see  [Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="5f7ca-138">读取文本</span><span class="sxs-lookup"><span data-stu-id="5f7ca-138">Reading Text</span></span>  
 <span data-ttu-id="5f7ca-139">下面的示例读取文件中的文本。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-139">The following example reads text from a file.</span></span> <span data-ttu-id="5f7ca-140">将会缓冲文本，并且在此情况下，会将其放入 <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="5f7ca-141">与前一示例不同，await 的计算将生成一个值。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="5f7ca-142"><xref:System.IO.Stream.ReadAsync%2A> 方法返回 <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>，因此在操作完成后 await 的评估会得出 `Int32` 值 (`numRead`)。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="5f7ca-143">有关详细信息，请参阅[异步返回类型 (C#)](./async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-143">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>  
  
```csharp  
public async Task ProcessReadAsync()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="5f7ca-144">并行异步 I/O</span><span class="sxs-lookup"><span data-stu-id="5f7ca-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="5f7ca-145">下面的示例通过编写 10 个文本文件来演示并行处理。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="5f7ca-146">对于每个文件，<xref:System.IO.Stream.WriteAsync%2A> 方法将返回一个任务，此任务随后将添加到任务列表中。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="5f7ca-147">`await Task.WhenAll(tasks);` 语句将退出该方法，并在所有任务的文件处理完成时在此方法中继续。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="5f7ca-148">该示例将在任务完成后关闭 `finally` 块中的所有 <xref:System.IO.FileStream> 实例。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="5f7ca-149">如果每个 `FileStream` 均已在 `using` 语句中创建，则可能在任务完成前释放 `FileStream`。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="5f7ca-150">请注意，性能提升几乎完全来自并行处理而不是异步处理。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="5f7ca-151">异步的优点在于它不会占用多个线程，也不会占用用户界面线程。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async Task ProcessWriteMultAsync()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="5f7ca-152">当使用 <xref:System.IO.Stream.WriteAsync%2A> 和 <xref:System.IO.Stream.ReadAsync%2A> 方法时，可以指定可用于取消操作中间流的 <xref:System.Threading.CancellationToken>。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="5f7ca-153">有关详细信息，请参阅[微调异步应用程序 (C#)](./fine-tuning-your-async-application.md) 和 [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md)（托管线程中的取消）。</span><span class="sxs-lookup"><span data-stu-id="5f7ca-153">For more information, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f7ca-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f7ca-154">See also</span></span>

- [<span data-ttu-id="5f7ca-155">使用 Async 和 Await 的异步编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="5f7ca-155">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="5f7ca-156">异步返回类型 (C#)</span><span class="sxs-lookup"><span data-stu-id="5f7ca-156">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="5f7ca-157">异步程序中的控制流 (C#)</span><span class="sxs-lookup"><span data-stu-id="5f7ca-157">Control Flow in Async Programs (C#)</span></span>](./control-flow-in-async-programs.md)
