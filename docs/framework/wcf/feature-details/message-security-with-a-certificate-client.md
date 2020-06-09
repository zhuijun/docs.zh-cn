---
title: 使用证书客户端的消息安全
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 2b2717bc68da9f07cd38e10a5d75b2a7df9add45
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602630"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="b0af0-102">使用证书客户端的消息安全</span><span class="sxs-lookup"><span data-stu-id="b0af0-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="b0af0-103">下面的方案演示使用消息安全模式保护 Windows Communication Foundation （WCF）客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="b0af0-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="b0af0-104">使用证书对客户端和服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b0af0-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="b0af0-105">有关详细信息，请参阅[分布式应用程序安全性](distributed-application-security.md)。</span><span class="sxs-lookup"><span data-stu-id="b0af0-105">For more information, see [Distributed Application Security](distributed-application-security.md).</span></span>

 ![显示具有证书的客户端的屏幕截图。](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="b0af0-107">有关示例应用程序，请参阅[消息安全证书](../samples/message-security-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="b0af0-107">For a sample application, see [Message Security Certificate](../samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="b0af0-108">特征</span><span class="sxs-lookup"><span data-stu-id="b0af0-108">Characteristic</span></span>|<span data-ttu-id="b0af0-109">描述</span><span class="sxs-lookup"><span data-stu-id="b0af0-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b0af0-110">安全模式</span><span class="sxs-lookup"><span data-stu-id="b0af0-110">Security Mode</span></span>|<span data-ttu-id="b0af0-111">Message</span><span class="sxs-lookup"><span data-stu-id="b0af0-111">Message</span></span>|  
|<span data-ttu-id="b0af0-112">互操作性</span><span class="sxs-lookup"><span data-stu-id="b0af0-112">Interoperability</span></span>|<span data-ttu-id="b0af0-113">仅 WCF</span><span class="sxs-lookup"><span data-stu-id="b0af0-113">WCF only</span></span>|  
|<span data-ttu-id="b0af0-114">身份验证（服务器）</span><span class="sxs-lookup"><span data-stu-id="b0af0-114">Authentication (Server)</span></span>|<span data-ttu-id="b0af0-115">使用服务证书</span><span class="sxs-lookup"><span data-stu-id="b0af0-115">Using service certificate</span></span>|  
|<span data-ttu-id="b0af0-116">身份验证（客户端）</span><span class="sxs-lookup"><span data-stu-id="b0af0-116">Authentication (Client)</span></span>|<span data-ttu-id="b0af0-117">使用客户端证书</span><span class="sxs-lookup"><span data-stu-id="b0af0-117">Using client certificate</span></span>|  
|<span data-ttu-id="b0af0-118">完整性</span><span class="sxs-lookup"><span data-stu-id="b0af0-118">Integrity</span></span>|<span data-ttu-id="b0af0-119">是</span><span class="sxs-lookup"><span data-stu-id="b0af0-119">Yes</span></span>|  
|<span data-ttu-id="b0af0-120">机密性</span><span class="sxs-lookup"><span data-stu-id="b0af0-120">Confidentiality</span></span>|<span data-ttu-id="b0af0-121">是</span><span class="sxs-lookup"><span data-stu-id="b0af0-121">Yes</span></span>|  
|<span data-ttu-id="b0af0-122">Transport</span><span class="sxs-lookup"><span data-stu-id="b0af0-122">Transport</span></span>|<span data-ttu-id="b0af0-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="b0af0-123">HTTP</span></span>|  
|<span data-ttu-id="b0af0-124">绑定</span><span class="sxs-lookup"><span data-stu-id="b0af0-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="b0af0-125">服务</span><span class="sxs-lookup"><span data-stu-id="b0af0-125">Service</span></span>  
 <span data-ttu-id="b0af0-126">下面的代码和配置应独立运行。</span><span class="sxs-lookup"><span data-stu-id="b0af0-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b0af0-127">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="b0af0-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="b0af0-128">使用代码（而不使用配置）创建独立服务。</span><span class="sxs-lookup"><span data-stu-id="b0af0-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="b0af0-129">使用提供的配置创建服务，但不定义任何终结点。</span><span class="sxs-lookup"><span data-stu-id="b0af0-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b0af0-130">代码</span><span class="sxs-lookup"><span data-stu-id="b0af0-130">Code</span></span>  
 <span data-ttu-id="b0af0-131">下面的代码演示如何创建一个使用消息安全来建立安全上下文的服务终结点。</span><span class="sxs-lookup"><span data-stu-id="b0af0-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="b0af0-132">Configuration</span><span class="sxs-lookup"><span data-stu-id="b0af0-132">Configuration</span></span>  
 <span data-ttu-id="b0af0-133">以下配置可代替代码使用。</span><span class="sxs-lookup"><span data-stu-id="b0af0-133">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCertificateClient"
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="b0af0-134">客户端</span><span class="sxs-lookup"><span data-stu-id="b0af0-134">Client</span></span>  
 <span data-ttu-id="b0af0-135">下面的代码和配置应独立运行。</span><span class="sxs-lookup"><span data-stu-id="b0af0-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b0af0-136">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="b0af0-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="b0af0-137">使用代码（和客户端代码）创建独立客户端。</span><span class="sxs-lookup"><span data-stu-id="b0af0-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="b0af0-138">创建不定义任何终结点地址的客户端。</span><span class="sxs-lookup"><span data-stu-id="b0af0-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="b0af0-139">而使用将配置名称作为自变量的客户端构造函数。</span><span class="sxs-lookup"><span data-stu-id="b0af0-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="b0af0-140">例如：</span><span class="sxs-lookup"><span data-stu-id="b0af0-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="b0af0-141">代码</span><span class="sxs-lookup"><span data-stu-id="b0af0-141">Code</span></span>  
 <span data-ttu-id="b0af0-142">下面的代码创建客户端。</span><span class="sxs-lookup"><span data-stu-id="b0af0-142">The following code creates the client.</span></span> <span data-ttu-id="b0af0-143">绑定设置为消息模式安全，客户端凭据类型设置为 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="b0af0-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="b0af0-144">Configuration</span><span class="sxs-lookup"><span data-stu-id="b0af0-144">Configuration</span></span>  
 <span data-ttu-id="b0af0-145">下面的配置使用终结点行为指定客户端证书。</span><span class="sxs-lookup"><span data-stu-id="b0af0-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="b0af0-146">有关证书的详细信息，请参阅[使用证书](working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="b0af0-146">For more information about certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="b0af0-147">此代码还使用 <`identity`> 元素来指定预期服务器标识的域名系统（DNS）。</span><span class="sxs-lookup"><span data-stu-id="b0af0-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="b0af0-148">有关标识的详细信息，请参阅[服务标识和身份验证](service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="b0af0-148">For more information about identity, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0af0-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0af0-149">See also</span></span>

- [<span data-ttu-id="b0af0-150">安全性概述</span><span class="sxs-lookup"><span data-stu-id="b0af0-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="b0af0-151">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="b0af0-151">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [<span data-ttu-id="b0af0-152">使用证书</span><span class="sxs-lookup"><span data-stu-id="b0af0-152">Working with Certificates</span></span>](working-with-certificates.md)
- <span data-ttu-id="b0af0-153">[Windows Server App Fabric 的安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b0af0-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
