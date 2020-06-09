---
title: 调试 Windows 身份验证错误
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: eb3274b98234324bd47aa456feb4845da5a7f3a9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599277"
---
# <a name="debug-windows-authentication-errors"></a><span data-ttu-id="f60ea-102">调试 Windows 身份验证错误</span><span class="sxs-lookup"><span data-stu-id="f60ea-102">Debug Windows authentication errors</span></span>

<span data-ttu-id="f60ea-103">使用 Windows 验证身份作为安全机制时，安全支持提供程序接口 (SSPI) 将处理安全进程。</span><span class="sxs-lookup"><span data-stu-id="f60ea-103">When using Windows authentication as a security mechanism, the Security Support Provider Interface (SSPI) handles security processes.</span></span> <span data-ttu-id="f60ea-104">当 SSPI 层发生安全错误时，它们将由 Windows Communication Foundation （WCF）呈现。</span><span class="sxs-lookup"><span data-stu-id="f60ea-104">When security errors occur at the SSPI layer, they are surfaced by Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f60ea-105">本主题提供一组问题以帮助诊断这些错误。</span><span class="sxs-lookup"><span data-stu-id="f60ea-105">This topic provides a framework and set of questions to help diagnose the errors.</span></span>  
  
 <span data-ttu-id="f60ea-106">有关 Kerberos 协议的概述，请参阅[Kerberos 说明](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10));有关 SSPI 的概述，请参阅[sspi](/windows/win32/secauthn/sspi)。</span><span class="sxs-lookup"><span data-stu-id="f60ea-106">For an overview of the Kerberos protocol, see [Kerberos Explained](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10)); for an overview of SSPI, see [SSPI](/windows/win32/secauthn/sspi).</span></span>  
  
 <span data-ttu-id="f60ea-107">对于 Windows 身份验证，WCF 通常使用*Negotiate*安全支持提供程序（SSP），该提供程序在客户端和服务之间执行 Kerberos 相互身份验证。</span><span class="sxs-lookup"><span data-stu-id="f60ea-107">For Windows authentication, WCF typically uses the *Negotiate* Security Support Provider (SSP), which performs Kerberos mutual authentication between the client and service.</span></span> <span data-ttu-id="f60ea-108">如果 Kerberos 协议不可用，则默认情况下，WCF 将回退到 NT LAN Manager （NTLM）。</span><span class="sxs-lookup"><span data-stu-id="f60ea-108">If the Kerberos protocol is not available, by default WCF falls back to NT LAN Manager (NTLM).</span></span> <span data-ttu-id="f60ea-109">但是，你可以将 WCF 配置为仅使用 Kerberos 协议（如果 Kerberos 不可用，则会引发异常）。</span><span class="sxs-lookup"><span data-stu-id="f60ea-109">However, you can configure WCF to use only the Kerberos protocol (and to throw an exception if Kerberos is not available).</span></span> <span data-ttu-id="f60ea-110">你还可以将 WCF 配置为使用受限形式的 Kerberos 协议。</span><span class="sxs-lookup"><span data-stu-id="f60ea-110">You can also configure WCF to use restricted forms of the Kerberos protocol.</span></span>  
  
## <a name="debugging-methodology"></a><span data-ttu-id="f60ea-111">调试方法</span><span class="sxs-lookup"><span data-stu-id="f60ea-111">Debugging Methodology</span></span>  
 <span data-ttu-id="f60ea-112">基本方法如下所述：</span><span class="sxs-lookup"><span data-stu-id="f60ea-112">The basic method is as follows:</span></span>  
  
1. <span data-ttu-id="f60ea-113">确定您是否正在使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f60ea-113">Determine whether you are using Windows authentication.</span></span> <span data-ttu-id="f60ea-114">如果您正在使用任何其他方案，则本主题不适用。</span><span class="sxs-lookup"><span data-stu-id="f60ea-114">If you are using any other scheme, this topic does not apply.</span></span>  
  
