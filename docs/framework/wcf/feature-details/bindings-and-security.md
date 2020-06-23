---
title: 绑定与安全
description: 了解如何根据您的安全需求来选择正确的绑定。 WCF 提供的系统提供的绑定提供了对 WCF 应用程序进行编程的一种快速方法。
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: e012ec9ad340c74f5bc776cfc6d8b88326210fec
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245322"
---
# <a name="bindings-and-security"></a><span data-ttu-id="2767a-104">绑定与安全</span><span class="sxs-lookup"><span data-stu-id="2767a-104">Bindings and Security</span></span>

<span data-ttu-id="2767a-105">随 Windows Communication Foundation （WCF）提供的系统提供的绑定提供了对 WCF 应用程序进行编程的一种快速方法。</span><span class="sxs-lookup"><span data-stu-id="2767a-105">The system-provided bindings included with Windows Communication Foundation (WCF) offer a quick way to program WCF applications.</span></span> <span data-ttu-id="2767a-106">但有一个例外，就是所有绑定都启用了默认的安全方案。</span><span class="sxs-lookup"><span data-stu-id="2767a-106">With one exception, all the bindings have a default security scheme enabled.</span></span> <span data-ttu-id="2767a-107">本主题将帮助你根据安全需要来选择正确的绑定。</span><span class="sxs-lookup"><span data-stu-id="2767a-107">This topic helps you select the right binding for your security needs.</span></span>

