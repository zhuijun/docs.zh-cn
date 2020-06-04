---
title: 在完成一个异步任务后取消剩余任务
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: be716e98263c865adad3c197236467b2f48d7740
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396670"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="2f8b4-102">在完成一个异步任务后取消剩余任务 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f8b4-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>

<span data-ttu-id="2f8b4-103">通过结合使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 方法和 <xref:System.Threading.CancellationToken>，可在一个任务完成时取消所有剩余任务。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="2f8b4-104">`WhenAny` 方法采用任务集合中的一个参数。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="2f8b4-105">该方法启动所有任务，并返回单个任务。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="2f8b4-106">当集合中任意任务完成时，完成单个任务。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-106">The single task is complete when any task in the collection is complete.</span></span>

<span data-ttu-id="2f8b4-107">此示例演示如何结合使用取消标记与 `WhenAny` 保留任务集合中第一个要完成的任务，并取消剩余任务。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="2f8b4-108">每个任务都下载网站内容。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="2f8b4-109">本示例显示第一个完成的下载的内容长度，并取消其他下载。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>

> [!NOTE]
> <span data-ttu-id="2f8b4-110">若要运行该示例，计算机上必须安装有 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="2f8b4-111">下载示例</span><span class="sxs-lookup"><span data-stu-id="2f8b4-111">Downloading the Example</span></span>

