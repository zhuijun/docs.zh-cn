---
title: 将 .NET for Apache Spark 作业提交到 Azure HDInsight
description: 了解如何使用 spark-submit 和 Apache Livy 将 .NET for Apache Spark 作业提交到 Azure HDInsight。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: cb99cd8028d504924d2dd69910efed0065d0a2e2
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2020
ms.locfileid: "91954914"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="ffc6b-103">将 .NET for Apache Spark 作业提交到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="ffc6b-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="ffc6b-104">可通过两种方法将 .NET for Apache Spark 作业部署到 HDInsight：`spark-submit` 和 Apache Livy。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="ffc6b-105">使用 spark-submit 进行部署</span><span class="sxs-lookup"><span data-stu-id="ffc6b-105">Deploy using spark-submit</span></span>

<span data-ttu-id="ffc6b-106">可以使用 [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令将 .NET for Apache Spark 作业提交到 Azure HDInsight。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="ffc6b-107">导航到 Azure 门户中的 HDInsight Spark 群集，然后选择“SSH + 群集登录名”  。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="ffc6b-108">复制 ssh 登录信息，并将登录名粘贴到终端。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="ffc6b-109">使用在群集创建期间设置的密码登录到群集。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="ffc6b-110">应会看到“欢迎使用 Ubuntu 和 Spark”的消息。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="ffc6b-111">使用 spark-submit 命令在 HDInsight 群集上运行应用  。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="ffc6b-112">请记得将示例脚本中的 mycontainer 和 mystorageaccount 替换为 blob 容器和存储帐户的实际名称   。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="ffc6b-113">另外，请确保将 `microsoft-spark-2.3.x-0.6.0.jar` 替换为要用于部署的适当的 jar 文件。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="ffc6b-114">`2.3.x` 表示 Apache Spark 的版本，`0.6.0` 表示 [.NET for Apache Spark 辅助角色](https://github.com/dotnet/spark/releases)的版本。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="ffc6b-115">使用 Apache Livy 进行部署</span><span class="sxs-lookup"><span data-stu-id="ffc6b-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="ffc6b-116">可以使用 [Apache Livy](https://livy.incubator.apache.org/)（即 Apache Spark REST API）将 .NET for Apache Spark 作业提交到 Azure HDInsight Spark 群集。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="ffc6b-117">有关详细信息，请参阅[使用 Apache Livy 提交远程作业](/azure/hdinsight/spark/apache-spark-livy-rest-interface)。</span><span class="sxs-lookup"><span data-stu-id="ffc6b-117">For more information, see [Remote jobs with Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="ffc6b-118">可使用 `curl` 在 Linux 上运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ffc6b-118">You can run the following command on Linux using `curl`:</span></span>

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a><span data-ttu-id="ffc6b-119">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ffc6b-119">Next steps</span></span>

* [<span data-ttu-id="ffc6b-120">.NET for Apache Spark 入门</span><span class="sxs-lookup"><span data-stu-id="ffc6b-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="ffc6b-121">将 .NET for Apache Spark 应用程序部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="ffc6b-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="ffc6b-122">HDInsight 文档</span><span class="sxs-lookup"><span data-stu-id="ffc6b-122">HDInsight Documentation</span></span>](/azure/hdinsight/)
