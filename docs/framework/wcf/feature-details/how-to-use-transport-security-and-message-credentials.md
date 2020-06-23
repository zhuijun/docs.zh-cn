---
title: 如何：使用传输安全和消息凭据
description: 了解如何通过消息凭据实现传输安全，消息凭据提供 WCF 中的最优秀传输和消息安全模式。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f632a4389eafc155cedcae94707c9418b6696f2c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246644"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="96e71-103">如何：使用传输安全和消息凭据</span><span class="sxs-lookup"><span data-stu-id="96e71-103">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="96e71-104">使用传输和消息凭据来保护服务在 Windows Communication Foundation （WCF）中使用传输和消息安全模式的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="96e71-104">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="96e71-105">总之，传输层安全提供了完整性和机密性，而消息层安全则提供了严格的传输安全机制所不可能提供的多种凭据。</span><span class="sxs-lookup"><span data-stu-id="96e71-105">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="96e71-106">本主题演示使用 <xref:System.ServiceModel.WSHttpBinding> 和 <xref:System.ServiceModel.NetTcpBinding> 绑定通过消息凭据实现传输的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="96e71-106">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="96e71-107">有关设置安全模式的详细信息，请参阅[如何：设置安全模式](../how-to-set-the-security-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="96e71-107">For more information about setting the security mode, see [How to: Set the Security Mode](../how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="96e71-108">在将安全模式设置为 `TransportWithMessageCredential` 时，传输会确定实际提供传输级安全的机制。</span><span class="sxs-lookup"><span data-stu-id="96e71-108">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="96e71-109">对于 HTTP，该机制为基于 HTTP 的安全套接字层 (SSL)（SSL over HTPP，或 HTTPS）；对于 TCP，该机制为 SSL over TCP 或 Windows。</span><span class="sxs-lookup"><span data-stu-id="96e71-109">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="96e71-110">如果传输为 HTTP（使用 <xref:System.ServiceModel.WSHttpBinding>），则由 SSL over HTTP 提供传输级安全。</span><span class="sxs-lookup"><span data-stu-id="96e71-110">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="96e71-111">在这种情况下，必须使用绑定到某个端口的 SSL 证书来配置承载服务的计算机，如本主题稍后所示。</span><span class="sxs-lookup"><span data-stu-id="96e71-111">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="96e71-112">如果传输为 TCP（使用 <xref:System.ServiceModel.NetTcpBinding>），则默认情况下提供的传输级安全为 Windows 安全，即 SSL over TCP。</span><span class="sxs-lookup"><span data-stu-id="96e71-112">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="96e71-113">使用 SSL over TCP 时，必须使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 方法指定证书，如本主题稍后所示。</span><span class="sxs-lookup"><span data-stu-id="96e71-113">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="96e71-114">使用 WSHttpBinding 和证书来获得传输安全（在代码中）</span><span class="sxs-lookup"><span data-stu-id="96e71-114">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="96e71-115">使用 HttpCfg.exe 工具将 SSL 证书绑定到计算机上的某个端口。</span><span class="sxs-lookup"><span data-stu-id="96e71-115">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="96e71-116">有关详细信息，请参阅[如何：使用 SSL 证书配置端口](how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="96e71-116">For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2. <span data-ttu-id="96e71-117">创建 <xref:System.ServiceModel.WSHttpBinding> 类的一个实例，并将 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> 属性设置为 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。</span><span class="sxs-lookup"><span data-stu-id="96e71-117">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3. <span data-ttu-id="96e71-118">将 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 属性设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="96e71-118">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="96e71-119">（有关详细信息，请参阅[选择凭据类型](selecting-a-credential-type.md)。）下面的代码使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。</span><span class="sxs-lookup"><span data-stu-id="96e71-119">(For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="96e71-120">用适当的基址创建 <xref:System.Uri> 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="96e71-120">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="96e71-121">请注意，该地址必须使用“HTTPS”方案，且必须包含计算机的实际名称以及 SSL 证书绑定到的端口号。</span><span class="sxs-lookup"><span data-stu-id="96e71-121">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="96e71-122">（也可以在配置中设置基址。）</span><span class="sxs-lookup"><span data-stu-id="96e71-122">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="96e71-123">使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法添加一个服务终结点。</span><span class="sxs-lookup"><span data-stu-id="96e71-123">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6. <span data-ttu-id="96e71-124">创建 <xref:System.ServiceModel.ServiceHost> 的实例并调用 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="96e71-124">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="96e71-125">使用 NetTcpBinding 和证书来获得传输安全（在代码中）</span><span class="sxs-lookup"><span data-stu-id="96e71-125">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="96e71-126">创建 <xref:System.ServiceModel.NetTcpBinding> 类的一个实例，并将 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 属性设置为 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。</span><span class="sxs-lookup"><span data-stu-id="96e71-126">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="96e71-127">将 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> 设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="96e71-127">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="96e71-128">下面的代码使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。</span><span class="sxs-lookup"><span data-stu-id="96e71-128">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3. <span data-ttu-id="96e71-129">用适当的基址创建 <xref:System.Uri> 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="96e71-129">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="96e71-130">请注意，该地址必须使用“net.tcp”方案。</span><span class="sxs-lookup"><span data-stu-id="96e71-130">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="96e71-131">（也可以在配置中设置基址。）</span><span class="sxs-lookup"><span data-stu-id="96e71-131">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4. <span data-ttu-id="96e71-132">创建 <xref:System.ServiceModel.ServiceHost> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="96e71-132">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5. <span data-ttu-id="96e71-133">使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 类的 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 方法显式设置服务的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="96e71-133">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6. <span data-ttu-id="96e71-134">使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法添加一个服务终结点。</span><span class="sxs-lookup"><span data-stu-id="96e71-134">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7. <span data-ttu-id="96e71-135">调用 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="96e71-135">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="96e71-136">使用 NetTcpBinding 和 Windows 来获得传输安全（在代码中）</span><span class="sxs-lookup"><span data-stu-id="96e71-136">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1. <span data-ttu-id="96e71-137">创建 <xref:System.ServiceModel.NetTcpBinding> 类的一个实例，并将 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 属性设置为 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。</span><span class="sxs-lookup"><span data-stu-id="96e71-137">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="96e71-138">将传输安全设置为使用 Windows，方法是将 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> 设置为 <xref:System.ServiceModel.TcpClientCredentialType.Windows>。</span><span class="sxs-lookup"><span data-stu-id="96e71-138">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="96e71-139">（请注意，这是默认值。）</span><span class="sxs-lookup"><span data-stu-id="96e71-139">(Note that this is the default.)</span></span>  
  
