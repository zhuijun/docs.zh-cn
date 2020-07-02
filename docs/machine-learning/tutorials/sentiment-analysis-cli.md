---
title: 使用 ML.NET CLI 分析情绪
description: 从示例数据集自动生成 ML 模型和相关 C# 代码
author: cesardl
ms.author: cesardl
ms.date: 06/03/2020
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: fcd325d518b276ccb042f3702db978e9189715b8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85326020"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="3f62c-103">使用 ML.NET CLI 分析情绪</span><span class="sxs-lookup"><span data-stu-id="3f62c-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="3f62c-104">了解如何使用 ML.NET CLI 自动生成 ML.NET 模型和基础 C# 代码。</span><span class="sxs-lookup"><span data-stu-id="3f62c-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="3f62c-105">用户提供想要实现的数据集和机器学习任务，CLI 使用 AutoML 引擎创建模型生成和部署源代码以及分类模型。</span><span class="sxs-lookup"><span data-stu-id="3f62c-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the classification model.</span></span>

<span data-ttu-id="3f62c-106">在本教程中，将执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="3f62c-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="3f62c-107">为选定的机器学习任务准备数据</span><span class="sxs-lookup"><span data-stu-id="3f62c-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="3f62c-108">从 CLI 运行“mlnet classification”命令</span><span class="sxs-lookup"><span data-stu-id="3f62c-108">Run the 'mlnet classification' command from the CLI</span></span>
> - <span data-ttu-id="3f62c-109">查看质量指标结果</span><span class="sxs-lookup"><span data-stu-id="3f62c-109">Review the quality metric results</span></span>
> - <span data-ttu-id="3f62c-110">了解生成的 C# 代码，以在应用程序中使用模型</span><span class="sxs-lookup"><span data-stu-id="3f62c-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="3f62c-111">探索生成用于训练模型的 C# 代码</span><span class="sxs-lookup"><span data-stu-id="3f62c-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="3f62c-112">本主题涉及目前处于预览状态的 ML.NET CLI 工具，且材料可能会有所变化。</span><span class="sxs-lookup"><span data-stu-id="3f62c-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="3f62c-113">有关详细信息，请访问 [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) 页。</span><span class="sxs-lookup"><span data-stu-id="3f62c-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="3f62c-114">ML.NET CLI 是 ML.NET 的一部分，其主要目标是在学习 ML.NET 时为 .NET 开发人员“普及”ML.NET，以便无需从头编写代码即可开始使用。</span><span class="sxs-lookup"><span data-stu-id="3f62c-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="3f62c-115">可以在任何命令提示符（Windows、Mac 或 Linux）上运行 ML.NET CLI，以根据提供的训练数据集生成高质量的 ML.NET 模型和源代码。</span><span class="sxs-lookup"><span data-stu-id="3f62c-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="3f62c-116">先决条件</span><span class="sxs-lookup"><span data-stu-id="3f62c-116">Pre-requisites</span></span>

