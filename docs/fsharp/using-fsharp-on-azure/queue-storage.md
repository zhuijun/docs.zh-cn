---
title: 通过 F# 实现 Azure 队列存储入门
description: Azure 队列用于在应用程序组件之间进行可靠的异步消息传送。 应用程序组件可以利用云消息传送进行独立缩放。
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: daa5372b7903f10c0d966c5c92e35c8bf9d362d8
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756216"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="5df1c-104">使用 F 开始使用 Azure 队列存储\#</span><span class="sxs-lookup"><span data-stu-id="5df1c-104">Get started with Azure Queue storage using F\#</span></span>

<span data-ttu-id="5df1c-105">Azure 队列存储用于在应用程序组件之间进行云消息传送。</span><span class="sxs-lookup"><span data-stu-id="5df1c-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="5df1c-106">在设计应用程序以实现伸缩性时，通常要将各个应用程序组件分离，使其可以独立地进行伸缩。</span><span class="sxs-lookup"><span data-stu-id="5df1c-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="5df1c-107">队列存储提供的异步消息传送适用于在应用程序组件之间进行通信，无论这些应用程序组件是运行在云中、桌面上、本地服务器上还是移动设备上。</span><span class="sxs-lookup"><span data-stu-id="5df1c-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="5df1c-108">队列存储还支持管理异步任务以及构建过程工作流。</span><span class="sxs-lookup"><span data-stu-id="5df1c-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="5df1c-109">关于本教程</span><span class="sxs-lookup"><span data-stu-id="5df1c-109">About this tutorial</span></span>

<span data-ttu-id="5df1c-110">本教程演示如何使用 Azure 队列存储为一些常见任务编写 F # 代码。</span><span class="sxs-lookup"><span data-stu-id="5df1c-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="5df1c-111">涉及的任务包括创建和删除队列、添加、读取和删除队列消息。</span><span class="sxs-lookup"><span data-stu-id="5df1c-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="5df1c-112">有关队列存储的概念性概述，请参阅 [队列存储的 .net 指南](/azure/storage/storage-dotnet-how-to-use-queues)。</span><span class="sxs-lookup"><span data-stu-id="5df1c-112">For a conceptual overview of queue storage, see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5df1c-113">必备知识</span><span class="sxs-lookup"><span data-stu-id="5df1c-113">Prerequisites</span></span>

