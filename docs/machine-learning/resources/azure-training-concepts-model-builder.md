---
title: 模型生成器 Azure 培训资源
description: Azure 机器学习资源指南
ms.topic: reference
ms.date: 06/01/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: d9eb5560ef33f8f80dbe53e17087c606a8697378
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289468"
---
# <a name="model-builder-azure-training-resources"></a><span data-ttu-id="80849-103">模型生成器 Azure 培训资源</span><span class="sxs-lookup"><span data-stu-id="80849-103">Model Builder Azure Training Resources</span></span>

<span data-ttu-id="80849-104">以下指南可帮助你详细了解用于通过模型生成器在 Azure 中训练模型的资源。</span><span class="sxs-lookup"><span data-stu-id="80849-104">The following is a guide to help you learn more about resources used to train models in Azure with Model Builder.</span></span>

## <a name="what-is-an-azure-machine-learning-experiment"></a><span data-ttu-id="80849-105">什么是 Azure 机器学习试验？</span><span class="sxs-lookup"><span data-stu-id="80849-105">What is an Azure Machine Learning experiment?</span></span>

<span data-ttu-id="80849-106">Azure 机器学习试验是一项资源，需要先生成它才能在 Azure 上运行模型生成器训练。</span><span class="sxs-lookup"><span data-stu-id="80849-106">An Azure Machine Learning experiment is a resource that needs to be created before running Model Builder training on Azure.</span></span>

<span data-ttu-id="80849-107">试验会封装一次或多次机器学习训练运行的配置和结果。</span><span class="sxs-lookup"><span data-stu-id="80849-107">The experiment encapsulates the configuration and results for one or more machine learning training runs.</span></span> <span data-ttu-id="80849-108">试验属于特定工作区。</span><span class="sxs-lookup"><span data-stu-id="80849-108">Experiments belong to a specific workspace.</span></span> <span data-ttu-id="80849-109">第一次创建试验时，将在该工作区中注册其名称。</span><span class="sxs-lookup"><span data-stu-id="80849-109">The first time an experiment is created, its name is registered in the workspace.</span></span> <span data-ttu-id="80849-110">如果任何后续运行使用相同的试验名称，则该运行将记录为同一试验的一部分。</span><span class="sxs-lookup"><span data-stu-id="80849-110">Any subsequent runs - if the same experiment name is used - are logged as part of the same experiment.</span></span> <span data-ttu-id="80849-111">否则会创建新试验。</span><span class="sxs-lookup"><span data-stu-id="80849-111">Otherwise, a new experiment is created.</span></span>

## <a name="what-is-an-azure-machine-learning-workspace"></a><span data-ttu-id="80849-112">什么是 Azure 机器学习工作区？</span><span class="sxs-lookup"><span data-stu-id="80849-112">What is an Azure Machine Learning workspace?</span></span>

<span data-ttu-id="80849-113">工作区是一项 Azure 机器学习资源，它为在运行过程中创建的所有 Azure 机器学习资源和项目提供了一个中心位置。</span><span class="sxs-lookup"><span data-stu-id="80849-113">A workspace is an Azure Machine Learning resource that provides a central place for all Azure Machine Learning resources and artifacts created as part of training run.</span></span>

<span data-ttu-id="80849-114">若要创建 Azure 机器学习工作区，需要满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="80849-114">To create an Azure Machine Learning workspace, the following are required:</span></span>

- <span data-ttu-id="80849-115">姓名:工作区的名称介于 3-33 个字符之间。</span><span class="sxs-lookup"><span data-stu-id="80849-115">Name: A name for your workspace between 3-33 characters.</span></span> <span data-ttu-id="80849-116">名称只能包含字母数字字符和连字符。</span><span class="sxs-lookup"><span data-stu-id="80849-116">Names may only contain alphanumeric characters and hyphens.</span></span>
- <span data-ttu-id="80849-117">地区：工作区和资源部署到的数据中心的地理位置。</span><span class="sxs-lookup"><span data-stu-id="80849-117">Region: The geographic location of the data center where your workspace and resources are deployed to.</span></span> <span data-ttu-id="80849-118">建议选择靠近你或你的客户的位置。</span><span class="sxs-lookup"><span data-stu-id="80849-118">It is recommended that you choose a location close to where you or your customers are.</span></span>
- <span data-ttu-id="80849-119">资源组：用于容纳 Azure 解决方案所有相关资源的容器。</span><span class="sxs-lookup"><span data-stu-id="80849-119">Resource group: A container that contains all related resources for an Azure solution.</span></span>

## <a name="what-is-an-azure-machine-learning-compute"></a><span data-ttu-id="80849-120">什么是 Azure 机器学习计算？</span><span class="sxs-lookup"><span data-stu-id="80849-120">What is an Azure Machine Learning compute?</span></span>

