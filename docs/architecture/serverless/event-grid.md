---
title: Azure 事件网格 - 无服务器应用
description: Azure 事件网格是一种无服务器解决方案，用于在按事件付费模型上进行大规模可靠的事件传递和路由。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 30937bafd8069eb4508dce18351964103421373a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171879"
---
# <a name="event-grid"></a><span data-ttu-id="fc73a-103">事件网格</span><span class="sxs-lookup"><span data-stu-id="fc73a-103">Event Grid</span></span>

<span data-ttu-id="fc73a-104">[Azure 事件网格](/azure/event-grid/overview)提供基于事件的应用程序的无服务器基础结构。</span><span class="sxs-lookup"><span data-stu-id="fc73a-104">[Azure Event Grid](/azure/event-grid/overview) provides serverless infrastructure for event-based applications.</span></span> <span data-ttu-id="fc73a-105">你可以从任何源发布到事件网格，并从任何平台使用消息。</span><span class="sxs-lookup"><span data-stu-id="fc73a-105">You can publish to Event Grid from any source and consume messages from any platform.</span></span> <span data-ttu-id="fc73a-106">事件网格还提供对 Azure 资源中的事件的内置支持，以简化与应用程序的集成。</span><span class="sxs-lookup"><span data-stu-id="fc73a-106">Event Grid also has built-in support for events from Azure resources to streamline integration with your applications.</span></span> <span data-ttu-id="fc73a-107">例如，你可以订阅 blob 存储事件，以在上载文件时通知应用。</span><span class="sxs-lookup"><span data-stu-id="fc73a-107">For example, you can subscribe to blob storage events to notify your app when a file is uploaded.</span></span> <span data-ttu-id="fc73a-108">然后，应用程序可以发布由其他云或本地应用程序使用的自定义事件网格消息。</span><span class="sxs-lookup"><span data-stu-id="fc73a-108">Your application can then publish a custom event grid message that is consumed by other cloud or on-premises applications.</span></span> <span data-ttu-id="fc73a-109">生成事件网格是为了可靠地处理大规模事件。</span><span class="sxs-lookup"><span data-stu-id="fc73a-109">Event Grid was built to reliably handle massive scale.</span></span> <span data-ttu-id="fc73a-110">你可以从发布和订阅消息而无需设置必需的基础结构中受益。</span><span class="sxs-lookup"><span data-stu-id="fc73a-110">You get the benefits of publishing and subscribing to messages without the overhead of setting up the necessary infrastructure.</span></span>

![事件网格徽标](./media/event-grid-logo.png)

<span data-ttu-id="fc73a-112">事件网格的主要功能包括：</span><span class="sxs-lookup"><span data-stu-id="fc73a-112">The major features of event grid include:</span></span>

- <span data-ttu-id="fc73a-113">完全托管的事件路由。</span><span class="sxs-lookup"><span data-stu-id="fc73a-113">Fully managed event routing.</span></span>
- <span data-ttu-id="fc73a-114">近实时大规模事件传递。</span><span class="sxs-lookup"><span data-stu-id="fc73a-114">Near real-time event delivery at scale.</span></span>
- <span data-ttu-id="fc73a-115">Azure 内部和外部的广泛覆盖面。</span><span class="sxs-lookup"><span data-stu-id="fc73a-115">Broad coverage both inside and outside of Azure.</span></span>

## <a name="scenarios"></a><span data-ttu-id="fc73a-116">方案</span><span class="sxs-lookup"><span data-stu-id="fc73a-116">Scenarios</span></span>

<span data-ttu-id="fc73a-117">事件网格解决了几种不同的方案。</span><span class="sxs-lookup"><span data-stu-id="fc73a-117">Event Grid addresses several different scenarios.</span></span> <span data-ttu-id="fc73a-118">本部分介绍三个最常见的方案。</span><span class="sxs-lookup"><span data-stu-id="fc73a-118">This section covers three of the most common ones.</span></span>

### <a name="ops-automation"></a><span data-ttu-id="fc73a-119">运维自动化</span><span class="sxs-lookup"><span data-stu-id="fc73a-119">Ops automation</span></span>

