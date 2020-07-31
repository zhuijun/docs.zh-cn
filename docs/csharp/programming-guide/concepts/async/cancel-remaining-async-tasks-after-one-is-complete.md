---
title: 在完成一个异步任务后取消剩余任务 (C#)
description: 在此示例中，当一个任务完成时，结合使用 Task.WhenAny 方法和 C# 中的 CancellationToken 来取消所有剩余任务。
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 6de60c8faa93752961e3703a042885a71972cc4a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925275"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="a1abd-103">在完成一个异步任务后取消剩余任务 (C#)</span><span class="sxs-lookup"><span data-stu-id="a1abd-103">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="a1abd-104">通过结合使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 方法和 <xref:System.Threading.CancellationToken>，可在一个任务完成时取消所有剩余任务。</span><span class="sxs-lookup"><span data-stu-id="a1abd-104">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="a1abd-105">`WhenAny` 方法采用任务集合中的一个参数。</span><span class="sxs-lookup"><span data-stu-id="a1abd-105">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="a1abd-106">该方法启动所有任务，并返回单个任务。</span><span class="sxs-lookup"><span data-stu-id="a1abd-106">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="a1abd-107">当集合中任意任务完成时，完成单个任务。</span><span class="sxs-lookup"><span data-stu-id="a1abd-107">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="a1abd-108">此示例演示如何结合使用取消标记与 `WhenAny` 保留任务集合中第一个要完成的任务，并取消剩余任务。</span><span class="sxs-lookup"><span data-stu-id="a1abd-108">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="a1abd-109">每个任务都下载网站内容。</span><span class="sxs-lookup"><span data-stu-id="a1abd-109">Each task downloads the contents of a website.</span></span> <span data-ttu-id="a1abd-110">本示例显示第一个完成的下载的内容长度，并取消其他下载。</span><span class="sxs-lookup"><span data-stu-id="a1abd-110">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1abd-111">若要运行该示例，计算机上必须安装有 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="a1abd-111">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="a1abd-112">下载示例</span><span class="sxs-lookup"><span data-stu-id="a1abd-112">Downloading the Example</span></span>  
 <span data-ttu-id="a1abd-113">若要下载完整的 Windows Presentation Foundation (WPF) 项目，请参阅 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）。</span><span class="sxs-lookup"><span data-stu-id="a1abd-113">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="a1abd-114">解压缩下载的文件，然后启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a1abd-114">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="a1abd-115">在菜单栏上，依次选择 **“文件”** 、 **“打开”** 和 **“项目/解决方案”** 。</span><span class="sxs-lookup"><span data-stu-id="a1abd-115">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="a1abd-116">在“打开项目”对话框中，打开保存已解压的示例代码的文件夹，然后打开 AsyncFineTuningCS 的解决方案 (.sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="a1abd-116">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4. <span data-ttu-id="a1abd-117">在“解决方案资源管理器”中，打开“CancelAfterOneTask”项目的快捷菜单，然后选择“设为启动项目”。</span><span class="sxs-lookup"><span data-stu-id="a1abd-117">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="a1abd-118">选择 F5 键运行该项目。</span><span class="sxs-lookup"><span data-stu-id="a1abd-118">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="a1abd-119">选择 Ctrl+F5 键运行该项目，而不进行调试。</span><span class="sxs-lookup"><span data-stu-id="a1abd-119">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="a1abd-120">运行程序若干次，以验证首先完成的下载是不同的。</span><span class="sxs-lookup"><span data-stu-id="a1abd-120">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="a1abd-121">如果不想下载项目，可在本主题末尾处查看 MainWindow.xaml.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="a1abd-121">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="a1abd-122">生成示例</span><span class="sxs-lookup"><span data-stu-id="a1abd-122">Building the Example</span></span>  
 <span data-ttu-id="a1abd-123">本主题中的示例添加到[取消异步任务或任务列表 (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)中开发的项目，以取消任务列表。</span><span class="sxs-lookup"><span data-stu-id="a1abd-123">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="a1abd-124">该示例使用相同的 UI，但未显示使用“取消”按钮。</span><span class="sxs-lookup"><span data-stu-id="a1abd-124">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="a1abd-125">若要自行生成示例，请按“下载示例”部分的说明逐步操作，选择“CancelAListOfTasks”作为“启动项目”。</span><span class="sxs-lookup"><span data-stu-id="a1abd-125">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="a1abd-126">将此主题中的更改添加到该项目。</span><span class="sxs-lookup"><span data-stu-id="a1abd-126">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="a1abd-127">在 **CancelAListOfTasks** 项目的 MainWindow.xaml.cs 文件中，通过将每个网站的处理步骤从 `AccessTheWebAsync` 中的循环移动至下列异步方法来启动转换。</span><span class="sxs-lookup"><span data-stu-id="a1abd-127">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
// ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="a1abd-128">在 `AccessTheWebAsync` 中，此示例使用查询、<xref:System.Linq.Enumerable.ToArray%2A> 方法和 `WhenAny` 方法创建并启动任务数组。</span><span class="sxs-lookup"><span data-stu-id="a1abd-128">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="a1abd-129">将 `WhenAny` 应用到数组将返回单个任务，该任务在等待时对任务数组中首先完成的任务进行评估。</span><span class="sxs-lookup"><span data-stu-id="a1abd-129">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="a1abd-130">在 `AccessTheWebAsync` 中，进行下列更改。</span><span class="sxs-lookup"><span data-stu-id="a1abd-130">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="a1abd-131">星号标记了代码文件中的更改。</span><span class="sxs-lookup"><span data-stu-id="a1abd-131">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="a1abd-132">注释禁止或删除循环。</span><span class="sxs-lookup"><span data-stu-id="a1abd-132">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="a1abd-133">创建一个查询，它在执行时将生成常规任务的集合。</span><span class="sxs-lookup"><span data-stu-id="a1abd-133">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="a1abd-134">每次调用 `ProcessURLAsync` 均在 `TResult` 为整数时返回 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="a1abd-134">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. <span data-ttu-id="a1abd-135">通过调用 `ToArray` 来执行查询并启动任务。</span><span class="sxs-lookup"><span data-stu-id="a1abd-135">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="a1abd-136">下一步中应用 `WhenAny` 方法将在不使用 `ToArray` 的情况下执行查询并启动任务，但其他方法可能无法执行此操作。</span><span class="sxs-lookup"><span data-stu-id="a1abd-136">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="a1abd-137">最安全的做法是显式强制执行查询。</span><span class="sxs-lookup"><span data-stu-id="a1abd-137">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="a1abd-138">在任务集合上调用 `WhenAny`。</span><span class="sxs-lookup"><span data-stu-id="a1abd-138">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="a1abd-139">`WhenAny` 返回 `Task(Of Task(Of Integer))` 或 `Task<Task<int>>`。</span><span class="sxs-lookup"><span data-stu-id="a1abd-139">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="a1abd-140">也就是说，在等待时 `WhenAny` 将返回一个任务，它将评估单个的 `Task(Of Integer)` 或 `Task<int>`。</span><span class="sxs-lookup"><span data-stu-id="a1abd-140">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="a1abd-141">该单个任务是集合中首先完成的任务。</span><span class="sxs-lookup"><span data-stu-id="a1abd-141">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="a1abd-142">首先完成的任务被分配给 `firstFinishedTask`。</span><span class="sxs-lookup"><span data-stu-id="a1abd-142">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="a1abd-143">`firstFinishedTask` 的类型为 <xref:System.Threading.Tasks.Task%601>，其中 `TResult` 是整数，这是因为它是 `ProcessURLAsync` 的返回类型。</span><span class="sxs-lookup"><span data-stu-id="a1abd-143">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. <span data-ttu-id="a1abd-144">在此示例中，你只对首先完成的任务感兴趣。</span><span class="sxs-lookup"><span data-stu-id="a1abd-144">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="a1abd-145">因此，使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 取消剩余任务。</span><span class="sxs-lookup"><span data-stu-id="a1abd-145">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. <span data-ttu-id="a1abd-146">最后，等待 `firstFinishedTask` 检索下载内容的长度。</span><span class="sxs-lookup"><span data-stu-id="a1abd-146">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="a1abd-147">运行程序若干次，以验证首先完成的下载是不同的。</span><span class="sxs-lookup"><span data-stu-id="a1abd-147">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="a1abd-148">完整的示例</span><span class="sxs-lookup"><span data-stu-id="a1abd-148">Complete Example</span></span>  
 <span data-ttu-id="a1abd-149">下列代码是示例的完整 MainWindow.xaml.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="a1abd-149">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="a1abd-150">对添加到此示例的元素进行了星号标记。</span><span class="sxs-lookup"><span data-stu-id="a1abd-150">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="a1abd-151">请注意，必须为 <xref:System.Net.Http> 添加引用。</span><span class="sxs-lookup"><span data-stu-id="a1abd-151">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="a1abd-152">可以从 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）下载这些项目。</span><span class="sxs-lookup"><span data-stu-id="a1abd-152">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterOneTask  
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
                resultsTextBox.Text += "\r\nDownload complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Comment out or delete the loop.  
            //foreach (var url in urlList)  
            //{  
            //    // GetAsync returns a Task<HttpResponseMessage>.
            //    // Argument ct carries the message if the Cancel button is chosen.
            //    // ***Note that the Cancel button can cancel all remaining downloads.  
            //    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            //    // Retrieve the website contents from the HttpResponseMessage.  
            //    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            //    resultsTextBox.Text +=  
            //        $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            //}  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURLAsync(url, client, ct);  
  
            // ***Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // ***Call WhenAny and then await the result. The task that finishes
            // first is assigned to firstFinishedTask.  
            Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
            // ***Cancel the rest of the downloads. You just want the first one.  
            cts.Cancel();  
  
            // ***Await the first completed task and display the results.
            // Run the program several times to demonstrate that different  
            // websites can finish first.  
            var length = await firstFinishedTask;  
            resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
        }  
  
        // ***Bundle the processing steps for a website into one async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
  
        // Add a method that creates a list of web addresses.  
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
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1abd-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="a1abd-153">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="a1abd-154">微调异步应用程序 (C#)</span><span class="sxs-lookup"><span data-stu-id="a1abd-154">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="a1abd-155">使用 Async 和 Await 的异步编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="a1abd-155">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="a1abd-156">异步示例：微调应用程序</span><span class="sxs-lookup"><span data-stu-id="a1abd-156">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
