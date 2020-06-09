---
title: WCF 安全编程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 2b3c96e91c0d6f01fa30b3b617449e7d4a148933
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596768"
---
# <a name="programming-wcf-security"></a><span data-ttu-id="233fe-102">WCF 安全编程</span><span class="sxs-lookup"><span data-stu-id="233fe-102">Programming WCF Security</span></span>
<span data-ttu-id="233fe-103">本主题介绍用于创建安全 Windows Communication Foundation （WCF）应用程序的基本编程任务。</span><span class="sxs-lookup"><span data-stu-id="233fe-103">This topic describes the fundamental programming tasks used to create a secure Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="233fe-104">本主题仅介绍身份验证、机密性和完整性，共同称为*传输安全性*。</span><span class="sxs-lookup"><span data-stu-id="233fe-104">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="233fe-105">本主题不涉及授权（控制对资源或服务的访问权限）;有关授权的信息，请参阅[授权](authorization-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="233fe-105">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="233fe-106">有关安全概念的重要介绍（特别是在 WCF 方面），请参阅 MSDN 上的模式和实践教程集，以了解[Web 服务增强（WSE）3.0 的方案、模式和实现指南](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="233fe-106">For a valuable introduction to security concepts, especially in regard to WCF, see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="233fe-107">WCF 安全编程基于三个步骤设置：安全模式、客户端凭据类型和凭据值。</span><span class="sxs-lookup"><span data-stu-id="233fe-107">Programming WCF security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="233fe-108">可以通过代码或配置执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="233fe-108">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="233fe-109">设置安全模式</span><span class="sxs-lookup"><span data-stu-id="233fe-109">Setting the Security Mode</span></span>  
 <span data-ttu-id="233fe-110">下面说明了在 WCF 中用安全模式编程的一般步骤：</span><span class="sxs-lookup"><span data-stu-id="233fe-110">The following explains the general steps for programming with the security mode in WCF:</span></span>  
  
1. <span data-ttu-id="233fe-111">选择一个适合于应用程序要求的预定义绑定。</span><span class="sxs-lookup"><span data-stu-id="233fe-111">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="233fe-112">有关绑定选项的列表，请参阅[系统提供的绑定](../system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="233fe-112">For a list of the binding choices, see [System-Provided Bindings](../system-provided-bindings.md).</span></span> <span data-ttu-id="233fe-113">默认情况下，几乎每个绑定都启用了安全。</span><span class="sxs-lookup"><span data-stu-id="233fe-113">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="233fe-114">一个例外是 <xref:System.ServiceModel.BasicHttpBinding> 类（使用配置， [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ）。</span><span class="sxs-lookup"><span data-stu-id="233fe-114">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="233fe-115">所选的绑定确定了传输协议。</span><span class="sxs-lookup"><span data-stu-id="233fe-115">The binding you select determines the transport.</span></span> <span data-ttu-id="233fe-116">例如，<xref:System.ServiceModel.WSHttpBinding> 使用 HTTP 传输协议；而 <xref:System.ServiceModel.NetTcpBinding> 使用 TCP 传输协议。</span><span class="sxs-lookup"><span data-stu-id="233fe-116">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2. <span data-ttu-id="233fe-117">为绑定选择一个安全模式。</span><span class="sxs-lookup"><span data-stu-id="233fe-117">Select one of the security modes for the binding.</span></span> <span data-ttu-id="233fe-118">请注意，所选的绑定确定了可以进行的模式选择。</span><span class="sxs-lookup"><span data-stu-id="233fe-118">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="233fe-119">例如，<xref:System.ServiceModel.WSDualHttpBinding> 不允许启用传输安全（它不是选项）。</span><span class="sxs-lookup"><span data-stu-id="233fe-119">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="233fe-120">同样，<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 和 <xref:System.ServiceModel.NetNamedPipeBinding> 都不允许启用消息安全。</span><span class="sxs-lookup"><span data-stu-id="233fe-120">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="233fe-121">您有三个选择：</span><span class="sxs-lookup"><span data-stu-id="233fe-121">You have three choices:</span></span>  
  
    1. `Transport`  
  
         <span data-ttu-id="233fe-122">传输安全取决于所选绑定使用的机制。</span><span class="sxs-lookup"><span data-stu-id="233fe-122">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="233fe-123">例如，如果要使用 `WSHttpBinding`，则安全机制是安全套接字层 (SSL)（它也是 HTTPS 协议的机制）。</span><span class="sxs-lookup"><span data-stu-id="233fe-123">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="233fe-124">一般说来，传输安全的主要优点是它提供了较高的吞吐量，而无论您使用哪种传输协议。</span><span class="sxs-lookup"><span data-stu-id="233fe-124">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="233fe-125">但是，它确实具有两个限制：第一个限制是传输机制指示了用于对用户进行身份验证的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="233fe-125">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="233fe-126">只有当服务需要与其他要求不同类型凭据的服务交互操作时，这才是一个缺点。</span><span class="sxs-lookup"><span data-stu-id="233fe-126">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="233fe-127">第二个限制是，因为安全不是在消息级应用的，所以安全是逐个跃点实现的，而不是以端对端方式实现的。</span><span class="sxs-lookup"><span data-stu-id="233fe-127">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="233fe-128">只有当客户端和服务之间的消息路径包含中介时，后一个限制才会成为问题。</span><span class="sxs-lookup"><span data-stu-id="233fe-128">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> <span data-ttu-id="233fe-129">有关使用哪种传输的详细信息，请参阅[选择传输](choosing-a-transport.md)。</span><span class="sxs-lookup"><span data-stu-id="233fe-129">For more information about which transport to use, see [Choosing a Transport](choosing-a-transport.md).</span></span> <span data-ttu-id="233fe-130">有关使用传输安全的详细信息，请参阅[传输安全概述](transport-security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="233fe-130">For more information about using transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>  
  
    2. `Message`  
  
         <span data-ttu-id="233fe-131">消息安全意味着每个消息都包含必要的标头和数据，以保证消息的安全。</span><span class="sxs-lookup"><span data-stu-id="233fe-131">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="233fe-132">因为标头的组成千变万化，所以可以包含任意数量的凭据。</span><span class="sxs-lookup"><span data-stu-id="233fe-132">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="233fe-133">如果您要与其他要求传输机制无法提供的特定凭据类型的服务交互操作，或者如果必须将消息用于多个服务（其中每个服务都要求不同的凭据类型），那么这会是一个有用的办法。</span><span class="sxs-lookup"><span data-stu-id="233fe-133">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         <span data-ttu-id="233fe-134">有关详细信息，请参阅[消息安全](message-security-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="233fe-134">For more information, see [Message Security](message-security-in-wcf.md).</span></span>  
  
    3. `TransportWithMessageCredential`  
  
         <span data-ttu-id="233fe-135">此选择使用传输层来保证消息传输的安全，同时每个消息都包含其他服务需要的丰富凭据。</span><span class="sxs-lookup"><span data-stu-id="233fe-135">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="233fe-136">这便将传输安全的性能优点与消息安全的丰富凭据优点结合起来。</span><span class="sxs-lookup"><span data-stu-id="233fe-136">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="233fe-137">使用下列绑定可实现这一点：<xref:System.ServiceModel.BasicHttpBinding>、<xref:System.ServiceModel.WSFederationHttpBinding>、<xref:System.ServiceModel.NetPeerTcpBinding> 和 <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="233fe-137">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3. <span data-ttu-id="233fe-138">如果决定对 HTTP 使用传输安全（即 HTTPS），还必须用 SSL 证书配置主机并且在端口上启用 SSL。</span><span class="sxs-lookup"><span data-stu-id="233fe-138">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> <span data-ttu-id="233fe-139">有关详细信息，请参阅[HTTP 传输安全](http-transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="233fe-139">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
4. <span data-ttu-id="233fe-140">如果您要使用 <xref:System.ServiceModel.WSHttpBinding> 并且不需要建立安全会话，请将 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> 属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="233fe-140">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="233fe-141">当客户端和服务使用对称密钥创建通道时（客户端和服务器在整个对话过程中都使用相同的密钥，直到对话结束），将发生安全会话。</span><span class="sxs-lookup"><span data-stu-id="233fe-141">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="233fe-142">设置客户端凭据类型</span><span class="sxs-lookup"><span data-stu-id="233fe-142">Setting the Client Credential Type</span></span>  
 <span data-ttu-id="233fe-143">选择适当的客户端凭据类型。</span><span class="sxs-lookup"><span data-stu-id="233fe-143">Select a client credential type as appropriate.</span></span> <span data-ttu-id="233fe-144">有关详细信息，请参阅[选择凭据类型](selecting-a-credential-type.md)。</span><span class="sxs-lookup"><span data-stu-id="233fe-144">For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).</span></span> <span data-ttu-id="233fe-145">下列客户端凭据类型可用：</span><span class="sxs-lookup"><span data-stu-id="233fe-145">The following client credential types are available:</span></span>  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 <span data-ttu-id="233fe-146">根据您设置模式的方式的不同，必须设置凭据类型。</span><span class="sxs-lookup"><span data-stu-id="233fe-146">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="233fe-147">例如，如果您已经选择了 `wsHttpBinding`，并且将模式设置为“Message”，则还可以将 Message 元素的 `clientCredentialType` 属性设置为下列值之一：`None`、`Windows`、`UserName`、`Certificate` 和 `IssuedToken`，如下面的配置示例所示。</span><span class="sxs-lookup"><span data-stu-id="233fe-147">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="233fe-148">或者在代码中：</span><span class="sxs-lookup"><span data-stu-id="233fe-148">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="233fe-149">设置服务凭据值</span><span class="sxs-lookup"><span data-stu-id="233fe-149">Setting Service Credential Values</span></span>  
 <span data-ttu-id="233fe-150">一旦选择了客户端凭据类型，就必须设置可供服务和客户端使用的实际凭据。</span><span class="sxs-lookup"><span data-stu-id="233fe-150">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="233fe-151">在服务上，使用 <xref:System.ServiceModel.Description.ServiceCredentials> 类设置凭据，并且由 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 类的 <xref:System.ServiceModel.ServiceHostBase> 属性返回。</span><span class="sxs-lookup"><span data-stu-id="233fe-151">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="233fe-152">所使用的绑定暗示了服务凭据类型、选择的安全模式和客户端凭据类型。</span><span class="sxs-lookup"><span data-stu-id="233fe-152">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="233fe-153">下面的代码为服务凭据设置了证书。</span><span class="sxs-lookup"><span data-stu-id="233fe-153">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="233fe-154">设置客户端凭据值</span><span class="sxs-lookup"><span data-stu-id="233fe-154">Setting Client Credential Values</span></span>  
 <span data-ttu-id="233fe-155">在客户端上，使用 <xref:System.ServiceModel.Description.ClientCredentials> 类设置客户端凭据值，并且通过 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 类的 <xref:System.ServiceModel.ClientBase%601> 属性返回该值。</span><span class="sxs-lookup"><span data-stu-id="233fe-155">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="233fe-156">下面的代码在使用 TCP 协议的客户端上将证书设置为凭据。</span><span class="sxs-lookup"><span data-stu-id="233fe-156">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="233fe-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="233fe-157">See also</span></span>

- [<span data-ttu-id="233fe-158">基本 WCF 编程</span><span class="sxs-lookup"><span data-stu-id="233fe-158">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- [<span data-ttu-id="233fe-159">常用安全方案</span><span class="sxs-lookup"><span data-stu-id="233fe-159">Common Security Scenarios</span></span>](common-security-scenarios.md)