![运维自动化](./media/ops-automation.png)

<span data-ttu-id="fc73a-121">事件网格可以通过在预配基础结构时通知 [Azure 自动化](/azure/automation)来帮助加速自动化并简化策略强制执行。</span><span class="sxs-lookup"><span data-stu-id="fc73a-121">Event Grid can help speed automation and simplify policy enforcement by notifying [Azure Automation](/azure/automation) when infrastructure is provisioned.</span></span>

### <a name="application-integration"></a><span data-ttu-id="fc73a-122">应用程序集成</span><span class="sxs-lookup"><span data-stu-id="fc73a-122">Application integration</span></span>

![应用程序集成](./media/app-integration.png)

<span data-ttu-id="fc73a-124">可以使用事件网格将应用连接到其他服务。</span><span class="sxs-lookup"><span data-stu-id="fc73a-124">You can use Event Grid to connect your app to other services.</span></span> <span data-ttu-id="fc73a-125">使用标准 HTTP 协议，甚至可以轻松修改旧应用，以便发布事件网格消息。</span><span class="sxs-lookup"><span data-stu-id="fc73a-125">Using standard HTTP protocols, even legacy apps can be easily modified to publish Event Grid messages.</span></span> <span data-ttu-id="fc73a-126">Webhook 可供其他服务和平台使用事件网格消息。</span><span class="sxs-lookup"><span data-stu-id="fc73a-126">Web hooks are available for other services and platforms to consume Event Grid messages.</span></span>

### <a name="serverless-apps"></a><span data-ttu-id="fc73a-127">无服务器应用</span><span class="sxs-lookup"><span data-stu-id="fc73a-127">Serverless apps</span></span>

![无服务器应用](./media/serverless-apps.png)

<span data-ttu-id="fc73a-129">事件网格可以触发 Azure Functions、逻辑应用或你自己的自定义代码。</span><span class="sxs-lookup"><span data-stu-id="fc73a-129">Event Grid can trigger Azure Functions, Logic Apps, or your own custom code.</span></span> <span data-ttu-id="fc73a-130">使用事件网格的主要好处在于它使用“推送”  机制在事件发生时发送消息。</span><span class="sxs-lookup"><span data-stu-id="fc73a-130">A major benefit of using Event Grid is that it uses a *push* mechanism to send messages when events occur.</span></span> <span data-ttu-id="fc73a-131">与“轮询”  机制相比，推送体系结构消耗的资源较少，缩放性较好。</span><span class="sxs-lookup"><span data-stu-id="fc73a-131">The push architecture consumes fewer resources and scales better than *polling* mechanisms.</span></span> <span data-ttu-id="fc73a-132">轮询必须定期检查更新。</span><span class="sxs-lookup"><span data-stu-id="fc73a-132">Polling must check for updates on a regular interval.</span></span>

## <a name="event-grid-vs-other-azure-messaging-services"></a><span data-ttu-id="fc73a-133">事件网格与其他 Azure 消息传递服务</span><span class="sxs-lookup"><span data-stu-id="fc73a-133">Event Grid vs. other Azure messaging services</span></span>

<span data-ttu-id="fc73a-134">Azure 提供了多个消息传递服务，包括[事件中心](/azure/event-hubs)和[服务总线](/azure/service-bus-messaging)。</span><span class="sxs-lookup"><span data-stu-id="fc73a-134">Azure provides several messaging services, including [Event Hubs](/azure/event-hubs) and [Service Bus](/azure/service-bus-messaging).</span></span> <span data-ttu-id="fc73a-135">每个服务都旨在处理一组特定的用例。</span><span class="sxs-lookup"><span data-stu-id="fc73a-135">Each is designed to address a specific set of use cases.</span></span> <span data-ttu-id="fc73a-136">下图高度概括了服务之间的差异。</span><span class="sxs-lookup"><span data-stu-id="fc73a-136">The following diagram provides a high-level overview of the differences between the services.</span></span>

![Azure 消息传递组件](./media/azure-messaging-services.png)

