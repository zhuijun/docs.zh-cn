---
title: ML.NET CLI 命令参考
description: ML.NET CLI 工具中 auto-train 命令的概述、示例和参考。
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 397f6fda8554024624b3ef630856dc8eca9696b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594538"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="89513-103">ML.NET CLI 命令参考</span><span class="sxs-lookup"><span data-stu-id="89513-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="89513-104">`classification`、`regression` 和 `recommendation` 命令是 ML.NET CLI 工具提供的主要命令。</span><span class="sxs-lookup"><span data-stu-id="89513-104">The `classification`, `regression`, and `recommendation` commands are the main commands provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="89513-105">这些命令允许使用自动化机器学习 (AutoML) 以及用于运行模型/对模型评分的示例 C# 代码生成用于分类、回归和建议模型的高质量 ML.NET 模型。</span><span class="sxs-lookup"><span data-stu-id="89513-105">These commands allow you to generate good quality ML.NET models for classification, regression, and recommendation models using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="89513-106">此外，还会生成用于训练模型的 C# 代码，以便你可以研究模型的算法和设置。</span><span class="sxs-lookup"><span data-stu-id="89513-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="89513-107">本主题涉及目前处于预览状态的 ML.NET CLI 和 ML.NET AutoML，且材料可能会有所变化。</span><span class="sxs-lookup"><span data-stu-id="89513-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="89513-108">概述</span><span class="sxs-lookup"><span data-stu-id="89513-108">Overview</span></span>

<span data-ttu-id="89513-109">示例用法：</span><span class="sxs-lookup"><span data-stu-id="89513-109">Example usage:</span></span>

```console
mlnet regression --dataset "cars.csv" --label-col price
```

<span data-ttu-id="89513-110">`mlnet` ML 任务命令（`classification`、`regression` 和 `recommendation`）生成以下资产：</span><span class="sxs-lookup"><span data-stu-id="89513-110">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) generate the following assets:</span></span>

- <span data-ttu-id="89513-111">可供使用的序列化模型 .zip 文件（“最佳模型”）。</span><span class="sxs-lookup"><span data-stu-id="89513-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="89513-112">用于运行生成的模型和对其进行评分的 C# 代码。</span><span class="sxs-lookup"><span data-stu-id="89513-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="89513-113">包含用于生成该模型的训练代码的 C# 代码。</span><span class="sxs-lookup"><span data-stu-id="89513-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="89513-114">前两个资产可以直接用于最终用户应用（ASP.NET Core Web 应用、服务、桌面应用等），以使用模型进行预测。</span><span class="sxs-lookup"><span data-stu-id="89513-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="89513-115">第三个资产（训练代码）显示 CLI 用于训练生成的模型的 ML.NET API 代码，因此可以研究模型的特定算法和设置。</span><span class="sxs-lookup"><span data-stu-id="89513-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="89513-116">示例</span><span class="sxs-lookup"><span data-stu-id="89513-116">Examples</span></span>

<span data-ttu-id="89513-117">用于分类问题的最简单的 CLI 命令（AutoML 从提供的数据中推断出大部分配置）：</span><span class="sxs-lookup"><span data-stu-id="89513-117">The simplest CLI command for a classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

<span data-ttu-id="89513-118">另一个用于回归问题的简单 CLI 命令：</span><span class="sxs-lookup"><span data-stu-id="89513-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

<span data-ttu-id="89513-119">使用训练数据集、测试数据集和进一步的自定义显式参数创建和训练分类模型：</span><span class="sxs-lookup"><span data-stu-id="89513-119">Create and train a classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a><span data-ttu-id="89513-120">命令选项</span><span class="sxs-lookup"><span data-stu-id="89513-120">Command options</span></span>

