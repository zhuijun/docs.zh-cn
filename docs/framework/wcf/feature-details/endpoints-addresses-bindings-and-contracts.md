---
title: 终结点：地址、绑定和协定
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3ac7f0b165b99a1ed3702628958f7d4c7702f5b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593511"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="87377-102">终结点：地址、绑定和协定</span><span class="sxs-lookup"><span data-stu-id="87377-102">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="87377-103">与 Windows Communication Foundation （WCF）服务的所有通信都通过服务*终结点*进行。</span><span class="sxs-lookup"><span data-stu-id="87377-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="87377-104">终结点为客户端提供对 WCF 服务所提供的功能的访问权限。</span><span class="sxs-lookup"><span data-stu-id="87377-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="87377-105">每个终结点包含四个属性：</span><span class="sxs-lookup"><span data-stu-id="87377-105">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="87377-106">一个指示可以查找终结点的位置的地址。</span><span class="sxs-lookup"><span data-stu-id="87377-106">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="87377-107">一个指定客户端如何与终结点进行通信的绑定。</span><span class="sxs-lookup"><span data-stu-id="87377-107">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="87377-108">一个标识可用操作的协定。</span><span class="sxs-lookup"><span data-stu-id="87377-108">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="87377-109">一组指定终结点的本地实现细节的行为。</span><span class="sxs-lookup"><span data-stu-id="87377-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="87377-110">本主题讨论此终结点结构，并说明它在 WCF 对象模型中的表示方式。</span><span class="sxs-lookup"><span data-stu-id="87377-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="87377-111">终结点的结构</span><span class="sxs-lookup"><span data-stu-id="87377-111">The Structure of an Endpoint</span></span>

