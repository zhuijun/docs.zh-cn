---
title: Windows Workflow Foundation 功能详细信息
description: 本文介绍 .NET Framework 4 添加到 Windows Workflow Foundation 的新功能，以及这些功能可能有用的方案。
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: ae15f3ed536967cb15d1a5913f9ca1eab8a510d9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554601"
---
# <a name="windows-workflow-foundation-feature-specifics"></a><span data-ttu-id="13e11-103">Windows Workflow Foundation 功能详细信息</span><span class="sxs-lookup"><span data-stu-id="13e11-103">Windows Workflow Foundation Feature Specifics</span></span>

<span data-ttu-id="13e11-104">.NET Framework 4 添加了许多功能以 Windows Workflow Foundation。</span><span class="sxs-lookup"><span data-stu-id="13e11-104">.NET Framework 4 adds a number of features to Windows Workflow Foundation.</span></span> <span data-ttu-id="13e11-105">本文档介绍了大量新的功能，并详述了这些功能可用于的方案。</span><span class="sxs-lookup"><span data-stu-id="13e11-105">This document describes a number of the new features, and gives details about scenarios in which they may be useful.</span></span>

## <a name="messaging-activities"></a><span data-ttu-id="13e11-106">消息传递活动</span><span class="sxs-lookup"><span data-stu-id="13e11-106">Messaging Activities</span></span>

<span data-ttu-id="13e11-107">消息传递活动 (<xref:System.ServiceModel.Activities.Receive> 、 <xref:System.ServiceModel.Activities.SendReply> 、 <xref:System.ServiceModel.Activities.Send> 、 <xref:System.ServiceModel.Activities.ReceiveReply>) 用于从工作流发送和接收 WCF 消息。</span><span class="sxs-lookup"><span data-stu-id="13e11-107">The messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) are used to send and receive WCF messages from your workflow.</span></span> <span data-ttu-id="13e11-108"><xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活动用于形成通过 WSDL 公开的 Windows Communication Foundation (WCF) 服务操作，就像标准 WCF web 服务一样。</span><span class="sxs-lookup"><span data-stu-id="13e11-108"><xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities are used to form a Windows Communication Foundation (WCF) service operation that is exposed via WSDL just like standard WCF web services.</span></span> <span data-ttu-id="13e11-109"><xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 用于使用类似于 WCF 的 web 服务 <xref:System.ServiceModel.ChannelFactory> ; 对于生成预配置活动的 Workflow Foundation 也存在 **添加服务引用** 体验。</span><span class="sxs-lookup"><span data-stu-id="13e11-109"><xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> are used to consume a web service similar to a WCF <xref:System.ServiceModel.ChannelFactory>; an **Add Service Reference** experience also exists for Workflow Foundation that generates pre-configured activities.</span></span>

### <a name="getting-started-with-messaging-activities"></a><span data-ttu-id="13e11-110">消息传递活动入门</span><span class="sxs-lookup"><span data-stu-id="13e11-110">Getting Started with Messaging Activities</span></span>

- <span data-ttu-id="13e11-111">在 Visual Studio 2012 中，创建一个 WCF 工作流服务应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="13e11-111">In Visual Studio 2012, create a WCF Workflow Service Application project.</span></span> <span data-ttu-id="13e11-112"><xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 对将置于画布上。</span><span class="sxs-lookup"><span data-stu-id="13e11-112">A <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> pair will be placed on your canvas.</span></span>

