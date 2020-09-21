---
title: 在异步任务完成时对其进行处理
description: 此示例演示如何使用 C# 中的 Task.WhenAny 启动多个任务并在完成时处理其结果，而不是按照它们的启动顺序进行处理。
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 520953eaf851dc82440e39b348aa4b246255e126
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557302"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a><span data-ttu-id="a7efd-103">在异步任务完成时对其进行处理 (C#)</span><span class="sxs-lookup"><span data-stu-id="a7efd-103">Process asynchronous tasks as they complete (C#)</span></span>

<span data-ttu-id="a7efd-104">通过使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>，可同时启动多个任务，并在它们完成时逐个对它们进行处理，而不是按照它们的启动顺序进行处理。</span><span class="sxs-lookup"><span data-stu-id="a7efd-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they're completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="a7efd-105">下面的示例使用查询来创建一组任务。</span><span class="sxs-lookup"><span data-stu-id="a7efd-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="a7efd-106">每个任务都下载指定网站的内容。</span><span class="sxs-lookup"><span data-stu-id="a7efd-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="a7efd-107">在对 while 循环的每次迭代中，对 <xref:System.Threading.Tasks.Task.WhenAny%2A> 的等待调用返回任务集合中首先完成下载的任务。</span><span class="sxs-lookup"><span data-stu-id="a7efd-107">In each iteration of a while loop, an awaited call to <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="a7efd-108">此任务从集合中删除并进行处理。</span><span class="sxs-lookup"><span data-stu-id="a7efd-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="a7efd-109">循环重复进行，直到集合中不包含任何任务。</span><span class="sxs-lookup"><span data-stu-id="a7efd-109">The loop repeats until the collection contains no more tasks.</span></span>

## <a name="create-example-application"></a><span data-ttu-id="a7efd-110">创建示例应用程序</span><span class="sxs-lookup"><span data-stu-id="a7efd-110">Create example application</span></span>

