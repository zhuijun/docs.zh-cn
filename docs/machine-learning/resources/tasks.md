---
title: 机器学习任务
description: 浏览 ML.NET 中支持的不同机器学习任务和关联的任务。
ms.date: 12/23/2019
ms.openlocfilehash: e6e36bd65dbadb8cb7b8edbf9e2e82071c208378
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144443"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="08ff0-103">ML.NET 中的机器学习任务</span><span class="sxs-lookup"><span data-stu-id="08ff0-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="08ff0-104">机器学习任务是根据所询问的问题和可用数据进行的预测或推理的类型。</span><span class="sxs-lookup"><span data-stu-id="08ff0-104">A machine learning task is the type of prediction or inference being made, based on the problem or question that is being asked, and the available data.</span></span> <span data-ttu-id="08ff0-105">例如，分类任务将数据分配给类别，聚类分析任务根据相似性对数据进行分组。</span><span class="sxs-lookup"><span data-stu-id="08ff0-105">For example, the classification task assigns data to categories, and the clustering task groups data according to similarity.</span></span>

<span data-ttu-id="08ff0-106">机器学习任务依赖于数据中的模式，而不是显式编程。</span><span class="sxs-lookup"><span data-stu-id="08ff0-106">Machine learning tasks rely on patterns in the data rather than being explicitly programmed.</span></span>

<span data-ttu-id="08ff0-107">本文介绍了可以从 ML.NET 中选择的不同机器学习任务，以及一些常见用例。</span><span class="sxs-lookup"><span data-stu-id="08ff0-107">This article describes the different machine learning tasks that you can choose from in ML.NET and some common use cases.</span></span>

<span data-ttu-id="08ff0-108">决定适合场景的任务后，则需要选择最佳算法来训练模型。</span><span class="sxs-lookup"><span data-stu-id="08ff0-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="08ff0-109">本节列出了每个任务的可用算法。</span><span class="sxs-lookup"><span data-stu-id="08ff0-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="08ff0-110">二元分类</span><span class="sxs-lookup"><span data-stu-id="08ff0-110">Binary classification</span></span>

