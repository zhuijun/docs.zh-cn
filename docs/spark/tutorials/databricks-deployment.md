---
title: 将 .NET for Apache Spark 应用程序部署到 Databricks
description: 了解如何将 .NET for Apache Spark 应用程序部署到 Databricks。
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 1f705878a577a7fa375346cae18010d8c8cc77e1
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955442"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="8df62-103">教程：将 .NET for Apache Spark 应用程序部署到 Databricks</span><span class="sxs-lookup"><span data-stu-id="8df62-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="8df62-104">本教程介绍如何使用 Azure Databricks 将应用部署到云。Azure Databricks 是一种基于 Apache Spark 的分析平台，包含一键设置、经过简化的工作流以及支持协作的交互式工作区。</span><span class="sxs-lookup"><span data-stu-id="8df62-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="8df62-105">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="8df62-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="8df62-106">创建 Azure Databricks 工作区。</span><span class="sxs-lookup"><span data-stu-id="8df62-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="8df62-107">发布 .NET for Apache Spark 应用。</span><span class="sxs-lookup"><span data-stu-id="8df62-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="8df62-108">创建 Spark 作业和 Spark 群集。</span><span class="sxs-lookup"><span data-stu-id="8df62-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="8df62-109">在 Spark 群集上运行应用。</span><span class="sxs-lookup"><span data-stu-id="8df62-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8df62-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="8df62-110">Prerequisites</span></span>