<span data-ttu-id="5df1c-114">若要使用本指南，必须先 [创建 Azure 存储帐户](/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="5df1c-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="5df1c-115">还需要此帐户的存储访问密钥。</span><span class="sxs-lookup"><span data-stu-id="5df1c-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="5df1c-116">创建 F # 脚本并开始 F# 交互窗口</span><span class="sxs-lookup"><span data-stu-id="5df1c-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="5df1c-117">本文中的示例可用于 F # 应用程序或 F # 脚本。</span><span class="sxs-lookup"><span data-stu-id="5df1c-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="5df1c-118">若要创建 F # 脚本，请创建 `.fsx` 扩展名为的文件，例如 `queues.fsx` f # 开发环境中的文件。</span><span class="sxs-lookup"><span data-stu-id="5df1c-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="5df1c-119">接下来，使用 [包管理器](package-management.md) （如 [Paket](https://fsprojects.github.io/Paket/) 或 [NuGet](https://www.nuget.org/) ） `WindowsAzure.Storage` `WindowsAzure.Storage.dll` 通过指令在脚本中安装包和引用 `#r` 。</span><span class="sxs-lookup"><span data-stu-id="5df1c-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="5df1c-120">添加命名空间声明</span><span class="sxs-lookup"><span data-stu-id="5df1c-120">Add namespace declarations</span></span>

<span data-ttu-id="5df1c-121">将下列 `open` 语句添加到 `queues.fsx` 文件顶部：</span><span class="sxs-lookup"><span data-stu-id="5df1c-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="5df1c-122">获取连接字符串</span><span class="sxs-lookup"><span data-stu-id="5df1c-122">Get your connection string</span></span>

<span data-ttu-id="5df1c-123">本教程需要 Azure 存储连接字符串。</span><span class="sxs-lookup"><span data-stu-id="5df1c-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="5df1c-124">有关连接字符串的详细信息，请参阅 [配置存储连接字符串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="5df1c-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="5df1c-125">对于本教程，您将在脚本中输入连接字符串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5df1c-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="5df1c-126">但对于实际项目， **不建议这样做** 。</span><span class="sxs-lookup"><span data-stu-id="5df1c-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="5df1c-127">存储帐户密钥类似于存储帐户的根密码。</span><span class="sxs-lookup"><span data-stu-id="5df1c-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="5df1c-128">始终要小心保护存储帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="5df1c-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="5df1c-129">避免将其分发给其他用户、对其进行硬编码或将其保存在其他人可以访问的纯文本文件中。</span><span class="sxs-lookup"><span data-stu-id="5df1c-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="5df1c-130">如果你认为密钥可能已泄漏，你可以使用 Azure 门户重新生成密钥。</span><span class="sxs-lookup"><span data-stu-id="5df1c-130">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="5df1c-131">对于实际应用程序，维护存储连接字符串的最佳方式是在配置文件中。</span><span class="sxs-lookup"><span data-stu-id="5df1c-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="5df1c-132">若要从配置文件中提取连接字符串，可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5df1c-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="5df1c-133">不一定要使用 Azure Configuration Manager。</span><span class="sxs-lookup"><span data-stu-id="5df1c-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="5df1c-134">你还可以使用 API，例如 .NET Framework 的 `ConfigurationManager` 类型。</span><span class="sxs-lookup"><span data-stu-id="5df1c-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="5df1c-135">解析连接字符串</span><span class="sxs-lookup"><span data-stu-id="5df1c-135">Parse the connection string</span></span>

<span data-ttu-id="5df1c-136">若要分析连接字符串，请使用：</span><span class="sxs-lookup"><span data-stu-id="5df1c-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="5df1c-137">这将返回 `CloudStorageAccount` 。</span><span class="sxs-lookup"><span data-stu-id="5df1c-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="5df1c-138">创建队列服务客户端</span><span class="sxs-lookup"><span data-stu-id="5df1c-138">Create the Queue service client</span></span>

<span data-ttu-id="5df1c-139">`CloudQueueClient`类使你能够检索存储在队列存储中的队列。</span><span class="sxs-lookup"><span data-stu-id="5df1c-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="5df1c-140">下面是创建服务客户端的一种方法：</span><span class="sxs-lookup"><span data-stu-id="5df1c-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="5df1c-141">现在，已准备好编写从队列存储读取数据并将数据写入队列存储的代码。</span><span class="sxs-lookup"><span data-stu-id="5df1c-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="5df1c-142">创建队列</span><span class="sxs-lookup"><span data-stu-id="5df1c-142">Create a queue</span></span>

<span data-ttu-id="5df1c-143">此示例演示如何创建队列（如果该队列尚不存在）：</span><span class="sxs-lookup"><span data-stu-id="5df1c-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="5df1c-144">在队列中插入消息</span><span class="sxs-lookup"><span data-stu-id="5df1c-144">Insert a message into a queue</span></span>

<span data-ttu-id="5df1c-145">若要将消息插入现有队列，请先创建一个新的 `CloudQueueMessage` 。</span><span class="sxs-lookup"><span data-stu-id="5df1c-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="5df1c-146">接下来，调用 `AddMessage` 方法。</span><span class="sxs-lookup"><span data-stu-id="5df1c-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="5df1c-147">`CloudQueueMessage`可以使用 utf-8 格式的字符串 (创建) 或 `byte` 数组，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5df1c-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="5df1c-148">扫视下一条消息</span><span class="sxs-lookup"><span data-stu-id="5df1c-148">Peek at the next message</span></span>

<span data-ttu-id="5df1c-149">通过调用方法，可以查看队列前面的消息，而不必从队列中将其删除 `PeekMessage` 。</span><span class="sxs-lookup"><span data-stu-id="5df1c-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="5df1c-150">获取要处理的下一条消息</span><span class="sxs-lookup"><span data-stu-id="5df1c-150">Get the next message for processing</span></span>

<span data-ttu-id="5df1c-151">可以通过调用方法来检索队列前面的消息，以便进行处理 `GetMessage` 。</span><span class="sxs-lookup"><span data-stu-id="5df1c-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="5df1c-152">稍后，您可以使用来指示成功处理消息 `DeleteMessage` 。</span><span class="sxs-lookup"><span data-stu-id="5df1c-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="5df1c-153">更改已排队消息的内容</span><span class="sxs-lookup"><span data-stu-id="5df1c-153">Change the contents of a queued message</span></span>

<span data-ttu-id="5df1c-154">您可以在队列中就地更改检索到的消息的内容。</span><span class="sxs-lookup"><span data-stu-id="5df1c-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="5df1c-155">如果消息表示工作任务，可使用此功能来更新该工作任务的状态。</span><span class="sxs-lookup"><span data-stu-id="5df1c-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="5df1c-156">以下代码使用新内容更新队列消息，并将可见性超时设置为再延长 60 秒。</span><span class="sxs-lookup"><span data-stu-id="5df1c-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="5df1c-157">这会保存与消息关联的工作的状态，并额外为客户端提供一分钟的时间来继续处理消息。</span><span class="sxs-lookup"><span data-stu-id="5df1c-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="5df1c-158">可使用此方法跟踪队列消息上的多步骤工作流，即使处理步骤因硬件或软件故障而失败，也无需从头开始操作。</span><span class="sxs-lookup"><span data-stu-id="5df1c-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="5df1c-159">通常，还可以保留重试计数，如果消息重试次数超过若干次，则会将其删除。</span><span class="sxs-lookup"><span data-stu-id="5df1c-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="5df1c-160">这可避免每次处理某条消息时都触发应用程序错误。</span><span class="sxs-lookup"><span data-stu-id="5df1c-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="5df1c-161">取消对下一条消息的排队</span><span class="sxs-lookup"><span data-stu-id="5df1c-161">De-queue the next message</span></span>

<span data-ttu-id="5df1c-162">代码通过两个步骤来取消对队列中某条消息的排队。</span><span class="sxs-lookup"><span data-stu-id="5df1c-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="5df1c-163">调用时 `GetMessage` ，将获取队列中的下一条消息。</span><span class="sxs-lookup"><span data-stu-id="5df1c-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="5df1c-164">从 `GetMessage` 返回的消息对于从此队列读取消息的任何其他代码都是不可见的。</span><span class="sxs-lookup"><span data-stu-id="5df1c-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="5df1c-165">默认情况下，此消息持续 30 秒不可见。</span><span class="sxs-lookup"><span data-stu-id="5df1c-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="5df1c-166">若要完成从队列中删除消息，还必须调用 `DeleteMessage` 。</span><span class="sxs-lookup"><span data-stu-id="5df1c-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="5df1c-167">此删除消息的两步过程可确保，如果代码因硬件或软件故障而无法处理消息，则代码的其他实例可以获取相同消息并重试。</span><span class="sxs-lookup"><span data-stu-id="5df1c-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="5df1c-168">代码在处理消息后会立即调用 `DeleteMessage`。</span><span class="sxs-lookup"><span data-stu-id="5df1c-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="5df1c-169">将异步工作流用于常见的队列存储 Api</span><span class="sxs-lookup"><span data-stu-id="5df1c-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="5df1c-170">此示例演示如何将异步工作流与公共队列存储 Api 一起使用。</span><span class="sxs-lookup"><span data-stu-id="5df1c-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="5df1c-171">用于取消对消息进行排队的其他选项</span><span class="sxs-lookup"><span data-stu-id="5df1c-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="5df1c-172">可通过两种方式自定义队列中消息的检索。</span><span class="sxs-lookup"><span data-stu-id="5df1c-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="5df1c-173">首先，可获取一批消息（最多 32 条）。</span><span class="sxs-lookup"><span data-stu-id="5df1c-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="5df1c-174">其次，可以设置更长或更短的不可见超时时间，从而允许代码使用更多或更少时间来完全处理每个消息。</span><span class="sxs-lookup"><span data-stu-id="5df1c-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="5df1c-175">下面的代码示例使用 `GetMessages` 在一个调用中获取20条消息，然后处理每条消息。</span><span class="sxs-lookup"><span data-stu-id="5df1c-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="5df1c-176">它还将每条消息的不可见超时时间设置为 5 分钟。</span><span class="sxs-lookup"><span data-stu-id="5df1c-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="5df1c-177">5分钟会同时为所有消息启动，因此，在调用后5分钟后 `GetMessages` ，任何尚未删除的消息都将再次变得可见。</span><span class="sxs-lookup"><span data-stu-id="5df1c-177">The 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages that have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="5df1c-178">获取队列长度</span><span class="sxs-lookup"><span data-stu-id="5df1c-178">Get the queue length</span></span>

<span data-ttu-id="5df1c-179">可以获取队列中消息的估计数。</span><span class="sxs-lookup"><span data-stu-id="5df1c-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="5df1c-180">`FetchAttributes`方法要求队列服务检索队列属性，包括消息计数。</span><span class="sxs-lookup"><span data-stu-id="5df1c-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="5df1c-181">`ApproximateMessageCount`属性返回方法检索到的最后一个值 `FetchAttributes` ，而不会调用队列服务。</span><span class="sxs-lookup"><span data-stu-id="5df1c-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="5df1c-182">删除队列</span><span class="sxs-lookup"><span data-stu-id="5df1c-182">Delete a queue</span></span>

<span data-ttu-id="5df1c-183">若要删除队列及其中包含的所有消息，请对 `Delete` 队列对象调用方法。</span><span class="sxs-lookup"><span data-stu-id="5df1c-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="5df1c-184">后续步骤</span><span class="sxs-lookup"><span data-stu-id="5df1c-184">Next steps</span></span>

<span data-ttu-id="5df1c-185">现在，了解了有关队列存储的基础知识，可单击下面的链接来了解更复杂的存储任务。</span><span class="sxs-lookup"><span data-stu-id="5df1c-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="5df1c-186">用于 .NET 的 Azure 存储 API</span><span class="sxs-lookup"><span data-stu-id="5df1c-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="5df1c-187">Azure 存储类型提供程序</span><span class="sxs-lookup"><span data-stu-id="5df1c-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="5df1c-188">Azure 存储团队博客</span><span class="sxs-lookup"><span data-stu-id="5df1c-188">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- <span data-ttu-id="5df1c-189">[Configure Azure Storage connection strings](/azure/storage/common/storage-configure-connection-string)（配置 Azure 存储连接字符串）</span><span class="sxs-lookup"><span data-stu-id="5df1c-189">[Configure Azure Storage connection strings](/azure/storage/common/storage-configure-connection-string)</span></span>
- [<span data-ttu-id="5df1c-190">Azure 存储服务 REST API 参考</span><span class="sxs-lookup"><span data-stu-id="5df1c-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