<span data-ttu-id="2f8b4-112">若要下载完整的 Windows Presentation Foundation (WPF) 项目，请参阅 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序），然后遵循以下步骤。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="2f8b4-113">解压缩下载的文件，然后启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="2f8b4-114">在菜单栏上，依次选择 **“文件”** 、 **“打开”** 和 **“项目/解决方案”** 。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="2f8b4-115">在“打开项目”\*\*\*\* 对话框中，打开保存已解压的示例代码的文件夹，然后打开 AsyncFineTuningVB 的解决方案 (.sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="2f8b4-116">在“解决方案资源管理器”  中，打开“CancelAfterOneTask”  项目的快捷菜单，然后选择“设为启动项目”  。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="2f8b4-117">选择 F5 键运行该项目。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-117">Choose the F5 key to run the project.</span></span>

    <span data-ttu-id="2f8b4-118">选择 Ctrl+F5 键运行该项目，而不进行调试。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="2f8b4-119">运行程序若干次，以验证首先完成的下载是不同的。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-119">Run the program several times to verify that different downloads finish first.</span></span>

<span data-ttu-id="2f8b4-120">如果不想下载项目，可在本主题末尾处查看 MainWindow.xaml.vb 文件。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="2f8b4-121">生成示例</span><span class="sxs-lookup"><span data-stu-id="2f8b4-121">Building the Example</span></span>

<span data-ttu-id="2f8b4-122">本主题中的示例将添加到[取消异步任务或任务列表](cancel-an-async-task-or-a-list-of-tasks.md)中开发的项目，以取消任务列表。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="2f8b4-123">该示例使用相同的 UI，但未显示使用“取消”  按钮。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="2f8b4-124">若要自行生成示例，请按“下载示例”部分的说明逐步操作，选择“CancelAListOfTasks”  作为“启动项目”  。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="2f8b4-125">将此主题中的更改添加到该项目。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-125">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="2f8b4-126">在**CancelAListOfTasks**项目的 mainwindow.xaml 文件中，通过将每个网站的处理步骤从中的循环移动 `AccessTheWebAsync` 到下面的异步方法来启动转换。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>

```vb
' ***Bundle the processing steps for a website into one async method.
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

    ' GetAsync returns a Task(Of HttpResponseMessage).
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

    ' Retrieve the website contents from the HttpResponseMessage.
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

    Return urlContents.Length
End Function
```

<span data-ttu-id="2f8b4-127">在 `AccessTheWebAsync` 中，此示例使用查询、<xref:System.Linq.Enumerable.ToArray%2A> 方法和 `WhenAny` 方法创建并启动任务数组。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="2f8b4-128">将 `WhenAny` 应用到数组将返回单个任务，该任务在等待时对任务数组中首先完成的任务进行评估。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>

<span data-ttu-id="2f8b4-129">在 `AccessTheWebAsync` 中，进行下列更改。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="2f8b4-130">星号标记了代码文件中的更改。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-130">Asterisks mark the changes in the code file.</span></span>

1. <span data-ttu-id="2f8b4-131">注释禁止或删除循环。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-131">Comment out or delete the loop.</span></span>

2. <span data-ttu-id="2f8b4-132">创建一个查询，它在执行时将生成常规任务的集合。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="2f8b4-133">每次调用 `ProcessURLAsync` 均在 `TResult` 为整数时返回 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>

    ```vb
    ' ***Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. <span data-ttu-id="2f8b4-134">通过调用 `ToArray` 来执行查询并启动任务。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="2f8b4-135">下一步中应用 `WhenAny` 方法将在不使用 `ToArray` 的情况下执行查询并启动任务，但其他方法可能无法执行此操作。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="2f8b4-136">最安全的做法是显式强制执行查询。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-136">The safest practice is to force execution of the query explicitly.</span></span>

    ```vb
    ' ***Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="2f8b4-137">在任务集合上调用 `WhenAny`。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="2f8b4-138">`WhenAny` 返回 `Task(Of Task(Of Integer))` 或 `Task<Task<int>>`。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="2f8b4-139">也就是说，在等待时 `WhenAny` 将返回一个任务，它将评估单个的 `Task(Of Integer)` 或 `Task<int>`。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="2f8b4-140">该单个任务是集合中首先完成的任务。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="2f8b4-141">首先完成的任务被分配给 `firstFinishedTask`。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="2f8b4-142">`firstFinishedTask` 的类型为 <xref:System.Threading.Tasks.Task%601>，其中 `TResult` 是整数，这是因为它是 `ProcessURLAsync` 的返回类型。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>

    ```vb
    ' ***Call WhenAny and then await the result. The task that finishes
    ' first is assigned to firstFinishedTask.
    Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. <span data-ttu-id="2f8b4-143">在此示例中，你只对首先完成的任务感兴趣。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="2f8b4-144">因此，使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 取消剩余任务。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>

    ```vb
    ' ***Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. <span data-ttu-id="2f8b4-145">最后，等待 `firstFinishedTask` 检索下载内容的长度。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>

    ```vb
    Dim length = Await firstFinishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

<span data-ttu-id="2f8b4-146">运行程序若干次，以验证首先完成的下载是不同的。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-146">Run the program several times to verify that different downloads finish first.</span></span>

## <a name="complete-example"></a><span data-ttu-id="2f8b4-147">完整的示例</span><span class="sxs-lookup"><span data-stu-id="2f8b4-147">Complete Example</span></span>

<span data-ttu-id="2f8b4-148">下面的代码是该示例的完整 Mainwindow.xaml 或 MainWindow.xaml.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="2f8b4-149">对添加到此示例的元素进行了星号标记。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-149">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="2f8b4-150">请注意，必须为 <xref:System.Net.Http> 添加引用。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="2f8b4-151">可以从 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）下载这些项目。</span><span class="sxs-lookup"><span data-stu-id="2f8b4-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Download complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        '' Comment out or delete the loop.
        ''For Each url In urlList
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).
        ''    ' Argument ct carries the message if the Cancel button is chosen.
        ''    ' Note that the Cancel button can cancel all remaining downloads.
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ''    ' Retrieve the website contents from the HttpResponseMessage.
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ''    resultsTextBox.Text &=
        ''        vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        ''Next

        ' ***Create a query that, when executed, returns a collection of tasks.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client, ct)

        ' ***Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' ***Call WhenAny and then await the result. The task that finishes
        ' first is assigned to firstFinishedTask.
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)

        ' ***Cancel the rest of the downloads. You just want the first one.
        cts.Cancel()

        ' ***Await the first completed task and display the results
        ' Run the program several times to demonstrate that different
        ' websites can finish first.
        Dim length = Await firstFinishedTask
        resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    End Function

    ' ***Bundle the processing steps for a website into one async method.
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        Return urlContents.Length
    End Function

    ' Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Sample output:

' Length of the downloaded website:  158856

' Download complete.
```

## <a name="see-also"></a><span data-ttu-id="2f8b4-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f8b4-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="2f8b4-153">微调异步应用程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f8b4-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="2f8b4-154">使用 Async 和 Await 的异步编程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f8b4-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- <span data-ttu-id="2f8b4-155">[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）</span><span class="sxs-lookup"><span data-stu-id="2f8b4-155">[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)</span></span>
