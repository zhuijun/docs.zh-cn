---
title: 通过 Windows 身份验证确保的传输安全
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 6703da4f97cba38ee0dc334d3010ca509d1fb3ef
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598692"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="2febd-102">通过 Windows 身份验证确保的传输安全</span><span class="sxs-lookup"><span data-stu-id="2febd-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="2febd-103">下面的方案演示了 Windows 安全性所保护的 Windows Communication Foundation （WCF）客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="2febd-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="2febd-104">有关编程的详细信息，请参阅[如何：使用 Windows 凭据保护服务](../how-to-secure-a-service-with-windows-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="2febd-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="2febd-105">Intranet Web 服务显示了人力资源信息。</span><span class="sxs-lookup"><span data-stu-id="2febd-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="2febd-106">客户端是 Windows 窗体应用程序。</span><span class="sxs-lookup"><span data-stu-id="2febd-106">The client is a Windows Form application.</span></span> <span data-ttu-id="2febd-107">该应用程序部署在具有 Kerberos 控制器保护的域中。</span><span class="sxs-lookup"><span data-stu-id="2febd-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![使用 Windows 身份验证的传输安全性](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="2febd-109">特征</span><span class="sxs-lookup"><span data-stu-id="2febd-109">Characteristic</span></span>|<span data-ttu-id="2febd-110">描述</span><span class="sxs-lookup"><span data-stu-id="2febd-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2febd-111">安全模式</span><span class="sxs-lookup"><span data-stu-id="2febd-111">Security Mode</span></span>|<span data-ttu-id="2febd-112">Transport</span><span class="sxs-lookup"><span data-stu-id="2febd-112">Transport</span></span>|  
|<span data-ttu-id="2febd-113">互操作性</span><span class="sxs-lookup"><span data-stu-id="2febd-113">Interoperability</span></span>|<span data-ttu-id="2febd-114">仅 WCF</span><span class="sxs-lookup"><span data-stu-id="2febd-114">WCF only</span></span>|  
|<span data-ttu-id="2febd-115">身份验证（服务器）</span><span class="sxs-lookup"><span data-stu-id="2febd-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="2febd-116">身份验证（客户端）</span><span class="sxs-lookup"><span data-stu-id="2febd-116">Authentication (Client)</span></span>|<span data-ttu-id="2febd-117">是（使用 Windows 集成身份验证）</span><span class="sxs-lookup"><span data-stu-id="2febd-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="2febd-118">是（使用 Windows 集成身份验证）</span><span class="sxs-lookup"><span data-stu-id="2febd-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="2febd-119">完整性</span><span class="sxs-lookup"><span data-stu-id="2febd-119">Integrity</span></span>|<span data-ttu-id="2febd-120">是</span><span class="sxs-lookup"><span data-stu-id="2febd-120">Yes</span></span>|  
|<span data-ttu-id="2febd-121">机密性</span><span class="sxs-lookup"><span data-stu-id="2febd-121">Confidentiality</span></span>|<span data-ttu-id="2febd-122">是</span><span class="sxs-lookup"><span data-stu-id="2febd-122">Yes</span></span>|  
|<span data-ttu-id="2febd-123">Transport</span><span class="sxs-lookup"><span data-stu-id="2febd-123">Transport</span></span>|<span data-ttu-id="2febd-124">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="2febd-124">NET.TCP</span></span>|  
|<span data-ttu-id="2febd-125">绑定</span><span class="sxs-lookup"><span data-stu-id="2febd-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="2febd-126">服务</span><span class="sxs-lookup"><span data-stu-id="2febd-126">Service</span></span>  
 <span data-ttu-id="2febd-127">下面的代码和配置应独立运行。</span><span class="sxs-lookup"><span data-stu-id="2febd-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="2febd-128">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="2febd-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="2febd-129">使用代码（而不使用配置）创建独立服务。</span><span class="sxs-lookup"><span data-stu-id="2febd-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="2febd-130">使用提供的配置创建服务，但不定义任何终结点。</span><span class="sxs-lookup"><span data-stu-id="2febd-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2febd-131">代码</span><span class="sxs-lookup"><span data-stu-id="2febd-131">Code</span></span>  
 <span data-ttu-id="2febd-132">下面的代码演示如何创建使用 Windows 安全的服务终结点。</span><span class="sxs-lookup"><span data-stu-id="2febd-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="2febd-133">Configuration</span><span class="sxs-lookup"><span data-stu-id="2febd-133">Configuration</span></span>  
 <span data-ttu-id="2febd-134">可以使用下面的配置代替代码来设置服务终结点：</span><span class="sxs-lookup"><span data-stu-id="2febd-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="2febd-135">客户端</span><span class="sxs-lookup"><span data-stu-id="2febd-135">Client</span></span>  
 <span data-ttu-id="2febd-136">下面的代码和配置应独立运行。</span><span class="sxs-lookup"><span data-stu-id="2febd-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="2febd-137">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="2febd-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="2febd-138">使用代码（和客户端代码）创建独立客户端。</span><span class="sxs-lookup"><span data-stu-id="2febd-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="2febd-139">创建不定义任何终结点地址的客户端。</span><span class="sxs-lookup"><span data-stu-id="2febd-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="2febd-140">而使用将配置名称作为自变量的客户端构造函数。</span><span class="sxs-lookup"><span data-stu-id="2febd-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="2febd-141">例如：</span><span class="sxs-lookup"><span data-stu-id="2febd-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="2febd-142">代码</span><span class="sxs-lookup"><span data-stu-id="2febd-142">Code</span></span>  
 <span data-ttu-id="2febd-143">下面的代码创建客户端。</span><span class="sxs-lookup"><span data-stu-id="2febd-143">The following code creates the client.</span></span> <span data-ttu-id="2febd-144">绑定配置为使用传输模式安全（采用 TCP 传输协议），并且客户端凭据类型设置为 Windows。</span><span class="sxs-lookup"><span data-stu-id="2febd-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="2febd-145">Configuration</span><span class="sxs-lookup"><span data-stu-id="2febd-145">Configuration</span></span>  
 <span data-ttu-id="2febd-146">可以使用下面的配置代替代码来创建客户端。</span><span class="sxs-lookup"><span data-stu-id="2febd-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2febd-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2febd-147">See also</span></span>

- [<span data-ttu-id="2febd-148">安全性概述</span><span class="sxs-lookup"><span data-stu-id="2febd-148">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="2febd-149">如何：使用 Windows 凭据保护服务的安全</span><span class="sxs-lookup"><span data-stu-id="2febd-149">How to: Secure a Service with Windows Credentials</span></span>](../how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="2febd-150">[Windows Server App Fabric 的安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2febd-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
