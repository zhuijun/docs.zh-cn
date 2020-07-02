---
title: .NET for Apache Spark 入门
description: 了解如何在 Windows、MacOS 和 Ubuntu 上使用 .NET Core 运行 .NET for Apache Spark 应用。
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: be150bcef0029f69136e21c35791c863220af244
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617647"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="91148-103">教程：.NET for Apache Spark 入门</span><span class="sxs-lookup"><span data-stu-id="91148-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="91148-104">本教程介绍如何在 Windows、MacOS 和 Ubuntu 上使用 .NET Core 运行 .NET for Apache Spark 应用。</span><span class="sxs-lookup"><span data-stu-id="91148-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, MacOS, and Ubuntu.</span></span>

<span data-ttu-id="91148-105">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="91148-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="91148-106">为 .NET for Apache Spark 作环境准备</span><span class="sxs-lookup"><span data-stu-id="91148-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="91148-107">编写你的第一个 .NET for Apache Spark 应用程序</span><span class="sxs-lookup"><span data-stu-id="91148-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="91148-108">构建和运行简单的 .NET for Apache Spark 应用程序</span><span class="sxs-lookup"><span data-stu-id="91148-108">Build and run your simple .NET for Apache Spark application</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="91148-109">准备环境</span><span class="sxs-lookup"><span data-stu-id="91148-109">Prepare your environment</span></span>

<span data-ttu-id="91148-110">在开始编写应用之前，需要先设置一些必备依赖项。</span><span class="sxs-lookup"><span data-stu-id="91148-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="91148-111">如果可从命令行环境运行 `dotnet`、`java`、`mvn` 和 `spark-shell`，则表示你的环境已准备就绪且你可跳到下一部分。</span><span class="sxs-lookup"><span data-stu-id="91148-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="91148-112">如果无法运行任何或部分命令，请执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="91148-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="91148-113">1.安装 .NET</span><span class="sxs-lookup"><span data-stu-id="91148-113">1. Install .NET</span></span>

<span data-ttu-id="91148-114">要开始构建 .NET 应用，需要下载并安装 .NET SDK（软件开发工具包）。</span><span class="sxs-lookup"><span data-stu-id="91148-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="91148-115">下载并安装 [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)。</span><span class="sxs-lookup"><span data-stu-id="91148-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="91148-116">安装 SDK 会将 `dotnet` 工具链添加到路径。</span><span class="sxs-lookup"><span data-stu-id="91148-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="91148-117">安装 .NET Core SDK 后，打开一个新的命令提示符或终端，然后运行 `dotnet`。</span><span class="sxs-lookup"><span data-stu-id="91148-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="91148-118">如果该命令运行并打印出有关如何使用 dotnet 的信息，则可转到下一步。</span><span class="sxs-lookup"><span data-stu-id="91148-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="91148-119">如果收到 `'dotnet' is not recognized as an internal or external command` 错误，请确保在运行命令之前已打开新的命令提示符或终端。</span><span class="sxs-lookup"><span data-stu-id="91148-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="91148-120">2.安装 Java</span><span class="sxs-lookup"><span data-stu-id="91148-120">2. Install Java</span></span>

