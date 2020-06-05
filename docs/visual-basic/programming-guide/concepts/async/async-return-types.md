---
title: 异步返回类型
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 5d19fc9831580412da24333be0885fce55384658
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396709"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="dd3b7-102">异步返回类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd3b7-102">Async Return Types (Visual Basic)</span></span>

<span data-ttu-id="dd3b7-103">异步方法具有三个可能的返回类型：<xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.Task>和 void。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="dd3b7-104">在 Visual Basic 中，void 返回类型被写为 [Sub](../../language-features/procedures/sub-procedures.md) 过程。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-104">In Visual Basic, the void return type is written as a [Sub](../../language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="dd3b7-105">有关异步方法的详细信息，请参阅[采用 async 和 Await 的异步编程（Visual Basic）](index.md)。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="dd3b7-106">在以下其中一节检查每个返回类型，且在本主题末尾可以找到使用全部三种类型的完整示例。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>

> [!NOTE]
> <span data-ttu-id="dd3b7-107">若要运行该示例，计算机上必须安装 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="taskt-return-type"></a><a name="BKMK_TaskTReturnType"></a><span data-ttu-id="dd3b7-108">Task(T) 返回类型</span><span class="sxs-lookup"><span data-stu-id="dd3b7-108">Task(T) Return Type</span></span>

<span data-ttu-id="dd3b7-109"><xref:System.Threading.Tasks.Task%601>返回类型用于包含操作数具有类型的[return](../../../language-reference/statements/return-statement.md)语句的异步方法 `TResult` 。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>

<span data-ttu-id="dd3b7-110">在下面的示例中，`TaskOfT_MethodAsync` 异步方法包含返回整数的 return 语句。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="dd3b7-111">因此，该方法声明必须指定 `Task(Of Integer)` 的返回类型。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>

```vb
' TASK(OF T) EXAMPLE
Async Function TaskOfT_MethodAsync() As Task(Of Integer)

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.FromResult is a placeholder for actual work that returns a string.
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

    ' The method then can process the result in some way.
    Dim leisureHours As Integer
    If today.First() = "S" Then
        leisureHours = 16
    Else
        leisureHours = 5
    End If

    ' Because the return statement specifies an operand of type Integer, the
    ' method must have a return type of Task(Of Integer).
    Return leisureHours
End Function
```

