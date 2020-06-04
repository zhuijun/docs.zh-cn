---
title: 一段时间后取消异步任务
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: 048d4c19d459905ea579ede96c69230e718d55aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396683"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a><span data-ttu-id="fa69f-102">在一段时间后取消异步任务 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa69f-102">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>

<span data-ttu-id="fa69f-103">如果不希望等待操作结束，可使用 <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> 方法在一段时间后取消异步操作。</span><span class="sxs-lookup"><span data-stu-id="fa69f-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="fa69f-104">此方法会计划取消未在 `CancelAfter` 表达式指定的时间段内完成的任何关联任务。</span><span class="sxs-lookup"><span data-stu-id="fa69f-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="fa69f-105">此示例添加到[取消异步任务或任务列表 (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) 中开发的代码，以下载网站列表并显示每个网站的内容长度。</span><span class="sxs-lookup"><span data-stu-id="fa69f-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="fa69f-106">若要运行示例，计算机上必须安装有 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本 。</span><span class="sxs-lookup"><span data-stu-id="fa69f-106">To run the examples, you must have Visual Studio 2012 or later and the .NET Framework 4.5 or later installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="fa69f-107">下载示例</span><span class="sxs-lookup"><span data-stu-id="fa69f-107">Downloading the Example</span></span>

<span data-ttu-id="fa69f-108">若要下载完整的 Windows Presentation Foundation (WPF) 项目，请参阅 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序），然后遵循以下步骤。</span><span class="sxs-lookup"><span data-stu-id="fa69f-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="fa69f-109">解压缩下载的文件，然后启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="fa69f-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="fa69f-110">在菜单栏上，依次选择 **“文件”** 、 **“打开”** 和 **“项目/解决方案”** 。</span><span class="sxs-lookup"><span data-stu-id="fa69f-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="fa69f-111">在“打开项目”\*\*\*\* 对话框中，打开保存已解压的示例代码的文件夹，然后打开 AsyncFineTuningVB 的解决方案 (.sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="fa69f-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="fa69f-112">在“解决方案资源管理器”  中，打开“CancelAfterTime”  项目的快捷菜单，然后选择“设为启动项目”  。</span><span class="sxs-lookup"><span data-stu-id="fa69f-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="fa69f-113">选择 F5 键运行该项目。</span><span class="sxs-lookup"><span data-stu-id="fa69f-113">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="fa69f-114">选择 Ctrl+F5 键运行该项目，而不进行调试。</span><span class="sxs-lookup"><span data-stu-id="fa69f-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="fa69f-115">多次运行程序以验证输出是否显示所有网站的输出、不显示网站的输出或显示某些网站的输出。</span><span class="sxs-lookup"><span data-stu-id="fa69f-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

 <span data-ttu-id="fa69f-116">如果不想下载项目，可在本主题末尾处查看 MainWindow.xaml.vb 文件。</span><span class="sxs-lookup"><span data-stu-id="fa69f-116">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="fa69f-117">生成示例</span><span class="sxs-lookup"><span data-stu-id="fa69f-117">Building the Example</span></span>

<span data-ttu-id="fa69f-118">本主题中的示例添加到[取消异步任务或任务列表 (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) 中开发的项目，以取消任务列表。</span><span class="sxs-lookup"><span data-stu-id="fa69f-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="fa69f-119">该示例使用相同的 UI，但未显示使用“取消”  按钮。</span><span class="sxs-lookup"><span data-stu-id="fa69f-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="fa69f-120">若要自行生成示例，请按“下载示例”部分的说明逐步操作，选择“CancelAListOfTasks”  作为“启动项目”  。</span><span class="sxs-lookup"><span data-stu-id="fa69f-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="fa69f-121">将此主题中的更改添加到该项目。</span><span class="sxs-lookup"><span data-stu-id="fa69f-121">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="fa69f-122">若要指定将任务标记为取消之前的最长时间，请将对 `CancelAfter` 的调用添加到 `startButton_Click`，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="fa69f-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="fa69f-123">新增内容标有星号。</span><span class="sxs-lookup"><span data-stu-id="fa69f-123">The addition is marked with asterisks.</span></span>

```vb
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

    ' Instantiate the CancellationTokenSource.
    cts = New CancellationTokenSource()

    resultsTextBox.Clear()

    Try
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        ' can adjust the time.)
        cts.CancelAfter(2500)

        Await AccessTheWebAsync(cts.Token)
        resultsTextBox.Text &= vbCrLf & "Downloads complete."

    Catch ex As OperationCanceledException
        resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

    Catch ex As Exception
        resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
    End Try

    ' Set the CancellationTokenSource to Nothing when the download is complete.
    cts = Nothing
End Sub
```

<span data-ttu-id="fa69f-124">多次运行程序以验证输出是否显示所有网站的输出、不显示网站的输出或显示某些网站的输出。</span><span class="sxs-lookup"><span data-stu-id="fa69f-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="fa69f-125">下面的输出是一个示例：</span><span class="sxs-lookup"><span data-stu-id="fa69f-125">The following output is a sample:</span></span>

```console
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="fa69f-126">完整示例</span><span class="sxs-lookup"><span data-stu-id="fa69f-126">Complete Example</span></span>

<span data-ttu-id="fa69f-127">下列代码是示例的 MainWindow.xaml.vb 文件的完整文本。</span><span class="sxs-lookup"><span data-stu-id="fa69f-127">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="fa69f-128">对添加到此示例的元素进行了星号标记。</span><span class="sxs-lookup"><span data-stu-id="fa69f-128">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="fa69f-129">请注意，必须为 <xref:System.Net.Http> 添加引用。</span><span class="sxs-lookup"><span data-stu-id="fa69f-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="fa69f-130">可以从 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）下载这些项目。</span><span class="sxs-lookup"><span data-stu-id="fa69f-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
            ' can adjust the time.)
            cts.CancelAfter(2500)

            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
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

        ' Process each element in the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
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

' Length of the downloaded string: 35990.

' Length of the downloaded string: 407399.

' Length of the downloaded string: 226091.

' Downloads canceled.
```

## <a name="see-also"></a><span data-ttu-id="fa69f-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa69f-131">See also</span></span>

- [<span data-ttu-id="fa69f-132">使用 Async 和 Await 的异步编程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa69f-132">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="fa69f-133">演练：使用 Async 和 Await 访问 Web (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa69f-133">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="fa69f-134">取消一个异步任务或一组任务 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa69f-134">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>](cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="fa69f-135">微调异步应用程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa69f-135">Fine-Tuning Your Async Application (Visual Basic)</span></span>](fine-tuning-your-async-application.md)
- <span data-ttu-id="fa69f-136">[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）</span><span class="sxs-lookup"><span data-stu-id="fa69f-136">[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)</span></span>
