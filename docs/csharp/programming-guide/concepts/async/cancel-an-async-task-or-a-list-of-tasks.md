---
title: 取消任务列表 (C#)
description: 了解如何使用取消令牌向任务列表发出取消请求的信号。
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 84cd1bb413d20b6c13be8415c13c72b57873b1cf
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654700"
---
# <a name="cancel-a-list-of-tasks-c"></a><span data-ttu-id="638a6-103">取消任务列表 (C#)</span><span class="sxs-lookup"><span data-stu-id="638a6-103">Cancel a list of tasks (C#)</span></span>

<span data-ttu-id="638a6-104">如果不想等待异步控制台应用程序完成，可以取消该应用程序。</span><span class="sxs-lookup"><span data-stu-id="638a6-104">You can cancel an async console application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="638a6-105">通过遵循本主题中的示例，可将取消添加到下载网站内容的应用程序。</span><span class="sxs-lookup"><span data-stu-id="638a6-105">By following the example in this topic, you can add a cancellation to an application that downloads the contents of a list of websites.</span></span> <span data-ttu-id="638a6-106">可通过将 <xref:System.Threading.CancellationTokenSource> 实例与每个任务进行关联来取消多个任务。</span><span class="sxs-lookup"><span data-stu-id="638a6-106">You can cancel many tasks by associating the <xref:System.Threading.CancellationTokenSource> instance with each task.</span></span> <span data-ttu-id="638a6-107">如果选择 <kbd>Enter</kbd> 键，则将取消所有尚未完成的任务。</span><span class="sxs-lookup"><span data-stu-id="638a6-107">If you select the <kbd>Enter</kbd> key, you cancel all tasks that aren't yet complete.</span></span>

<span data-ttu-id="638a6-108">本教程涉及：</span><span class="sxs-lookup"><span data-stu-id="638a6-108">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="638a6-109">创建 .NET 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="638a6-109">Creating a .NET console application</span></span>
> - <span data-ttu-id="638a6-110">编写支持取消的异步应用程序</span><span class="sxs-lookup"><span data-stu-id="638a6-110">Writing an async application that supports cancellation</span></span>
> - <span data-ttu-id="638a6-111">演示发出取消信号</span><span class="sxs-lookup"><span data-stu-id="638a6-111">Demonstrating signaling cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="638a6-112">必备条件</span><span class="sxs-lookup"><span data-stu-id="638a6-112">Prerequisites</span></span>

<span data-ttu-id="638a6-113">本教程需要的内容如下：</span><span class="sxs-lookup"><span data-stu-id="638a6-113">This tutorial requires the following:</span></span>

- [<span data-ttu-id="638a6-114">.NET 5.0 或更高版本的 SDK</span><span class="sxs-lookup"><span data-stu-id="638a6-114">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="638a6-115">集成开发环境 (IDE)</span><span class="sxs-lookup"><span data-stu-id="638a6-115">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="638a6-116">建议使用 Visual Studio、Visual Studio Code 或 Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="638a6-116">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a><span data-ttu-id="638a6-117">创建示例应用程序</span><span class="sxs-lookup"><span data-stu-id="638a6-117">Create example application</span></span>

<span data-ttu-id="638a6-118">创建新的 .NET Core 控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="638a6-118">Create a new .NET Core console application.</span></span> <span data-ttu-id="638a6-119">可通过使用 [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) 命令或从 [Visual Studio](/visualstudio/install/install-visual-studio) 进行创建。</span><span class="sxs-lookup"><span data-stu-id="638a6-119">You can create one by using the [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="638a6-120">在你最喜欢的编辑器中打开 Program.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="638a6-120">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="638a6-121">替换 using 语句</span><span class="sxs-lookup"><span data-stu-id="638a6-121">Replace using statements</span></span>

<span data-ttu-id="638a6-122">将现有 using 语句替换为以下声明：</span><span class="sxs-lookup"><span data-stu-id="638a6-122">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="638a6-123">添加字段</span><span class="sxs-lookup"><span data-stu-id="638a6-123">Add fields</span></span>

<span data-ttu-id="638a6-124">在 `Program` 类定义中，添加以下三个字段：</span><span class="sxs-lookup"><span data-stu-id="638a6-124">In the `Program` class definition, add these three fields:</span></span>

```csharp
static readonly CancellationTokenSource s_cts = new CancellationTokenSource();

static readonly HttpClient s_client = new HttpClient
{
    MaxResponseContentBufferSize = 1_000_000
};

static readonly IEnumerable<string> s_urlList = new string[]
{
    "https://docs.microsoft.com",
    "https://docs.microsoft.com/aspnet/core",
    "https://docs.microsoft.com/azure",
    "https://docs.microsoft.com/azure/devops",
    "https://docs.microsoft.com/dotnet",
    "https://docs.microsoft.com/dynamics365",
    "https://docs.microsoft.com/education",
    "https://docs.microsoft.com/enterprise-mobility-security",
    "https://docs.microsoft.com/gaming",
    "https://docs.microsoft.com/graph",
    "https://docs.microsoft.com/microsoft-365",
    "https://docs.microsoft.com/office",
    "https://docs.microsoft.com/powershell",
    "https://docs.microsoft.com/sql",
    "https://docs.microsoft.com/surface",
    "https://docs.microsoft.com/system-center",
    "https://docs.microsoft.com/visualstudio",
    "https://docs.microsoft.com/windows",
    "https://docs.microsoft.com/xamarin"
};
```

<span data-ttu-id="638a6-125"><xref:System.Threading.CancellationTokenSource> 用于向 <xref:System.Threading.CancellationToken> 发出请求取消的信号。</span><span class="sxs-lookup"><span data-stu-id="638a6-125">The <xref:System.Threading.CancellationTokenSource> is used to signal a requested cancellation to a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="638a6-126">`HttpClient` 公开发送 HTTP 请求和接收 HTTP 响应的能力。</span><span class="sxs-lookup"><span data-stu-id="638a6-126">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="638a6-127">`s_urlList` 包括应用程序计划处理的所有 URL。</span><span class="sxs-lookup"><span data-stu-id="638a6-127">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="638a6-128">更新应用程序入口点</span><span class="sxs-lookup"><span data-stu-id="638a6-128">Update application entry point</span></span>

<span data-ttu-id="638a6-129">控制台应用程序的主入口点是 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="638a6-129">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="638a6-130">将现有方法替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="638a6-130">Replace the existing method with the following:</span></span>

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");
    Console.WriteLine("Press the ENTER key to cancel...\n");

    Task cancelTask = Task.Run(() =>
    {
        while (Console.ReadKey().Key != ConsoleKey.Enter)
        {
            Console.WriteLine("Press the ENTER key to cancel...");
        }

        Console.WriteLine("\nENTER key pressed: cancelling downloads.\n");
        s_cts.Cancel();
    });

    Task sumPageSizesTask = SumPageSizesAsync();

    await Task.WhenAny(new[] { cancelTask, sumPageSizesTask });

    Console.WriteLine("Application ending.");
}
```

<span data-ttu-id="638a6-131">目前将已更新的 `Main` 方法视为[异步 main 方法](../../../whats-new/csharp-7-1.md#async-main)，这允许将异步入口点引入可执行文件中。</span><span class="sxs-lookup"><span data-stu-id="638a6-131">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7-1.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="638a6-132">将几条说明性消息写入控制台，然后声明名为 `cancelTask` 的 <xref:System.Threading.Tasks.Task> 实例，这将读取控制台密钥笔画。</span><span class="sxs-lookup"><span data-stu-id="638a6-132">It writes a few instructional messages to the console, then declares a <xref:System.Threading.Tasks.Task> instance named `cancelTask`, which will read console key strokes.</span></span> <span data-ttu-id="638a6-133">如果按 <kbd>Enter</kbd>，则会调用 <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="638a6-133">If the <kbd>Enter</kbd> key is pressed, a call to <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> is made.</span></span> <span data-ttu-id="638a6-134">这将发出取消信号。</span><span class="sxs-lookup"><span data-stu-id="638a6-134">This will signal cancellation.</span></span> <span data-ttu-id="638a6-135">下一步，从 `SumPageSizesAsync` 方法分配 `sumPageSizesTask` 变量。</span><span class="sxs-lookup"><span data-stu-id="638a6-135">Next, the `sumPageSizesTask` variable is assigned from the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="638a6-136">然后，将这两个任务传递到 <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType>，这会在完成两个任务中的任意一个时继续。</span><span class="sxs-lookup"><span data-stu-id="638a6-136">Both tasks are then passed to <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType>, which will continue when any of the two tasks have completed.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="638a6-137">创建异步总和页面大小方法</span><span class="sxs-lookup"><span data-stu-id="638a6-137">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="638a6-138">在 `Main` 方法下，添加 `SumPageSizesAsync` 方法：</span><span class="sxs-lookup"><span data-stu-id="638a6-138">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    int total = 0;
    foreach (string url in s_urlList)
    {
        int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
        total += contentLength;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

<span data-ttu-id="638a6-139">该方法从实例化和启动 <xref:System.Diagnostics.Stopwatch> 开始。</span><span class="sxs-lookup"><span data-stu-id="638a6-139">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="638a6-140">然后会在 `s_urlList` 的每个 URL 中进行循环，并调用 `ProcessUrlAsync`。</span><span class="sxs-lookup"><span data-stu-id="638a6-140">It then loops through each URL in the `s_urlList` and calls `ProcessUrlAsync`.</span></span> <span data-ttu-id="638a6-141">对于每次迭代，`s_cts.Token` 都会传递到 `ProcessUrlAsync` 方法中，并且代码将返回 <xref:System.Threading.Tasks.Task%601>，其中 `TResult` 是一个整数：</span><span class="sxs-lookup"><span data-stu-id="638a6-141">With each iteration, the `s_cts.Token` is passed into the `ProcessUrlAsync` method and the code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a><span data-ttu-id="638a6-142">添加进程方法</span><span class="sxs-lookup"><span data-stu-id="638a6-142">Add process method</span></span>

<span data-ttu-id="638a6-143">在 `SumPageSizesAsync` 方法下添加以下 `ProcessUrlAsync` 方法：</span><span class="sxs-lookup"><span data-stu-id="638a6-143">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync();
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="638a6-144">对于任何给定的 URL，该方法都将使用提供的 `client` 实例以 `byte[]` 形式来获取响应。</span><span class="sxs-lookup"><span data-stu-id="638a6-144">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="638a6-145"><xref:System.Threading.CancellationToken> 实例会传递到 <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> 和 <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType> 方法中。</span><span class="sxs-lookup"><span data-stu-id="638a6-145">The <xref:System.Threading.CancellationToken> instance is passed into the <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> and <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="638a6-146">`token` 用于注册请求取消。</span><span class="sxs-lookup"><span data-stu-id="638a6-146">The `token` is used to register for requested cancellation.</span></span> <span data-ttu-id="638a6-147">将 URL 和长度写入控制台后会返回该长度。</span><span class="sxs-lookup"><span data-stu-id="638a6-147">The length is returned after the URL and length is written to the console.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="638a6-148">示例应用程序输出</span><span class="sxs-lookup"><span data-stu-id="638a6-148">Example application output</span></span>

```console
Application started.
Press the ENTER key to cancel...

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663
https://docs.microsoft.com/dotnet                                67,452
https://docs.microsoft.com/dynamics365                           48,582
https://docs.microsoft.com/education                             22,924

ENTER key pressed: cancelling downloads.

Application ending.
```

## <a name="complete-example"></a><span data-ttu-id="638a6-149">完整示例</span><span class="sxs-lookup"><span data-stu-id="638a6-149">Complete example</span></span>

<span data-ttu-id="638a6-150">下列代码是示例的 Program.cs 文件的完整文本。</span><span class="sxs-lookup"><span data-stu-id="638a6-150">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="638a6-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="638a6-151">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="638a6-152">使用 Async 和 Await 的异步编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="638a6-152">Asynchronous programming with async and await (C#)</span></span>](index.md)

## <a name="next-steps"></a><span data-ttu-id="638a6-153">后续步骤</span><span class="sxs-lookup"><span data-stu-id="638a6-153">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="638a6-154">在一段时间后取消异步任务 (C#)</span><span class="sxs-lookup"><span data-stu-id="638a6-154">Cancel async tasks after a period of time (C#)</span></span>](cancel-async-tasks-after-a-period-of-time.md)