<span data-ttu-id="80849-121">Azure 机器学习计算是基于云的 Linux VM，用于训练。</span><span class="sxs-lookup"><span data-stu-id="80849-121">An Azure Machine Learning compute is a cloud-based Linux VM used for training.</span></span>

<span data-ttu-id="80849-122">若要创建 Azure 机器学习工作区，需要满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="80849-122">To create an Azure Machine Learning workspace, the following are required:</span></span>

- <span data-ttu-id="80849-123">姓名:工作区的名称介于 2-16 个字符之间。</span><span class="sxs-lookup"><span data-stu-id="80849-123">Name: A name for your workspace between 2-16 characters.</span></span> <span data-ttu-id="80849-124">名称只能包含字母数字字符和连字符。</span><span class="sxs-lookup"><span data-stu-id="80849-124">Names may only contain alphanumeric characters and hyphens.</span></span>
- <span data-ttu-id="80849-125">计算大小</span><span class="sxs-lookup"><span data-stu-id="80849-125">Compute size</span></span>

    <span data-ttu-id="80849-126">模型生成器可以使用以下 GPU 优化的计算类型之一：</span><span class="sxs-lookup"><span data-stu-id="80849-126">Model Builder can use one of the following GPU-optimized compute types:</span></span>

    | <span data-ttu-id="80849-127">大小</span><span class="sxs-lookup"><span data-stu-id="80849-127">Size</span></span> | <span data-ttu-id="80849-128">vCPU</span><span class="sxs-lookup"><span data-stu-id="80849-128">vCPU</span></span> | <span data-ttu-id="80849-129">内存: GiB</span><span class="sxs-lookup"><span data-stu-id="80849-129">Memory: GiB</span></span> | <span data-ttu-id="80849-130">临时存储 (SSD) GiB</span><span class="sxs-lookup"><span data-stu-id="80849-130">Temp storage (SSD) GiB</span></span> | <span data-ttu-id="80849-131">GPU</span><span class="sxs-lookup"><span data-stu-id="80849-131">GPU</span></span> | <span data-ttu-id="80849-132">GPU 内存：GiB</span><span class="sxs-lookup"><span data-stu-id="80849-132">GPU memory: GiB</span></span> | <span data-ttu-id="80849-133">最大数据磁盘数</span><span class="sxs-lookup"><span data-stu-id="80849-133">Max data disks</span></span> | <span data-ttu-id="80849-134">最大 NIC 数</span><span class="sxs-lookup"><span data-stu-id="80849-134">Max NICs</span></span> |
    |---|---|---|---|---|---|---|---|
    | <span data-ttu-id="80849-135">Standard_NC12</span><span class="sxs-lookup"><span data-stu-id="80849-135">Standard_NC12</span></span>   | <span data-ttu-id="80849-136">12</span><span class="sxs-lookup"><span data-stu-id="80849-136">12</span></span> | <span data-ttu-id="80849-137">112</span><span class="sxs-lookup"><span data-stu-id="80849-137">112</span></span> | <span data-ttu-id="80849-138">680</span><span class="sxs-lookup"><span data-stu-id="80849-138">680</span></span>  | <span data-ttu-id="80849-139">2</span><span class="sxs-lookup"><span data-stu-id="80849-139">2</span></span> | <span data-ttu-id="80849-140">24</span><span class="sxs-lookup"><span data-stu-id="80849-140">24</span></span> | <span data-ttu-id="80849-141">48</span><span class="sxs-lookup"><span data-stu-id="80849-141">48</span></span> | <span data-ttu-id="80849-142">2</span><span class="sxs-lookup"><span data-stu-id="80849-142">2</span></span> |
    | <span data-ttu-id="80849-143">Standard_NC24</span><span class="sxs-lookup"><span data-stu-id="80849-143">Standard_NC24</span></span>   | <span data-ttu-id="80849-144">24</span><span class="sxs-lookup"><span data-stu-id="80849-144">24</span></span> | <span data-ttu-id="80849-145">224</span><span class="sxs-lookup"><span data-stu-id="80849-145">224</span></span> | <span data-ttu-id="80849-146">1440</span><span class="sxs-lookup"><span data-stu-id="80849-146">1440</span></span> | <span data-ttu-id="80849-147">4</span><span class="sxs-lookup"><span data-stu-id="80849-147">4</span></span> | <span data-ttu-id="80849-148">48</span><span class="sxs-lookup"><span data-stu-id="80849-148">48</span></span> | <span data-ttu-id="80849-149">64</span><span class="sxs-lookup"><span data-stu-id="80849-149">64</span></span> | <span data-ttu-id="80849-150">4</span><span class="sxs-lookup"><span data-stu-id="80849-150">4</span></span> |

    <span data-ttu-id="80849-151">有关 GPU 优化计算类型的更多详细信息，请访问 [NC 系列 Linux VM 文档](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json)。</span><span class="sxs-lookup"><span data-stu-id="80849-151">Visit the [NC-series Linux VM documentation](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) for more details on GPU optimized compute types.</span></span>
