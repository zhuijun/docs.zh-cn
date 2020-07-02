---
title: 将 .NET for Apache Spark 应用程序部署到 Amazon EMR Spark
description: 了解如何将 .NET for Apache Spark 应用程序部署到 Amazon EMR Spark。
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6cf26044693c5d923d11e1bbc72232e7009fe73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618254"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="3d12f-103">将 .NET for Apache Spark 应用程序部署到 Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="3d12f-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="3d12f-104">本教程介绍如何将 .NET for Apache Spark 应用程序部署到 Amazon EMR Spark。</span><span class="sxs-lookup"><span data-stu-id="3d12f-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span>

<span data-ttu-id="3d12f-105">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="3d12f-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="3d12f-106">准备 Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="3d12f-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="3d12f-107">发布 Spark .NET 应用</span><span class="sxs-lookup"><span data-stu-id="3d12f-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="3d12f-108">将应用部署到 Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="3d12f-108">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="3d12f-109">运行你的应用</span><span class="sxs-lookup"><span data-stu-id="3d12f-109">Run your app</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="3d12f-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="3d12f-110">Prerequisites</span></span>

<span data-ttu-id="3d12f-111">开始之前，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3d12f-111">Before you start, do the following:</span></span>

* <span data-ttu-id="3d12f-112">下载 [AWS CLI](https://aws.amazon.com/cli/)。</span><span class="sxs-lookup"><span data-stu-id="3d12f-112">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="3d12f-113">将 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 下载到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="3d12f-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="3d12f-114">这是稍后用于将 .NET for Apache Spark 依赖文件复制到 Spark 群集的工作器节点的帮助程序脚本。</span><span class="sxs-lookup"><span data-stu-id="3d12f-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="3d12f-115">准备辅助角色依赖项</span><span class="sxs-lookup"><span data-stu-id="3d12f-115">Prepare worker dependencies</span></span>

<span data-ttu-id="3d12f-116">Microsoft.Spark.Worker 是后端组件，位于 Spark 群集的单个工作器节点上  。</span><span class="sxs-lookup"><span data-stu-id="3d12f-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="3d12f-117">想要执行 C# UDF（用户定义的函数），Spark 需要了解如何启动 .NET CLR 以执行 UDF。</span><span class="sxs-lookup"><span data-stu-id="3d12f-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="3d12f-118">Microsoft.Spark.Worker 向 Spark 提供启用此功能的类集合  。</span><span class="sxs-lookup"><span data-stu-id="3d12f-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="3d12f-119">选择要在群集上部署的 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp 版本。</span><span class="sxs-lookup"><span data-stu-id="3d12f-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="3d12f-120">例如，如果需要使用 `netcoreapp2.1` 的 `.NET for Apache Spark v0.1.0`，则下载 [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)。</span><span class="sxs-lookup"><span data-stu-id="3d12f-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="3d12f-121">将 `Microsoft.Spark.Worker.<release>.tar.gz` 和 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 上传到群集具有访问权限的分布式文件系统（如 S3）。</span><span class="sxs-lookup"><span data-stu-id="3d12f-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="3d12f-122">准备 .NET for Apache Spark 应用</span><span class="sxs-lookup"><span data-stu-id="3d12f-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="3d12f-123">按照[入门](get-started.md)教程来生成应用。</span><span class="sxs-lookup"><span data-stu-id="3d12f-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="3d12f-124">发布独立的 Spark .NET 应用。</span><span class="sxs-lookup"><span data-stu-id="3d12f-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="3d12f-125">在 Linux 上运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="3d12f-125">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="3d12f-126">为已发布的文件生成 `<your app>.zip`。</span><span class="sxs-lookup"><span data-stu-id="3d12f-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="3d12f-127">使用 `zip` 在 Linux 上运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="3d12f-127">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="3d12f-128">将以下项上传到群集具有访问权限的分布式文件系统（如 S3）：</span><span class="sxs-lookup"><span data-stu-id="3d12f-128">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="3d12f-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`：此 jar 作为 [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet 包的一部分包含在内，并且并置在应用的生成输出目录中。</span><span class="sxs-lookup"><span data-stu-id="3d12f-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="3d12f-130">要放在每个执行程序的工作目录中的文件（如每位工作人员都可以访问的依赖文件或公共数据）或程序集（如包含应用所依赖的用户定义的函数或库的 DLL）。</span><span class="sxs-lookup"><span data-stu-id="3d12f-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="3d12f-131">部署到 Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="3d12f-131">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="3d12f-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) 是一个托管群集平台，可简化 AWS 上运行的大数据框架。</span><span class="sxs-lookup"><span data-stu-id="3d12f-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="3d12f-133">Amazon EMR Spark 基于 Linux。</span><span class="sxs-lookup"><span data-stu-id="3d12f-133">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="3d12f-134">因此，如果要将应用部署到 Amazon EMR Spark，请确保应用与 .NET Standard 兼容，并且使用 [.NET Core 编译器](https://dotnet.microsoft.com/download)编译应用。</span><span class="sxs-lookup"><span data-stu-id="3d12f-134">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="3d12f-135">部署 Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="3d12f-135">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="3d12f-136">只需在创建群集时执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="3d12f-136">This step is only required at cluster creation.</span></span>