<span data-ttu-id="08ff0-111">[监管式机器学习](glossary.md#supervised-machine-learning)任务，用于预测数据实例所属的两个类（类别）。</span><span class="sxs-lookup"><span data-stu-id="08ff0-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="08ff0-112">分类算法输入是一组标记示例，其中每个标签为整数 0 或 1。</span><span class="sxs-lookup"><span data-stu-id="08ff0-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="08ff0-113">二元分类算法的输出是一个分类器，可用于预测未标记的新实例的类。</span><span class="sxs-lookup"><span data-stu-id="08ff0-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="08ff0-114">二元分类方案示例包括：</span><span class="sxs-lookup"><span data-stu-id="08ff0-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="08ff0-115">[了解 Twitter 评论的情绪](../tutorials/sentiment-analysis.md)，“正面”或“负面”。</span><span class="sxs-lookup"><span data-stu-id="08ff0-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="08ff0-116">诊断患者是否患有某种疾病。</span><span class="sxs-lookup"><span data-stu-id="08ff0-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="08ff0-117">决定是否要将电子邮件标记为“垃圾邮件”。</span><span class="sxs-lookup"><span data-stu-id="08ff0-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="08ff0-118">确定照片是否包含特定项，例如狗或水果。</span><span class="sxs-lookup"><span data-stu-id="08ff0-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="08ff0-119">有关详细信息，请参阅 Wikipedia 上的[二元分类](https://en.wikipedia.org/wiki/Binary_classification)一文。</span><span class="sxs-lookup"><span data-stu-id="08ff0-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="08ff0-120">二元分类训练程序</span><span class="sxs-lookup"><span data-stu-id="08ff0-120">Binary classification trainers</span></span>

<span data-ttu-id="08ff0-121">可以使用以下算法训练二元分类模型：</span><span class="sxs-lookup"><span data-stu-id="08ff0-121">You can train a binary classification model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="08ff0-122">二元分类输入和输出</span><span class="sxs-lookup"><span data-stu-id="08ff0-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="08ff0-123">为了通过二元分类获得最佳结果，应平衡训练数据（即正训练数据和负训练数据的数量相等）。</span><span class="sxs-lookup"><span data-stu-id="08ff0-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="08ff0-124">应在训练前处理缺失值。</span><span class="sxs-lookup"><span data-stu-id="08ff0-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="08ff0-125">输入标签列数据必须为 <xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="08ff0-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="08ff0-126">输入特征列数据必须为 <xref:System.Single> 的固定大小向量。</span><span class="sxs-lookup"><span data-stu-id="08ff0-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="08ff0-127">这些训练程序将输出以下列：</span><span class="sxs-lookup"><span data-stu-id="08ff0-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="08ff0-128">输出列名称</span><span class="sxs-lookup"><span data-stu-id="08ff0-128">Output Column Name</span></span> | <span data-ttu-id="08ff0-129">列名称</span><span class="sxs-lookup"><span data-stu-id="08ff0-129">Column Type</span></span> | <span data-ttu-id="08ff0-130">描述</span><span class="sxs-lookup"><span data-stu-id="08ff0-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="08ff0-131">由模型计算得出的原始分数</span><span class="sxs-lookup"><span data-stu-id="08ff0-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="08ff0-132">预测的标签，基于分数符号。</span><span class="sxs-lookup"><span data-stu-id="08ff0-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="08ff0-133">负分数映射到 `false`，正分数映射到 `true`。</span><span class="sxs-lookup"><span data-stu-id="08ff0-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="08ff0-134">多类分类</span><span class="sxs-lookup"><span data-stu-id="08ff0-134">Multiclass classification</span></span>

<span data-ttu-id="08ff0-135">[监管式机器学习](glossary.md#supervised-machine-learning)任务，用于预测数据实例的类（类别）。</span><span class="sxs-lookup"><span data-stu-id="08ff0-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="08ff0-136">分类算法输入是一组标记示例。</span><span class="sxs-lookup"><span data-stu-id="08ff0-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="08ff0-137">每个标签通常以文本形式开始。</span><span class="sxs-lookup"><span data-stu-id="08ff0-137">Each label normally starts as text.</span></span> <span data-ttu-id="08ff0-138">然后通过 TermTransform 运行，它可将其转换为 Key（数字）类型。</span><span class="sxs-lookup"><span data-stu-id="08ff0-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="08ff0-139">分类算法的输出是一个分类器，可用于预测未标记的新实例的类。</span><span class="sxs-lookup"><span data-stu-id="08ff0-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="08ff0-140">多类分类方案示例包括：</span><span class="sxs-lookup"><span data-stu-id="08ff0-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="08ff0-141">确定狗的品种是“西伯利亚哈士奇”、“金毛寻回犬”、“贵宾犬”等。</span><span class="sxs-lookup"><span data-stu-id="08ff0-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="08ff0-142">了解电影评论是“正面”、“中立”还是“负面”。</span><span class="sxs-lookup"><span data-stu-id="08ff0-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="08ff0-143">将酒店评语分类为“位置”、“价格”、“整洁度”等。</span><span class="sxs-lookup"><span data-stu-id="08ff0-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="08ff0-144">有关详细信息，请参阅 Wikipedia 上的[多类分类](https://en.wikipedia.org/wiki/Multiclass_classification)一文。</span><span class="sxs-lookup"><span data-stu-id="08ff0-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="08ff0-145">一个与所有升级任何[二元分类学习器](#binary-classification)，以便对多类数据集进行操作。</span><span class="sxs-lookup"><span data-stu-id="08ff0-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="08ff0-146">有关详细信息，请参阅 [Wikipedia](https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)。</span><span class="sxs-lookup"><span data-stu-id="08ff0-146">More information on [Wikipedia](https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="08ff0-147">多类分类训练程序</span><span class="sxs-lookup"><span data-stu-id="08ff0-147">Multiclass classification trainers</span></span>

<span data-ttu-id="08ff0-148">可以使用以下训练算法训练多类分类模型：</span><span class="sxs-lookup"><span data-stu-id="08ff0-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="08ff0-149">多类分类输入和输出</span><span class="sxs-lookup"><span data-stu-id="08ff0-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="08ff0-150">输入标签列数据必须为 [key](xref:Microsoft.ML.Data.KeyDataViewType) 类型。</span><span class="sxs-lookup"><span data-stu-id="08ff0-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="08ff0-151">特征列必须为 <xref:System.Single> 的固定大小向量。</span><span class="sxs-lookup"><span data-stu-id="08ff0-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="08ff0-152">该训练程序输出以下列：</span><span class="sxs-lookup"><span data-stu-id="08ff0-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="08ff0-153">输出名称</span><span class="sxs-lookup"><span data-stu-id="08ff0-153">Output Name</span></span> | <span data-ttu-id="08ff0-154">类型</span><span class="sxs-lookup"><span data-stu-id="08ff0-154">Type</span></span> | <span data-ttu-id="08ff0-155">描述</span><span class="sxs-lookup"><span data-stu-id="08ff0-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="08ff0-156"><xref:System.Single> 的向量</span><span class="sxs-lookup"><span data-stu-id="08ff0-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="08ff0-157">所有类的分数。</span><span class="sxs-lookup"><span data-stu-id="08ff0-157">The scores of all classes.</span></span> <span data-ttu-id="08ff0-158">值越高意味着落入相关类的概率越高。</span><span class="sxs-lookup"><span data-stu-id="08ff0-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="08ff0-159">如果第 i 个元素具有最大值，则预测的标签索引为 i。</span><span class="sxs-lookup"><span data-stu-id="08ff0-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="08ff0-160">请注意，i 是从零开始的索引。</span><span class="sxs-lookup"><span data-stu-id="08ff0-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="08ff0-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) 类型</span><span class="sxs-lookup"><span data-stu-id="08ff0-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="08ff0-162">预测标签的索引。</span><span class="sxs-lookup"><span data-stu-id="08ff0-162">The predicted label's index.</span></span> <span data-ttu-id="08ff0-163">如果其值为 i，则实际标签为键值输入标签类型中的第 i 个类别。</span><span class="sxs-lookup"><span data-stu-id="08ff0-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="08ff0-164">回归测试</span><span class="sxs-lookup"><span data-stu-id="08ff0-164">Regression</span></span>

<span data-ttu-id="08ff0-165">[监管式机器学习](glossary.md#supervised-machine-learning)任务，用于从一组相关特征中预测标签值。</span><span class="sxs-lookup"><span data-stu-id="08ff0-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="08ff0-166">标签可以是任何实际值，而不是像在分类任务中那样来自一组有限的值。</span><span class="sxs-lookup"><span data-stu-id="08ff0-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="08ff0-167">回归算法模拟其相关特征上的标签依赖关系，以确定标签将如何随着特征值的变化而变化。</span><span class="sxs-lookup"><span data-stu-id="08ff0-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="08ff0-168">回归算法输入是一组带已知值标签的示例。</span><span class="sxs-lookup"><span data-stu-id="08ff0-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="08ff0-169">回归算法输出是一个函数，可用于预测任何一组新输入特征的标签值。</span><span class="sxs-lookup"><span data-stu-id="08ff0-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="08ff0-170">回归方案示例包括：</span><span class="sxs-lookup"><span data-stu-id="08ff0-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="08ff0-171">基于房子特性（如卧室数量、位置或大小）来预测房价。</span><span class="sxs-lookup"><span data-stu-id="08ff0-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="08ff0-172">基于历史数据和当前市场趋势预测将来的股票价格。</span><span class="sxs-lookup"><span data-stu-id="08ff0-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="08ff0-173">基于广告预算预测产品销售。</span><span class="sxs-lookup"><span data-stu-id="08ff0-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="08ff0-174">回归训练程序</span><span class="sxs-lookup"><span data-stu-id="08ff0-174">Regression trainers</span></span>

<span data-ttu-id="08ff0-175">可以使用以下算法训练回归模型：</span><span class="sxs-lookup"><span data-stu-id="08ff0-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="08ff0-176">回归输入和输出</span><span class="sxs-lookup"><span data-stu-id="08ff0-176">Regression inputs and outputs</span></span>

<span data-ttu-id="08ff0-177">输入标签列数据必须为 <xref:System.Single>。</span><span class="sxs-lookup"><span data-stu-id="08ff0-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="08ff0-178">此任务的训练程序输出以下列：</span><span class="sxs-lookup"><span data-stu-id="08ff0-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="08ff0-179">输出名称</span><span class="sxs-lookup"><span data-stu-id="08ff0-179">Output Name</span></span> | <span data-ttu-id="08ff0-180">类型</span><span class="sxs-lookup"><span data-stu-id="08ff0-180">Type</span></span> | <span data-ttu-id="08ff0-181">描述</span><span class="sxs-lookup"><span data-stu-id="08ff0-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="08ff0-182">模型预测的原始分数</span><span class="sxs-lookup"><span data-stu-id="08ff0-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="08ff0-183">聚类分析</span><span class="sxs-lookup"><span data-stu-id="08ff0-183">Clustering</span></span>

<span data-ttu-id="08ff0-184">[非监管式机器学习](glossary.md#unsupervised-machine-learning)任务，用于将数据实例分组到包含类似特性的群集。</span><span class="sxs-lookup"><span data-stu-id="08ff0-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="08ff0-185">聚类分析还可用来识别可能无法通过浏览或简单的观察以逻辑方式推导出的数据集中的关系。</span><span class="sxs-lookup"><span data-stu-id="08ff0-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="08ff0-186">聚类分析算法的输入和输出取决于选择的方法。</span><span class="sxs-lookup"><span data-stu-id="08ff0-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="08ff0-187">可以采取分发、质心、连接或基于密度的方法。</span><span class="sxs-lookup"><span data-stu-id="08ff0-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="08ff0-188">ML.NET 当前支持使用 K 平均值聚类分析的基于质心的方法。</span><span class="sxs-lookup"><span data-stu-id="08ff0-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="08ff0-189">聚类分析方案示例包括：</span><span class="sxs-lookup"><span data-stu-id="08ff0-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="08ff0-190">基于酒店选择的习惯和特征来了解酒店来宾群。</span><span class="sxs-lookup"><span data-stu-id="08ff0-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="08ff0-191">确定客户群和人口统计信息来帮助生成目标广告活动。</span><span class="sxs-lookup"><span data-stu-id="08ff0-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="08ff0-192">基于生产指标对清单进行分类。</span><span class="sxs-lookup"><span data-stu-id="08ff0-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="08ff0-193">聚类分析训练程序</span><span class="sxs-lookup"><span data-stu-id="08ff0-193">Clustering trainer</span></span>

<span data-ttu-id="08ff0-194">可以使用以下算法训练聚类分析模型：</span><span class="sxs-lookup"><span data-stu-id="08ff0-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="08ff0-195">聚类分析输入和输出</span><span class="sxs-lookup"><span data-stu-id="08ff0-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="08ff0-196">输入特征数据必须为 <xref:System.Single>。</span><span class="sxs-lookup"><span data-stu-id="08ff0-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="08ff0-197">无需标签。</span><span class="sxs-lookup"><span data-stu-id="08ff0-197">No labels are needed.</span></span>

<span data-ttu-id="08ff0-198">该训练程序输出以下列：</span><span class="sxs-lookup"><span data-stu-id="08ff0-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="08ff0-199">输出名称</span><span class="sxs-lookup"><span data-stu-id="08ff0-199">Output Name</span></span> | <span data-ttu-id="08ff0-200">类型</span><span class="sxs-lookup"><span data-stu-id="08ff0-200">Type</span></span> | <span data-ttu-id="08ff0-201">描述</span><span class="sxs-lookup"><span data-stu-id="08ff0-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="08ff0-202"><xref:System.Single> 的向量</span><span class="sxs-lookup"><span data-stu-id="08ff0-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="08ff0-203">给定数据点到所有群集的质心的距离</span><span class="sxs-lookup"><span data-stu-id="08ff0-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="08ff0-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) 类型</span><span class="sxs-lookup"><span data-stu-id="08ff0-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="08ff0-205">模型预测的最接近的群集的索引。</span><span class="sxs-lookup"><span data-stu-id="08ff0-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="08ff0-206">异常情况检测</span><span class="sxs-lookup"><span data-stu-id="08ff0-206">Anomaly detection</span></span>

<span data-ttu-id="08ff0-207">此任务使用主体组件分析 (PCA) 创建异常情况检测模型。</span><span class="sxs-lookup"><span data-stu-id="08ff0-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="08ff0-208">基于 PCA 的异常情况检测有助于在以下场景中构建模型：可以很轻松地从一个类中获得定型数据（例如有效事务），但难以获得目标异常的足够示例。</span><span class="sxs-lookup"><span data-stu-id="08ff0-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="08ff0-209">PCA 是机器学习中已建立的一种技术，由于它揭示了数据的内部结构，并解释了数据中的差异，因此经常被用于探索性数据分析。</span><span class="sxs-lookup"><span data-stu-id="08ff0-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="08ff0-210">PCA 的工作方式是通过分析包含多个变量的数据。</span><span class="sxs-lookup"><span data-stu-id="08ff0-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="08ff0-211">它查找变量之间的关联性，并确定最能捕捉结果差异的值的组合。</span><span class="sxs-lookup"><span data-stu-id="08ff0-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="08ff0-212">这些组合的特性值用于创建一个更紧凑的特性空间，称为主体组件。</span><span class="sxs-lookup"><span data-stu-id="08ff0-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="08ff0-213">异常情况检测包含机器学习中的许多重要任务：</span><span class="sxs-lookup"><span data-stu-id="08ff0-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="08ff0-214">识别潜在的欺诈交易。</span><span class="sxs-lookup"><span data-stu-id="08ff0-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="08ff0-215">指示发生了网络入侵的学习模式。</span><span class="sxs-lookup"><span data-stu-id="08ff0-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="08ff0-216">发现异常的患者群集。</span><span class="sxs-lookup"><span data-stu-id="08ff0-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="08ff0-217">检查输入系统的值。</span><span class="sxs-lookup"><span data-stu-id="08ff0-217">Checking values entered into a system.</span></span>

<span data-ttu-id="08ff0-218">根据定义，异常情况属于罕见事件，因此很难收集具有代表性的数据样本用于建模。</span><span class="sxs-lookup"><span data-stu-id="08ff0-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="08ff0-219">此类别中包含的算法是专门设计用来解决使用不平衡数据集建立和定型模型的核心挑战。</span><span class="sxs-lookup"><span data-stu-id="08ff0-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="08ff0-220">异常情况检测训练程序</span><span class="sxs-lookup"><span data-stu-id="08ff0-220">Anomaly detection trainer</span></span>

<span data-ttu-id="08ff0-221">可以使用以下算法训练异常情况检测模型：</span><span class="sxs-lookup"><span data-stu-id="08ff0-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="08ff0-222">异常情况检测输入和输出</span><span class="sxs-lookup"><span data-stu-id="08ff0-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="08ff0-223">输入特征必须为 <xref:System.Single> 的固定大小向量。</span><span class="sxs-lookup"><span data-stu-id="08ff0-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="08ff0-224">该训练程序输出以下列：</span><span class="sxs-lookup"><span data-stu-id="08ff0-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="08ff0-225">输出名称</span><span class="sxs-lookup"><span data-stu-id="08ff0-225">Output Name</span></span> | <span data-ttu-id="08ff0-226">类型</span><span class="sxs-lookup"><span data-stu-id="08ff0-226">Type</span></span> | <span data-ttu-id="08ff0-227">描述</span><span class="sxs-lookup"><span data-stu-id="08ff0-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="08ff0-228">由异常情况检测模型计算得出的非负无界分数</span><span class="sxs-lookup"><span data-stu-id="08ff0-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="08ff0-229">true/false 值表示输入是否异常 (PredictedLabel=true) 或 (PredictedLabel=false)</span><span class="sxs-lookup"><span data-stu-id="08ff0-229">A true/false value representing whether the input is an anomaly (PredictedLabel=true) or not (PredictedLabel=false)</span></span> |

## <a name="ranking"></a><span data-ttu-id="08ff0-230">排名</span><span class="sxs-lookup"><span data-stu-id="08ff0-230">Ranking</span></span>

<span data-ttu-id="08ff0-231">排名任务从一组标记的示例构建排名程序。</span><span class="sxs-lookup"><span data-stu-id="08ff0-231">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="08ff0-232">该示例集由实例组组成，这些实例组可以使用给定的标准进行评分。</span><span class="sxs-lookup"><span data-stu-id="08ff0-232">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="08ff0-233">每个实例的排名标签是 { 0, 1, 2, 3, 4 }。</span><span class="sxs-lookup"><span data-stu-id="08ff0-233">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="08ff0-234">排名程序定型为用每个实例的未知分数对新实例组进行排名。</span><span class="sxs-lookup"><span data-stu-id="08ff0-234">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="08ff0-235">ML.NET 排名学习器基于[机器已学习的排名](https://en.wikipedia.org/wiki/Learning_to_rank)。</span><span class="sxs-lookup"><span data-stu-id="08ff0-235">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="08ff0-236">排名训练算法</span><span class="sxs-lookup"><span data-stu-id="08ff0-236">Ranking training algorithms</span></span>

<span data-ttu-id="08ff0-237">可以使用以下算法训练排名模型：</span><span class="sxs-lookup"><span data-stu-id="08ff0-237">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="08ff0-238">排名输入和输出</span><span class="sxs-lookup"><span data-stu-id="08ff0-238">Ranking input and outputs</span></span>

<span data-ttu-id="08ff0-239">输入标签数据类型必须为 [key](xref:Microsoft.ML.Data.KeyDataViewType) 类型或 <xref:System.Single>。</span><span class="sxs-lookup"><span data-stu-id="08ff0-239">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="08ff0-240">标签的值决定相关性，其中较高的值表示较高的相关性。</span><span class="sxs-lookup"><span data-stu-id="08ff0-240">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="08ff0-241">如果标签为 [key](xref:Microsoft.ML.Data.KeyDataViewType) 类型，则键索引为相关性值，其中最小索引是最不相关的。</span><span class="sxs-lookup"><span data-stu-id="08ff0-241">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="08ff0-242">如果标签为 <xref:System.Single>，则较大的值表示较高的相关性。</span><span class="sxs-lookup"><span data-stu-id="08ff0-242">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="08ff0-243">特征数据必须为 <xref:System.Single> 的固定大小向量，输入行组列必须为 [key](xref:Microsoft.ML.Data.KeyDataViewType) 类型。</span><span class="sxs-lookup"><span data-stu-id="08ff0-243">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="08ff0-244">该训练程序输出以下列：</span><span class="sxs-lookup"><span data-stu-id="08ff0-244">This trainer outputs the following:</span></span>

| <span data-ttu-id="08ff0-245">输出名称</span><span class="sxs-lookup"><span data-stu-id="08ff0-245">Output Name</span></span> | <span data-ttu-id="08ff0-246">类型</span><span class="sxs-lookup"><span data-stu-id="08ff0-246">Type</span></span> | <span data-ttu-id="08ff0-247">描述</span><span class="sxs-lookup"><span data-stu-id="08ff0-247">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="08ff0-248">由模型计算以确定预测的无界分数</span><span class="sxs-lookup"><span data-stu-id="08ff0-248">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="08ff0-249">建议</span><span class="sxs-lookup"><span data-stu-id="08ff0-249">Recommendation</span></span>

<span data-ttu-id="08ff0-250">推荐任务支持生成推荐产品或服务的列表。</span><span class="sxs-lookup"><span data-stu-id="08ff0-250">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="08ff0-251">ML.NET 使用[矩阵因子分解 (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29)，这是一种[协作筛选](https://en.wikipedia.org/wiki/Collaborative_filtering)算法，当目录中有历史产品评级数据时，推荐使用该算法。</span><span class="sxs-lookup"><span data-stu-id="08ff0-251">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="08ff0-252">例如，你为用户提供历史电影评级数据，并希望向他们推荐接下来可能观看的其他电影。</span><span class="sxs-lookup"><span data-stu-id="08ff0-252">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="08ff0-253">建议训练算法</span><span class="sxs-lookup"><span data-stu-id="08ff0-253">Recommendation training algorithms</span></span>

<span data-ttu-id="08ff0-254">可以使用以下算法训练建议模型：</span><span class="sxs-lookup"><span data-stu-id="08ff0-254">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a><span data-ttu-id="08ff0-255">预测</span><span class="sxs-lookup"><span data-stu-id="08ff0-255">Forecasting</span></span>

<span data-ttu-id="08ff0-256">预测任务使用过去的时序数据来预测将来的行为。</span><span class="sxs-lookup"><span data-stu-id="08ff0-256">The forecasting task use past time-series data to make predictions about future behavior.</span></span> <span data-ttu-id="08ff0-257">适用于预测的场景包括天气预测、季节性销售预测和预测维护。</span><span class="sxs-lookup"><span data-stu-id="08ff0-257">Scenarios applicable to forecasting include weather forecasting, seasonal sales predictions, and predictive maintenance,</span></span>

### <a name="forecasting-trainers"></a><span data-ttu-id="08ff0-258">预测训练器</span><span class="sxs-lookup"><span data-stu-id="08ff0-258">Forecasting trainers</span></span>

<span data-ttu-id="08ff0-259">可以使用以下算法训练预测模型：</span><span class="sxs-lookup"><span data-stu-id="08ff0-259">You can train a forecasting model with the following algorithm:</span></span>

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