2. <span data-ttu-id="f60ea-115">如果你确定使用的是 Windows 身份验证，请确定你的 WCF 配置是使用 Kerberos direct 还是 Negotiate。</span><span class="sxs-lookup"><span data-stu-id="f60ea-115">If you are sure you are using Windows authentication, determine whether your WCF configuration uses Kerberos direct or Negotiate.</span></span>  
  
3. <span data-ttu-id="f60ea-116">确定了配置是使用 Kerberos 协议还是 NTLM 后，您可以在正确的上下文中理解错误消息。</span><span class="sxs-lookup"><span data-stu-id="f60ea-116">Once you have determined whether your configuration is using the Kerberos protocol or NTLM, you can understand error messages in the correct context.</span></span>  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a><span data-ttu-id="f60ea-117">Kerberos 协议和 NTLM 的可用性</span><span class="sxs-lookup"><span data-stu-id="f60ea-117">Availability of the Kerberos Protocol and NTLM</span></span>  
 <span data-ttu-id="f60ea-118">Kerberos SSP 要求域控制器作为 Kerberos 密钥发行中心 (KDC)。</span><span class="sxs-lookup"><span data-stu-id="f60ea-118">The Kerberos SSP requires a domain controller to act as the Kerberos Key Distribution Center (KDC).</span></span> <span data-ttu-id="f60ea-119">只有在客户端和服务都使用域标识时，Kerberos 协议才可用。</span><span class="sxs-lookup"><span data-stu-id="f60ea-119">The Kerberos protocol is available only when both the client and service are using domain identities.</span></span> <span data-ttu-id="f60ea-120">在其他帐户组合中，将使用 NTLM，如下表摘要所示。</span><span class="sxs-lookup"><span data-stu-id="f60ea-120">In other account combinations, NTLM is used, as summarized in the following table.</span></span>  
  
 <span data-ttu-id="f60ea-121">表的标题显示服务器可能使用的帐户类型。</span><span class="sxs-lookup"><span data-stu-id="f60ea-121">The table headers show possible account types used by the server.</span></span> <span data-ttu-id="f60ea-122">左列显示客户端可能使用的帐户类型。</span><span class="sxs-lookup"><span data-stu-id="f60ea-122">The left column shows possible account types used by the client.</span></span>  
  
||<span data-ttu-id="f60ea-123">本地用户</span><span class="sxs-lookup"><span data-stu-id="f60ea-123">Local User</span></span>|<span data-ttu-id="f60ea-124">Local System</span><span class="sxs-lookup"><span data-stu-id="f60ea-124">Local System</span></span>|<span data-ttu-id="f60ea-125">域用户</span><span class="sxs-lookup"><span data-stu-id="f60ea-125">Domain User</span></span>|<span data-ttu-id="f60ea-126">域计算机</span><span class="sxs-lookup"><span data-stu-id="f60ea-126">Domain Machine</span></span>|  
|-|----------------|------------------|-----------------|--------------------|  
|<span data-ttu-id="f60ea-127">本地用户</span><span class="sxs-lookup"><span data-stu-id="f60ea-127">Local User</span></span>|<span data-ttu-id="f60ea-128">NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-128">NTLM</span></span>|<span data-ttu-id="f60ea-129">NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-129">NTLM</span></span>|<span data-ttu-id="f60ea-130">NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-130">NTLM</span></span>|<span data-ttu-id="f60ea-131">NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-131">NTLM</span></span>|  
|<span data-ttu-id="f60ea-132">Local System</span><span class="sxs-lookup"><span data-stu-id="f60ea-132">Local System</span></span>|<span data-ttu-id="f60ea-133">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-133">Anonymous NTLM</span></span>|<span data-ttu-id="f60ea-134">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-134">Anonymous NTLM</span></span>|<span data-ttu-id="f60ea-135">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-135">Anonymous NTLM</span></span>|<span data-ttu-id="f60ea-136">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-136">Anonymous NTLM</span></span>|  
|<span data-ttu-id="f60ea-137">域用户</span><span class="sxs-lookup"><span data-stu-id="f60ea-137">Domain User</span></span>|<span data-ttu-id="f60ea-138">NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-138">NTLM</span></span>|<span data-ttu-id="f60ea-139">NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-139">NTLM</span></span>|<span data-ttu-id="f60ea-140">Kerberos</span><span class="sxs-lookup"><span data-stu-id="f60ea-140">Kerberos</span></span>|<span data-ttu-id="f60ea-141">Kerberos</span><span class="sxs-lookup"><span data-stu-id="f60ea-141">Kerberos</span></span>|  
|<span data-ttu-id="f60ea-142">域计算机</span><span class="sxs-lookup"><span data-stu-id="f60ea-142">Domain Machine</span></span>|<span data-ttu-id="f60ea-143">NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-143">NTLM</span></span>|<span data-ttu-id="f60ea-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="f60ea-144">NTLM</span></span>|<span data-ttu-id="f60ea-145">Kerberos</span><span class="sxs-lookup"><span data-stu-id="f60ea-145">Kerberos</span></span>|<span data-ttu-id="f60ea-146">Kerberos</span><span class="sxs-lookup"><span data-stu-id="f60ea-146">Kerberos</span></span>|  
  
 <span data-ttu-id="f60ea-147">具体地说，四种帐户类型包括：</span><span class="sxs-lookup"><span data-stu-id="f60ea-147">Specifically, the four account types include:</span></span>  
  
