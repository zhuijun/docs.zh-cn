---
title: 如何：保护元数据终结点
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: c5efd921d3826ef814bf45d6895255981101d992
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592952"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="02119-102">如何：保护元数据终结点</span><span class="sxs-lookup"><span data-stu-id="02119-102">How to: Secure Metadata Endpoints</span></span>

<span data-ttu-id="02119-103">服务的元数据中可能包含恶意用户可以利用的关于您的应用程序的敏感信息。</span><span class="sxs-lookup"><span data-stu-id="02119-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="02119-104">服务使用者可能还要求一种用于获取关于服务的元数据的安全机制。</span><span class="sxs-lookup"><span data-stu-id="02119-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="02119-105">因此，有时需要使用安全终结点来发布元数据。</span><span class="sxs-lookup"><span data-stu-id="02119-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>

<span data-ttu-id="02119-106">通常使用 Windows Communication Foundation （WCF）中定义的标准安全机制来保护元数据终结点，以保护应用程序终结点。</span><span class="sxs-lookup"><span data-stu-id="02119-106">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="02119-107">有关详细信息，请参阅[安全性概述](security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="02119-107">For more information, see [Security Overview](security-overview.md).</span></span>

<span data-ttu-id="02119-108">本主题演示创建由安全套接字层 (SSL) 证书保护的终结点（换言之，HTTPS 终结点）的步骤。</span><span class="sxs-lookup"><span data-stu-id="02119-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="02119-109">在代码中创建安全的 HTTPS GET 元数据终结点</span><span class="sxs-lookup"><span data-stu-id="02119-109">To create a secure HTTPS GET metadata endpoint in code</span></span>

1. <span data-ttu-id="02119-110">使用适当的 X.509 证书配置端口。</span><span class="sxs-lookup"><span data-stu-id="02119-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="02119-111">该证书必须来自受信任的颁发机构，而且还必须有既定的“服务授权”用途。</span><span class="sxs-lookup"><span data-stu-id="02119-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="02119-112">必须使用 HttpCfg.exe 工具将该证书附加到该端口。</span><span class="sxs-lookup"><span data-stu-id="02119-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="02119-113">请参阅[如何：使用 SSL 证书配置端口](how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="02119-113">See [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="02119-114">该证书或其域名系统 (DNS) 的主题必须与计算机的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="02119-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="02119-115">这一点非常重要，原因是 HTTPS 机制所执行的前几个步骤之一是检查是否将证书颁发给了在其上调用了该证书的地址的统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="02119-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>

2. <span data-ttu-id="02119-116">创建 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 类的新实例。</span><span class="sxs-lookup"><span data-stu-id="02119-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>

3. <span data-ttu-id="02119-117">将 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> 类的 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="02119-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>

4. <span data-ttu-id="02119-118">将 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> 属性设置为适当的 URL。</span><span class="sxs-lookup"><span data-stu-id="02119-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="02119-119">请注意，如果指定了绝对地址，则 URL 必须以方案开头 `https://` 。</span><span class="sxs-lookup"><span data-stu-id="02119-119">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="02119-120">如果指定相对地址，则必须为服务主机提供一个 HTTPS 基址。</span><span class="sxs-lookup"><span data-stu-id="02119-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="02119-121">如果不设置此属性，则默认地址为 ""，或者直接为服务的 HTTPS 基址。</span><span class="sxs-lookup"><span data-stu-id="02119-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

5. <span data-ttu-id="02119-122">将该实例添加到 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 类的 <xref:System.ServiceModel.Description.ServiceDescription> 属性返回的行为集合中，如下面的代码所示：</span><span class="sxs-lookup"><span data-stu-id="02119-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="02119-123">在配置中创建安全的 HTTPS GET 元数据终结点</span><span class="sxs-lookup"><span data-stu-id="02119-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>

1. <span data-ttu-id="02119-124">将一个 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 元素添加到 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 服务的配置文件的元素中。</span><span class="sxs-lookup"><span data-stu-id="02119-124">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>

2. <span data-ttu-id="02119-125">向 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 元素添加元素 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="02119-125">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

3. <span data-ttu-id="02119-126">向 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) 元素添加元素 `<serviceBehaviors>` 。</span><span class="sxs-lookup"><span data-stu-id="02119-126">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>

