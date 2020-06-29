---
title: 为模型生成器加载培训数据
description: 了解如何从 SQL Server 数据库或文件加载培训数据，以在 ML.NET 的众多模型生成器方案中使用。
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 64e366b3c66427ccd2810324abeb880f6cb9ebc1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602201"
---
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="f4a5a-103">将培训数据加载到模型生成器</span><span class="sxs-lookup"><span data-stu-id="f4a5a-103">Load training data into Model Builder</span></span>

<span data-ttu-id="f4a5a-104">了解如何从文件或 SQL Server 数据库加载培训数据集，以 ML.NET 的众多模型生成器方案中使用。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="f4a5a-105">模型生成器方案可以将 SQL Server 数据库、图像文件和 CSV 或 TSV 文件格式用作培训数据。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="f4a5a-106">模型生成器的培训数据集限制</span><span class="sxs-lookup"><span data-stu-id="f4a5a-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="f4a5a-107">模型生成器对于你可用于培训模型的数据的数量和类型有如下限制：</span><span class="sxs-lookup"><span data-stu-id="f4a5a-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="f4a5a-108">SQL Server 数据：100,000 行</span><span class="sxs-lookup"><span data-stu-id="f4a5a-108">SQL Server data: 100,000 rows</span></span>
- <span data-ttu-id="f4a5a-109">CSV 和 TSV 文件：无大小限制</span><span class="sxs-lookup"><span data-stu-id="f4a5a-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="f4a5a-110">图像：仅 PNG 和JPG。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="f4a5a-111">模型生成器方案</span><span class="sxs-lookup"><span data-stu-id="f4a5a-111">Model Builder scenarios</span></span>

<span data-ttu-id="f4a5a-112">模型生成器可帮助你为以下机器学习方案创建模型：</span><span class="sxs-lookup"><span data-stu-id="f4a5a-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="f4a5a-113">情绪分析（二元分类）：将文本数据划分为两个类别。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="f4a5a-114">问题分类（多类分类）：将文本数据划分为 3 个或更多个类别。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="f4a5a-115">价格预测（回归）：预测一个数值。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="f4a5a-116">图像分类（深度学习）：根据特征分类图像。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="f4a5a-117">自定义方案：利用回归、分类和其他任务，通过数据生成自定义方案。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="f4a5a-118">本文介绍了使用文本或数值数据的分类和回归方案，以及图像分类方案。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span>

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="f4a5a-119">从文件加载文本或数值数据</span><span class="sxs-lookup"><span data-stu-id="f4a5a-119">Load text or numeric data from a file</span></span>

<span data-ttu-id="f4a5a-120">你可以将文件中的文本或数值数据加载到模型生成器中。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="f4a5a-121">它接受逗号分隔 (CSV) 或制表符分隔 (TSV) 的文件格式。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span>

1. <span data-ttu-id="f4a5a-122">在模型生成器的数据步骤中，从数据源下拉列表中选择“文件”  。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="f4a5a-123">选择“选择文件”文本框旁边的按钮，并使用文件资源管理器浏览并选择数据文件。 </span><span class="sxs-lookup"><span data-stu-id="f4a5a-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="f4a5a-124">在“要预测的列(标签)”下拉列表中选择一个类别  。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="f4a5a-125">在“输入列(特性)”下拉列表中，确认已选择要包括的数据列。 </span><span class="sxs-lookup"><span data-stu-id="f4a5a-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="f4a5a-126">你已经为模型生成器设置了数据源文件。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="f4a5a-127">选择“培训”  链接，转到模型生成器中的下一步。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="f4a5a-128">从 SQL Server 数据库加载数据</span><span class="sxs-lookup"><span data-stu-id="f4a5a-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="f4a5a-129">模型生成器支持从本地和远程 SQL Server 数据库加载数据。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="f4a5a-130">如需将 SQL Server 数据库中的数据加载到模型生成器，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="f4a5a-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="f4a5a-131">在模型生成器的数据步骤中，从数据源下拉列表中选择“SQL Server”  。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="f4a5a-132">选择“连接到 SQL Server 数据库”文本框旁的按钮。 </span><span class="sxs-lookup"><span data-stu-id="f4a5a-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="f4a5a-133">在“选择数据”对话框中，选择“Microsoft SQL Server 数据库文件”   。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="f4a5a-134">取消选中“始终使用此选择”复选框，然后选择“继续”  </span><span class="sxs-lookup"><span data-stu-id="f4a5a-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="f4a5a-135">在“连接属性”对话框中，选择“浏览”，然后选择已下载的 .MDF 文件。  </span><span class="sxs-lookup"><span data-stu-id="f4a5a-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="f4a5a-136">选择“确定” </span><span class="sxs-lookup"><span data-stu-id="f4a5a-136">Select **OK**</span></span>
1. <span data-ttu-id="f4a5a-137">从“表名称”下拉列表选择数据集名称。 </span><span class="sxs-lookup"><span data-stu-id="f4a5a-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="f4a5a-138">从“要预测的列(标签)”下拉列表中，选择想要预测的数据类别。 </span><span class="sxs-lookup"><span data-stu-id="f4a5a-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="f4a5a-139">在“输入列(特性)”下拉列表中，确认已选择要包括的列。 </span><span class="sxs-lookup"><span data-stu-id="f4a5a-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span>

<span data-ttu-id="f4a5a-140">你已经为模型生成器设置了数据源文件。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="f4a5a-141">选择“培训”  链接，转到模型生成器中的下一步。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="f4a5a-142">设置图像数据文件</span><span class="sxs-lookup"><span data-stu-id="f4a5a-142">Set up image data files</span></span>

<span data-ttu-id="f4a5a-143">模型生成器要求图像数据为 JPG 或 PNG 文件，并且整合在与分类类别对应的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span>

<span data-ttu-id="f4a5a-144">若要将图像加载到模型生成器，请提供指向单个顶级目录的路径：</span><span class="sxs-lookup"><span data-stu-id="f4a5a-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="f4a5a-145">此顶级目录包含一个要预测的各个类别的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span>
- <span data-ttu-id="f4a5a-146">每个子文件夹包含属于它的类别的图像文件。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-146">Each subfolder contains the image files belonging to its category.</span></span>

<span data-ttu-id="f4a5a-147">在下面所示的文件夹结构中，顶级目录为 flower_photos。 </span><span class="sxs-lookup"><span data-stu-id="f4a5a-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="f4a5a-148">有 5 个子目录，它们对应要预测的类别：菊花、蒲公英、玫瑰、向日葵和郁金香。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="f4a5a-149">每个子目录包含属于其各自类别的图像。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-149">Each of these subdirectories contains images belonging to its respective category.</span></span>

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg
```

## <a name="next-steps"></a><span data-ttu-id="f4a5a-150">后续步骤</span><span class="sxs-lookup"><span data-stu-id="f4a5a-150">Next steps</span></span>

<span data-ttu-id="f4a5a-151">按照以下教程使用模型生成器生成机器学习应用：</span><span class="sxs-lookup"><span data-stu-id="f4a5a-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="f4a5a-152">使用回归法预测价格</span><span class="sxs-lookup"><span data-stu-id="f4a5a-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="f4a5a-153">使用二元分类分析 Web 应用程序中的情绪</span><span class="sxs-lookup"><span data-stu-id="f4a5a-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md)

<span data-ttu-id="f4a5a-154">若使用代码培训模型，请[了解如何使用 ML.NET API 加载数据](load-data-ml-net.md)。</span><span class="sxs-lookup"><span data-stu-id="f4a5a-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