<span data-ttu-id="a7efd-111">创建新的 .NET Core 控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="a7efd-111">Create a new .NET Core console application.</span></span> <span data-ttu-id="a7efd-112">可使用 [dotnet new console](../../../../core/tools/dotnet-new.md#console) 命令或 [Visual Studio](/visualstudio/install/install-visual-studio) 进行创建。</span><span class="sxs-lookup"><span data-stu-id="a7efd-112">You can create one by using the [dotnet new console](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="a7efd-113">在你最喜欢的编辑器中打开 Program.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="a7efd-113">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="a7efd-114">替换 using 语句</span><span class="sxs-lookup"><span data-stu-id="a7efd-114">Replace using statements</span></span>

<span data-ttu-id="a7efd-115">将现有 using 语句替换为以下声明：</span><span class="sxs-lookup"><span data-stu-id="a7efd-115">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="a7efd-116">添加字段</span><span class="sxs-lookup"><span data-stu-id="a7efd-116">Add fields</span></span>

<span data-ttu-id="a7efd-117">在 `Program` 类定义中，添加以下两个字段：</span><span class="sxs-lookup"><span data-stu-id="a7efd-117">In the `Program` class definition, add the following two fields:</span></span>

```csharp
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

<span data-ttu-id="a7efd-118">`HttpClient` 公开发送 HTTP 请求和接收 HTTP 响应的能力。</span><span class="sxs-lookup"><span data-stu-id="a7efd-118">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="a7efd-119">`s_urlList` 包括应用程序计划处理的所有 URL。</span><span class="sxs-lookup"><span data-stu-id="a7efd-119">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="a7efd-120">更新应用程序入口点</span><span class="sxs-lookup"><span data-stu-id="a7efd-120">Update application entry point</span></span>

<span data-ttu-id="a7efd-121">控制台应用程序的主入口点是 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="a7efd-121">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="a7efd-122">将现有方法替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="a7efd-122">Replace the existing method with the following:</span></span>

```csharp
static Task Main() => SumPageSizesAsync();
```

<span data-ttu-id="a7efd-123">目前将已更新的 `Main` 方法视为[异步 main 方法](../../../whats-new/csharp-7-1.md#async-main)，这允许将异步入口点引入可执行文件中。</span><span class="sxs-lookup"><span data-stu-id="a7efd-123">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7-1.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="a7efd-124">它表示对 `SumPageSizesAsync` 的调用。</span><span class="sxs-lookup"><span data-stu-id="a7efd-124">It is expressed a call to `SumPageSizesAsync`.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="a7efd-125">创建异步总和页面大小方法</span><span class="sxs-lookup"><span data-stu-id="a7efd-125">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="a7efd-126">在 `Main` 方法下，添加 `SumPageSizesAsync` 方法：</span><span class="sxs-lookup"><span data-stu-id="a7efd-126">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    IEnumerable<Task<int>> downloadTasksQuery =
        from url in s_urlList
        select ProcessUrlAsync(url, s_client);

    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

    int total = 0;
    while (downloadTasks.Any())
    {
        Task<int> finishedTask = await Task.WhenAny(downloadTasks);
        downloadTasks.Remove(finishedTask);
        total += await finishedTask;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

<span data-ttu-id="a7efd-127">该方法从实例化和启动 <xref:System.Diagnostics.Stopwatch> 开始。</span><span class="sxs-lookup"><span data-stu-id="a7efd-127">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="a7efd-128">然后它会包含一个查询，执行此查询时，将创建任务集合。</span><span class="sxs-lookup"><span data-stu-id="a7efd-128">It then includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="a7efd-129">每次对以下代码中的 `ProcessUrlAsync` 进行调用都会返回 <xref:System.Threading.Tasks.Task%601>，其中 `TResult` 是一个整数：</span><span class="sxs-lookup"><span data-stu-id="a7efd-129">Each call to `ProcessUrlAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

<span data-ttu-id="a7efd-130">由于 LINQ 的[延迟执行](../../../../standard/linq/deferred-execution-example.md)，因此可调用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 来启动每个任务。</span><span class="sxs-lookup"><span data-stu-id="a7efd-130">Due to [deferred execution](../../../../standard/linq/deferred-execution-example.md) with the LINQ, you call <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> to start each task.</span></span>

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

<span data-ttu-id="a7efd-131">`while` 循环针对集合中的每个任务执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="a7efd-131">The `while` loop performs the following steps for each task in the collection:</span></span>

1. <span data-ttu-id="a7efd-132">等待调用 `WhenAny`，以标识集合中首个已完成下载的任务。</span><span class="sxs-lookup"><span data-stu-id="a7efd-132">Awaits a call to `WhenAny` to identify the first task in the collection that has finished its download.</span></span>

    ```csharp
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
    ```

1. <span data-ttu-id="a7efd-133">从集合中移除任务。</span><span class="sxs-lookup"><span data-stu-id="a7efd-133">Removes that task from the collection.</span></span>

    ```csharp
    downloadTasks.Remove(firstFinishedTask);
    ```

1. <span data-ttu-id="a7efd-134">等待 `finishedTask`，由对 `ProcessUrlAsync` 的调用返回。</span><span class="sxs-lookup"><span data-stu-id="a7efd-134">Awaits `finishedTask`, which is returned by a call to `ProcessUrlAsync`.</span></span> <span data-ttu-id="a7efd-135">`finishedTask` 变量是 <xref:System.Threading.Tasks.Task%601>，其中 `TResult` 是整数。</span><span class="sxs-lookup"><span data-stu-id="a7efd-135">The `finishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span> <span data-ttu-id="a7efd-136">任务已完成，但需等待它检索已下载网站的长度，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="a7efd-136">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="a7efd-137">如果任务出错，`await` 将引发存储在 `AggregateException` 中的第一个子异常，这一点与读取 <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> 属性将引发 `AggregateException` 不同。</span><span class="sxs-lookup"><span data-stu-id="a7efd-137">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> property, which would throw the `AggregateException`.</span></span>

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a><span data-ttu-id="a7efd-138">添加进程方法</span><span class="sxs-lookup"><span data-stu-id="a7efd-138">Add process method</span></span>

<span data-ttu-id="a7efd-139">在 `SumPageSizesAsync` 方法下添加以下 `ProcessUrlAsync` 方法：</span><span class="sxs-lookup"><span data-stu-id="a7efd-139">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="a7efd-140">对于任何给定的 URL，该方法都将使用提供的 `client` 实例以 `byte[]` 形式来获取响应。</span><span class="sxs-lookup"><span data-stu-id="a7efd-140">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="a7efd-141">将 URL 和长度写入控制台后会返回该长度。</span><span class="sxs-lookup"><span data-stu-id="a7efd-141">The length is returned after the URL and length is written to the console.</span></span>

<span data-ttu-id="a7efd-142">多次运行此程序以验证并不总是以相同顺序显示已下载的长度。</span><span class="sxs-lookup"><span data-stu-id="a7efd-142">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="a7efd-143">如示例所示，可以在循环中使用 `WhenAny` 来解决涉及少量任务的问题。</span><span class="sxs-lookup"><span data-stu-id="a7efd-143">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="a7efd-144">但是，如果要处理大量任务，可以采用其他更高效的方法。</span><span class="sxs-lookup"><span data-stu-id="a7efd-144">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="a7efd-145">有关详细信息和示例，请参阅 [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete)（在任务完成时处理它们）。</span><span class="sxs-lookup"><span data-stu-id="a7efd-145">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span></span>

## <a name="complete-example"></a><span data-ttu-id="a7efd-146">完整示例</span><span class="sxs-lookup"><span data-stu-id="a7efd-146">Complete example</span></span>

<span data-ttu-id="a7efd-147">下列代码是示例的 Program.cs 文件的完整文本。</span><span class="sxs-lookup"><span data-stu-id="a7efd-147">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="a7efd-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7efd-148">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="a7efd-149">使用 Async 和 Await 的异步编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="a7efd-149">Asynchronous programming with async and await (C#)</span></span>](index.md)
