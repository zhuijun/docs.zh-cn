---
title: 将 .NET for Apache Spark 应用程序部署到 Azure HDInsight
description: 了解如何将 .NET for Apache Spark 应用程序部署到 HDInsight。
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9a4ca80463de41a50d103c696b2108d0cef023fc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548372"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="c61c2-103">教程：将 .NET for Apache Spark 应用程序部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="c61c2-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="c61c2-104">本教程介绍如何通过 Azure HDInsight 群集将 .NET for Apache Spark 应用部署到云中。</span><span class="sxs-lookup"><span data-stu-id="c61c2-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="c61c2-105">由于 HDInsight 中的 Spark 群集与 Azure 存储和 Azure Data Lake Storage 兼容，因此使用 HDInsight，你可以更加容易地在 Azure 中创建和配置 Spark 群集。</span><span class="sxs-lookup"><span data-stu-id="c61c2-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="c61c2-106">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="c61c2-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="c61c2-107">使用 Azure 存储资源管理器访问存储帐户。</span><span class="sxs-lookup"><span data-stu-id="c61c2-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="c61c2-108">创建 Azure HDInsight 群集。</span><span class="sxs-lookup"><span data-stu-id="c61c2-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="c61c2-109">发布 .NET for Apache Spark 应用。</span><span class="sxs-lookup"><span data-stu-id="c61c2-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="c61c2-110">创建并运行 HDInsight 脚本操作。</span><span class="sxs-lookup"><span data-stu-id="c61c2-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="c61c2-111">在 HDInsight 群集上运行 .NET for Apache Spark 应用。</span><span class="sxs-lookup"><span data-stu-id="c61c2-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="c61c2-112">先决条件</span><span class="sxs-lookup"><span data-stu-id="c61c2-112">Prerequisites</span></span>

