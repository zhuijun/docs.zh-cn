---
title: <transport> 的 <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732736"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="715fb-102">\<transport> 的 \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="715fb-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="715fb-103">定义 HTTP 传输的身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="715fb-103">Defines authentication settings for the HTTP transport.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a><span data-ttu-id="715fb-104">语法</span><span class="sxs-lookup"><span data-stu-id="715fb-104">Syntax</span></span>

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a><span data-ttu-id="715fb-105">类型</span><span class="sxs-lookup"><span data-stu-id="715fb-105">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="715fb-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="715fb-106">Attributes and Elements</span></span>

<span data-ttu-id="715fb-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="715fb-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="715fb-108">特性</span><span class="sxs-lookup"><span data-stu-id="715fb-108">Attributes</span></span>

|<span data-ttu-id="715fb-109">属性</span><span class="sxs-lookup"><span data-stu-id="715fb-109">Attribute</span></span>|<span data-ttu-id="715fb-110">说明</span><span class="sxs-lookup"><span data-stu-id="715fb-110">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="715fb-111">指定用于向服务证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="715fb-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="715fb-112">此属性的类型为 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="715fb-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="715fb-113">指定用于向域代理证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="715fb-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="715fb-114">此属性的类型为 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="715fb-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="715fb-115">一个字符串，指定摘要式或基本身份验证的身份验证领域。</span><span class="sxs-lookup"><span data-stu-id="715fb-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="715fb-116">默认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="715fb-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="715fb-117">身份验证领域至少指定执行身份验证的主机的名称。</span><span class="sxs-lookup"><span data-stu-id="715fb-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="715fb-118">它还可以指定具有访问权限的用户的集合。</span><span class="sxs-lookup"><span data-stu-id="715fb-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="715fb-119">用户可以查询身份验证领域，以确定多个可能的用户名和密码中哪一个可以使用。</span><span class="sxs-lookup"><span data-stu-id="715fb-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="715fb-120">此枚举指定应何时强制实施 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>。</span><span class="sxs-lookup"><span data-stu-id="715fb-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="715fb-121">1. 从不–不强制实施策略（禁用扩展保护）。</span><span class="sxs-lookup"><span data-stu-id="715fb-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="715fb-122">WhenSupported-仅当客户端支持扩展保护时才强制实施策略。</span><span class="sxs-lookup"><span data-stu-id="715fb-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="715fb-123">3. always –始终强制实施策略。</span><span class="sxs-lookup"><span data-stu-id="715fb-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="715fb-124">不支持扩展保护的客户端将无法进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="715fb-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="715fb-125">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="715fb-125">clientCredentialType Attribute</span></span>

|<span data-ttu-id="715fb-126">值</span><span class="sxs-lookup"><span data-stu-id="715fb-126">Value</span></span>|<span data-ttu-id="715fb-127">说明</span><span class="sxs-lookup"><span data-stu-id="715fb-127">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="715fb-128">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="715fb-128">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="715fb-129">使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="715fb-129">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="715fb-130">使用摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="715fb-130">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="715fb-131">对 Windows 域使用 NTLM 身份验证作为回退。</span><span class="sxs-lookup"><span data-stu-id="715fb-131">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="715fb-132">使用集成 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="715fb-132">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="715fb-133">使用 X.509 证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="715fb-133">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="715fb-134">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="715fb-134">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="715fb-135">值</span><span class="sxs-lookup"><span data-stu-id="715fb-135">Value</span></span>|<span data-ttu-id="715fb-136">说明</span><span class="sxs-lookup"><span data-stu-id="715fb-136">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="715fb-137">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="715fb-137">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="715fb-138">使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="715fb-138">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="715fb-139">使用摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="715fb-139">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="715fb-140">对 Windows 域使用 NTLM 作为回退。</span><span class="sxs-lookup"><span data-stu-id="715fb-140">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="715fb-141">使用集成 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="715fb-141">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="715fb-142">使用 X.509 证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="715fb-142">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="715fb-143">子元素</span><span class="sxs-lookup"><span data-stu-id="715fb-143">Child Elements</span></span>

<span data-ttu-id="715fb-144">无。</span><span class="sxs-lookup"><span data-stu-id="715fb-144">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="715fb-145">父元素</span><span class="sxs-lookup"><span data-stu-id="715fb-145">Parent Elements</span></span>

|<span data-ttu-id="715fb-146">元素</span><span class="sxs-lookup"><span data-stu-id="715fb-146">Element</span></span>|<span data-ttu-id="715fb-147">描述</span><span class="sxs-lookup"><span data-stu-id="715fb-147">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="715fb-148">表示的安全功能 [\<wsHttpBinding>](wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="715fb-148">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="715fb-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="715fb-149">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="715fb-150">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="715fb-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="715fb-151">绑定</span><span class="sxs-lookup"><span data-stu-id="715fb-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="715fb-152">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="715fb-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="715fb-153">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="715fb-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
