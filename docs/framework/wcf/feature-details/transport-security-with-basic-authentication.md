---
title: 通过基本身份验证确保的传输安全
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 7c83de70e404fe8304bc2e35c1bb5df9e42f95b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576091"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="eb3f1-102">通过基本身份验证确保的传输安全</span><span class="sxs-lookup"><span data-stu-id="eb3f1-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="eb3f1-103">下图显示 Windows Communication Foundation （WCF）服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="eb3f1-104">服务器需要一个有效的可用于安全套接字层 (SSL) 的 X.509 证书，并且客户端必须信任此服务器证书。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="eb3f1-105">而且，Web 服务已经有了一个可以使用的 SSL 实现。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="eb3f1-106">有关在 Internet Information Services （IIS）上启用基本身份验证的详细信息，请参阅 <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> 。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-106">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![显示具有基本身份验证的传输安全的屏幕截图。](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="eb3f1-108">特征</span><span class="sxs-lookup"><span data-stu-id="eb3f1-108">Characteristic</span></span>|<span data-ttu-id="eb3f1-109">描述</span><span class="sxs-lookup"><span data-stu-id="eb3f1-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="eb3f1-110">安全模式</span><span class="sxs-lookup"><span data-stu-id="eb3f1-110">Security Mode</span></span>|<span data-ttu-id="eb3f1-111">Transport</span><span class="sxs-lookup"><span data-stu-id="eb3f1-111">Transport</span></span>|  
|<span data-ttu-id="eb3f1-112">互操作性</span><span class="sxs-lookup"><span data-stu-id="eb3f1-112">Interoperability</span></span>|<span data-ttu-id="eb3f1-113">与现有的 Web 服务客户端和服务进行互操作</span><span class="sxs-lookup"><span data-stu-id="eb3f1-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="eb3f1-114">身份验证（服务器）</span><span class="sxs-lookup"><span data-stu-id="eb3f1-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="eb3f1-115">身份验证（客户端）</span><span class="sxs-lookup"><span data-stu-id="eb3f1-115">Authentication (Client)</span></span>|<span data-ttu-id="eb3f1-116">是（使用 HTTPS）</span><span class="sxs-lookup"><span data-stu-id="eb3f1-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="eb3f1-117">是（通过用户名/密码）</span><span class="sxs-lookup"><span data-stu-id="eb3f1-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="eb3f1-118">完整性</span><span class="sxs-lookup"><span data-stu-id="eb3f1-118">Integrity</span></span>|<span data-ttu-id="eb3f1-119">是</span><span class="sxs-lookup"><span data-stu-id="eb3f1-119">Yes</span></span>|  
|<span data-ttu-id="eb3f1-120">机密性</span><span class="sxs-lookup"><span data-stu-id="eb3f1-120">Confidentiality</span></span>|<span data-ttu-id="eb3f1-121">是</span><span class="sxs-lookup"><span data-stu-id="eb3f1-121">Yes</span></span>|  
|<span data-ttu-id="eb3f1-122">Transport</span><span class="sxs-lookup"><span data-stu-id="eb3f1-122">Transport</span></span>|<span data-ttu-id="eb3f1-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="eb3f1-123">HTTPS</span></span>|  
|<span data-ttu-id="eb3f1-124">绑定</span><span class="sxs-lookup"><span data-stu-id="eb3f1-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="eb3f1-125">服务</span><span class="sxs-lookup"><span data-stu-id="eb3f1-125">Service</span></span>  
 <span data-ttu-id="eb3f1-126">下面的代码和配置应独立运行。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="eb3f1-127">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="eb3f1-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="eb3f1-128">使用代码（而不使用配置）创建独立服务。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="eb3f1-129">使用提供的配置创建服务，但不定义任何终结点。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="eb3f1-130">代码</span><span class="sxs-lookup"><span data-stu-id="eb3f1-130">Code</span></span>  
 <span data-ttu-id="eb3f1-131">下面的代码演示如何创建使用 Windows 域用户名和密码确保传输安全的服务终结点。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="eb3f1-132">请注意，此服务要求使用 X.509 证书向客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="eb3f1-133">有关详细信息，请参阅使用[证书](working-with-certificates.md)和[如何：使用 SSL 证书配置端口](how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-133">For more information, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="eb3f1-134">Configuration</span><span class="sxs-lookup"><span data-stu-id="eb3f1-134">Configuration</span></span>  
 <span data-ttu-id="eb3f1-135">下面将配置一个服务以使用具有传输级安全的基本身份验证：</span><span class="sxs-lookup"><span data-stu-id="eb3f1-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="eb3f1-136">客户端</span><span class="sxs-lookup"><span data-stu-id="eb3f1-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="eb3f1-137">代码</span><span class="sxs-lookup"><span data-stu-id="eb3f1-137">Code</span></span>  
 <span data-ttu-id="eb3f1-138">下面的代码演示包括用户名和密码在内的客户端代码。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="eb3f1-139">请注意，此用户必须提供一个有效的 Windows 用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="eb3f1-140">此处不显示用于返回用户名和密码的代码。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="eb3f1-141">使用对话框或其他界面来查询用户的相关信息。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb3f1-142">用户名和密码只能使用代码进行设置。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="eb3f1-143">Configuration</span><span class="sxs-lookup"><span data-stu-id="eb3f1-143">Configuration</span></span>  
 <span data-ttu-id="eb3f1-144">下面的代码演示客户端配置。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb3f1-145">不能使用配置来设置用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="eb3f1-146">此处显示的配置必须使用代码进行扩充以设置用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="eb3f1-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb3f1-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb3f1-147">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="eb3f1-148">使用证书</span><span class="sxs-lookup"><span data-stu-id="eb3f1-148">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="eb3f1-149">如何：使用 SSL 证书配置端口</span><span class="sxs-lookup"><span data-stu-id="eb3f1-149">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="eb3f1-150">安全性概述</span><span class="sxs-lookup"><span data-stu-id="eb3f1-150">Security Overview</span></span>](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="eb3f1-151">[Windows Server App Fabric 的安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="eb3f1-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
