---
title: 异步程序中的控制流
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 0c479b9dd2a691b1b353fac54ee3320a895b1c7f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396657"
---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="cb3b9-102">异步程序中的控制流 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb3b9-102">Control Flow in Async Programs (Visual Basic)</span></span>

<span data-ttu-id="cb3b9-103">可以使用 `Async` 和 `Await` 关键字更加轻松地编写和维护异步程序。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="cb3b9-104">但是，如果不了解程序的运行方式，结果可能会让你大吃一惊。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="cb3b9-105">此主题通过一个简单的异步程序跟踪控制流，以显示控制从一种方法移动到另一种方法的情况，以及每次所传输的信息。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

> [!NOTE]
> <span data-ttu-id="cb3b9-106">`Async` 和 `Await` 关键字是在 Visual Studio 2012 中引入的。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>

<span data-ttu-id="cb3b9-107">通常，可通过[Async](../../../language-reference/modifiers/async.md)修饰符标记包含异步代码的方法。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-107">In general, you mark methods that contain asynchronous code with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="cb3b9-108">在使用 async 修饰符标记的方法中，可以使用[Await （Visual Basic）](../../../language-reference/operators/await-operator.md)运算符来指定方法的暂停位置，以等待调用的异步进程完成。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="cb3b9-109">有关详细信息，请参阅[采用 Async 和 Await 的异步编程（Visual Basic）](index.md)。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="cb3b9-110">下面的示例使用异步方法以字符串的形式下载指定网站的内容，并显示该字符串的长度。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="cb3b9-111">此示例包含以下两种方法。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-111">The example contains the following two methods.</span></span>

- <span data-ttu-id="cb3b9-112">`startButton_Click`，它调用 `AccessTheWebAsync` 并显示结果。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="cb3b9-113">`AccessTheWebAsync`，它以字符串的形式下载网站的内容，并返回该字符串的长度。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="cb3b9-114">`AccessTheWebAsync` 使用异步 <xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 来下载内容。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="cb3b9-115">编号的显示行显示在整个程序的策略点处，以帮助你了解程序的运行方式和说明被标记的每个点处发生的情况。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="cb3b9-116">显示行标记为“1”到“6”。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="cb3b9-117">该标签表示程序到达这些代码行的顺序。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-117">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="cb3b9-118">下面的代码显示该程序的概要。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-118">The following code shows an outline of the program.</span></span>

```vb
Class MainWindow

    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

        ' ONE
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

        ' FOUR
        Dim contentLength As Integer = Await getLengthTask

        ' SIX
        ResultsTextBox.Text &=
            vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

    End Sub

    Async Function AccessTheWebAsync() As Task(Of Integer)

        ' TWO
        Dim client As HttpClient = New HttpClient()
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://msdn.microsoft.com")

        ' THREE
        Dim urlContents As String = Await getStringTask

        ' FIVE
        Return urlContents.Length
    End Function

End Class
```

<span data-ttu-id="cb3b9-119">每个标记位置（“1”到“6”）显示有关该程序的当前状态的信息。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="cb3b9-120">将生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="cb3b9-120">The following output is produced:</span></span>

