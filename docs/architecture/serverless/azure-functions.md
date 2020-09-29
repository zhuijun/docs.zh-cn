---
title: Azure Functions - 无服务器应用
description: Azure 函数跨多种语言（C#、JavaScript、Java）和平台提供无服务器功能，以提供事件驱动的即时缩放代码。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 7625b2a0dafb90dc1bf2fb7fe680d53b20764c09
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171801"
---
# <a name="azure-functions"></a><span data-ttu-id="9d83f-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="9d83f-103">Azure Functions</span></span>

<span data-ttu-id="9d83f-104">Azure Functions 提供无服务器计算体验。</span><span class="sxs-lookup"><span data-stu-id="9d83f-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="9d83f-105">函数由触发器  （如对 HTTP 终结点或计时器的访问权限）调用，并执行代码块或业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="9d83f-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="9d83f-106">函数还支持连接到存储和队列等资源的专门绑定  。</span><span class="sxs-lookup"><span data-stu-id="9d83f-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Azure Functions 徽标](./media/azure-functions-logo.png)

<span data-ttu-id="9d83f-108">当前运行时版本 3.0 支持跨平台 .NET Core 3.1 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9d83f-108">The current runtime version 3.0 supports cross-platform .NET Core 3.1 applications.</span></span> <span data-ttu-id="9d83f-109">支持除 C# 之外的其他语言（如 JavaScript、F#和 Java）。</span><span class="sxs-lookup"><span data-stu-id="9d83f-109">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="9d83f-110">在门户中创建的函数提供丰富的脚本编写语法。</span><span class="sxs-lookup"><span data-stu-id="9d83f-110">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="9d83f-111">可以通过完全的平台支持和功能来部署作为独立项目创建的函数。</span><span class="sxs-lookup"><span data-stu-id="9d83f-111">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="9d83f-112">有关详细信息，请参阅 [Azure Functions 文档](/azure/azure-functions)。</span><span class="sxs-lookup"><span data-stu-id="9d83f-112">For more information, see [Azure Functions documentation](/azure/azure-functions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="9d83f-113">编程语言支持</span><span class="sxs-lookup"><span data-stu-id="9d83f-113">Programming language support</span></span>

<span data-ttu-id="9d83f-114">正式版 (GA) 支持以下语言。</span><span class="sxs-lookup"><span data-stu-id="9d83f-114">The following languages are all supported in general availability (GA).</span></span>

|<span data-ttu-id="9d83f-115">语言</span><span class="sxs-lookup"><span data-stu-id="9d83f-115">Language</span></span>      |<span data-ttu-id="9d83f-116">支持的运行时</span><span class="sxs-lookup"><span data-stu-id="9d83f-116">Supported runtimes</span></span>|
|--------------|------------------|
|<span data-ttu-id="9d83f-117">**C#**</span><span class="sxs-lookup"><span data-stu-id="9d83f-117">**C#**</span></span>        |<span data-ttu-id="9d83f-118">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="9d83f-118">.NET Core 3.1</span></span>     |
|<span data-ttu-id="9d83f-119">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="9d83f-119">**JavaScript**</span></span>|<span data-ttu-id="9d83f-120">Node 10 和 12</span><span class="sxs-lookup"><span data-stu-id="9d83f-120">Node 10 & 12</span></span>      |
|<span data-ttu-id="9d83f-121">**F#**</span><span class="sxs-lookup"><span data-stu-id="9d83f-121">**F#**</span></span>        |<span data-ttu-id="9d83f-122">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="9d83f-122">.NET Core 3.1</span></span>     |
|<span data-ttu-id="9d83f-123">**Java**</span><span class="sxs-lookup"><span data-stu-id="9d83f-123">**Java**</span></span>      |<span data-ttu-id="9d83f-124">Java 8</span><span class="sxs-lookup"><span data-stu-id="9d83f-124">Java 8</span></span>            |
|<span data-ttu-id="9d83f-125">**Python**</span><span class="sxs-lookup"><span data-stu-id="9d83f-125">**Python**</span></span>    |<span data-ttu-id="9d83f-126">Python 3.6、3.7 和 3.8</span><span class="sxs-lookup"><span data-stu-id="9d83f-126">Python 3.6, 3.7, & 3.8</span></span>|
|<span data-ttu-id="9d83f-127">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="9d83f-127">**TypeScript**</span></span>|<span data-ttu-id="9d83f-128">Node 10 和 12（通过 JavaScript）</span><span class="sxs-lookup"><span data-stu-id="9d83f-128">Node 10 & 12 (via JavaScript)</span></span>|
|<span data-ttu-id="9d83f-129">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="9d83f-129">**PowerShell**</span></span>|<span data-ttu-id="9d83f-130">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="9d83f-130">PowerShell Core 6</span></span>|