- <span data-ttu-id="13e11-113">右键单击该项目，然后选择 " **添加服务引用**"。</span><span class="sxs-lookup"><span data-stu-id="13e11-113">Right-click on the project and select **Add Service Reference**.</span></span> <span data-ttu-id="13e11-114">指向现有 web 服务 WSDL，并单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="13e11-114">Point to an existing web service WSDL and click **OK**.</span></span> <span data-ttu-id="13e11-115">生成项目以显示在 <xref:System.ServiceModel.Activities.Send> 工具箱中使用和) 实现的生成的活动 (<xref:System.ServiceModel.Activities.ReceiveReply> 。</span><span class="sxs-lookup"><span data-stu-id="13e11-115">Build your project to show the generated activities (implemented using <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply>) in your toolbox.</span></span>

- [<span data-ttu-id="13e11-116">工作流服务文档</span><span class="sxs-lookup"><span data-stu-id="13e11-116">Workflow services documentation</span></span>](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a><span data-ttu-id="13e11-117">消息传递活动示例方案</span><span class="sxs-lookup"><span data-stu-id="13e11-117">Messaging Activities Example Scenario</span></span>

<span data-ttu-id="13e11-118">`BestPriceFinder`服务会调用多个航空公司服务来查找特定路线的最佳票证价格。</span><span class="sxs-lookup"><span data-stu-id="13e11-118">A `BestPriceFinder` service calls out to multiple airline services to find the best ticket price for a particular route.</span></span> <span data-ttu-id="13e11-119">实现此方案需要你使用消息活动来接收价格请求、从后端服务检索价格以及使用最佳价格回复价格请求。</span><span class="sxs-lookup"><span data-stu-id="13e11-119">Implementing this scenario would require you to use the message activities to receive the price request, retrieve the prices from the back-end services, and reply to the price request with the best price.</span></span> <span data-ttu-id="13e11-120">还需要使用其他现成的活动来创建用于计算最佳价格的业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="13e11-120">It would also require you to use other out-of-box activities to create the business logic for calculating the best price.</span></span>

## <a name="workflowservicehost"></a><span data-ttu-id="13e11-121">WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="13e11-121">WorkflowServiceHost</span></span>

<span data-ttu-id="13e11-122"><xref:System.ServiceModel.WorkflowServiceHost>是支持多个实例、配置和 WCF 消息传递 (的现成工作流主机，但工作流不需要使用消息传递) 承载。</span><span class="sxs-lookup"><span data-stu-id="13e11-122">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren't required to use messaging in order to be hosted).</span></span> <span data-ttu-id="13e11-123">它还通过一组服务行为集成了持久性、跟踪和实例控件。</span><span class="sxs-lookup"><span data-stu-id="13e11-123">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span> <span data-ttu-id="13e11-124">就像 WCF 的一样 <xref:System.ServiceModel.ServiceHost> ， <xref:System.ServiceModel.WorkflowServiceHost> 可以在控制台/WINFORMS/WPF 应用程序或 Windows 服务中自承载，也可以在 IIS 或 WAS) 的 .xamlx 文件中自承载 (。</span><span class="sxs-lookup"><span data-stu-id="13e11-124">Just like WCF's <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in a console/WinForms/WPF application or Windows service, or web-hosted (as a .xamlx file) in IIS or WAS.</span></span>

### <a name="getting-started-with-workflow-service-host"></a><span data-ttu-id="13e11-125">工作流服务主机入门</span><span class="sxs-lookup"><span data-stu-id="13e11-125">Getting Started with Workflow Service Host</span></span>

- <span data-ttu-id="13e11-126">在 Visual Studio 2010 中，创建一个 WCF 工作流服务应用程序项目：此项目将设置为 <xref:System.ServiceModel.WorkflowServiceHost> 在 web 宿主环境中使用。</span><span class="sxs-lookup"><span data-stu-id="13e11-126">In Visual Studio 2010, create a WCF Workflow Service Application project: this project will be set up to use <xref:System.ServiceModel.WorkflowServiceHost> in a web-host environment.</span></span>

- <span data-ttu-id="13e11-127">若要承载非消息传递工作流，请添加一个自定义 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>，它将创建基于消息的实例。</span><span class="sxs-lookup"><span data-stu-id="13e11-127">In order to host a non-messaging workflow, add a custom <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> that will create the instance based on a message.</span></span>

- <span data-ttu-id="13e11-128">可通过将 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 添加到 <xref:System.ServiceModel.WorkflowServiceHost>，然后使用 <xref:System.ServiceModel.Activities.WorkflowControlClient> 来控制工作流实例（例如，已挂起或已终止）。</span><span class="sxs-lookup"><span data-stu-id="13e11-128">Workflow instances can be controlled (e.g. suspended or terminated) by adding a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> to the <xref:System.ServiceModel.WorkflowServiceHost> and then using a <xref:System.ServiceModel.Activities.WorkflowControlClient>.</span></span>

- <span data-ttu-id="13e11-129"><xref:System.ServiceModel.WorkflowServiceHost> 的示例可在以下部分找到：</span><span class="sxs-lookup"><span data-stu-id="13e11-129">Samples for the <xref:System.ServiceModel.WorkflowServiceHost> can be found in the following sections:</span></span>

  - [<span data-ttu-id="13e11-130">执行</span><span class="sxs-lookup"><span data-stu-id="13e11-130">Execution</span></span>](./samples/execution.md)

  - <span data-ttu-id="13e11-131">应用程序： [挂起的实例管理](./samples/suspended-instance-management.md)</span><span class="sxs-lookup"><span data-stu-id="13e11-131">Application: [Suspended Instance Management](./samples/suspended-instance-management.md)</span></span>

- [<span data-ttu-id="13e11-132">承载工作流服务概述</span><span class="sxs-lookup"><span data-stu-id="13e11-132">Hosting Workflow services overview</span></span>](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a><span data-ttu-id="13e11-133">WorkflowServiceHost 方案</span><span class="sxs-lookup"><span data-stu-id="13e11-133">WorkflowServiceHost Scenario</span></span>

<span data-ttu-id="13e11-134">BestPriceFinder 服务将调用多个航空公司服务来查找特定路线的最佳票证价格。</span><span class="sxs-lookup"><span data-stu-id="13e11-134">A BestPriceFinder service calls out to multiple airline services to find the best ticket price for a particular route.</span></span> <span data-ttu-id="13e11-135">实现此方案需要您在中承载工作流 <xref:System.ServiceModel.WorkflowServiceHost> 。</span><span class="sxs-lookup"><span data-stu-id="13e11-135">Implementing this scenario would require you to host the workflow in <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="13e11-136">它还将使用消息活动接收价格请求、从后端服务检索价格，并使用最大价格回复价格请求。</span><span class="sxs-lookup"><span data-stu-id="13e11-136">It would also use the message activities to receive the price request, retrieve the prices from the back-end services, and reply to the price request with the best price.</span></span>

## <a name="correlation"></a><span data-ttu-id="13e11-137">相关性</span><span class="sxs-lookup"><span data-stu-id="13e11-137">Correlation</span></span>

<span data-ttu-id="13e11-138">相关性具有以下两种含义：</span><span class="sxs-lookup"><span data-stu-id="13e11-138">A correlation is one of two things:</span></span>

- <span data-ttu-id="13e11-139">将消息组合在一起的方法；即，请求消息与其答复之间的关系。</span><span class="sxs-lookup"><span data-stu-id="13e11-139">A way of grouping messages together; that is, the relationship between a request message and its reply.</span></span>

- <span data-ttu-id="13e11-140">将一段数据映射到一个服务实例的方法</span><span class="sxs-lookup"><span data-stu-id="13e11-140">A way of mapping a piece of data to a service instance</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-141">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-141">Getting Started</span></span>

- <span data-ttu-id="13e11-142">若要开始学习相关性，请在 Visual Studio 中创建一个新项目。</span><span class="sxs-lookup"><span data-stu-id="13e11-142">To get started with correlation, create a new project in Visual Studio.</span></span> <span data-ttu-id="13e11-143">创建一个类型为 <xref:System.ServiceModel.Activities.CorrelationHandle> 的变量。</span><span class="sxs-lookup"><span data-stu-id="13e11-143">Create a variable of type <xref:System.ServiceModel.Activities.CorrelationHandle>.</span></span>

- <span data-ttu-id="13e11-144">例如，将消息组合在一起的请求-答复相关性就是用于将消息组合在一起的相关性。</span><span class="sxs-lookup"><span data-stu-id="13e11-144">An example of correlation used to group messages together is a Request-Reply correlation that groups messages together.</span></span>

  - <span data-ttu-id="13e11-145">在 <xref:System.ServiceModel.Activities.Receive> 活动上，单击 <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> 属性，并 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> 使用在上述第一步中创建的 CorrelationHandle 添加。</span><span class="sxs-lookup"><span data-stu-id="13e11-145">On a <xref:System.ServiceModel.Activities.Receive> activity, click on the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> property and add a <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> using the CorrelationHandle created in the first step above.</span></span>

  - <span data-ttu-id="13e11-146"><xref:System.ServiceModel.Activities.SendReply>右键单击 <xref:System.ServiceModel.Activities.Receive> 并单击 "创建 SendReply" 创建活动。</span><span class="sxs-lookup"><span data-stu-id="13e11-146">Create a <xref:System.ServiceModel.Activities.SendReply> activity by right-clicking on the <xref:System.ServiceModel.Activities.Receive> and clicking "Create SendReply".</span></span> <span data-ttu-id="13e11-147">将其粘贴到工作流中的 <xref:System.ServiceModel.Activities.Receive> 活动后。</span><span class="sxs-lookup"><span data-stu-id="13e11-147">Paste it into your workflow after the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

- <span data-ttu-id="13e11-148">将一段数据映射到一个服务实例的示例为基于内容的相关性，它将一段数据（例如，订单 ID）映射到一个特定的工作流实例。</span><span class="sxs-lookup"><span data-stu-id="13e11-148">An example of mapping a piece of data to a service instance is content-based correlation which maps a piece of data (for example, an order ID) to a particular workflow instance.</span></span>

  - <span data-ttu-id="13e11-149">在任何消息传递活动上，单击 `CorrelationInitializers` 属性，并使用上面创建的 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 变量添加 <xref:System.ServiceModel.Activities.CorrelationHandle>。</span><span class="sxs-lookup"><span data-stu-id="13e11-149">On any messaging activity, click on the `CorrelationInitializers` property and add a <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> using the <xref:System.ServiceModel.Activities.CorrelationHandle> variable created above.</span></span> <span data-ttu-id="13e11-150">从下拉菜单中，双击消息上的所需属性（如 OrderID）。</span><span class="sxs-lookup"><span data-stu-id="13e11-150">Double-click on the desired property on the message (e.g. OrderID) from the drop-down menu.</span></span> <span data-ttu-id="13e11-151">将 `CorrelatesWith` 属性设置为上面使用的 <xref:System.ServiceModel.Activities.CorrelationHandle> 变量。</span><span class="sxs-lookup"><span data-stu-id="13e11-151">Set the `CorrelatesWith` property to the <xref:System.ServiceModel.Activities.CorrelationHandle> variable used above.</span></span>

- [<span data-ttu-id="13e11-152">相关性概念文档</span><span class="sxs-lookup"><span data-stu-id="13e11-152">Correlation Conceptual Documentation</span></span>](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a><span data-ttu-id="13e11-153">相关性方案</span><span class="sxs-lookup"><span data-stu-id="13e11-153">Correlation Scenario</span></span>

<span data-ttu-id="13e11-154">订单处理工作流用于处理新订单创建和更新正在处理的现有订单。</span><span class="sxs-lookup"><span data-stu-id="13e11-154">An order-processing workflow is used to handle new order creation and updating existing orders that are in process.</span></span> <span data-ttu-id="13e11-155">实现此方案需要您在中承载工作流 <xref:System.ServiceModel.WorkflowServiceHost> 并使用消息传递活动。</span><span class="sxs-lookup"><span data-stu-id="13e11-155">Implementing this scenario would require you to host the workflow in <xref:System.ServiceModel.WorkflowServiceHost> and use the messaging activities.</span></span> <span data-ttu-id="13e11-156">它还需要基于的相关性 `orderId` 以确保对正确工作流进行更新。</span><span class="sxs-lookup"><span data-stu-id="13e11-156">It would also require correlation based on the `orderId` to ensure that updates are made to the correct workflow.</span></span>

## <a name="simplified-configuration"></a><span data-ttu-id="13e11-157">简化配置</span><span class="sxs-lookup"><span data-stu-id="13e11-157">Simplified Configuration</span></span>

<span data-ttu-id="13e11-158">WCF 配置架构很复杂，并为用户提供很多难以查找功能的用户。</span><span class="sxs-lookup"><span data-stu-id="13e11-158">The WCF configuration schema is complex and provides users with many hard to find features.</span></span> <span data-ttu-id="13e11-159">在中 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ，我们致力于帮助 WCF 用户使用以下功能配置其服务：</span><span class="sxs-lookup"><span data-stu-id="13e11-159">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], we have focused on helping WCF users configure their services with the following features:</span></span>

- <span data-ttu-id="13e11-160">使用户不需要为每个服务进行显式配置。</span><span class="sxs-lookup"><span data-stu-id="13e11-160">Removing the need for explicit per-service configuration.</span></span> <span data-ttu-id="13e11-161">如果未为服务配置任何 \<service> 元素，并且服务未以编程方式定义任何终结点，则会将一组终结点自动添加到服务、每个服务基址和服务实现的每个协定。</span><span class="sxs-lookup"><span data-stu-id="13e11-161">If you do not configure any \<service> elements for your service, and your service does not define programmatically any endpoint, then a set of endpoints will be automatically added to your service, one per service base address and per contract implemented by your service.</span></span>

- <span data-ttu-id="13e11-162">使用户能够为 WCF 绑定和行为定义默认值，这些默认值将应用于无显示配置的服务。</span><span class="sxs-lookup"><span data-stu-id="13e11-162">Enables the user to define default values for WCF bindings and behaviors, which will be applied to services with no explicit configuration.</span></span>

- <span data-ttu-id="13e11-163">标准终结点定义了可重用的预配置终结点，这些终结点具有一个或多个终结点属性（地址、绑定和协定）的固定值，并允许定义自定义属性。</span><span class="sxs-lookup"><span data-stu-id="13e11-163">Standard endpoints define reusable preconfigured endpoints, which have fixed values for one or more of the endpoint properties (address, binding and contract), and allow defining custom properties.</span></span>

- <span data-ttu-id="13e11-164">最后， <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 允许对 WCF 客户端配置进行集中管理，这在应用程序域加载时间之后选择或更改配置的情况下很有用。</span><span class="sxs-lookup"><span data-stu-id="13e11-164">Finally, the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows you to do central management of WCF client configuration, useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-165">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-165">Getting Started</span></span>

- <span data-ttu-id="13e11-166">[WCF 4.0 开发人员指南](/previous-versions/dotnet/articles/ee354381(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="13e11-166">[A Developer's Guide to WCF 4.0](/previous-versions/dotnet/articles/ee354381(v=msdn.10))</span></span>

- [<span data-ttu-id="13e11-167">配置通道工厂</span><span class="sxs-lookup"><span data-stu-id="13e11-167">Configuration Channel Factory</span></span>](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [<span data-ttu-id="13e11-168">标准终结点元素</span><span class="sxs-lookup"><span data-stu-id="13e11-168">Standard Endpoint Element</span></span>](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [<span data-ttu-id="13e11-169">.NET Framework 4 中的服务配置改进</span><span class="sxs-lookup"><span data-stu-id="13e11-169">Service configuration improvements in .NET Framework 4</span></span>](/archive/blogs/endpoint/service-configuration-improvements-in-net-4)

- [<span data-ttu-id="13e11-170">.NET 4 中的常见用户错误：WF/WCF 服务配置名称键入错误</span><span class="sxs-lookup"><span data-stu-id="13e11-170">Common User Mistake in .NET 4: Mistyping the WF/WCF Service Configuration Name</span></span>](/archive/blogs/endpoint/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name)

### <a name="simplified-configuration-scenarios"></a><span data-ttu-id="13e11-171">简化配置方案</span><span class="sxs-lookup"><span data-stu-id="13e11-171">Simplified Configuration Scenarios</span></span>

- <span data-ttu-id="13e11-172">经验丰富的 .ASMX 开发人员想要开始使用 WCF。</span><span class="sxs-lookup"><span data-stu-id="13e11-172">An experienced ASMX developer wants to start using WCF.</span></span> <span data-ttu-id="13e11-173">不过，WCF 看起来太复杂了！</span><span class="sxs-lookup"><span data-stu-id="13e11-173">However, WCF seems way too complicated!</span></span> <span data-ttu-id="13e11-174">我需要在配置文件中编写哪些信息呢？</span><span class="sxs-lookup"><span data-stu-id="13e11-174">What is all that information that I need to write in a configuration file?</span></span> <span data-ttu-id="13e11-175">在 .NET 4 中，您甚至可以决定完全不使用配置文件。</span><span class="sxs-lookup"><span data-stu-id="13e11-175">In .NET 4, you can even decide to not have a configuration file at all.</span></span>

- <span data-ttu-id="13e11-176">现有的一组 WCF 服务难以进行配置和维护。</span><span class="sxs-lookup"><span data-stu-id="13e11-176">An existing set of WCF services are very difficult to configure and maintain.</span></span> <span data-ttu-id="13e11-177">配置文件具有数千行 XML 代码，操作这些代码会产生很大的风险。</span><span class="sxs-lookup"><span data-stu-id="13e11-177">The configuration file has thousands of lines of XML code that are extremely dangerous to touch.</span></span> <span data-ttu-id="13e11-178">需要获得帮助以减少代码量，来提高可管理性。</span><span class="sxs-lookup"><span data-stu-id="13e11-178">Help is needed to reduce that amount of code to something more manageable.</span></span>

## <a name="data-contract-resolver"></a><span data-ttu-id="13e11-179">数据协定解析程序</span><span class="sxs-lookup"><span data-stu-id="13e11-179">Data Contract Resolver</span></span>

<span data-ttu-id="13e11-180">.NET 3.5 中包含对已知类型的设计的几个限制：</span><span class="sxs-lookup"><span data-stu-id="13e11-180">In .NET 3.5, there were a few limitations in the design of known types:</span></span>

- <span data-ttu-id="13e11-181">在序列化或反序列化过程中不能动态添加已知类型。</span><span class="sxs-lookup"><span data-stu-id="13e11-181">Adding known types dynamically, during serialization or deserialization, was not possible.</span></span>

- <span data-ttu-id="13e11-182">序列化程序无法处理未知的 xsi:type 信息。</span><span class="sxs-lookup"><span data-stu-id="13e11-182">Serializers could not deal with unknown xsi:type information.</span></span>

- <span data-ttu-id="13e11-183">用户无法指定他们想要在网络上显示的 xsi:type，例如，使网络上的序列化实例更小一些。</span><span class="sxs-lookup"><span data-stu-id="13e11-183">It was not possible for users to specify what xsi:type they would like to have appear on the wire to, for instance, make the size of a serialization instance on the wire smaller.</span></span>

<span data-ttu-id="13e11-184">[DataContractResolver](../wcf/samples/datacontractresolver.md)在 .net 4.5 中解决了这些问题。</span><span class="sxs-lookup"><span data-stu-id="13e11-184">The [DataContractResolver](../wcf/samples/datacontractresolver.md) solves these issues in .NET 4.5.</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-185">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-185">Getting Started</span></span>

- [<span data-ttu-id="13e11-186">数据协定解析程序 API 文档</span><span class="sxs-lookup"><span data-stu-id="13e11-186">Data Contract Resolver API documentation</span></span>](xref:System.Runtime.Serialization.DataContractResolver)

- [<span data-ttu-id="13e11-187">引入数据协定解析程序</span><span class="sxs-lookup"><span data-stu-id="13e11-187">Introducing the Data Contract Resolver</span></span>](/archive/blogs/youssefm/configuring-known-types-dynamically-introducing-the-datacontractresolver)

- <span data-ttu-id="13e11-188">示例：</span><span class="sxs-lookup"><span data-stu-id="13e11-188">Samples:</span></span>

  - [<span data-ttu-id="13e11-189">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="13e11-189">DataContractResolver</span></span>](../wcf/samples/datacontractresolver.md)

  - [<span data-ttu-id="13e11-190">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="13e11-190">KnownAssemblyAttribute</span></span>](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a><span data-ttu-id="13e11-191">数据协定解析程序方案</span><span class="sxs-lookup"><span data-stu-id="13e11-191">Data Contract Resolver Scenarios</span></span>

- <span data-ttu-id="13e11-192">无需在服务中声明数十个 <xref:System.Runtime.Serialization.KnownTypeAttribute> 对象。</span><span class="sxs-lookup"><span data-stu-id="13e11-192">Avoiding having to declare tens of <xref:System.Runtime.Serialization.KnownTypeAttribute> objects in a service.</span></span>

- <span data-ttu-id="13e11-193">减小 XML Blob 的大小。</span><span class="sxs-lookup"><span data-stu-id="13e11-193">Reducing the size of the XML blob.</span></span>

## <a name="flowchart"></a><span data-ttu-id="13e11-194">流程图</span><span class="sxs-lookup"><span data-stu-id="13e11-194">Flowchart</span></span>

<span data-ttu-id="13e11-195">流程图是用于以可视方式表示域问题的已知范例。</span><span class="sxs-lookup"><span data-stu-id="13e11-195">Flowchart is a well-known paradigm to visually represent domain problems.</span></span> <span data-ttu-id="13e11-196">它是我们在 .NET 4 中引入的新的控制流样式。</span><span class="sxs-lookup"><span data-stu-id="13e11-196">It is a new control flow style we're introducing in .NET 4.</span></span> <span data-ttu-id="13e11-197">流程图的核心特点是，在任何给定时间只能执行一个活动。</span><span class="sxs-lookup"><span data-stu-id="13e11-197">A core characteristic of Flowchart is that only one activity is executed at any given time.</span></span> <span data-ttu-id="13e11-198">流程图可以表示循环和备选结果，但无法表示多个节点的并发执行。</span><span class="sxs-lookup"><span data-stu-id="13e11-198">Flowcharts can express loops and alternative outcomes, but cannot natively express concurrent execution of multiple nodes.</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-199">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-199">Getting Started</span></span>

- <span data-ttu-id="13e11-200">在 Visual Studio 2012 中，创建工作流控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="13e11-200">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="13e11-201">在工作流设计器中添加流程图。</span><span class="sxs-lookup"><span data-stu-id="13e11-201">Add a Flowchart in the workflow designer.</span></span>

- <span data-ttu-id="13e11-202">流程图功能使用以下类：</span><span class="sxs-lookup"><span data-stu-id="13e11-202">The flowchart feature uses the following classes:</span></span>

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- <span data-ttu-id="13e11-203">示例：</span><span class="sxs-lookup"><span data-stu-id="13e11-203">Samples:</span></span>

  - [<span data-ttu-id="13e11-204">使用 TryCatch 在 Flowchart 活动中进行错误处理</span><span class="sxs-lookup"><span data-stu-id="13e11-204">Fault Handling in a Flowchart Activity Using TryCatch</span></span>](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [<span data-ttu-id="13e11-205">招聘流程</span><span class="sxs-lookup"><span data-stu-id="13e11-205">Hiring Process</span></span>](./samples/hiring-process.md)

- <span data-ttu-id="13e11-206">设计器文档：</span><span class="sxs-lookup"><span data-stu-id="13e11-206">Designer Documentation:</span></span>

  - [<span data-ttu-id="13e11-207">流程图活动设计器</span><span class="sxs-lookup"><span data-stu-id="13e11-207">Flowchart Activity Designers</span></span>](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a><span data-ttu-id="13e11-208">流程图方案</span><span class="sxs-lookup"><span data-stu-id="13e11-208">Flowchart Scenarios</span></span>

<span data-ttu-id="13e11-209">流程图活动可用于实现猜谜游戏。</span><span class="sxs-lookup"><span data-stu-id="13e11-209">A flowchart activity can be used to implement a guessing game.</span></span> <span data-ttu-id="13e11-210">猜谜游戏非常简单：计算机选择一个随机数，然后玩家必须猜出该数字。</span><span class="sxs-lookup"><span data-stu-id="13e11-210">The guessing game is very simple: the computer selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="13e11-211">当播放机提交每个猜测时，计算机将显示一个提示， (即 "尝试使用较小的数字" ) 。</span><span class="sxs-lookup"><span data-stu-id="13e11-211">When the player submits each guess, the computer shows them a hint (i.e. "try a lower number").</span></span> <span data-ttu-id="13e11-212">如果播放机在尝试次数少于7次时发现数字，则会从计算机接收特殊的表意。</span><span class="sxs-lookup"><span data-stu-id="13e11-212">If the player finds the number in less than 7 attempts, they receive a special congratulation from the computer.</span></span> <span data-ttu-id="13e11-213">可使用以下过程活动组合来实现此游戏：</span><span class="sxs-lookup"><span data-stu-id="13e11-213">This game can be implemented with a combination of the following procedural activities:</span></span>

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a><span data-ttu-id="13e11-214">过程活动（Sequence、If、ForEach、Switch、Assign、DoWhile 和 While）</span><span class="sxs-lookup"><span data-stu-id="13e11-214">Procedural activities (Sequence, If, ForEach, Switch, Assign, DoWhile, While)</span></span>

<span data-ttu-id="13e11-215">过程活动提供了一种机制，该机制使用程序员熟悉的概念为顺序控制流建模。</span><span class="sxs-lookup"><span data-stu-id="13e11-215">Procedural activities provide a mechanism to model sequential control flow using concepts that are familiar to programmers.</span></span> <span data-ttu-id="13e11-216">这些活动启用传统的结构化编程语言构造，并在适当的情况下使用 c # 和 Visual Basic 等常见过程语言提供语言奇偶校验。</span><span class="sxs-lookup"><span data-stu-id="13e11-216">These activities enable traditionally structured programming language constructs and, when appropriate, provide language parity with common procedural languages such as C# and Visual Basic.</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-217">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-217">Getting Started</span></span>

- <span data-ttu-id="13e11-218">在 Visual Studio 2012 中，创建工作流控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="13e11-218">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="13e11-219">在工作流设计器中添加过程活动。</span><span class="sxs-lookup"><span data-stu-id="13e11-219">Add procedural activities in the workflow designer.</span></span>

- <span data-ttu-id="13e11-220">示例：</span><span class="sxs-lookup"><span data-stu-id="13e11-220">Samples:</span></span>

  - [<span data-ttu-id="13e11-221">招聘流程</span><span class="sxs-lookup"><span data-stu-id="13e11-221">Hiring Process</span></span>](./samples/hiring-process.md)

  - [<span data-ttu-id="13e11-222">企业采购过程</span><span class="sxs-lookup"><span data-stu-id="13e11-222">Corporate Purchase Process</span></span>](./samples/corporate-purchase-process.md)

- <span data-ttu-id="13e11-223">设计器文档：</span><span class="sxs-lookup"><span data-stu-id="13e11-223">Designer Documentation:</span></span>

  - [<span data-ttu-id="13e11-224">Parallel 活动设计器</span><span class="sxs-lookup"><span data-stu-id="13e11-224">Parallel Activity Designer</span></span>](/visualstudio/workflow-designer/parallel-activity-designer)

  - [<span data-ttu-id="13e11-225">ParallelForEach\<T> 活动设计器</span><span class="sxs-lookup"><span data-stu-id="13e11-225">ParallelForEach\<T> Activity Designer</span></span>](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a><span data-ttu-id="13e11-226">过程活动方案</span><span class="sxs-lookup"><span data-stu-id="13e11-226">Procedural Activity Scenarios</span></span>

- <span data-ttu-id="13e11-227"><xref:System.Activities.Statements.Parallel>： Intranet 文档管理系统具有文档审批工作流。</span><span class="sxs-lookup"><span data-stu-id="13e11-227"><xref:System.Activities.Statements.Parallel>: An intranet document management system has a document approval workflow.</span></span> <span data-ttu-id="13e11-228">文档需要先经过多个部门人员的审批，然后才能发布到 Intranet。</span><span class="sxs-lookup"><span data-stu-id="13e11-228">Documents need to be approved by people in several departments before they can be published to the intranet.</span></span> <span data-ttu-id="13e11-229">没有建立批准的顺序;当文档处于 "批准挂起" 阶段时，它们可能会随时发生。</span><span class="sxs-lookup"><span data-stu-id="13e11-229">There isn't an established order for the approvals; they can occur at any time while the document is in the "approval pending" phase.</span></span> <span data-ttu-id="13e11-230">当用户提交要审阅的文档时，必须由其直接管理者、intranet 管理员和内部通信管理器批准。</span><span class="sxs-lookup"><span data-stu-id="13e11-230">When a user submits a document for review, it must be approved by their direct manager, the intranet administrator, and the internal communications manager.</span></span>

- <span data-ttu-id="13e11-231"><xref:System.Activities.Statements.ParallelForEach%601>：WF 应用程序将管理大型公司内的公司采购。</span><span class="sxs-lookup"><span data-stu-id="13e11-231"><xref:System.Activities.Statements.ParallelForEach%601>: A WF application manages corporate buys within a large company.</span></span> <span data-ttu-id="13e11-232">公司规则指明，在计划任何采购操作前需要评估三个不同的供应商。</span><span class="sxs-lookup"><span data-stu-id="13e11-232">The corporate rules dictate that before planning any purchase operation, the valuations of three different vendors is required.</span></span> <span data-ttu-id="13e11-233">购买部门的员工从公司的供应商列表中选择三个供应商。</span><span class="sxs-lookup"><span data-stu-id="13e11-233">An employee from the buying department selects three vendors from the company's vendor list.</span></span> <span data-ttu-id="13e11-234">在选择这些供应商并向他们发送通知后，公司将等待他们提出经济实惠的建议。</span><span class="sxs-lookup"><span data-stu-id="13e11-234">After these vendors have been selected and notified, the company will wait for their economic proposals.</span></span> <span data-ttu-id="13e11-235">这些建议会以任意顺序出现。</span><span class="sxs-lookup"><span data-stu-id="13e11-235">The proposals can come in any order.</span></span> <span data-ttu-id="13e11-236">为了在 WF 中实现此方案，我们使用了 <xref:System.Activities.Statements.ParallelForEach%601>，它会循环访问供应商集合并要求他们提供经济建议。</span><span class="sxs-lookup"><span data-stu-id="13e11-236">To implement this scenario in WF, we use a <xref:System.Activities.Statements.ParallelForEach%601> that will iterate through our collection of vendors and ask for their economic proposals.</span></span> <span data-ttu-id="13e11-237">收集完所有建议后，选择并显示最好的建议。</span><span class="sxs-lookup"><span data-stu-id="13e11-237">After all offers are gathered, the best one is selected and displayed.</span></span>

## <a name="invokemethod"></a><span data-ttu-id="13e11-238">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="13e11-238">InvokeMethod</span></span>

<span data-ttu-id="13e11-239"><xref:System.Activities.Statements.InvokeMethod> 活动允许在范围内的对象或类型中调用公共方法。</span><span class="sxs-lookup"><span data-stu-id="13e11-239">The <xref:System.Activities.Statements.InvokeMethod> activity allows invoking public methods in objects or types in scope.</span></span> <span data-ttu-id="13e11-240">它支持调用实例和带有或不带参数（包括参数数组）的静态方法以及泛型方法。</span><span class="sxs-lookup"><span data-stu-id="13e11-240">It supports invoking instance and static methods with or without parameters (including parameter arrays), and generic methods.</span></span> <span data-ttu-id="13e11-241">它还允许以同步方式和异步方式执行方法。</span><span class="sxs-lookup"><span data-stu-id="13e11-241">It also allows executing method synchronously and asynchronously.</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-242">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-242">Getting Started</span></span>

- <span data-ttu-id="13e11-243">在 Visual Studio 2012 中，创建工作流控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="13e11-243">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="13e11-244">在工作流设计器中添加一个 <xref:System.Activities.Statements.InvokeMethod> 活动，并对该活动配置静态和实例方法。</span><span class="sxs-lookup"><span data-stu-id="13e11-244">Add an <xref:System.Activities.Statements.InvokeMethod> activity in the workflow designer, and configure static and instance methods on it.</span></span>

- <span data-ttu-id="13e11-245">设计器文档： [InvokeMethod 活动设计器](/visualstudio/workflow-designer/invokemethod-activity-designer)</span><span class="sxs-lookup"><span data-stu-id="13e11-245">Designer Documentation: [InvokeMethod Activity Designer](/visualstudio/workflow-designer/invokemethod-activity-designer)</span></span>

### <a name="invokemethod-scenarios"></a><span data-ttu-id="13e11-246">InvokeMethod 方案</span><span class="sxs-lookup"><span data-stu-id="13e11-246">InvokeMethod Scenarios</span></span>

- <span data-ttu-id="13e11-247">需要调用范围内的对象中的方法。</span><span class="sxs-lookup"><span data-stu-id="13e11-247">A method in an object in scope needs to be invoked.</span></span> <span data-ttu-id="13e11-248">例如，需要将值添加到词典。</span><span class="sxs-lookup"><span data-stu-id="13e11-248">For example, a value needs to be added to a dictionary.</span></span> <span data-ttu-id="13e11-249">调用词典实例的 Add 方法并提供键和值。</span><span class="sxs-lookup"><span data-stu-id="13e11-249">The Add method of the instance of the dictionary is invoked, and the key and value are provided.</span></span>

- <span data-ttu-id="13e11-250">需要对旧 CLR 对象调用方法。</span><span class="sxs-lookup"><span data-stu-id="13e11-250">A method needs to be invoked on a legacy CLR object.</span></span> <span data-ttu-id="13e11-251">如果旧类在工作流执行过程中位于范围内，则可以使用 <xref:System.Activities.Statements.InvokeMethod>，而不是创建将包装对该旧类的调用的自定义活动。</span><span class="sxs-lookup"><span data-stu-id="13e11-251">Instead of creating a custom activity to wrap the call to that legacy class, if it is in scope during the workflow execution, <xref:System.Activities.Statements.InvokeMethod> can be used.</span></span>

## <a name="error-handling-activities"></a><span data-ttu-id="13e11-252">错误处理活动</span><span class="sxs-lookup"><span data-stu-id="13e11-252">Error handling activities</span></span>

<span data-ttu-id="13e11-253"><xref:System.Activities.Statements.TryCatch>活动提供了一种机制，用于捕获在执行一组包含的活动的过程中发生的异常， (类似于 c # 中的 Try/Catch 构造和 Visual Basic) 。</span><span class="sxs-lookup"><span data-stu-id="13e11-253">The <xref:System.Activities.Statements.TryCatch> activity provides a mechanism for catching exceptions that occur during the execution of a set of contained activities (similar to the Try/Catch construct in C# and Visual Basic).</span></span> <span data-ttu-id="13e11-254"><xref:System.Activities.Statements.TryCatch> 提供了工作流级别的异常处理。</span><span class="sxs-lookup"><span data-stu-id="13e11-254"><xref:System.Activities.Statements.TryCatch> provides exception handling at the workflow level.</span></span> <span data-ttu-id="13e11-255">当引发未经处理的异常时，工作流将中止，并且不会执行 Finally 块。</span><span class="sxs-lookup"><span data-stu-id="13e11-255">When an unhandled exception is thrown, the workflow is aborted and the Finally block won't be executed.</span></span> <span data-ttu-id="13e11-256">此行为与 C# 一致。</span><span class="sxs-lookup"><span data-stu-id="13e11-256">This behavior is consistent with C#.</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-257">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-257">Getting Started</span></span>

- <span data-ttu-id="13e11-258">在 Visual Studio 2012 中，创建工作流控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="13e11-258">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="13e11-259">在工作流设计器中添加 <xref:System.Activities.Statements.TryCatch> 活动。</span><span class="sxs-lookup"><span data-stu-id="13e11-259">Add a <xref:System.Activities.Statements.TryCatch> activity in the workflow designer.</span></span>

- <span data-ttu-id="13e11-260">示例： [使用 TryCatch 在 Flowchart 活动中进行错误处理](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)</span><span class="sxs-lookup"><span data-stu-id="13e11-260">Sample: [Fault Handling in a Flowchart Activity Using TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)</span></span>

- <span data-ttu-id="13e11-261">设计器文档： [错误处理活动设计器](/visualstudio/workflow-designer/error-handling-activity-designers)</span><span class="sxs-lookup"><span data-stu-id="13e11-261">Designer Documentation: [Error Handling Activity Designers](/visualstudio/workflow-designer/error-handling-activity-designers)</span></span>

### <a name="error-handling-scenarios"></a><span data-ttu-id="13e11-262">错误处理方案</span><span class="sxs-lookup"><span data-stu-id="13e11-262">Error handling scenarios</span></span>

<span data-ttu-id="13e11-263">需要执行一组活动，并且需要在发生错误时执行特定的逻辑。</span><span class="sxs-lookup"><span data-stu-id="13e11-263">A set of activities needs to be executed, and specific logic needs to be executed when an error occurs.</span></span> <span data-ttu-id="13e11-264">如果在执行错误处理逻辑的过程中发现该错误是不可恢复的，则会重新引发该异常，并且父活动（或主机）将处理该问题。</span><span class="sxs-lookup"><span data-stu-id="13e11-264">If during that error handling logic it is found that the error is not recoverable, the exception will be rethrown, and the parent activity (or the host) will deal with the problem.</span></span>

## <a name="pick-activity"></a><span data-ttu-id="13e11-265">Pick 活动</span><span class="sxs-lookup"><span data-stu-id="13e11-265">Pick activity</span></span>

<span data-ttu-id="13e11-266"><xref:System.Activities.Statements.Pick> 活动在 WF 中提供基于事件的控制流建模。</span><span class="sxs-lookup"><span data-stu-id="13e11-266">The <xref:System.Activities.Statements.Pick> Activity provides event-based control flow modeling in WF.</span></span> <span data-ttu-id="13e11-267"><xref:System.Activities.Statements.Pick> 包含多个分支，其中每个分支均要等到特定事件发生后才会运行。</span><span class="sxs-lookup"><span data-stu-id="13e11-267"><xref:System.Activities.Statements.Pick> contains many branches where each branch waits for a particular event to occur before running.</span></span> <span data-ttu-id="13e11-268">在此设置中，<xref:System.Activities.Statements.Pick> 的行为类似于 <xref:System.Activities.Statements.Switch%601>，该活动将只对其执行正在侦听的一组事件中的某个事件。</span><span class="sxs-lookup"><span data-stu-id="13e11-268">In this setup, a <xref:System.Activities.Statements.Pick> behaves similar to a <xref:System.Activities.Statements.Switch%601> to which the Activity will execute only one of the set of events it is listening.</span></span> <span data-ttu-id="13e11-269">每个分支都是事件驱动的，并且发生的事件将先运行对应的分支。</span><span class="sxs-lookup"><span data-stu-id="13e11-269">Each branch is event driven and the event that occurs runs the corresponding branch first.</span></span> <span data-ttu-id="13e11-270">所有其他分支会取消并停止侦听事件。</span><span class="sxs-lookup"><span data-stu-id="13e11-270">All other branches cancel and stop listening for events.</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-271">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-271">Getting Started</span></span>

- <span data-ttu-id="13e11-272">在 Visual Studio 2012 中，创建工作流控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="13e11-272">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="13e11-273">在工作流设计器中添加 <xref:System.Activities.Statements.Pick> 活动。</span><span class="sxs-lookup"><span data-stu-id="13e11-273">Add a <xref:System.Activities.Statements.Pick> activity in the workflow designer.</span></span>

- <span data-ttu-id="13e11-274">示例： [使用 Pick 活动](./samples/using-the-pick-activity.md)</span><span class="sxs-lookup"><span data-stu-id="13e11-274">Sample: [Using the Pick Activity](./samples/using-the-pick-activity.md)</span></span>

- <span data-ttu-id="13e11-275">设计器文档： [Pick 活动设计器](/visualstudio/workflow-designer/pick-activity-designer)</span><span class="sxs-lookup"><span data-stu-id="13e11-275">Designer documentation: [Pick Activity Designer](/visualstudio/workflow-designer/pick-activity-designer)</span></span>

### <a name="pick-scenario"></a><span data-ttu-id="13e11-276">Pick 方案</span><span class="sxs-lookup"><span data-stu-id="13e11-276">Pick Scenario</span></span>

<span data-ttu-id="13e11-277">系统需要提示用户进行输入。</span><span class="sxs-lookup"><span data-stu-id="13e11-277">A user needs to be prompted for input.</span></span> <span data-ttu-id="13e11-278">在正常情况下，开发人员将使用类似的方法调用 <xref:System.Console.ReadLine%2A> 来提示用户输入。</span><span class="sxs-lookup"><span data-stu-id="13e11-278">Under normal circumstances, the developer would use a method call like <xref:System.Console.ReadLine%2A> to prompt for a user's input.</span></span> <span data-ttu-id="13e11-279">此设置的问题是，程序会一直等到用户输入后才运行。</span><span class="sxs-lookup"><span data-stu-id="13e11-279">The problem with this setup is that the program waits until the user enters something.</span></span> <span data-ttu-id="13e11-280">在此方案中，需要超时来取消对阻止活动的阻止。</span><span class="sxs-lookup"><span data-stu-id="13e11-280">In this scenario, a time-out is needed to unblock a blocking activity.</span></span> <span data-ttu-id="13e11-281">常见的方案会要求在给定持续时间内完成任务。</span><span class="sxs-lookup"><span data-stu-id="13e11-281">A common scenario is one that requires a task to be completed within a given time duration.</span></span> <span data-ttu-id="13e11-282">在阻止活动超时的方案中，Pick 将添加大量值。</span><span class="sxs-lookup"><span data-stu-id="13e11-282">Timing out a blocking activity is a scenario where Pick adds a lot of value.</span></span>

## <a name="wcf-routing-service"></a><span data-ttu-id="13e11-283">WCF 路由服务</span><span class="sxs-lookup"><span data-stu-id="13e11-283">WCF Routing Service</span></span>

<span data-ttu-id="13e11-284">路由服务是一种通用软件路由器，可用于控制 WCF 消息在客户端和服务之间的流动方式。</span><span class="sxs-lookup"><span data-stu-id="13e11-284">The Routing Service is designed to be a generic software Router that allows you to control how WCF messages flow in between your clients and services.</span></span> <span data-ttu-id="13e11-285">使用路由服务，您可以将客户端与服务分离，这为您提供了更大的可支持的配置，并且在考虑如何托管服务时具有的灵活性。</span><span class="sxs-lookup"><span data-stu-id="13e11-285">The Routing Service allows you to decouple your clients from your services, which gives you much more freedom in terms of the configurations that you can support and the flexibility you have when considering how to host your services.</span></span> <span data-ttu-id="13e11-286">在 .NET 3.5 中，客户端和服务紧密耦合;客户端必须了解它需要与之通信的所有服务。</span><span class="sxs-lookup"><span data-stu-id="13e11-286">In .NET 3.5, clients and services were tightly coupled; a client had to know about all of the services it needed to talk to and where they were located.</span></span> <span data-ttu-id="13e11-287">此外，.NET Framework 3.5 中的 WCF 具有以下限制：</span><span class="sxs-lookup"><span data-stu-id="13e11-287">In addition, WCF in .NET Framework 3.5 had the following limitations:</span></span>

- <span data-ttu-id="13e11-288">错误处理较为复杂，因为必须将此逻辑硬编码到客户端中。</span><span class="sxs-lookup"><span data-stu-id="13e11-288">Error handling was complex, as this logic had to be hard-coded into the client.</span></span>

- <span data-ttu-id="13e11-289">客户端和服务必须始终使用同一绑定。</span><span class="sxs-lookup"><span data-stu-id="13e11-289">Clients and services had to always use the same bindings.</span></span>

- <span data-ttu-id="13e11-290">服务很少能适当地分解：让客户端与一个能实现所有操作的服务进行通信而不必在多个服务之间选择，这样的做法更简单一些。</span><span class="sxs-lookup"><span data-stu-id="13e11-290">Services were rarely well factored: it is easier to have the client talk to one service which implements everything, rather than needing to choose between multiple services.</span></span>

<span data-ttu-id="13e11-291">.NET 4 中的路由服务旨在更轻松地解决这些问题。</span><span class="sxs-lookup"><span data-stu-id="13e11-291">The routing service in .NET 4 is designed to make these problems easier to solve.</span></span> <span data-ttu-id="13e11-292">新的路由服务具有以下功能：</span><span class="sxs-lookup"><span data-stu-id="13e11-292">The new routing service has the following features:</span></span>

1. <span data-ttu-id="13e11-293">基于内容的路由（<xref:System.ServiceModel.Dispatcher.MessageFilter> 对象会检查消息以确定其发送位置。）</span><span class="sxs-lookup"><span data-stu-id="13e11-293">Content based routing (<xref:System.ServiceModel.Dispatcher.MessageFilter> objects examine a message to determine where it should be sent.)</span></span>

2. <span data-ttu-id="13e11-294">协议桥接 (传输 & 消息) </span><span class="sxs-lookup"><span data-stu-id="13e11-294">Protocol bridging (transport & message)</span></span>

3. <span data-ttu-id="13e11-295">错误处理（路由器将捕获通信异常并将故障转移到备份终结点）</span><span class="sxs-lookup"><span data-stu-id="13e11-295">Error handling (the router catches communication exceptions and fails over to backup endpoints)</span></span>

4. <span data-ttu-id="13e11-296"><xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 和路由配置的动态（内存中）更新。</span><span class="sxs-lookup"><span data-stu-id="13e11-296">Dynamic (in memory) update of <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> and Routing Configuration.</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-297">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-297">Getting Started</span></span>

1. <span data-ttu-id="13e11-298">文档： [路由](../wcf/feature-details/routing.md)</span><span class="sxs-lookup"><span data-stu-id="13e11-298">Documentation: [Routing](../wcf/feature-details/routing.md)</span></span>

2. <span data-ttu-id="13e11-299">示例： [路由服务 &#91;WCF 示例&#93;](../wcf/samples/routing-services.md)</span><span class="sxs-lookup"><span data-stu-id="13e11-299">Samples: [Routing Services &#91;WCF Samples&#93;](../wcf/samples/routing-services.md)</span></span>

3. <span data-ttu-id="13e11-300">博客： [路由规则！](/archive/blogs/RoutingRules/)</span><span class="sxs-lookup"><span data-stu-id="13e11-300">Blog: [Routing Rules!](/archive/blogs/RoutingRules/)</span></span>

### <a name="routing-scenarios"></a><span data-ttu-id="13e11-301">路由方案</span><span class="sxs-lookup"><span data-stu-id="13e11-301">Routing Scenarios</span></span>

<span data-ttu-id="13e11-302">路由服务在以下方案中很有用：</span><span class="sxs-lookup"><span data-stu-id="13e11-302">The routing service is useful in the following scenarios:</span></span>

- <span data-ttu-id="13e11-303">客户端可与多个服务通信，而无需直接处理所有这些服务。</span><span class="sxs-lookup"><span data-stu-id="13e11-303">Clients can talk to multiple services without having to address them all directly.</span></span>

- <span data-ttu-id="13e11-304">客户端可对客户端请求执行其他逻辑以确定其路由位置</span><span class="sxs-lookup"><span data-stu-id="13e11-304">Clients can perform additional logic on a client request to determine where to route it</span></span>

- <span data-ttu-id="13e11-305">将客户端执行的操作分解为多个服务实现而不重构客户端。</span><span class="sxs-lookup"><span data-stu-id="13e11-305">Decompose the operations a client performs into multiple service implementations without refactoring the client.</span></span>

- <span data-ttu-id="13e11-306">客户端和服务可与具有不同安全设置的不同绑定进行通信。</span><span class="sxs-lookup"><span data-stu-id="13e11-306">Clients and services can speak different bindings with different security settings.</span></span>

- <span data-ttu-id="13e11-307">可以使客户端更为可靠一些，从而防止出现故障或服务不可用的情况。</span><span class="sxs-lookup"><span data-stu-id="13e11-307">Clients can be enabled to be more robust against failure or the unavailability of services.</span></span>

## <a name="wcf-discovery"></a><span data-ttu-id="13e11-308">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="13e11-308">WCF Discovery</span></span>

<span data-ttu-id="13e11-309">WCF 发现是一种框架技术，可让你将发现机制纳入应用程序基础结构。</span><span class="sxs-lookup"><span data-stu-id="13e11-309">WCF Discovery is a framework technology that allows you to incorporate a discovery mechanism to your application infrastructure.</span></span> <span data-ttu-id="13e11-310">利用此技术，您可以使服务可发现，并配置客户端以搜索服务。</span><span class="sxs-lookup"><span data-stu-id="13e11-310">You can use this to make your service discoverable, and configure your clients to search for services.</span></span> <span data-ttu-id="13e11-311">不再需要使用终结点对客户端进行硬编码，即可使应用程序的可靠性更高，容错能力更强。</span><span class="sxs-lookup"><span data-stu-id="13e11-311">Clients no longer need to be hard coded with endpoint, making your application more robust and fault tolerant.</span></span> <span data-ttu-id="13e11-312">Discovery 是一个用于将自动配置功能构建到应用程序中的最佳平台。</span><span class="sxs-lookup"><span data-stu-id="13e11-312">Discovery is the perfect platform to build auto-configuration capabilities into your application.</span></span>

<span data-ttu-id="13e11-313">该产品是基于 WS-Discovery 标准构建的。</span><span class="sxs-lookup"><span data-stu-id="13e11-313">The product is built on top of the WS-Discovery standard.</span></span> <span data-ttu-id="13e11-314">它设计为可互操作、可扩展和通用。</span><span class="sxs-lookup"><span data-stu-id="13e11-314">It's designed to be interoperable, extensible, and generic.</span></span> <span data-ttu-id="13e11-315">该产品支持两种操作模式：</span><span class="sxs-lookup"><span data-stu-id="13e11-315">The product supports two modes of operation:</span></span>

1. <span data-ttu-id="13e11-316">托管：在此模式中，网络上有一个了解现有服务的实体，客户端可直接从该实体查询信息。</span><span class="sxs-lookup"><span data-stu-id="13e11-316">Managed: where there is an entity on the network knowledgeable about existing services, clients query it directly for information.</span></span> <span data-ttu-id="13e11-317">这与 Active Directory 类似。</span><span class="sxs-lookup"><span data-stu-id="13e11-317">This is analogous to Active Directory.</span></span>

2. <span data-ttu-id="13e11-318">临时：在此模式中，客户端使用多播消息来查找服务。</span><span class="sxs-lookup"><span data-stu-id="13e11-318">Ad-hoc: where clients use multicast messages to locate services.</span></span>

<span data-ttu-id="13e11-319">此外，发现消息是网络协议不可知的；可以对支持该模式需求的任何协议使用它们。</span><span class="sxs-lookup"><span data-stu-id="13e11-319">Furthermore, discovery messages are network protocol agnostic; you can use them on top any protocol that supports the mode requirements.</span></span> <span data-ttu-id="13e11-320">例如，发现多播消息可以通过 UDP 通道或支持多播消息的任何其他网络发送。</span><span class="sxs-lookup"><span data-stu-id="13e11-320">For example, discovery multicast messages can be sent over the UDP channel or any other network that supports multicast messaging.</span></span> <span data-ttu-id="13e11-321">这些设计点与功能灵活性结合，使你能够将发现专门调整到你的解决方案。</span><span class="sxs-lookup"><span data-stu-id="13e11-321">These design points, combined with feature flexibility, allow you to adapt the discovery specifically to your solution.</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-322">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-322">Getting Started</span></span>

- <span data-ttu-id="13e11-323">文档： [WCF 发现](../wcf/feature-details/wcf-discovery.md)</span><span class="sxs-lookup"><span data-stu-id="13e11-323">Documentation: [WCF Discovery](../wcf/feature-details/wcf-discovery.md)</span></span>

- <span data-ttu-id="13e11-324">示例： [发现 (示例) ](../wcf/samples/discovery-samples.md)</span><span class="sxs-lookup"><span data-stu-id="13e11-324">Samples: [Discovery (Samples)](../wcf/samples/discovery-samples.md)</span></span>

### <a name="discovery-scenarios"></a><span data-ttu-id="13e11-325">Discovery 方案</span><span class="sxs-lookup"><span data-stu-id="13e11-325">Discovery Scenarios</span></span>

<span data-ttu-id="13e11-326">开发人员不希望对终结点进行硬编码，因为我的服务的可用时间未知。</span><span class="sxs-lookup"><span data-stu-id="13e11-326">A developer doesn't want to hard code endpoints, since it is unknown when my service will be available.</span></span> <span data-ttu-id="13e11-327">相反，开发人员希望在运行时选择服务。</span><span class="sxs-lookup"><span data-stu-id="13e11-327">Instead, the developer wants to choose a service at runtime.</span></span> <span data-ttu-id="13e11-328">应用程序的各个组件之间需要更大程度的分离、稳定性和自动配置。</span><span class="sxs-lookup"><span data-stu-id="13e11-328">More decoupling, robustness, and auto-configuration is needed between the components in the application.</span></span>

## <a name="tracking"></a><span data-ttu-id="13e11-329">跟踪</span><span class="sxs-lookup"><span data-stu-id="13e11-329">Tracking</span></span>

<span data-ttu-id="13e11-330">工作流跟踪提供对工作流实例的执行的见解。</span><span class="sxs-lookup"><span data-stu-id="13e11-330">Workflow tracking provides insight into the execution of a workflow instance.</span></span> <span data-ttu-id="13e11-331">跟踪事件在工作流实例级别从工作流发出，并在工作流中执行活动时发出。</span><span class="sxs-lookup"><span data-stu-id="13e11-331">The tracking events are emitted from a workflow at the workflow instance level and when activities within the workflow execute.</span></span> <span data-ttu-id="13e11-332">需要将工作流跟踪参与者添加到工作流主机中以订阅跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="13e11-332">A workflow tracking participant needs to be added to the workflow host to subscribe to tracking records.</span></span> <span data-ttu-id="13e11-333">使用跟踪配置文件筛选跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="13e11-333">The tracking records are filtered using a tracking profile.</span></span> <span data-ttu-id="13e11-334">.NET Framework 为 Windows) 跟踪参与者提供 ETW (事件跟踪，并在 machine.config 文件中安装基本配置文件。</span><span class="sxs-lookup"><span data-stu-id="13e11-334">The .NET Framework provides an ETW (Event Tracing for Windows) tracking participant, and a basic profile is installed in the machine.config file.</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-335">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-335">Getting Started</span></span>

1. <span data-ttu-id="13e11-336">在 Visual Studio 2010 中，创建 WCF 工作流服务应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="13e11-336">In Visual Studio 2010, create a WCF Workflow Service Application project.</span></span> <span data-ttu-id="13e11-337"><xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 对将置于画布上以开始操作。</span><span class="sxs-lookup"><span data-stu-id="13e11-337">A <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> pair will be placed on your canvas to start.</span></span>

2. <span data-ttu-id="13e11-338">打开 web.config 并添加一个无配置文件的 ETW 跟踪行为。</span><span class="sxs-lookup"><span data-stu-id="13e11-338">Open the web.config and add an ETW tracking behavior with no profile.</span></span>

    1. <span data-ttu-id="13e11-339">使用默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="13e11-339">The default profile is used.</span></span>

    2. <span data-ttu-id="13e11-340">打开事件查看器并在以下节点中启用分析通道： **事件查看器**、 **应用程序和服务日志**、 **Microsoft**、 **Windows**、 **应用程序服务器应用程序**。</span><span class="sxs-lookup"><span data-stu-id="13e11-340">Open event viewer and enable the analytic channel in the following node: **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="13e11-341">右键单击 " **分析** "，然后选择 " **启用日志**"。</span><span class="sxs-lookup"><span data-stu-id="13e11-341">Right-click **Analytic** and select **Enable Log**.</span></span>

    3. <span data-ttu-id="13e11-342">运行工作流服务。</span><span class="sxs-lookup"><span data-stu-id="13e11-342">Run the workflow service.</span></span>

    4. <span data-ttu-id="13e11-343">在事件查看器中观察工作流跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="13e11-343">Observe the workflow tracking events in event viewer.</span></span>

3. <span data-ttu-id="13e11-344">示例： [跟踪](./samples/tracking.md)</span><span class="sxs-lookup"><span data-stu-id="13e11-344">Samples: [Tracking](./samples/tracking.md)</span></span>

4. <span data-ttu-id="13e11-345">概念文档： [工作流跟踪和跟踪](workflow-tracking-and-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="13e11-345">Conceptual documentation: [Workflow Tracking and Tracing](workflow-tracking-and-tracing.md)</span></span>

## <a name="sql-workflow-instance-store"></a><span data-ttu-id="13e11-346">SQL 工作流实例存储</span><span class="sxs-lookup"><span data-stu-id="13e11-346">SQL Workflow Instance Store</span></span>

<span data-ttu-id="13e11-347"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 是实例存储的基于 SQL Server 的实现。</span><span class="sxs-lookup"><span data-stu-id="13e11-347">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> is a SQL Server-based implementation of an instance store.</span></span> <span data-ttu-id="13e11-348">实例存储将存储正在运行的实例的状态以及加载和恢复该实例所需的所有数据。</span><span class="sxs-lookup"><span data-stu-id="13e11-348">An instance store stores the state of a running instance together with all data necessary to load and resume that instance.</span></span> <span data-ttu-id="13e11-349">服务主机将在工作流仍存在时指示实例存储保存实例状态，并在该实例的消息到达或延迟活动过期时指示实例存储加载实例状态。</span><span class="sxs-lookup"><span data-stu-id="13e11-349">The service host instructs the instance store to save the instance state if the workflow persists, and it instructs the instance store to load the instance state when a message arrives for that instance or a delay activity expires.</span></span>

### <a name="getting-started"></a><span data-ttu-id="13e11-350">入门</span><span class="sxs-lookup"><span data-stu-id="13e11-350">Getting Started</span></span>

1. <span data-ttu-id="13e11-351">在 Visual Studio 2012 中，创建包含隐式或显式活动的工作流 <xref:System.Activities.Statements.Persist> 。</span><span class="sxs-lookup"><span data-stu-id="13e11-351">In Visual Studio 2012, create a Workflow that contains an implicit or explicit <xref:System.Activities.Statements.Persist> activity.</span></span> <span data-ttu-id="13e11-352">将 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 行为添加到工作流服务主机。</span><span class="sxs-lookup"><span data-stu-id="13e11-352">Add the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> behavior to your workflow service host.</span></span> <span data-ttu-id="13e11-353">这可以在代码或应用程序配置文件中完成。</span><span class="sxs-lookup"><span data-stu-id="13e11-353">This can be done in code or in the application configuration file.</span></span>

2. <span data-ttu-id="13e11-354">示例： [持久性](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="13e11-354">Samples: [Persistence](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))</span></span>

3. <span data-ttu-id="13e11-355">概念文档： [SQL 工作流实例存储区](sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="13e11-355">Conceptual documentation: [SQL Workflow Instance Store](sql-workflow-instance-store.md).</span></span>