```console
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a><span data-ttu-id="cb3b9-121">设置程序</span><span class="sxs-lookup"><span data-stu-id="cb3b9-121">Set Up the Program</span></span>

<span data-ttu-id="cb3b9-122">可以从 MSDN 下载本主题使用的代码，也可以自行生成该代码。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="cb3b9-123">若要运行该示例，必须在计算机上安装 Visual Studio 2012 或更高版本，并安装 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="cb3b9-124">下载程序</span><span class="sxs-lookup"><span data-stu-id="cb3b9-124">Download the Program</span></span>

<span data-ttu-id="cb3b9-125">可以从[异步示例：异步程序中的控制流](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)中下载此主题的应用程序。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="cb3b9-126">以下步骤将打开并运行该程序。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-126">The following steps open and run the program.</span></span>

1. <span data-ttu-id="cb3b9-127">解压缩下载的文件，然后启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-127">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="cb3b9-128">在菜单栏上，依次选择 **“文件”** 、 **“打开”** 和 **“项目/解决方案”** 。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="cb3b9-129">导航到保存已解压缩的示例代码的文件夹，打开解决方案 (.sln) 文件，然后选择 F5 键以生成并运行项目。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>

### <a name="build-the-program-yourself"></a><span data-ttu-id="cb3b9-130">您自行生成程序</span><span class="sxs-lookup"><span data-stu-id="cb3b9-130">Build the Program Yourself</span></span>

<span data-ttu-id="cb3b9-131">以下 Windows Presentation Foundation (WPF) 项目包含本主题的代码示例。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="cb3b9-132">若要运行项目，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="cb3b9-132">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="cb3b9-133">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-133">Start Visual Studio.</span></span>

2. <span data-ttu-id="cb3b9-134">在菜单栏上，依次选择“文件”  、“新建”  、“项目”  。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="cb3b9-135">**“新建项目”** 对话框随即打开。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-135">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="cb3b9-136">在 "**已安装的模板**" 窗格中选择 " **Visual Basic**"，然后从项目类型列表中选择 " **WPF 应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="cb3b9-137">输入 `AsyncTracer` 作为项目名称，然后选择“确定”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

    <span data-ttu-id="cb3b9-138">新项目将出现在“解决方案资源管理器”  中。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-138">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="cb3b9-139">在 Visual Studio 代码编辑器中，选择 **“MainWindow.xaml”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

    <span data-ttu-id="cb3b9-140">如果此选项卡不可见，则在“解决方案资源管理器”  中，打开 MainWindow.xaml 的快捷菜单，然后选择“查看代码”  。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="cb3b9-141">在 MainWindow.xaml 的“XAML”  视图中，将代码替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```vb
    <Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"
        Title="Control Flow Trace" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>

        </Grid>
    </Window>
    ```

    <span data-ttu-id="cb3b9-142">MainWindow.xaml 的“设计”  视图中将显示一个简单的窗口，其中包含一个文本框和一个按钮。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="cb3b9-143">对 <xref:System.Net.Http> 添加引用。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-143">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="cb3b9-144">在**解决方案资源管理器**中，打开 mainwindow.xaml 的快捷菜单，然后选择 "**查看代码**"。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

9. <span data-ttu-id="cb3b9-145">在 Mainwindow.xaml 中，将代码替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

    ```vb
    ' Add an Imports statement and a reference for System.Net.Http.
    Imports System.Net.Http

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

            ' The display lines in the example lead you through the control shifts.
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &
                "           Calling AccessTheWebAsync." & vbCrLf

            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is started." & vbCrLf &
                "           About to await getLengthTask -- no caller to return to." & vbCrLf

            Dim contentLength As Integer = Await getLengthTask

            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is finished." & vbCrLf &
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &
                "           About to display contentLength and exit." & vbCrLf

            ResultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)
        End Sub

        Async Function AccessTheWebAsync() As Task(Of Integer)

            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."

            ' Declare an HttpClient object.
            Dim client As HttpClient = New HttpClient()

            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf

            ' GetStringAsync returns a Task(Of String).
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &
                "           Task getStringTask is started."

            ' AccessTheWebAsync can continue to work until getStringTask is awaited.

            ResultsTextBox.Text &=
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf

            ' Retrieve the website contents when task is complete.
            Dim urlContents As String = Await getStringTask

            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &
                vbCrLf & "           Task getStringTask is complete." &
                vbCrLf & "           Processing the return statement." &
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf

            Return urlContents.Length
        End Function

    End Class
    ```

10. <span data-ttu-id="cb3b9-146">按 F5 键运行程序，然后选择“启动”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="cb3b9-147">应显示以下输出：</span><span class="sxs-lookup"><span data-stu-id="cb3b9-147">The following output should appear:</span></span>

    ```console
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a><span data-ttu-id="cb3b9-148">跟踪程序</span><span class="sxs-lookup"><span data-stu-id="cb3b9-148">Trace the Program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="cb3b9-149">步骤 1 和步骤 2</span><span class="sxs-lookup"><span data-stu-id="cb3b9-149">Steps ONE and TWO</span></span>

