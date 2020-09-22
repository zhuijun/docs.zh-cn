---
title: 在 Windows 上部署 .NET for Apache Spark 应用程序
description: 了解如何在 Windows 上部署 .NET for Apache Spark 应用程序。
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 249b4bccbf1378d8ef8c824f39151c33fb9f875a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557146"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="8098b-103">部署 .NET for Apache Spark 应用程序</span><span class="sxs-lookup"><span data-stu-id="8098b-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="8098b-104">此操作说明介绍在 Windows 上部署 .NET for Apache Spark 应用程序的步骤。</span><span class="sxs-lookup"><span data-stu-id="8098b-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="debug-your-application"></a><span data-ttu-id="8098b-105">调试应用程序</span><span class="sxs-lookup"><span data-stu-id="8098b-105">Debug your application</span></span>

<span data-ttu-id="8098b-106">打开“新命令提示符”窗口并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="8098b-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="8098b-107">运行命令时，会看到以下输出：</span><span class="sxs-lookup"><span data-stu-id="8098b-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="8098b-108">在调试模式下，DotnetRunner 不启动 .NET 应用程序，而是等待你启动 .NET 应用。</span><span class="sxs-lookup"><span data-stu-id="8098b-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="8098b-109">将此命令提示符窗口保持为打开状态，并通过 C# 调试器启动 .NET 应用程序以调试应用程序。</span><span class="sxs-lookup"><span data-stu-id="8098b-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="8098b-110">使用 C# 调试器（[适用于 Windows/macOS 的 Visual Studio 调试器](https://visualstudio.microsoft.com/vs/)或 [Visual Studio Code 中的 C# 调试器扩展](https://code.visualstudio.com/Docs/editor/debugging)）启动 .NET 应用程序以调试应用程序。</span><span class="sxs-lookup"><span data-stu-id="8098b-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="8098b-111">调试用户定义函数 (UDF)</span><span class="sxs-lookup"><span data-stu-id="8098b-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="8098b-112">只有安装了 Visual Studio 调试器的 Windows 上支持用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="8098b-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="8098b-113">在运行 `spark-submit`之前，请设置以下环境变量：</span><span class="sxs-lookup"><span data-stu-id="8098b-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="8098b-114">运行 Spark 应用程序时，将弹出 `Choose Just-In-Time Debugger` 窗口。</span><span class="sxs-lookup"><span data-stu-id="8098b-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="8098b-115">选择 Visual Studio 调试器。</span><span class="sxs-lookup"><span data-stu-id="8098b-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="8098b-116">调试器将在 [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52) 中的以下位置处中断：</span><span class="sxs-lookup"><span data-stu-id="8098b-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="8098b-117">导航到包含计划调试的 UDF 的 .cs 文件，并[设置断点](/visualstudio/debugger/using-breakpoints?view=vs-2019)。</span><span class="sxs-lookup"><span data-stu-id="8098b-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="8098b-118">断点将显示 `The breakpoint will not currently be hit`，因为工作线程尚未加载包含 UDF 的程序集。</span><span class="sxs-lookup"><span data-stu-id="8098b-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="8098b-119">点击 `F5` 继续应用程序，最终会点击断点。</span><span class="sxs-lookup"><span data-stu-id="8098b-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="8098b-120">将为每个任务弹出“选择实时调试器”窗口。</span><span class="sxs-lookup"><span data-stu-id="8098b-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="8098b-121">若要避免弹出过多窗口，请将执行器数设置为较小数目。</span><span class="sxs-lookup"><span data-stu-id="8098b-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="8098b-122">例如，可以将“--master local[1]”选项用于 spark-submit，以将任务数设置为 1，这将启动一个调试器实例。</span><span class="sxs-lookup"><span data-stu-id="8098b-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="8098b-123">调试 Scala 代码</span><span class="sxs-lookup"><span data-stu-id="8098b-123">Debug Scala code</span></span>

<span data-ttu-id="8098b-124">如果需要调试 Scala 端代码（`DotnetRunner`、`DotnetBackendHandler` 等），可以使用以下命令，并使用 [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html) 将调试程序附加到正在运行的进程：</span><span class="sxs-lookup"><span data-stu-id="8098b-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="8098b-125">运行命令后，使用 [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html) 将调试程序附加到正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="8098b-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8098b-126">后续步骤</span><span class="sxs-lookup"><span data-stu-id="8098b-126">Next steps</span></span>

* [<span data-ttu-id="8098b-127">.NET for Apache Spark 入门</span><span class="sxs-lookup"><span data-stu-id="8098b-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="8098b-128">将 .NET for Apache Spark 应用程序部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="8098b-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="8098b-129">将 .NET for Apache Spark 应用程序部署到 Databricks</span><span class="sxs-lookup"><span data-stu-id="8098b-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="8098b-130">将 .NET for Apache Spark 应用程序部署到 Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="8098b-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