<span data-ttu-id="dd3b7-112">当 `TaskOfT_MethodAsync` 从 await 表达式中调用时，await 表达式将检索存储在由 `TaskOfT_MethodAsync` 返回的任务中的整数值（`leisureHours` 的值）。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="dd3b7-113">有关 await 表达式的详细信息，请参阅[Await 运算符](../../../language-reference/operators/await-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-113">For more information about await expressions, see [Await Operator](../../../language-reference/operators/await-operator.md).</span></span>

<span data-ttu-id="dd3b7-114">以下代码调用和等待方法 `TaskOfT_MethodAsync`。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="dd3b7-115">此结果分配给 `result1` 变量。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-115">The result is assigned to the `result1` variable.</span></span>

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

<span data-ttu-id="dd3b7-116">通过从应用程序 `Await` 中分离对 `TaskOfT_MethodAsync` 的调用，你可以更好地了解此操作，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="dd3b7-117">对非立即等待的方法 `TaskOfT_MethodAsync` 的调用返回 `Task(Of Integer)`，正如你从方法声明预料的一样。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="dd3b7-118">该任务指派给示例中的 `integerTask` 变量。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="dd3b7-119">因为 `integerTask` 是 <xref:System.Threading.Tasks.Task%601>，所以它包含类型 `TResult` 的 <xref:System.Threading.Tasks.Task%601.Result> 属性。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="dd3b7-120">在这种情况下，TResult 表示整数类型。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="dd3b7-121">`Await` 应用于 `integerTask`，await 表达式的计算结果为 `integerTask` 的 <xref:System.Threading.Tasks.Task%601.Result%2A> 属性内容。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="dd3b7-122">此值分配给 `result2` 变量。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-122">The value is assigned to the `result2` variable.</span></span>

> [!WARNING]
> <span data-ttu-id="dd3b7-123"><xref:System.Threading.Tasks.Task%601.Result%2A> 属性为阻止属性。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="dd3b7-124">如果你在其任务完成之前尝试访问它，当前处于活动状态的线程将被阻止，直到任务完成且值为可用。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="dd3b7-125">在大多数情况下，应通过使用 `Await` 访问此值，而不是直接访问属性。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

<span data-ttu-id="dd3b7-126">以下代码中的显示语句验证 `result1` 变量、`result2` 变量与 `Result` 属性的值是否相同。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="dd3b7-127">请记住，`Result` 属性是锁定属性，在其任务完成之前不应访问。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="task-return-type"></a><a name="BKMK_TaskReturnType"></a><span data-ttu-id="dd3b7-128">任务返回类型</span><span class="sxs-lookup"><span data-stu-id="dd3b7-128">Task Return Type</span></span>

<span data-ttu-id="dd3b7-129">不包含 return 语句或包含不返回操作数的 return 语句的异步方法通常具有返回类型 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="dd3b7-130">如果将这些方法编写为同步运行，则这些方法将是[Sub](../../language-features/procedures/sub-procedures.md)过程。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-130">Such methods would be [Sub](../../language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="dd3b7-131">如果在异步方法中使用 `Task` 返回类型，调用方法可以使用 `Await` 运算符暂停调用方的完成，直至被调用的异步方法结束。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>

<span data-ttu-id="dd3b7-132">在下面的示例中，异步方法 `Task_MethodAsync` 不包含 return 语句。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="dd3b7-133">因此，为此方法指定 `Task` 返回类型，这将启用 `Task_MethodAsync` 为等待。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="dd3b7-134">`Task` 类型的定义不包括存储返回值的 `Result` 属性。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>

```vb
' TASK EXAMPLE
Async Function Task_MethodAsync() As Task

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.Delay is a placeholder for actual work.
    Await Task.Delay(2000)
    textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

    ' This method has no return statement, so its return type is Task.
End Function
```

<span data-ttu-id="dd3b7-135">通过使用 await 语句而不是 await 表达式来调用和等待 `Task_MethodAsync`，类似于异步 `Sub` 或返回返回 void 的方法的调用语句。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="dd3b7-136">`Await`在此情况下，运算符的应用程序不会生成值。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>

<span data-ttu-id="dd3b7-137">以下代码调用和等待方法 `Task_MethodAsync`。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

<span data-ttu-id="dd3b7-138">如前面的示例所示 <xref:System.Threading.Tasks.Task%601> ，可以将对的调用与 `Task_MethodAsync` 运算符的应用分开 `Await` ，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="dd3b7-139">但是，请记住，`Task` 没有 `Result` 属性，并且当 await 运算符应用于 `Task` 时不产生值。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>

<span data-ttu-id="dd3b7-140">以下代码从等待 `Task_MethodAsync` 返回的任务中分离调用 `Task_MethodAsync`。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="void-return-type"></a><a name="BKMK_VoidReturnType"></a><span data-ttu-id="dd3b7-141">Void 返回类型</span><span class="sxs-lookup"><span data-stu-id="dd3b7-141">Void Return Type</span></span>

<span data-ttu-id="dd3b7-142">过程的主要用途 `Sub` 是在事件处理程序中，其中没有返回类型（在其他语言中称为 void 返回类型）。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="dd3b7-143">Void 返回还可用于替代返回 void 的方法，或者用于执行可分类为"发后不理"活动的方法。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="dd3b7-144">但是，你应尽可能地返回 `Task`，因为不能等待返回 void 的异步方法。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="dd3b7-145">这种方法的任何调用方必须能够继续完成，而无需等待调用的异步方法完成，并且调用方必须独立于异步方法生成的任何值或异常。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>

<span data-ttu-id="dd3b7-146">返回 void 的异步方法的调用方无法捕获从该方法引发的异常，且此类未经处理的异常可能会导致应用程序故障。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="dd3b7-147">如果返回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 的异步方法中出现异常，此异常将存储于返回的任务中，并在等待该任务时再次引发。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="dd3b7-148">因此，请确保可以产生异常的任何异步方法都具有返回类型 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>，并确保会等待对方法的调用。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>

<span data-ttu-id="dd3b7-149">若要详细了解如何在异步方法中捕获异常，请参阅 [Try...Catch...Finally 语句](../../../language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>

<span data-ttu-id="dd3b7-150">下面的代码定义了异步事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-150">The following code defines an async event handler.</span></span>

```vb
' SUB EXAMPLE
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

    textBox1.Clear()

    ' Start the process and await its completion. DriverAsync is a
    ' Task-returning async method.
    Await DriverAsync()

    ' Say goodbye.
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
End Sub
```

## <a name="complete-example"></a><a name="BKMK_Example"></a><span data-ttu-id="dd3b7-151">完整示例</span><span class="sxs-lookup"><span data-stu-id="dd3b7-151">Complete Example</span></span>

<span data-ttu-id="dd3b7-152">以下 Windows Presentation Foundation (WPF) 项目包含本主题中的代码示例。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>

 <span data-ttu-id="dd3b7-153">若要运行项目，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="dd3b7-153">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="dd3b7-154">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-154">Start Visual Studio.</span></span>

2. <span data-ttu-id="dd3b7-155">在菜单栏上，依次选择“文件”  、“新建”  、“项目”  。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="dd3b7-156">**“新建项目”** 对话框随即打开。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-156">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="dd3b7-157">在 "**已安装**的**模板**" 类别中，选择 " **Visual Basic**"，然后选择 " **Windows**"。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="dd3b7-158">从项目类型列表中，选择“WPF 应用程序”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-158">Choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="dd3b7-159">输入 `AsyncReturnTypes` 作为项目名称，然后选择“确定”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="dd3b7-160">新项目将出现在“解决方案资源管理器”  中。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-160">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="dd3b7-161">在 Visual Studio 代码编辑器中，选择 **“MainWindow.xaml”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="dd3b7-162">如果此选项卡不可见，则在“解决方案资源管理器”\*\*\*\* 中，打开 MainWindow.xaml 的快捷菜单，然后选择“打开”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>

6. <span data-ttu-id="dd3b7-163">在 MainWindow.xaml 的“XAML”\*\*\*\* 窗口中，将代码替换为下面的代码。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>

    ```vb
    <Window x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>

        </Grid>
    </Window>
    ```

     <span data-ttu-id="dd3b7-164">MainWindow.xaml 的“设计”\*\*\*\* 视图中将显示一个简单的窗口，其中包含一个文本框和一个按钮。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>

7. <span data-ttu-id="dd3b7-165">在**解决方案资源管理器**中，打开 mainwindow.xaml 的快捷菜单，然后选择 "**查看代码**"。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

8. <span data-ttu-id="dd3b7-166">将 MainWindow.xaml.vb 中的代码替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>

    ```vb
    Class MainWindow

        ' SUB EXAMPLE
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

            textBox1.Clear()

            ' Start the process and await its completion. DriverAsync is a
            ' Task-returning async method.
            Await DriverAsync()

            ' Say goodbye.
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
        End Sub

        Async Function DriverAsync() As Task

            ' Task(Of T)
            ' Call and await the Task(Of T)-returning async method in the same statement.
            Dim result1 As Integer = Await TaskOfT_MethodAsync()

            ' Call and await in separate statements.
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

            ' You can do other work that does not rely on resultTask before awaiting.
            textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

            Dim result2 As Integer = Await integerTask

            ' Display the values of the result1 variable, the result2 variable, and
            ' the resultTask.Result property.
            textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
            textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
            textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf

            ' Task
            ' Call and await the Task-returning async method in the same statement.
            Await Task_MethodAsync()

            ' Call and await in separate statements.
            Dim simpleTask As Task = Task_MethodAsync()

            ' You can do other work that does not rely on simpleTask before awaiting.
            textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

            Await simpleTask
        End Function

        ' TASK(OF T) EXAMPLE
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.FromResult is a placeholder for actual work that returns a string.
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

            ' The method then can process the result in some way.
            Dim leisureHours As Integer
            If today.First() = "S" Then
                leisureHours = 16
            Else
                leisureHours = 5
            End If

            ' Because the return statement specifies an operand of type Integer, the
            ' method must have a return type of Task(Of Integer).
            Return leisureHours
        End Function

        ' TASK EXAMPLE
        Async Function Task_MethodAsync() As Task

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.Delay is a placeholder for actual work.
            Await Task.Delay(2000)
            textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

            ' This method has no return statement, so its return type is Task.
        End Function

    End Class
    ```

9. <span data-ttu-id="dd3b7-167">按 F5 键运行程序，然后选择“启动”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="dd3b7-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="dd3b7-168">应显示以下输出：</span><span class="sxs-lookup"><span data-stu-id="dd3b7-168">The following output should appear:</span></span>

    ```console
    Application can continue working while the Task<T> runs. . . .

    Value of result1 variable:   5
    Value of result2 variable:   5
    Value of integerTask.Result: 5

    Sorry for the delay. . . .

    Application can continue working while the Task runs. . . .

    Sorry for the delay. . . .

    All done, exiting button-click event handler.
    ```

## <a name="see-also"></a><span data-ttu-id="dd3b7-169">请参阅</span><span class="sxs-lookup"><span data-stu-id="dd3b7-169">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="dd3b7-170">演练：使用 Async 和 Await 访问 Web (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd3b7-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="dd3b7-171">异步程序中的控制流 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd3b7-171">Control Flow in Async Programs (Visual Basic)</span></span>](control-flow-in-async-programs.md)
- [<span data-ttu-id="dd3b7-172">异步</span><span class="sxs-lookup"><span data-stu-id="dd3b7-172">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="dd3b7-173">Await 运算符</span><span class="sxs-lookup"><span data-stu-id="dd3b7-173">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