- <span data-ttu-id="80849-152">计算优先级</span><span class="sxs-lookup"><span data-stu-id="80849-152">Compute priority</span></span>

  - <span data-ttu-id="80849-153">低优先级：适用于执行时间较短的任务。</span><span class="sxs-lookup"><span data-stu-id="80849-153">Low-priority: Suited for tasks with shorter execution times.</span></span> <span data-ttu-id="80849-154">可能会受到中断和缺乏可用性的影响。</span><span class="sxs-lookup"><span data-stu-id="80849-154">May be impacted by interruptions and lack of availability.</span></span> <span data-ttu-id="80849-155">通常成本较低，因为它充分利用了 Azure 中的过剩容量。</span><span class="sxs-lookup"><span data-stu-id="80849-155">Usually costs less because it takes advantage of surplus capacity in Azure.</span></span>
  - <span data-ttu-id="80849-156">专用：适用于任何持续时间的任务，特别是长时间运行的作业。</span><span class="sxs-lookup"><span data-stu-id="80849-156">Dedicated: Suited for tasks of any duration, but especially long-running jobs.</span></span> <span data-ttu-id="80849-157">不受中断或缺乏可用性影响。</span><span class="sxs-lookup"><span data-stu-id="80849-157">Not impacted by interruptions or lack of availability.</span></span> <span data-ttu-id="80849-158">通常成本更高，因为它在 Azure 中为任务保留一组专用计算资源。</span><span class="sxs-lookup"><span data-stu-id="80849-158">Usually costs more because it reserves a dedicated set of compute resources in Azure for your tasks.</span></span>

## <a name="training"></a><span data-ttu-id="80849-159">训练</span><span class="sxs-lookup"><span data-stu-id="80849-159">Training</span></span>

<span data-ttu-id="80849-160">在 Azure 上训练仅适用于模型生成器图像分类方案。</span><span class="sxs-lookup"><span data-stu-id="80849-160">Training on Azure is only available for the Model Builder image classification scenario.</span></span> <span data-ttu-id="80849-161">用于训练这些模型的算法是基于 ResNet50 体系结构的深度神经网络。</span><span class="sxs-lookup"><span data-stu-id="80849-161">The algorithm used to train these models is a Deep Neural Network based on the ResNet50 architecture.</span></span> <span data-ttu-id="80849-162">训练过程需要一定的时间，并且根据所选计算的大小和数据量，所需时间可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="80849-162">The training process takes some time and the amount of time may vary depending on the size of compute selected as well as amount of data.</span></span> <span data-ttu-id="80849-163">第一次对模型进行训练时，由于必须预配资源，训练时间可能稍长。</span><span class="sxs-lookup"><span data-stu-id="80849-163">The first time a model is trained, you can expect a slightly longer training time because resources have to be provisioned.</span></span> <span data-ttu-id="80849-164">可以在 Visual Studio 中选择“监视 Azure 门户中的当前运行”链接以跟踪运行进度。</span><span class="sxs-lookup"><span data-stu-id="80849-164">You can track the progress of your runs by selecting the "Monitor current run in Azure portal" link in Visual Studio.</span></span>

## <a name="results"></a><span data-ttu-id="80849-165">结果</span><span class="sxs-lookup"><span data-stu-id="80849-165">Results</span></span>

<span data-ttu-id="80849-166">训练完成后，会将两个项目添加到你的解决方案，它们包含以下后缀：</span><span class="sxs-lookup"><span data-stu-id="80849-166">Once training is complete, two projects are added to your solution with the following suffixes:</span></span>

