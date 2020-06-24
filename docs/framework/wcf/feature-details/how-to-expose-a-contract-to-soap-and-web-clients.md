---
title: 如何：向 SOAP 和 Web 客户端公开协定
description: 了解如何使 WFC 服务器终结点可用于 SOAP 和非 SOAP 客户端。 默认情况下，终结点仅可用于 SOAP 客户端。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: b1bdb7af51e0e2795c36865058fbeb34a716e3e2
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246969"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="37bdc-104">如何：向 SOAP 和 Web 客户端公开协定</span><span class="sxs-lookup"><span data-stu-id="37bdc-104">How to: Expose a Contract to SOAP and Web Clients</span></span>

<span data-ttu-id="37bdc-105">默认情况下，Windows Communication Foundation （WCF）使终结点仅可用于 SOAP 客户端。</span><span class="sxs-lookup"><span data-stu-id="37bdc-105">By default, Windows Communication Foundation (WCF) makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="37bdc-106">[如何：创建基本 WCF WEB HTTP 服务](how-to-create-a-basic-wcf-web-http-service.md)，终结点可供非 SOAP 客户端使用。</span><span class="sxs-lookup"><span data-stu-id="37bdc-106">In [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="37bdc-107">有时可能需要使相同的协定可以同时作为 Web 终结点和 SOAP 终结点使用。</span><span class="sxs-lookup"><span data-stu-id="37bdc-107">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="37bdc-108">本主题演示了如何实现此目的的示例。</span><span class="sxs-lookup"><span data-stu-id="37bdc-108">This topic shows an example of how to do this.</span></span>

## <a name="to-define-the-service-contract"></a><span data-ttu-id="37bdc-109">定义服务协定</span><span class="sxs-lookup"><span data-stu-id="37bdc-109">To define the service contract</span></span>

1. <span data-ttu-id="37bdc-110">使用用标记的接口和特性定义服务协定 <xref:System.ServiceModel.ServiceContractAttribute> ， <xref:System.ServiceModel.Web.WebInvokeAttribute> <xref:System.ServiceModel.Web.WebGetAttribute> 如下面的代码所示：</span><span class="sxs-lookup"><span data-stu-id="37bdc-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code:</span></span>

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="37bdc-111">默认情况下，<xref:System.ServiceModel.Web.WebInvokeAttribute> 将 POST 调用映射到操作。</span><span class="sxs-lookup"><span data-stu-id="37bdc-111">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="37bdc-112">但是，可以通过指定“method=”参数指定要映射到操作的方法。</span><span class="sxs-lookup"><span data-stu-id="37bdc-112">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="37bdc-113"><xref:System.ServiceModel.Web.WebGetAttribute> 不具有“method=”参数，仅将 GET 调用映射到服务操作。</span><span class="sxs-lookup"><span data-stu-id="37bdc-113"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="37bdc-114">实现服务协定，如下面的代码所示：</span><span class="sxs-lookup"><span data-stu-id="37bdc-114">Implement the service contract, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="37bdc-115">承载服务</span><span class="sxs-lookup"><span data-stu-id="37bdc-115">To host the service</span></span>

1. <span data-ttu-id="37bdc-116">创建一个 <xref:System.ServiceModel.ServiceHost> 对象，如下面的代码所示：</span><span class="sxs-lookup"><span data-stu-id="37bdc-116">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. <span data-ttu-id="37bdc-117">为 <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.BasicHttpBinding> SOAP 终结点添加一个，如下面的代码所示：</span><span class="sxs-lookup"><span data-stu-id="37bdc-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. <span data-ttu-id="37bdc-118">为 <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.WebHttpBinding> 非 SOAP 终结点添加，并将添加 <xref:System.ServiceModel.Description.WebHttpBehavior> 到终结点，如下面的代码所示：</span><span class="sxs-lookup"><span data-stu-id="37bdc-118">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. <span data-ttu-id="37bdc-119">对 `Open()` 实例调用 <xref:System.ServiceModel.ServiceHost> 以打开服务主机，如下面的代码所示：</span><span class="sxs-lookup"><span data-stu-id="37bdc-119">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="37bdc-120">在 Internet Explorer 中调用映射到 GET 的服务操作</span><span class="sxs-lookup"><span data-stu-id="37bdc-120">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="37bdc-121">打开 Internet Explorer 并键入 " `http://localhost:8000/Web/EchoWithGet?s=Hello, world!` "，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="37bdc-121">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="37bdc-122">URL 包含服务的基址（ `http://localhost:8000/` ）、终结点的相对地址（""）、要调用的服务操作（"EchoWithGet"）和一个问号，后跟一个用 "and" 符分隔的命名参数列表（&）。</span><span class="sxs-lookup"><span data-stu-id="37bdc-122">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="37bdc-123">使用代码在 Web 终结点上调用服务操作</span><span class="sxs-lookup"><span data-stu-id="37bdc-123">To call service operations on the Web endpoint in code</span></span>

1. <span data-ttu-id="37bdc-124">在 <xref:System.ServiceModel.Web.WebChannelFactory%601> 块中创建 `using` 的实例，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="37bdc-124">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> <span data-ttu-id="37bdc-125">将自动在 `Close()` 块末尾处的通道上调用 `using`。</span><span class="sxs-lookup"><span data-stu-id="37bdc-125">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>

1. <span data-ttu-id="37bdc-126">创建通道并调用服务，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="37bdc-126">Create the channel and call the service, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="37bdc-127">在 SOAP 终结点上调用服务操作</span><span class="sxs-lookup"><span data-stu-id="37bdc-127">To call service operations on the SOAP endpoint</span></span>

1. <span data-ttu-id="37bdc-128">在 <xref:System.ServiceModel.ChannelFactory> 块中创建 `using` 的实例，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="37bdc-128">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. <span data-ttu-id="37bdc-129">创建通道并调用服务，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="37bdc-129">Create the channel and call the service, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a><span data-ttu-id="37bdc-130">关闭服务主机</span><span class="sxs-lookup"><span data-stu-id="37bdc-130">To close the service host</span></span>

1. <span data-ttu-id="37bdc-131">关闭服务主机，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="37bdc-131">Close the service host, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a><span data-ttu-id="37bdc-132">示例</span><span class="sxs-lookup"><span data-stu-id="37bdc-132">Example</span></span>

<span data-ttu-id="37bdc-133">下面是此主题的完整代码列表：</span><span class="sxs-lookup"><span data-stu-id="37bdc-133">The following is the full code listing for this topic:</span></span>

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a><span data-ttu-id="37bdc-134">编译代码</span><span class="sxs-lookup"><span data-stu-id="37bdc-134">Compiling the code</span></span>

 <span data-ttu-id="37bdc-135">编译 Service.cs 时，请参考 System.ServiceModel.dll 和 System.ServiceModel.Web.dll。</span><span class="sxs-lookup"><span data-stu-id="37bdc-135">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="37bdc-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="37bdc-136">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="37bdc-137">WCF Web HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="37bdc-137">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
