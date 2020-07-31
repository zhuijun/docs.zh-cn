---
title: 取消一个异步任务或一组任务 (C#)
description: 使用这些示例添加一个按钮，用于在异步应用程序完成之前将其取消。 此 C# 应用程序下载一个或多个网站的内容。
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 21bdbc3bc7c3b752fab160429d71356fb87d9976
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925341"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="65118-104">取消异步任务或任务列表 (C#)</span><span class="sxs-lookup"><span data-stu-id="65118-104">Cancel an async task or a list of tasks (C#)</span></span>

<span data-ttu-id="65118-105">如果不想等待异步应用程序完成，可以设置一个按钮用来取消它。</span><span class="sxs-lookup"><span data-stu-id="65118-105">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="65118-106">通过遵循本主题中的示例，可以为下载一个或一组网站内容的应用程序添加一个取消按钮。</span><span class="sxs-lookup"><span data-stu-id="65118-106">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="65118-107">示例使用[微调异步应用程序 (C#)](./fine-tuning-your-async-application.md) 描述的 UI。</span><span class="sxs-lookup"><span data-stu-id="65118-107">The examples use the UI that [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="65118-108">若要运行该示例，计算机上必须安装有 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="65118-108">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="cancel-a-task"></a><span data-ttu-id="65118-109">取消任务</span><span class="sxs-lookup"><span data-stu-id="65118-109">Cancel a task</span></span>

<span data-ttu-id="65118-110">第一个示例将“取消”按钮与单个下载任务关联。</span><span class="sxs-lookup"><span data-stu-id="65118-110">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="65118-111">如果在应用程序下载内容时选择按钮，下载将取消。</span><span class="sxs-lookup"><span data-stu-id="65118-111">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="65118-112">下载示例</span><span class="sxs-lookup"><span data-stu-id="65118-112">Download the example</span></span>

<span data-ttu-id="65118-113">若要下载完整的 Windows Presentation Foundation (WPF) 项目，请参阅 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）。</span><span class="sxs-lookup"><span data-stu-id="65118-113">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="65118-114">解压缩下载的文件，然后启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="65118-114">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="65118-115">在菜单栏上，依次选择“文件” > “打开” > “项目/解决方案”。</span><span class="sxs-lookup"><span data-stu-id="65118-115">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="65118-116">在“打开项目”对话框中，打开保存已解压的示例代码的文件夹，然后打开 AsyncFineTuningCS 的解决方案 (.sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="65118-116">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="65118-117">在“解决方案资源管理器”中，打开 “CancelATask” 项目的快捷菜单，然后选择“设为启动项目”。</span><span class="sxs-lookup"><span data-stu-id="65118-117">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="65118-118">选择“F5”键以运行项目（或按 Ctrl+F5 以运行该项目，而无需调试它）。</span><span class="sxs-lookup"><span data-stu-id="65118-118">Choose the **F5** key to run the project (or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

> [!TIP]
> <span data-ttu-id="65118-119">如果不想下载项目，可在本主题末尾处查看 MainWindow.xaml.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="65118-119">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="65118-120">生成示例</span><span class="sxs-lookup"><span data-stu-id="65118-120">Build the example</span></span>
 <span data-ttu-id="65118-121">下列更改将“取消”按钮添加到下载网站的应用程序中。</span><span class="sxs-lookup"><span data-stu-id="65118-121">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="65118-122">如果不想下载或生成示例，则可在本主题末尾的“完整示例”部分查看最终产品。</span><span class="sxs-lookup"><span data-stu-id="65118-122">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="65118-123">星号标记了代码中的更改。</span><span class="sxs-lookup"><span data-stu-id="65118-123">Asterisks mark the changes in the code.</span></span>

 <span data-ttu-id="65118-124">要自行生成示例，请按“下载示例”部分的说明逐步操作，选择“StarterCode”而不是“CancelATask”作为“启动项目”。</span><span class="sxs-lookup"><span data-stu-id="65118-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

 <span data-ttu-id="65118-125">然后将下列更改添加到该项目的 MainWindow.xaml.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="65118-125">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>

1. <span data-ttu-id="65118-126">声明一个 `CancellationTokenSource` 变量 `cts`，它作用于所有访问它的方法。</span><span class="sxs-lookup"><span data-stu-id="65118-126">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="65118-127">为“取消”按钮添加以下事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="65118-127">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="65118-128">用户请求取消时，事件处理程序使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 方法通知 `cts`。</span><span class="sxs-lookup"><span data-stu-id="65118-128">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

    ```csharp
    // ***Add an event handler for the Cancel button.
    private void cancelButton_Click(object sender, RoutedEventArgs e)
    {
        if (cts != null)
        {
            cts.Cancel();
        }
    }
    ```

3. <span data-ttu-id="65118-129">为“启动”按钮 `startButton_Click` 在事件处理程序中进行下列更改。</span><span class="sxs-lookup"><span data-stu-id="65118-129">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    - <span data-ttu-id="65118-130">实例化 `CancellationTokenSource`、`cts`。</span><span class="sxs-lookup"><span data-stu-id="65118-130">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - <span data-ttu-id="65118-131">在 `AccessTheWebAsync` 调用中（该操作下载指定网站的内容），将 `cts` 的 <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> 属性作为参数发送。</span><span class="sxs-lookup"><span data-stu-id="65118-131">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="65118-132">如果请求取消，则 `Token` 属性传播消息。</span><span class="sxs-lookup"><span data-stu-id="65118-132">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="65118-133">如果用户选择取消下载操作，请添加显示消息的 catch 块。</span><span class="sxs-lookup"><span data-stu-id="65118-133">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="65118-134">下列代码显示这些更改。</span><span class="sxs-lookup"><span data-stu-id="65118-134">The following code shows the changes.</span></span>

        ```csharp
        try
        {
            // ***Send a token to carry the message if cancellation is requested.
            int contentLength = await AccessTheWebAsync(cts.Token);
            resultsTextBox.Text += $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }
        // *** If cancellation is requested, an OperationCanceledException results.
        catch (OperationCanceledException)
        {
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";
        }
        catch (Exception)
        {
            resultsTextBox.Text += "\r\nDownload failed.\r\n";
        }
        ```

4. <span data-ttu-id="65118-135">在 `AccessTheWebAsync` 中，使用 <xref:System.Net.Http.HttpClient> 类型中 `GetAsync` 方法的 <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> 重载来下载网站内容。</span><span class="sxs-lookup"><span data-stu-id="65118-135">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="65118-136">将 `ct`（`AccessTheWebAsync` 的 <xref:System.Threading.CancellationToken> 参数）作为第二个参数传递。</span><span class="sxs-lookup"><span data-stu-id="65118-136">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="65118-137">如果用户选择“取消”按钮，则令牌携带消息。</span><span class="sxs-lookup"><span data-stu-id="65118-137">The token carries the message if the user chooses the **Cancel** button.</span></span>

     <span data-ttu-id="65118-138">下列代码显示 `AccessTheWebAsync` 中的更改。</span><span class="sxs-lookup"><span data-stu-id="65118-138">The following code shows the changes in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Provide a parameter for the CancellationToken.
    async Task<int> AccessTheWebAsync(CancellationToken ct)
    {
        HttpClient client = new HttpClient();

        resultsTextBox.Text += "\r\nReady to download.\r\n";

        // You might need to slow things down to have a chance to cancel.
        await Task.Delay(250);

        // GetAsync returns a Task<HttpResponseMessage>.
        // ***The ct argument carries the message if the Cancel button is chosen.
        HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // The result of the method is the length of the downloaded website.
        return urlContents.Length;
    }
    ```

5. <span data-ttu-id="65118-139">如果不取消该程序，它将生成以下输出。</span><span class="sxs-lookup"><span data-stu-id="65118-139">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     <span data-ttu-id="65118-140">如果在程序完成下载内容前，选择“取消”按钮，则程序将生成以下输出。</span><span class="sxs-lookup"><span data-stu-id="65118-140">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><span data-ttu-id="65118-141">取消任务列表</span><span class="sxs-lookup"><span data-stu-id="65118-141">Cancel a list of tasks</span></span>

<span data-ttu-id="65118-142">通过将相同的 `CancellationTokenSource` 示例与每个任务关联，可以扩展先前的示例，从而取消多个任务。</span><span class="sxs-lookup"><span data-stu-id="65118-142">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="65118-143">如果选择“取消”按钮，则将取消所有尚未完成的任务。</span><span class="sxs-lookup"><span data-stu-id="65118-143">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="65118-144">下载示例</span><span class="sxs-lookup"><span data-stu-id="65118-144">Download the example</span></span>

<span data-ttu-id="65118-145">若要下载完整的 Windows Presentation Foundation (WPF) 项目，请参阅 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）。</span><span class="sxs-lookup"><span data-stu-id="65118-145">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="65118-146">解压缩下载的文件，然后启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="65118-146">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="65118-147">在菜单栏上，依次选择“文件” > “打开” > “项目/解决方案”。</span><span class="sxs-lookup"><span data-stu-id="65118-147">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="65118-148">在“打开项目”对话框中，打开保存已解压的示例代码的文件夹，然后打开 AsyncFineTuningCS 的解决方案 (.sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="65118-148">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="65118-149">在“解决方案资源管理器”中，打开 “CancelAListOfTasks” 项目的快捷菜单，然后选择“设为启动项目”。</span><span class="sxs-lookup"><span data-stu-id="65118-149">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="65118-150">按 F5 键运行此项目。</span><span class="sxs-lookup"><span data-stu-id="65118-150">Choose the **F5** key to run the project.</span></span>

     <span data-ttu-id="65118-151">选择 Ctrl+F5 键来运行此项目，而无需调试。</span><span class="sxs-lookup"><span data-stu-id="65118-151">Choose the **Ctrl**+**F5** keys to run the project without debugging it.</span></span>

<span data-ttu-id="65118-152">如果不想下载项目，可在本主题末尾处查看 MainWindow.xaml.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="65118-152">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="65118-153">生成示例</span><span class="sxs-lookup"><span data-stu-id="65118-153">Build the example</span></span>

<span data-ttu-id="65118-154">要自行扩展示例，请按“下载示例”部分的说明逐步操作，但要选择“CancelATask”作为“启动项目”。</span><span class="sxs-lookup"><span data-stu-id="65118-154">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="65118-155">向该项目添加下列更改。</span><span class="sxs-lookup"><span data-stu-id="65118-155">Add the following changes to that project.</span></span> <span data-ttu-id="65118-156">星号标记了程序中的更改。</span><span class="sxs-lookup"><span data-stu-id="65118-156">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="65118-157">添加一个方法，用于创建 Web 地址的列表。</span><span class="sxs-lookup"><span data-stu-id="65118-157">Add a method to create a list of web addresses.</span></span>

    ```csharp
    // ***Add a method that creates a list of web addresses.
    private List<string> SetUpURLList()
    {
        List<string> urls = new List<string>
        {
            "https://msdn.microsoft.com",
            "https://msdn.microsoft.com/library/hh290138.aspx",
            "https://msdn.microsoft.com/library/hh290140.aspx",
            "https://msdn.microsoft.com/library/dd470362.aspx",
            "https://msdn.microsoft.com/library/aa578028.aspx",
            "https://msdn.microsoft.com/library/ms404677.aspx",
            "https://msdn.microsoft.com/library/ff730837.aspx"
        };
        return urls;
    }
    ```

2. <span data-ttu-id="65118-158">在 `AccessTheWebAsync` 中调用方法。</span><span class="sxs-lookup"><span data-stu-id="65118-158">Call the method in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. <span data-ttu-id="65118-159">在 `AccessTheWebAsync` 中添加下列循环，用于处理列表中的每个 Web 地址。</span><span class="sxs-lookup"><span data-stu-id="65118-159">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

    ```csharp
    // ***Add a loop to process the list of web addresses.
    foreach (var url in urlList)
    {
        // GetAsync returns a Task<HttpResponseMessage>.
        // Argument ct carries the message if the Cancel button is chosen.
        // ***Note that the Cancel button can cancel all remaining downloads.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
    }
    ```

4. <span data-ttu-id="65118-160">由于 `AccessTheWebAsync` 显示了长度，因此该方法无需返回任何内容。</span><span class="sxs-lookup"><span data-stu-id="65118-160">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="65118-161">删除返回语句，并将方法的返回类型更改为 <xref:System.Threading.Tasks.Task>，而不是 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="65118-161">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     <span data-ttu-id="65118-162">使用语句而非表达式从 `startButton_Click` 调用方法。</span><span class="sxs-lookup"><span data-stu-id="65118-162">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. <span data-ttu-id="65118-163">如果不取消该程序，它将生成以下输出。</span><span class="sxs-lookup"><span data-stu-id="65118-163">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

     <span data-ttu-id="65118-164">如果在下载完成之前选择“取消”按钮，则输出将包含取消前已完成下载的长度。</span><span class="sxs-lookup"><span data-stu-id="65118-164">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><span data-ttu-id="65118-165">完成示例</span><span class="sxs-lookup"><span data-stu-id="65118-165">Complete examples</span></span>

<span data-ttu-id="65118-166">以下各部分包含每个前面示例的代码。</span><span class="sxs-lookup"><span data-stu-id="65118-166">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="65118-167">请注意，必须为 <xref:System.Net.Http> 添加引用。</span><span class="sxs-lookup"><span data-stu-id="65118-167">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="65118-168">可以从[异步示例：Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）下载这些项目。</span><span class="sxs-lookup"><span data-stu-id="65118-168">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="example---cancel-a-task"></a><span data-ttu-id="65118-169">示例 - 取消任务</span><span class="sxs-lookup"><span data-stu-id="65118-169">Example - Cancel a task</span></span>

<span data-ttu-id="65118-170">下列代码是取消单个任务示例的完整 MainWindow.xaml.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="65118-170">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>

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

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.

using System.Threading;
namespace CancelATask
{
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // ***Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Send a token to carry the message if cancellation is requested.
                int contentLength = await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }
            // *** If cancellation is requested, an OperationCanceledException results.
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownload failed.\r\n";
            }

            // ***Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // ***Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // ***Provide a parameter for the CancellationToken.
        async Task<int> AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            resultsTextBox.Text += "\r\nReady to download.\r\n";

            // You might need to slow things down to have a chance to cancel.
            await Task.Delay(250);

            // GetAsync returns a Task<HttpResponseMessage>.
            // ***The ct argument carries the message if the Cancel button is chosen.
            HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            // The result of the method is the length of the downloaded website.
            return urlContents.Length;
        }
    }

    // Output for a successful download:

    // Ready to download.

    // Length of the downloaded string: 158125.

    // Or, if you cancel:

    // Ready to download.

    // Download canceled.
}
```

### <a name="example---cancel-a-list-of-tasks"></a><span data-ttu-id="65118-171">示例 - 取消任务列表</span><span class="sxs-lookup"><span data-stu-id="65118-171">Example - Cancel a list of tasks</span></span>

<span data-ttu-id="65118-172">下列代码是取消任务列表示例的完整 MainWindow.xaml.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="65118-172">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>

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

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.
using System.Threading;

namespace CancelAListOfTasks
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                await AccessTheWebAsync(cts.Token);
                // ***Small change in the display lines.
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.";
            }

            // Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // Provide a parameter for the CancellationToken.
        // ***Change the return type to Task because the method has no return statement.
        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // ***Call SetUpURLList to make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Add a loop to process the list of web addresses.
            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // ***Note that the Cancel button can cancel all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        // ***Add a method that creates a list of web addresses.
        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Output if you do not choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Length of the downloaded string: 158124.

    //Length of the downloaded string: 204890.

    //Length of the downloaded string: 175488.

    //Length of the downloaded string: 145790.

    //Downloads complete.

    // Sample output if you choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="65118-173">请参阅</span><span class="sxs-lookup"><span data-stu-id="65118-173">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="65118-174">使用 Async 和 Await 的异步编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="65118-174">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="65118-175">微调异步应用程序 (C#)</span><span class="sxs-lookup"><span data-stu-id="65118-175">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="65118-176">异步示例：微调应用程序</span><span class="sxs-lookup"><span data-stu-id="65118-176">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