<span data-ttu-id="9d83f-131">有关详细信息，请参阅[支持的语言](/azure/azure-functions/supported-languages)。</span><span class="sxs-lookup"><span data-stu-id="9d83f-131">For more information, see [Supported languages](/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="9d83f-132">应用服务计划</span><span class="sxs-lookup"><span data-stu-id="9d83f-132">App service plans</span></span>

<span data-ttu-id="9d83f-133">函数由应用服务计划  进行支持。</span><span class="sxs-lookup"><span data-stu-id="9d83f-133">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="9d83f-134">该计划定义函数应用使用的资源。</span><span class="sxs-lookup"><span data-stu-id="9d83f-134">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="9d83f-135">你可以将计划分配给某个区域，确定将使用的虚拟机的大小和数量，并选择定价层。</span><span class="sxs-lookup"><span data-stu-id="9d83f-135">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="9d83f-136">为了获取真正的无服务器方法，函数应用可以使用“消耗”  计划。</span><span class="sxs-lookup"><span data-stu-id="9d83f-136">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="9d83f-137">“消耗”计划将根据负载自动缩放后端。</span><span class="sxs-lookup"><span data-stu-id="9d83f-137">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="9d83f-138">函数应用的另一个托管选项是[高级计划](/azure/azure-functions/functions-premium-plan)。</span><span class="sxs-lookup"><span data-stu-id="9d83f-138">Another hosting option for function apps is the [Premium plan](/azure/azure-functions/functions-premium-plan).</span></span> <span data-ttu-id="9d83f-139">此计划提供了一个“alwayson”实例以避免冷启动，支持 VNet 连接等高级功能，并在高级硬件上运行。</span><span class="sxs-lookup"><span data-stu-id="9d83f-139">This plan provides an "always on" instance to avoid cold start, supports advanced features like VNet connectivity, and runs on premium hardware.</span></span>

<span data-ttu-id="9d83f-140">有关详细信息，请参阅[应用服务计划](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)。</span><span class="sxs-lookup"><span data-stu-id="9d83f-140">For more information, see [App service plans](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="9d83f-141">创建第一个函数</span><span class="sxs-lookup"><span data-stu-id="9d83f-141">Create your first function</span></span>

<span data-ttu-id="9d83f-142">可以通过三种常用方法创建函数应用。</span><span class="sxs-lookup"><span data-stu-id="9d83f-142">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="9d83f-143">门户中的脚本函数。</span><span class="sxs-lookup"><span data-stu-id="9d83f-143">Script functions in the portal.</span></span>
- <span data-ttu-id="9d83f-144">使用 Azure CLI 创建必要的资源。</span><span class="sxs-lookup"><span data-stu-id="9d83f-144">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="9d83f-145">使用最喜欢的 IDE 在本地生成函数并将其发布到 Azure。</span><span class="sxs-lookup"><span data-stu-id="9d83f-145">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="9d83f-146">有关在门户中创建脚本函数的详细信息，请参阅[在 Azure 门户中创建第一个函数](/azure/azure-functions/functions-create-first-azure-function)。</span><span class="sxs-lookup"><span data-stu-id="9d83f-146">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="9d83f-147">若要从 Azure CLI 构建，请参阅[使用 Azure CLI 创建你的第一个函数](/azure/azure-functions/functions-create-first-azure-function-azure-cli)。</span><span class="sxs-lookup"><span data-stu-id="9d83f-147">To build from the Azure CLI, see [Create your first function using the Azure CLI](/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="9d83f-148">若要从 Visual Studio 创建函数，请参阅[使用 Visual Studio 创建你的第一个函数](/azure/azure-functions/functions-create-your-first-function-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="9d83f-148">To create a function from Visual Studio, see [Create your first function using Visual Studio](/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="9d83f-149">了解触发器和绑定</span><span class="sxs-lookup"><span data-stu-id="9d83f-149">Understand triggers and bindings</span></span>

<span data-ttu-id="9d83f-150">函数由触发器  调用，且只能有一个触发器。</span><span class="sxs-lookup"><span data-stu-id="9d83f-150">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="9d83f-151">除了调用函数外，某些触发器还用作绑定。</span><span class="sxs-lookup"><span data-stu-id="9d83f-151">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="9d83f-152">除了触发器外，还可以定义多个绑定。</span><span class="sxs-lookup"><span data-stu-id="9d83f-152">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="9d83f-153">“绑定”  提供将数据连接到代码的声明性方式。</span><span class="sxs-lookup"><span data-stu-id="9d83f-153">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="9d83f-154">它们可以传入（输入）或接收数据（输出）。</span><span class="sxs-lookup"><span data-stu-id="9d83f-154">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="9d83f-155">触发器和绑定使函数易于使用。</span><span class="sxs-lookup"><span data-stu-id="9d83f-155">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="9d83f-156">绑定消除了手动创建数据库或文件系统连接的系统开销。</span><span class="sxs-lookup"><span data-stu-id="9d83f-156">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="9d83f-157">绑定所需的所有信息都包含在脚本的特殊 functions.json  文件中，或在代码中用特性声明。</span><span class="sxs-lookup"><span data-stu-id="9d83f-157">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="9d83f-158">一些常见触发器包括：</span><span class="sxs-lookup"><span data-stu-id="9d83f-158">Some common triggers include:</span></span>

- <span data-ttu-id="9d83f-159">Blob 存储：在存储中上载或更改文件或文件夹时调用函数。</span><span class="sxs-lookup"><span data-stu-id="9d83f-159">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="9d83f-160">HTTP：调用函数，如 REST API。</span><span class="sxs-lookup"><span data-stu-id="9d83f-160">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="9d83f-161">队列：在队列中存在项时调用函数。</span><span class="sxs-lookup"><span data-stu-id="9d83f-161">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="9d83f-162">计时器：按定期节奏调用函数。</span><span class="sxs-lookup"><span data-stu-id="9d83f-162">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="9d83f-163">绑定示例包括：</span><span class="sxs-lookup"><span data-stu-id="9d83f-163">Examples of bindings include:</span></span>

- <span data-ttu-id="9d83f-164">CosmosDB：轻松连接到数据库以加载或保存文件。</span><span class="sxs-lookup"><span data-stu-id="9d83f-164">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="9d83f-165">表存储：使用函数应用中的键/值存储。</span><span class="sxs-lookup"><span data-stu-id="9d83f-165">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="9d83f-166">队列存储：轻松从队列中检索项，或在队列中放置新项。</span><span class="sxs-lookup"><span data-stu-id="9d83f-166">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="9d83f-167">下面的示例 functions.json  文件定义触发器和绑定：</span><span class="sxs-lookup"><span data-stu-id="9d83f-167">The following example *functions.json* file defines a trigger and a binding:</span></span>

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

<span data-ttu-id="9d83f-168">在此示例中，函数由对 `images` 容器中的 blob 存储的更改触发。</span><span class="sxs-lookup"><span data-stu-id="9d83f-168">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="9d83f-169">传递文件的信息，因此触发器也充当绑定。</span><span class="sxs-lookup"><span data-stu-id="9d83f-169">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="9d83f-170">另一个绑定用于将信息放到名为 `images` 的队列中。</span><span class="sxs-lookup"><span data-stu-id="9d83f-170">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="9d83f-171">下面是该函数的 C# 脚本：</span><span class="sxs-lookup"><span data-stu-id="9d83f-171">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="9d83f-172">该示例是一个简单的函数，该函数采用已修改或已上载到 blob 存储的文件的名称，并将其放在队列中供以后处理。</span><span class="sxs-lookup"><span data-stu-id="9d83f-172">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="9d83f-173">有关触发器和绑定的完整列表，请参阅 [Azure Functions 触发器和绑定概念](/azure/azure-functions/functions-triggers-bindings)。</span><span class="sxs-lookup"><span data-stu-id="9d83f-173">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](/azure/azure-functions/functions-triggers-bindings).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9d83f-174">[上一页](azure-serverless-platform.md)
>[下一页](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="9d83f-174">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
