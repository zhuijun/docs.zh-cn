---
title: 如何：创建安全会话
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 80973a31050cf1ede03d4a3919066c62625ae590
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593407"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="8682c-102">如何：创建安全会话</span><span class="sxs-lookup"><span data-stu-id="8682c-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="8682c-103">除了 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) 绑定，当启用消息安全时，Windows Communication Foundation （WCF）中系统提供的绑定会自动使用安全会话。</span><span class="sxs-lookup"><span data-stu-id="8682c-103">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="8682c-104">默认情况下，安全会话不会在已回收的 Web 服务器中存在。</span><span class="sxs-lookup"><span data-stu-id="8682c-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="8682c-105">建立安全会话时，客户端和服务将缓存与安全会话关联的密钥。</span><span class="sxs-lookup"><span data-stu-id="8682c-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="8682c-106">交换消息时，只交换已缓存密钥的标识符。</span><span class="sxs-lookup"><span data-stu-id="8682c-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="8682c-107">如果回收了 Web 服务器，则也会回收缓存，因此 Web 服务器将无法检索该标识符的已缓存密钥。</span><span class="sxs-lookup"><span data-stu-id="8682c-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="8682c-108">如果发生这种情况，将会引发异常并返回至客户端。</span><span class="sxs-lookup"><span data-stu-id="8682c-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="8682c-109">使用有状态安全上下文令牌 (SCT) 的安全会话可以在回收 Web 服务器后存在。</span><span class="sxs-lookup"><span data-stu-id="8682c-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="8682c-110">有关在安全会话中使用有状态 SCT 的详细信息，请参阅[如何：为安全会话创建安全上下文令牌](how-to-create-a-security-context-token-for-a-secure-session.md)。</span><span class="sxs-lookup"><span data-stu-id="8682c-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="8682c-111">通过使用系统提供的一个绑定指定服务使用安全会话</span><span class="sxs-lookup"><span data-stu-id="8682c-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
- <span data-ttu-id="8682c-112">配置服务以使用支持消息安全的系统提供的绑定。</span><span class="sxs-lookup"><span data-stu-id="8682c-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="8682c-113">除 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) 绑定外，当系统提供的绑定配置为使用消息安全性时，WCF 将自动使用安全会话。</span><span class="sxs-lookup"><span data-stu-id="8682c-113">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="8682c-114">下表列出了支持消息安全的系统提供的绑定以及消息安全是否是默认的安全机制。</span><span class="sxs-lookup"><span data-stu-id="8682c-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="8682c-115">系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="8682c-115">System-provided binding</span></span>|<span data-ttu-id="8682c-116">配置元素</span><span class="sxs-lookup"><span data-stu-id="8682c-116">Configuration element</span></span>|<span data-ttu-id="8682c-117">默认情况下是否启用消息安全</span><span class="sxs-lookup"><span data-stu-id="8682c-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="8682c-118">否</span><span class="sxs-lookup"><span data-stu-id="8682c-118">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="8682c-119">是</span><span class="sxs-lookup"><span data-stu-id="8682c-119">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="8682c-120">是</span><span class="sxs-lookup"><span data-stu-id="8682c-120">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="8682c-121">是</span><span class="sxs-lookup"><span data-stu-id="8682c-121">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="8682c-122">No</span><span class="sxs-lookup"><span data-stu-id="8682c-122">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="8682c-123">否</span><span class="sxs-lookup"><span data-stu-id="8682c-123">No</span></span>|  
  
     <span data-ttu-id="8682c-124">下面的代码示例使用配置来指定一个名为 `wsHttpBinding_Calculator` 的绑定，该绑定使用 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 、消息安全和安全会话。</span><span class="sxs-lookup"><span data-stu-id="8682c-124">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="8682c-125">下面的代码示例指定 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 使用、消息安全和安全会话来保护 `secureCalculator` 服务。</span><span class="sxs-lookup"><span data-stu-id="8682c-125">The following code example specifies that the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="8682c-126">可以 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 通过将属性设置为来关闭安全会话 `establishSecurityContext` `false` 。</span><span class="sxs-lookup"><span data-stu-id="8682c-126">Secure sessions can be turned off for the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="8682c-127">对于其他系统提供的绑定，只能通过创建自定义绑定来关闭安全会话。</span><span class="sxs-lookup"><span data-stu-id="8682c-127">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="8682c-128">通过使用自定义绑定来指定服务使用安全会话</span><span class="sxs-lookup"><span data-stu-id="8682c-128">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
- <span data-ttu-id="8682c-129">创建一个自定义绑定，该绑定指定由安全会话保护 SOAP 消息。</span><span class="sxs-lookup"><span data-stu-id="8682c-129">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="8682c-130">有关创建自定义绑定的详细信息，请参阅[如何：自定义系统提供的绑定](../extending/how-to-customize-a-system-provided-binding.md)。</span><span class="sxs-lookup"><span data-stu-id="8682c-130">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="8682c-131">下面的代码示例使用配置来指定使用安全会话的消息的自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="8682c-131">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="8682c-132">下面的代码示例创建一个自定义绑定，该绑定使用 <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> 身份验证模式启动安全会话。</span><span class="sxs-lookup"><span data-stu-id="8682c-132">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8682c-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8682c-133">See also</span></span>

- [<span data-ttu-id="8682c-134">WCF 绑定概述</span><span class="sxs-lookup"><span data-stu-id="8682c-134">WCF Bindings Overview</span></span>](../bindings-overview.md)