<span data-ttu-id="fc73a-138">有关更深入的比较，请参阅[比较消息传递服务](/azure/event-grid/compare-messaging-services)。</span><span class="sxs-lookup"><span data-stu-id="fc73a-138">For a more in-depth comparison, see [Compare messaging services](/azure/event-grid/compare-messaging-services).</span></span>

## <a name="performance-targets"></a><span data-ttu-id="fc73a-139">性能目标</span><span class="sxs-lookup"><span data-stu-id="fc73a-139">Performance targets</span></span>

<span data-ttu-id="fc73a-140">使用事件网格，可以利用以下性能保证：</span><span class="sxs-lookup"><span data-stu-id="fc73a-140">Using Event Grid you can take advantage of the following performance guarantees:</span></span>

- <span data-ttu-id="fc73a-141">在 99% 的时间内实现亚秒级端到端延迟。</span><span class="sxs-lookup"><span data-stu-id="fc73a-141">Subsecond end-to-end latency in the 99th percentile.</span></span>
- <span data-ttu-id="fc73a-142">99.99% 可用性。</span><span class="sxs-lookup"><span data-stu-id="fc73a-142">99.99% availability.</span></span>
- <span data-ttu-id="fc73a-143">每个区域每秒 1 千万个事件。</span><span class="sxs-lookup"><span data-stu-id="fc73a-143">10 million events per second per region.</span></span>
- <span data-ttu-id="fc73a-144">每个区域 1 亿个订阅。</span><span class="sxs-lookup"><span data-stu-id="fc73a-144">100 million subscriptions per region.</span></span>
- <span data-ttu-id="fc73a-145">50 毫秒发布服务器延迟。</span><span class="sxs-lookup"><span data-stu-id="fc73a-145">50-ms publisher latency.</span></span>
- <span data-ttu-id="fc73a-146">以指数后退方式进行 24 小时重试，以保证在 1 天窗口中送达。</span><span class="sxs-lookup"><span data-stu-id="fc73a-146">24-hour retry with exponential back-off for guaranteed delivery in the 1-day window.</span></span>
- <span data-ttu-id="fc73a-147">透明的区域故障转移。</span><span class="sxs-lookup"><span data-stu-id="fc73a-147">Transparent regional failover.</span></span>

## <a name="event-grid-schema"></a><span data-ttu-id="fc73a-148">事件网格架构</span><span class="sxs-lookup"><span data-stu-id="fc73a-148">Event Grid schema</span></span>

<span data-ttu-id="fc73a-149">事件网格使用标准架构来包装自定义事件。</span><span class="sxs-lookup"><span data-stu-id="fc73a-149">Event Grid uses a standard schema to wrap custom events.</span></span> <span data-ttu-id="fc73a-150">该架构类似于包装自定义数据元素的信封。</span><span class="sxs-lookup"><span data-stu-id="fc73a-150">The schema is like an envelope that wraps your custom data element.</span></span> <span data-ttu-id="fc73a-151">下面是事件网格消息示例：</span><span class="sxs-lookup"><span data-stu-id="fc73a-151">Here is an example Event Grid message:</span></span>

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

<span data-ttu-id="fc73a-152">除了 `data` 属性，消息的所有内容都是标准的。</span><span class="sxs-lookup"><span data-stu-id="fc73a-152">Everything about the message is standard except the `data` property.</span></span> <span data-ttu-id="fc73a-153">你可以检查消息并使用 `eventType` 和 `dataVersion` 对负载的自定义部分进行反序列化。</span><span class="sxs-lookup"><span data-stu-id="fc73a-153">You can inspect the message and use the `eventType` and `dataVersion` to de-serialize the custom portion of the payload.</span></span>

## <a name="azure-resources"></a><span data-ttu-id="fc73a-154">Azure 资源</span><span class="sxs-lookup"><span data-stu-id="fc73a-154">Azure resources</span></span>

