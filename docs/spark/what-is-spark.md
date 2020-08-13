---
title: 什么是 Apache Spark？
description: 了解 Apache Spark 和大数据方案。
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: cde66c4084b7c86e1b78d89c2bad94402dbd7d60
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555989"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="d422b-103">什么是 Apache Spark？</span><span class="sxs-lookup"><span data-stu-id="d422b-103">What is Apache Spark?</span></span>

<span data-ttu-id="d422b-104">[Apache Spark](https://spark.apache.org/) 是一种开放源代码并行处理框架，支持使用内存中处理来提升大数据分析应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="d422b-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="d422b-105">大数据解决方案旨在处理对传统数据库来说太大或太复杂的数据。</span><span class="sxs-lookup"><span data-stu-id="d422b-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="d422b-106">Spark 处理内存中的大量数据，这比基于磁盘的替代方法要快得多。</span><span class="sxs-lookup"><span data-stu-id="d422b-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span>

## <a name="common-big-data-scenarios"></a><span data-ttu-id="d422b-107">常见的大数据方案</span><span class="sxs-lookup"><span data-stu-id="d422b-107">Common big data scenarios</span></span>

<span data-ttu-id="d422b-108">如果需要存储和处理大量数据、转换非结构化数据或处理流数据，则可以考虑使用大数据体系结构。</span><span class="sxs-lookup"><span data-stu-id="d422b-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="d422b-109">Spark 是一种通用的分布式处理引擎，可用于多个大数据方案。</span><span class="sxs-lookup"><span data-stu-id="d422b-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span>

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="d422b-110">提取、转换和加载 (ETL)</span><span class="sxs-lookup"><span data-stu-id="d422b-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="d422b-111">[提取、转换和加载 (ETL)](/azure/architecture/data-guide/relational-data/etl) 是从一个或多个源收集数据、修改数据以及将数据移动到新数据存储的过程。</span><span class="sxs-lookup"><span data-stu-id="d422b-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="d422b-112">可通过多种方法来转换数据，其中包括：</span><span class="sxs-lookup"><span data-stu-id="d422b-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="d422b-113">Filtering</span><span class="sxs-lookup"><span data-stu-id="d422b-113">Filtering</span></span>
* <span data-ttu-id="d422b-114">排序</span><span class="sxs-lookup"><span data-stu-id="d422b-114">Sorting</span></span>
* <span data-ttu-id="d422b-115">聚合</span><span class="sxs-lookup"><span data-stu-id="d422b-115">Aggregating</span></span>
* <span data-ttu-id="d422b-116">联接</span><span class="sxs-lookup"><span data-stu-id="d422b-116">Joining</span></span>
* <span data-ttu-id="d422b-117">清理</span><span class="sxs-lookup"><span data-stu-id="d422b-117">Cleaning</span></span>
* <span data-ttu-id="d422b-118">删除重复项</span><span class="sxs-lookup"><span data-stu-id="d422b-118">Deduplicating</span></span>
* <span data-ttu-id="d422b-119">正在验证</span><span class="sxs-lookup"><span data-stu-id="d422b-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="d422b-120">实时数据流处理</span><span class="sxs-lookup"><span data-stu-id="d422b-120">Real-time data stream processing</span></span>

<span data-ttu-id="d422b-121">流数据（或实时数据）是移动数据。</span><span class="sxs-lookup"><span data-stu-id="d422b-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="d422b-122">IoT 设备、网络日志和点击流中的遥测都是流数据示例。</span><span class="sxs-lookup"><span data-stu-id="d422b-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="d422b-123">可以处理实时数据以提供有用的信息，例如地理空间分析、远程监视和异常情况检测。</span><span class="sxs-lookup"><span data-stu-id="d422b-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="d422b-124">就像关系数据一样，可以在将数据移动到输出接收器之前筛选、聚合和准备流数据。</span><span class="sxs-lookup"><span data-stu-id="d422b-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="d422b-125">Apache Spark 通过 [Spark Streaming](https://spark.apache.org/streaming/) 支持[实时数据流处理](/azure/architecture/data-guide/big-data/real-time-processing)。</span><span class="sxs-lookup"><span data-stu-id="d422b-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span>

### <a name="batch-processing"></a><span data-ttu-id="d422b-126">批处理</span><span class="sxs-lookup"><span data-stu-id="d422b-126">Batch processing</span></span>

<span data-ttu-id="d422b-127">[批处理](/azure/architecture/data-guide/big-data/batch-processing)是对静态大数据的处理。</span><span class="sxs-lookup"><span data-stu-id="d422b-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="d422b-128">可以使用并行的长时间运行的作业来筛选、聚合和准备非常大的数据集。</span><span class="sxs-lookup"><span data-stu-id="d422b-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="d422b-129">通过 MLlib 进行机器学习</span><span class="sxs-lookup"><span data-stu-id="d422b-129">Machine learning through MLlib</span></span>

<span data-ttu-id="d422b-130">机器学习用于处理高级分析问题。</span><span class="sxs-lookup"><span data-stu-id="d422b-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="d422b-131">计算机可以使用现有数据来预测将来的行为、结果和趋势。</span><span class="sxs-lookup"><span data-stu-id="d422b-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="d422b-132">Apache Spark 的机器学习库 [MLlib](https://spark.apache.org/mllib/) 包含多个机器学习算法和实用工具。</span><span class="sxs-lookup"><span data-stu-id="d422b-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="d422b-133">通过 GraphX 进行图形处理</span><span class="sxs-lookup"><span data-stu-id="d422b-133">Graph processing through GraphX</span></span>

<span data-ttu-id="d422b-134">图形是由边缘连接的节点的集合。</span><span class="sxs-lookup"><span data-stu-id="d422b-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="d422b-135">如果有分层数据或有包含互连关系的数据，则可以使用图形数据库。</span><span class="sxs-lookup"><span data-stu-id="d422b-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="d422b-136">可以使用 Apache Spark 的 [GraphX](https://spark.apache.org/graphx/) API 来处理此数据。</span><span class="sxs-lookup"><span data-stu-id="d422b-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="d422b-137">采用 Spark SQL 的 SQL 和结构化数据处理</span><span class="sxs-lookup"><span data-stu-id="d422b-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="d422b-138">如果使用的是结构化（格式化）数据，则可以在使用 [Spark SQL](https://spark.apache.org/sql/) 的 Spark 应用程序中使用 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="d422b-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="d422b-139">Apache Spark 体系结构</span><span class="sxs-lookup"><span data-stu-id="d422b-139">Apache Spark architecture</span></span>

<span data-ttu-id="d422b-140">使用主角色/辅助角色体系结构的 Apache Spark 有三个主要组件：驱动程序、执行程序和群集管理器。</span><span class="sxs-lookup"><span data-stu-id="d422b-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Apache Spark 体系结构](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="d422b-142">驱动程序</span><span class="sxs-lookup"><span data-stu-id="d422b-142">Driver</span></span>

<span data-ttu-id="d422b-143">驱动程序由程序（如 C# 控制台应用）和 Spark 会话组成。</span><span class="sxs-lookup"><span data-stu-id="d422b-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="d422b-144">Spark 会话会对程序进行处理，将其分成由执行程序处理的较小任务。</span><span class="sxs-lookup"><span data-stu-id="d422b-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="d422b-145">执行程序</span><span class="sxs-lookup"><span data-stu-id="d422b-145">Executors</span></span>

<span data-ttu-id="d422b-146">每个执行程序或工作器节点会接收来自驱动程序的任务，并执行该任务。</span><span class="sxs-lookup"><span data-stu-id="d422b-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="d422b-147">执行程序驻留在称为群集的实体上。</span><span class="sxs-lookup"><span data-stu-id="d422b-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="d422b-148">群集管理器</span><span class="sxs-lookup"><span data-stu-id="d422b-148">Cluster manager</span></span>

<span data-ttu-id="d422b-149">群集管理器与驱动程序和执行程序进行通信，以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d422b-149">The cluster manager communicates with both the driver and the executors to:</span></span>

* <span data-ttu-id="d422b-150">管理资源分配</span><span class="sxs-lookup"><span data-stu-id="d422b-150">Manage resource allocation</span></span>
* <span data-ttu-id="d422b-151">管理程序部分</span><span class="sxs-lookup"><span data-stu-id="d422b-151">Manage program division</span></span>
* <span data-ttu-id="d422b-152">管理程序执行</span><span class="sxs-lookup"><span data-stu-id="d422b-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="d422b-153">语言支持</span><span class="sxs-lookup"><span data-stu-id="d422b-153">Language support</span></span>

<span data-ttu-id="d422b-154">Apache Spark 支持以下编程语言：</span><span class="sxs-lookup"><span data-stu-id="d422b-154">Apache Spark supports the following programming languages:</span></span>

* <span data-ttu-id="d422b-155">Scala</span><span class="sxs-lookup"><span data-stu-id="d422b-155">Scala</span></span>
* <span data-ttu-id="d422b-156">Python</span><span class="sxs-lookup"><span data-stu-id="d422b-156">Python</span></span>
* <span data-ttu-id="d422b-157">Java</span><span class="sxs-lookup"><span data-stu-id="d422b-157">Java</span></span>
* <span data-ttu-id="d422b-158">SQL</span><span class="sxs-lookup"><span data-stu-id="d422b-158">SQL</span></span>
* <span data-ttu-id="d422b-159">R</span><span class="sxs-lookup"><span data-stu-id="d422b-159">R</span></span>
* <span data-ttu-id="d422b-160">.NET 语言 (C#/F#)</span><span class="sxs-lookup"><span data-stu-id="d422b-160">.NET languages (C#/F#)</span></span>

## <a name="spark-apis"></a><span data-ttu-id="d422b-161">Spark API</span><span class="sxs-lookup"><span data-stu-id="d422b-161">Spark APIs</span></span>

<span data-ttu-id="d422b-162">Apache Spark 支持以下 API：</span><span class="sxs-lookup"><span data-stu-id="d422b-162">Apache Spark supports the following APIs:</span></span>

* [<span data-ttu-id="d422b-163">Spark Scala API</span><span class="sxs-lookup"><span data-stu-id="d422b-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [<span data-ttu-id="d422b-164">Spark Java API</span><span class="sxs-lookup"><span data-stu-id="d422b-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [<span data-ttu-id="d422b-165">Spark Python API</span><span class="sxs-lookup"><span data-stu-id="d422b-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [<span data-ttu-id="d422b-166">Spark R API</span><span class="sxs-lookup"><span data-stu-id="d422b-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* <span data-ttu-id="d422b-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html)（内置函数）</span><span class="sxs-lookup"><span data-stu-id="d422b-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="d422b-168">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d422b-168">Next steps</span></span>

<span data-ttu-id="d422b-169">了解如何在 .NET 应用程序中使用 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="d422b-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="d422b-170">使用 .NET for Apache Spark，具有 .NET 经验和业务逻辑的开发人员可使用 C# 和 F# 编写大数据查询。</span><span class="sxs-lookup"><span data-stu-id="d422b-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d422b-171">什么是 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d422b-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
