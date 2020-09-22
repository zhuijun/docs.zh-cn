---
title: 使用经过训练的模型进行预测
description: 了解如何使用经过训练的模型进行预测
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2e8263db289bed50e7437b695134458b8c07e0e5
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679568"
---
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="13d33-103">使用经过训练的模型进行预测</span><span class="sxs-lookup"><span data-stu-id="13d33-103">Make predictions with a trained model</span></span>

<span data-ttu-id="13d33-104">了解如何使用经过训练的模型进行预测</span><span class="sxs-lookup"><span data-stu-id="13d33-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="13d33-105">创建数据模型</span><span class="sxs-lookup"><span data-stu-id="13d33-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="13d33-106">输入数据</span><span class="sxs-lookup"><span data-stu-id="13d33-106">Input data</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="output-data"></a><span data-ttu-id="13d33-107">输出数据</span><span class="sxs-lookup"><span data-stu-id="13d33-107">Output data</span></span>

<span data-ttu-id="13d33-108">与 `Features` 和 `Label` 输入列名一样，ML.NET 为模型生成的预测值列提供默认名称。</span><span class="sxs-lookup"><span data-stu-id="13d33-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="13d33-109">名称可能因任务而异。</span><span class="sxs-lookup"><span data-stu-id="13d33-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="13d33-110">由于此示例中使用的算法是线性回归算法，输出列的默认名称为 `Score`，它由 `PredictedPrice` 属性上的 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 特性定义。</span><span class="sxs-lookup"><span data-stu-id="13d33-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="13d33-111">设置预测管道</span><span class="sxs-lookup"><span data-stu-id="13d33-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="13d33-112">无论是进行单一预测还是批量预测，都需要将预测管道加载到应用程序中。</span><span class="sxs-lookup"><span data-stu-id="13d33-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="13d33-113">此管道包含数据预处理转换以及经过训练的模型。</span><span class="sxs-lookup"><span data-stu-id="13d33-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="13d33-114">下面的代码片段从名为 `model.zip` 的文件中加载预测管道。</span><span class="sxs-lookup"><span data-stu-id="13d33-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="13d33-115">单一预测</span><span class="sxs-lookup"><span data-stu-id="13d33-115">Single prediction</span></span>

<span data-ttu-id="13d33-116">若要进行单一预测，请使用加载的预测管道创建 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。</span><span class="sxs-lookup"><span data-stu-id="13d33-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="13d33-117">然后，使用 [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A) 方法并将输入数据作为参数传入。</span><span class="sxs-lookup"><span data-stu-id="13d33-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="13d33-118">请注意，使用 [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A) 方法不要求输入为 [`IDataView`](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="13d33-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="13d33-119">这是因为它可以方便地内在化输入数据类型操作，以便能够传入输入数据类型的对象。</span><span class="sxs-lookup"><span data-stu-id="13d33-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="13d33-120">此外，由于 `CurrentPrice` 是尝试使用新数据进行预测的目标或标签，假设此时没有用于它的值。</span><span class="sxs-lookup"><span data-stu-id="13d33-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Input Data
HousingData inputData = new HousingData
{
    Size = 900f,
    HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
};

// Get Prediction
HousingPrediction prediction = predictionEngine.Predict(inputData);
```

<span data-ttu-id="13d33-121">如果访问 `prediction` 对象的 `Score` 属性，则应获得类似于 `150079` 的值。</span><span class="sxs-lookup"><span data-stu-id="13d33-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="13d33-122">多个预测</span><span class="sxs-lookup"><span data-stu-id="13d33-122">Multiple predictions</span></span>

<span data-ttu-id="13d33-123">给定以下数据，将其加载到 [`IDataView`](xref:Microsoft.ML.IDataView) 中。</span><span class="sxs-lookup"><span data-stu-id="13d33-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="13d33-124">在这种情况下，[`IDataView`](xref:Microsoft.ML.IDataView) 的名称可能是 `inputData`。</span><span class="sxs-lookup"><span data-stu-id="13d33-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="13d33-125">因为 `CurrentPrice` 是尝试使用新数据进行预测的目标或标签，所以假设此时没有用于它的值。</span><span class="sxs-lookup"><span data-stu-id="13d33-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f, 175000f, 210000f }
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f }
    }
};
```

<span data-ttu-id="13d33-126">然后，使用 [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) 方法应用数据转换并生成预测。</span><span class="sxs-lookup"><span data-stu-id="13d33-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="13d33-127">使用 [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) 方法检查预测值。</span><span class="sxs-lookup"><span data-stu-id="13d33-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="13d33-128">分数列中的预测值应如下所示：</span><span class="sxs-lookup"><span data-stu-id="13d33-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="13d33-129">观测</span><span class="sxs-lookup"><span data-stu-id="13d33-129">Observation</span></span> | <span data-ttu-id="13d33-130">预测</span><span class="sxs-lookup"><span data-stu-id="13d33-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="13d33-131">1</span><span class="sxs-lookup"><span data-stu-id="13d33-131">1</span></span> | <span data-ttu-id="13d33-132">144638.2</span><span class="sxs-lookup"><span data-stu-id="13d33-132">144638.2</span></span> |
| <span data-ttu-id="13d33-133">2</span><span class="sxs-lookup"><span data-stu-id="13d33-133">2</span></span> | <span data-ttu-id="13d33-134">150079.4</span><span class="sxs-lookup"><span data-stu-id="13d33-134">150079.4</span></span> |
| <span data-ttu-id="13d33-135">3</span><span class="sxs-lookup"><span data-stu-id="13d33-135">3</span></span> | <span data-ttu-id="13d33-136">107789.8</span><span class="sxs-lookup"><span data-stu-id="13d33-136">107789.8</span></span> |
