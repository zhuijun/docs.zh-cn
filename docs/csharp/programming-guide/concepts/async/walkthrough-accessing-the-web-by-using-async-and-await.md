---
title: 演练：使用 async 和 await 访问 Web (C#)
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: edc45f252b75c742afe4f073ca7dd92d9784d2c4
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240642"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="5ee00-102">演练：使用 async 和 await 访问 Web (C#)</span><span class="sxs-lookup"><span data-stu-id="5ee00-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>

<span data-ttu-id="5ee00-103">使用 async/await 功能可以更轻松直观地编写异步程序。</span><span class="sxs-lookup"><span data-stu-id="5ee00-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="5ee00-104">你可以编写类似于同步代码的异步代码，并让编译器处理异步代码通常需要的疑难回调函数和延续。</span><span class="sxs-lookup"><span data-stu-id="5ee00-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="5ee00-105">有关 Async 功能的详细信息，请参阅[使用 Async 和 Await 的异步编程 (C#)](./index.md)。</span><span class="sxs-lookup"><span data-stu-id="5ee00-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="5ee00-106">本演练从对网站列表中的字节数进行求和的同步 Windows Presentation Foundation (WPF) 应用程序入手，</span><span class="sxs-lookup"><span data-stu-id="5ee00-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="5ee00-107">然后使用新功能将该应用程序转换为异步解决方案。</span><span class="sxs-lookup"><span data-stu-id="5ee00-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="5ee00-108">如果不想自行生成应用，可以下载[异步示例：访问 Web 演练（C# 和 Visual Basic）](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)。</span><span class="sxs-lookup"><span data-stu-id="5ee00-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

> [!NOTE]
> <span data-ttu-id="5ee00-109">若要运行该示例，计算机上必须安装有 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="5ee00-109">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="5ee00-110">创建 WPF 应用程序</span><span class="sxs-lookup"><span data-stu-id="5ee00-110">Create a WPF application</span></span>

1. <span data-ttu-id="5ee00-111">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="5ee00-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="5ee00-112">在菜单栏上，依次选择“文件” > “新建” > “项目”。</span><span class="sxs-lookup"><span data-stu-id="5ee00-112">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="5ee00-113">**“新建项目”** 对话框随即打开。</span><span class="sxs-lookup"><span data-stu-id="5ee00-113">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="5ee00-114">在“已安装的模板”窗格中，选择“Visual C#”，然后从项目类型列表选择“WPF 应用程序”。</span><span class="sxs-lookup"><span data-stu-id="5ee00-114">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="5ee00-115">在“名称”文本框中，输入 `AsyncExampleWPF`，然后选择“确定”按钮。</span><span class="sxs-lookup"><span data-stu-id="5ee00-115">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="5ee00-116">新项目将出现在“解决方案资源管理器”中。</span><span class="sxs-lookup"><span data-stu-id="5ee00-116">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="5ee00-117">设计简单的 WPF MainWindow</span><span class="sxs-lookup"><span data-stu-id="5ee00-117">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="5ee00-118">在 Visual Studio 代码编辑器中，选择 **“MainWindow.xaml”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="5ee00-118">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="5ee00-119">如果“工具箱”窗口不可见，则打开“视图”菜单，然后选择“工具箱”  。</span><span class="sxs-lookup"><span data-stu-id="5ee00-119">If the **Toolbox** window isn't visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="5ee00-120">向“MainWindow”窗口添加一个“Button”控件和一个“TextBox”控件。</span><span class="sxs-lookup"><span data-stu-id="5ee00-120">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="5ee00-121">突出显示“TextBox”控件，在“属性”窗口中，设置下列值：</span><span class="sxs-lookup"><span data-stu-id="5ee00-121">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="5ee00-122">将“名称”属性设置为 `resultsTextBox`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-122">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="5ee00-123">将“高度”属性设置为 250。</span><span class="sxs-lookup"><span data-stu-id="5ee00-123">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="5ee00-124">将“宽度”属性设置为 500。</span><span class="sxs-lookup"><span data-stu-id="5ee00-124">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="5ee00-125">在“文本”选项卡中，指定等宽字体，例如 Lucida Console 或 Global Monospace。</span><span class="sxs-lookup"><span data-stu-id="5ee00-125">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="5ee00-126">突出显示“Button”控件，在“属性”窗口中，设置下列值：</span><span class="sxs-lookup"><span data-stu-id="5ee00-126">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="5ee00-127">将“名称”属性设置为 `startButton`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-127">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="5ee00-128">将“内容”属性的值从“Button”更改为“Start”。</span><span class="sxs-lookup"><span data-stu-id="5ee00-128">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="5ee00-129">确定文本框和按钮的位置，以便它们都在“MainWindow”窗口中显示。</span><span class="sxs-lookup"><span data-stu-id="5ee00-129">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

     <span data-ttu-id="5ee00-130">有关 WPF XAML 设计器的详细信息，请参阅[使用 XAML 设计器创建 UI](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="5ee00-130">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="5ee00-131">添加引用</span><span class="sxs-lookup"><span data-stu-id="5ee00-131">Add a reference</span></span>

1. <span data-ttu-id="5ee00-132">在“解决方案资源管理器”中，突出显示项目的名称。</span><span class="sxs-lookup"><span data-stu-id="5ee00-132">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="5ee00-133">在菜单栏上，选择“项目” > “添加引用”。</span><span class="sxs-lookup"><span data-stu-id="5ee00-133">On the menu bar, choose **Project** > **Add Reference**.</span></span>

     <span data-ttu-id="5ee00-134">此时将显示“引用管理器”对话框。</span><span class="sxs-lookup"><span data-stu-id="5ee00-134">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="5ee00-135">在对话框顶部，验证项目是否以 .NET Framework 4.5 或更高版本为目标。</span><span class="sxs-lookup"><span data-stu-id="5ee00-135">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="5ee00-136">在“程序集”类别中，选择“Framework”（如果尚未选择它） 。</span><span class="sxs-lookup"><span data-stu-id="5ee00-136">In the **Assemblies** category, choose **Framework** if it isn't already chosen.</span></span>

5. <span data-ttu-id="5ee00-137">在名称列表中，选中“System.Net.Http”复选框。</span><span class="sxs-lookup"><span data-stu-id="5ee00-137">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="5ee00-138">选择“确定”按钮关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="5ee00-138">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-using-directives"></a><span data-ttu-id="5ee00-139">添加必要的 using 指令</span><span class="sxs-lookup"><span data-stu-id="5ee00-139">Add necessary using directives</span></span>

1. <span data-ttu-id="5ee00-140">在“解决方案资源管理器”中，打开 MainWindow.xaml.cs 的快捷菜单，然后选择“查看代码”。</span><span class="sxs-lookup"><span data-stu-id="5ee00-140">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

2. <span data-ttu-id="5ee00-141">将下列 `using` 指令添加到代码文件的顶部（如果它们尚不存在）。</span><span class="sxs-lookup"><span data-stu-id="5ee00-141">Add the following `using` directives at the top of the code file if they're not already present.</span></span>

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a><span data-ttu-id="5ee00-142">创建同步应用</span><span class="sxs-lookup"><span data-stu-id="5ee00-142">Create a synchronous app</span></span>

1. <span data-ttu-id="5ee00-143">在设计窗口 MainWindow.xaml 中，双击“启动”按钮以在 MainWindow.xaml.cs 中创建 `startButton_Click` 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="5ee00-143">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="5ee00-144">在 MainWindow.xaml.cs 中，将下列代码复制到 `startButton_Click` 的正文中：</span><span class="sxs-lookup"><span data-stu-id="5ee00-144">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    <span data-ttu-id="5ee00-145">代码调用驱动应用程序 `SumPageSizes` 的方法，并在控件返回到 `startButton_Click` 时显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="5ee00-145">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="5ee00-146">该同步解决方案的代码包含以下四个方法：</span><span class="sxs-lookup"><span data-stu-id="5ee00-146">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="5ee00-147">`SumPageSizes`，从 `SetUpURLList` 获取网页 URL 列表并随后调用 `GetURLContents` 和 `DisplayResults` 以处理每个 URL。</span><span class="sxs-lookup"><span data-stu-id="5ee00-147">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="5ee00-148">`SetUpURLList`，生成并返回 Web 地址列表。</span><span class="sxs-lookup"><span data-stu-id="5ee00-148">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="5ee00-149">`GetURLContents`，下载每个网站的内容并将内容作为字节数组返回。</span><span class="sxs-lookup"><span data-stu-id="5ee00-149">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="5ee00-150">`DisplayResults`，显示每个 URL 的字节数组中的字节数。</span><span class="sxs-lookup"><span data-stu-id="5ee00-150">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="5ee00-151">复制以下四个方法，然后将它们粘贴在 MainWindow.xaml.cs 中的 `startButton_Click` 事件处理程序下：</span><span class="sxs-lookup"><span data-stu-id="5ee00-151">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>

    ```csharp
    private void SumPageSizes()
    {
        // Make a list of web addresses.
        List<string> urlList = SetUpURLList();

        var total = 0;
        foreach (var url in urlList)
        {
            // GetURLContents returns the contents of url as a byte array.
            byte[] urlContents = GetURLContents(url);

            DisplayResults(url, urlContents);

            // Update the total.
            total += urlContents.Length;
        }

        // Display the total count for all of the web addresses.
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
        {
            "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
            "https://msdn.microsoft.com",
            "https://msdn.microsoft.com/library/hh290136.aspx",
            "https://msdn.microsoft.com/library/ee256749.aspx",
            "https://msdn.microsoft.com/library/hh290138.aspx",
            "https://msdn.microsoft.com/library/hh290140.aspx",
            "https://msdn.microsoft.com/library/dd470362.aspx",
            "https://msdn.microsoft.com/library/aa578028.aspx",
            "https://msdn.microsoft.com/library/ms404677.aspx",
            "https://msdn.microsoft.com/library/ff730837.aspx"
        };
        return urls;
    }

    private byte[] GetURLContents(string url)
    {
        // The downloaded resource ends up in the variable named content.
        var content = new MemoryStream();

        // Initialize an HttpWebRequest for the current URL.
        var webReq = (HttpWebRequest)WebRequest.Create(url);

        // Send the request to the Internet resource and wait for
        // the response.
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        using (WebResponse response = webReq.GetResponse())
        {
            // Get the data stream that is associated with the specified URL.
            using (Stream responseStream = response.GetResponseStream())
            {
                // Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content);
            }
        }

        // Return the result as a byte array.
        return content.ToArray();
    }

    private void DisplayResults(string url, byte[] content)
    {
        // Display the length of each website. The string format
        // is designed to be used with a monospaced font, such as
        // Lucida Console or Global Monospace.
        var bytes = content.Length;
        // Strip off the "https://".
        var displayURL = url.Replace("https://", "");
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="5ee00-152">测试同步解决方案</span><span class="sxs-lookup"><span data-stu-id="5ee00-152">Test the synchronous solution</span></span>

<span data-ttu-id="5ee00-153">按 F5 键运行程序，然后选择“启动”按钮。</span><span class="sxs-lookup"><span data-stu-id="5ee00-153">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

<span data-ttu-id="5ee00-154">此时应显示类似于以下列表的输出：</span><span class="sxs-lookup"><span data-stu-id="5ee00-154">Output that resembles the following list should appear:</span></span>

```text
msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
msdn.microsoft.com                                            33964
msdn.microsoft.com/library/hh290136.aspx               225793
msdn.microsoft.com/library/ee256749.aspx               143577
msdn.microsoft.com/library/hh290138.aspx               237372
msdn.microsoft.com/library/hh290140.aspx               128279
msdn.microsoft.com/library/dd470362.aspx               157649
msdn.microsoft.com/library/aa578028.aspx               204457
msdn.microsoft.com/library/ms404677.aspx               176405
msdn.microsoft.com/library/ff730837.aspx               143474

Total bytes returned:  1834802

Control returned to startButton_Click.
```

<span data-ttu-id="5ee00-155">请注意，显示计数需要几秒钟时间。</span><span class="sxs-lookup"><span data-stu-id="5ee00-155">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="5ee00-156">与此同时，在等待请求的资源下载时，UI 线程处于被阻止状态。</span><span class="sxs-lookup"><span data-stu-id="5ee00-156">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="5ee00-157">因此，选择“启动”按钮后，将无法移动、最大化、最小化显示窗口，甚至也无法关闭显示窗口。</span><span class="sxs-lookup"><span data-stu-id="5ee00-157">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="5ee00-158">在字节计数开始显示之前，这些操作都会失败。</span><span class="sxs-lookup"><span data-stu-id="5ee00-158">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="5ee00-159">如果网站没有响应，将不会指示哪个网站失败。</span><span class="sxs-lookup"><span data-stu-id="5ee00-159">If a website isn't responding, you have no indication of which site failed.</span></span> <span data-ttu-id="5ee00-160">甚至停止等待和关闭程序也会很困难。</span><span class="sxs-lookup"><span data-stu-id="5ee00-160">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="5ee00-161">将 GetURLContents 转换为异步方法</span><span class="sxs-lookup"><span data-stu-id="5ee00-161">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="5ee00-162">要将同步解决方案转换为异步解决方案，最佳着手点在 `GetURLContents` 中，因为对 <xref:System.Net.HttpWebRequest> 方法 <xref:System.Net.HttpWebRequest.GetResponse%2A> 的调用以及对 <xref:System.IO.Stream> 方法 <xref:System.IO.Stream.CopyTo%2A> 的调用是应用程序访问 Web 的位置。</span><span class="sxs-lookup"><span data-stu-id="5ee00-162">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="5ee00-163">.NET Framework 提供两种方法的异步版本，使转换变得轻松。</span><span class="sxs-lookup"><span data-stu-id="5ee00-163">.NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

     <span data-ttu-id="5ee00-164">有关 `GetURLContents` 中使用的方法的详细信息，请参阅 <xref:System.Net.WebRequest>。</span><span class="sxs-lookup"><span data-stu-id="5ee00-164">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5ee00-165">在你按照本演练中的步骤进行操作的过程中，将出现多个编译器错误。</span><span class="sxs-lookup"><span data-stu-id="5ee00-165">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="5ee00-166">你可以忽略这些错误并继续演练。</span><span class="sxs-lookup"><span data-stu-id="5ee00-166">You can ignore them and continue with the walkthrough.</span></span>

     <span data-ttu-id="5ee00-167">将在 `GetURLContents` 的第三行中调用的方法从 `GetResponse` 更改为基于任务的异步 <xref:System.Net.WebRequest.GetResponseAsync%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5ee00-167">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. <span data-ttu-id="5ee00-168">`GetResponseAsync` 返回 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="5ee00-168">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="5ee00-169">在这种情况下，任务返回变量 `TResult` 具有类型 <xref:System.Net.WebResponse>。</span><span class="sxs-lookup"><span data-stu-id="5ee00-169">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="5ee00-170">该任务是在请求的任务已下载且任务已完成运行后，生成实际 `WebResponse` 对象的承诺。</span><span class="sxs-lookup"><span data-stu-id="5ee00-170">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

     <span data-ttu-id="5ee00-171">要从任务检索 `WebResponse` 值，请将 [await](../../../language-reference/operators/await.md) 运算符应用到对 `GetResponseAsync` 的调用，如下列代码所示。</span><span class="sxs-lookup"><span data-stu-id="5ee00-171">To retrieve the `WebResponse` value from the task, apply an [await](../../../language-reference/operators/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     <span data-ttu-id="5ee00-172">`await` 运算符将当前方法 `GetURLContents` 的执行挂起，直到完成等待的任务为止。</span><span class="sxs-lookup"><span data-stu-id="5ee00-172">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="5ee00-173">同时，控制权返回给当前方法的调用方。</span><span class="sxs-lookup"><span data-stu-id="5ee00-173">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="5ee00-174">在此示例中，当前方法是 `GetURLContents`，调用方是 `SumPageSizes`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-174">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="5ee00-175">任务完成时，承诺的 `WebResponse` 对象作为等待的任务的值生成，并分配给变量 `response`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-175">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

     <span data-ttu-id="5ee00-176">上一条语句可以分为以下两条语句，以阐明所发生的情况。</span><span class="sxs-lookup"><span data-stu-id="5ee00-176">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     <span data-ttu-id="5ee00-177">对 `webReq.GetResponseAsync` 的调用返回 `Task(Of WebResponse)` 或 `Task<WebResponse>`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-177">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="5ee00-178">然后，await 运算符将应用于任务以检索 `WebResponse` 值。</span><span class="sxs-lookup"><span data-stu-id="5ee00-178">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>

     <span data-ttu-id="5ee00-179">如果你的异步方法需要完成不依赖于任务的完成的工作，则在调用异步方法之后及应用 `await` 运算符之前的这段时间，该方法可以在这两个语句之间继续完成该工作。</span><span class="sxs-lookup"><span data-stu-id="5ee00-179">If your async method has work to do that doesn't depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="5ee00-180">有关示例，请参阅[如何使用 Async 和 Await 并行发起多个 Web 请求 (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) 和[如何使用 Task.WhenAll 扩展异步演练 (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。</span><span class="sxs-lookup"><span data-stu-id="5ee00-180">For examples, see [How to make multiple web requests in parallel by using async and await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="5ee00-181">因为在上一步中添加了 `await` 运算符，所以会发生编译器错误。</span><span class="sxs-lookup"><span data-stu-id="5ee00-181">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="5ee00-182">该运算符仅可在使用 [async](../../../language-reference/keywords/async.md) 修饰符标记的方法中使用。</span><span class="sxs-lookup"><span data-stu-id="5ee00-182">The operator can be used only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="5ee00-183">当你重复转换步骤以使用对 `CopyToAsync` 的调用替换对 `CopyTo` 的调用时，请忽略该错误。</span><span class="sxs-lookup"><span data-stu-id="5ee00-183">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="5ee00-184">更改被调用到 <xref:System.IO.Stream.CopyToAsync%2A> 的方法的名称。</span><span class="sxs-lookup"><span data-stu-id="5ee00-184">Change the name of the method that's called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="5ee00-185">`CopyTo` 或 `CopyToAsync` 方法复制字节到其参数 `content`，并且不返回有意义的值。</span><span class="sxs-lookup"><span data-stu-id="5ee00-185">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn't return a meaningful value.</span></span> <span data-ttu-id="5ee00-186">在同步版本中，对 `CopyTo` 的调用是不返回值的简单语句。</span><span class="sxs-lookup"><span data-stu-id="5ee00-186">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="5ee00-187">异步版本 `CopyToAsync` 返回 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="5ee00-187">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="5ee00-188">任务函数类似“Task(void)”，并让该方法能够等待。</span><span class="sxs-lookup"><span data-stu-id="5ee00-188">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="5ee00-189">应用 `Await` 或 `await` 到对 `CopyToAsync` 的调用，如下列代码所示。</span><span class="sxs-lookup"><span data-stu-id="5ee00-189">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         <span data-ttu-id="5ee00-190">上一条语句缩写以下两行代码。</span><span class="sxs-lookup"><span data-stu-id="5ee00-190">The previous statement abbreviates the following two lines of code.</span></span>

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. <span data-ttu-id="5ee00-191">`GetURLContents` 中仍需要完成的操作是调整方法签名。</span><span class="sxs-lookup"><span data-stu-id="5ee00-191">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="5ee00-192">仅可在使用 [async](../../../language-reference/keywords/async.md) 修饰符标记的方法中使用 `await` 运算符。</span><span class="sxs-lookup"><span data-stu-id="5ee00-192">You can use the `await` operator only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="5ee00-193">添加修饰符以将方法标记为*异步方法*，如下列代码所示。</span><span class="sxs-lookup"><span data-stu-id="5ee00-193">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. <span data-ttu-id="5ee00-194">异步方法的返回类型在 C# 中只能为 <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601> 或 `void`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-194">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="5ee00-195">通常情况下，`void` 的返回类型仅可在异步事件处理程序中使用，其中需要 `void`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-195">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="5ee00-196">在其他情况下，如果完成的方法具有返回 T 类型的值的 [return](../../../language-reference/keywords/return.md) 语句，则使用 `Task(T)`；如果完成的方法不返回有意义的值，则使用 `Task`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-196">In other cases, you use `Task(T)` if the completed method has a [return](../../../language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn't return a meaningful value.</span></span> <span data-ttu-id="5ee00-197">可以将 `Task` 返回类型视为表示“Task(void)”。</span><span class="sxs-lookup"><span data-stu-id="5ee00-197">You can think of the `Task` return type as meaning "Task(void)."</span></span>

     <span data-ttu-id="5ee00-198">有关详细信息，请参阅[异步返回类型 (C#)](./async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5ee00-198">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>

     <span data-ttu-id="5ee00-199">方法 `GetURLContents` 具有 return 语句，且该语句返回字节数组。</span><span class="sxs-lookup"><span data-stu-id="5ee00-199">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="5ee00-200">因此，异步版本的返回类型为 Task(T)，其中 T 为字节数组。</span><span class="sxs-lookup"><span data-stu-id="5ee00-200">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="5ee00-201">在方法签名中进行下列更改：</span><span class="sxs-lookup"><span data-stu-id="5ee00-201">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="5ee00-202">将返回类型更改为 `Task<byte[]>`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-202">Change the return type to `Task<byte[]>`.</span></span>

    - <span data-ttu-id="5ee00-203">按照约定，异步方法的名称以“Async”结尾，因此，请重命名方法 `GetURLContentsAsync`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-203">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

     <span data-ttu-id="5ee00-204">下列代码显示这些更改。</span><span class="sxs-lookup"><span data-stu-id="5ee00-204">The following code shows these changes.</span></span>

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     <span data-ttu-id="5ee00-205">进行这几处更改后，`GetURLContents` 到异步方法的转换完成。</span><span class="sxs-lookup"><span data-stu-id="5ee00-205">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="5ee00-206">将 SumPageSizes 转换为异步方法</span><span class="sxs-lookup"><span data-stu-id="5ee00-206">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="5ee00-207">为 `SumPageSizes` 重复之前过程中的步骤。</span><span class="sxs-lookup"><span data-stu-id="5ee00-207">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="5ee00-208">首先，将对 `GetURLContents` 的调用更改为异步调用。</span><span class="sxs-lookup"><span data-stu-id="5ee00-208">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="5ee00-209">将调用的方法的名称从 `GetURLContents` 更改为 `GetURLContentsAsync`（如果尚未执行此操作）。</span><span class="sxs-lookup"><span data-stu-id="5ee00-209">Change the name of the method that's called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="5ee00-210">将 `await` 应用到 `GetURLContentsAsync` 返回的任务，以便获取字节数组值。</span><span class="sxs-lookup"><span data-stu-id="5ee00-210">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

     <span data-ttu-id="5ee00-211">下列代码显示这些更改。</span><span class="sxs-lookup"><span data-stu-id="5ee00-211">The following code shows these changes.</span></span>

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     <span data-ttu-id="5ee00-212">上一个分配缩写以下两行代码。</span><span class="sxs-lookup"><span data-stu-id="5ee00-212">The previous assignment abbreviates the following two lines of code.</span></span>

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. <span data-ttu-id="5ee00-213">在方法签名中进行下列更改：</span><span class="sxs-lookup"><span data-stu-id="5ee00-213">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="5ee00-214">使用 `async` 修饰符标记方法。</span><span class="sxs-lookup"><span data-stu-id="5ee00-214">Mark the method with the `async` modifier.</span></span>

    - <span data-ttu-id="5ee00-215">将“Async”添加到方法名称。</span><span class="sxs-lookup"><span data-stu-id="5ee00-215">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="5ee00-216">这一次没有任务返回变量 T，因为 `SumPageSizesAsync` 不返回 T 的值。（该方法没有 `return` 语句。）但是，该方法必须返回 `Task` 才能进行等待。</span><span class="sxs-lookup"><span data-stu-id="5ee00-216">There is no task return variable, T, this time because `SumPageSizesAsync` doesn't return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="5ee00-217">因此，将该方法的返回类型从 `void` 更改为 `Task`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-217">Therefore, change the return type of the method from `void` to `Task`.</span></span>

    <span data-ttu-id="5ee00-218">下列代码显示这些更改。</span><span class="sxs-lookup"><span data-stu-id="5ee00-218">The following code shows these changes.</span></span>

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     <span data-ttu-id="5ee00-219">从 `SumPageSizes` 到 `SumPageSizesAsync` 的转换完成。</span><span class="sxs-lookup"><span data-stu-id="5ee00-219">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="5ee00-220">将 startButton_Click 转换为异步方法</span><span class="sxs-lookup"><span data-stu-id="5ee00-220">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="5ee00-221">在事件处理程序中，将调用的方法的名称从 `SumPageSizes` 更改为 `SumPageSizesAsync`（如果尚未执行此操作）。</span><span class="sxs-lookup"><span data-stu-id="5ee00-221">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven't already done so.</span></span>

2. <span data-ttu-id="5ee00-222">由于 `SumPageSizesAsync` 是异步方法，请更改事件处理程序中的代码以等待结果。</span><span class="sxs-lookup"><span data-stu-id="5ee00-222">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

     <span data-ttu-id="5ee00-223">对 `SumPageSizesAsync` 的调用反射对 `GetURLContentsAsync` 中的 `CopyToAsync` 的调用。</span><span class="sxs-lookup"><span data-stu-id="5ee00-223">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="5ee00-224">调用返回的是 `Task`，而不是 `Task(T)`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-224">The call returns a `Task`, not a `Task(T)`.</span></span>

     <span data-ttu-id="5ee00-225">与之前的过程一样，你可以使用一条语句或两条语句转换调用。</span><span class="sxs-lookup"><span data-stu-id="5ee00-225">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="5ee00-226">下列代码显示这些更改。</span><span class="sxs-lookup"><span data-stu-id="5ee00-226">The following code shows these changes.</span></span>

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. <span data-ttu-id="5ee00-227">要防止意外重新进入操作，请在 `startButton_Click` 顶部添加下列语句，以禁用“启动”按钮。</span><span class="sxs-lookup"><span data-stu-id="5ee00-227">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     <span data-ttu-id="5ee00-228">可以重新启用事件处理程序末尾的按钮。</span><span class="sxs-lookup"><span data-stu-id="5ee00-228">You can reenable the button at the end of the event handler.</span></span>

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     <span data-ttu-id="5ee00-229">有关重新进入的详细信息，请参阅[处理异步应用中的重新进入 (C#)](./handling-reentrancy-in-async-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="5ee00-229">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](./handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="5ee00-230">最后，将 `async` 修饰符添加到声明，以便事件处理程序可以等待 `SumPagSizesAsync`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-230">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     <span data-ttu-id="5ee00-231">通常情况下，事件处理程序的名称不会更改。</span><span class="sxs-lookup"><span data-stu-id="5ee00-231">Typically, the names of event handlers aren't changed.</span></span> <span data-ttu-id="5ee00-232">返回类型没有更改为 `Task`，因为事件处理程序必须返回 `void`。</span><span class="sxs-lookup"><span data-stu-id="5ee00-232">The return type isn't changed to `Task` because event handlers must return `void`.</span></span>

     <span data-ttu-id="5ee00-233">项目从同步处理到异步处理的转换完成。</span><span class="sxs-lookup"><span data-stu-id="5ee00-233">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="5ee00-234">测试异步解决方案</span><span class="sxs-lookup"><span data-stu-id="5ee00-234">Test the asynchronous solution</span></span>

1. <span data-ttu-id="5ee00-235">按 F5 键运行程序，然后选择“启动”按钮。</span><span class="sxs-lookup"><span data-stu-id="5ee00-235">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="5ee00-236">此时应显示类似于同步解决方案的输出的输出。</span><span class="sxs-lookup"><span data-stu-id="5ee00-236">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="5ee00-237">但是，请注意下列差异。</span><span class="sxs-lookup"><span data-stu-id="5ee00-237">However, notice the following differences.</span></span>

    - <span data-ttu-id="5ee00-238">处理完成后，所有结果不会同时出现。</span><span class="sxs-lookup"><span data-stu-id="5ee00-238">The results don't all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="5ee00-239">例如，两个程序都在 `startButton_Click` 中包含一行可以清除文本框的代码。</span><span class="sxs-lookup"><span data-stu-id="5ee00-239">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="5ee00-240">目的在于，在一组结果显示后，第二次选择“启动”按钮时，可以清除运行之间的文本框。</span><span class="sxs-lookup"><span data-stu-id="5ee00-240">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="5ee00-241">在同步版本中，下载完成且 UI 线程可以自由完成其他工作时，文本框在计数第二次显示之前即被清除。</span><span class="sxs-lookup"><span data-stu-id="5ee00-241">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="5ee00-242">在异步版本中，选择“启动”按钮后立即清除文本框。</span><span class="sxs-lookup"><span data-stu-id="5ee00-242">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="5ee00-243">最重要的是，UI 线程在下载过程中未被阻止。</span><span class="sxs-lookup"><span data-stu-id="5ee00-243">Most importantly, the UI thread isn't blocked during the downloads.</span></span> <span data-ttu-id="5ee00-244">在 Web 资源下载、计数和显示期间，可以移动窗口或调整窗口大小。</span><span class="sxs-lookup"><span data-stu-id="5ee00-244">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="5ee00-245">如果其中一个网站速度缓慢或没有响应，则可以通过选择“关闭”按钮取消操作（右上角红色字段中的 x）。</span><span class="sxs-lookup"><span data-stu-id="5ee00-245">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-method-geturlcontentsasync-with-a-net-method"></a><span data-ttu-id="5ee00-246">使用 .NET 方法替换方法 GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="5ee00-246">Replace method GetURLContentsAsync with a .NET method</span></span>

1. <span data-ttu-id="5ee00-247">.NET Framework 4.5 及更高版本提供了许多可供使用的异步方法。</span><span class="sxs-lookup"><span data-stu-id="5ee00-247">.NET Framework 4.5 and later versions provide many async methods that you can use.</span></span> <span data-ttu-id="5ee00-248">其中一个是 <xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>，它可以执行本演练所需的操作。</span><span class="sxs-lookup"><span data-stu-id="5ee00-248">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="5ee00-249">你可以使用它来替代你在早前过程中创建的 `GetURLContentsAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="5ee00-249">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

     <span data-ttu-id="5ee00-250">第一步是在方法 `SumPageSizesAsync` 中创建 `HttpClient` 对象。</span><span class="sxs-lookup"><span data-stu-id="5ee00-250">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="5ee00-251">在方法的开头添加下列声明。</span><span class="sxs-lookup"><span data-stu-id="5ee00-251">Add the following declaration at the start of the method.</span></span>

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. <span data-ttu-id="5ee00-252">在 `SumPageSizesAsync,` 中，使用对 `HttpClient` 方法的调用替换对 `GetURLContentsAsync` 方法的调用。</span><span class="sxs-lookup"><span data-stu-id="5ee00-252">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. <span data-ttu-id="5ee00-253">删除或注释禁用你编写的 `GetURLContentsAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="5ee00-253">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="5ee00-254">按 F5 键运行程序，然后选择“启动”按钮。</span><span class="sxs-lookup"><span data-stu-id="5ee00-254">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="5ee00-255">此版本的项目的行为应与“测试异步解决方案”过程描述的行为匹配，且你的工作量应该更少。</span><span class="sxs-lookup"><span data-stu-id="5ee00-255">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example-code"></a><span data-ttu-id="5ee00-256">示例代码</span><span class="sxs-lookup"><span data-stu-id="5ee00-256">Example code</span></span>

<span data-ttu-id="5ee00-257">下列代码包含使用你编写的异步 `GetURLContentsAsync` 方法从同步解决方案转换为异步解决方案的完整示例。</span><span class="sxs-lookup"><span data-stu-id="5ee00-257">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="5ee00-258">请注意，它与原始同步解决方案十分类似。</span><span class="sxs-lookup"><span data-stu-id="5ee00-258">Notice that it strongly resembles the original, synchronous solution.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                byte[] urlContents = await GetURLContentsAsync(url);

                // The previous line abbreviates the following two assignment statements.

                // GetURLContentsAsync returns a Task<T>. At completion, the task
                // produces a byte array.
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }
            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())

            // The previous statement abbreviates the following two statements.

            //Task<WebResponse> responseTask = webReq.GetResponseAsync();
            //using (WebResponse response = await responseTask)
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    // Read the bytes in responseStream and copy them to content.
                    await responseStream.CopyToAsync(content);

                    // The previous statement abbreviates the following two statements.

                    // CopyToAsync returns a Task, not a Task<T>.
                    //Task copyTask = responseStream.CopyToAsync(content);

                    // When copyTask is completed, content contains a copy of
                    // responseStream.
                    //await copyTask;
                }
            }
            // Return the result as a byte array.
            return content.ToArray();
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

<span data-ttu-id="5ee00-259">下列代码包含使用 `HttpClient` 方法 `GetByteArrayAsync` 的解决方案的完整示例。</span><span class="sxs-lookup"><span data-stu-id="5ee00-259">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            // One-step async call.
            await SumPageSizesAsync();

            //// Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client =
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                // GetByteArrayAsync returns a task. At completion, the task
                // produces a byte array.
                byte[] urlContents = await client.GetByteArrayAsync(url);

                // The following two lines can replace the previous assignment statement.
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="5ee00-260">请参阅</span><span class="sxs-lookup"><span data-stu-id="5ee00-260">See also</span></span>

- <span data-ttu-id="5ee00-261">[异步示例：访问 Web 演练（C# 和 Visual Basic）](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="5ee00-261">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span></span>
- [<span data-ttu-id="5ee00-262">async</span><span class="sxs-lookup"><span data-stu-id="5ee00-262">async</span></span>](../../../language-reference/keywords/async.md)
- [<span data-ttu-id="5ee00-263">await</span><span class="sxs-lookup"><span data-stu-id="5ee00-263">await</span></span>](../../../language-reference/operators/await.md)
- [<span data-ttu-id="5ee00-264">使用 Async 和 Await 的异步编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="5ee00-264">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="5ee00-265">异步返回类型 (C#)</span><span class="sxs-lookup"><span data-stu-id="5ee00-265">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="5ee00-266">基于任务的异步编程 (TAP)</span><span class="sxs-lookup"><span data-stu-id="5ee00-266">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="5ee00-267">如何使用 Task.WhenAll 扩展异步演练 (C#)</span><span class="sxs-lookup"><span data-stu-id="5ee00-267">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="5ee00-268">如何使用 Async 和 Await 并行发出多个 Web 请求 (C#)</span><span class="sxs-lookup"><span data-stu-id="5ee00-268">How to make multiple web requests in parallel by using async and await (C#)</span></span>](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