- <span data-ttu-id="3f62c-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="3f62c-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) or later</span></span>
- <span data-ttu-id="3f62c-118">（可选）[Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="3f62c-118">(Optional) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="3f62c-119">ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="3f62c-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="3f62c-120">可以通过 Visual Studio 或使用 `dotnet run` (.NET Core CLI) 运行生成的 C# 代码项目。</span><span class="sxs-lookup"><span data-stu-id="3f62c-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="3f62c-121">准备数据</span><span class="sxs-lookup"><span data-stu-id="3f62c-121">Prepare your data</span></span>

<span data-ttu-id="3f62c-122">我们将使用用于“情绪分析”方案（二元分类机器学习任务）的现有数据集。</span><span class="sxs-lookup"><span data-stu-id="3f62c-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="3f62c-123">用户可以通过类似的方式使用自己的数据集，系统将为用户生成模型和代码。</span><span class="sxs-lookup"><span data-stu-id="3f62c-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="3f62c-124">下载 [UCI Sentiment Labeled Sentences 数据集 zip 文件（参见以下备注中的引文）](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)并在选择的任何文件夹中解压缩文件。</span><span class="sxs-lookup"><span data-stu-id="3f62c-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f62c-125">本教程使用的数据集摘自 KDD 2015 中由 Kotzias 等提出的“From Group to Individual Labels using Deep Features”，</span><span class="sxs-lookup"><span data-stu-id="3f62c-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="3f62c-126">并托管在 UCI 机器学习存储库中（Dua, D. 和 Karra Taniskidou, E.(2017)）。</span><span class="sxs-lookup"><span data-stu-id="3f62c-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="3f62c-127">UCI 机器学习存储库 [http://archive.ics.uci.edu/ml ]。</span><span class="sxs-lookup"><span data-stu-id="3f62c-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="3f62c-128">加利福尼亚州，加利福尼亚大学：欧文分校，信息与计算机科学学院。</span><span class="sxs-lookup"><span data-stu-id="3f62c-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="3f62c-129">将 `yelp_labelled.txt` 文件复制到之前创建的任何文件夹（例如 `/cli-test`）。</span><span class="sxs-lookup"><span data-stu-id="3f62c-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="3f62c-130">打开首选命令提示符并移至复制数据集文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="3f62c-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="3f62c-131">例如：</span><span class="sxs-lookup"><span data-stu-id="3f62c-131">For example:</span></span>

    ```console
    cd /cli-test
    ```

    <span data-ttu-id="3f62c-132">使用任何文本编辑器（例如 Visual Studio Code）都可以打开并浏览 `yelp_labelled.txt` 数据集文件。</span><span class="sxs-lookup"><span data-stu-id="3f62c-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="3f62c-133">可以看到结构：</span><span class="sxs-lookup"><span data-stu-id="3f62c-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="3f62c-134">文件没有标头。</span><span class="sxs-lookup"><span data-stu-id="3f62c-134">The file has no header.</span></span> <span data-ttu-id="3f62c-135">将使用列的索引。</span><span class="sxs-lookup"><span data-stu-id="3f62c-135">You will use the column's index.</span></span>

    - <span data-ttu-id="3f62c-136">只有两列：</span><span class="sxs-lookup"><span data-stu-id="3f62c-136">There are just two columns:</span></span>

        | <span data-ttu-id="3f62c-137">文本（列索引 0）</span><span class="sxs-lookup"><span data-stu-id="3f62c-137">Text (Column index 0)</span></span> | <span data-ttu-id="3f62c-138">标签（列索引 1）</span><span class="sxs-lookup"><span data-stu-id="3f62c-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="3f62c-139">哇...喜欢这个地方。</span><span class="sxs-lookup"><span data-stu-id="3f62c-139">Wow... Loved this place.</span></span> | <span data-ttu-id="3f62c-140">1</span><span class="sxs-lookup"><span data-stu-id="3f62c-140">1</span></span> |
        | <span data-ttu-id="3f62c-141">酥皮不行。</span><span class="sxs-lookup"><span data-stu-id="3f62c-141">Crust is not good.</span></span> | <span data-ttu-id="3f62c-142">0</span><span class="sxs-lookup"><span data-stu-id="3f62c-142">0</span></span> |
        | <span data-ttu-id="3f62c-143">不够高雅，纹理令人反感。</span><span class="sxs-lookup"><span data-stu-id="3f62c-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="3f62c-144">0</span><span class="sxs-lookup"><span data-stu-id="3f62c-144">0</span></span> |
        | <span data-ttu-id="3f62c-145">...更多文本行...</span><span class="sxs-lookup"><span data-stu-id="3f62c-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="3f62c-146">...（1 或 0）...</span><span class="sxs-lookup"><span data-stu-id="3f62c-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="3f62c-147">确保从编辑器中关闭数据集文件。</span><span class="sxs-lookup"><span data-stu-id="3f62c-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="3f62c-148">现在，已准备好开始将 CLI 用于此“情绪分析”方案。</span><span class="sxs-lookup"><span data-stu-id="3f62c-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f62c-149">完成本教程后，还可以尝试使用自己的数据集，前提是它们可供用于 ML.NET CLI 预览版目前支持的任何 ML 任务，即“二元分类”、“分类”、“回归”和“建议” 。</span><span class="sxs-lookup"><span data-stu-id="3f62c-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Classification', 'Regression',* and *'Recommendation'*.</span></span>

## <a name="run-the-mlnet-classification-command"></a><span data-ttu-id="3f62c-150">运行“mlnet classification”命令</span><span class="sxs-lookup"><span data-stu-id="3f62c-150">Run the 'mlnet classification' command</span></span>

1. <span data-ttu-id="3f62c-151">运行以下 ML.NET CLI 命令：</span><span class="sxs-lookup"><span data-stu-id="3f62c-151">Run the following ML.NET CLI command:</span></span>

    ```console
    mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
    ```

    <span data-ttu-id="3f62c-152">此命令运行 **`mlnet classification` 命令**：</span><span class="sxs-lookup"><span data-stu-id="3f62c-152">This command runs the **`mlnet classification` command**:</span></span>
    - <span data-ttu-id="3f62c-153">对于“分类”的“ML 任务”</span><span class="sxs-lookup"><span data-stu-id="3f62c-153">for the **ML task** of *classification*</span></span>
    - <span data-ttu-id="3f62c-154">使用**数据集文件 `yelp_labelled.txt`** 作为训练和测试数据集（CLI 在内部将使用交叉验证或将其拆分为两个数据集，一个用于训练，另一个用于测试）</span><span class="sxs-lookup"><span data-stu-id="3f62c-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="3f62c-155">想要预测的**目的/目标列**（通常称为 **“标签”** ）是**索引为 1 的列**（这是第二列，因为索引从 0 开始）</span><span class="sxs-lookup"><span data-stu-id="3f62c-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="3f62c-156">**不使用带有列名的文件标头**，因为此特定数据集文件没有标头</span><span class="sxs-lookup"><span data-stu-id="3f62c-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="3f62c-157">试验的“目标探索/训练时间”为 10 秒 </span><span class="sxs-lookup"><span data-stu-id="3f62c-157">the **targeted exploration/train time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="3f62c-158">将看到 CLI 的输出，类似于：</span><span class="sxs-lookup"><span data-stu-id="3f62c-158">You will see output from the CLI, similar to:</span></span>

    ![PowerShell 上的 ML.NET CLI 分类](./media/mlnet-cli/mlnet-classification-powershell.gif)

    <span data-ttu-id="3f62c-160">在此特殊情况下，只需 10 秒且只需提供小型数据集，CLI 工具就能够运行相当多次迭代，这意味着基于不同的算法/配置组合，以及不同的内部数据转换和算法的超参数进行多次训练。</span><span class="sxs-lookup"><span data-stu-id="3f62c-160">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span>

    <span data-ttu-id="3f62c-161">最后，10 秒内找到的“最佳质量”模型是使用具有任何特定配置的特定训练程序/算法的模型。</span><span class="sxs-lookup"><span data-stu-id="3f62c-161">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="3f62c-162">根据探索时间，命令可以生成不同的结果。</span><span class="sxs-lookup"><span data-stu-id="3f62c-162">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="3f62c-163">选择基于显示的多个指标，例如 `Accuracy`。</span><span class="sxs-lookup"><span data-stu-id="3f62c-163">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="3f62c-164">**了解模型的质量指标**</span><span class="sxs-lookup"><span data-stu-id="3f62c-164">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="3f62c-165">评估二元分类模型的第一个指标（同时也是最简单的指标）是准确性，该指标易于理解。</span><span class="sxs-lookup"><span data-stu-id="3f62c-165">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="3f62c-166">“准确性指正确预测与测试数据集的比例。”</span><span class="sxs-lookup"><span data-stu-id="3f62c-166">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="3f62c-167">越接近 100% (1.00) 越好。</span><span class="sxs-lookup"><span data-stu-id="3f62c-167">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="3f62c-168">但是，存在仅使用准确性指标进行测量达不到要求的情况，特别是当测试数据集中的标签（在本例中为 0 和 1）处于非平衡状态时。</span><span class="sxs-lookup"><span data-stu-id="3f62c-168">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="3f62c-169">如需其他指标和更多**有关指标的详细信息**（例如准确性、AUC、AUCPR 以及用于评估不同模型的 F1 分数），请参阅[了解 ML.NET 指标](../resources/metrics.md)。</span><span class="sxs-lookup"><span data-stu-id="3f62c-169">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, and F1-score used to evaluate the different models, see [Understanding ML.NET metrics](../resources/metrics.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f62c-170">可以尝试使用完全相同的数据集并为 `--max-exploration-time` 指定数分钟时间（例如三分钟，因此指定 180 秒），这将找到一个更好的“最佳模型”，其具有用于此数据集（非常小，1,000 行）的不同训练管道配置。</span><span class="sxs-lookup"><span data-stu-id="3f62c-170">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span>

    <span data-ttu-id="3f62c-171">为了找到针对较大数据集的“生产就绪模型”“最佳/优质”模型，应该使用 CLI 进行试验，其通常根据数据集的大小指定更多探索时间。</span><span class="sxs-lookup"><span data-stu-id="3f62c-171">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="3f62c-172">实际上，在许多情况下，可能需要进行多个小时的探索，特别是在数据集的行数和列数很多的情况下。</span><span class="sxs-lookup"><span data-stu-id="3f62c-172">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span>

1. <span data-ttu-id="3f62c-173">之前的命令执行生成了以下资产：</span><span class="sxs-lookup"><span data-stu-id="3f62c-173">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="3f62c-174">可供使用的序列化模型 .zip 文件（“最佳模型”）。</span><span class="sxs-lookup"><span data-stu-id="3f62c-174">A serialized model .zip ("best model") ready to use.</span></span>
    - <span data-ttu-id="3f62c-175">用于运行生成的模型/对生成的模型评分的 C# 代码（使用该模型在最终用户应用中进行预测）。</span><span class="sxs-lookup"><span data-stu-id="3f62c-175">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="3f62c-176">用于生成模型的 C# 训练代码（学习目的）。</span><span class="sxs-lookup"><span data-stu-id="3f62c-176">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="3f62c-177">具有探索过的所有迭代的日志文件，其中包含有关使用其超参数和数据转换组合尝试过的每个算法的特定详细信息。</span><span class="sxs-lookup"><span data-stu-id="3f62c-177">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span>

    <span data-ttu-id="3f62c-178">前两个资产（.zip 文件模型和用于运行该模型的 C# 代码）可以直接用于最终用户应用（ASP.NET Core Web 应用、服务、桌面应用等），以使用生成的 ML 模型进行预测。</span><span class="sxs-lookup"><span data-stu-id="3f62c-178">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="3f62c-179">第三个资产（训练代码）显示 CLI 用于训练生成的模型的 ML.NET API 代码，因此可以研究 CLI 选择的特定训练程序/算法和超参数。</span><span class="sxs-lookup"><span data-stu-id="3f62c-179">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="3f62c-180">这些枚举资产将在本教程的后续步骤中进行说明。</span><span class="sxs-lookup"><span data-stu-id="3f62c-180">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="3f62c-181">浏览生成的 C# 代码，该代码用于运行模型以进行预测</span><span class="sxs-lookup"><span data-stu-id="3f62c-181">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="3f62c-182">在 Visual Studio（2017 或 2019）中，打开在原始目标文件夹（在教程中命名为 `/cli-test`）内名为 `SampleClassification` 的文件夹中生成的解决方案。</span><span class="sxs-lookup"><span data-stu-id="3f62c-182">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="3f62c-183">应该看到类似于如下的解决方案：</span><span class="sxs-lookup"><span data-stu-id="3f62c-183">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f62c-184">在本教程中，我们建议使用 Visual Studio，但也可以使用任何文本编辑器浏览生成的 C# 代码（两个项目），并在 macOS、Linux 或 Windows 计算机上使用 `dotnet CLI` 运行生成的控制台应用。</span><span class="sxs-lookup"><span data-stu-id="3f62c-184">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![CLI 生成的 VS 解决方案](./media/mlnet-cli/mlnet-cli-solution-explorer.png)

    - <span data-ttu-id="3f62c-186">生成的**类库**（包含序列化 ML 模型（.zip 文件）和数据类（数据模型））可以直接用于最终用户应用程序，甚至可以通过直接引用该类库（或根据需要移动代码）进行使用。</span><span class="sxs-lookup"><span data-stu-id="3f62c-186">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="3f62c-187">生成的**控制台应用**包含必须查看的执行代码，随后通常会重用“评分代码”（运行 ML 模型以进行预测的代码），方法是将该简单代码（仅几行）移至想要进行预测的最终用户应用程序。</span><span class="sxs-lookup"><span data-stu-id="3f62c-187">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span>

1. <span data-ttu-id="3f62c-188">打开类库项目中的 ModelInput.cs  和 ModelOutput.cs  类文件。</span><span class="sxs-lookup"><span data-stu-id="3f62c-188">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="3f62c-189">可发现这些类是用于保存数据的“数据类”或 POCO 类。</span><span class="sxs-lookup"><span data-stu-id="3f62c-189">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="3f62c-190">它是“样板代码”，但如果数据集有数十甚至数百列，则生成它很有用。</span><span class="sxs-lookup"><span data-stu-id="3f62c-190">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span>
    - <span data-ttu-id="3f62c-191">从数据集中读取数据时使用 `ModelInput` 类。</span><span class="sxs-lookup"><span data-stu-id="3f62c-191">The `ModelInput` class is used when reading data from the dataset.</span></span>
    - <span data-ttu-id="3f62c-192">`ModelOutput` 类用于获取预测结果（预测数据）。</span><span class="sxs-lookup"><span data-stu-id="3f62c-192">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="3f62c-193">打开 Program.cs 文件并浏览代码。</span><span class="sxs-lookup"><span data-stu-id="3f62c-193">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="3f62c-194">只需几行，就能够运行模型并进行示例预测。</span><span class="sxs-lookup"><span data-stu-id="3f62c-194">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        // Create single instance of sample data from first line of dataset for model input
        ModelInput sampleData = new ModelInput()
        {
            Col0 = @"Wow... Loved this place.",
        };

        // Make a single prediction on the sample data and print results
        var predictionResult = ConsumeModel.Predict(sampleData);

        Console.WriteLine("Using model to make single prediction -- Comparing actual Col1 with predicted Col1 from sample data...\n\n");
        Console.WriteLine($"Col0: {sampleData.Col0}");
        Console.WriteLine($"\n\nPredicted Col1 value {predictionResult.Prediction} \nPredicted Col1 scores: [{String.Join(",", predictionResult.Score)}]\n\n");
        Console.WriteLine("=============== End of process, hit any key to finish ===============");
        Console.ReadKey();
    }
    ```

    - 第一行代码创建一个样本数据，在本例中基于数据集的第一行用于预测。 <span data-ttu-id="3f62c-196">还可以通过更新代码来创建自己的硬编码数据：</span><span class="sxs-lookup"><span data-stu-id="3f62c-196">You can also create you own 'hard-coded' data by updating the code:</span></span>

        ```csharp
        ModelInput sampleData = new ModelInput()
        {
            Col0 = "The ML.NET CLI is great for getting started. Very cool!"
        };
        ```

    - <span data-ttu-id="3f62c-197">下一行代码对指定的输入数据使用 `ConsumeModel.Predict()` 方法，以预测并返回结果（基于 ModelOutput.cs 架构）。</span><span class="sxs-lookup"><span data-stu-id="3f62c-197">The next line of code uses the `ConsumeModel.Predict()` method on the specified input data to make a prediction and return the results (based on the ModelOutput.cs schema).</span></span>
    - <span data-ttu-id="3f62c-198">最后几行代码输出样本数据的属性（本例中为注释）、情绪预测以及正面情绪 (1) 和负面情绪 (2) 的相应评分。</span><span class="sxs-lookup"><span data-stu-id="3f62c-198">The last lines of code print out the properties of the sample data (in this case the Comment) as well as the Sentiment prediction and corresponding Scores for positive sentiment (1) and negative sentiment (2).</span></span>

1. <span data-ttu-id="3f62c-199">使用从数据集第一行加载的原始示例数据或通过提供自己的自定义硬编码示例数据来运行项目。</span><span class="sxs-lookup"><span data-stu-id="3f62c-199">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="3f62c-200">应该获得与以下内容相当的预测：</span><span class="sxs-lookup"><span data-stu-id="3f62c-200">You should get a prediction comparable to:</span></span>

![ML.NET CLI 从 Visual Studio 运行应用](./media/mlnet-cli/mlnet-cli-console-app.png)<span data-ttu-id="3f62c-202">)</span><span class="sxs-lookup"><span data-stu-id="3f62c-202">)</span></span>

1. <span data-ttu-id="3f62c-203">尝试将硬编码示例数据更改为具有不同情绪的其他句子，并查看模型预测正面或负面情绪的表现如何。</span><span class="sxs-lookup"><span data-stu-id="3f62c-203">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span>

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="3f62c-204">为最终用户应用程序注入 ML 模型预测</span><span class="sxs-lookup"><span data-stu-id="3f62c-204">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="3f62c-205">可以使用类似的“ML 模型评分代码”在最终用户应用程序中运行模型并进行预测。</span><span class="sxs-lookup"><span data-stu-id="3f62c-205">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span>

<span data-ttu-id="3f62c-206">例如，可以直接将该代码移至任何 Windows 桌面应用程序（例如 WPF 和 WinForms），并以与在控制台应用中相同的方式运行模型。</span><span class="sxs-lookup"><span data-stu-id="3f62c-206">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="3f62c-207">但是，应该优化实现这些代码行来运行 ML 模型的方式（即，缓存模型 .zip 文件并加载一次），并使用单一实例对象，而不是在每个请求上创建它们，特别是在应用程序需要具有可伸缩性（例如 Web 应用程序或分布式服务）的情况下，如以下部分所述。</span><span class="sxs-lookup"><span data-stu-id="3f62c-207">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="3f62c-208">在可缩放的 ASP.NET Core Web 应用和服务（多线程应用）中运行 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="3f62c-208">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="3f62c-209">应该优化模型对象（从模型的 .zip 文件加载的 `ITransformer`）和 `PredictionEngine` 对象的创建，尤其是在可缩放的 Web 应用和分布式服务上运行时。</span><span class="sxs-lookup"><span data-stu-id="3f62c-209">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="3f62c-210">对于第一种情况，模型对象 (`ITransformer`) 的优化很简单。</span><span class="sxs-lookup"><span data-stu-id="3f62c-210">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="3f62c-211">由于 `ITransformer` 对象为线程安全型，所以可将该对象作为单一实例或静态对象进行缓存，这样就只需加载模型一次。</span><span class="sxs-lookup"><span data-stu-id="3f62c-211">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="3f62c-212">对于第二个对象（`PredictionEngine` 对象），优化并不容易，因为 `PredictionEngine` 对象不为线程安全型，所以无法在 ASP.NET Core 应用中将此对象实例化为单一实例或静态对象。</span><span class="sxs-lookup"><span data-stu-id="3f62c-212">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="3f62c-213">此[博客文章](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)深入讨论了此线程安全和可伸缩性问题。</span><span class="sxs-lookup"><span data-stu-id="3f62c-213">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

<span data-ttu-id="3f62c-214">然而，事情已经变得比博客文章中解释的容易得多。</span><span class="sxs-lookup"><span data-stu-id="3f62c-214">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="3f62c-215">我们开发出一个更简单的方法，并创建了一个很不错的 **“.NET Core 集成包”** ，用户可通过在应用程序 DI 服务（依赖项注入服务）中注册它来轻松地在 ASP.NET Core 应用和服务中使用它，然后可通过代码直接使用它。</span><span class="sxs-lookup"><span data-stu-id="3f62c-215">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="3f62c-216">查看以下相关教程和示例：</span><span class="sxs-lookup"><span data-stu-id="3f62c-216">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="3f62c-217">教程：在可缩放的 ASP.NET Core Web 应用和 WebAPI 上运行 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="3f62c-217">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="3f62c-218">示例：ASP.NET Core WebAPI 上的可缩放 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="3f62c-218">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="3f62c-219">探索生成用于训练“最佳质量”模型的的 C# 代码</span><span class="sxs-lookup"><span data-stu-id="3f62c-219">Explore the generated C# code that was used to train the "best quality" model</span></span>

<span data-ttu-id="3f62c-220">出于更高级的学习目的，还可以探索 CLI 工具生成用于训练生成的模型的 C# 代码。</span><span class="sxs-lookup"><span data-stu-id="3f62c-220">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="3f62c-221">该“训练模型代码”目前在名为 `ModelBuilder` 的生成的自定义类中生成，因此可以研究该训练代码。</span><span class="sxs-lookup"><span data-stu-id="3f62c-221">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="3f62c-222">更重要的是，对于此特定方案（情绪分析模型），还可以将该生成的训练代码与以下教程中所述的代码进行比较：</span><span class="sxs-lookup"><span data-stu-id="3f62c-222">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="3f62c-223">比较：[教程：在情绪分析二元分类方案中使用 ML.NET](sentiment-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="3f62c-223">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="3f62c-224">将教程中选择的算法和管道配置与 CLI 工具生成的代码进行比较很有趣。</span><span class="sxs-lookup"><span data-stu-id="3f62c-224">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="3f62c-225">根据迭代和搜索更好的模型所花费的时间，所选算法及其特定的超参数和管道配置可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="3f62c-225">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

<span data-ttu-id="3f62c-226">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="3f62c-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="3f62c-227">为选定 ML 任务（要解决的问题）准备数据</span><span class="sxs-lookup"><span data-stu-id="3f62c-227">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="3f62c-228">在 CLI 工具中运行“mlnet classification”命令</span><span class="sxs-lookup"><span data-stu-id="3f62c-228">Run the 'mlnet classification' command in the CLI tool</span></span>
> - <span data-ttu-id="3f62c-229">查看质量指标结果</span><span class="sxs-lookup"><span data-stu-id="3f62c-229">Review the quality metric results</span></span>
> - <span data-ttu-id="3f62c-230">了解生成用于运行模型的 C# 代码（用于最终用户应用的代码）</span><span class="sxs-lookup"><span data-stu-id="3f62c-230">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="3f62c-231">探索生成的用于训练“最佳质量”模型的 C# 代码（学习目的）</span><span class="sxs-lookup"><span data-stu-id="3f62c-231">Explore the generated C# code that was used to train the "best quality" model (earning purposes)</span></span>

## <a name="see-also"></a><span data-ttu-id="3f62c-232">请参阅</span><span class="sxs-lookup"><span data-stu-id="3f62c-232">See also</span></span>

- [<span data-ttu-id="3f62c-233">使用 ML.NET CLI 自动进行模型训练</span><span class="sxs-lookup"><span data-stu-id="3f62c-233">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="3f62c-234">教程：在可缩放的 ASP.NET Core Web 应用和 WebAPI 上运行 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="3f62c-234">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="3f62c-235">示例：ASP.NET Core WebAPI 上的可缩放 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="3f62c-235">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="3f62c-236">ML.NET CLI auto-train 命令参考指南</span><span class="sxs-lookup"><span data-stu-id="3f62c-236">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="3f62c-237">ML.NET CLI 中的遥测</span><span class="sxs-lookup"><span data-stu-id="3f62c-237">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
