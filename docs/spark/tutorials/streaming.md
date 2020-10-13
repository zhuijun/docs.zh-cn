---
title: 使用 .NET for Apache Spark 进行结构化流式处理的教程
description: 在本教程中，了解如何使用 .NET for Apache Spark 进行 Spark 结构化流式处理。
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 47c716db931dc912b80844fe69283b12d030c238
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955572"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="5497b-103">教程：使用 .NET for Apache Spark 进行结构化流式处理</span><span class="sxs-lookup"><span data-stu-id="5497b-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>

<span data-ttu-id="5497b-104">本教程介绍如何使用 .NET for Apache Spark 调用 Spark 结构化流式处理。</span><span class="sxs-lookup"><span data-stu-id="5497b-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="5497b-105">Spark 结构化流式处理是 Apache Spark 对处理实时数据流的支持。</span><span class="sxs-lookup"><span data-stu-id="5497b-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="5497b-106">流处理是指在生成实时数据时对其进行分析。</span><span class="sxs-lookup"><span data-stu-id="5497b-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="5497b-107">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="5497b-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="5497b-108">创建和运行 .NET for Apache Spark 应用程序</span><span class="sxs-lookup"><span data-stu-id="5497b-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="5497b-109">使用 netcat 创建数据流</span><span class="sxs-lookup"><span data-stu-id="5497b-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="5497b-110">使用用户定义的函数和 SparkSQL 分析流式处理数据</span><span class="sxs-lookup"><span data-stu-id="5497b-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5497b-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="5497b-111">Prerequisites</span></span>

<span data-ttu-id="5497b-112">如果这是你的第一个 .NET for Apache Spark 应用程序，请开始使用[入门教程](get-started.md)以熟悉基础知识。</span><span class="sxs-lookup"><span data-stu-id="5497b-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="5497b-113">创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="5497b-113">Create a console application</span></span>

1. <span data-ttu-id="5497b-114">在命令提示符处，运行以下命令来创建新的控制台应用程序：</span><span class="sxs-lookup"><span data-stu-id="5497b-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="5497b-115">`dotnet` 命令将创建 `console` 类型的 `new` 应用程序。</span><span class="sxs-lookup"><span data-stu-id="5497b-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="5497b-116">`-o` 参数将创建名为 mySparkStreamingApp 的目录，其中会存储你的应用并填充必需文件  。</span><span class="sxs-lookup"><span data-stu-id="5497b-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="5497b-117">`cd mySparkStreamingApp` 命令会将目录更改为你刚才创建的应用目录。</span><span class="sxs-lookup"><span data-stu-id="5497b-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="5497b-118">要在应用中使用 .NET for Apache Spark，请安装 Microsoft.Spark 包。</span><span class="sxs-lookup"><span data-stu-id="5497b-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="5497b-119">在控制台中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="5497b-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="5497b-120">建立连接并连接到数据流</span><span class="sxs-lookup"><span data-stu-id="5497b-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="5497b-121">测试流处理的一个常用方法是通过 netcat  。</span><span class="sxs-lookup"><span data-stu-id="5497b-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="5497b-122">netcat（也称为 nc  ）可用于从网络连接中读取以及向网络连接写入。</span><span class="sxs-lookup"><span data-stu-id="5497b-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="5497b-123">通过终端窗口建立与 netcat 的网络连接。</span><span class="sxs-lookup"><span data-stu-id="5497b-123">You establish a network connection with netcat through a terminal window.</span></span>

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="5497b-124">使用 netcat 创建数据流</span><span class="sxs-lookup"><span data-stu-id="5497b-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="5497b-125">[下载 netcat](https://sourceforge.net/projects/nc110/files/)。</span><span class="sxs-lookup"><span data-stu-id="5497b-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="5497b-126">然后，从 zip 下载中提取文件并将提取的目录追加到“PATH”环境变量。</span><span class="sxs-lookup"><span data-stu-id="5497b-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="5497b-127">若要启动新连接，请打开新的控制台并运行用于连接到端口 9999 上的 localhost 的以下命令。</span><span class="sxs-lookup"><span data-stu-id="5497b-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="5497b-128">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="5497b-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="5497b-129">在 Linux 上：</span><span class="sxs-lookup"><span data-stu-id="5497b-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="5497b-130">Spark 程序侦听在此命令提示符下键入的输入。</span><span class="sxs-lookup"><span data-stu-id="5497b-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="5497b-131">创建 SparkSession</span><span class="sxs-lookup"><span data-stu-id="5497b-131">Create a SparkSession</span></span>

1. <span data-ttu-id="5497b-132">将以下附加的 `using` 语句添加到 mySparkStreamingApp 中 Program.cs 文件顶部   ：</span><span class="sxs-lookup"><span data-stu-id="5497b-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="5497b-133">将以下代码添加到 `Main` 方法，以创建新的 `SparkSession`。</span><span class="sxs-lookup"><span data-stu-id="5497b-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="5497b-134">Spark 会话是使用数据集和数据帧 API 对 Spark 进行编程的入口点。</span><span class="sxs-lookup"><span data-stu-id="5497b-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="5497b-135">通过调用上面创建的 spark 对象，可在整个程序中访问 Spark 和数据帧功能  。</span><span class="sxs-lookup"><span data-stu-id="5497b-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="5497b-136">使用 ReadStream() 连接到流</span><span class="sxs-lookup"><span data-stu-id="5497b-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="5497b-137">`ReadStream()` 方法返回一个 `DataStreamReader`，它可用于以 `DataFrame` 形式读取流式处理数据。</span><span class="sxs-lookup"><span data-stu-id="5497b-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="5497b-138">包括主机和端口信息，以告知 Spark 应用获取其流式处理数据的位置。</span><span class="sxs-lookup"><span data-stu-id="5497b-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="5497b-139">注册用户定义的函数</span><span class="sxs-lookup"><span data-stu-id="5497b-139">Register a user-defined function</span></span>

