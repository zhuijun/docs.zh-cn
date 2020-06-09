---
title: 了解生成的客户端代码
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: f04b67ae13307fb3c2a2981204526880f55d58f1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595058"
---
# <a name="understanding-generated-client-code"></a><span data-ttu-id="af001-102">了解生成的客户端代码</span><span class="sxs-lookup"><span data-stu-id="af001-102">Understanding Generated Client Code</span></span>
<span data-ttu-id="af001-103">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 可生成用于生成客户端应用程序的客户端代码和客户端应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="af001-103">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) generates client code and a client application configuration file for use in building client applications.</span></span> <span data-ttu-id="af001-104">本主题提供了有关标准服务协定方案的生成代码示例的教程。</span><span class="sxs-lookup"><span data-stu-id="af001-104">This topic provides a tour of generated code examples for standard service contract scenarios.</span></span> <span data-ttu-id="af001-105">有关使用生成的代码生成客户端应用程序的详细信息，请参阅[WCF 客户端概述](../wcf-client-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="af001-105">For more information about building a client application using the generated code, see [WCF Client Overview](../wcf-client-overview.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="af001-106">概述</span><span class="sxs-lookup"><span data-stu-id="af001-106">Overview</span></span>  
 <span data-ttu-id="af001-107">如果使用 Visual Studio 生成项目的 Windows Communication Foundation （WCF）客户端类型，则通常不需要检查生成的客户端代码。</span><span class="sxs-lookup"><span data-stu-id="af001-107">If you use Visual Studio to generate Windows Communication Foundation (WCF) client types for your project, you typically do not need to examine the generated client code.</span></span> <span data-ttu-id="af001-108">如果您并未使用为您执行相同服务的开发环境，您可以使用 Svcutil.exe 之类的工具来生成客户端代码，然后使用该代码开发客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="af001-108">If you are not using a development environment that performs the same services for you, you can use a tool such as Svcutil.exe to generate client code and then use that code to develop your client application.</span></span>  
  
 <span data-ttu-id="af001-109">由于 Svcutil.exe 具有许多可以修改生成的类型信息的选项，因此本主题并不对所有方案进行讨论。</span><span class="sxs-lookup"><span data-stu-id="af001-109">Because Svcutil.exe has a number of options that modify the generated type information, this topic does not discuss all scenarios.</span></span> <span data-ttu-id="af001-110">但是，以下标准任务涉及查找生成的代码：</span><span class="sxs-lookup"><span data-stu-id="af001-110">However, the following standard tasks involve locating generated code:</span></span>  
  
- <span data-ttu-id="af001-111">标识服务协定接口。</span><span class="sxs-lookup"><span data-stu-id="af001-111">Identifying service contract interfaces.</span></span>  
  
- <span data-ttu-id="af001-112">标识 WCF 客户端类。</span><span class="sxs-lookup"><span data-stu-id="af001-112">Identifying the WCF client class.</span></span>  
  
- <span data-ttu-id="af001-113">标识数据类型。</span><span class="sxs-lookup"><span data-stu-id="af001-113">Identifying data types.</span></span>  
  
- <span data-ttu-id="af001-114">标识双工服务的回调协定。</span><span class="sxs-lookup"><span data-stu-id="af001-114">Identifying callback contracts for duplex services.</span></span>  
  
- <span data-ttu-id="af001-115">标识帮助器服务协定通道接口。</span><span class="sxs-lookup"><span data-stu-id="af001-115">Identifying the helper service contract channel interface.</span></span>  
  
### <a name="finding-service-contract-interfaces"></a><span data-ttu-id="af001-116">查找服务协定接口</span><span class="sxs-lookup"><span data-stu-id="af001-116">Finding Service Contract Interfaces</span></span>  
 <span data-ttu-id="af001-117">若要查找对服务协定建模的接口，请搜索使用 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 属性进行标记的接口。</span><span class="sxs-lookup"><span data-stu-id="af001-117">To locate the interfaces that model service contracts, search for interfaces that are marked with the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="af001-118">由于存在其他属性 (Attribute) 和设置在该属性 (Attribute) 自身上的显式属性 (Property)，因此要通过快速读取查找该属性 (Attribute) 通常并不容易。</span><span class="sxs-lookup"><span data-stu-id="af001-118">Often this attribute can be difficult to locate with a quick read due to the presence of other attributes and the explicit properties set on the attribute itself.</span></span> <span data-ttu-id="af001-119">请记住，服务协定接口和客户端协定接口属于两种不同的类型。</span><span class="sxs-lookup"><span data-stu-id="af001-119">Remember that the service contract interface and the client contract interface are two different types.</span></span> <span data-ttu-id="af001-120">下面的代码示例演示原始服务协定。</span><span class="sxs-lookup"><span data-stu-id="af001-120">The following code example shows the original service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 <span data-ttu-id="af001-121">下面的代码示例演示 Svcutil.exe 生成的相同服务协定。</span><span class="sxs-lookup"><span data-stu-id="af001-121">The following code example shows the same service contract as generated by Svcutil.exe.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 <span data-ttu-id="af001-122">您可以使用生成的服务协定接口和 <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> 类来创建 WCF 信道对象，以调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="af001-122">You can use the generated service contract interface along with the <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> class to create a WCF channel object with which to invoke service operations.</span></span> <span data-ttu-id="af001-123">有关详细信息，请参阅[如何：使用 ChannelFactory](how-to-use-the-channelfactory.md)。</span><span class="sxs-lookup"><span data-stu-id="af001-123">For more information, see [How to: Use the ChannelFactory](how-to-use-the-channelfactory.md).</span></span>  
  
### <a name="finding-wcf-client-classes"></a><span data-ttu-id="af001-124">查找 WCF 客户端类</span><span class="sxs-lookup"><span data-stu-id="af001-124">Finding WCF Client Classes</span></span>  
 <span data-ttu-id="af001-125">若要查找实现您要使用的服务协定的 WCF 客户端类，请搜索的扩展名 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> ，其中类型参数为您先前找到的、扩展该接口的服务协定接口。</span><span class="sxs-lookup"><span data-stu-id="af001-125">To locate the WCF client class that implements the service contract you want to use, search for an extension of <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, where the type parameter is the service contract interface that you previously located and that extends that interface.</span></span> <span data-ttu-id="af001-126">下面的代码示例演示类型为 <xref:System.ServiceModel.ClientBase%601> 的 `ISampleService`类。</span><span class="sxs-lookup"><span data-stu-id="af001-126">The following code example shows the <xref:System.ServiceModel.ClientBase%601> class of type `ISampleService`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 <span data-ttu-id="af001-127">可以通过创建新实例并调用它实现的方法来使用此 WCF 客户端类。</span><span class="sxs-lookup"><span data-stu-id="af001-127">You can use this WCF client class by creating a new instance of it and calling the methods it implements.</span></span> <span data-ttu-id="af001-128">这些方法调用服务操作，可设计和配置该服务操作以进行交互。</span><span class="sxs-lookup"><span data-stu-id="af001-128">Those methods invoke the service operation with which it is designed and configured to interact.</span></span> <span data-ttu-id="af001-129">有关详细信息，请参阅[WCF 客户端概述](../wcf-client-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="af001-129">For more information, see [WCF Client Overview](../wcf-client-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af001-130">SvcUtil.exe 在生成 WCF 客户端类时会将一个 <xref:System.Diagnostics.DebuggerStepThroughAttribute> 添加到该客户端类，以防止调试器逐步调试该 WCF 客户端类。</span><span class="sxs-lookup"><span data-stu-id="af001-130">When SvcUtil.exe generates a WCF client class, it adds a <xref:System.Diagnostics.DebuggerStepThroughAttribute> to the client class that prevents debuggers from stepping through the WCF client class.</span></span>  
  
### <a name="finding-data-types"></a><span data-ttu-id="af001-131">查找数据类型</span><span class="sxs-lookup"><span data-stu-id="af001-131">Finding Data Types</span></span>  
 <span data-ttu-id="af001-132">若要在生成的代码中查找数据类型，最简单的方法就是标识协定中指定的类型名称并搜索该类型声明的代码。</span><span class="sxs-lookup"><span data-stu-id="af001-132">To locate data types in the generated code, the most basic mechanism is to identify the type name specified in a contract and search the code for that type declaration.</span></span> <span data-ttu-id="af001-133">例如，下面的协定指定 `SampleMethod` 可以返回 `microsoft.wcf.documentation.SampleFault`类型的 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="af001-133">For example, the following contract specifies that the `SampleMethod` can return a SOAP fault of type `microsoft.wcf.documentation.SampleFault`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 <span data-ttu-id="af001-134">搜索 `SampleFault` 查找下面的类型声明。</span><span class="sxs-lookup"><span data-stu-id="af001-134">Searching for `SampleFault` locates the following type declaration.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 <span data-ttu-id="af001-135">在本示例中，数据类型为客户端上的特定异常（一个 <xref:System.ServiceModel.FaultException%601> ，其中详细信息类型为 `microsoft.wcf.documentation.SampleFault`）引发的详细信息类型。</span><span class="sxs-lookup"><span data-stu-id="af001-135">In this case the data type is the detail type thrown by a specific exception on the client, a <xref:System.ServiceModel.FaultException%601> where the detail type parameter is `microsoft.wcf.documentation.SampleFault`.</span></span> <span data-ttu-id="af001-136">有关数据类型的详细信息，请参阅[在服务协定中指定数据传输](specifying-data-transfer-in-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="af001-136">For more information about data types, see [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="af001-137">有关在客户端中处理异常的详细信息，请参阅[发送和接收错误](../sending-and-receiving-faults.md)。</span><span class="sxs-lookup"><span data-stu-id="af001-137">For more information about handling exceptions in clients, see [Sending and Receiving Faults](../sending-and-receiving-faults.md).</span></span>  
  
### <a name="finding-callback-contracts-for-duplex-services"></a><span data-ttu-id="af001-138">查找双工服务的回调协定</span><span class="sxs-lookup"><span data-stu-id="af001-138">Finding Callback Contracts for Duplex Services</span></span>  
 <span data-ttu-id="af001-139">如果要查找协定接口为其 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> 属性指定一个值的服务协定，则该协定指定一个双工协定。</span><span class="sxs-lookup"><span data-stu-id="af001-139">If you locate a service contract for which the contract interface specifies a value for the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property, then that contract specifies a duplex contract.</span></span> <span data-ttu-id="af001-140">双工协定要求客户端应用程序创建一个回调类，该类实现回调协定并将此类的一个实例传递给 <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> 或用来与服务进行通信的 <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="af001-140">Duplex contracts require the client application to create a callback class that implements the callback contract and pass an instance of that class to the <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> or <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> used to communicate with the service.</span></span> <span data-ttu-id="af001-141">有关双工客户端的详细信息，请参阅[如何：使用双工协定访问服务](how-to-access-services-with-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="af001-141">For more information about duplex clients, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="af001-142">下面的协定指定一个 `SampleDuplexHelloCallback`类型的回调协定。</span><span class="sxs-lookup"><span data-stu-id="af001-142">The following contract specifies a callback contract of type `SampleDuplexHelloCallback`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 <span data-ttu-id="af001-143">搜索该回调协定定位下面的接口，客户端应用程序必须实现该接口。</span><span class="sxs-lookup"><span data-stu-id="af001-143">Searching for that callback contract locates the following interface that the client application must implement.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a><span data-ttu-id="af001-144">查找服务协定通道接口</span><span class="sxs-lookup"><span data-stu-id="af001-144">Finding Service Contract Channel Interfaces</span></span>  
 <span data-ttu-id="af001-145">当 <xref:System.ServiceModel.ChannelFactory> 类与服务协定接口一起使用时，您必须强制转换到 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> 接口以显式打开、关闭或中止通道。</span><span class="sxs-lookup"><span data-stu-id="af001-145">When using the <xref:System.ServiceModel.ChannelFactory> class with a service contract interface, you must cast to the <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface to explicitly open, close, or abort the channel.</span></span> <span data-ttu-id="af001-146">为便于操作，Svcutil.exe 工具还生成一个帮助器接口，该接口可同时实现服务协定接口和 <xref:System.ServiceModel.IClientChannel> ，以使您无需进行强制转换就能够与客户端通道基础结构进行交互。</span><span class="sxs-lookup"><span data-stu-id="af001-146">To make it easier to work with, the Svcutil.exe tool also generates a helper interface that implements both the service contract interface and <xref:System.ServiceModel.IClientChannel> to enable you to interact with the client channel infrastructure without having to cast.</span></span> <span data-ttu-id="af001-147">下面的代码演示实现上述服务协定的帮助器客户端通道的定义。</span><span class="sxs-lookup"><span data-stu-id="af001-147">The following code shows the definition of a helper client channel that implements the preceding service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="af001-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af001-148">See also</span></span>

- [<span data-ttu-id="af001-149">WCF 客户端概述</span><span class="sxs-lookup"><span data-stu-id="af001-149">WCF Client Overview</span></span>](../wcf-client-overview.md)