<span data-ttu-id="89513-121">`mlnet` ML 任务命令（`classification`、`regression` 和 `recommendation`）基于提供的数据集和 ML.NET CLI 选项训练多个模型。</span><span class="sxs-lookup"><span data-stu-id="89513-121">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) train multiple models based on the provided dataset and ML.NET CLI options.</span></span> <span data-ttu-id="89513-122">这些命令还可用于选择最佳模型，将模型保存为序列化的 .zip 文件，并生成用于评分和训练的相关 C# 代码。</span><span class="sxs-lookup"><span data-stu-id="89513-122">These commands also select the best model, save the model as a serialized .zip file, and generate related C# code for scoring and training.</span></span>

### <a name="classification-options"></a><span data-ttu-id="89513-123">分类选项</span><span class="sxs-lookup"><span data-stu-id="89513-123">Classification options</span></span>

<span data-ttu-id="89513-124">运行 `mlnet classification` 将训练分类模型。</span><span class="sxs-lookup"><span data-stu-id="89513-124">Running `mlnet classification` will train a classification model.</span></span> <span data-ttu-id="89513-125">如果希望 ML 模型将数据分类为 2 个或更多个类（例如情绪分析），请选择此命令。</span><span class="sxs-lookup"><span data-stu-id="89513-125">Choose this command if you want an ML Model to categorize data into 2 or more classes (e.g. sentiment analysis).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a><span data-ttu-id="89513-126">回归选项</span><span class="sxs-lookup"><span data-stu-id="89513-126">Regression options</span></span>

<span data-ttu-id="89513-127">运行 `mlnet regression` 将训练回归模型。</span><span class="sxs-lookup"><span data-stu-id="89513-127">Running `mlnet regression` will train a regression model.</span></span> <span data-ttu-id="89513-128">如果希望 ML 模型预测数值（例如价格预测），请选择此命令。</span><span class="sxs-lookup"><span data-stu-id="89513-128">Choose this command if you want an ML Model to predict a numeric value (e.g. price prediction).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a><span data-ttu-id="89513-129">建议选项</span><span class="sxs-lookup"><span data-stu-id="89513-129">Recommendation options</span></span>

<span data-ttu-id="89513-130">运行 `mlnet recommendation` 将训练建议模型。</span><span class="sxs-lookup"><span data-stu-id="89513-130">Running `mlnet recommendation` will train a recommendation model.</span></span>  <span data-ttu-id="89513-131">如果希望 ML 模型根据评级（例如产品建议）向用户推荐项，请选择此命令。</span><span class="sxs-lookup"><span data-stu-id="89513-131">Choose this command if you want an ML Model to recommend items to users based on ratings (e.g. product recommendation).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

<span data-ttu-id="89513-132">无效输入选项会导致 CLI 工具发出有效输入和错误消息列表。</span><span class="sxs-lookup"><span data-stu-id="89513-132">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="dataset"></a><span data-ttu-id="89513-133">数据集</span><span class="sxs-lookup"><span data-stu-id="89513-133">Dataset</span></span>

<span data-ttu-id="89513-134">`--dataset | -d`（字符串）</span><span class="sxs-lookup"><span data-stu-id="89513-134">`--dataset | -d` (string)</span></span>

<span data-ttu-id="89513-135">此参数向以下任一选项提供文件路径：</span><span class="sxs-lookup"><span data-stu-id="89513-135">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="89513-136">*A：整个数据集文件：* 如果使用此选项且用户未提供 `--test-dataset` 和 `--validation-dataset`，则将在内部使用交叉验证（K 折等）或自动数据拆分方法来验证模型。</span><span class="sxs-lookup"><span data-stu-id="89513-136">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="89513-137">在这种情况下，用户将只需要提供数据集文件路径。</span><span class="sxs-lookup"><span data-stu-id="89513-137">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="89513-138">*B：训练数据集文件：* 如果用户还提供用于模型验证的数据集（使用 `--test-dataset` 和可选的 `--validation-dataset`），则 `--dataset` 参数意味着仅拥有“训练数据集”。</span><span class="sxs-lookup"><span data-stu-id="89513-138">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="89513-139">例如，当使用 80%-20% 方法来验证模型的质量以及获取准确性指标时，“训练数据集”将拥有 80% 的数据，而“测试数据集”将拥有 20% 的数据。</span><span class="sxs-lookup"><span data-stu-id="89513-139">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="89513-140">测试数据集</span><span class="sxs-lookup"><span data-stu-id="89513-140">Test dataset</span></span>