<span data-ttu-id="8df62-111">开始之前，请完成以下任务：</span><span class="sxs-lookup"><span data-stu-id="8df62-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="8df62-112">如果没有 Azure 帐户，请创建一个[免费帐户](https://azure.microsoft.com/free/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="8df62-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="8df62-113">登录 [Azure 门户](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="8df62-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="8df62-114">完成 [.NET for Apache Spark - 10 分钟入门](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)教程。</span><span class="sxs-lookup"><span data-stu-id="8df62-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="8df62-115">创建 Azure Databricks 工作区</span><span class="sxs-lookup"><span data-stu-id="8df62-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="8df62-116">不能使用 Azure 免费试用订阅完成本教程。</span><span class="sxs-lookup"><span data-stu-id="8df62-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="8df62-117">如果你有免费帐户，请转到个人资料并将订阅更改为“即用即付”。</span><span class="sxs-lookup"><span data-stu-id="8df62-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="8df62-118">有关详细信息，请参阅 [Azure 免费帐户](https://azure.microsoft.com/free/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="8df62-118">For more information, see [Azure free account](https://azure.microsoft.com/free/dotnet/).</span></span> <span data-ttu-id="8df62-119">然后，[移除支出限制](/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)，并为你所在区域的 vCPU [请求增加配额](/azure/azure-supportability/resource-manager-core-quotas-request)。</span><span class="sxs-lookup"><span data-stu-id="8df62-119">Then, [remove the spending limit](/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="8df62-120">创建 Azure Databricks 工作区时，可以选择“试用版(高级 - 14天免费 DBU)”定价层，让工作区访问免费的高级 Azure Databricks DBU 14 天。</span><span class="sxs-lookup"><span data-stu-id="8df62-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="8df62-121">在本部分，使用 Azure 门户创建 Azure Databricks 工作区。</span><span class="sxs-lookup"><span data-stu-id="8df62-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="8df62-122">在 Azure 门户中，选择“创建资源” > “分析” > “Azure Databricks”。</span><span class="sxs-lookup"><span data-stu-id="8df62-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![在 Azure 门户中创建 Azure Databricks 资源](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="8df62-124">在“Azure Databricks 服务”下，提供所需的值以创建 Databricks 工作区。</span><span class="sxs-lookup"><span data-stu-id="8df62-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="8df62-125">Property</span><span class="sxs-lookup"><span data-stu-id="8df62-125">Property</span></span>  |<span data-ttu-id="8df62-126">描述</span><span class="sxs-lookup"><span data-stu-id="8df62-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="8df62-127">**工作区名称**</span><span class="sxs-lookup"><span data-stu-id="8df62-127">**Workspace name**</span></span>     | <span data-ttu-id="8df62-128">为 Databricks 工作区提供一个名称。</span><span class="sxs-lookup"><span data-stu-id="8df62-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="8df62-129">**订阅**</span><span class="sxs-lookup"><span data-stu-id="8df62-129">**Subscription**</span></span>     | <span data-ttu-id="8df62-130">从下拉列表中选择自己的 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="8df62-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="8df62-131">**资源组**</span><span class="sxs-lookup"><span data-stu-id="8df62-131">**Resource group**</span></span>     | <span data-ttu-id="8df62-132">指定是要创建新的资源组还是使用现有的资源组。</span><span class="sxs-lookup"><span data-stu-id="8df62-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="8df62-133">资源组是用于保存 Azure 解决方案相关资源的容器。</span><span class="sxs-lookup"><span data-stu-id="8df62-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="8df62-134">有关详细信息，请参阅 [Azure 资源组概述](/azure/azure-resource-manager/resource-group-overview)。</span><span class="sxs-lookup"><span data-stu-id="8df62-134">For more information, see [Azure Resource Group overview](/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="8df62-135">**位置**</span><span class="sxs-lookup"><span data-stu-id="8df62-135">**Location**</span></span>     | <span data-ttu-id="8df62-136">选择首选区域。</span><span class="sxs-lookup"><span data-stu-id="8df62-136">Select your preferred region.</span></span> <span data-ttu-id="8df62-137">有关可用区域的信息，请参阅[各区域推出的 Azure 服务](https://azure.microsoft.com/regions/services/)。</span><span class="sxs-lookup"><span data-stu-id="8df62-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="8df62-138">**定价层**</span><span class="sxs-lookup"><span data-stu-id="8df62-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="8df62-139">在“标准”、“高级”和“试用”之间进行选择。  </span><span class="sxs-lookup"><span data-stu-id="8df62-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="8df62-140">有关这些层的详细信息，请参阅 [Databricks 价格页](https://azure.microsoft.com/pricing/details/databricks/)。</span><span class="sxs-lookup"><span data-stu-id="8df62-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="8df62-141">**虚拟网络**</span><span class="sxs-lookup"><span data-stu-id="8df62-141">**Virtual Network**</span></span>     |   <span data-ttu-id="8df62-142">否</span><span class="sxs-lookup"><span data-stu-id="8df62-142">No</span></span>       |

3. <span data-ttu-id="8df62-143">选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="8df62-143">Select **Create**.</span></span> <span data-ttu-id="8df62-144">创建工作区需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="8df62-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="8df62-145">创建工作区时，可以在“通知”中查看部署状态。</span><span class="sxs-lookup"><span data-stu-id="8df62-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="8df62-146">安装 Azure Databricks 工具</span><span class="sxs-lookup"><span data-stu-id="8df62-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="8df62-147">可使用 Databricks CLI 连接到 Azure Databricks 群集，然后将文件从本地计算机上传到这些群集。</span><span class="sxs-lookup"><span data-stu-id="8df62-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="8df62-148">Databricks 群集通过 DBFS（Databricks 文件系统）访问文件。</span><span class="sxs-lookup"><span data-stu-id="8df62-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="8df62-149">Databricks CLI 需要使用 Python 3.6 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="8df62-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="8df62-150">如果已安装 Python，则可以跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="8df62-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="8df62-151">**对于 Windows：**</span><span class="sxs-lookup"><span data-stu-id="8df62-151">**For Windows:**</span></span>

   [<span data-ttu-id="8df62-152">下载适用于 Windows 的 Python</span><span class="sxs-lookup"><span data-stu-id="8df62-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="8df62-153">**对于 Linux：** 大多数 Linux 发行版上都预安装了 Python。</span><span class="sxs-lookup"><span data-stu-id="8df62-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="8df62-154">要查看已安装的版本，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="8df62-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="8df62-155">使用 pip 安装 Databricks CLI。</span><span class="sxs-lookup"><span data-stu-id="8df62-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="8df62-156">Python 3.4 及更高版本默认包含 pip。</span><span class="sxs-lookup"><span data-stu-id="8df62-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="8df62-157">使用适用于 Python 3 的 pip3。</span><span class="sxs-lookup"><span data-stu-id="8df62-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="8df62-158">运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="8df62-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="8df62-159">安装 Databricks CLI 后，打开一个新的命令提示符并运行命令 `databricks`。</span><span class="sxs-lookup"><span data-stu-id="8df62-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="8df62-160">如果收到“[databricks] 未被识别为内部或外部命令错误”，请确认是否打开了新的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="8df62-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="8df62-161">设置 Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="8df62-161">Set up Azure Databricks</span></span>

<span data-ttu-id="8df62-162">Databricks CLI 安装完毕之后，接下来需要设置身份验证详细信息。</span><span class="sxs-lookup"><span data-stu-id="8df62-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="8df62-163">运行 Databricks CLI 命令 `databricks configure --token`。</span><span class="sxs-lookup"><span data-stu-id="8df62-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="8df62-164">运行配置命令后，系统会提示你进入主机。</span><span class="sxs-lookup"><span data-stu-id="8df62-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="8df62-165">你的主机 URL 使用的格式为 `https://<Location>.azuredatabricks.net`。</span><span class="sxs-lookup"><span data-stu-id="8df62-165">Your host URL uses the format: `https://<Location>.azuredatabricks.net`.</span></span> <span data-ttu-id="8df62-166">例如，如果在创建 Azure Databricks 服务期间选择了“eastus2”，则主机将为 `https://eastus2.azuredatabricks.net`。</span><span class="sxs-lookup"><span data-stu-id="8df62-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be `https://eastus2.azuredatabricks.net`.</span></span>

3. <span data-ttu-id="8df62-167">进入主机之后，系统会提示你输入令牌。</span><span class="sxs-lookup"><span data-stu-id="8df62-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="8df62-168">在 Azure 门户中，选择“启动工作区”以启动 Azure Databricks 工作区。</span><span class="sxs-lookup"><span data-stu-id="8df62-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![启动 Azure Databricks 工作区](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="8df62-170">在工作区主页上，选择“用户设置”。</span><span class="sxs-lookup"><span data-stu-id="8df62-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Azure Databricks 工作区中的“用户设置”](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="8df62-172">在“用户设置”页上，可以生成新的令牌。</span><span class="sxs-lookup"><span data-stu-id="8df62-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="8df62-173">复制生成的令牌，并将其粘贴回命令提示符。</span><span class="sxs-lookup"><span data-stu-id="8df62-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![在 Azure Databricks 工作区中生成新的访问令牌](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="8df62-175">现在，应可以访问创建的任何 Azure Databricks 群集，并将文件上传到 DBFS。</span><span class="sxs-lookup"><span data-stu-id="8df62-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="8df62-176">下载辅助角色依赖项</span><span class="sxs-lookup"><span data-stu-id="8df62-176">Download worker dependencies</span></span>

1. <span data-ttu-id="8df62-177">Microsoft.Spark.Worker 可帮助 Apache Spark 执行你的应用，例如你可能已编写的任何用户定义函数 (UDF)。</span><span class="sxs-lookup"><span data-stu-id="8df62-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="8df62-178">下载 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz)。</span><span class="sxs-lookup"><span data-stu-id="8df62-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="8df62-179">install-worker.sh 是一个脚本，可使用该脚本将 .NET for Apache Spark 依赖项文件复制到群集的节点中。</span><span class="sxs-lookup"><span data-stu-id="8df62-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="8df62-180">在本地计算机上创建一个名为 install-worker.sh 的新文件，并粘贴位于 GitHub 上的 [install-worker.sh 内容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh)。</span><span class="sxs-lookup"><span data-stu-id="8df62-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="8df62-181">db-init.sh 是用于将依赖项安装到 Databricks Spark 群集上的脚本。</span><span class="sxs-lookup"><span data-stu-id="8df62-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="8df62-182">在本地计算机上创建一个名为 db-init.sh 的新文件，并粘贴位于 GitHub 上的 [db-init.sh 内容](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh)。</span><span class="sxs-lookup"><span data-stu-id="8df62-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="8df62-183">在刚刚创建的文件中，将 `DOTNET_SPARK_RELEASE` 变量设置为 `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`。</span><span class="sxs-lookup"><span data-stu-id="8df62-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="8df62-184">按原样保留 db-init.sh 文件的其余部分。</span><span class="sxs-lookup"><span data-stu-id="8df62-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="8df62-185">如果使用 Windows，请验证 install-worker.sh 中的行尾和 db-init.sh 脚本是否为 Unix 样式 (LF) 。</span><span class="sxs-lookup"><span data-stu-id="8df62-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="8df62-186">可通过文本编辑器（例如，记事本++ 和 Atom）更改行尾。</span><span class="sxs-lookup"><span data-stu-id="8df62-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="8df62-187">发布你的应用</span><span class="sxs-lookup"><span data-stu-id="8df62-187">Publish your app</span></span>

<span data-ttu-id="8df62-188">接下来，发布在 [.NET for Apache Spark - 10 分钟入门](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)教程中创建的 mySparkApp，以确保 Spark 群集可以访问运行应用所需的所有文件。</span><span class="sxs-lookup"><span data-stu-id="8df62-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="8df62-189">运行以下命令以发布 mySparkApp：</span><span class="sxs-lookup"><span data-stu-id="8df62-189">Run the following commands to publish the *mySparkApp*:</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="8df62-190">执行以下任务以压缩已发布的应用文件，以便你可以轻松地将其上传到 Databricks Spark 群集。</span><span class="sxs-lookup"><span data-stu-id="8df62-190">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="8df62-191">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="8df62-191">**On Windows:**</span></span>

   <span data-ttu-id="8df62-192">导航到 mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64。</span><span class="sxs-lookup"><span data-stu-id="8df62-192">Navigate to mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64.</span></span> <span data-ttu-id="8df62-193">然后，右键单击“发布”文件夹，再选择“发送到”>“压缩文件夹” 。</span><span class="sxs-lookup"><span data-stu-id="8df62-193">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="8df62-194">将新文件夹命名为“publish.zip”。</span><span class="sxs-lookup"><span data-stu-id="8df62-194">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="8df62-195">**在 Linux 上，运行以下命令：**</span><span class="sxs-lookup"><span data-stu-id="8df62-195">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="8df62-196">上传文件</span><span class="sxs-lookup"><span data-stu-id="8df62-196">Upload files</span></span>

<span data-ttu-id="8df62-197">在本部分中，将多个文件上传到 DBFS，以便群集拥有在云中运行应用所需的一切。</span><span class="sxs-lookup"><span data-stu-id="8df62-197">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="8df62-198">每次将文件上传到 DBFS 时，请确保你位于该文件所在的计算机目录中。</span><span class="sxs-lookup"><span data-stu-id="8df62-198">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="8df62-199">运行以下命令，以将 db-init.sh、install-worker.sh 和 Microsoft.Spark.Worker 上传到 DBFS  ：</span><span class="sxs-lookup"><span data-stu-id="8df62-199">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="8df62-200">运行以下命令以上传群集运行应用所需的其余文件：已压缩的发布文件夹、input.txt 和 microsoft-spark-2.4.x-0.3.1.jar 。</span><span class="sxs-lookup"><span data-stu-id="8df62-200">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.1.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.1\ubuntu.16.04-x64 directory
   databricks fs cp publish.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="8df62-201">创建作业</span><span class="sxs-lookup"><span data-stu-id="8df62-201">Create a job</span></span>

<span data-ttu-id="8df62-202">应用通过运行 spark-submit（用于运行 .NET for Apache Spark 作业的命令）的作业在 Azure Databricks 上运行。</span><span class="sxs-lookup"><span data-stu-id="8df62-202">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="8df62-203">在 Azure Databricks 工作区中，选择“作业”图标，然后选择“+ 创建作业” 。</span><span class="sxs-lookup"><span data-stu-id="8df62-203">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![创建 Azure Databricks 作业](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="8df62-205">选择作业的标题，然后选择“配置 spark-submit”。</span><span class="sxs-lookup"><span data-stu-id="8df62-205">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![为 Databricks 作业配置 spark-submit](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="8df62-207">在作业配置中粘贴以下参数。</span><span class="sxs-lookup"><span data-stu-id="8df62-207">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="8df62-208">然后，选择“确认”。</span><span class="sxs-lookup"><span data-stu-id="8df62-208">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="8df62-209">创建群集</span><span class="sxs-lookup"><span data-stu-id="8df62-209">Create a cluster</span></span>

1. <span data-ttu-id="8df62-210">导航到作业并选择“编辑”以配置作业的群集。</span><span class="sxs-lookup"><span data-stu-id="8df62-210">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="8df62-211">将群集设置为“Spark 2.4.1”。</span><span class="sxs-lookup"><span data-stu-id="8df62-211">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="8df62-212">然后，选择“高级选项” > “Init 脚本” 。</span><span class="sxs-lookup"><span data-stu-id="8df62-212">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="8df62-213">将 Init 脚本路径设置为 `dbfs:/spark-dotnet/db-init.sh`。</span><span class="sxs-lookup"><span data-stu-id="8df62-213">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![在 Azure Databricks 中配置 Spark 群集](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="8df62-215">选择“确认”以确认群集设置。</span><span class="sxs-lookup"><span data-stu-id="8df62-215">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="8df62-216">运行你的应用</span><span class="sxs-lookup"><span data-stu-id="8df62-216">Run your app</span></span>

1. <span data-ttu-id="8df62-217">导航到作业并选择“立即运行”，在新配置的 Spark 群集上运行作业。</span><span class="sxs-lookup"><span data-stu-id="8df62-217">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="8df62-218">创建作业的群集需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="8df62-218">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="8df62-219">一旦创建完成，你的作业就会被提交，你可以查看输出。</span><span class="sxs-lookup"><span data-stu-id="8df62-219">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="8df62-220">从左侧菜单中选择“群集”，然后选择“名称”并运行作业。</span><span class="sxs-lookup"><span data-stu-id="8df62-220">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="8df62-221">选择“驱动程序日志”以查看作业的输出。</span><span class="sxs-lookup"><span data-stu-id="8df62-221">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="8df62-222">应用执行完毕后，你将在写入标准输出控制台的入门本地运行中看到相同的字数表。</span><span class="sxs-lookup"><span data-stu-id="8df62-222">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Azure Databricks 作业输出表](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="8df62-224">恭喜，你已在云中运行了第一个 .NET for Apache Spark 应用程序！</span><span class="sxs-lookup"><span data-stu-id="8df62-224">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="8df62-225">清理资源</span><span class="sxs-lookup"><span data-stu-id="8df62-225">Clean up resources</span></span>

<span data-ttu-id="8df62-226">如果不再需要 Databricks 工作区，可在 Azure 门户中删除 Azure Databricks 资源。</span><span class="sxs-lookup"><span data-stu-id="8df62-226">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="8df62-227">还可以选择资源组名称来打开“资源组”页，然后选择“删除资源组”。</span><span class="sxs-lookup"><span data-stu-id="8df62-227">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8df62-228">后续步骤</span><span class="sxs-lookup"><span data-stu-id="8df62-228">Next steps</span></span>

<span data-ttu-id="8df62-229">在本教程中，你已将 .NET for Apache Spark 应用程序部署到 Databricks。</span><span class="sxs-lookup"><span data-stu-id="8df62-229">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="8df62-230">要了解有关 Databricks 的详细信息，请继续阅读 Azure Databricks 文档。</span><span class="sxs-lookup"><span data-stu-id="8df62-230">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8df62-231">Azure Databricks 文档</span><span class="sxs-lookup"><span data-stu-id="8df62-231">Azure Databricks Documentation</span></span>](/azure/azure-databricks/)