- <span data-ttu-id="f60ea-148">本地用户：仅计算机用户配置文件。</span><span class="sxs-lookup"><span data-stu-id="f60ea-148">Local User: Machine-only user profile.</span></span> <span data-ttu-id="f60ea-149">例如： `MachineName\Administrator` 或 `MachineName\ProfileName` 。</span><span class="sxs-lookup"><span data-stu-id="f60ea-149">For example: `MachineName\Administrator` or `MachineName\ProfileName`.</span></span>  
  
- <span data-ttu-id="f60ea-150">本地系统：未加入域的计算机上的内置帐户 SYSTEM。</span><span class="sxs-lookup"><span data-stu-id="f60ea-150">Local System: The built-in account SYSTEM on a machine that is not joined to a domain.</span></span>  
  
- <span data-ttu-id="f60ea-151">域用户：Windows 域中的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="f60ea-151">Domain User: A user account on a Windows domain.</span></span> <span data-ttu-id="f60ea-152">例如：`DomainName\ProfileName`。</span><span class="sxs-lookup"><span data-stu-id="f60ea-152">For example: `DomainName\ProfileName`.</span></span>  
  
- <span data-ttu-id="f60ea-153">域计算机：具有计算机标识并在加入 Windows 域的计算机上运行的进程。</span><span class="sxs-lookup"><span data-stu-id="f60ea-153">Domain Machine: A process with machine identity running on a machine joined to a Windows domain.</span></span> <span data-ttu-id="f60ea-154">例如：`MachineName\Network Service`。</span><span class="sxs-lookup"><span data-stu-id="f60ea-154">For example: `MachineName\Network Service`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f60ea-155">在调用 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 类的 <xref:System.ServiceModel.ServiceHost> 方法时，将捕获服务凭据。</span><span class="sxs-lookup"><span data-stu-id="f60ea-155">The service credential is captured when the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method of the <xref:System.ServiceModel.ServiceHost> class is called.</span></span> <span data-ttu-id="f60ea-156">每当客户端发送消息时，即会读取客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="f60ea-156">The client credential is read whenever the client sends a message.</span></span>  
  
## <a name="common-windows-authentication-problems"></a><span data-ttu-id="f60ea-157">常见的 Windows 身份验证问题</span><span class="sxs-lookup"><span data-stu-id="f60ea-157">Common Windows Authentication Problems</span></span>  
 <span data-ttu-id="f60ea-158">该节讨论一些常见的 Windows 身份验证问题和可能的纠正方法。</span><span class="sxs-lookup"><span data-stu-id="f60ea-158">This section discusses some common Windows authentication problems and possible remedies.</span></span>  
  