4. <span data-ttu-id="02119-127">将 `name` 元素的 `<behavior>` 属性设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="02119-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="02119-128">需要 `name` 属性。</span><span class="sxs-lookup"><span data-stu-id="02119-128">The `name` attribute is required.</span></span> <span data-ttu-id="02119-129">下面的示例使用 `mySvcBehavior` 值。</span><span class="sxs-lookup"><span data-stu-id="02119-129">The example below uses the value `mySvcBehavior`.</span></span>

5. <span data-ttu-id="02119-130">将添加 [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) 到 `<behavior>` 元素。</span><span class="sxs-lookup"><span data-stu-id="02119-130">Add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>

6. <span data-ttu-id="02119-131">将 `httpsGetEnabled` 元素的 `<serviceMetadata>` 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="02119-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>

7. <span data-ttu-id="02119-132">将 `httpsGetUrl` 元素的 `<serviceMetadata>` 属性设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="02119-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="02119-133">请注意，如果指定了绝对地址，则 URL 必须以方案开头 `https://` 。</span><span class="sxs-lookup"><span data-stu-id="02119-133">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="02119-134">如果指定相对地址，则必须为服务主机提供一个 HTTPS 基址。</span><span class="sxs-lookup"><span data-stu-id="02119-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="02119-135">如果不设置此属性，则默认地址为 ""，或者直接为服务的 HTTPS 基址。</span><span class="sxs-lookup"><span data-stu-id="02119-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

8. <span data-ttu-id="02119-136">若要将行为与服务一起使用，请将 `behaviorConfiguration` 元素的属性设置 [\<service>](../../configure-apps/file-schema/wcf/service.md) 为行为元素的 name 特性的值。</span><span class="sxs-lookup"><span data-stu-id="02119-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="02119-137">下面的配置代码演示了一个完整的示例。</span><span class="sxs-lookup"><span data-stu-id="02119-137">The following configuration code shows a complete example.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <system.serviceModel>
      <behaviors>
       <serviceBehaviors>
        <behavior name="mySvcBehavior">
         <serviceMetadata httpsGetEnabled="true"
              httpsGetUrl="https://localhost:8036/calcMetadata" />
        </behavior>
       </serviceBehaviors>
      </behaviors>
     <services>
      <service behaviorConfiguration="mySvcBehavior"
            name="Microsoft.Security.Samples.Calculator">
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"
       binding="wsHttpBinding" bindingConfiguration=""
       contract="Microsoft.Security.Samples.ICalculator" />
      </service>
     </services>
    </system.serviceModel>
    </configuration>
    ```

## <a name="example"></a><span data-ttu-id="02119-138">示例</span><span class="sxs-lookup"><span data-stu-id="02119-138">Example</span></span>

<span data-ttu-id="02119-139">下面的示例创建 <xref:System.ServiceModel.ServiceHost> 类的一个实例并添加一个终结点。</span><span class="sxs-lookup"><span data-stu-id="02119-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="02119-140">然后，该代码创建 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 类的一个实例并设置属性以创建一个安全的元数据交换点。</span><span class="sxs-lookup"><span data-stu-id="02119-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="02119-141">编译代码</span><span class="sxs-lookup"><span data-stu-id="02119-141">Compiling the Code</span></span>

<span data-ttu-id="02119-142">该代码示例使用下列命名空间：</span><span class="sxs-lookup"><span data-stu-id="02119-142">The code example uses the following namespaces:</span></span>

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="02119-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02119-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [<span data-ttu-id="02119-144">如何：使用 SSL 证书配置端口</span><span class="sxs-lookup"><span data-stu-id="02119-144">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="02119-145">使用证书</span><span class="sxs-lookup"><span data-stu-id="02119-145">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="02119-146">元数据的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="02119-146">Security Considerations with Metadata</span></span>](security-considerations-with-metadata.md)
- [<span data-ttu-id="02119-147">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="02119-147">Securing Services and Clients</span></span>](securing-services-and-clients.md)
