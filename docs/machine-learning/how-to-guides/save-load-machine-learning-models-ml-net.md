---
title: 保存和加载经过训练的模型
description: 了解如何保存和加载经过训练的模型
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 681a35956a8959e2f1cbb5a7023e0ef29b67097e
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679529"
---
# <a name="save-and-load-trained-models"></a><span data-ttu-id="926ce-103">保存和加载经过训练的模型</span><span class="sxs-lookup"><span data-stu-id="926ce-103">Save and load trained models</span></span>

<span data-ttu-id="926ce-104">了解如何在应用程序中保存和加载经过训练的模型。</span><span class="sxs-lookup"><span data-stu-id="926ce-104">Learn how to save and load trained models in your application.</span></span>

<span data-ttu-id="926ce-105">在整个模型生成过程中，模型位于内存中，并且可以在整个应用程序生命周期中访问。</span><span class="sxs-lookup"><span data-stu-id="926ce-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="926ce-106">但是，一旦应用程序停止运行，而模型未在本地或远程的某个位置保存，则无法再访问该模型。</span><span class="sxs-lookup"><span data-stu-id="926ce-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="926ce-107">通常情况下，在其他应用程序中训练模型之后，某些时候会使用模型进行推理或重新训练。</span><span class="sxs-lookup"><span data-stu-id="926ce-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="926ce-108">因此，存储模型很重要。</span><span class="sxs-lookup"><span data-stu-id="926ce-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="926ce-109">使用类似下文详述的数据准备和模型训练管道时，请使用本文档后续部分中介绍的步骤保存和加载模型。</span><span class="sxs-lookup"><span data-stu-id="926ce-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="926ce-110">虽然此示例使用线性回归模型，但相同的过程适用于其他 ML.NET 算法。</span><span class="sxs-lookup"><span data-stu-id="926ce-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f, 125000f, 122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    }
};

// Create MLContext
MLContext mlContext = new MLContext();

// Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Define data preparation estimator
EstimatorChain<RegressionPredictionTransformer<LinearRegressionModelParameters>> pipelineEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .Append(mlContext.Regression.Trainers.Sdca());

// Train model
ITransformer trainedModel = pipelineEstimator.Fit(data);

// Save model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

<span data-ttu-id="926ce-111">由于大部分模型和数据准备管道都继承自同一组类，这些组件的保存和加载方法签名相同。</span><span class="sxs-lookup"><span data-stu-id="926ce-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="926ce-112">根据用例，可以将数据准备管道和模型合并为单个 [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601)（输出单个 [`ITransformer`](xref:Microsoft.ML.ITransformer)），也可将它们分隔，从而为其各自创建单独的 [`ITransformer`](xref:Microsoft.ML.ITransformer)。</span><span class="sxs-lookup"><span data-stu-id="926ce-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span>

## <a name="save-a-model-locally"></a><span data-ttu-id="926ce-113">在本地保存模型</span><span class="sxs-lookup"><span data-stu-id="926ce-113">Save a model locally</span></span>

<span data-ttu-id="926ce-114">保存模型时，需要以下两项：</span><span class="sxs-lookup"><span data-stu-id="926ce-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="926ce-115">模型的 [`ITransformer`](xref:Microsoft.ML.ITransformer)。</span><span class="sxs-lookup"><span data-stu-id="926ce-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="926ce-116">[`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) 预期输入的 [`ITransformer`](xref:Microsoft.ML.ITransformer)。</span><span class="sxs-lookup"><span data-stu-id="926ce-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="926ce-117">训练模型后，通过 [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save%2A) 方法使用输入数据的 `DataViewSchema` 将经过训练的模型保存到名为 `model.zip` 的文件中。</span><span class="sxs-lookup"><span data-stu-id="926ce-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save%2A) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span>

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="926ce-118">加载本地存储的模型</span><span class="sxs-lookup"><span data-stu-id="926ce-118">Load a model stored locally</span></span>

<span data-ttu-id="926ce-119">本地存储的模型可用于其他进程或应用程序，如 `ASP.NET Core` 和 `Serverless Web Applications`。</span><span class="sxs-lookup"><span data-stu-id="926ce-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="926ce-120">若要了解详细信息，请参阅[在 Web API 中使用 ML.NET](./serve-model-web-api-ml-net.md) 和[部署 ML.NET 无服务器 Web 应用](./serve-model-serverless-azure-functions-ml-net.md)操作说明文章。</span><span class="sxs-lookup"><span data-stu-id="926ce-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span>

<span data-ttu-id="926ce-121">在单独的应用程序或进程中，配合使用 [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load%2A) 方法和文件路径将经过训练的模型载入应用程序。</span><span class="sxs-lookup"><span data-stu-id="926ce-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load%2A) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="926ce-122">加载远程存储的模型</span><span class="sxs-lookup"><span data-stu-id="926ce-122">Load a model stored remotely</span></span>

<span data-ttu-id="926ce-123">若要将存储在远程位置的数据准备管道和模型加载到应用程序中，请使用 [`Stream`](xref:System.IO.Stream)，而不要使用 [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load%2A) 方法中的文件路径。</span><span class="sxs-lookup"><span data-stu-id="926ce-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load%2A) method.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema and ITransformers
DataViewSchema modelSchema;
ITransformer trainedModel;

// Load data prep pipeline and trained model
using (HttpClient client = new HttpClient())
{
    Stream modelFile = await client.GetStreamAsync("<YOUR-REMOTE-FILE-LOCATION>");

    trainedModel = mlContext.Model.Load(modelFile, out modelSchema);
}
```

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="926ce-124">使用单独的数据准备和模型管道</span><span class="sxs-lookup"><span data-stu-id="926ce-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="926ce-125">使用单独的数据准备和模型训练管道是可选方案。</span><span class="sxs-lookup"><span data-stu-id="926ce-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="926ce-126">管道的分离使得用户能够更轻松地检查已学习的模型参数。</span><span class="sxs-lookup"><span data-stu-id="926ce-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="926ce-127">对于预测，保存和加载包含数据准备和模型训练操作的单个管道更轻松。</span><span class="sxs-lookup"><span data-stu-id="926ce-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="926ce-128">使用单独的数据准备管道和模型时，流程与单个管道相同；但现在需要同时保存和加载两个管道。</span><span class="sxs-lookup"><span data-stu-id="926ce-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="926ce-129">给定单独的数据准备和模型训练管道：</span><span class="sxs-lookup"><span data-stu-id="926ce-129">Given separate data preparation and model training pipelines:</span></span>

```csharp
// Define data preparation estimator
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data preparation transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Pre-process data using data prep operations
IDataView transformedData = dataPrepTransformer.Transform(data);

// Train regression model
RegressionPredictionTransformer<LinearRegressionModelParameters> trainedModel = sdcaEstimator.Fit(transformedData);
```

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="926ce-130">保存数据准备管道和经过训练的模型</span><span class="sxs-lookup"><span data-stu-id="926ce-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="926ce-131">若要保存数据准备管道和经过训练的模型，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="926ce-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="926ce-132">加载数据准备管道和经过训练的模型</span><span class="sxs-lookup"><span data-stu-id="926ce-132">Load data preparation pipeline and trained model</span></span>

<span data-ttu-id="926ce-133">在单独的进程或应用程序中，同时加载数据准备管道和经过训练的模型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="926ce-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
