---
title: <transport> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 996b3655b0698595256c9a7197f705d46e6e9fcf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169812"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="122e4-102">\<transport> 的 \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="122e4-102">\<transport> of \<netHttpBinding></span></span>

<span data-ttu-id="122e4-103">为 HTTP 传输定义控制身份验证参数的属性。</span><span class="sxs-lookup"><span data-stu-id="122e4-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="122e4-104">语法</span><span class="sxs-lookup"><span data-stu-id="122e4-104">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="122e4-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="122e4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="122e4-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="122e4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="122e4-107">特性</span><span class="sxs-lookup"><span data-stu-id="122e4-107">Attributes</span></span>  
  
|<span data-ttu-id="122e4-108">属性</span><span class="sxs-lookup"><span data-stu-id="122e4-108">Attribute</span></span>|<span data-ttu-id="122e4-109">描述</span><span class="sxs-lookup"><span data-stu-id="122e4-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="122e4-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="122e4-110">clientCredentialType</span></span>|<span data-ttu-id="122e4-111">-指定执行使用 HTTP 身份验证的客户端身份验证时要使用的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="122e4-111">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="122e4-112">默认为 `None`。</span><span class="sxs-lookup"><span data-stu-id="122e4-112">The default is `None`.</span></span> <span data-ttu-id="122e4-113">此属性的类型为 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="122e4-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="122e4-114">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="122e4-114">proxyCredentialType</span></span>|<span data-ttu-id="122e4-115">-指定使用代理通过 HTTP 在域中执行客户端身份验证时使用的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="122e4-115">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="122e4-116">只有当父 `mode` 元素的 `security` 属性为 `Transport` 或 `TransportCredentialsOnly` 时，此属性才适用。</span><span class="sxs-lookup"><span data-stu-id="122e4-116">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="122e4-117">此属性的类型为 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="122e4-117">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="122e4-118">realm</span><span class="sxs-lookup"><span data-stu-id="122e4-118">realm</span></span>|<span data-ttu-id="122e4-119">一个字符串，指定摘要式或基本身份验证的 HTTP 身份验证方案所使用的领域。</span><span class="sxs-lookup"><span data-stu-id="122e4-119">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="122e4-120">默认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="122e4-120">The default is an empty string.</span></span>|  
|<span data-ttu-id="122e4-121">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="122e4-121">policyEnforcement</span></span>|<span data-ttu-id="122e4-122">此枚举指定应何时强制实施 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>。</span><span class="sxs-lookup"><span data-stu-id="122e4-122">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="122e4-123">1. 从不–不会强制实施策略 (禁用扩展保护) 。</span><span class="sxs-lookup"><span data-stu-id="122e4-123">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="122e4-124">WhenSupported-仅当客户端支持扩展保护时才强制实施策略。</span><span class="sxs-lookup"><span data-stu-id="122e4-124">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="122e4-125">3. always –始终强制实施策略。</span><span class="sxs-lookup"><span data-stu-id="122e4-125">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="122e4-126">不支持扩展保护的客户端将无法进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="122e4-126">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="122e4-127">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="122e4-127">protectionScenario</span></span>|<span data-ttu-id="122e4-128">此枚举指定此策略强制实施的保护方案。</span><span class="sxs-lookup"><span data-stu-id="122e4-128">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="122e4-129">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="122e4-129">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="122e4-130">值</span><span class="sxs-lookup"><span data-stu-id="122e4-130">Value</span></span>|<span data-ttu-id="122e4-131">描述</span><span class="sxs-lookup"><span data-stu-id="122e4-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="122e4-132">无</span><span class="sxs-lookup"><span data-stu-id="122e4-132">None</span></span>|<span data-ttu-id="122e4-133">在传输过程中不能保证消息的安全。</span><span class="sxs-lookup"><span data-stu-id="122e4-133">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="122e4-134">基本</span><span class="sxs-lookup"><span data-stu-id="122e4-134">Basic</span></span>|<span data-ttu-id="122e4-135">指定基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="122e4-135">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="122e4-136">摘要</span><span class="sxs-lookup"><span data-stu-id="122e4-136">Digest</span></span>|<span data-ttu-id="122e4-137">指定摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="122e4-137">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="122e4-138">Ntlm</span><span class="sxs-lookup"><span data-stu-id="122e4-138">Ntlm</span></span>|<span data-ttu-id="122e4-139">指定 NTLM 身份验证（如果可能且 Windows 身份验证失败）。</span><span class="sxs-lookup"><span data-stu-id="122e4-139">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="122e4-140">Windows</span><span class="sxs-lookup"><span data-stu-id="122e4-140">Windows</span></span>|<span data-ttu-id="122e4-141">指定 Windows 集成身份验证。</span><span class="sxs-lookup"><span data-stu-id="122e4-141">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="122e4-142">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="122e4-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="122e4-143">值</span><span class="sxs-lookup"><span data-stu-id="122e4-143">Value</span></span>|<span data-ttu-id="122e4-144">描述</span><span class="sxs-lookup"><span data-stu-id="122e4-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="122e4-145">无</span><span class="sxs-lookup"><span data-stu-id="122e4-145">None</span></span>|<span data-ttu-id="122e4-146">-传输过程中消息不受保护。</span><span class="sxs-lookup"><span data-stu-id="122e4-146">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="122e4-147">基本</span><span class="sxs-lookup"><span data-stu-id="122e4-147">Basic</span></span>|<span data-ttu-id="122e4-148">指定“RFC 2617 – HTTP 身份验证：基本和摘要式身份验证”所定义的基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="122e4-148">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="122e4-149">摘要</span><span class="sxs-lookup"><span data-stu-id="122e4-149">Digest</span></span>|<span data-ttu-id="122e4-150">指定“RFC 2617 – HTTP 身份验证：基本和摘要式身份验证”所定义的摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="122e4-150">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="122e4-151">Ntlm</span><span class="sxs-lookup"><span data-stu-id="122e4-151">Ntlm</span></span>|<span data-ttu-id="122e4-152">指定 NTLM 身份验证（如果可能且 Windows 身份验证失败）。</span><span class="sxs-lookup"><span data-stu-id="122e4-152">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="122e4-153">Windows</span><span class="sxs-lookup"><span data-stu-id="122e4-153">Windows</span></span>|<span data-ttu-id="122e4-154">指定 Windows 集成身份验证。</span><span class="sxs-lookup"><span data-stu-id="122e4-154">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="122e4-155">证书</span><span class="sxs-lookup"><span data-stu-id="122e4-155">Certificate</span></span>|<span data-ttu-id="122e4-156">使用证书执行客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="122e4-156">Performs client authentication using a certificate.</span></span> <span data-ttu-id="122e4-157">此选项只在父 `Mode` 元素的 `security` 属性设置为“Transport”时才起作用，如果该属性设置为“TransportCredentialOnly”，则此选项将不起作用。</span><span class="sxs-lookup"><span data-stu-id="122e4-157">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="122e4-158">子元素</span><span class="sxs-lookup"><span data-stu-id="122e4-158">Child Elements</span></span>  

 <span data-ttu-id="122e4-159">无</span><span class="sxs-lookup"><span data-stu-id="122e4-159">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="122e4-160">父元素</span><span class="sxs-lookup"><span data-stu-id="122e4-160">Parent Elements</span></span>  
  
|<span data-ttu-id="122e4-161">元素</span><span class="sxs-lookup"><span data-stu-id="122e4-161">Element</span></span>|<span data-ttu-id="122e4-162">描述</span><span class="sxs-lookup"><span data-stu-id="122e4-162">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|<span data-ttu-id="122e4-163">定义的安全功能 [\<netHttpBinding>](nethttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="122e4-163">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="122e4-164">示例</span><span class="sxs-lookup"><span data-stu-id="122e4-164">Example</span></span>  

 <span data-ttu-id="122e4-165">下面的示例演示如何对基本绑定使用 SSL 传输安全。</span><span class="sxs-lookup"><span data-stu-id="122e4-165">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="122e4-166">默认情况下，基本绑定支持 HTTP 通信。</span><span class="sxs-lookup"><span data-stu-id="122e4-166">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="122e4-167">请参阅</span><span class="sxs-lookup"><span data-stu-id="122e4-167">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="122e4-168">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="122e4-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="122e4-169">绑定</span><span class="sxs-lookup"><span data-stu-id="122e4-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="122e4-170">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="122e4-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="122e4-171">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="122e4-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