<span data-ttu-id="89513-141">`--test-dataset | -t`（字符串）</span><span class="sxs-lookup"><span data-stu-id="89513-141">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="89513-142">指向测试数据集文件的文件路径，例如，在进行常规验证以获取准确性指标时使用 80%-20% 方法的情况。</span><span class="sxs-lookup"><span data-stu-id="89513-142">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="89513-143">如果使用 `--test-dataset`，则还需要 `--dataset`。</span><span class="sxs-lookup"><span data-stu-id="89513-143">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="89513-144">除非使用 --validation-dataset，否则 `--test-dataset` 参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="89513-144">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="89513-145">在这种情况下，用户必须使用三个参数。</span><span class="sxs-lookup"><span data-stu-id="89513-145">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="89513-146">验证数据集</span><span class="sxs-lookup"><span data-stu-id="89513-146">Validation dataset</span></span>

<span data-ttu-id="89513-147">`--validation-dataset | -v`（字符串）</span><span class="sxs-lookup"><span data-stu-id="89513-147">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="89513-148">指向验证数据集文件的文件路径。</span><span class="sxs-lookup"><span data-stu-id="89513-148">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="89513-149">验证数据集在任何情况下都是可选的。</span><span class="sxs-lookup"><span data-stu-id="89513-149">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="89513-150">如果使用 `validation dataset`，则行为应为：</span><span class="sxs-lookup"><span data-stu-id="89513-150">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="89513-151">`test-dataset` 和 `--dataset` 参数也是必需的。</span><span class="sxs-lookup"><span data-stu-id="89513-151">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="89513-152">`validation-dataset` 数据集用于估算模型选择的预测误差。</span><span class="sxs-lookup"><span data-stu-id="89513-152">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="89513-153">`test-dataset` 用于评估最终选定模型的泛化误差。</span><span class="sxs-lookup"><span data-stu-id="89513-153">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="89513-154">理想情况下，测试集应保存在“保管库”中，并仅在数据分析结束时显示。</span><span class="sxs-lookup"><span data-stu-id="89513-154">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="89513-155">一般来说，使用 `validation dataset` 以及 `test dataset` 时，验证阶段拆分为两部分：</span><span class="sxs-lookup"><span data-stu-id="89513-155">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="89513-156">在第一部分中，只需查看模型并使用验证数据选择性能最佳的方法即可（= 验证）</span><span class="sxs-lookup"><span data-stu-id="89513-156">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="89513-157">然后，估算选定方法的准确性（= 测试）。</span><span class="sxs-lookup"><span data-stu-id="89513-157">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="89513-158">因此，数据分离可以是 80/10/10 或 75/15/10。</span><span class="sxs-lookup"><span data-stu-id="89513-158">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="89513-159">例如：</span><span class="sxs-lookup"><span data-stu-id="89513-159">For example:</span></span>

- <span data-ttu-id="89513-160">`training-dataset` 文件应拥有 75% 的数据。</span><span class="sxs-lookup"><span data-stu-id="89513-160">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="89513-161">`validation-dataset` 文件应拥有 15% 的数据。</span><span class="sxs-lookup"><span data-stu-id="89513-161">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="89513-162">`test-dataset` 文件应拥有 10% 的数据。</span><span class="sxs-lookup"><span data-stu-id="89513-162">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="89513-163">在任何情况下，这些百分比都将由使用 CLI 的用户决定，用户将提供已经拆分的文件。</span><span class="sxs-lookup"><span data-stu-id="89513-163">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column"></a><span data-ttu-id="89513-164">标签列</span><span class="sxs-lookup"><span data-stu-id="89513-164">Label column</span></span>

<span data-ttu-id="89513-165">`--label-col`（int 或 string）</span><span class="sxs-lookup"><span data-stu-id="89513-165">`--label-col` (int or string)</span></span>

