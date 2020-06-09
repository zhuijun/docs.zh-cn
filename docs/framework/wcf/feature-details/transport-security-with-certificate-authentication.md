---
title: 利用证书身份验证的传输安全
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: 47322cbcddf9f33101bbfbeaa07a3fab74b9d26a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576013"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="868f6-102">利用证书身份验证的传输安全</span><span class="sxs-lookup"><span data-stu-id="868f6-102">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="868f6-103">本文讨论在使用传输安全时，如何使用 x.509 证书进行服务器和客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="868f6-103">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="868f6-104">有关 X.509 证书的详细信息，请参阅 [X.509 公钥证书](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates)。</span><span class="sxs-lookup"><span data-stu-id="868f6-104">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="868f6-105">证书必须由证书颁发机构颁发，证书颁发机构通常是证书的第三方颁发者。</span><span class="sxs-lookup"><span data-stu-id="868f6-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="868f6-106">在 Windows Server 域中，可以使用 Active Directory 证书服务向域中的客户端计算机颁发证书。</span><span class="sxs-lookup"><span data-stu-id="868f6-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="868f6-107">在此方案中，该服务承载在使用安全套接字层 (SSL) 配置的 Internet Information Services (IIS) 之下。</span><span class="sxs-lookup"><span data-stu-id="868f6-107">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="868f6-108">该服务使用 SSL (X.509) 证书进行配置，以允许客户端验证服务器的身份。</span><span class="sxs-lookup"><span data-stu-id="868f6-108">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="868f6-109">客户端也使用 X.509 证书进行配置，以允许服务验证客户端的身份。</span><span class="sxs-lookup"><span data-stu-id="868f6-109">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="868f6-110">客户端必须信任服务器的证书，服务器也必须信任客户端的证书。</span><span class="sxs-lookup"><span data-stu-id="868f6-110">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="868f6-111">服务和客户端验证彼此身份的实际机制超出了本文的范围。</span><span class="sxs-lookup"><span data-stu-id="868f6-111">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="868f6-112">有关详细信息，请参阅维基百科上的[数字签名](https://en.wikipedia.org/wiki/Digital_signature)。</span><span class="sxs-lookup"><span data-stu-id="868f6-112">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="868f6-113">该方案实现一个请求/回复消息模式，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="868f6-113">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="868f6-114">![使用证书进行安全传输](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="868f6-114">![Secure transfer using certificates](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="868f6-115">有关将证书用于服务的详细信息，请参阅使用[证书](working-with-certificates.md)和[如何：使用 SSL 证书配置端口](how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="868f6-115">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="868f6-116">下表描述了该方案的各项特征。</span><span class="sxs-lookup"><span data-stu-id="868f6-116">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="868f6-117">特征</span><span class="sxs-lookup"><span data-stu-id="868f6-117">Characteristic</span></span>|<span data-ttu-id="868f6-118">描述</span><span class="sxs-lookup"><span data-stu-id="868f6-118">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="868f6-119">安全模式</span><span class="sxs-lookup"><span data-stu-id="868f6-119">Security Mode</span></span>|<span data-ttu-id="868f6-120">Transport</span><span class="sxs-lookup"><span data-stu-id="868f6-120">Transport</span></span>|  
|<span data-ttu-id="868f6-121">互操作性</span><span class="sxs-lookup"><span data-stu-id="868f6-121">Interoperability</span></span>|<span data-ttu-id="868f6-122">与现有 Web 服务客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="868f6-122">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="868f6-123">身份验证（服务器）</span><span class="sxs-lookup"><span data-stu-id="868f6-123">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="868f6-124">身份验证（客户端）</span><span class="sxs-lookup"><span data-stu-id="868f6-124">Authentication (Client)</span></span>|<span data-ttu-id="868f6-125">是（使用 SSL 证书）</span><span class="sxs-lookup"><span data-stu-id="868f6-125">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="868f6-126">是（使用 X.509 证书）</span><span class="sxs-lookup"><span data-stu-id="868f6-126">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="868f6-127">数据完整性</span><span class="sxs-lookup"><span data-stu-id="868f6-127">Data Integrity</span></span>|<span data-ttu-id="868f6-128">是</span><span class="sxs-lookup"><span data-stu-id="868f6-128">Yes</span></span>|  
|<span data-ttu-id="868f6-129">数据保密性</span><span class="sxs-lookup"><span data-stu-id="868f6-129">Data Confidentiality</span></span>|<span data-ttu-id="868f6-130">是</span><span class="sxs-lookup"><span data-stu-id="868f6-130">Yes</span></span>|  
|<span data-ttu-id="868f6-131">Transport</span><span class="sxs-lookup"><span data-stu-id="868f6-131">Transport</span></span>|<span data-ttu-id="868f6-132">HTTPS</span><span class="sxs-lookup"><span data-stu-id="868f6-132">HTTPS</span></span>|  
|<span data-ttu-id="868f6-133">绑定</span><span class="sxs-lookup"><span data-stu-id="868f6-133">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="868f6-134">配置服务</span><span class="sxs-lookup"><span data-stu-id="868f6-134">Configure the Service</span></span>  
 <span data-ttu-id="868f6-135">由于该方案中的服务承载于 IIS 之下，因此它是使用 web.config 文件配置的。</span><span class="sxs-lookup"><span data-stu-id="868f6-135">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="868f6-136">以下 web.config 揭示了如何配置  <xref:System.ServiceModel.WSHttpBinding> 以使用传输安全性和 X.509 客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="868f6-136">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a><span data-ttu-id="868f6-137">配置客户端</span><span class="sxs-lookup"><span data-stu-id="868f6-137">Configure the Client</span></span>  
 <span data-ttu-id="868f6-138">可以在代码中或在 app.config 文件中配置客户端。</span><span class="sxs-lookup"><span data-stu-id="868f6-138">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="868f6-139">下例揭示了如何在代码中配置客户端。</span><span class="sxs-lookup"><span data-stu-id="868f6-139">The following example shows how to configure the client in code.</span></span>  
  
```csharp
// Create the binding.  
var myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.
var ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
var cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 <span data-ttu-id="868f6-140">也可以在 app.config 文件中配置客户端，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="868f6-140">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="868f6-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="868f6-141">See also</span></span>

- [<span data-ttu-id="868f6-142">安全性概述</span><span class="sxs-lookup"><span data-stu-id="868f6-142">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="868f6-143">[Windows Server App Fabric 的安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="868f6-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
