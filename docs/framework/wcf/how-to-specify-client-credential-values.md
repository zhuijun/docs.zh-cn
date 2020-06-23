---
title: 如何：指定客户端凭据值
description: 了解 WCF 服务如何指定如何对该服务进行客户端身份验证。 此示例指定 x.509 证书和传输模式。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 75a21a7dc083282f6b2fe839167ff1b2eddfb373
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244447"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="fc5bd-104">如何：指定客户端凭据值</span><span class="sxs-lookup"><span data-stu-id="fc5bd-104">How to: Specify Client Credential Values</span></span>

<span data-ttu-id="fc5bd-105">使用 Windows Communication Foundation （WCF），服务可以指定如何向服务验证客户端。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-105">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="fc5bd-106">例如，服务可以规定客户端使用证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-106">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>

## <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="fc5bd-107">确定客户端凭据类型</span><span class="sxs-lookup"><span data-stu-id="fc5bd-107">To determine the client credential type</span></span>

1. <span data-ttu-id="fc5bd-108">从服务的元数据终结点检索元数据。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-108">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="fc5bd-109">通常，元数据包括两个文件：采用所选编程语言（默认情况下为 Visual C#）的客户端代码和一个 XML 配置文件。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-109">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="fc5bd-110">检索元数据的方法之一是使用 Svcutil.exe 工具返回客户端代码和客户端配置。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-110">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="fc5bd-111">有关详细信息，请参阅[检索元数据](./feature-details/retrieving-metadata.md)和[元数据实用工具（Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-111">For more information, see [Retrieving Metadata](./feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

2. <span data-ttu-id="fc5bd-112">打开 XML 配置文件。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-112">Open the XML configuration file.</span></span> <span data-ttu-id="fc5bd-113">如果使用的是 Svcutil.exe 工具，则文件的默认名称为 Output.config。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-113">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>

3. <span data-ttu-id="fc5bd-114">找到 **\<security>** 具有**mode**特性的元素（ **\<security mode =**`MessageOrTransport`**>** 其中 `MessageOrTransport` 设置为一种安全模式）。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-114">Find the **\<security>** element with the **mode** attribute (**\<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>

4. <span data-ttu-id="fc5bd-115">找到与模式值匹配的子元素。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-115">Find the child element that matches the mode value.</span></span> <span data-ttu-id="fc5bd-116">例如，如果模式设置为 "**消息**"，则查找 **\<message>** 元素中包含的元素 **\<security>** 。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-116">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>

5. <span data-ttu-id="fc5bd-117">请注意分配给**clientCredentialType**特性的值。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-117">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="fc5bd-118">实际值取决于所使用的模式（传输或消息）。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-118">The actual value depends on which mode is used, transport or message.</span></span>

<span data-ttu-id="fc5bd-119">下面的 XML 代码演示了对使用消息安全性并要求使用证书对客户端进行身份验证的客户端的配置。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-119">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="fc5bd-120">示例：TCP 传输模式，使用证书作为客户端凭据</span><span class="sxs-lookup"><span data-stu-id="fc5bd-120">Example: TCP Transport Mode with Certificate as Client Credential</span></span>

<span data-ttu-id="fc5bd-121">此示例将安全模式设置为“传输”模式，并将客户端凭据值设置为 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-121">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="fc5bd-122">下面的过程演示如何在代码和配置中设置客户端上的客户端凭据值。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-122">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="fc5bd-123">这假定你已使用配置的[元数据实用工具（Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)从服务返回元数据（代码和配置）。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-123">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="fc5bd-124">有关详细信息，请参阅[如何：创建客户端](how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-124">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="fc5bd-125">在代码中指定客户端上的客户端凭据值</span><span class="sxs-lookup"><span data-stu-id="fc5bd-125">To specify the client credential value on the client in code</span></span>

1. <span data-ttu-id="fc5bd-126">使用配置的[元数据实用工具（Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)从服务生成代码和配置。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-126">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>

2. <span data-ttu-id="fc5bd-127">使用生成的代码创建 WCF 客户端的实例。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-127">Create an instance of the WCF client using the generated code.</span></span>

3. <span data-ttu-id="fc5bd-128">在客户端类上，将 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 类的 <xref:System.ServiceModel.ClientBase%601> 属性设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-128">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="fc5bd-129">本示例使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 类的 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> 方法将该属性设置为 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-129">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     <span data-ttu-id="fc5bd-130">可以使用 <xref:System.Security.Cryptography.X509Certificates.X509FindType> 类的任何枚举。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-130">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="fc5bd-131">如果该证书发生更改（由于超过到期日期），则在此处使用主题名称。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-131">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="fc5bd-132">使用主题名称，基础结构可以再次查找该证书。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-132">Using the subject name enables the infrastructure to find the certificate again.</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="fc5bd-133">在配置中指定客户端上的客户端凭据值</span><span class="sxs-lookup"><span data-stu-id="fc5bd-133">To specify the client credential value on the client in configuration</span></span>

1. <span data-ttu-id="fc5bd-134">向 [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 元素添加元素 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-134">Add a [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

2. <span data-ttu-id="fc5bd-135">向 [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) 元素添加元素 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-135">Add a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="fc5bd-136">请确保将必需的 `name` 属性设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-136">Be sure to set the required `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="fc5bd-137">向 [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) 元素添加元素 [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-137">Add a [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>

4. <span data-ttu-id="fc5bd-138">将下列特性设置为适当的值：`storeLocation`、`storeName`、`x509FindType` 和 `findValue`，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-138">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="fc5bd-139">有关证书的详细信息，请参阅[使用证书](./feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-139">For more information about certificates, see [Working with Certificates](./feature-details/working-with-certificates.md).</span></span>

    ```xml
    <behaviors>
       <endpointBehaviors>
          <behavior name="endpointCredentialBehavior">
            <clientCredentials>
              <clientCertificate findValue="Contoso.com"
                                 storeLocation="LocalMachine"
                                 storeName="TrustedPeople"
                                 x509FindType="FindBySubjectName" />
            </clientCredentials>
          </behavior>
       </endpointBehaviors>
    </behaviors>
    ```

5. <span data-ttu-id="fc5bd-140">在配置客户端时，通过设置 `behaviorConfiguration` 元素的 `<endpoint>` 特性来指定该行为，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-140">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="fc5bd-141">终结点元素是元素的子元素 [\<client>](../configure-apps/file-schema/wcf/client.md) 。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-141">The endpoint element is a child of the [\<client>](../configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="fc5bd-142">同时还要通过将 `bindingConfiguration` 特性设置为客户端的绑定来指定绑定配置的名称。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-142">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="fc5bd-143">如果使用的是生成的配置文件，则自动生成该绑定的名称。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-143">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="fc5bd-144">在本例中，名称为 `"tcpBindingWithCredential"`。</span><span class="sxs-lookup"><span data-stu-id="fc5bd-144">In this example, the name is `"tcpBindingWithCredential"`.</span></span>

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a><span data-ttu-id="fc5bd-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="fc5bd-145">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="fc5bd-146">WCF 安全编程</span><span class="sxs-lookup"><span data-stu-id="fc5bd-146">Programming WCF Security</span></span>](./feature-details/programming-wcf-security.md)
- [<span data-ttu-id="fc5bd-147">选择凭据类型</span><span class="sxs-lookup"><span data-stu-id="fc5bd-147">Selecting a Credential Type</span></span>](./feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="fc5bd-148">ServiceModel 元数据实用工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="fc5bd-148">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="fc5bd-149">使用证书</span><span class="sxs-lookup"><span data-stu-id="fc5bd-149">Working with Certificates</span></span>](./feature-details/working-with-certificates.md)
- [<span data-ttu-id="fc5bd-150">如何：创建客户端</span><span class="sxs-lookup"><span data-stu-id="fc5bd-150">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)