<span data-ttu-id="89513-166">借助此参数，可以使用数据集标头中设置的列名或数据集文件中列的数字索引（列索引值从 0 开始）来指定特定的目的/目标列（想要预测的变量）。</span><span class="sxs-lookup"><span data-stu-id="89513-166">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="89513-167">此参数用于分类和回归问题 。</span><span class="sxs-lookup"><span data-stu-id="89513-167">This argument is used for *classification* and *regression* problems.</span></span>

## <a name="item-column"></a><span data-ttu-id="89513-168">项列</span><span class="sxs-lookup"><span data-stu-id="89513-168">Item column</span></span>

<span data-ttu-id="89513-169">`--item-col`（int 或 string）</span><span class="sxs-lookup"><span data-stu-id="89513-169">`--item-col` (int or string)</span></span>

<span data-ttu-id="89513-170">项列包含用户评分的项目列表（向用户建议的项）。</span><span class="sxs-lookup"><span data-stu-id="89513-170">The item column has the list of items that users rate (items are recommended to users).</span></span> <span data-ttu-id="89513-171">可以使用数据集标头中设置的列名或数据集文件中列的数字索引（列索引值从 0 开始）来指定此列。</span><span class="sxs-lookup"><span data-stu-id="89513-171">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="89513-172">此参数仅用于建议任务。</span><span class="sxs-lookup"><span data-stu-id="89513-172">This argument is used only for the *recommendation* task.</span></span>

## <a name="rating-column"></a><span data-ttu-id="89513-173">评级列</span><span class="sxs-lookup"><span data-stu-id="89513-173">Rating column</span></span>

<span data-ttu-id="89513-174">`--rating-col`（int 或 string）</span><span class="sxs-lookup"><span data-stu-id="89513-174">`--rating-col` (int or string)</span></span>

<span data-ttu-id="89513-175">评级列包含用户给项的评级列表。</span><span class="sxs-lookup"><span data-stu-id="89513-175">The rating column has the list of ratings that are given to items by users.</span></span> <span data-ttu-id="89513-176">可以使用数据集标头中设置的列名或数据集文件中列的数字索引（列索引值从 0 开始）来指定此列。</span><span class="sxs-lookup"><span data-stu-id="89513-176">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="89513-177">此参数仅用于建议任务。</span><span class="sxs-lookup"><span data-stu-id="89513-177">This argument is used only for the *recommendation* task.</span></span>

## <a name="user-column"></a><span data-ttu-id="89513-178">用户列</span><span class="sxs-lookup"><span data-stu-id="89513-178">User column</span></span>

<span data-ttu-id="89513-179">`--user-col`（int 或 string）</span><span class="sxs-lookup"><span data-stu-id="89513-179">`--user-col` (int or string)</span></span>

<span data-ttu-id="89513-180">用户列包含为项评级的用户列表。</span><span class="sxs-lookup"><span data-stu-id="89513-180">The user column has the list of users that give ratings to items.</span></span> <span data-ttu-id="89513-181">可以使用数据集标头中设置的列名或数据集文件中列的数字索引（列索引值从 0 开始）来指定此列。</span><span class="sxs-lookup"><span data-stu-id="89513-181">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="89513-182">此参数仅用于建议任务。</span><span class="sxs-lookup"><span data-stu-id="89513-182">This argument is used only for the *recommendation* task.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="89513-183">忽略列</span><span class="sxs-lookup"><span data-stu-id="89513-183">Ignore columns</span></span>

<span data-ttu-id="89513-184">`--ignore-columns`（字符串）</span><span class="sxs-lookup"><span data-stu-id="89513-184">`--ignore-columns` (string)</span></span>