- <span data-ttu-id="80849-167">*ConsoleApp*：C# .Net Core 控制台应用程序，提供用于生成预测管道和进行预测的起始代码。</span><span class="sxs-lookup"><span data-stu-id="80849-167">*ConsoleApp*: A C# .NET Core console application that provides starter code to build the prediction pipeline and make predictions.</span></span>
- <span data-ttu-id="80849-168">*模型*：C# .NET Standard 应用程序，包含多个数据模型，它们定义了输入和输出模型数据的架构以及以下资产：</span><span class="sxs-lookup"><span data-stu-id="80849-168">*Model*: A C# .NET Standard application that contains the data models that define the schema of input and output model data as well as the following assets:</span></span>

  - <span data-ttu-id="80849-169">bestModel.onnx：Open Neural Network Exchange (ONNX) 格式的模型序列化版本。</span><span class="sxs-lookup"><span data-stu-id="80849-169">bestModel.onnx: A serialized version of the model in Open Neural Network Exchange (ONNX) format.</span></span> <span data-ttu-id="80849-170">ONNX 是 AI 模型的开源格式，它支持 ML.NET、PyTorch 和 TensorFlow 等框架之间的互操作性。</span><span class="sxs-lookup"><span data-stu-id="80849-170">ONNX is an open source format for AI models that supports interoperability between frameworks like ML.NET, PyTorch and TensorFlow.</span></span>
  - <span data-ttu-id="80849-171">bestModelMap.json：进行预测以将模型输出映射到文本类别时使用的类别列表。</span><span class="sxs-lookup"><span data-stu-id="80849-171">bestModelMap.json: A list of categories used when making predictions to map the model output to a text category.</span></span>
  - <span data-ttu-id="80849-172">MLModel.zip：ML.NET 预测管道的序列化版本，它使用 bestModel.onnx 模型的序列化版本进行预测，使用 `bestModelMap.json` 文件映射输出。</span><span class="sxs-lookup"><span data-stu-id="80849-172">MLModel.zip: A serialized version of the ML.NET prediction pipeline that uses the serialized version of the model *bestModel.onnx* to make predictions and maps outputs using the `bestModelMap.json` file.</span></span>

## <a name="use-the-machine-learning-model"></a><span data-ttu-id="80849-173">使用机器学习模型</span><span class="sxs-lookup"><span data-stu-id="80849-173">Use the machine learning model</span></span>

<span data-ttu-id="80849-174">模型项目中的 `ModelInput` 和 `ModelOutput` 类分别定义模型预期输入和输出的架构。</span><span class="sxs-lookup"><span data-stu-id="80849-174">The `ModelInput` and `ModelOutput` classes in the *Model* project define the schema of the model's expected input and output respectively.</span></span>

<span data-ttu-id="80849-175">在图像分类方案中，`ModelInput` 包含两列：</span><span class="sxs-lookup"><span data-stu-id="80849-175">In an image classification scenario, the `ModelInput` contains two columns:</span></span>

- <span data-ttu-id="80849-176">`ImageSource`：图像位置的字符串路径。</span><span class="sxs-lookup"><span data-stu-id="80849-176">`ImageSource`: The string path of the image location.</span></span>
- <span data-ttu-id="80849-177">`Label`：图像所属的实际类别。</span><span class="sxs-lookup"><span data-stu-id="80849-177">`Label`: The actual category the image belongs to.</span></span> <span data-ttu-id="80849-178">`Label` 仅在训练时用作输入，进行预测时不需要提供它。</span><span class="sxs-lookup"><span data-stu-id="80849-178">`Label` is only used as an input when training and does not need to be provided when making predictions.</span></span>

<span data-ttu-id="80849-179">`ModelOutput` 包含两列：</span><span class="sxs-lookup"><span data-stu-id="80849-179">The `ModelOutput` contains two columns:</span></span>

- <span data-ttu-id="80849-180">`Prediction`：图像的预测类别。</span><span class="sxs-lookup"><span data-stu-id="80849-180">`Prediction`: The image's predicted category.</span></span>
- <span data-ttu-id="80849-181">`Score`：所有类别的概率列表（最高为 `Prediction`）。</span><span class="sxs-lookup"><span data-stu-id="80849-181">`Score`: The list of probabilities for all categories (the highest belongs to the `Prediction`).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="80849-182">疑难解答</span><span class="sxs-lookup"><span data-stu-id="80849-182">Troubleshooting</span></span>

### <a name="cannot-create-compute"></a><span data-ttu-id="80849-183">无法创建计算</span><span class="sxs-lookup"><span data-stu-id="80849-183">Cannot create compute</span></span>

<span data-ttu-id="80849-184">如果在创建 Azure 机器学习计算期间出错，计算资源可能仍然存在，只是处于出错状态。</span><span class="sxs-lookup"><span data-stu-id="80849-184">If an error occurs during Azure Machine Learning compute creation, the compute resource may still exist, in an errored state.</span></span> <span data-ttu-id="80849-185">如果尝试重新创建同名计算资源，操作将会失败。</span><span class="sxs-lookup"><span data-stu-id="80849-185">If you try to re-create the compute resource with the same name, the operation fails.</span></span> <span data-ttu-id="80849-186">请通过以下一种方法修复此错误：</span><span class="sxs-lookup"><span data-stu-id="80849-186">To fix this error, either:</span></span>

- <span data-ttu-id="80849-187">创建具有其他名称的新计算</span><span class="sxs-lookup"><span data-stu-id="80849-187">Create the new compute with a different name</span></span>
- <span data-ttu-id="80849-188">转到 Azure 门户，并删除原始计算资源</span><span class="sxs-lookup"><span data-stu-id="80849-188">Go to the Azure portal, and remove the original compute resource</span></span>