<span data-ttu-id="5497b-140">可以使用 Spark 应用程序中的 UDF（用户定义的函数）来对数据执行计算和分析  。</span><span class="sxs-lookup"><span data-stu-id="5497b-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="5497b-141">将以下代码添加到 `Main` 方法，以注册名为 `udfArray` 的 UDF。</span><span class="sxs-lookup"><span data-stu-id="5497b-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span>

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="5497b-142">此 UDF 处理从 netcat 终端接收的每个字符串，以生成包含原始字符串（包含在 str  中）的数组，后跟与原始字符串的长度串联的原始字符串。</span><span class="sxs-lookup"><span data-stu-id="5497b-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span>

<span data-ttu-id="5497b-143">例如，在 netcat 终端中输入“Hello world”会生成一个数组，其中  ：</span><span class="sxs-lookup"><span data-stu-id="5497b-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="5497b-144">array\[0] = Hello world</span><span class="sxs-lookup"><span data-stu-id="5497b-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="5497b-145">array\[1] = Hello world 11</span><span class="sxs-lookup"><span data-stu-id="5497b-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="5497b-146">使用 SparkSQL</span><span class="sxs-lookup"><span data-stu-id="5497b-146">Use SparkSQL</span></span>

<span data-ttu-id="5497b-147">使用 SparkSQL 对存储在数据帧中的数据执行各种功能。</span><span class="sxs-lookup"><span data-stu-id="5497b-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="5497b-148">通常将 UDF 和 SparkSQL 结合起来以将 UDF 应用于数据帧的每一行。</span><span class="sxs-lookup"><span data-stu-id="5497b-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="5497b-149">此代码片段将 udfArray 应用于数据帧中的每个值，这表示从 netcat 终端读取的每个字符串  。</span><span class="sxs-lookup"><span data-stu-id="5497b-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="5497b-150">应用 SparkSQL 方法 <xref:Microsoft.Spark.Sql.Functions.Explode%2A>，将数组的每个项放在其自己的行中。</span><span class="sxs-lookup"><span data-stu-id="5497b-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="5497b-151">最后，使用 <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> 放置在新的数据帧 arrayDF 中生成的列  。</span><span class="sxs-lookup"><span data-stu-id="5497b-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="5497b-152">显示流</span><span class="sxs-lookup"><span data-stu-id="5497b-152">Display your stream</span></span>

<span data-ttu-id="5497b-153">使用 <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> 来确定输出的特征，例如将结果打印到控制台并仅显示最新输出。</span><span class="sxs-lookup"><span data-stu-id="5497b-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="5497b-154">运行代码</span><span class="sxs-lookup"><span data-stu-id="5497b-154">Run your code</span></span>

<span data-ttu-id="5497b-155">Spark 中的结构化流式处理通过一系列小型批处理来处理数据  。</span><span class="sxs-lookup"><span data-stu-id="5497b-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="5497b-156">运行程序时，建立 netcat 连接的命令提示符允许你开始键入。</span><span class="sxs-lookup"><span data-stu-id="5497b-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="5497b-157">每次在该命令提示符下键入数据后按 Enter 键，Spark 都会将你的项视为批处理，并运行 UDF。</span><span class="sxs-lookup"><span data-stu-id="5497b-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="5497b-158">使用 spark-submit 运行应用</span><span class="sxs-lookup"><span data-stu-id="5497b-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="5497b-159">启动新的 netcat 会话后，打开新终端并运行 `spark-submit` 命令，该命令类似于以下命令：</span><span class="sxs-lookup"><span data-stu-id="5497b-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="5497b-160">请确保将包含实际路径的上述命令更新为 Microsoft Spark jar 文件。</span><span class="sxs-lookup"><span data-stu-id="5497b-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="5497b-161">上述命令还假定你的 netcat 服务器正在 localhost 端口 9999 上运行。</span><span class="sxs-lookup"><span data-stu-id="5497b-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="5497b-162">获取代码</span><span class="sxs-lookup"><span data-stu-id="5497b-162">Get the code</span></span>

<span data-ttu-id="5497b-163">本教程使用 [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) 示例，但 GitHub 上还有其他三个完整的流处理示例：</span><span class="sxs-lookup"><span data-stu-id="5497b-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="5497b-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)：从任意源流式传输的数据的字数统计</span><span class="sxs-lookup"><span data-stu-id="5497b-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="5497b-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs)：包含窗口化逻辑的数据的字数统计</span><span class="sxs-lookup"><span data-stu-id="5497b-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="5497b-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)：从 Kafka 流式传输的数据的字数统计</span><span class="sxs-lookup"><span data-stu-id="5497b-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="5497b-167">后续步骤</span><span class="sxs-lookup"><span data-stu-id="5497b-167">Next steps</span></span>

<span data-ttu-id="5497b-168">请继续学习下一篇文章，了解如何将 .NET for Apache Spark 应用程序部署到 Databricks。</span><span class="sxs-lookup"><span data-stu-id="5497b-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="5497b-169">教程：将 .NET for Apache Spark 应用程序部署到 Databricks</span><span class="sxs-lookup"><span data-stu-id="5497b-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