<span data-ttu-id="2767a-108">有关 WCF 安全性的概述，请参阅[安全性概述](security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2767a-108">For an overview of WCF security, see [Security Overview](security-overview.md).</span></span> <span data-ttu-id="2767a-109">有关使用绑定对 WCF 编程的详细信息，请参阅对[Wcf 安全编程](programming-wcf-security.md)。</span><span class="sxs-lookup"><span data-stu-id="2767a-109">For more information about programming WCF using bindings, see [Programming WCF Security](programming-wcf-security.md).</span></span>

<span data-ttu-id="2767a-110">如果你已经选择了一个绑定，可以在[安全行为](security-behaviors-in-wcf.md)中了解有关与安全性相关联的运行时行为的详细信息。</span><span class="sxs-lookup"><span data-stu-id="2767a-110">If you have already selected a binding, you can find out more about the run-time behaviors that are associated with security in [Security Behaviors](security-behaviors-in-wcf.md).</span></span>

<span data-ttu-id="2767a-111">部分安全性功能无法用系统提供的绑定进行编程。</span><span class="sxs-lookup"><span data-stu-id="2767a-111">Some security functions are not programmable using the system-provided bindings.</span></span> <span data-ttu-id="2767a-112">有关使用自定义绑定的更多控制，请参阅[使用自定义绑定的安全功能](security-capabilities-with-custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="2767a-112">For more control using a custom binding, see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md).</span></span>

## <a name="security-functions-of-bindings"></a><span data-ttu-id="2767a-113">绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="2767a-113">Security Functions of Bindings</span></span>

<span data-ttu-id="2767a-114">WCF 包含多个系统提供的绑定，这些绑定可满足大多数需求。</span><span class="sxs-lookup"><span data-stu-id="2767a-114">WCF includes a number of system-provided bindings that meet most needs.</span></span> <span data-ttu-id="2767a-115">如果某个特定绑定不能满足要求，您还可以创建自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="2767a-115">If a particular binding does not suffice, you can also create a custom binding.</span></span> <span data-ttu-id="2767a-116">有关系统提供的绑定的列表，请参阅[系统提供的绑定](../system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="2767a-116">For a list of system-provided bindings, see [System-Provided Bindings](../system-provided-bindings.md).</span></span> <span data-ttu-id="2767a-117">有关自定义绑定的详细信息，请参阅[自定义绑定](../extending/custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="2767a-117">For more information about custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>

<span data-ttu-id="2767a-118">WCF 中的每个绑定都有两种形式：作为 API，以及在配置文件中使用的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="2767a-118">Every binding in WCF has two forms: as an API and as an XML element used in a configuration file.</span></span> <span data-ttu-id="2767a-119">例如， `WSHttpBinding` （API）在中有一个对应的 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2767a-119">For example, the `WSHttpBinding` (API) has a counterpart in the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>

<span data-ttu-id="2767a-120">下一节列出了每个绑定的两种形式，并概括了安全功能。</span><span class="sxs-lookup"><span data-stu-id="2767a-120">The following section lists both forms for each binding and summarizes the security features.</span></span>

### <a name="basichttp"></a><span data-ttu-id="2767a-121">BasicHttp</span><span class="sxs-lookup"><span data-stu-id="2767a-121">BasicHttp</span></span>

<span data-ttu-id="2767a-122">在代码中，使用 <xref:System.ServiceModel.BasicHttpBinding> 类; 在配置中，使用 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2767a-122">In code, use the <xref:System.ServiceModel.BasicHttpBinding> class; in configuration, use the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>

<span data-ttu-id="2767a-123">此绑定的目的是与如下一系列现有技术一起使用：</span><span class="sxs-lookup"><span data-stu-id="2767a-123">This binding is designed for use with a range of existing technologies, including the following:</span></span>

- <span data-ttu-id="2767a-124">ASP.NET Web 服务 (ASMX) 版本 1。</span><span class="sxs-lookup"><span data-stu-id="2767a-124">ASP.NET Web services (ASMX), version 1.</span></span>

- <span data-ttu-id="2767a-125">Web Service Enhancements (WSE) 应用程序。</span><span class="sxs-lookup"><span data-stu-id="2767a-125">Web Service Enhancements (WSE) applications.</span></span>

- <span data-ttu-id="2767a-126">Web 服务互操作性（WS-I）规范（）中定义的基本配置文件 <https://go.microsoft.com/fwlink/?LinkId=38955> 。</span><span class="sxs-lookup"><span data-stu-id="2767a-126">Basic Profile as defined in the Web Services Interoperability (WS-I) specification (<https://go.microsoft.com/fwlink/?LinkId=38955>).</span></span>

- <span data-ttu-id="2767a-127">WS-I 中定义的基本安全配置文件。</span><span class="sxs-lookup"><span data-stu-id="2767a-127">Basic security profile as defined in WS-I.</span></span>

<span data-ttu-id="2767a-128">默认情况下，此绑定是不安全的。</span><span class="sxs-lookup"><span data-stu-id="2767a-128">By default, this binding is not secure.</span></span> <span data-ttu-id="2767a-129">它的目的是与 ASMX 服务进行互操作。</span><span class="sxs-lookup"><span data-stu-id="2767a-129">It is designed to interoperate with ASMX services.</span></span> <span data-ttu-id="2767a-130">启用安全性后，此绑定可以与 Internet 信息服务 (IIS) 安全机制（例如基本身份验证、摘要和 Windows 集成安全性）进行无缝的互操作。</span><span class="sxs-lookup"><span data-stu-id="2767a-130">When security is enabled, the binding is designed for seamless interoperation with Internet Information Services (IIS) security mechanisms, such as basic authentication, digest, and integrated Windows security.</span></span> <span data-ttu-id="2767a-131">有关详细信息，请参阅[传输安全概述](transport-security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2767a-131">For more information, see [Transport Security Overview](transport-security-overview.md).</span></span> <span data-ttu-id="2767a-132">此绑定支持以下功能：</span><span class="sxs-lookup"><span data-stu-id="2767a-132">This binding supports the following:</span></span>

- <span data-ttu-id="2767a-133">HTTPS 传输安全。</span><span class="sxs-lookup"><span data-stu-id="2767a-133">HTTPS transport security.</span></span>

- <span data-ttu-id="2767a-134">HTTP 基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-134">HTTP basic authentication.</span></span>

- <span data-ttu-id="2767a-135">WS-Security。</span><span class="sxs-lookup"><span data-stu-id="2767a-135">WS-Security.</span></span>

<span data-ttu-id="2767a-136">有关详细信息，请参阅<xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>和<xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="2767a-136">For more information, see <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>, and <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>

### <a name="wshttpbinding"></a><span data-ttu-id="2767a-137">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2767a-137">WSHttpBinding</span></span>

<span data-ttu-id="2767a-138">在代码中，使用 <xref:System.ServiceModel.WSHttpBinding> 类; 在配置中，使用 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2767a-138">In code, use the <xref:System.ServiceModel.WSHttpBinding> class; in configuration, use the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>

<span data-ttu-id="2767a-139">默认情况下，此绑定实现 WS-Security 规范，并提供与实现 WS-\* 规范的服务的互操作性。</span><span class="sxs-lookup"><span data-stu-id="2767a-139">By default, this binding implements the WS-Security specification and provides interoperability with services that implement the WS-\* specifications.</span></span> <span data-ttu-id="2767a-140">它支持以下功能：</span><span class="sxs-lookup"><span data-stu-id="2767a-140">It supports the following:</span></span>

- <span data-ttu-id="2767a-141">HTTPS 传输安全。</span><span class="sxs-lookup"><span data-stu-id="2767a-141">HTTPS transport security.</span></span>

- <span data-ttu-id="2767a-142">WS-Security。</span><span class="sxs-lookup"><span data-stu-id="2767a-142">WS-Security.</span></span>

- <span data-ttu-id="2767a-143">使用 SOAP 消息凭据安全对调用方进行身份验证的 HTTPS 传输保护。</span><span class="sxs-lookup"><span data-stu-id="2767a-143">HTTPS transport protection with SOAP message credential security for authenticating the caller.</span></span>

<span data-ttu-id="2767a-144">有关详细信息，请参阅、、、、、 <xref:System.ServiceModel.WSHttpSecurity> <xref:System.ServiceModel.MessageSecurityOverHttp> <xref:System.ServiceModel.MessageCredentialType> <xref:System.ServiceModel.SecurityMode> <xref:System.ServiceModel.HttpTransportSecurity> <xref:System.ServiceModel.HttpClientCredentialType> 和 <xref:System.ServiceModel.HttpProxyCredentialType> 。</span><span class="sxs-lookup"><span data-stu-id="2767a-144">For more information, see <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, and <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>

### <a name="wsdualhttpbinding"></a><span data-ttu-id="2767a-145">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2767a-145">WSDualHttpBinding</span></span>

<span data-ttu-id="2767a-146">在代码中，使用 <xref:System.ServiceModel.WSDualHttpBinding> 类; 在配置中，使用 [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2767a-146">In code, use the <xref:System.ServiceModel.WSDualHttpBinding> class; in configuration, use the [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>

<span data-ttu-id="2767a-147">此绑定的目的是启用双工服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="2767a-147">This binding is designed to enable duplex service applications.</span></span> <span data-ttu-id="2767a-148">此绑定实现了 WS-Security 规范，以便获得基于消息的传送安全。</span><span class="sxs-lookup"><span data-stu-id="2767a-148">This binding implements the WS-Security specification for message-based transfer security.</span></span> <span data-ttu-id="2767a-149">传输安全不可用。</span><span class="sxs-lookup"><span data-stu-id="2767a-149">Transport security is not available.</span></span> <span data-ttu-id="2767a-150">默认情况下，它提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="2767a-150">By default, it provides the following features:</span></span>

- <span data-ttu-id="2767a-151">实现 WS-Reliable Messaging 以保证可靠性。</span><span class="sxs-lookup"><span data-stu-id="2767a-151">Implements WS-Reliable Messaging for reliability.</span></span>

- <span data-ttu-id="2767a-152">实现 WS-Security 以保证传送安全和身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-152">Implements WS-Security for transfer security and authentication.</span></span>

- <span data-ttu-id="2767a-153">使用 HTTP 进行消息传递。</span><span class="sxs-lookup"><span data-stu-id="2767a-153">Uses HTTP for message delivery.</span></span>

- <span data-ttu-id="2767a-154">使用文本/XML 消息编码。</span><span class="sxs-lookup"><span data-stu-id="2767a-154">Uses text/XML message encoding.</span></span>

 <span data-ttu-id="2767a-155">使用 WS-Security（消息层安全性），可通过此绑定配置下列参数：</span><span class="sxs-lookup"><span data-stu-id="2767a-155">Using WS-Security (message-layer security), the binding allows you to configure the following parameters:</span></span>

- <span data-ttu-id="2767a-156">用来确定加密算法的安全算法组。</span><span class="sxs-lookup"><span data-stu-id="2767a-156">The security algorithm suite to determine the cryptographic algorithm.</span></span>

- <span data-ttu-id="2767a-157">下列功能的绑定选项：</span><span class="sxs-lookup"><span data-stu-id="2767a-157">Binding options for the following:</span></span>

  - <span data-ttu-id="2767a-158">提供可在客户端带外使用的服务凭据。</span><span class="sxs-lookup"><span data-stu-id="2767a-158">Providing service credentials available out-of-band at the client.</span></span>

  - <span data-ttu-id="2767a-159">提供从服务协商的服务凭据作为通道设置的一部分。</span><span class="sxs-lookup"><span data-stu-id="2767a-159">Providing service credentials negotiated from the service as part of channel setup.</span></span>

<span data-ttu-id="2767a-160">有关详细信息，请参阅 <xref:System.ServiceModel.WSDualHttpSecurity> 和 <xref:System.ServiceModel.WSDualHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="2767a-160">For more information, see <xref:System.ServiceModel.WSDualHttpSecurity> and <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>

### <a name="nettcpbinding"></a><span data-ttu-id="2767a-161">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="2767a-161">NetTcpBinding</span></span>

<span data-ttu-id="2767a-162">在代码中，使用 <xref:System.ServiceModel.NetTcpBinding> 类; 在配置中，使用 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2767a-162">In code, use the <xref:System.ServiceModel.NetTcpBinding> class; in configuration, use the [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>

<span data-ttu-id="2767a-163">此绑定针对计算机之间的通信进行了优化。</span><span class="sxs-lookup"><span data-stu-id="2767a-163">This binding is optimized for cross-machine communication.</span></span> <span data-ttu-id="2767a-164">默认情况下，它具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="2767a-164">By default, it has the following characteristics:</span></span>

- <span data-ttu-id="2767a-165">实现传输层安全性。</span><span class="sxs-lookup"><span data-stu-id="2767a-165">Implements transport-layer security.</span></span>

- <span data-ttu-id="2767a-166">利用 Windows 安全性来实现传送安全性和身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-166">Leverages Windows security for transfer security and authentication.</span></span>

- <span data-ttu-id="2767a-167">使用 TCP 进行传输。</span><span class="sxs-lookup"><span data-stu-id="2767a-167">Uses TCP for transport.</span></span>

- <span data-ttu-id="2767a-168">实现二进制消息编码。</span><span class="sxs-lookup"><span data-stu-id="2767a-168">Implements binary message encoding.</span></span>

- <span data-ttu-id="2767a-169">实现 WS-Reliable Messaging。</span><span class="sxs-lookup"><span data-stu-id="2767a-169">Implements WS-Reliable Messaging.</span></span>

<span data-ttu-id="2767a-170">此绑定具有下列选项：</span><span class="sxs-lookup"><span data-stu-id="2767a-170">Options include the following:</span></span>

- <span data-ttu-id="2767a-171">消息层安全性（使用 WS-Security）。</span><span class="sxs-lookup"><span data-stu-id="2767a-171">Message-layer security (using WS-Security).</span></span>

- <span data-ttu-id="2767a-172">使用消息凭据实现传输安全性：保密性和完整性由 Transport Layer Security (TLS) over TCP 提供，授权凭据由 WS-Security 提供。</span><span class="sxs-lookup"><span data-stu-id="2767a-172">Transport security with message credential—confidentiality and integrity provided by Transport Layer Security (TLS) over TCP, and credentials for authorization provided by WS-Security.</span></span>

<span data-ttu-id="2767a-173">有关详细信息，请参阅 <xref:System.ServiceModel.NetTcpSecurity> 、、 <xref:System.ServiceModel.TcpTransportSecurity> <xref:System.ServiceModel.TcpClientCredentialType> 、 <xref:System.ServiceModel.MessageSecurityOverTcp> 和 <xref:System.ServiceModel.MessageCredentialType> 。</span><span class="sxs-lookup"><span data-stu-id="2767a-173">For more information, see <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>, and <xref:System.ServiceModel.MessageCredentialType>.</span></span>

### <a name="netnamedpipebinding"></a><span data-ttu-id="2767a-174">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="2767a-174">NetNamedPipeBinding</span></span>

<span data-ttu-id="2767a-175">在代码中，使用 <xref:System.ServiceModel.NetNamedPipeBinding> 类; 在配置中，使用 [\<netNamedPipeBinding>](../../configure-apps/file-schema/wcf/netnamedpipebinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2767a-175">In code, use the <xref:System.ServiceModel.NetNamedPipeBinding> class; in configuration, use the [\<netNamedPipeBinding>](../../configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>

<span data-ttu-id="2767a-176">此绑定针对进程之间的通信（通常在同一台计算机上）进行了优化。</span><span class="sxs-lookup"><span data-stu-id="2767a-176">This binding is optimized for cross-process communication (usually on the same machine).</span></span> <span data-ttu-id="2767a-177">默认情况下，此绑定具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="2767a-177">By default, this binding has the following characteristics:</span></span>

- <span data-ttu-id="2767a-178">使用传输安全性来实现消息传输和身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-178">Uses transport security for message transfer and authentication.</span></span>

- <span data-ttu-id="2767a-179">使用命名管道进行消息传递。</span><span class="sxs-lookup"><span data-stu-id="2767a-179">Uses named pipes for message delivery.</span></span>

- <span data-ttu-id="2767a-180">实现二进制消息编码。</span><span class="sxs-lookup"><span data-stu-id="2767a-180">Implements binary message encoding.</span></span>

- <span data-ttu-id="2767a-181">加密和消息签名。</span><span class="sxs-lookup"><span data-stu-id="2767a-181">Encryption and message signing.</span></span>

<span data-ttu-id="2767a-182">此绑定具有下列选项：</span><span class="sxs-lookup"><span data-stu-id="2767a-182">Options include the following:</span></span>

- <span data-ttu-id="2767a-183">使用 Windows 安全性进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-183">Authentication using Windows security.</span></span>

<span data-ttu-id="2767a-184">有关详细信息，请参阅<xref:System.ServiceModel.NetNamedPipeSecurity>、<xref:System.ServiceModel.NetNamedPipeSecurityMode>和<xref:System.ServiceModel.NamedPipeTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="2767a-184">For more information, see <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode>, and <xref:System.ServiceModel.NamedPipeTransportSecurity>.</span></span>

### <a name="msmqintegrationbinding"></a><span data-ttu-id="2767a-185">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="2767a-185">MsmqIntegrationBinding</span></span>

<span data-ttu-id="2767a-186">在代码中，使用 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 类; 在配置中，使用 [\<msmqIntegrationBinding>](../../configure-apps/file-schema/wcf/msmqintegrationbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2767a-186">In code, use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> class; in configuration, use the [\<msmqIntegrationBinding>](../../configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>

<span data-ttu-id="2767a-187">此绑定经过优化，可用于创建与非 WCF Microsoft 消息队列（MSMQ）终结点互操作的 WCF 客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="2767a-187">This binding is optimized for creating WCF clients and services that interoperate with non-WCF Microsoft Message Queuing (MSMQ) endpoints.</span></span>

<span data-ttu-id="2767a-188">默认情况下，此绑定使用传输安全性并提供下列安全特征：</span><span class="sxs-lookup"><span data-stu-id="2767a-188">By default, this binding uses transport security and provides the following security characteristics:</span></span>

- <span data-ttu-id="2767a-189">可以禁用安全性 (None)。</span><span class="sxs-lookup"><span data-stu-id="2767a-189">Security can be disabled (None).</span></span>

- <span data-ttu-id="2767a-190">MSMQ 传输安全性 (Transport)。</span><span class="sxs-lookup"><span data-stu-id="2767a-190">MSMQ transport security (Transport).</span></span>

<span data-ttu-id="2767a-191">有关详细信息，请参阅 <xref:System.ServiceModel.NetMsmqSecurity> 和 <xref:System.ServiceModel.NetMsmqSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="2767a-191">For more information, see <xref:System.ServiceModel.NetMsmqSecurity> and <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>

### <a name="netmsmqbinding"></a><span data-ttu-id="2767a-192">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="2767a-192">NetMsmqBinding</span></span>

<span data-ttu-id="2767a-193">在代码中，使用 <xref:System.ServiceModel.NetMsmqBinding> 类; 在配置中，使用 [\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2767a-193">In code, use the <xref:System.ServiceModel.NetMsmqBinding> class; in configuration, use the [\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md).</span></span>

<span data-ttu-id="2767a-194">此绑定用于创建需要 MSMQ 排队消息支持的 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="2767a-194">This binding is intended for use when creating WCF services that require MSMQ queued message support.</span></span>

<span data-ttu-id="2767a-195">默认情况下，此绑定使用传输安全性并提供下列安全特征：</span><span class="sxs-lookup"><span data-stu-id="2767a-195">By default, this binding uses transport security and provides the following security characteristics:</span></span>

- <span data-ttu-id="2767a-196">可以禁用安全性 (None)。</span><span class="sxs-lookup"><span data-stu-id="2767a-196">Security can be disabled (None).</span></span>

- <span data-ttu-id="2767a-197">MSMQ 传输安全性 (Transport)。</span><span class="sxs-lookup"><span data-stu-id="2767a-197">MSMQ transport security (Transport).</span></span>

- <span data-ttu-id="2767a-198">基于 SOAP 的消息安全性 (Message)。</span><span class="sxs-lookup"><span data-stu-id="2767a-198">SOAP-based message security (Message).</span></span>

- <span data-ttu-id="2767a-199">同时启用传输安全性和消息安全性 (Both)。</span><span class="sxs-lookup"><span data-stu-id="2767a-199">Simultaneous Transport and Message security (Both).</span></span>

- <span data-ttu-id="2767a-200">支持的客户端凭据类型：None、Windows、UserName、Certificate、IssuedToken。</span><span class="sxs-lookup"><span data-stu-id="2767a-200">Client Credential Types supported: None, Windows, UserName, Certificate, IssuedToken.</span></span>

<span data-ttu-id="2767a-201">仅当安全模式设置为 <xref:System.ServiceModel.MessageCredentialType.Certificate> 或 <xref:System.ServiceModel.NetMsmqSecurityMode.Both> 时，才支持 <xref:System.ServiceModel.NetMsmqSecurityMode.Message> 凭据。</span><span class="sxs-lookup"><span data-stu-id="2767a-201">The <xref:System.ServiceModel.MessageCredentialType.Certificate> credential is supported only when the security mode is set to either <xref:System.ServiceModel.NetMsmqSecurityMode.Both> or <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.</span></span>

<span data-ttu-id="2767a-202">有关详细信息，请参阅 <xref:System.ServiceModel.MessageSecurityOverMsmq> 和 <xref:System.ServiceModel.MsmqTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="2767a-202">For more information, see <xref:System.ServiceModel.MessageSecurityOverMsmq> and <xref:System.ServiceModel.MsmqTransportSecurity>.</span></span>

### <a name="wsfederationhttpbinding"></a><span data-ttu-id="2767a-203">WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2767a-203">WSFederationHttpBinding</span></span>

<span data-ttu-id="2767a-204">在代码中，使用 <xref:System.ServiceModel.WSFederationHttpBinding> 类; 在配置中，使用 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2767a-204">In code, use the <xref:System.ServiceModel.WSFederationHttpBinding> class; in configuration, use the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>

<span data-ttu-id="2767a-205">默认情况下，此绑定使用 WS-Security（消息层安全性）。</span><span class="sxs-lookup"><span data-stu-id="2767a-205">By default, this binding uses WS-Security (message-layer security).</span></span>

<span data-ttu-id="2767a-206">有关详细信息，请参阅[联合](federation.md)、 <xref:System.ServiceModel.WSFederationHttpSecurity> 和 <xref:System.ServiceModel.WSFederationHttpSecurityMode> 。</span><span class="sxs-lookup"><span data-stu-id="2767a-206">For more information, see [Federation](federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, and <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="2767a-207">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="2767a-207">Custom Bindings</span></span>

<span data-ttu-id="2767a-208">如果系统提供的绑定都不能满足您的需求，则可以使用自定义安全绑定元素来创建自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="2767a-208">If none of the system-provided bindings meets you requirements, you can create a custom binding with a custom security binding element.</span></span> <span data-ttu-id="2767a-209">有关详细信息，请参阅[具有自定义绑定的安全功能](security-capabilities-with-custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="2767a-209">For more information, see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md).</span></span>

## <a name="binding-choices"></a><span data-ttu-id="2767a-210">绑定选择</span><span class="sxs-lookup"><span data-stu-id="2767a-210">Binding Choices</span></span>

<span data-ttu-id="2767a-211">下表概括了安全模式设置中提供的功能，也就是说，它列出了当安全模式设置为 `Transport`、`Message` 或 `TransportWithMessageCredential` 时可以使用的功能。</span><span class="sxs-lookup"><span data-stu-id="2767a-211">The following table summarizes the features offered in the security mode setting, that is, it lists the features available when the security mode is set to `Transport`, `Message`, or `TransportWithMessageCredential`.</span></span> <span data-ttu-id="2767a-212">使用此表可帮助您找到应用程序所需的安全功能。</span><span class="sxs-lookup"><span data-stu-id="2767a-212">Use this table to help you find the security features your application requires.</span></span>

|<span data-ttu-id="2767a-213">设置</span><span class="sxs-lookup"><span data-stu-id="2767a-213">Setting</span></span>|<span data-ttu-id="2767a-214">功能</span><span class="sxs-lookup"><span data-stu-id="2767a-214">Features</span></span>|
|-------------|--------------|
|<span data-ttu-id="2767a-215">传输</span><span class="sxs-lookup"><span data-stu-id="2767a-215">Transport</span></span>|<span data-ttu-id="2767a-216">服务器身份验证</span><span class="sxs-lookup"><span data-stu-id="2767a-216">Server authentication</span></span><br /><br /> <span data-ttu-id="2767a-217">客户端身份验证</span><span class="sxs-lookup"><span data-stu-id="2767a-217">Client authentication</span></span><br /><br /> <span data-ttu-id="2767a-218">点对点安全性</span><span class="sxs-lookup"><span data-stu-id="2767a-218">Point-to-point security</span></span><br /><br /> <span data-ttu-id="2767a-219">互操作性</span><span class="sxs-lookup"><span data-stu-id="2767a-219">Interoperability</span></span><br /><br /> <span data-ttu-id="2767a-220">硬件加速</span><span class="sxs-lookup"><span data-stu-id="2767a-220">Hardware acceleration</span></span><br /><br /> <span data-ttu-id="2767a-221">高吞吐量</span><span class="sxs-lookup"><span data-stu-id="2767a-221">High throughput</span></span><br /><br /> <span data-ttu-id="2767a-222">安全防火墙</span><span class="sxs-lookup"><span data-stu-id="2767a-222">Secure firewall</span></span><br /><br /> <span data-ttu-id="2767a-223">高延迟应用程序</span><span class="sxs-lookup"><span data-stu-id="2767a-223">High-latency applications</span></span><br /><br /> <span data-ttu-id="2767a-224">跨越多个跃点重新加密</span><span class="sxs-lookup"><span data-stu-id="2767a-224">Re-encryption across multiple hops</span></span>|
|<span data-ttu-id="2767a-225">消息</span><span class="sxs-lookup"><span data-stu-id="2767a-225">Message</span></span>|<span data-ttu-id="2767a-226">服务器身份验证</span><span class="sxs-lookup"><span data-stu-id="2767a-226">Server authentication</span></span><br /><br /> <span data-ttu-id="2767a-227">客户端身份验证</span><span class="sxs-lookup"><span data-stu-id="2767a-227">Client authentication</span></span><br /><br /> <span data-ttu-id="2767a-228">端到端安全性</span><span class="sxs-lookup"><span data-stu-id="2767a-228">End-to-end security</span></span><br /><br /> <span data-ttu-id="2767a-229">互操作性</span><span class="sxs-lookup"><span data-stu-id="2767a-229">Interoperability</span></span><br /><br /> <span data-ttu-id="2767a-230">丰富的声明</span><span class="sxs-lookup"><span data-stu-id="2767a-230">Rich claims</span></span><br /><br /> <span data-ttu-id="2767a-231">联合</span><span class="sxs-lookup"><span data-stu-id="2767a-231">Federation</span></span><br /><br /> <span data-ttu-id="2767a-232">多重身份验证</span><span class="sxs-lookup"><span data-stu-id="2767a-232">Multifactor authentication</span></span><br /><br /> <span data-ttu-id="2767a-233">自定义令牌</span><span class="sxs-lookup"><span data-stu-id="2767a-233">Custom tokens</span></span><br /><br /> <span data-ttu-id="2767a-234">公证人/时间戳服务</span><span class="sxs-lookup"><span data-stu-id="2767a-234">Notary/timestamp service</span></span><br /><br /> <span data-ttu-id="2767a-235">高延迟应用程序</span><span class="sxs-lookup"><span data-stu-id="2767a-235">High-latency applications</span></span><br /><br /> <span data-ttu-id="2767a-236">消息签名的持久性</span><span class="sxs-lookup"><span data-stu-id="2767a-236">Persistence of message signatures</span></span>|
|<span data-ttu-id="2767a-237">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="2767a-237">TransportWithMessageCredential</span></span>|<span data-ttu-id="2767a-238">服务器身份验证</span><span class="sxs-lookup"><span data-stu-id="2767a-238">Server authentication</span></span><br /><br /> <span data-ttu-id="2767a-239">客户端身份验证</span><span class="sxs-lookup"><span data-stu-id="2767a-239">Client authentication</span></span><br /><br /> <span data-ttu-id="2767a-240">点对点安全性</span><span class="sxs-lookup"><span data-stu-id="2767a-240">Point-to-point security</span></span><br /><br /> <span data-ttu-id="2767a-241">互操作性</span><span class="sxs-lookup"><span data-stu-id="2767a-241">Interoperability</span></span><br /><br /> <span data-ttu-id="2767a-242">硬件加速</span><span class="sxs-lookup"><span data-stu-id="2767a-242">Hardware acceleration</span></span><br /><br /> <span data-ttu-id="2767a-243">高吞吐量</span><span class="sxs-lookup"><span data-stu-id="2767a-243">High throughput</span></span><br /><br /> <span data-ttu-id="2767a-244">丰富的客户端声明</span><span class="sxs-lookup"><span data-stu-id="2767a-244">Rich client claims</span></span><br /><br /> <span data-ttu-id="2767a-245">联合</span><span class="sxs-lookup"><span data-stu-id="2767a-245">Federation</span></span><br /><br /> <span data-ttu-id="2767a-246">多重身份验证</span><span class="sxs-lookup"><span data-stu-id="2767a-246">Multifactor authentication</span></span><br /><br /> <span data-ttu-id="2767a-247">自定义令牌</span><span class="sxs-lookup"><span data-stu-id="2767a-247">Custom tokens</span></span><br /><br /> <span data-ttu-id="2767a-248">安全防火墙</span><span class="sxs-lookup"><span data-stu-id="2767a-248">Secure firewall</span></span><br /><br /> <span data-ttu-id="2767a-249">高延迟应用程序</span><span class="sxs-lookup"><span data-stu-id="2767a-249">High-latency applications</span></span><br /><br /> <span data-ttu-id="2767a-250">跨越多个跃点重新加密</span><span class="sxs-lookup"><span data-stu-id="2767a-250">Re-encryption across multiple hops</span></span>|

<span data-ttu-id="2767a-251">下表列出了支持各种模式设置的绑定。</span><span class="sxs-lookup"><span data-stu-id="2767a-251">The following table lists the bindings that support the various mode settings.</span></span> <span data-ttu-id="2767a-252">请从该表中选择用来创建服务终结点的绑定。</span><span class="sxs-lookup"><span data-stu-id="2767a-252">Select a binding from the table to use to create your service endpoint.</span></span>

|<span data-ttu-id="2767a-253">绑定</span><span class="sxs-lookup"><span data-stu-id="2767a-253">Binding</span></span>|<span data-ttu-id="2767a-254">是否支持 Transport 模式</span><span class="sxs-lookup"><span data-stu-id="2767a-254">Transport mode support</span></span>|<span data-ttu-id="2767a-255">是否支持 Message 模式</span><span class="sxs-lookup"><span data-stu-id="2767a-255">Message mode support</span></span>|<span data-ttu-id="2767a-256">是否支持 TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="2767a-256">TransportWithMessageCredential support</span></span>|
|-------------|----------------------------|--------------------------|--------------------------------------------|
|`BasicHttpBinding`|<span data-ttu-id="2767a-257">是</span><span class="sxs-lookup"><span data-stu-id="2767a-257">Yes</span></span>|<span data-ttu-id="2767a-258">是</span><span class="sxs-lookup"><span data-stu-id="2767a-258">Yes</span></span>|<span data-ttu-id="2767a-259">是</span><span class="sxs-lookup"><span data-stu-id="2767a-259">Yes</span></span>|
|`WSHttpBinding`|<span data-ttu-id="2767a-260">是</span><span class="sxs-lookup"><span data-stu-id="2767a-260">Yes</span></span>|<span data-ttu-id="2767a-261">是</span><span class="sxs-lookup"><span data-stu-id="2767a-261">Yes</span></span>|<span data-ttu-id="2767a-262">是</span><span class="sxs-lookup"><span data-stu-id="2767a-262">Yes</span></span>|
|`WSDualHttpBinding`|<span data-ttu-id="2767a-263">No</span><span class="sxs-lookup"><span data-stu-id="2767a-263">No</span></span>|<span data-ttu-id="2767a-264">是</span><span class="sxs-lookup"><span data-stu-id="2767a-264">Yes</span></span>|<span data-ttu-id="2767a-265">No</span><span class="sxs-lookup"><span data-stu-id="2767a-265">No</span></span>|
|`NetTcpBinding`|<span data-ttu-id="2767a-266">是</span><span class="sxs-lookup"><span data-stu-id="2767a-266">Yes</span></span>|<span data-ttu-id="2767a-267">是</span><span class="sxs-lookup"><span data-stu-id="2767a-267">Yes</span></span>|<span data-ttu-id="2767a-268">是</span><span class="sxs-lookup"><span data-stu-id="2767a-268">Yes</span></span>|
|`NetNamedPipeBinding`|<span data-ttu-id="2767a-269">是</span><span class="sxs-lookup"><span data-stu-id="2767a-269">Yes</span></span>|<span data-ttu-id="2767a-270">No</span><span class="sxs-lookup"><span data-stu-id="2767a-270">No</span></span>|<span data-ttu-id="2767a-271">否</span><span class="sxs-lookup"><span data-stu-id="2767a-271">No</span></span>|
|`NetMsmqBinding`|<span data-ttu-id="2767a-272">是</span><span class="sxs-lookup"><span data-stu-id="2767a-272">Yes</span></span>|<span data-ttu-id="2767a-273">是</span><span class="sxs-lookup"><span data-stu-id="2767a-273">Yes</span></span>|<span data-ttu-id="2767a-274">No</span><span class="sxs-lookup"><span data-stu-id="2767a-274">No</span></span>|
|`MsmqIntegrationBinding`|<span data-ttu-id="2767a-275">是</span><span class="sxs-lookup"><span data-stu-id="2767a-275">Yes</span></span>|<span data-ttu-id="2767a-276">No</span><span class="sxs-lookup"><span data-stu-id="2767a-276">No</span></span>|<span data-ttu-id="2767a-277">否</span><span class="sxs-lookup"><span data-stu-id="2767a-277">No</span></span>|
|`wsFederationHttpBinding`|<span data-ttu-id="2767a-278">否</span><span class="sxs-lookup"><span data-stu-id="2767a-278">No</span></span>|<span data-ttu-id="2767a-279">是</span><span class="sxs-lookup"><span data-stu-id="2767a-279">Yes</span></span>|<span data-ttu-id="2767a-280">是</span><span class="sxs-lookup"><span data-stu-id="2767a-280">Yes</span></span>|

## <a name="transport-credentials-in-bindings"></a><span data-ttu-id="2767a-281">绑定中的传输凭据</span><span class="sxs-lookup"><span data-stu-id="2767a-281">Transport Credentials in Bindings</span></span>

<span data-ttu-id="2767a-282">下表列出了在传输安全模式下使用 `BasicHttpBinding` 或 `WSHttpBinding` 时可用的客户端凭据类型。</span><span class="sxs-lookup"><span data-stu-id="2767a-282">The following table lists the client credential types available when using either `BasicHttpBinding` or `WSHttpBinding` in transport security mode.</span></span>

|<span data-ttu-id="2767a-283">类型</span><span class="sxs-lookup"><span data-stu-id="2767a-283">Type</span></span>|<span data-ttu-id="2767a-284">说明</span><span class="sxs-lookup"><span data-stu-id="2767a-284">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="2767a-285">无</span><span class="sxs-lookup"><span data-stu-id="2767a-285">None</span></span>|<span data-ttu-id="2767a-286">指定客户端不需要提供任何凭据。</span><span class="sxs-lookup"><span data-stu-id="2767a-286">Specifies that the client does not need to present any credential.</span></span> <span data-ttu-id="2767a-287">这相当于匿名客户端。</span><span class="sxs-lookup"><span data-stu-id="2767a-287">This translates to an anonymous client.</span></span>|
|<span data-ttu-id="2767a-288">基本</span><span class="sxs-lookup"><span data-stu-id="2767a-288">Basic</span></span>|<span data-ttu-id="2767a-289">基本身份验证</span><span class="sxs-lookup"><span data-stu-id="2767a-289">Basic authentication.</span></span> <span data-ttu-id="2767a-290">有关详细信息，请参阅 RFC 2617 – HTTP 身份验证：基本和摘要式身份验证，可在 <https://go.microsoft.com/fwlink/?LinkId=84023> 。</span><span class="sxs-lookup"><span data-stu-id="2767a-290">For more information, see RFC 2617 – HTTP Authentication: Basic and Digest Authentication, available at <https://go.microsoft.com/fwlink/?LinkId=84023>.</span></span>|
|<span data-ttu-id="2767a-291">摘要</span><span class="sxs-lookup"><span data-stu-id="2767a-291">Digest</span></span>|<span data-ttu-id="2767a-292">摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-292">Digest authentication.</span></span> <span data-ttu-id="2767a-293">有关详细信息，请参阅 RFC 2617 – HTTP 身份验证：基本和摘要式身份验证，可在 <https://go.microsoft.com/fwlink/?LinkId=84023> 。</span><span class="sxs-lookup"><span data-stu-id="2767a-293">For more information, see RFC 2617 – HTTP Authentication: Basic and Digest Authentication, available at <https://go.microsoft.com/fwlink/?LinkId=84023>.</span></span>|
|<span data-ttu-id="2767a-294">NTLM</span><span class="sxs-lookup"><span data-stu-id="2767a-294">NTLM</span></span>|<span data-ttu-id="2767a-295">NT LAN Manager (NTLM) 身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-295">NT LAN Manager (NTLM) authentication.</span></span>|
|<span data-ttu-id="2767a-296">Windows</span><span class="sxs-lookup"><span data-stu-id="2767a-296">Windows</span></span>|<span data-ttu-id="2767a-297">Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-297">Windows authentication.</span></span>|
|<span data-ttu-id="2767a-298">证书</span><span class="sxs-lookup"><span data-stu-id="2767a-298">Certificate</span></span>|<span data-ttu-id="2767a-299">使用证书执行的身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-299">Authentication performed using a certificate.</span></span>|
|<span data-ttu-id="2767a-300">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="2767a-300">IssuedToken</span></span>|<span data-ttu-id="2767a-301">允许服务要求使用由 security token service 或 CardSpace 颁发的令牌对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-301">Allows the service to require that the client be authenticated using a token issued by a security token service or by CardSpace.</span></span> <span data-ttu-id="2767a-302">有关详细信息，请参阅[联合和颁发的令牌](federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="2767a-302">For more information, see [Federation and Issued Tokens](federation-and-issued-tokens.md).</span></span>|

### <a name="message-client-credentials-in-bindings"></a><span data-ttu-id="2767a-303">绑定中的消息客户端凭据</span><span class="sxs-lookup"><span data-stu-id="2767a-303">Message Client Credentials in Bindings</span></span>

<span data-ttu-id="2767a-304">下表列出在 Message 安全模式下使用绑定时可用的客户端凭据类型。</span><span class="sxs-lookup"><span data-stu-id="2767a-304">The following table lists the client credential types available when using a binding in Message security mode.</span></span>

|<span data-ttu-id="2767a-305">类型</span><span class="sxs-lookup"><span data-stu-id="2767a-305">Type</span></span>|<span data-ttu-id="2767a-306">说明</span><span class="sxs-lookup"><span data-stu-id="2767a-306">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="2767a-307">无</span><span class="sxs-lookup"><span data-stu-id="2767a-307">None</span></span>|<span data-ttu-id="2767a-308">允许服务与匿名客户端交互。</span><span class="sxs-lookup"><span data-stu-id="2767a-308">Allows the service to interact with anonymous clients.</span></span>|
|<span data-ttu-id="2767a-309">Windows</span><span class="sxs-lookup"><span data-stu-id="2767a-309">Windows</span></span>|<span data-ttu-id="2767a-310">允许在 Windows 凭据的已通过身份验证的上下文中执行 SOAP 消息交换。</span><span class="sxs-lookup"><span data-stu-id="2767a-310">Allows SOAP message exchanges to be made under the authenticated context of a Windows credential.</span></span>|
|<span data-ttu-id="2767a-311">UserName</span><span class="sxs-lookup"><span data-stu-id="2767a-311">UserName</span></span>|<span data-ttu-id="2767a-312">允许服务要求使用用户名凭据对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-312">Allows the service to require that the client be authenticated using a user name credential.</span></span> <span data-ttu-id="2767a-313">请注意，当安全模式设置为时 `TransportWithMessageCredential` ，WCF 不支持发送密码摘要，也不支持使用密码派生密钥并使用此类密钥进行消息模式安全性。</span><span class="sxs-lookup"><span data-stu-id="2767a-313">Note that when the security mode is set to `TransportWithMessageCredential`, WCF does not support sending a password digest or deriving keys using password and using such keys for Message mode security.</span></span> <span data-ttu-id="2767a-314">因此，在使用用户名凭据时，WCF 会强制保护传输。</span><span class="sxs-lookup"><span data-stu-id="2767a-314">As such, WCF enforces that the transport is secured when using user name credentials.</span></span>|
|<span data-ttu-id="2767a-315">证书</span><span class="sxs-lookup"><span data-stu-id="2767a-315">Certificate</span></span>|<span data-ttu-id="2767a-316">允许服务要求使用证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2767a-316">Allows the service to require that the client be authenticated using a certificate.</span></span>|
|<span data-ttu-id="2767a-317">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="2767a-317">IssuedToken</span></span>|<span data-ttu-id="2767a-318">允许服务使用安全令牌服务来提供自定义令牌。</span><span class="sxs-lookup"><span data-stu-id="2767a-318">Allows the service to use a security token service to supply a custom token.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2767a-319">请参阅</span><span class="sxs-lookup"><span data-stu-id="2767a-319">See also</span></span>

- [<span data-ttu-id="2767a-320">安全性概述</span><span class="sxs-lookup"><span data-stu-id="2767a-320">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="2767a-321">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="2767a-321">Securing Services and Clients</span></span>](securing-services-and-clients.md)
- [<span data-ttu-id="2767a-322">选择凭据类型</span><span class="sxs-lookup"><span data-stu-id="2767a-322">Selecting a Credential Type</span></span>](selecting-a-credential-type.md)
- [<span data-ttu-id="2767a-323">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="2767a-323">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="2767a-324">安全行为</span><span class="sxs-lookup"><span data-stu-id="2767a-324">Security Behaviors</span></span>](security-behaviors-in-wcf.md)
- <span data-ttu-id="2767a-325">[Windows Server App Fabric 的安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2767a-325">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
