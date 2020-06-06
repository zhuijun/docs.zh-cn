---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152731"
---
# \<federationConfiguration>
<span data-ttu-id="61265-101"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule> <xref:System.IdentityModel.Services.SessionAuthenticationModule> 通过 WS 联合身份验证协议使用联合身份验证时配置（WSFAM）和（SAM）。</span><span class="sxs-lookup"><span data-stu-id="61265-101">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="61265-102"><xref:System.Security.Claims.ClaimsAuthorizationManager>当使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 类提供基于声明的访问控制时，配置。</span><span class="sxs-lookup"><span data-stu-id="61265-102">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="61265-103">语法</span><span class="sxs-lookup"><span data-stu-id="61265-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61265-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="61265-104">Attributes and Elements</span></span>  
 <span data-ttu-id="61265-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="61265-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61265-106">特性</span><span class="sxs-lookup"><span data-stu-id="61265-106">Attributes</span></span>  
  
|<span data-ttu-id="61265-107">属性</span><span class="sxs-lookup"><span data-stu-id="61265-107">Attribute</span></span>|<span data-ttu-id="61265-108">说明</span><span class="sxs-lookup"><span data-stu-id="61265-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61265-109">name</span><span class="sxs-lookup"><span data-stu-id="61265-109">name</span></span>|<span data-ttu-id="61265-110">此联合配置元素的名称。</span><span class="sxs-lookup"><span data-stu-id="61265-110">The name of this federation configuration element.</span></span> <span data-ttu-id="61265-111">此属性主要为未来的协议提供扩展点。</span><span class="sxs-lookup"><span data-stu-id="61265-111">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="61265-112">可选。</span><span class="sxs-lookup"><span data-stu-id="61265-112">Optional.</span></span>|  
|<span data-ttu-id="61265-113">identityConfigurationName</span><span class="sxs-lookup"><span data-stu-id="61265-113">identityConfigurationName</span></span>|<span data-ttu-id="61265-114">要使用的元素中指定的标识配置节的名称 [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="61265-114">The name of the identity configuration section as specified in an [\<identityConfiguration>](identityconfiguration.md) element to use.</span></span> <span data-ttu-id="61265-115">如果未指定此属性，则使用 "默认标识配置" 部分。</span><span class="sxs-lookup"><span data-stu-id="61265-115">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="61265-116">可选。</span><span class="sxs-lookup"><span data-stu-id="61265-116">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61265-117">子元素</span><span class="sxs-lookup"><span data-stu-id="61265-117">Child Elements</span></span>  
  
|<span data-ttu-id="61265-118">元素</span><span class="sxs-lookup"><span data-stu-id="61265-118">Element</span></span>|<span data-ttu-id="61265-119">描述</span><span class="sxs-lookup"><span data-stu-id="61265-119">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="61265-120">配置 SAM 使用的 cookie 处理程序。</span><span class="sxs-lookup"><span data-stu-id="61265-120">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="61265-121">可选。</span><span class="sxs-lookup"><span data-stu-id="61265-121">Optional.</span></span>|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="61265-122">配置用于加密和解密令牌的证书。</span><span class="sxs-lookup"><span data-stu-id="61265-122">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="61265-123">可选。</span><span class="sxs-lookup"><span data-stu-id="61265-123">Optional.</span></span>|  
|[\<wsFederation>](wsfederation.md)|<span data-ttu-id="61265-124">配置 WS-FEDERATION 身份验证模块（WSFAM）。</span><span class="sxs-lookup"><span data-stu-id="61265-124">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="61265-125">可选。</span><span class="sxs-lookup"><span data-stu-id="61265-125">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61265-126">父元素</span><span class="sxs-lookup"><span data-stu-id="61265-126">Parent Elements</span></span>  
  
|<span data-ttu-id="61265-127">元素</span><span class="sxs-lookup"><span data-stu-id="61265-127">Element</span></span>|<span data-ttu-id="61265-128">描述</span><span class="sxs-lookup"><span data-stu-id="61265-128">Description</span></span>|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|<span data-ttu-id="61265-129">使用 WS 联合身份验证协议进行身份验证的配置节。</span><span class="sxs-lookup"><span data-stu-id="61265-129">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61265-130">注解</span><span class="sxs-lookup"><span data-stu-id="61265-130">Remarks</span></span>  
 <span data-ttu-id="61265-131">\<federationConfiguration>元素在两个不同的方案中提供设置：</span><span class="sxs-lookup"><span data-stu-id="61265-131">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
- <span data-ttu-id="61265-132">在被动 Web 应用程序中使用 WS 联合身份验证时，元素包含配置 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> （WSFAM）和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）的设置。</span><span class="sxs-lookup"><span data-stu-id="61265-132">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="61265-133">它还引用了用于配置安全令牌处理程序和证书的标识配置，以及声明授权管理器和声明身份验证管理器等组件。</span><span class="sxs-lookup"><span data-stu-id="61265-133">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
- <span data-ttu-id="61265-134">当使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 类在代码中提供基于声明的访问控制时，元素会引用标识配置，该配置将用于做出授权决定的声明授权管理器和策略。</span><span class="sxs-lookup"><span data-stu-id="61265-134">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="61265-135">即使在非被动 Web 应用场景的情况下，也是如此。例如，Windows Communication Foundation （WCF）应用程序或不是基于 Web 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="61265-135">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="61265-136">如果应用程序不是被动 Web 应用程序，则 [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) 仅应用该元素所引用的标识配置的元素（及其子策略元素，如果存在） `<federationConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="61265-136">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="61265-137">将忽略所有其他成员。</span><span class="sxs-lookup"><span data-stu-id="61265-137">All others are ignored.</span></span>  
  
 <span data-ttu-id="61265-138">无论方案如何，运行时都将加载默认的联合身份验证配置。</span><span class="sxs-lookup"><span data-stu-id="61265-138">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="61265-139">此行为定义如下：</span><span class="sxs-lookup"><span data-stu-id="61265-139">The behavior is defined as follows:</span></span>  
  
1. <span data-ttu-id="61265-140">如果没有任何 `<federationConfiguration>` 元素，则运行时将创建联合配置并使用默认值填充该配置。</span><span class="sxs-lookup"><span data-stu-id="61265-140">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="61265-141">此默认的联合身份验证配置将引用默认的标识配置。</span><span class="sxs-lookup"><span data-stu-id="61265-141">This default federation configuration will reference the default identity configuration.</span></span>  
  
2. <span data-ttu-id="61265-142">如果存在单个 `<federationConfiguration>` 元素，则它是默认的联合配置，而不考虑它是命名还是未命名。</span><span class="sxs-lookup"><span data-stu-id="61265-142">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="61265-143">如果 `identityConfiguration` 指定其属性，则引用命名标识配置; 否则，将引用默认标识配置。</span><span class="sxs-lookup"><span data-stu-id="61265-143">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3. <span data-ttu-id="61265-144">如果存在未命名的 `<federationConfiguration>` 元素，则它是默认的联合身份验证配置。</span><span class="sxs-lookup"><span data-stu-id="61265-144">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="61265-145">如果 `identityConfiguration` 指定其属性，则引用命名标识配置; 否则，将引用默认标识配置。</span><span class="sxs-lookup"><span data-stu-id="61265-145">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4. <span data-ttu-id="61265-146">如果存在多个命名 `<federationConfiguration>` 元素，且未命名 `<federationConfiguration>` 元素不存在，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="61265-146">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="61265-147">通常，只定义了一个 `<federationConfiguration>` 部分。</span><span class="sxs-lookup"><span data-stu-id="61265-147">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="61265-148">此部分是默认的联合身份验证配置。</span><span class="sxs-lookup"><span data-stu-id="61265-148">This section is the default federation configuration.</span></span> <span data-ttu-id="61265-149">您可以指定多个唯一命名的 `<federationConfiguration>` 元素; 但是，在这种情况下，如果要加载非命名的联合配置，则必须为提供处理程序。</span><span class="sxs-lookup"><span data-stu-id="61265-149">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="61265-150"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>事件，并将 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> 处理程序中的属性设置为 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 使用 `<federationConfiguration>` 配置文件中相应元素的值进行初始化的对象。</span><span class="sxs-lookup"><span data-stu-id="61265-150"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="61265-151">`<federationConfiguration>`元素由 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> 类表示。</span><span class="sxs-lookup"><span data-stu-id="61265-151">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="61265-152">配置对象本身由 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 类表示。</span><span class="sxs-lookup"><span data-stu-id="61265-152">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="61265-153">单个 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 实例在属性上设置 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> ，并为应用程序提供联合配置。</span><span class="sxs-lookup"><span data-stu-id="61265-153">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61265-154">示例</span><span class="sxs-lookup"><span data-stu-id="61265-154">Example</span></span>  
 <span data-ttu-id="61265-155">下面的 XML 演示一个 `<federationConfiguration>` 元素，该元素指定 WSFAM 的设置，并指定 SAM 使用默认 cookie 处理程序（类的实例 <xref:System.IdentityModel.Services.ChunkedCookieHandler> ）。</span><span class="sxs-lookup"><span data-stu-id="61265-155">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="61265-156">在此示例中，cookie 处理程序和 WSFAM 都不需要使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="61265-156">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="61265-157">这是因为 `requireHttps` 元素上的特性 `<wsFederation>` 和上的 `requireSsl` 特性 `<cookieHandlerElement>` 是 `false` 。</span><span class="sxs-lookup"><span data-stu-id="61265-157">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="61265-158">对于大多数生产环境，不建议使用这些设置，因为它们可能会带来安全风险。</span><span class="sxs-lookup"><span data-stu-id="61265-158">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"
      issuer="http://localhost:15839/wsFederationSTS/Issue"
      realm="http://localhost:50969/" reply="http://localhost:50969/"
      requireHttps="false"
      signOutReply="http://localhost:50969/SignedOutPage.html"
      signOutQueryString="Param1=value2&Param2=value2"
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61265-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61265-159">See also</span></span>

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](identityconfiguration.md)