<span data-ttu-id="89513-185">借助此参数，可以忽略数据集文件中的现有列，这样一来，训练过程便不会加载和使用它们。</span><span class="sxs-lookup"><span data-stu-id="89513-185">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="89513-186">指定想要忽略的列名。</span><span class="sxs-lookup"><span data-stu-id="89513-186">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="89513-187">使用“, ”（逗号加空格）或“ ”（空格）分隔多个列名。</span><span class="sxs-lookup"><span data-stu-id="89513-187">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="89513-188">可以对包含空格的列名使用引号（例如，“logged in”）。</span><span class="sxs-lookup"><span data-stu-id="89513-188">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="89513-189">示例：</span><span class="sxs-lookup"><span data-stu-id="89513-189">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="89513-190">具有标头</span><span class="sxs-lookup"><span data-stu-id="89513-190">Has header</span></span>

<span data-ttu-id="89513-191">`--has-header`（布尔值）</span><span class="sxs-lookup"><span data-stu-id="89513-191">`--has-header` (bool)</span></span>

<span data-ttu-id="89513-192">指定数据集文件是否拥有标头行。</span><span class="sxs-lookup"><span data-stu-id="89513-192">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="89513-193">可能的值有：</span><span class="sxs-lookup"><span data-stu-id="89513-193">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="89513-194">如果用户未指定此参数，则 ML.NET CLI 将尝试检测此属性。</span><span class="sxs-lookup"><span data-stu-id="89513-194">The ML.NET CLI will try to detect this property if this argument is not specified by the user.</span></span>

## <a name="train-time"></a><span data-ttu-id="89513-195">训练时间</span><span class="sxs-lookup"><span data-stu-id="89513-195">Train time</span></span>

<span data-ttu-id="89513-196">`--train-time`（字符串）</span><span class="sxs-lookup"><span data-stu-id="89513-196">`--train-time` (string)</span></span>

<span data-ttu-id="89513-197">默认情况下，最长探索/训练时间为 30 分钟。</span><span class="sxs-lookup"><span data-stu-id="89513-197">By default, the maximum exploration / train time is 30 minutes.</span></span>

<span data-ttu-id="89513-198">此参数设置探索多个训练程序和配置的过程的最长持续时间（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="89513-198">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="89513-199">如果提供的时间对于单次迭代来说太短（例如 2 秒），则可能会超出配置的时间。</span><span class="sxs-lookup"><span data-stu-id="89513-199">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="89513-200">在这种情况下，实际时间是在单次迭代中生成一个模型配置所需的时间。</span><span class="sxs-lookup"><span data-stu-id="89513-200">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="89513-201">迭代所需的时间可能因数据集的大小而异。</span><span class="sxs-lookup"><span data-stu-id="89513-201">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="89513-202">缓存</span><span class="sxs-lookup"><span data-stu-id="89513-202">Cache</span></span>

<span data-ttu-id="89513-203">`--cache`（字符串）</span><span class="sxs-lookup"><span data-stu-id="89513-203">`--cache` (string)</span></span>

<span data-ttu-id="89513-204">如果使用缓存，则整个训练数据集将在内存中加载。</span><span class="sxs-lookup"><span data-stu-id="89513-204">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="89513-205">对于中小型数据集，使用缓存可以大幅提高训练性能，这意味着训练时间可以比不使用缓存时更短。</span><span class="sxs-lookup"><span data-stu-id="89513-205">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="89513-206">但是，对于大型数据集，在内存中加载所有数据可能会产生负面影响，因为可能会出现内存不足的情况。</span><span class="sxs-lookup"><span data-stu-id="89513-206">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="89513-207">如果使用大型数据集文件进行训练而不使用缓存，ML.NET 将在训练期间需要加载更多数据时从驱动器中流式传输数据块。</span><span class="sxs-lookup"><span data-stu-id="89513-207">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="89513-208">你可以指定以下值：</span><span class="sxs-lookup"><span data-stu-id="89513-208">You can specify the following values:</span></span>