<span data-ttu-id="fc73a-155">使用事件网格的主要好处是 Azure 生成的自动消息。</span><span class="sxs-lookup"><span data-stu-id="fc73a-155">A major benefit of using Event Grid is the automatic messages produced by Azure.</span></span> <span data-ttu-id="fc73a-156">在 Azure 中，资源自动发布到主题  ，使你可以订阅各种事件。</span><span class="sxs-lookup"><span data-stu-id="fc73a-156">In Azure, resources automatically publish to a *topic* that allows you to subscribe for various events.</span></span> <span data-ttu-id="fc73a-157">下表列出了可自动使用的资源类型、消息类型和事件。</span><span class="sxs-lookup"><span data-stu-id="fc73a-157">The following table lists the resource types, message types, and events that are available automatically.</span></span>

| <span data-ttu-id="fc73a-158">Azure 资源</span><span class="sxs-lookup"><span data-stu-id="fc73a-158">Azure resource</span></span> | <span data-ttu-id="fc73a-159">事件类型</span><span class="sxs-lookup"><span data-stu-id="fc73a-159">Event type</span></span> | <span data-ttu-id="fc73a-160">描述</span><span class="sxs-lookup"><span data-stu-id="fc73a-160">Description</span></span> |
| -------------- | ---------- | ----------- |
| <span data-ttu-id="fc73a-161">Azure 订阅</span><span class="sxs-lookup"><span data-stu-id="fc73a-161">Azure subscription</span></span> | <span data-ttu-id="fc73a-162">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="fc73a-162">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="fc73a-163">当资源创建或更新操作成功时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-163">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="fc73a-164">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="fc73a-164">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="fc73a-165">当资源创建或更新操作失败时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-165">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="fc73a-166">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="fc73a-166">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="fc73a-167">当资源创建或更新操作取消时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-167">Raised when a resource create or update operation is canceled.</span></span> |
|  | <span data-ttu-id="fc73a-168">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="fc73a-168">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="fc73a-169">当资源删除操作成功时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-169">Raised when a resource delete operation succeeds.</span></span> |
|  | <span data-ttu-id="fc73a-170">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="fc73a-170">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="fc73a-171">当资源删除操作失败时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-171">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="fc73a-172">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="fc73a-172">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="fc73a-173">当资源删除操作取消时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-173">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="fc73a-174">取消模板部署时会发生此事件。</span><span class="sxs-lookup"><span data-stu-id="fc73a-174">This event happens when a template deployment is canceled.</span></span> |
| <span data-ttu-id="fc73a-175">Blob 存储</span><span class="sxs-lookup"><span data-stu-id="fc73a-175">Blob storage</span></span> | <span data-ttu-id="fc73a-176">Microsoft.Storage.BlobCreated</span><span class="sxs-lookup"><span data-stu-id="fc73a-176">Microsoft.Storage.BlobCreated</span></span> | <span data-ttu-id="fc73a-177">创建 Blob 时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-177">Raised when a blob is created.</span></span> |
| | <span data-ttu-id="fc73a-178">Microsoft.Storage.BlobDeleted</span><span class="sxs-lookup"><span data-stu-id="fc73a-178">Microsoft.Storage.BlobDeleted</span></span> | <span data-ttu-id="fc73a-179">删除 Blob 时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-179">Raised when a blob is deleted.</span></span> |
| <span data-ttu-id="fc73a-180">事件中心</span><span class="sxs-lookup"><span data-stu-id="fc73a-180">Event hubs</span></span> | <span data-ttu-id="fc73a-181">Microsoft.EventHub.CaptureFileCreated</span><span class="sxs-lookup"><span data-stu-id="fc73a-181">Microsoft.EventHub.CaptureFileCreated</span></span> | <span data-ttu-id="fc73a-182">创建捕获文件时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-182">Raised when a capture file is created.</span></span>
| <span data-ttu-id="fc73a-183">IoT 中心</span><span class="sxs-lookup"><span data-stu-id="fc73a-183">IoT Hub</span></span> | <span data-ttu-id="fc73a-184">Microsoft.Devices.DeviceCreated</span><span class="sxs-lookup"><span data-stu-id="fc73a-184">Microsoft.Devices.DeviceCreated</span></span> | <span data-ttu-id="fc73a-185">当设备注册到 IoT 中心时发布。</span><span class="sxs-lookup"><span data-stu-id="fc73a-185">Published when a device is registered to an IoT hub.</span></span> |
| | <span data-ttu-id="fc73a-186">Microsoft.Devices.DeviceDeleted</span><span class="sxs-lookup"><span data-stu-id="fc73a-186">Microsoft.Devices.DeviceDeleted</span></span> | <span data-ttu-id="fc73a-187">当设备从 IoT 中心删除时发布。</span><span class="sxs-lookup"><span data-stu-id="fc73a-187">Published when a device is deleted from an IoT hub.</span></span> |
| <span data-ttu-id="fc73a-188">资源组</span><span class="sxs-lookup"><span data-stu-id="fc73a-188">Resource groups</span></span> | <span data-ttu-id="fc73a-189">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="fc73a-189">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="fc73a-190">当资源创建或更新操作成功时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-190">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="fc73a-191">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="fc73a-191">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="fc73a-192">当资源创建或更新操作失败时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-192">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="fc73a-193">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="fc73a-193">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="fc73a-194">当资源创建或更新操作取消时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-194">Raised when a resource create or update operation is canceled.</span></span> |
| | <span data-ttu-id="fc73a-195">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="fc73a-195">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="fc73a-196">当资源删除操作成功时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-196">Raised when a resource delete operation succeeds.</span></span> |
| | <span data-ttu-id="fc73a-197">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="fc73a-197">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="fc73a-198">当资源删除操作失败时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-198">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="fc73a-199">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="fc73a-199">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="fc73a-200">当资源删除操作取消时引发。</span><span class="sxs-lookup"><span data-stu-id="fc73a-200">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="fc73a-201">取消模板部署时会发生此事件。</span><span class="sxs-lookup"><span data-stu-id="fc73a-201">This event happens when a template deployment is canceled.</span></span> |

