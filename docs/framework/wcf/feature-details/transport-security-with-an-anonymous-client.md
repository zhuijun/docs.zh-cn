---
title: 匿名客户端的传输安全
description: 查看此 WCF 方案，该方案使用传输安全通过客户端信任的证书对服务器进行身份验证。 未对客户端进行身份验证。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 5e8bcab4cdd8f27e9ea27e66fe4c848ccd35e99c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556806"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="ad262-104">匿名客户端的传输安全</span><span class="sxs-lookup"><span data-stu-id="ad262-104">Transport security with an anonymous client</span></span>

<span data-ttu-id="ad262-105">此 Windows Communication Foundation (WCF) 方案使用传输安全 (HTTPS) 来确保机密性和完整性。</span><span class="sxs-lookup"><span data-stu-id="ad262-105">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="ad262-106">必须使用安全套接字层 (SSL) 证书对服务器进行身份验证，并且客户端必须信任服务器的证书。</span><span class="sxs-lookup"><span data-stu-id="ad262-106">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="ad262-107">客户端不通过任何机制进行身份验证，因此是匿名的。</span><span class="sxs-lookup"><span data-stu-id="ad262-107">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="ad262-108">有关示例应用程序，请参阅 [WS 传输安全性](../samples/ws-transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="ad262-108">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="ad262-109">有关传输安全的详细信息，请参阅 [传输安全概述](transport-security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ad262-109">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="ad262-110">有关将证书用于服务的详细信息，请参阅使用 [证书](working-with-certificates.md) 和 [如何：使用 SSL 证书配置端口](how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="ad262-110">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![对匿名客户端使用传输安全性](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="ad262-112">特征</span><span class="sxs-lookup"><span data-stu-id="ad262-112">Characteristic</span></span>|<span data-ttu-id="ad262-113">说明</span><span class="sxs-lookup"><span data-stu-id="ad262-113">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="ad262-114">安全模式</span><span class="sxs-lookup"><span data-stu-id="ad262-114">Security Mode</span></span>|<span data-ttu-id="ad262-115">Transport</span><span class="sxs-lookup"><span data-stu-id="ad262-115">Transport</span></span>|
|<span data-ttu-id="ad262-116">互操作性</span><span class="sxs-lookup"><span data-stu-id="ad262-116">Interoperability</span></span>|<span data-ttu-id="ad262-117">与现有 Web 服务和客户端</span><span class="sxs-lookup"><span data-stu-id="ad262-117">With existing Web services and clients</span></span>|
|<span data-ttu-id="ad262-118">身份验证（服务器）</span><span class="sxs-lookup"><span data-stu-id="ad262-118">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="ad262-119">身份验证（客户端）</span><span class="sxs-lookup"><span data-stu-id="ad262-119">Authentication (Client)</span></span>|<span data-ttu-id="ad262-120">是</span><span class="sxs-lookup"><span data-stu-id="ad262-120">Yes</span></span><br /><br /> <span data-ttu-id="ad262-121">应用程序级别 (无 WCF 支持) </span><span class="sxs-lookup"><span data-stu-id="ad262-121">Application level (no WCF support)</span></span>|
|<span data-ttu-id="ad262-122">完整性</span><span class="sxs-lookup"><span data-stu-id="ad262-122">Integrity</span></span>|<span data-ttu-id="ad262-123">是</span><span class="sxs-lookup"><span data-stu-id="ad262-123">Yes</span></span>|
|<span data-ttu-id="ad262-124">保密性</span><span class="sxs-lookup"><span data-stu-id="ad262-124">Confidentiality</span></span>|<span data-ttu-id="ad262-125">是</span><span class="sxs-lookup"><span data-stu-id="ad262-125">Yes</span></span>|
|<span data-ttu-id="ad262-126">Transport</span><span class="sxs-lookup"><span data-stu-id="ad262-126">Transport</span></span>|<span data-ttu-id="ad262-127">HTTPS</span><span class="sxs-lookup"><span data-stu-id="ad262-127">HTTPS</span></span>|
|<span data-ttu-id="ad262-128">绑定</span><span class="sxs-lookup"><span data-stu-id="ad262-128">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="ad262-129">服务</span><span class="sxs-lookup"><span data-stu-id="ad262-129">Service</span></span>

<span data-ttu-id="ad262-130">下面的代码和配置应独立运行。</span><span class="sxs-lookup"><span data-stu-id="ad262-130">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ad262-131">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="ad262-131">Do one of the following:</span></span>

- <span data-ttu-id="ad262-132">使用代码（而不使用配置）创建独立服务。</span><span class="sxs-lookup"><span data-stu-id="ad262-132">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="ad262-133">使用提供的配置创建服务，但不定义任何终结点。</span><span class="sxs-lookup"><span data-stu-id="ad262-133">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="ad262-134">代码</span><span class="sxs-lookup"><span data-stu-id="ad262-134">Code</span></span>

<span data-ttu-id="ad262-135">下面的代码演示如何使用传输安全创建终结点：</span><span class="sxs-lookup"><span data-stu-id="ad262-135">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="ad262-136">Configuration</span><span class="sxs-lookup"><span data-stu-id="ad262-136">Configuration</span></span>

<span data-ttu-id="ad262-137">下面的代码使用配置设置相同的终结点。</span><span class="sxs-lookup"><span data-stu-id="ad262-137">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="ad262-138">客户端不通过任何机制进行身份验证，因此是匿名的。</span><span class="sxs-lookup"><span data-stu-id="ad262-138">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="ServiceModel.Calculator">
        <endpoint address="https://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="SecuredByTransportEndpoint"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator">
          <security mode="Transport">
            <transport clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="ad262-139">客户端</span><span class="sxs-lookup"><span data-stu-id="ad262-139">Client</span></span>

<span data-ttu-id="ad262-140">下面的代码和配置应独立运行。</span><span class="sxs-lookup"><span data-stu-id="ad262-140">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ad262-141">执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="ad262-141">Do one of the following:</span></span>

- <span data-ttu-id="ad262-142">使用代码（和客户端代码）创建独立客户端。</span><span class="sxs-lookup"><span data-stu-id="ad262-142">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="ad262-143">创建不定义任何终结点地址的客户端。</span><span class="sxs-lookup"><span data-stu-id="ad262-143">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="ad262-144">而使用将配置名称作为自变量的客户端构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad262-144">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="ad262-145">例如：</span><span class="sxs-lookup"><span data-stu-id="ad262-145">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="ad262-146">代码</span><span class="sxs-lookup"><span data-stu-id="ad262-146">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="ad262-147">Configuration</span><span class="sxs-lookup"><span data-stu-id="ad262-147">Configuration</span></span>

<span data-ttu-id="ad262-148">下面的配置可代替代码用于设置服务。</span><span class="sxs-lookup"><span data-stu-id="ad262-148">The following configuration can be used instead of the code to set up the service.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Transport">
            <transport clientCredentialType="None" />
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

## <a name="see-also"></a><span data-ttu-id="ad262-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="ad262-149">See also</span></span>

- [<span data-ttu-id="ad262-150">安全性概述</span><span class="sxs-lookup"><span data-stu-id="ad262-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="ad262-151">WS 传输安全</span><span class="sxs-lookup"><span data-stu-id="ad262-151">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="ad262-152">传输安全概述</span><span class="sxs-lookup"><span data-stu-id="ad262-152">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="ad262-153">[Windows Server App Fabric 的安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ad262-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