<span data-ttu-id="89513-209">`on`：强制在训练时使用缓存。</span><span class="sxs-lookup"><span data-stu-id="89513-209">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="89513-210">`off`：强制在训练时不使用缓存。</span><span class="sxs-lookup"><span data-stu-id="89513-210">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="89513-211">`auto`：是否使用缓存取决于 AutoML 试探法。</span><span class="sxs-lookup"><span data-stu-id="89513-211">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="89513-212">通常情况下，如果使用 `auto` 选项，小型/中型数据集将使用缓存，而大型数据集将不使用缓存。</span><span class="sxs-lookup"><span data-stu-id="89513-212">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="89513-213">如果未指定 `--cache` 参数，则默认情况下将使用缓存 `auto` 配置。</span><span class="sxs-lookup"><span data-stu-id="89513-213">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="89513-214">“属性”</span><span class="sxs-lookup"><span data-stu-id="89513-214">Name</span></span>

<span data-ttu-id="89513-215">`--name`（字符串）</span><span class="sxs-lookup"><span data-stu-id="89513-215">`--name` (string)</span></span>

<span data-ttu-id="89513-216">创建的输出项目或解决方案的名称。</span><span class="sxs-lookup"><span data-stu-id="89513-216">The name for the created output project or solution.</span></span> <span data-ttu-id="89513-217">如果未指定名称，则使用名称 `sample-{mltask}`。</span><span class="sxs-lookup"><span data-stu-id="89513-217">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="89513-218">ML.NET 模型文件（.zip 文件）也将获得相同的名称。</span><span class="sxs-lookup"><span data-stu-id="89513-218">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="89513-219">输出路径</span><span class="sxs-lookup"><span data-stu-id="89513-219">Output path</span></span>

<span data-ttu-id="89513-220">`--output-path | -o`（字符串）</span><span class="sxs-lookup"><span data-stu-id="89513-220">`--output-path | -o` (string)</span></span>

<span data-ttu-id="89513-221">用于放置生成的输出的根位置/文件夹。</span><span class="sxs-lookup"><span data-stu-id="89513-221">Root location/folder to place the generated output.</span></span> <span data-ttu-id="89513-222">默认为当前目录。</span><span class="sxs-lookup"><span data-stu-id="89513-222">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="89513-223">详细级别</span><span class="sxs-lookup"><span data-stu-id="89513-223">Verbosity</span></span>

<span data-ttu-id="89513-224">`--verbosity | -v`（字符串）</span><span class="sxs-lookup"><span data-stu-id="89513-224">`--verbosity | -v` (string)</span></span>

<span data-ttu-id="89513-225">设置标准输出的详细级别。</span><span class="sxs-lookup"><span data-stu-id="89513-225">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="89513-226">允许的值包括：</span><span class="sxs-lookup"><span data-stu-id="89513-226">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="89513-227">`m[inimal]`（默认情况）</span><span class="sxs-lookup"><span data-stu-id="89513-227">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="89513-228">`diag[nostic]`（日志记录信息级别）</span><span class="sxs-lookup"><span data-stu-id="89513-228">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="89513-229">默认情况下，CLI 工具应在运行时显示一些最低限度的反馈 (`minimal`)，例如提及它正在运行以及剩余多少时间或已完成时间的百分比（如果可能）。</span><span class="sxs-lookup"><span data-stu-id="89513-229">By default, the CLI tool should show some minimum feedback (`minimal`) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="89513-230">帮助</span><span class="sxs-lookup"><span data-stu-id="89513-230">Help</span></span>

`-h |--help`

<span data-ttu-id="89513-231">打印命令帮助，其中包含对每个命令的参数的描述。</span><span class="sxs-lookup"><span data-stu-id="89513-231">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="89513-232">请参阅</span><span class="sxs-lookup"><span data-stu-id="89513-232">See also</span></span>

- [<span data-ttu-id="89513-233">如何安装 ML.NET CLI 工具</span><span class="sxs-lookup"><span data-stu-id="89513-233">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="89513-234">ML.NET CLI 概述</span><span class="sxs-lookup"><span data-stu-id="89513-234">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="89513-235">教程：使用 ML.NET CLI 分析情绪</span><span class="sxs-lookup"><span data-stu-id="89513-235">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="89513-236">ML.NET CLI 中的遥测</span><span class="sxs-lookup"><span data-stu-id="89513-236">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