### <a name="kerberos-protocol"></a><span data-ttu-id="f60ea-159">Kerberos 协议</span><span class="sxs-lookup"><span data-stu-id="f60ea-159">Kerberos Protocol</span></span>  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a><span data-ttu-id="f60ea-160">Kerberos 协议的 SPN/UPN 问题</span><span class="sxs-lookup"><span data-stu-id="f60ea-160">SPN/UPN Problems with the Kerberos Protocol</span></span>  
 <span data-ttu-id="f60ea-161">在使用 Windows 身份验证并且 SSPI 使用或协商 Kerberos 协议时，客户端终结点使用的 URL 必须包括服务主机在服务 URL 中的完全限定域名。</span><span class="sxs-lookup"><span data-stu-id="f60ea-161">When using Windows authentication, and the Kerberos protocol is used or negotiated by SSPI, the URL the client endpoint uses must include the fully qualified domain name of the service's host inside the service URL.</span></span> <span data-ttu-id="f60ea-162">此处假定在其下运行服务的帐户可以访问将该计算机添加到 Active Directory 域中时所创建的计算机（默认）服务主体名称 (SPN) 密钥，这通常可以通过在“网络服务”帐户下运行该服务来实现。</span><span class="sxs-lookup"><span data-stu-id="f60ea-162">This assumes that the account under which the service is running has access to the machine (default) service principal name (SPN) key that is created when the computer is added to the Active Directory domain, which is most commonly done by running the service under the Network Service account.</span></span> <span data-ttu-id="f60ea-163">如果服务不能访问计算机 SPN 密钥，则必须在客户端的终结点标识中提供在其下运行该服务的帐户的正确 SPN 或用户主体名称 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="f60ea-163">If the service does not have access to the machine SPN key, you must supply the correct SPN or user principal name (UPN) of the account under which the service is running in the client's endpoint identity.</span></span> <span data-ttu-id="f60ea-164">有关 WCF 如何与 SPN 和 UPN 一起使用的详细信息，请参阅[服务标识和身份验证](service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="f60ea-164">For more information about how WCF works with SPN and UPN, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="f60ea-165">在负载平衡方案（如网络场或网络园）中，常见的做法是为每个应用程序定义唯一帐户，为该帐户分配 SPN，并确保应用程序的所有服务都使用该帐户来运行。</span><span class="sxs-lookup"><span data-stu-id="f60ea-165">In load-balancing scenarios, such as Web farms or Web gardens, a common practice is to define a unique account for each application, assign an SPN to that account, and ensure that all of the application's services run in that account.</span></span>  
  
 <span data-ttu-id="f60ea-166">为了获取服务帐户的 SPN，需要具有 Active Directory 域管理员的身份。</span><span class="sxs-lookup"><span data-stu-id="f60ea-166">To obtain an SPN for your service's account, you need to be an Active Directory domain administrator.</span></span> <span data-ttu-id="f60ea-167">有关详细信息，请参阅[适用于 Windows 的 Kerberos 技术补充](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="f60ea-167">For more information, see [Kerberos Technical Supplement for Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span>  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a><span data-ttu-id="f60ea-168">Kerberos 协议定向要求在域计算机帐户下运行服务</span><span class="sxs-lookup"><span data-stu-id="f60ea-168">Kerberos Protocol Direct Requires the Service to Run Under a Domain Machine Account</span></span>  
 <span data-ttu-id="f60ea-169">当 `ClientCredentialType` 属性设置为 `Windows` 且 <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> 属性设置为 `false` 时，会发生这种情况，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="f60ea-169">This occurs when the `ClientCredentialType` property is set to `Windows` and the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> property is set to `false`, as shown in the following code.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 <span data-ttu-id="f60ea-170">若要解决这个问题，请在加入域的计算机上使用域计算机帐户（比如“网络服务”）来运行该服务。</span><span class="sxs-lookup"><span data-stu-id="f60ea-170">To remedy, run the service using a Domain Machine account, such as Network Service, on a domain joined machine.</span></span>  
  
### <a name="delegation-requires-credential-negotiation"></a><span data-ttu-id="f60ea-171">委托要求凭据协商</span><span class="sxs-lookup"><span data-stu-id="f60ea-171">Delegation Requires Credential Negotiation</span></span>  
 <span data-ttu-id="f60ea-172">若要与委托一起使用 Kerberos 身份验证协议，必须用凭据协商实现 Kerberos 协议（有时称作“多路”或“多步”Kerberos）。</span><span class="sxs-lookup"><span data-stu-id="f60ea-172">To use the Kerberos authentication protocol with delegation, you must implement the Kerberos protocol with credential negotiation (sometimes called "multi-leg" or "multi-step" Kerberos).</span></span> <span data-ttu-id="f60ea-173">如果不用凭据协商实现 Kerberos 协议（有时称作“单稳”或“单路”Kerberos），则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="f60ea-173">If you implement Kerberos authentication without credential negotiation (sometimes called "one-shot" or "single-leg" Kerberos), an exception will be thrown.</span></span>  
  
 <span data-ttu-id="f60ea-174">若要用凭据协商实现 Kerberos，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="f60ea-174">To implement Kerberos with credential negotiation, do the following steps:</span></span>  
  
1. <span data-ttu-id="f60ea-175">通过将 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 设置为 <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> 来实现委托。</span><span class="sxs-lookup"><span data-stu-id="f60ea-175">Implement delegation by setting <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> to <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span>  
  
2. <span data-ttu-id="f60ea-176">要求 SSPI 协商：</span><span class="sxs-lookup"><span data-stu-id="f60ea-176">Require SSPI negotiation:</span></span>  
  
    1. <span data-ttu-id="f60ea-177">如果要使用标准绑定，请将 `NegotiateServiceCredential` 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="f60ea-177">If you are using standard bindings, set the `NegotiateServiceCredential` property to `true`.</span></span>  
  
    2. <span data-ttu-id="f60ea-178">如果要使用自定义绑定，请将 `AuthenticationMode` 元素的 `Security` 属性设置为 `SspiNegotiated`。</span><span class="sxs-lookup"><span data-stu-id="f60ea-178">If you are using custom bindings, set the `AuthenticationMode` attribute of the `Security` element to `SspiNegotiated`.</span></span>  
  
3. <span data-ttu-id="f60ea-179">通过禁用 NTLM 来要求 SSPI 协商使用 Kerberos：</span><span class="sxs-lookup"><span data-stu-id="f60ea-179">Require the SSPI negotiation to use Kerberos by disallowing the use of NTLM:</span></span>  
  
    1. <span data-ttu-id="f60ea-180">为此，可在代码中使用下面的语句：`ChannelFactory.Credentials.Windows.AllowNtlm = false`</span><span class="sxs-lookup"><span data-stu-id="f60ea-180">Do this in code, with the following statement: `ChannelFactory.Credentials.Windows.AllowNtlm = false`</span></span>  
  
    2. <span data-ttu-id="f60ea-181">或者在配置文件中将 `allowNtlm` 属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="f60ea-181">Or you can do this in the configuration file by setting the `allowNtlm` attribute to `false`.</span></span> <span data-ttu-id="f60ea-182">此属性包含在中 [\<windows>](../../configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="f60ea-182">This attribute is contained in the [\<windows>](../../configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).</span></span>  
  
### <a name="ntlm-protocol"></a><span data-ttu-id="f60ea-183">NTLM 协议</span><span class="sxs-lookup"><span data-stu-id="f60ea-183">NTLM Protocol</span></span>  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a><span data-ttu-id="f60ea-184">协商 SSP 回退到 NTLM，但 NTLM 已被禁用</span><span class="sxs-lookup"><span data-stu-id="f60ea-184">Negotiate SSP Falls Back to NTLM, but NTLM Is Disabled</span></span>  
 <span data-ttu-id="f60ea-185"><xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A>属性设置为 `false` ，这将导致 WINDOWS COMMUNICATION FOUNDATION （WCF）在使用 NTLM 时尽力引发异常。</span><span class="sxs-lookup"><span data-stu-id="f60ea-185">The <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> property is set to `false`, which causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="f60ea-186">将此属性设置为 `false` 可能不会阻止通过网络发送 NTLM 凭据。</span><span class="sxs-lookup"><span data-stu-id="f60ea-186">Setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>  
  
 <span data-ttu-id="f60ea-187">下面演示了如何禁用回退到 NTLM。</span><span class="sxs-lookup"><span data-stu-id="f60ea-187">The following shows how to disable fallback to NTLM.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a><span data-ttu-id="f60ea-188">NTLM 登录失败</span><span class="sxs-lookup"><span data-stu-id="f60ea-188">NTLM Logon Fails</span></span>  
 <span data-ttu-id="f60ea-189">客户端凭据在服务上无效。</span><span class="sxs-lookup"><span data-stu-id="f60ea-189">The client credentials are not valid on the service.</span></span> <span data-ttu-id="f60ea-190">请检查是否正确设置了用户名和密码，用户名和密码是否对应于运行服务的计算机已知的帐户。</span><span class="sxs-lookup"><span data-stu-id="f60ea-190">Check that the user name and password are correctly set and correspond to an account that is known to the computer where the service is running.</span></span> <span data-ttu-id="f60ea-191">NTLM 使用指定的凭据登录到服务计算机。</span><span class="sxs-lookup"><span data-stu-id="f60ea-191">NTLM uses the specified credentials to log on to the service's computer.</span></span> <span data-ttu-id="f60ea-192">虽然这些凭据在运行客户端的计算机上可能有效，但如果这些凭据在服务计算机上无效，登录也会失败。</span><span class="sxs-lookup"><span data-stu-id="f60ea-192">While the credentials may be valid on the computer where the client is running, this logon will fail if the credentials are not valid on the service's computer.</span></span>  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a><span data-ttu-id="f60ea-193">发生匿名 NTLM 登录，但默认情况下禁用匿名登录</span><span class="sxs-lookup"><span data-stu-id="f60ea-193">Anonymous NTLM Logon Occurs, but Anonymous Logons Are Disabled by Default</span></span>  
 <span data-ttu-id="f60ea-194">创建客户端时，<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 属性设置为 <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>（如下面的示例所示），但默认情况下，服务器不允许匿名登录。</span><span class="sxs-lookup"><span data-stu-id="f60ea-194">When creating a client, the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property is set to <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, as shown in the following example, but by default the server disallows anonymous logons.</span></span> <span data-ttu-id="f60ea-195">发生这种情况是因为 <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> 类的 <xref:System.ServiceModel.Security.WindowsServiceCredential> 属性的默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="f60ea-195">This occurs because the default value of the <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> property of the <xref:System.ServiceModel.Security.WindowsServiceCredential> class is `false`.</span></span>  
  
 <span data-ttu-id="f60ea-196">下面的客户端代码尝试启用匿名登录（请注意，默认属性为 `Identification`）。</span><span class="sxs-lookup"><span data-stu-id="f60ea-196">The following client code attempts to enable anonymous logons (note that the default property is `Identification`).</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 <span data-ttu-id="f60ea-197">下面的服务代码将默认值更改为允许服务器匿名登录。</span><span class="sxs-lookup"><span data-stu-id="f60ea-197">The following service code changes the default to enable anonymous logons by the server.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 <span data-ttu-id="f60ea-198">有关模拟的详细信息，请参阅[委派和模拟](delegation-and-impersonation-with-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="f60ea-198">For more information about impersonation, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="f60ea-199">或者，客户端正在使用内置帐户 SYSTEM 作为 Windows 服务运行。</span><span class="sxs-lookup"><span data-stu-id="f60ea-199">Alternatively, the client is running as a Windows service, using the built-in account SYSTEM.</span></span>  
  
### <a name="other-problems"></a><span data-ttu-id="f60ea-200">其他问题</span><span class="sxs-lookup"><span data-stu-id="f60ea-200">Other Problems</span></span>  
  
#### <a name="client-credentials-are-not-set-correctly"></a><span data-ttu-id="f60ea-201">客户端凭据设置不正确</span><span class="sxs-lookup"><span data-stu-id="f60ea-201">Client Credentials Are Not Set Correctly</span></span>  
 <span data-ttu-id="f60ea-202">Windows 身份验证使用由 <xref:System.ServiceModel.Security.WindowsClientCredential> 类的 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 属性返回的 <xref:System.ServiceModel.ClientBase%601> 实例，而不是 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>。</span><span class="sxs-lookup"><span data-stu-id="f60ea-202">Windows authentication uses the <xref:System.ServiceModel.Security.WindowsClientCredential> instance returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class, not the <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>.</span></span> <span data-ttu-id="f60ea-203">下面演示一个不正确的示例。</span><span class="sxs-lookup"><span data-stu-id="f60ea-203">The following shows an incorrect example.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 <span data-ttu-id="f60ea-204">下面演示的是正确的示例。</span><span class="sxs-lookup"><span data-stu-id="f60ea-204">The following shows the correct example.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a><span data-ttu-id="f60ea-205">SSPI 不可用</span><span class="sxs-lookup"><span data-stu-id="f60ea-205">SSPI Is Not Available</span></span>  
 <span data-ttu-id="f60ea-206">以下操作系统不支持使用 Windows 身份验证作为服务器： Windows XP Home Edition、Windows XP Media Center Edition 和 Windows Vista Home 版本。</span><span class="sxs-lookup"><span data-stu-id="f60ea-206">The following operating systems do not support Windows authentication when used as a server: Windows XP Home Edition, Windows XP Media Center Edition, and Windows Vista Home editions.</span></span>  
  
#### <a name="developing-and-deploying-with-different-identities"></a><span data-ttu-id="f60ea-207">使用不同的标识开发和部署</span><span class="sxs-lookup"><span data-stu-id="f60ea-207">Developing and Deploying with Different Identities</span></span>  
 <span data-ttu-id="f60ea-208">如果在一台计算机上开发应用程序，并在另一台计算机上部署它，然后在每台计算机上使用不同的帐户类型进行身份验证，则可能遇到不同的行为。</span><span class="sxs-lookup"><span data-stu-id="f60ea-208">If you develop your application on one machine, and deploy on another, and use different account types to authenticate on each machine, you may experience different behavior.</span></span> <span data-ttu-id="f60ea-209">例如，假定使用 `SSPI Negotiated` 身份验证模式，在 Windows XP Pro 计算机上开发应用程序。</span><span class="sxs-lookup"><span data-stu-id="f60ea-209">For example, suppose you develop your application on a Windows XP Pro machine using the `SSPI Negotiated` authentication mode.</span></span> <span data-ttu-id="f60ea-210">如果使用本地用户帐户进行身份验证，则会使用 NTLM 协议。</span><span class="sxs-lookup"><span data-stu-id="f60ea-210">If you use a local user account to authenticate with, then NTLM protocol will be used.</span></span> <span data-ttu-id="f60ea-211">在开发应用程序后，将服务部署到使用域帐户运行它的 Windows Server 2003 计算机。</span><span class="sxs-lookup"><span data-stu-id="f60ea-211">Once the application is developed, you deploy the service to a Windows Server 2003 machine where it runs under a domain account.</span></span> <span data-ttu-id="f60ea-212">此时，客户端将无法对服务进行身份验证，因为它将使用 Kerberos 和域控制器。</span><span class="sxs-lookup"><span data-stu-id="f60ea-212">At this point, the client will not be able to authenticate the service because it will be using Kerberos and a domain controller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f60ea-213">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f60ea-213">See also</span></span>

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="f60ea-214">委托和模拟</span><span class="sxs-lookup"><span data-stu-id="f60ea-214">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)
- [<span data-ttu-id="f60ea-215">不受支持的方案</span><span class="sxs-lookup"><span data-stu-id="f60ea-215">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