<span data-ttu-id="91148-121">安装适用于 Windows 和 MacOS 的 [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)，或适用于 Ubuntu 的 [OpenJDK 8](https://openjdk.java.net/install/)。</span><span class="sxs-lookup"><span data-stu-id="91148-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and MacOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="91148-122">选择适用于操作系统的合适版本。</span><span class="sxs-lookup"><span data-stu-id="91148-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="91148-123">例如，为 Windows x64 计算机选择 jdk-8u201-windows-x64.exe（如下所示），或为 MacOS 计算机选择 jdk-8u231-macosx-x64.dmg。</span><span class="sxs-lookup"><span data-stu-id="91148-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for MacOS.</span></span> <span data-ttu-id="91148-124">然后，使用命令 `java` 来验证安装。</span><span class="sxs-lookup"><span data-stu-id="91148-124">Then, use the command `java` to verify the installation.</span></span>

![Java 下载](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="91148-126">3.安装压缩软件</span><span class="sxs-lookup"><span data-stu-id="91148-126">3. Install compression software</span></span>

<span data-ttu-id="91148-127">Apache Spark 以 .tgz 压缩文件的形式下载。</span><span class="sxs-lookup"><span data-stu-id="91148-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="91148-128">使用提取程序（如 [7-Zip](https://www.7-zip.org/) 或 [WinZip](https://www.winzip.com/)）来提取文件。</span><span class="sxs-lookup"><span data-stu-id="91148-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="91148-129">4.安装 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="91148-129">4. Install Apache Spark</span></span>

<span data-ttu-id="91148-130">[下载并安装 Apache Spark](https://spark.apache.org/downloads.html)。</span><span class="sxs-lookup"><span data-stu-id="91148-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="91148-131">需要从版本 2.3.\* 或者 2.4.0、2.4.1、2.4.3 或 2.4.4 中进行选择（.NET for Apache Spark 与其他版本的 Apache Spark 不兼容）。</span><span class="sxs-lookup"><span data-stu-id="91148-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="91148-132">以下步骤中使用的命令假定你已[下载并安装 Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)。</span><span class="sxs-lookup"><span data-stu-id="91148-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="91148-133">若想要使用其他版本，请将 2.4.1 替换为适当的版本号。</span><span class="sxs-lookup"><span data-stu-id="91148-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="91148-134">然后，提取 .tar 文件和 Apache Spark 文件。</span><span class="sxs-lookup"><span data-stu-id="91148-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="91148-135">要提取嵌套的 .tar 文件：</span><span class="sxs-lookup"><span data-stu-id="91148-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="91148-136">找到你已下载的 spark-2.4.1-bin-hadoop2.7.tgz 文件。</span><span class="sxs-lookup"><span data-stu-id="91148-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="91148-137">右键单击该文件，然后选择“7-Zip”->“提取到此处”。</span><span class="sxs-lookup"><span data-stu-id="91148-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="91148-138">spark-2.4.1-bin-hadoop2.7.tar 是与你下载的 .tgz 文件一起创建的 。</span><span class="sxs-lookup"><span data-stu-id="91148-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="91148-139">要提取 Apache Spark 文件：</span><span class="sxs-lookup"><span data-stu-id="91148-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="91148-140">右键单击 spark-2.4.1-bin-hadoop2.7.tar，然后选择“7-Zip”->“提取文件...” </span><span class="sxs-lookup"><span data-stu-id="91148-140">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="91148-141">在“提取到”字段输入“C:\bin” 。</span><span class="sxs-lookup"><span data-stu-id="91148-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="91148-142">取消勾选“提取到”字段下面的复选框。</span><span class="sxs-lookup"><span data-stu-id="91148-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="91148-143">选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="91148-143">Select **OK**.</span></span>
* <span data-ttu-id="91148-144">Apache Spark 文件会提取到 C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="91148-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![安装 Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="91148-146">运行以下命令，以设置用于在 Windows 上查找 Apache Spark 的环境变量：</span><span class="sxs-lookup"><span data-stu-id="91148-146">Run the following commands to set the environment variables used to locate Apache Spark on **Windows**:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="91148-147">运行以下命令，以设置用于在 MacOS 和 Ubuntu 上查找 Apache Spark 的环境变量：</span><span class="sxs-lookup"><span data-stu-id="91148-147">Run the following commands to set the environment variables used to locate Apache Spark on **MacOS** and **Ubuntu**:</span></span>

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

<span data-ttu-id="91148-148">安装所有内容并设置环境变量后，打开新的命令提示符或终端并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="91148-148">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="91148-149">如果该命令运行并打印出版本信息，则可转到下一步。</span><span class="sxs-lookup"><span data-stu-id="91148-149">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="91148-150">如果收到 `'spark-submit' is not recognized as an internal or external command` 错误，请确保已打开新的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="91148-150">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="91148-151">5.安装 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="91148-151">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="91148-152">从 .NET for Apache Spark GitHub 下载 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases)。</span><span class="sxs-lookup"><span data-stu-id="91148-152">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="91148-153">例如，如果你在使用 Windows 计算机并计划使用 .NET Core，请[下载 Windows x64 netcoreapp3.1 版本](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip)。</span><span class="sxs-lookup"><span data-stu-id="91148-153">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span></span>

<span data-ttu-id="91148-154">要提取 Microsoft.Spark.Worker：</span><span class="sxs-lookup"><span data-stu-id="91148-154">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="91148-155">找到你已下载的 Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip 文件。</span><span class="sxs-lookup"><span data-stu-id="91148-155">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="91148-156">右键单击并选择“7-Zip”->“提取文件...”。</span><span class="sxs-lookup"><span data-stu-id="91148-156">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="91148-157">在“提取到”字段输入“C:\bin” 。</span><span class="sxs-lookup"><span data-stu-id="91148-157">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="91148-158">取消勾选“提取到”字段下面的复选框。</span><span class="sxs-lookup"><span data-stu-id="91148-158">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="91148-159">选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="91148-159">Select **OK**.</span></span>

![安装 .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="91148-161">6.安装 WinUtils（仅限 Windows）</span><span class="sxs-lookup"><span data-stu-id="91148-161">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="91148-162">.NET for Apache Spark 要求与 Apache Spark 一起安装 WinUtils。</span><span class="sxs-lookup"><span data-stu-id="91148-162">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="91148-163">[下载 winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe)。</span><span class="sxs-lookup"><span data-stu-id="91148-163">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="91148-164">然后，将 WinUtils 复制到 C:\bin\spark-2.4.1-bin-hadoop2.7\bin。</span><span class="sxs-lookup"><span data-stu-id="91148-164">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="91148-165">如果你在使用其他版本的 Hadoop（相关批注可参见 Spark 安装文件夹名称的末尾），请[选择与你的 Hadoop 版本兼容的 WinUtils 版本](https://github.com/steveloughran/winutils)。</span><span class="sxs-lookup"><span data-stu-id="91148-165">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="91148-166">7.设置 DOTNET_WORKER_DIR 并检查依赖项</span><span class="sxs-lookup"><span data-stu-id="91148-166">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="91148-167">运行以下命令之一来设置 `DOTNET_WORKER_DIR` 环境变量，.NET 应用使用该变量查找 .NET for Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="91148-167">Run one of the following commands to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span>

<span data-ttu-id="91148-168">在 Windows 上创建[新环境变量](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR`，并将其设置为下载和提取 Microsoft.Spark.Worker 时使用的目录（例如，`C:\bin\Microsoft.Spark.Worker\`）。</span><span class="sxs-lookup"><span data-stu-id="91148-168">On **Windows**, create a [new environment variable](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, `C:\bin\Microsoft.Spark.Worker\`).</span></span>

<span data-ttu-id="91148-169">在 MacOS 上使用 `export DOTNET_WORKER_DIR <your_path>` 创建新环境变量，并将其设置为下载和提取 Microsoft.Spark.Worker 时使用的目录（例如，~/bin/Microsoft.Spark.Worker/）。</span><span class="sxs-lookup"><span data-stu-id="91148-169">On **MacOS**, create a new environment variable using `export DOTNET_WORKER_DIR <your_path>` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker/*).</span></span>

<span data-ttu-id="91148-170">在 Ubuntu 上创建[新环境变量](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR`，并将其设置为下载和提取 Microsoft.Spark.Worker 时使用的目录（例如，~/bin/Microsoft.Spark.Worker）。</span><span class="sxs-lookup"><span data-stu-id="91148-170">On **Ubuntu**, create a [new environment variable](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker*).</span></span>

<span data-ttu-id="91148-171">最后，仔细检查是否可从命令行运行 `dotnet`、`java`、`mvn` 和 `spark-shell`，然后再转到下一部分。</span><span class="sxs-lookup"><span data-stu-id="91148-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="91148-172">编写 .NET for Apache Spark 应用</span><span class="sxs-lookup"><span data-stu-id="91148-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="91148-173">1.创建控制台应用</span><span class="sxs-lookup"><span data-stu-id="91148-173">1. Create a console app</span></span>

<span data-ttu-id="91148-174">在命令提示符处或终端中，运行以下命令来创建新的控制台应用程序：</span><span class="sxs-lookup"><span data-stu-id="91148-174">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="91148-175">`dotnet` 命令将创建 `console` 类型的 `new` 应用程序。</span><span class="sxs-lookup"><span data-stu-id="91148-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="91148-176">`-o` 参数将创建名为 mySparkApp 的目录，其中会存储你的应用并填充必需文件。</span><span class="sxs-lookup"><span data-stu-id="91148-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="91148-177">`cd mySparkApp` 命令会将目录更改为你刚才创建的应用目录。</span><span class="sxs-lookup"><span data-stu-id="91148-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="91148-178">2.安装 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="91148-178">2. Install NuGet package</span></span>

<span data-ttu-id="91148-179">要在应用中使用 .NET for Apache Spark，请安装 Microsoft.Spark 包。</span><span class="sxs-lookup"><span data-stu-id="91148-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="91148-180">在命令提示符处或终端中运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="91148-180">In your command prompt or terminal, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a><span data-ttu-id="91148-181">3.编写应用代码</span><span class="sxs-lookup"><span data-stu-id="91148-181">3. Code your app</span></span>

<span data-ttu-id="91148-182">在 Visual Studio Code 中打开 Program.cs 或打开任何文本编辑器，再将所有代码替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="91148-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-create-and-add-a-data-file"></a><span data-ttu-id="91148-183">4.创建和添加数据文件</span><span class="sxs-lookup"><span data-stu-id="91148-183">4. Create and add a data file</span></span>

<span data-ttu-id="91148-184">打开命令提示符或终端，然后导航到应用文件夹。</span><span class="sxs-lookup"><span data-stu-id="91148-184">Open your command prompt or terminal and navigate into your app folder.</span></span>

```bash
cd <your-app-output-directory>
```

<span data-ttu-id="91148-185">你的应用会处理包含多行文本的文件。</span><span class="sxs-lookup"><span data-stu-id="91148-185">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="91148-186">在 mySparkApp 目录中创建一个 input.txt 文件，其中包含以下文本 ：</span><span class="sxs-lookup"><span data-stu-id="91148-186">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="91148-187">运行 .NET for Apache Spark 应用</span><span class="sxs-lookup"><span data-stu-id="91148-187">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="91148-188">运行以下命令来构建应用程序：</span><span class="sxs-lookup"><span data-stu-id="91148-188">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="91148-189">运行以下命令，提交要在 Apache Spark 上运行的应用程序：</span><span class="sxs-lookup"><span data-stu-id="91148-189">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > <span data-ttu-id="91148-190">此命令假设已下载 Apache Spark 并添加到 PATH 环境变量，以便能够使用 `spark-submit`。</span><span class="sxs-lookup"><span data-stu-id="91148-190">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="91148-191">如果不是，需要使用完整路径（例如 C:\bin\apache-spark\bin\spark-submit 或 ~/spark/bin/spark-submit）。</span><span class="sxs-lookup"><span data-stu-id="91148-191">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

3. <span data-ttu-id="91148-192">在应用运行时，input.txt 的字数统计数据会写入控制台。</span><span class="sxs-lookup"><span data-stu-id="91148-192">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="91148-193">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="91148-193">Congratulations!</span></span> <span data-ttu-id="91148-194">你已成功创建并运行 .NET for Apache Spark 应用。</span><span class="sxs-lookup"><span data-stu-id="91148-194">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="91148-195">后续步骤</span><span class="sxs-lookup"><span data-stu-id="91148-195">Next steps</span></span>

<span data-ttu-id="91148-196">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="91148-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="91148-197">为 .NET for Apache Spark 准备 Windows 环境</span><span class="sxs-lookup"><span data-stu-id="91148-197">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="91148-198">编写你的第一个 .NET for Apache Spark 应用程序</span><span class="sxs-lookup"><span data-stu-id="91148-198">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="91148-199">构建和运行简单的 .NET for Apache Spark 应用程序</span><span class="sxs-lookup"><span data-stu-id="91148-199">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="91148-200">要观看解说上述步骤的视频，请查看 [.NET for Apache Spark 101 视频系列](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)。</span><span class="sxs-lookup"><span data-stu-id="91148-200">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="91148-201">查看资源页以了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="91148-201">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="91148-202">.NET for Apache Spark 资源</span><span class="sxs-lookup"><span data-stu-id="91148-202">.NET for Apache Spark Resources</span></span>](../resources/index.md)
