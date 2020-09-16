---
title: 使用相互证书的消息安全
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: bbe99b133e7edda191d17e9fe8a1dea89d3f0eb7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556520"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="70f16-102">使用相互证书的消息安全</span><span class="sxs-lookup"><span data-stu-id="70f16-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="70f16-103">下面的方案演示使用消息安全模式 Windows Communication Foundation (WCF) 服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="70f16-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="70f16-104">使用证书对客户端和服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="70f16-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="70f16-105">本方案是可互操作的，因为它使用具有 X.509 证书令牌配置文件的 WS-Security。</span><span class="sxs-lookup"><span data-stu-id="70f16-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70f16-106">本方案不对服务证书执行协商。</span><span class="sxs-lookup"><span data-stu-id="70f16-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="70f16-107">在进行任何通信之前，必须先向客户端提供服务证书。</span><span class="sxs-lookup"><span data-stu-id="70f16-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="70f16-108">服务器证书可以随应用程序一起分发，也可以通过带外通信来提供。</span><span class="sxs-lookup"><span data-stu-id="70f16-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="70f16-109">![具有相互证书的消息安全](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="70f16-109">![Message security with mutual certificates](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="70f16-110">特征</span><span class="sxs-lookup"><span data-stu-id="70f16-110">Characteristic</span></span>|<span data-ttu-id="70f16-111">说明</span><span class="sxs-lookup"><span data-stu-id="70f16-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="70f16-112">安全模式</span><span class="sxs-lookup"><span data-stu-id="70f16-112">Security Mode</span></span>|<span data-ttu-id="70f16-113">Message</span><span class="sxs-lookup"><span data-stu-id="70f16-113">Message</span></span>|  
|<span data-ttu-id="70f16-114">互操作性</span><span class="sxs-lookup"><span data-stu-id="70f16-114">Interoperability</span></span>|<span data-ttu-id="70f16-115">是，使用 WS-Security 和 X.509 证书令牌配置文件兼容的客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="70f16-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="70f16-116">身份验证</span><span class="sxs-lookup"><span data-stu-id="70f16-116">Authentication</span></span>|<span data-ttu-id="70f16-117">服务器和客户端的相互身份验证。</span><span class="sxs-lookup"><span data-stu-id="70f16-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="70f16-118">完整性</span><span class="sxs-lookup"><span data-stu-id="70f16-118">Integrity</span></span>|<span data-ttu-id="70f16-119">是</span><span class="sxs-lookup"><span data-stu-id="70f16-119">Yes</span></span>|  
|<span data-ttu-id="70f16-120">保密性</span><span class="sxs-lookup"><span data-stu-id="70f16-120">Confidentiality</span></span>|<span data-ttu-id="70f16-121">是</span><span class="sxs-lookup"><span data-stu-id="70f16-121">Yes</span></span>|  
|<span data-ttu-id="70f16-122">Transport</span><span class="sxs-lookup"><span data-stu-id="70f16-122">Transport</span></span>|<span data-ttu-id="70f16-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="70f16-123">HTTP</span></span>|  
|<span data-ttu-id="70f16-124">绑定</span><span class="sxs-lookup"><span data-stu-id="70f16-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="70f16-125">服务</span><span class="sxs-lookup"><span data-stu-id="70f16-125">Service</span></span>  
 <span data-ttu-id="70f16-126">下面的代码和配置应独立运行。</span><span class="sxs-lookup"><span data-stu-id="70f16-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="70f16-127">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="70f16-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="70f16-128">使用代码（而不使用配置）创建独立服务。</span><span class="sxs-lookup"><span data-stu-id="70f16-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="70f16-129">使用提供的配置创建服务，但不定义任何终结点。</span><span class="sxs-lookup"><span data-stu-id="70f16-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="70f16-130">代码</span><span class="sxs-lookup"><span data-stu-id="70f16-130">Code</span></span>  
 <span data-ttu-id="70f16-131">下面的代码演示如何创建使用消息安全的服务终结点。</span><span class="sxs-lookup"><span data-stu-id="70f16-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="70f16-132">服务请求一个证书来使自己通过身份验证。</span><span class="sxs-lookup"><span data-stu-id="70f16-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="70f16-133">Configuration</span><span class="sxs-lookup"><span data-stu-id="70f16-133">Configuration</span></span>  
 <span data-ttu-id="70f16-134">可以使用下面的配置，而不使用代码来创建同样的服务。</span><span class="sxs-lookup"><span data-stu-id="70f16-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"
                                storeLocation="LocalMachine"  
                                storeName="My"
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="serviceCredentialBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="70f16-135">客户端</span><span class="sxs-lookup"><span data-stu-id="70f16-135">Client</span></span>  
 <span data-ttu-id="70f16-136">下面的代码和配置应独立运行。</span><span class="sxs-lookup"><span data-stu-id="70f16-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="70f16-137">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="70f16-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="70f16-138">使用代码（和客户端代码）创建独立客户端。</span><span class="sxs-lookup"><span data-stu-id="70f16-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="70f16-139">创建不定义任何终结点地址的客户端。</span><span class="sxs-lookup"><span data-stu-id="70f16-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="70f16-140">而使用将配置名称作为自变量的客户端构造函数。</span><span class="sxs-lookup"><span data-stu-id="70f16-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="70f16-141">例如：</span><span class="sxs-lookup"><span data-stu-id="70f16-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="70f16-142">代码</span><span class="sxs-lookup"><span data-stu-id="70f16-142">Code</span></span>  
 <span data-ttu-id="70f16-143">下面的代码创建客户端。</span><span class="sxs-lookup"><span data-stu-id="70f16-143">The following code creates the client.</span></span> <span data-ttu-id="70f16-144">安全模式设置为“消息”，客户端凭据类型设置为“证书”。</span><span class="sxs-lookup"><span data-stu-id="70f16-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="70f16-145">Configuration</span><span class="sxs-lookup"><span data-stu-id="70f16-145">Configuration</span></span>  
 <span data-ttu-id="70f16-146">下面配置客户端。</span><span class="sxs-lookup"><span data-stu-id="70f16-146">The following configures the client.</span></span> <span data-ttu-id="70f16-147">必须使用指定客户端证书 [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="70f16-147">A client certificate must be specified using the [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="70f16-148">此外，还使用指定服务证书 [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="70f16-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="70f16-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="70f16-149">See also</span></span>

- [<span data-ttu-id="70f16-150">安全性概述</span><span class="sxs-lookup"><span data-stu-id="70f16-150">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="70f16-151">[Windows Server App Fabric 的安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="70f16-151">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="70f16-152">[如何：在 WCF 中创建和安装用于传输安全的临时证书](/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="70f16-152">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