<span data-ttu-id="3d12f-137">使用 [Bootstrap 操作](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)在创建群集期间运行 `install-worker.sh`。</span><span class="sxs-lookup"><span data-stu-id="3d12f-137">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="3d12f-138">使用 AWS CLI 在 Linux 上运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="3d12f-138">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a><span data-ttu-id="3d12f-139">运行你的应用</span><span class="sxs-lookup"><span data-stu-id="3d12f-139">Run your app</span></span>

<span data-ttu-id="3d12f-140">可采用两种方式在 Amazon EMR Spark 中运行应用：spark-submit 和 Amazon EMR 步骤。</span><span class="sxs-lookup"><span data-stu-id="3d12f-140">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="3d12f-141">使用 spark-submit</span><span class="sxs-lookup"><span data-stu-id="3d12f-141">Use spark-submit</span></span>

<span data-ttu-id="3d12f-142">可以使用 [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令将 .NET for Apache Spark 作业提交到 Amazon EMR Spark。</span><span class="sxs-lookup"><span data-stu-id="3d12f-142">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="3d12f-143">群集中某个节点的 `ssh`。</span><span class="sxs-lookup"><span data-stu-id="3d12f-143">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="3d12f-144">运行 `spark-submit`。</span><span class="sxs-lookup"><span data-stu-id="3d12f-144">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="3d12f-145">使用 Amazon EMR 步骤</span><span class="sxs-lookup"><span data-stu-id="3d12f-145">Use Amazon EMR Steps</span></span>

<span data-ttu-id="3d12f-146">[Amazon EMR 步骤](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html)可用于将作业提交到 EMR 群集上安装的 Spark 框架。</span><span class="sxs-lookup"><span data-stu-id="3d12f-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="3d12f-147">使用 AWS CLI 在 Linux 上运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="3d12f-147">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="3d12f-148">后续步骤</span><span class="sxs-lookup"><span data-stu-id="3d12f-148">Next steps</span></span>

<span data-ttu-id="3d12f-149">在本教程中，你已将 .NET for Apache Spark 应用程序部署到 Amazon EMR Spark。</span><span class="sxs-lookup"><span data-stu-id="3d12f-149">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="3d12f-150">对于 .NET for Apache Spark 示例项目，请继续使用 GitHub。</span><span class="sxs-lookup"><span data-stu-id="3d12f-150">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3d12f-151">.NET for Apache Spark 示例</span><span class="sxs-lookup"><span data-stu-id="3d12f-151">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
