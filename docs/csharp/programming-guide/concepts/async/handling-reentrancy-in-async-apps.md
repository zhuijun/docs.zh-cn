---
title: 处理异步应用中的重新进入 (C#)
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: e03e0f6ecd8e74dd8518f84ec03c76c1ef5b9ee6
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241807"
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="9a1c1-102">处理异步应用中的重新进入 (C#)</span><span class="sxs-lookup"><span data-stu-id="9a1c1-102">Handling Reentrancy in Async Apps (C#)</span></span>

<span data-ttu-id="9a1c1-103">在应用中包含异步代码时，应考虑并且可以阻止重新进入（指在异步操作完成之前重新进入它）。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="9a1c1-104">如果不识别并处理重新进入的可能性，则它可能会导致意外结果。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

<span data-ttu-id="9a1c1-105">**在本主题中**</span><span class="sxs-lookup"><span data-stu-id="9a1c1-105">**In this topic**</span></span>

- [<span data-ttu-id="9a1c1-106">识别重新进入</span><span class="sxs-lookup"><span data-stu-id="9a1c1-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)

- [<span data-ttu-id="9a1c1-107">处理重新进入</span><span class="sxs-lookup"><span data-stu-id="9a1c1-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)

  - [<span data-ttu-id="9a1c1-108">禁用“开始”按钮</span><span class="sxs-lookup"><span data-stu-id="9a1c1-108">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  - [<span data-ttu-id="9a1c1-109">取消和重启操作</span><span class="sxs-lookup"><span data-stu-id="9a1c1-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  - [<span data-ttu-id="9a1c1-110">运行多个操作并将输出排入队列</span><span class="sxs-lookup"><span data-stu-id="9a1c1-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

- [<span data-ttu-id="9a1c1-111">检查并运行示例应用</span><span class="sxs-lookup"><span data-stu-id="9a1c1-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)

> [!NOTE]
> <span data-ttu-id="9a1c1-112">若要运行该示例，计算机上必须安装 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-112">To run the example, you must have Visual Studio 2012 or newer and .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="9a1c1-113">传输层安全性 (TLS) 版本 1.2 现在是在应用开发中使用的最低版本。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-113">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="9a1c1-114">如果应用面向低于 4.7 的 .NET Framework 版本，请参阅以下文章，了解 [.NET Framework 传输层安全性 (TLS) 的最佳做法](../../../../framework/network-programming/tls.md)。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-114">If your app targets a .NET Framework version earlier than 4.7, refer to the following article for [Transport Layer Security (TLS) best practices with .NET Framework](../../../../framework/network-programming/tls.md).</span></span>

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="9a1c1-115">识别重新进入</span><span class="sxs-lookup"><span data-stu-id="9a1c1-115">Recognizing Reentrancy</span></span>

<span data-ttu-id="9a1c1-116">在本主题中的示例中，用户选择“开始”按钮以启动一个异步应用，该应用下载一系列网站并计算下载的总字节数。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-116">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="9a1c1-117">该示例的同步版本以相同方式进行响应（无论用户选择该按钮多少次），因为在第一次选择之后，UI 线程会忽略这些事件，直到应用完成运行。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-117">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="9a1c1-118">但是，在异步应用中，UI 线程会继续响应，你可能会在它完成之前重新进入异步操作。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-118">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="9a1c1-119">下面的示例显示用户仅选择“开始”按钮一次时的预期输出。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-119">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="9a1c1-120">下载网站的列表会出现，其中包含每个站点的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-120">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="9a1c1-121">总字节数会在结尾处显示。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-121">The total number of bytes appears at the end.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="9a1c1-122">但是，如果用户多次选择按钮，则会反复调用事件处理程序，并且每次都会重新进入下载进程。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-122">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="9a1c1-123">因此，会有多个异步操作同时运行，输出会使结果交错，而总字节数令人困惑。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-123">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
7. msdn.microsoft.com                                            42972
4. msdn.microsoft.com/library/hh290140.aspx               117152
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
7. msdn.microsoft.com                                            42972
5. msdn.microsoft.com/library/hh524395.aspx                68959
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="9a1c1-124">可以滚动到本主题末尾来评审生成此输出的代码。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-124">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="9a1c1-125">可以通过将解决方案下载到本地计算机，然后运行 WebsiteDownload 项目，或是通过使用本主题末尾的代码创建自己的项目，来体验该代码。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-125">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project.</span></span> <span data-ttu-id="9a1c1-126">有关详细信息和说明，请参阅[检查并运行示例应用](#BKMD_SettingUpTheExample)。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-126">For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="9a1c1-127">处理重新进入</span><span class="sxs-lookup"><span data-stu-id="9a1c1-127">Handling Reentrancy</span></span>

<span data-ttu-id="9a1c1-128">可以采用各种方式处理重新进入，具体取决于希望应用执行的操作。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-128">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="9a1c1-129">本主题展示了以下示例：</span><span class="sxs-lookup"><span data-stu-id="9a1c1-129">This topic presents the following examples:</span></span>

- [<span data-ttu-id="9a1c1-130">禁用“开始”按钮</span><span class="sxs-lookup"><span data-stu-id="9a1c1-130">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="9a1c1-131">在操作运行期间禁用“开始”按钮，以便用户无法中断它。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-131">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="9a1c1-132">取消和重启操作</span><span class="sxs-lookup"><span data-stu-id="9a1c1-132">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="9a1c1-133">当用户再次选择“开始”按钮时取消仍在运行的任何操作，然后让最近请求的操作继续运行。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-133">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="9a1c1-134">运行多个操作并将输出排入队列</span><span class="sxs-lookup"><span data-stu-id="9a1c1-134">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="9a1c1-135">允许所有请求的操作异步运行，但是会协调输出的显示，以便每个操作的结果按顺序一起显示。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-135">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="9a1c1-136">禁用“开始”按钮</span><span class="sxs-lookup"><span data-stu-id="9a1c1-136">Disable the Start Button</span></span>

<span data-ttu-id="9a1c1-137">可以通过在 `StartButton_Click` 事件处理程序顶部禁用“开始”按钮，在操作运行期间阻止该按钮。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-137">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="9a1c1-138">随后可以在操作完成时从 `finally` 块中重新启用中该按钮，以便用户可以再次运行应用。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-138">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="9a1c1-139">若要设置此方案，请对[检查并运行示例应用](#BKMD_SettingUpTheExample)中提供的基本代码进行以下更改。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-139">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="9a1c1-140">还可以从[异步示例：.NET 桌面应用中的重新进入](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)下载压缩文件。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-140">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="9a1c1-141">项目名是 DisableStartButton。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-141">The name of the project is DisableStartButton.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Text = "";

    // ***Disable the Start button until the downloads are complete.
    StartButton.IsEnabled = false;

    try
    {
        await AccessTheWebAsync();
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
    // ***Enable the Start button in case you want to run the program again.
    finally
    {
        StartButton.IsEnabled = true;
    }
}
```

<span data-ttu-id="9a1c1-142">由于进行了这些更改，所以该按钮在 `AccessTheWebAsync` 下载网站期间不会进行响应，因此无法重新进入该进程。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-142">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can't be reentered.</span></span>

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a><span data-ttu-id="9a1c1-143">取消和重启操作</span><span class="sxs-lookup"><span data-stu-id="9a1c1-143">Cancel and Restart the Operation</span></span>

<span data-ttu-id="9a1c1-144">可以使“开始”按钮保持活动状态而不是禁用该按钮，但是如果用户再次选择该按钮，则取消已在运行的操作，让最近开始的操作继续运行。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-144">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="9a1c1-145">有关取消的详细信息，请参阅[微调异步应用程序 (C#)](./fine-tuning-your-async-application.md)。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-145">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="9a1c1-146">若要设置此方案，请对[检查并运行示例应用](#BKMD_SettingUpTheExample)中提供的基本代码进行以下更改。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-146">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="9a1c1-147">还可以从[异步示例：.NET 桌面应用中的重新进入](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)下载压缩文件。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-147">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="9a1c1-148">项目名是 CancelAndRestart。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-148">The name of the project is CancelAndRestart.</span></span>

1. <span data-ttu-id="9a1c1-149">声明 <xref:System.Threading.CancellationTokenSource> 变量 `cts`，它处于所有方法的范围内。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-149">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that's in scope for all methods.</span></span>

    ```csharp
    public partial class MainWindow : Window   // Or class MainPage
    {
        // *** Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="9a1c1-150">在 `StartButton_Click` 中，确定操作是否已在进行。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-150">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="9a1c1-151">如果 `cts` 的值为 null，则没有任何操作处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-151">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="9a1c1-152">如果该值不为 null，则取消已在运行的操作。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-152">If the value isn't null, the operation that is already running is canceled.</span></span>

    ```csharp
    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }
    ```

3. <span data-ttu-id="9a1c1-153">将 `cts` 设置为表示当前进程的不同值。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-153">Set `cts` to a different value that represents the current process.</span></span>

    ```csharp
    // *** Now set cts to a new value that you can use to cancel the current process
    // if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;
    ```

4. <span data-ttu-id="9a1c1-154">在 `StartButton_Click` 末尾，当前进程完成，因此将 `cts` 的值重新设置为 null。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-154">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>

    ```csharp
    // *** When the process is complete, signal that another process can begin.
    if (cts == newCTS)
        cts = null;
    ```

<span data-ttu-id="9a1c1-155">以下代码显示了 `StartButton_Click` 中的所有更改。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-155">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="9a1c1-156">新增内容标有星号。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-156">The additions are marked with asterisks.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Clear();

    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }

    // *** Now set cts to cancel the current process if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;

    try
    {
        // ***Send cts.Token to carry the message if there is a cancellation request.
        await AccessTheWebAsync(cts.Token);

    }
    // *** Catch cancellations separately.
    catch (OperationCanceledException)
    {
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";
    }
    // *** When the process is complete, signal that another process can proceed.
    if (cts == newCTS)
        cts = null;
}
```

<span data-ttu-id="9a1c1-157">在 `AccessTheWebAsync` 中，进行下列更改。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-157">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="9a1c1-158">添加参数以从 `StartButton_Click` 接受取消标记。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-158">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="9a1c1-159">使用 <xref:System.Net.Http.HttpClient.GetAsync%2A> 方法下载网站，因为 `GetAsync` 接受 <xref:System.Threading.CancellationToken> 参数。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-159">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="9a1c1-160">调用 `DisplayResults` 以显示下载的每个网站的结果之前，检查 `ct` 以验证当前操作是否未取消。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-160">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn't been canceled.</span></span>

<span data-ttu-id="9a1c1-161">下面的代码演示了这些更改（使用星号标记）。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-161">The following code shows these changes, which are marked with asterisks.</span></span>

```csharp
// *** Provide a parameter for the CancellationToken from StartButton_Click.
async Task AccessTheWebAsync(CancellationToken ct)
{
    // Declare an HttpClient object.
    HttpClient client = new HttpClient();

    // Make a list of web addresses.
    List<string> urlList = SetUpURLList();

    var total = 0;
    var position = 0;

    foreach (var url in urlList)
    {
        // *** Use the HttpClient.GetAsync method because it accepts a
        // cancellation token.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // *** Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // *** Check for cancellations before displaying information about the
        // latest site.
        ct.ThrowIfCancellationRequested();

        DisplayResults(url, urlContents, ++position);

        // Update the total.
        total += urlContents.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

<span data-ttu-id="9a1c1-162">如果在此应用运行期间多次选择“开始”按钮，则它应生成类似于以下输出的结果。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-162">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               122505
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="9a1c1-163">若要消除部分列表，请对 `StartButton_Click` 中的第一行代码取消注释以在用户每次重新启动操作时清除文本框。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-163">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="9a1c1-164">运行多个操作并将输出排入队列</span><span class="sxs-lookup"><span data-stu-id="9a1c1-164">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="9a1c1-165">此第三个示例最复杂，因为应用会在用户每次选择“开始”按钮时启动另一个异步操作，并且所有操作都会运行到完成。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-165">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="9a1c1-166">所有请求的操作以异步方式从列表中下载网站，但是操作的输出会按顺序呈现。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-166">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="9a1c1-167">也就是说，实际下载活动是交错进行的（如[识别重新进入](#BKMK_RecognizingReentrancy)中的输出所示），但是每个组的结果列表会分开呈现。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-167">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="9a1c1-168">操作会共享一个全局 <xref:System.Threading.Tasks.Task> (`pendingWork`)，它用作显示进程的守卫。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-168">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="9a1c1-169">若要设置此方案，请对[检查并运行示例应用](#BKMD_SettingUpTheExample)中提供的基本代码进行以下更改。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-169">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="9a1c1-170">还可以从[异步示例：.NET 桌面应用中的重新进入](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)下载压缩文件。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-170">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="9a1c1-171">项目名是 QueueResults。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-171">The name of the project is QueueResults.</span></span>

<span data-ttu-id="9a1c1-172">下面的输出显示用户仅选择“开始”按钮一次时的结果。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-172">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="9a1c1-173">字母标签 A 指示结果来自首次选择“开始”按钮。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-173">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="9a1c1-174">编号显示下载目标列表中 URL 的顺序。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-174">The numbers show the order of the URLs in the list of download targets.</span></span>

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               209858
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71260
A-6. msdn.microsoft.com/library/ms404677.aspx               199186
A-7. msdn.microsoft.com                                            53266
A-8. msdn.microsoft.com/library/ff730837.aspx               148020

TOTAL bytes returned:  918876

#Group A is complete.
```

<span data-ttu-id="9a1c1-175">如果用户选择“开始”按钮三次，则应用会生成类似于以下各行的输出。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-175">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="9a1c1-176">以井号 (#) 开头的信息行会跟踪应用程序的进度。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-176">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               207089
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71259
A-6. msdn.microsoft.com/library/ms404677.aspx               199185

#Starting group B.
#Task assigned for group B.

A-7. msdn.microsoft.com                                            53266

#Starting group C.
#Task assigned for group C.

A-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916095

B-1. msdn.microsoft.com/library/hh191443.aspx                87389
B-2. msdn.microsoft.com/library/aa578028.aspx               207089
B-3. msdn.microsoft.com/library/jj155761.aspx                30870
B-4. msdn.microsoft.com/library/hh290140.aspx               119027
B-5. msdn.microsoft.com/library/hh524395.aspx                71260
B-6. msdn.microsoft.com/library/ms404677.aspx               199186

#Group A is complete.

B-7. msdn.microsoft.com                                            53266
B-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916097

C-1. msdn.microsoft.com/library/hh191443.aspx                87389
C-2. msdn.microsoft.com/library/aa578028.aspx               207089

#Group B is complete.

C-3. msdn.microsoft.com/library/jj155761.aspx                30870
C-4. msdn.microsoft.com/library/hh290140.aspx               119027
C-5. msdn.microsoft.com/library/hh524395.aspx                72765
C-6. msdn.microsoft.com/library/ms404677.aspx               199186
C-7. msdn.microsoft.com                                            56190
C-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  920526

#Group C is complete.
```

<span data-ttu-id="9a1c1-177">组 B 和 C 会在组 A 完成之前开始，但是每个组的输出会分开显示。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-177">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="9a1c1-178">组 A 的所有输出会首先显示，后跟组 B 的所有输出，再然后是组 C 的所有输出。应用会始终按顺序显示组，并且对于每个组，始终按 URL 在 URL 列表中的显示顺序来显示有关各个网站的信息。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-178">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="9a1c1-179">但是，无法预测下载实际发生的顺序。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-179">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="9a1c1-180">在多个组启动之后，它们生成的下载任务都处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-180">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="9a1c1-181">无法假定 A-1 会在 B-1 之前下载，并且无法假定 A-1 会在 A-2 之前下载。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-181">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="9a1c1-182">全局定义</span><span class="sxs-lookup"><span data-stu-id="9a1c1-182">Global Definitions</span></span>

<span data-ttu-id="9a1c1-183">示例代码包含所有方法都可见的以下两个全局声明。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-183">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```csharp
public partial class MainWindow : Window  // Class MainPage in Windows Store app.
{
    // ***Declare the following variables where all methods can access them.
    private Task pendingWork = null;
    private char group = (char)('A' - 1);
```

<span data-ttu-id="9a1c1-184">`Task` 变量 `pendingWork` 会监视显示进程并防止任何组中断另一个组的显示操作。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-184">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="9a1c1-185">字符变量 `group` 标记来自不同组的输出以验证结果是否按预期顺序出现。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-185">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="9a1c1-186">单击事件处理程序</span><span class="sxs-lookup"><span data-stu-id="9a1c1-186">The Click Event Handler</span></span>

<span data-ttu-id="9a1c1-187">事件处理程序 `StartButton_Click` 会在用户每次选择“开始”按钮时增加组号。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-187">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="9a1c1-188">随后处理程序会调用 `AccessTheWebAsync` 以运行下载操作。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-188">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // ***Verify that each group's results are displayed together, and that
    // the groups display in order, by marking each group with a letter.
    group = (char)(group + 1);
    ResultsTextBox.Text += $"\r\n\r\n#Starting group {group}.";

    try
    {
        // *** Pass the group value to AccessTheWebAsync.
        char finishedGroup = await AccessTheWebAsync(group);

        // The following line verifies a successful return from the download and
        // display procedures.
        ResultsTextBox.Text += $"\r\n\r\n#Group {finishedGroup} is complete.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
}
```

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="9a1c1-189">AccessTheWebAsync 方法</span><span class="sxs-lookup"><span data-stu-id="9a1c1-189">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="9a1c1-190">此示例将 `AccessTheWebAsync` 拆分为两个方法。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-190">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="9a1c1-191">第一个方法 `AccessTheWebAsync` 会为组启动所有下载任务并设置 `pendingWork` 以控制显示进程。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-191">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="9a1c1-192">该方法使用语言集成查询（LINQ 查询）和 <xref:System.Linq.Enumerable.ToArray%2A> 同时启动所有下载任务。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-192">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="9a1c1-193">`AccessTheWebAsync` 随后调用 `FinishOneGroupAsync` 以等待每个下载完成并显示其长度。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-193">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="9a1c1-194">`FinishOneGroupAsync` 会返回在 `AccessTheWebAsync` 中分配给 `pendingWork` 的任务。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-194">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="9a1c1-195">该值会在任务完成之前阻止另一个操作进行中断。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-195">That value prevents interruption by another operation before the task is complete.</span></span>

```csharp
private async Task<char> AccessTheWebAsync(char grp)
{
    HttpClient client = new HttpClient();

    // Make a list of the web addresses to download.
    List<string> urlList = SetUpURLList();

    // ***Kick off the downloads. The application of ToArray activates all the download tasks.
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();

    // ***Call the method that awaits the downloads and displays the results.
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);

    ResultsTextBox.Text += $"\r\n#Task assigned for group {grp}. Download tasks are active.\r\n";

    // ***This task is complete when a group has finished downloading and displaying.
    await pendingWork;

    // You can do other work here or just return.
    return grp;
}
```

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="9a1c1-196">FinishOneGroupAsync 方法</span><span class="sxs-lookup"><span data-stu-id="9a1c1-196">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="9a1c1-197">此方法会循环访问组中的下载任务（等待每个任务、显示下载网站的长度并将该长度添加到总和中）。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-197">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="9a1c1-198">`FinishOneGroupAsync` 中的第一个语句使用 `pendingWork` 确保进入方法不会干扰已在显示进程中或已在等待的操作。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-198">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="9a1c1-199">如果这类操作正在进行，则进入操作必须等待轮到它。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-199">If such an operation is in progress, the entering operation must wait its turn.</span></span>

```csharp
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)
{
    // ***Wait for the previous group to finish displaying results.
    if (pendingWork != null) await pendingWork;

    int total = 0;

    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.
    for (int i = 0; i < contentTasks.Length; i++)
    {
        // Await the download of a particular URL, and then display the URL and
        // its length.
        byte[] content = await contentTasks[i];
        DisplayResults(urls[i], content, i, grp);
        total += content.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

#### <a name="points-of-interest"></a><span data-ttu-id="9a1c1-200">兴趣点</span><span class="sxs-lookup"><span data-stu-id="9a1c1-200">Points of Interest</span></span>

<span data-ttu-id="9a1c1-201">输出中以井号 (#) 开头的信息行阐明了此示例的工作原理。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-201">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="9a1c1-202">输出演示以下模式。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-202">The output shows the following patterns.</span></span>

- <span data-ttu-id="9a1c1-203">一个组可以上一组显示其输出期间启动，但上一组的输出显示不会中断。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-203">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

    ```output
    #Starting group A.
    #Task assigned for group A. Download tasks are active.

    A-1. msdn.microsoft.com/library/hh191443.aspx                87389
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260

    #Starting group B.
    #Task assigned for group B. Download tasks are active.

    A-6. msdn.microsoft.com/library/ms404677.aspx               199186
    A-7. msdn.microsoft.com                                            53078
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915919

    B-1. msdn.microsoft.com/library/hh191443.aspx                87388
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870

    #Group A is complete.

    B-4. msdn.microsoft.com/library/hh290140.aspx               119027
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186
    B-7. msdn.microsoft.com                                            53078
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915908
    ```

- <span data-ttu-id="9a1c1-204">仅对于组 A（它首先启动），`pendingWork` 任务才在 `FinishOneGroupAsync` 启动时为 null。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-204">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="9a1c1-205">组 A 在它到达 `FinishOneGroupAsync` 时尚未完成 await 表达式。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-205">Group A hasn't yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="9a1c1-206">因此，控制权未返回给 `AccessTheWebAsync`，对 `pendingWork` 的第一个分配尚未发生。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-206">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="9a1c1-207">下面两行始终在输出中一起显示。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-207">The following two lines always appear together in the output.</span></span> <span data-ttu-id="9a1c1-208">该代码从不会在于 `StartButton_Click` 中启动组操作与将组的任务分配给 `pendingWork` 之间中断。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-208">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

    ```output
    #Starting group B.
    #Task assigned for group B. Download tasks are active.
    ```

    <span data-ttu-id="9a1c1-209">组进入 `StartButton_Click` 之后，操作在操作进入 `FinishOneGroupAsync` 之前不会完成 await 表达式。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-209">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="9a1c1-210">因此，没有其他操作可以在代码段期间获得控制权。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-210">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="9a1c1-211">检查并运行示例应用</span><span class="sxs-lookup"><span data-stu-id="9a1c1-211">Reviewing and Running the Example App</span></span>

<span data-ttu-id="9a1c1-212">若要更好地了解示例应用，可以下载它，自己生成或查看本主题末尾的代码，而无需实现应用。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-212">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="9a1c1-213">若要将示例作为 Windows Presentation Foundation (WPF) 桌面应用运行，计算机上必须安装有 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-213">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="9a1c1-214">下载应用</span><span class="sxs-lookup"><span data-stu-id="9a1c1-214">Downloading the App</span></span>

1. <span data-ttu-id="9a1c1-215">从[异步示例：.NET 桌面应用中的重新进入](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)下载压缩文件。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-215">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="9a1c1-216">解压缩下载的文件，然后启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-216">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="9a1c1-217">在菜单栏上，依次选择 **“文件”** 、 **“打开”** 和 **“项目/解决方案”** 。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-217">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="9a1c1-218">导航到保存解压缩的示例代码的文件夹，然后打开解决方案 (.sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-218">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="9a1c1-219">在“解决方案资源管理器”中，打开要运行的项目的快捷菜单，然后选择“设置为 StartUpProject”。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-219">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="9a1c1-220">选择 CTRL+F5 键以生成并运行项目。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-220">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a><span data-ttu-id="9a1c1-221">生成应用</span><span class="sxs-lookup"><span data-stu-id="9a1c1-221">Building the App</span></span>

<span data-ttu-id="9a1c1-222">以下部分提供用于将示例生成为 WPF 应用的代码。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-222">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="9a1c1-223">生成 WPF 应用程序</span><span class="sxs-lookup"><span data-stu-id="9a1c1-223">To build a WPF app</span></span>

1. <span data-ttu-id="9a1c1-224">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-224">Start Visual Studio.</span></span>

2. <span data-ttu-id="9a1c1-225">在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-225">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="9a1c1-226">**“新建项目”** 对话框随即打开。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-226">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="9a1c1-227">在“已安装的模板”窗格中，展开“Visual C#”，然后展开“Windows”。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-227">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="9a1c1-228">在项目类型列表中，选择“WPF 应用程序”。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-228">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="9a1c1-229">将项目命名为 `WebsiteDownloadWPF`，选择 .NET Framework 版本 4.6 或更高版本，然后单击“确定”按钮。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-229">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher, and then click the **OK** button.</span></span>

     <span data-ttu-id="9a1c1-230">新项目将出现在“解决方案资源管理器”中。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-230">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="9a1c1-231">在 Visual Studio 代码编辑器中，选择 **“MainWindow.xaml”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-231">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="9a1c1-232">如果此选项卡不可见，则在解决方案资源管理器 中，打开 MainWindow.xaml 的快捷菜单，然后选择“查看代码” 。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-232">If the tab isn't visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="9a1c1-233">在 MainWindow.xaml 的“XAML”视图中，将代码替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-233">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```csharp
    <Window x:Class="WebsiteDownloadWPF.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WebsiteDownloadWPF"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Width="517" Height="360">
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />
        </Grid>
    </Window>
    ```

     <span data-ttu-id="9a1c1-234">MainWindow.xaml 的“设计”视图中将显示一个简单的窗口，其中包含一个文本框和一个按钮。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-234">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="9a1c1-235">在“解决方案资源管理器”中，右键单击“引用”并选择“添加引用”  。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-235">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="9a1c1-236">如果尚未选择，请为 <xref:System.Net.Http> 添加引用。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-236">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="9a1c1-237">在“解决方案资源管理器”中，打开 MainWindow.xaml.cs 的快捷菜单，然后选择“查看代码”。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-237">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

10. <span data-ttu-id="9a1c1-238">在 MainWindow.xaml.cs 中，将代码替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-238">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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
    using System.Threading;

    namespace WebsiteDownloadWPF
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                System.Net.ServicePointManager.SecurityProtocol |= System.Net.SecurityProtocolType.Tls12;
                InitializeComponent();
            }

            private async void StartButton_Click(object sender, RoutedEventArgs e)
            {
                // This line is commented out to make the results clearer in the output.
                //ResultsTextBox.Text = "";

                try
                {
                    await AccessTheWebAsync();
                }
                catch (Exception)
                {
                    ResultsTextBox.Text += "\r\nDownloads failed.";
                }
            }

            private async Task AccessTheWebAsync()
            {
                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                // Make a list of web addresses.
                List<string> urlList = SetUpURLList();

                var total = 0;
                var position = 0;

                foreach (var url in urlList)
                {
                    // GetByteArrayAsync returns a task. At completion, the task
                    // produces a byte array.
                    byte[] urlContents = await client.GetByteArrayAsync(url);

                    DisplayResults(url, urlContents, ++position);

                    // Update the total.
                    total += urlContents.Length;
                }

                // Display the total count for all of the websites.
                ResultsTextBox.Text +=
                    $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
            }

            private List<string> SetUpURLList()
            {
                List<string> urls = new List<string>
                {
                    "https://msdn.microsoft.com/library/hh191443.aspx",
                    "https://msdn.microsoft.com/library/aa578028.aspx",
                    "https://msdn.microsoft.com/library/jj155761.aspx",
                    "https://msdn.microsoft.com/library/hh290140.aspx",
                    "https://msdn.microsoft.com/library/hh524395.aspx",
                    "https://msdn.microsoft.com/library/ms404677.aspx",
                    "https://msdn.microsoft.com",
                    "https://msdn.microsoft.com/library/ff730837.aspx"
                };
                return urls;
            }

            private void DisplayResults(string url, byte[] content, int pos)
            {
                // Display the length of each website. The string format is designed
                // to be used with a monospaced font, such as Lucida Console or
                // Global Monospace.

                // Strip off the "https://".
                var displayURL = url.Replace("https://", "");
                // Display position in the URL list, the URL, and the number of bytes.
                ResultsTextBox.Text += $"\n{pos}. {displayURL,-58} {content.Length,8}";
            }
        }
    }
    ```

11. <span data-ttu-id="9a1c1-239">选择 CTRL+F5 键以运行程序，然后多次选择“开始”按钮。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-239">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="9a1c1-240">从[禁用“开始”按钮](#BKMK_DisableTheStartButton)、[取消并重启操作](#BKMK_CancelAndRestart)或[运行多个操作并将输出排入队列](#BKMK_RunMultipleOperations)中进行更改以处理重新进入。</span><span class="sxs-lookup"><span data-stu-id="9a1c1-240">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a1c1-241">请参阅</span><span class="sxs-lookup"><span data-stu-id="9a1c1-241">See also</span></span>

- [<span data-ttu-id="9a1c1-242">演练：使用 Async 和 Await 访问 Web (C#)</span><span class="sxs-lookup"><span data-stu-id="9a1c1-242">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="9a1c1-243">使用 Async 和 Await 的异步编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="9a1c1-243">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