<span data-ttu-id="fc73a-202">有关详细信息，请参阅 [Azure 事件网格事件架构](/azure/event-grid/event-schema)。</span><span class="sxs-lookup"><span data-stu-id="fc73a-202">For more information, see [Azure Event Grid event schema](/azure/event-grid/event-schema).</span></span>

<span data-ttu-id="fc73a-203">你可以从任何类型的应用程序（甚至是在本地运行的应用程序）访问事件网格。</span><span class="sxs-lookup"><span data-stu-id="fc73a-203">You can access Event Grid from any type of application, even one that runs on-premises.</span></span>

## <a name="conclusion"></a><span data-ttu-id="fc73a-204">结束语</span><span class="sxs-lookup"><span data-stu-id="fc73a-204">Conclusion</span></span>

<span data-ttu-id="fc73a-205">在本章中，你了解了由 Azure Functions、逻辑应用和事件网格组成的 Azure 无服务器平台。</span><span class="sxs-lookup"><span data-stu-id="fc73a-205">In this chapter you learned about the Azure serverless platform that is composed of Azure Functions, Logic Apps, and Event Grid.</span></span> <span data-ttu-id="fc73a-206">你可以使用这些资源来构建完全无服务器的应用体系结构，或创建与其他云资源和本地服务器交互的混合解决方案。</span><span class="sxs-lookup"><span data-stu-id="fc73a-206">You can use these resources to build an entirely serverless app architecture, or create a hybrid solution that interacts with other cloud resources and on-premises servers.</span></span> <span data-ttu-id="fc73a-207">与无服务器数据平台（如 [Azure SQL](/azure/sql-database) 或 [CosmosDB](/azure/cosmos-db/introduction)）相结合，你可以构建完全托管的云本机应用程序。</span><span class="sxs-lookup"><span data-stu-id="fc73a-207">Combined with a serverless data platform such as [Azure SQL](/azure/sql-database) or [CosmosDB](/azure/cosmos-db/introduction), you can build fully managed cloud native applications.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="fc73a-208">推荐的资源</span><span class="sxs-lookup"><span data-stu-id="fc73a-208">Recommended resources</span></span>