<span data-ttu-id="cb3b9-150">在 `startButton_Click` 调用 `AccessTheWebAsync` 及 `AccessTheWebAsync` 调用异步 <xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 时，前两个显示行会跟踪路径。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="cb3b9-151">下图概述了从方法到方法的调用。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-151">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="cb3b9-152">![步骤 1 和步骤 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="cb3b9-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="cb3b9-153">`AccessTheWebAsync` 和 `client.GetStringAsync` 的返回类型都是 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="cb3b9-154">对于 `AccessTheWebAsync`，TResult 是一个整数。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="cb3b9-155">对于 `GetStringAsync`，TResult 是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="cb3b9-156">有关异步方法返回类型的详细信息，请参阅[异步返回类型（Visual Basic）](async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-156">For more information about async method return types, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>

<span data-ttu-id="cb3b9-157">在控制切换回调用方时，任务返回异步方法将返回一个任务实例。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="cb3b9-158">在调用的方法中遇到 `Await` 运算符或在调用的方法结束时，控制会从异步方法返回其调用方。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="cb3b9-159">标记为“3”到“6”的显示行将跟踪过程的这一部分。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="cb3b9-160">步骤 3</span><span class="sxs-lookup"><span data-stu-id="cb3b9-160">Step THREE</span></span>

<span data-ttu-id="cb3b9-161">在 `AccessTheWebAsync` 中，调用异步方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 以下载目标网页的内容。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="cb3b9-162">返回 `client.GetStringAsync` 时，控制将从 `client.GetStringAsync` 返回到 `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

<span data-ttu-id="cb3b9-163">`client.GetStringAsync` 方法将返回分配给 `AccessTheWebAsync` 中的 `getStringTask` 变量的字符串任务。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="cb3b9-164">该示例程序中的以下行说明了对 `client.GetStringAsync` 的调用和赋值。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

<span data-ttu-id="cb3b9-165">可以将任务视为 `client.GetStringAsync` 的一个承诺，用于最终生成实际字符串。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="cb3b9-166">同时，如果 `AccessTheWebAsync` 有要执行的工作，且该工作不依赖于 `client.GetStringAsync` 中承诺的字符串，则可在 `client.GetStringAsync` 等待时继续此工作。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="cb3b9-167">在示例中，以下标记为“3”的输出行表示执行独立工作的机会</span><span class="sxs-lookup"><span data-stu-id="cb3b9-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```console
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="cb3b9-168">当 `getStringTask` 处于等待状态时，下面的语句将暂停 `AccessTheWebAsync` 中的进度。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```vb
Dim urlContents As String = Await getStringTask
```

<span data-ttu-id="cb3b9-169">下图显示了从 `client.GetStringAsync` 到的赋值 `getStringTask` 以及从创建 `getStringTask` 到 Await 运算符的应用程序的控制流。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>

<span data-ttu-id="cb3b9-170">![步骤3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-三")</span><span class="sxs-lookup"><span data-stu-id="cb3b9-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>

<span data-ttu-id="cb3b9-171">Await 表达式将暂停 `AccessTheWebAsync`，直到返回 `client.GetStringAsync`。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="cb3b9-172">同时，控件返回至 `AccessTheWebAsync` 的调用方 `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="cb3b9-173">通常情况下，应立即等待对异步方法的调用。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="cb3b9-174">例如，以下赋值可以替换前面创建的代码，然后等待 `getStringTask`：`Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="cb3b9-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span></span>
>
> <span data-ttu-id="cb3b9-175">在本主题中，稍后将应用 await 运算符，以容纳通过程序标记控制流的输出行。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="cb3b9-176">步骤 4</span><span class="sxs-lookup"><span data-stu-id="cb3b9-176">Step FOUR</span></span>

<span data-ttu-id="cb3b9-177">`AccessTheWebAsync` 的声明的返回类型是 `Task(Of Integer)`。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-177">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="cb3b9-178">因此，当 `AccessTheWebAsync` 处于挂起状态时，它会将整数任务返回到 `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="cb3b9-179">应该了解返回的任务不是 `getStringTask`。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="cb3b9-180">返回的任务是一个新的整数任务，它表示挂起的方法 `AccessTheWebAsync` 中仍需完成的任务。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="cb3b9-181">该任务是 `AccessTheWebAsync` 中的一个承诺，当任务完成时，将生成一个整数。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="cb3b9-182">下列语句将此任务分配给 `getLengthTask` 变量。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

<span data-ttu-id="cb3b9-183">如 `AccessTheWebAsync` 中一样，`startButton_Click` 可以继续执行不依赖于异步任务 (`getLengthTask`) 的结果的工作，直到该任务处于等待状态。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="cb3b9-184">以下输出行表示该工作：</span><span class="sxs-lookup"><span data-stu-id="cb3b9-184">The following output lines represent that work:</span></span>

```console
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

<span data-ttu-id="cb3b9-185">当 `getLengthTask` 处于等待状态时，`startButton_Click` 中的进度将挂起。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="cb3b9-186">下面的赋值语句将挂起 `startButton_Click`，直到完成 `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="cb3b9-187">下图中的箭头显示控制流，该控制流从 `AccessTheWebAsync` 中的 await 表达式到 `getLengthTask` 的赋值值，后跟 `startButton_Click` 中的正常处理，直到 `getLengthTask` 处于等待状态。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

<span data-ttu-id="cb3b9-188">![步骤4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-四")</span><span class="sxs-lookup"><span data-stu-id="cb3b9-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="cb3b9-189">步骤 5</span><span class="sxs-lookup"><span data-stu-id="cb3b9-189">Step FIVE</span></span>

<span data-ttu-id="cb3b9-190">当 `client.GetStringAsync` 指示它已完成时，`AccessTheWebAsync` 中的处理将从挂起状态释放，且可以继续通过 await 语句。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="cb3b9-191">下面的输出行表示处理的恢复：</span><span class="sxs-lookup"><span data-stu-id="cb3b9-191">The following lines of output represent the resumption of processing:</span></span>

```console
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

<span data-ttu-id="cb3b9-192">return 语句 `urlContents.Length` 的操作数存储于 `AccessTheWebAsync` 返回的任务中。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="cb3b9-193">Await 表达式从 `startButton_Click` 中的 `getLengthTask` 检索该值。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

<span data-ttu-id="cb3b9-194">下图显示了完成 `client.GetStringAsync`（和 `getStringTask`）后控制的转移。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

<span data-ttu-id="cb3b9-195">![步骤 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-五")</span><span class="sxs-lookup"><span data-stu-id="cb3b9-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

<span data-ttu-id="cb3b9-196">`AccessTheWebAsync` 将一直运行直到完成，且控制将返回到 `startButton_Click`，它正在等待完成。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="cb3b9-197">步骤 6</span><span class="sxs-lookup"><span data-stu-id="cb3b9-197">Step SIX</span></span>

<span data-ttu-id="cb3b9-198">当 `AccessTheWebAsync` 指示它已完成时，处理可以继续通过 `startButton_Async` 中的 await 语句。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="cb3b9-199">事实上，该程序没有更多可执行的操作。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-199">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="cb3b9-200">下面的输出行表示 `startButton_Async` 中处理的恢复：</span><span class="sxs-lookup"><span data-stu-id="cb3b9-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```console
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

<span data-ttu-id="cb3b9-201">Await 表达式从 `getLengthTask` 中检索为 `AccessTheWebAsync` 中 return 语句的操作数的整数值。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="cb3b9-202">下面的语句将该值赋给 `contentLength` 变量。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-202">The following statement assigns that value to the `contentLength` variable.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="cb3b9-203">下图显示从 `AccessTheWebAsync` 到 `startButton_Click` 的控制的返回。</span><span class="sxs-lookup"><span data-stu-id="cb3b9-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

<span data-ttu-id="cb3b9-204">![步骤 6](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-六")</span><span class="sxs-lookup"><span data-stu-id="cb3b9-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="cb3b9-205">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb3b9-205">See also</span></span>

- [<span data-ttu-id="cb3b9-206">使用 Async 和 Await 的异步编程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb3b9-206">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="cb3b9-207">异步返回类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb3b9-207">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="cb3b9-208">演练：使用 Async 和 Await 访问 Web (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb3b9-208">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- <span data-ttu-id="cb3b9-209">[Async Sample: Control Flow in Async Programs (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)（异步示例：异步程序中的控制流（C# 和 Visual Basic））</span><span class="sxs-lookup"><span data-stu-id="cb3b9-209">[Async Sample: Control Flow in Async Programs (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)</span></span>
