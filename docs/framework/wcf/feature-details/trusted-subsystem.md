---
title: 受信任的子系统
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 29ac26616313ec8bd7661cb92c42f726ec051cd7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542882"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="1cd76-102">受信任的子系统</span><span class="sxs-lookup"><span data-stu-id="1cd76-102">Trusted Subsystem</span></span>
<span data-ttu-id="1cd76-103">客户端访问分布在网络上的一个或多个 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="1cd76-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="1cd76-104">Web 服务的设计使对其他资源（比如数据库或其他 Web 服务）的访问包装在 Web 服务的企业逻辑中。</span><span class="sxs-lookup"><span data-stu-id="1cd76-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="1cd76-105">必须保护这些资源不受到未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="1cd76-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="1cd76-106">下图描述了一个受信任的子系统过程。</span><span class="sxs-lookup"><span data-stu-id="1cd76-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="1cd76-107">![受信任子系统](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="1cd76-107">![Trusted subsystem](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="1cd76-108">以下步骤说明如图所示的受信任子系统过程：</span><span class="sxs-lookup"><span data-stu-id="1cd76-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1. <span data-ttu-id="1cd76-109">客户端向受信任的子系统随凭据一起提交请求。</span><span class="sxs-lookup"><span data-stu-id="1cd76-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2. <span data-ttu-id="1cd76-110">受信任的子系统对用户进行身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="1cd76-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3. <span data-ttu-id="1cd76-111">受信任的子系统向远程资源发送请求消息。</span><span class="sxs-lookup"><span data-stu-id="1cd76-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="1cd76-112">此请求伴随受信任子系统（或在其下执行受信任子系统过程的服务帐户）的凭据。</span><span class="sxs-lookup"><span data-stu-id="1cd76-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4. <span data-ttu-id="1cd76-113">后端资源对受信任子系统进行身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="1cd76-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="1cd76-114">然后处理请求并对受信任子系统发出响应。</span><span class="sxs-lookup"><span data-stu-id="1cd76-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5. <span data-ttu-id="1cd76-115">受信任子系统处理响应并对客户端发出其自己的响应。</span><span class="sxs-lookup"><span data-stu-id="1cd76-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="1cd76-116">特征</span><span class="sxs-lookup"><span data-stu-id="1cd76-116">Characteristic</span></span>|<span data-ttu-id="1cd76-117">说明</span><span class="sxs-lookup"><span data-stu-id="1cd76-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1cd76-118">安全模式</span><span class="sxs-lookup"><span data-stu-id="1cd76-118">Security Mode</span></span>|<span data-ttu-id="1cd76-119">Message</span><span class="sxs-lookup"><span data-stu-id="1cd76-119">Message</span></span>|  
|<span data-ttu-id="1cd76-120">互操作性</span><span class="sxs-lookup"><span data-stu-id="1cd76-120">Interoperability</span></span>|<span data-ttu-id="1cd76-121">仅 (WCF) Windows Communication Foundation。</span><span class="sxs-lookup"><span data-stu-id="1cd76-121">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="1cd76-122">身份验证（服务）</span><span class="sxs-lookup"><span data-stu-id="1cd76-122">Authentication (service)</span></span>|<span data-ttu-id="1cd76-123">安全令牌服务对客户端进行身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="1cd76-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="1cd76-124">身份验证（客户端）</span><span class="sxs-lookup"><span data-stu-id="1cd76-124">Authentication (client)</span></span>|<span data-ttu-id="1cd76-125">受信任子系统对客户端进行身份验证，资源对受信任子系统服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="1cd76-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="1cd76-126">完整性</span><span class="sxs-lookup"><span data-stu-id="1cd76-126">Integrity</span></span>|<span data-ttu-id="1cd76-127">是</span><span class="sxs-lookup"><span data-stu-id="1cd76-127">Yes</span></span>|  
|<span data-ttu-id="1cd76-128">保密性</span><span class="sxs-lookup"><span data-stu-id="1cd76-128">Confidentiality</span></span>|<span data-ttu-id="1cd76-129">是</span><span class="sxs-lookup"><span data-stu-id="1cd76-129">Yes</span></span>|  
|<span data-ttu-id="1cd76-130">Transport</span><span class="sxs-lookup"><span data-stu-id="1cd76-130">Transport</span></span>|<span data-ttu-id="1cd76-131">客户端和受信任子系统服务之间采用 HTTP。</span><span class="sxs-lookup"><span data-stu-id="1cd76-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="1cd76-132">受信任子系统服务和资源（后端服务）之间采用 NET.TCP。</span><span class="sxs-lookup"><span data-stu-id="1cd76-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="1cd76-133">绑定</span><span class="sxs-lookup"><span data-stu-id="1cd76-133">Binding</span></span>|<span data-ttu-id="1cd76-134"><xref:System.ServiceModel.WSHttpBinding> 与 <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1cd76-134"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="1cd76-135">资源（后端服务）</span><span class="sxs-lookup"><span data-stu-id="1cd76-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="1cd76-136">代码</span><span class="sxs-lookup"><span data-stu-id="1cd76-136">Code</span></span>  
 <span data-ttu-id="1cd76-137">下面的代码演示如何创建资源的服务终结点，该服务终结点使用 TCP 上的传输安全传输协议。</span><span class="sxs-lookup"><span data-stu-id="1cd76-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="1cd76-138">Configuration</span><span class="sxs-lookup"><span data-stu-id="1cd76-138">Configuration</span></span>  
 <span data-ttu-id="1cd76-139">下面的配置使用配置设置相同的终结点。</span><span class="sxs-lookup"><span data-stu-id="1cd76-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a><span data-ttu-id="1cd76-140">受信任的子系统</span><span class="sxs-lookup"><span data-stu-id="1cd76-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="1cd76-141">代码</span><span class="sxs-lookup"><span data-stu-id="1cd76-141">Code</span></span>  
 <span data-ttu-id="1cd76-142">下面的代码演示如何创建受信任子系统的服务终结点，该服务终结点使用 HTTP 上的消息安全协议以及用户名和密码进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="1cd76-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="1cd76-143">下面的代码演示受信任子系统中使用 TCP 上的传输安全传输协议与后端服务进行通信的服务。</span><span class="sxs-lookup"><span data-stu-id="1cd76-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="1cd76-144">Configuration</span><span class="sxs-lookup"><span data-stu-id="1cd76-144">Configuration</span></span>  
 <span data-ttu-id="1cd76-145">下面的配置使用配置设置相同的终结点。</span><span class="sxs-lookup"><span data-stu-id="1cd76-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="1cd76-146">注意有两个绑定：一个用于保证承载于受信任子系统中的服务的安全，另一个用于在受信任子系统和后端服务之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="1cd76-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="1cd76-147">客户端</span><span class="sxs-lookup"><span data-stu-id="1cd76-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="1cd76-148">代码</span><span class="sxs-lookup"><span data-stu-id="1cd76-148">Code</span></span>  
 <span data-ttu-id="1cd76-149">下面的代码演示如何创建与受信任子系统进行通信的客户端，该客户端使用 HTTP 上的消息安全协议以及用户名和密码进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="1cd76-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="1cd76-150">Configuration</span><span class="sxs-lookup"><span data-stu-id="1cd76-150">Configuration</span></span>  
 <span data-ttu-id="1cd76-151">下面的代码将客户端配置成使用 HTTP 上的消息安全协议以及用户名和密码进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="1cd76-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="1cd76-152">用户名和密码只能使用代码指定（不可配置）。</span><span class="sxs-lookup"><span data-stu-id="1cd76-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1cd76-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="1cd76-153">See also</span></span>

- [<span data-ttu-id="1cd76-154">安全性概述</span><span class="sxs-lookup"><span data-stu-id="1cd76-154">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="1cd76-155">[Windows Server App Fabric 的安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1cd76-155">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