<span data-ttu-id="c61c2-113">开始之前，请完成以下任务：</span><span class="sxs-lookup"><span data-stu-id="c61c2-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="c61c2-114">如果还没有 Azure 订阅，可以创建一个[免费帐户](https://azure.microsoft.com/free/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="c61c2-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="c61c2-115">登录 [Azure 门户](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="c61c2-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="c61c2-116">在 [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409)、[Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409) 或 [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) 计算机上安装 Azure 存储资源管理器。</span><span class="sxs-lookup"><span data-stu-id="c61c2-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="c61c2-117">完成 [.NET for Apache Spark - 10 分钟入门](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)教程。</span><span class="sxs-lookup"><span data-stu-id="c61c2-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="c61c2-118">访问存储帐户</span><span class="sxs-lookup"><span data-stu-id="c61c2-118">Access your storage accounts</span></span>

1. <span data-ttu-id="c61c2-119">打开 Azure 存储资源管理器。</span><span class="sxs-lookup"><span data-stu-id="c61c2-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="c61c2-120">在左侧菜单上选择“添加帐户”，并登录到 Azure 帐户  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![从存储资源管理器登录 Azure 帐户](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="c61c2-122">登录后，应会看到你所拥有的所有存储帐户以及上传到存储帐户的所有资源。</span><span class="sxs-lookup"><span data-stu-id="c61c2-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="c61c2-123">创建 HDInsight 群集</span><span class="sxs-lookup"><span data-stu-id="c61c2-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c61c2-124">HDInsight 群集基于分钟按比例收费，即使你未使用它们也是如此。</span><span class="sxs-lookup"><span data-stu-id="c61c2-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="c61c2-125">请务必在使用完之后删除群集。</span><span class="sxs-lookup"><span data-stu-id="c61c2-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="c61c2-126">有关详细信息，请参阅本教程的[清理资源](#clean-up-resources)部分。</span><span class="sxs-lookup"><span data-stu-id="c61c2-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="c61c2-127">访问 [Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="c61c2-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="c61c2-128">选择“+ 创建资源”。 </span><span class="sxs-lookup"><span data-stu-id="c61c2-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="c61c2-129">然后，从“Analytics”类别中选择“HDInsight”   。</span><span class="sxs-lookup"><span data-stu-id="c61c2-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![从 Azure 门户创建 HDInsight 资源](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="c61c2-131">在“基本”下，提供以下值  ：</span><span class="sxs-lookup"><span data-stu-id="c61c2-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="c61c2-132">Property</span><span class="sxs-lookup"><span data-stu-id="c61c2-132">Property</span></span>  |<span data-ttu-id="c61c2-133">描述</span><span class="sxs-lookup"><span data-stu-id="c61c2-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="c61c2-134">订阅</span><span class="sxs-lookup"><span data-stu-id="c61c2-134">Subscription</span></span>  | <span data-ttu-id="c61c2-135">从下拉列表中选择一个可用 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="c61c2-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="c61c2-136">资源组</span><span class="sxs-lookup"><span data-stu-id="c61c2-136">Resource group</span></span> | <span data-ttu-id="c61c2-137">指定是要创建新的资源组还是使用现有的资源组。</span><span class="sxs-lookup"><span data-stu-id="c61c2-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="c61c2-138">资源组是用于保存 Azure 解决方案相关资源的容器。</span><span class="sxs-lookup"><span data-stu-id="c61c2-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="c61c2-139">群集名称</span><span class="sxs-lookup"><span data-stu-id="c61c2-139">Cluster name</span></span> | <span data-ttu-id="c61c2-140">为 HDInsight Spark 群集命名。</span><span class="sxs-lookup"><span data-stu-id="c61c2-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="c61c2-141">位置</span><span class="sxs-lookup"><span data-stu-id="c61c2-141">Location</span></span>   | <span data-ttu-id="c61c2-142">选择资源组的位置。</span><span class="sxs-lookup"><span data-stu-id="c61c2-142">Select a location for the resource group.</span></span> <span data-ttu-id="c61c2-143">模板将此位置用于创建群集，以及用于默认群集存储。</span><span class="sxs-lookup"><span data-stu-id="c61c2-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="c61c2-144">群集类型</span><span class="sxs-lookup"><span data-stu-id="c61c2-144">Cluster type</span></span>| <span data-ttu-id="c61c2-145">选择“Spark”作为群集类型。 </span><span class="sxs-lookup"><span data-stu-id="c61c2-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="c61c2-146">群集版本</span><span class="sxs-lookup"><span data-stu-id="c61c2-146">Cluster version</span></span>|<span data-ttu-id="c61c2-147">选择群集类型后，此字段中将自动填充默认版本。</span><span class="sxs-lookup"><span data-stu-id="c61c2-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="c61c2-148">选择 2.3 或 2.4 版本的 Spark。</span><span class="sxs-lookup"><span data-stu-id="c61c2-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="c61c2-149">群集登录用户名</span><span class="sxs-lookup"><span data-stu-id="c61c2-149">Cluster login username</span></span>| <span data-ttu-id="c61c2-150">输入群集登录用户名。</span><span class="sxs-lookup"><span data-stu-id="c61c2-150">Enter the cluster login username.</span></span>  <span data-ttu-id="c61c2-151">默认名称为 *admin*。</span><span class="sxs-lookup"><span data-stu-id="c61c2-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="c61c2-152">群集登录密码</span><span class="sxs-lookup"><span data-stu-id="c61c2-152">Cluster login password</span></span>| <span data-ttu-id="c61c2-153">输入任何登录密码。</span><span class="sxs-lookup"><span data-stu-id="c61c2-153">Enter any login password.</span></span> |
    |<span data-ttu-id="c61c2-154">安全外壳 (SSH) 用户名</span><span class="sxs-lookup"><span data-stu-id="c61c2-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="c61c2-155">输入 SSH 用户名。</span><span class="sxs-lookup"><span data-stu-id="c61c2-155">Enter the SSH username.</span></span> <span data-ttu-id="c61c2-156">默认情况下，此帐户的密码与群集登录用户名帐户的密码相同  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="c61c2-157">在完成时选择“下一步:  存储 >>”转到“存储”页  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="c61c2-158">在“存储”下，提供以下值  ：</span><span class="sxs-lookup"><span data-stu-id="c61c2-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="c61c2-159">Property</span><span class="sxs-lookup"><span data-stu-id="c61c2-159">Property</span></span>  |<span data-ttu-id="c61c2-160">描述</span><span class="sxs-lookup"><span data-stu-id="c61c2-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="c61c2-161">主存储类型</span><span class="sxs-lookup"><span data-stu-id="c61c2-161">Primary storage type</span></span>|<span data-ttu-id="c61c2-162">使用默认值“Azure 存储”。 </span><span class="sxs-lookup"><span data-stu-id="c61c2-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="c61c2-163">选择方法</span><span class="sxs-lookup"><span data-stu-id="c61c2-163">Selection method</span></span>|<span data-ttu-id="c61c2-164">使用默认值“从列表中选择”。 </span><span class="sxs-lookup"><span data-stu-id="c61c2-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="c61c2-165">主存储帐户</span><span class="sxs-lookup"><span data-stu-id="c61c2-165">Primary storage account</span></span>|<span data-ttu-id="c61c2-166">选择订阅以及该订阅中的可用存储帐户。</span><span class="sxs-lookup"><span data-stu-id="c61c2-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="c61c2-167">容器</span><span class="sxs-lookup"><span data-stu-id="c61c2-167">Container</span></span>|<span data-ttu-id="c61c2-168">此容器是存储帐户中特定的 blob 容器，群集在该容器中查找文件以在云中运行应用。</span><span class="sxs-lookup"><span data-stu-id="c61c2-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="c61c2-169">可使用任何可用名称为其命名。</span><span class="sxs-lookup"><span data-stu-id="c61c2-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="c61c2-170">在“查看 + 创建”下，选择“创建”。  </span><span class="sxs-lookup"><span data-stu-id="c61c2-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="c61c2-171">创建群集大约需要 20 分钟时间。</span><span class="sxs-lookup"><span data-stu-id="c61c2-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="c61c2-172">必须先创建群集，才能继续执行下一步。</span><span class="sxs-lookup"><span data-stu-id="c61c2-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="c61c2-173">发布你的应用</span><span class="sxs-lookup"><span data-stu-id="c61c2-173">Publish your app</span></span>

<span data-ttu-id="c61c2-174">接下来，发布在 [.NET for Apache Spark - 10 分钟入门](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)教程中创建的 mySparkApp，以便 Spark 群集可以访问运行应用所需的所有文件  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="c61c2-175">运行以下命令以发布 mySparkApp  ：</span><span class="sxs-lookup"><span data-stu-id="c61c2-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="c61c2-176">在 Windows 上： </span><span class="sxs-lookup"><span data-stu-id="c61c2-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="c61c2-177">**在 Linux 上：**</span><span class="sxs-lookup"><span data-stu-id="c61c2-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="c61c2-178">执行以下任务以压缩已发布的应用文件，以便你可以轻松地将其上传到 HDInsight 群集。</span><span class="sxs-lookup"><span data-stu-id="c61c2-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="c61c2-179">在 Windows 上： </span><span class="sxs-lookup"><span data-stu-id="c61c2-179">**On Windows:**</span></span>

   <span data-ttu-id="c61c2-180">导航到 mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="c61c2-181">然后，右键单击“发布”文件夹，再选择“发送到”>“压缩文件夹”   。</span><span class="sxs-lookup"><span data-stu-id="c61c2-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="c61c2-182">将新文件夹命名为“publish.zip”  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="c61c2-183">**在 Linux 上，运行以下命令：**</span><span class="sxs-lookup"><span data-stu-id="c61c2-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="c61c2-184">将文件上传到 Azure</span><span class="sxs-lookup"><span data-stu-id="c61c2-184">Upload files to Azure</span></span>

<span data-ttu-id="c61c2-185">接下来，使用 Azure 存储资源管理器将以下五个文件上传到为群集存储选择的 blob 容器中：</span><span class="sxs-lookup"><span data-stu-id="c61c2-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="c61c2-186">Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="c61c2-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="c61c2-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="c61c2-187">install-worker.sh</span></span>
* <span data-ttu-id="c61c2-188">publish.zip</span><span class="sxs-lookup"><span data-stu-id="c61c2-188">publish.zip</span></span>
* <span data-ttu-id="c61c2-189">microsoft-spark-2.3.x-0.3.0.jar</span><span class="sxs-lookup"><span data-stu-id="c61c2-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="c61c2-190">input.txt。</span><span class="sxs-lookup"><span data-stu-id="c61c2-190">input.txt.</span></span>

1. <span data-ttu-id="c61c2-191">打开 Azure 存储资源管理器，然后从左侧菜单导航到存储帐户。</span><span class="sxs-lookup"><span data-stu-id="c61c2-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="c61c2-192">在存储帐户中的“Blob 容器”下，向下钻取到群集的 blob 容器  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="c61c2-193">Microsoft.Spark.Worker 可帮助 Apache Spark 执行你的应用，例如你可能已编写的任何用户定义函数 (UDF)  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="c61c2-194">下载 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz)。</span><span class="sxs-lookup"><span data-stu-id="c61c2-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="c61c2-195">然后，在 Azure 存储资源管理器中选择“上传”以上传辅助角色  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![将文件上传到 Azure 存储资源管理器](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="c61c2-197">install-worker.sh 是一个脚本，可使用该脚本将 .NET for Apache Spark 依赖项文件复制到群集的节点中  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="c61c2-198">在本地计算机上创建一个名为 install-worker.sh 的新文件，并粘贴位于 GitHub 上的 [install-worker.sh 内容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh)  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="c61c2-199">然后，将 install-worker.sh 上传到 blob 容器中  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="c61c2-200">群集需要 publish.zip 文件，后者包含应用的已发布文件。</span><span class="sxs-lookup"><span data-stu-id="c61c2-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="c61c2-201">导航到已发布文件夹“mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64”，并找到“publish.zip”   。</span><span class="sxs-lookup"><span data-stu-id="c61c2-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="c61c2-202">然后，将 publish.zip 上传到 blob 容器  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="c61c2-203">群集需要已打包到 jar 文件中的应用程序代码。</span><span class="sxs-lookup"><span data-stu-id="c61c2-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="c61c2-204">导航到已发布文件夹“mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64”，并找到“microsoft-spark-2.3.x-0.3.0.jar”   。</span><span class="sxs-lookup"><span data-stu-id="c61c2-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="c61c2-205">然后，将 jar 文件上传到 blob 容器。</span><span class="sxs-lookup"><span data-stu-id="c61c2-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="c61c2-206">对于 2.3.x 和 2.4.x 版的 Spark，可能存在多个 .jar 文件。</span><span class="sxs-lookup"><span data-stu-id="c61c2-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="c61c2-207">你需要选择与在群集创建期间选择的 Spark 版本相匹配的 .jar 文件。</span><span class="sxs-lookup"><span data-stu-id="c61c2-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="c61c2-208">例如，如果在群集创建期间选择了 Spark 2.3.2，请选择 microsoft-spark-2.3.x-0.3.0.jar  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="c61c2-209">群集需要应用的输入。</span><span class="sxs-lookup"><span data-stu-id="c61c2-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="c61c2-210">导航到 mySparkApp 目录，并找到“input.txt”   。</span><span class="sxs-lookup"><span data-stu-id="c61c2-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="c61c2-211">将输入文件上传到 blob 容器中的 user/sshuser 目录  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="c61c2-212">你将通过 ssh 连接到群集，群集将在此文件夹中查找其输入。</span><span class="sxs-lookup"><span data-stu-id="c61c2-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="c61c2-213">input.txt 文件是上传到特定目录的唯一文件  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="c61c2-214">运行 HDInsight 脚本操作</span><span class="sxs-lookup"><span data-stu-id="c61c2-214">Run the HDInsight script action</span></span>

<span data-ttu-id="c61c2-215">群集运行并将文件上传到 Azure 后，可在群集上运行 install-worker.sh 脚本  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="c61c2-216">导航到 Azure 门户中的 HDInsight Spark 群集，然后选择“脚本操作”  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="c61c2-217">选择“+ 提交新脚本”并提供以下值  ：</span><span class="sxs-lookup"><span data-stu-id="c61c2-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="c61c2-218">Property</span><span class="sxs-lookup"><span data-stu-id="c61c2-218">Property</span></span>  |<span data-ttu-id="c61c2-219">描述</span><span class="sxs-lookup"><span data-stu-id="c61c2-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="c61c2-220">脚本类型</span><span class="sxs-lookup"><span data-stu-id="c61c2-220">Script type</span></span> |<span data-ttu-id="c61c2-221">自定义</span><span class="sxs-lookup"><span data-stu-id="c61c2-221">Custom</span></span>|
   | <span data-ttu-id="c61c2-222">“属性”</span><span class="sxs-lookup"><span data-stu-id="c61c2-222">Name</span></span> | <span data-ttu-id="c61c2-223">安装辅助角色</span><span class="sxs-lookup"><span data-stu-id="c61c2-223">Install Worker</span></span>|
   | <span data-ttu-id="c61c2-224">Bash 脚本 URI</span><span class="sxs-lookup"><span data-stu-id="c61c2-224">Bash script URI</span></span> |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> <span data-ttu-id="c61c2-225">要确认此 URI，请在 Azure 存储资源管理器中右键单击“install-worker.sh”，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="c61c2-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="c61c2-226">节点类型</span><span class="sxs-lookup"><span data-stu-id="c61c2-226">Node type(s)</span></span>| <span data-ttu-id="c61c2-227">辅助角色</span><span class="sxs-lookup"><span data-stu-id="c61c2-227">Worker</span></span>|
   | <span data-ttu-id="c61c2-228">参数</span><span class="sxs-lookup"><span data-stu-id="c61c2-228">Parameters</span></span> | <span data-ttu-id="c61c2-229">azure</span><span class="sxs-lookup"><span data-stu-id="c61c2-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="c61c2-230">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="c61c2-230">/usr/local/bin</span></span>

3. <span data-ttu-id="c61c2-231">选择“创建”，提交脚本  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="c61c2-232">运行你的应用</span><span class="sxs-lookup"><span data-stu-id="c61c2-232">Run your app</span></span>

1. <span data-ttu-id="c61c2-233">导航到 Azure 门户中的 HDInsight Spark 群集，然后选择“SSH + 群集登录名”  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="c61c2-234">复制 ssh 登录信息，并将登录名粘贴到终端。</span><span class="sxs-lookup"><span data-stu-id="c61c2-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="c61c2-235">使用在群集创建期间设置的密码登录到群集。</span><span class="sxs-lookup"><span data-stu-id="c61c2-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="c61c2-236">应会看到“欢迎使用 Ubuntu 和 Spark”的消息。</span><span class="sxs-lookup"><span data-stu-id="c61c2-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="c61c2-237">使用 spark-submit 命令在 HDInsight 群集上运行应用  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="c61c2-238">请记得将示例脚本中的 mycontainer 和 mystorageaccount 替换为 blob 容器和存储帐户的实际名称   。</span><span class="sxs-lookup"><span data-stu-id="c61c2-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="c61c2-239">应用运行时，你将在写入控制台的“本地运行入门”中看到相同的字数表。</span><span class="sxs-lookup"><span data-stu-id="c61c2-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="c61c2-240">恭喜，你已在云中运行了第一个 .NET for Apache Spark 应用程序！</span><span class="sxs-lookup"><span data-stu-id="c61c2-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="c61c2-241">清理资源</span><span class="sxs-lookup"><span data-stu-id="c61c2-241">Clean up resources</span></span>

<span data-ttu-id="c61c2-242">HDInsight 将数据保存在 Azure 存储中，因此可以在不使用群集时放心将其删除。</span><span class="sxs-lookup"><span data-stu-id="c61c2-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="c61c2-243">此外，还需要为 HDInsight 群集付费，即使不用也是如此。</span><span class="sxs-lookup"><span data-stu-id="c61c2-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="c61c2-244">由于群集费用数倍于存储空间费用，因此在群集不用时删除群集可以节省费用。</span><span class="sxs-lookup"><span data-stu-id="c61c2-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="c61c2-245">还可以选择资源组名称来打开“资源组”页，然后选择“删除资源组”  。</span><span class="sxs-lookup"><span data-stu-id="c61c2-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="c61c2-246">通过删除资源组，可以删除 HDInsight Spark 群集和默认存储帐户。</span><span class="sxs-lookup"><span data-stu-id="c61c2-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c61c2-247">后续步骤</span><span class="sxs-lookup"><span data-stu-id="c61c2-247">Next steps</span></span>

<span data-ttu-id="c61c2-248">在本教程中，你已将 .NET for Apache Spark 应用程序部署到 Azure HDInsight。</span><span class="sxs-lookup"><span data-stu-id="c61c2-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="c61c2-249">要了解有关 HDInsight 的详细信息，请继续阅读 Azure HDInsight 文档。</span><span class="sxs-lookup"><span data-stu-id="c61c2-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c61c2-250">Azure HDInsight 文档</span><span class="sxs-lookup"><span data-stu-id="c61c2-250">Azure HDInsight Documentation</span></span>](/azure/hdinsight/)