- [<span data-ttu-id="fc73a-209">应用服务计划</span><span class="sxs-lookup"><span data-stu-id="fc73a-209">App service plans</span></span>](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [<span data-ttu-id="fc73a-210">Application Insights</span><span class="sxs-lookup"><span data-stu-id="fc73a-210">Application Insights</span></span>](/azure/application-insights)
- [<span data-ttu-id="fc73a-211">Application Insights Analytics</span><span class="sxs-lookup"><span data-stu-id="fc73a-211">Application Insights Analytics</span></span>](/azure/application-insights/app-insights-analytics)
- [<span data-ttu-id="fc73a-212">Azure:利用无服务器 Azure Functions 将你的应用引入云</span><span class="sxs-lookup"><span data-stu-id="fc73a-212">Azure: Bring your app to the cloud with serverless Azure Functions</span></span>](https://channel9.msdn.com/events/Connect/2017/E102)
- [<span data-ttu-id="fc73a-213">Azure 事件网格</span><span class="sxs-lookup"><span data-stu-id="fc73a-213">Azure Event Grid</span></span>](/azure/event-grid/overview)
- [<span data-ttu-id="fc73a-214">Azure 事件网格事件架构</span><span class="sxs-lookup"><span data-stu-id="fc73a-214">Azure Event Grid event schema</span></span>](/azure/event-grid/event-schema)
- [<span data-ttu-id="fc73a-215">Azure 事件中心</span><span class="sxs-lookup"><span data-stu-id="fc73a-215">Azure Event Hubs</span></span>](/azure/event-hubs)
- [<span data-ttu-id="fc73a-216">Azure Functions 文档</span><span class="sxs-lookup"><span data-stu-id="fc73a-216">Azure Functions documentation</span></span>](/azure/azure-functions)
- [<span data-ttu-id="fc73a-217">Azure Functions 触发器和绑定概念</span><span class="sxs-lookup"><span data-stu-id="fc73a-217">Azure Functions triggers and bindings concepts</span></span>](/azure/azure-functions/functions-triggers-bindings)
- [<span data-ttu-id="fc73a-218">Azure 逻辑应用</span><span class="sxs-lookup"><span data-stu-id="fc73a-218">Azure Logic Apps</span></span>](/azure/logic-apps)
- [<span data-ttu-id="fc73a-219">Azure 服务总线</span><span class="sxs-lookup"><span data-stu-id="fc73a-219">Azure Service Bus</span></span>](/azure/service-bus-messaging)
- [<span data-ttu-id="fc73a-220">Azure 表存储</span><span class="sxs-lookup"><span data-stu-id="fc73a-220">Azure Table Storage</span></span>](/azure/cosmos-db/table-storage-overview)
- [<span data-ttu-id="fc73a-221">使用 Azure 本地数据网关连接到本地数据源</span><span class="sxs-lookup"><span data-stu-id="fc73a-221">Connecting to on-premises data sources with Azure On-premises Data Gateway</span></span>](/azure/analysis-services/analysis-services-gateway)
- [<span data-ttu-id="fc73a-222">在 Azure 门户中创建你的第一个函数</span><span class="sxs-lookup"><span data-stu-id="fc73a-222">Create your first function in the Azure portal</span></span>](/azure/azure-functions/functions-create-first-azure-function)
- [<span data-ttu-id="fc73a-223">使用 Azure CLI 创建第一个函数</span><span class="sxs-lookup"><span data-stu-id="fc73a-223">Create your first function using the Azure CLI</span></span>](/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [<span data-ttu-id="fc73a-224">使用 Visual Studio 创建你的第一个函数</span><span class="sxs-lookup"><span data-stu-id="fc73a-224">Create your first function using Visual Studio</span></span>](/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [<span data-ttu-id="fc73a-225">Functions 支持的语言</span><span class="sxs-lookup"><span data-stu-id="fc73a-225">Functions supported languages</span></span>](/azure/azure-functions/supported-languages)
- [<span data-ttu-id="fc73a-226">监视 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="fc73a-226">Monitor Azure Functions</span></span>](/azure/azure-functions/functions-monitoring)

>[!div class="step-by-step"]
><span data-ttu-id="fc73a-227">[上一页](logic-apps.md)
>[下一页](durable-azure-functions.md)</span><span class="sxs-lookup"><span data-stu-id="fc73a-227">[Previous](logic-apps.md)
[Next](durable-azure-functions.md)</span></span>