3. <span data-ttu-id="96e71-140">将 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> 设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="96e71-140">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="96e71-141">下面的代码使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。</span><span class="sxs-lookup"><span data-stu-id="96e71-141">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="96e71-142">用适当的基址创建 <xref:System.Uri> 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="96e71-142">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="96e71-143">请注意，该地址必须使用“net.tcp”方案。</span><span class="sxs-lookup"><span data-stu-id="96e71-143">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="96e71-144">（也可以在配置中设置基址。）</span><span class="sxs-lookup"><span data-stu-id="96e71-144">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="96e71-145">创建 <xref:System.ServiceModel.ServiceHost> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="96e71-145">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6. <span data-ttu-id="96e71-146">使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 类的 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 方法显式设置服务的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="96e71-146">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7. <span data-ttu-id="96e71-147">使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法添加一个服务终结点。</span><span class="sxs-lookup"><span data-stu-id="96e71-147">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8. <span data-ttu-id="96e71-148">调用 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="96e71-148">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="96e71-149">使用配置</span><span class="sxs-lookup"><span data-stu-id="96e71-149">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="96e71-150">使用 WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="96e71-150">To use the WSHttpBinding</span></span>  
  
1. <span data-ttu-id="96e71-151">使用绑定到某个端口的 SSL 证书配置计算机。</span><span class="sxs-lookup"><span data-stu-id="96e71-151">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="96e71-152">（有关详细信息，请参阅[如何：使用 SSL 证书配置端口](how-to-configure-a-port-with-an-ssl-certificate.md)）。</span><span class="sxs-lookup"><span data-stu-id="96e71-152">(For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="96e71-153">不需要 `transport` 使用此配置设置 <> 元素值。</span><span class="sxs-lookup"><span data-stu-id="96e71-153">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2. <span data-ttu-id="96e71-154">指定消息级安全的客户端凭据类型。</span><span class="sxs-lookup"><span data-stu-id="96e71-154">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="96e71-155">下面的示例将 `clientCredentialType` <> 元素的特性设置 `message` 为 `UserName` 。</span><span class="sxs-lookup"><span data-stu-id="96e71-155">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="96e71-156">使用 NetTcpBinding 和证书来获得传输安全</span><span class="sxs-lookup"><span data-stu-id="96e71-156">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1. <span data-ttu-id="96e71-157">对于 SSL over TCP，必须在 `<behaviors>` 元素中显式指定证书。</span><span class="sxs-lookup"><span data-stu-id="96e71-157">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="96e71-158">下面的示例指定一个证书，该证书由其颁发机构存储在默认存储位置（本地计算机和个人存储）。</span><span class="sxs-lookup"><span data-stu-id="96e71-158">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="96e71-159">将添加 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) 到 "绑定" 部分</span><span class="sxs-lookup"><span data-stu-id="96e71-159">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3. <span data-ttu-id="96e71-160">添加一个绑定元素，并将 `name` 属性设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="96e71-160">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="96e71-161">添加一个 <`security`> 元素，并将 `mode` 特性设置为 `TransportWithMessageCredential` 。</span><span class="sxs-lookup"><span data-stu-id="96e71-161">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5. <span data-ttu-id="96e71-162">添加 <`message>` 元素，并将属性设置 `clientCredentialType` 为合适的值。</span><span class="sxs-lookup"><span data-stu-id="96e71-162">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="96e71-163">使用 NetTcpBinding 和 Windows 来获得传输安全</span><span class="sxs-lookup"><span data-stu-id="96e71-163">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1. <span data-ttu-id="96e71-164">将添加 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) 到 "绑定" 部分，</span><span class="sxs-lookup"><span data-stu-id="96e71-164">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2. <span data-ttu-id="96e71-165">添加一个 <`binding`> 元素，并将 `name` 属性设置为合适的值。</span><span class="sxs-lookup"><span data-stu-id="96e71-165">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="96e71-166">添加一个 <`security`> 元素，并将 `mode` 特性设置为 `TransportWithMessageCredential` 。</span><span class="sxs-lookup"><span data-stu-id="96e71-166">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4. <span data-ttu-id="96e71-167">添加一个 <`transport`> 元素，并将 `clientCredentialType` 特性设置为 `Windows` 。</span><span class="sxs-lookup"><span data-stu-id="96e71-167">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5. <span data-ttu-id="96e71-168">添加一个 <`message`> 元素，并将 `clientCredentialType` 属性设置为合适的值。</span><span class="sxs-lookup"><span data-stu-id="96e71-168">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="96e71-169">下面的代码将该值设置为一个证书。</span><span class="sxs-lookup"><span data-stu-id="96e71-169">The following code sets the value to a certificate.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="96e71-170">请参阅</span><span class="sxs-lookup"><span data-stu-id="96e71-170">See also</span></span>

- [<span data-ttu-id="96e71-171">如何：设置安全模式</span><span class="sxs-lookup"><span data-stu-id="96e71-171">How to: Set the Security Mode</span></span>](../how-to-set-the-security-mode.md)
- [<span data-ttu-id="96e71-172">保证服务的安全</span><span class="sxs-lookup"><span data-stu-id="96e71-172">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="96e71-173">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="96e71-173">Securing Services and Clients</span></span>](securing-services-and-clients.md)