<span data-ttu-id="87377-112">每个终结点由以下内容组成：</span><span class="sxs-lookup"><span data-stu-id="87377-112">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="87377-113">地址：地址唯一地标识终结点，并告诉服务的潜在客户其所在的位置。</span><span class="sxs-lookup"><span data-stu-id="87377-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="87377-114">它在 WCF 对象模型中由 <xref:System.ServiceModel.EndpointAddress> 类表示。</span><span class="sxs-lookup"><span data-stu-id="87377-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="87377-115">一个 <xref:System.ServiceModel.EndpointAddress> 类包含：</span><span class="sxs-lookup"><span data-stu-id="87377-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="87377-116">一个表示服务地址的 <xref:System.ServiceModel.EndpointAddress.Uri%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="87377-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="87377-117">一个表示服务安全标识和可选消息头集合的 <xref:System.ServiceModel.EndpointAddress.Identity%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="87377-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="87377-118">可选消息头用于提供其他更多详细寻址信息来标识终结点或与终结点交互。</span><span class="sxs-lookup"><span data-stu-id="87377-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="87377-119">有关详细信息，请参阅[指定终结点地址](../specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="87377-119">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="87377-120">绑定：绑定指定如何与终结点进行通信。</span><span class="sxs-lookup"><span data-stu-id="87377-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="87377-121">这包括：</span><span class="sxs-lookup"><span data-stu-id="87377-121">This includes:</span></span>

  - <span data-ttu-id="87377-122">要使用的传输协议（例如，TCP 或 HTTP）。</span><span class="sxs-lookup"><span data-stu-id="87377-122">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="87377-123">要用于消息的编码（例如，文本或二进制）。</span><span class="sxs-lookup"><span data-stu-id="87377-123">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="87377-124">必需的安全要求（例如，SSL 或 SOAP 消息安全）。</span><span class="sxs-lookup"><span data-stu-id="87377-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="87377-125">有关详细信息，请参阅[WCF 绑定概述](../bindings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="87377-125">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="87377-126">绑定由抽象基类在 WCF 对象模型中表示 <xref:System.ServiceModel.Channels.Binding> 。</span><span class="sxs-lookup"><span data-stu-id="87377-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="87377-127">大多数情况下，用户可以使用系统提供的绑定之一。</span><span class="sxs-lookup"><span data-stu-id="87377-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="87377-128">有关详细信息，请参阅[系统提供的绑定](../system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="87377-128">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="87377-129">协定：协定概述了终结点向客户端公开的功能。</span><span class="sxs-lookup"><span data-stu-id="87377-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="87377-130">协定指定：</span><span class="sxs-lookup"><span data-stu-id="87377-130">A contract specifies:</span></span>

  - <span data-ttu-id="87377-131">客户端可以调用的操作。</span><span class="sxs-lookup"><span data-stu-id="87377-131">What operations can be called by a client.</span></span>

  - <span data-ttu-id="87377-132">消息的窗体。</span><span class="sxs-lookup"><span data-stu-id="87377-132">The form of the message.</span></span>

  - <span data-ttu-id="87377-133">调用操作所需的输入参数或数据的类型。</span><span class="sxs-lookup"><span data-stu-id="87377-133">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="87377-134">客户端可以预期的处理或响应消息的类型。</span><span class="sxs-lookup"><span data-stu-id="87377-134">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="87377-135">有关定义协定的详细信息，请参阅[设计服务协定](../designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="87377-135">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="87377-136">行为：可以使用终结点行为来自定义服务终结点的本地行为。</span><span class="sxs-lookup"><span data-stu-id="87377-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="87377-137">终结点行为是通过参与生成 WCF 运行时的过程来实现的。</span><span class="sxs-lookup"><span data-stu-id="87377-137">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="87377-138">终结点行为的一个示例是 <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> 属性，可以利用该属性指定与 SOAP 或 Web 服务描述语言 (WSDL) 地址不同的侦听地址。</span><span class="sxs-lookup"><span data-stu-id="87377-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="87377-139">有关详细信息，请参阅[ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md)。</span><span class="sxs-lookup"><span data-stu-id="87377-139">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="87377-140">定义终结点</span><span class="sxs-lookup"><span data-stu-id="87377-140">Defining Endpoints</span></span>

<span data-ttu-id="87377-141">可以通过使用代码以强制方式或通过配置以声明方式指定服务的终结点。</span><span class="sxs-lookup"><span data-stu-id="87377-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="87377-142">有关详细信息，请参阅[如何：在配置中创建服务终结点](how-to-create-a-service-endpoint-in-configuration.md)和[如何：在代码中创建服务终结点](how-to-create-a-service-endpoint-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="87377-142">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="87377-143">本节内容</span><span class="sxs-lookup"><span data-stu-id="87377-143">In This Section</span></span>

<span data-ttu-id="87377-144">本节说明了绑定、终结点和地址的用途，演示了如何配置绑定和终结点，并演示了如何使用 `ClientVia` 行为和 `ListenUri` 属性。</span><span class="sxs-lookup"><span data-stu-id="87377-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="87377-145">[地址](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="87377-145">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="87377-146">介绍如何在 WCF 中对终结点寻址。</span><span class="sxs-lookup"><span data-stu-id="87377-146">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="87377-147">[绑定](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="87377-147">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="87377-148">描述如何使用绑定指定客户端与服务相互通信所需的传输、编码和协议详细信息。</span><span class="sxs-lookup"><span data-stu-id="87377-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="87377-149">[签订](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="87377-149">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="87377-150">描述协定如何定义服务的方法。</span><span class="sxs-lookup"><span data-stu-id="87377-150">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="87377-151">[如何：在配置中创建服务终结点](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="87377-151">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="87377-152">描述如何在配置中创建服务终结点。</span><span class="sxs-lookup"><span data-stu-id="87377-152">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="87377-153">[如何：在代码中创建服务终结点](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="87377-153">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="87377-154">描述如何在代码中创建服务终结点。</span><span class="sxs-lookup"><span data-stu-id="87377-154">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="87377-155">[如何：使用 Svcutil.exe 验证已编译的服务代码](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="87377-155">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="87377-156">介绍如何在不使用配置的[元数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)托管服务的情况下检测服务实现和配置中的错误。</span><span class="sxs-lookup"><span data-stu-id="87377-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87377-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87377-157">See also</span></span>

- [<span data-ttu-id="87377-158">正在配置服务</span><span class="sxs-lookup"><span data-stu-id="87377-158">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="87377-159">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="87377-159">Extending Bindings</span></span>](../extending/extending-bindings.md)
