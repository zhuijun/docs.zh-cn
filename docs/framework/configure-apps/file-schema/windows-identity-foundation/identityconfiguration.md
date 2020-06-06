---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 0fa8c574fd5663606cf081f1000a24884306edfe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251986"
---
# \<identityConfiguration>

<span data-ttu-id="6220f-101">指定服务级别标识设置。</span><span class="sxs-lookup"><span data-stu-id="6220f-101">Specifies service-level identity settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<identityConfiguration>**  

## <a name="syntax"></a><span data-ttu-id="6220f-102">语法</span><span class="sxs-lookup"><span data-stu-id="6220f-102">Syntax</span></span>

```xml
<system.identityModel>
  <identityConfiguration
      name=xs:string
      saveBootstrapContext=xs:boolean>
      maximumClockSkew=TimeSpan >
  </identityConfiguration>
</system.identityModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6220f-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6220f-103">Attributes and Elements</span></span>

<span data-ttu-id="6220f-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6220f-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6220f-105">特性</span><span class="sxs-lookup"><span data-stu-id="6220f-105">Attributes</span></span>

|<span data-ttu-id="6220f-106">属性</span><span class="sxs-lookup"><span data-stu-id="6220f-106">Attribute</span></span>|<span data-ttu-id="6220f-107">说明</span><span class="sxs-lookup"><span data-stu-id="6220f-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="6220f-108">name</span><span class="sxs-lookup"><span data-stu-id="6220f-108">name</span></span>|<span data-ttu-id="6220f-109">标识配置节的名称。</span><span class="sxs-lookup"><span data-stu-id="6220f-109">The name of the identity configuration section.</span></span> <span data-ttu-id="6220f-110">您可以使用此名称来引用特定的配置节。</span><span class="sxs-lookup"><span data-stu-id="6220f-110">You can use this name to reference a specific configuration section.</span></span> <span data-ttu-id="6220f-111">如果未 `name` 指定任何属性，则节将定义默认配置。</span><span class="sxs-lookup"><span data-stu-id="6220f-111">If no `name` attribute is specified, the section defines the default configuration.</span></span> <span data-ttu-id="6220f-112">默认配置始终用于被动联合身份验证方案。</span><span class="sxs-lookup"><span data-stu-id="6220f-112">The default configuration is always used for passive federation scenarios.</span></span> <span data-ttu-id="6220f-113">有关详细信息，请参阅 [\<federationConfiguration>](federationconfiguration.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="6220f-113">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>|
|<span data-ttu-id="6220f-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="6220f-114">saveBootstrapContext</span></span>|<span data-ttu-id="6220f-115">指定是否应在会话令牌中包含启动令牌。</span><span class="sxs-lookup"><span data-stu-id="6220f-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="6220f-116">还可以通过在元素上设置属性，在令牌处理程序集合上设置值 `saveBootstrapContext` [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="6220f-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span> <span data-ttu-id="6220f-117">标记处理程序集合上设置的值将覆盖在服务上设置的值。</span><span class="sxs-lookup"><span data-stu-id="6220f-117">A value set on the token handler collection overrides the value set on the service.</span></span>|
|<span data-ttu-id="6220f-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="6220f-118">maximumClockSkew</span></span>|<span data-ttu-id="6220f-119">一个 <xref:System.TimeSpan> ，它指定允许的最大时钟偏差。</span><span class="sxs-lookup"><span data-stu-id="6220f-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="6220f-120">控制执行区分时间的操作时允许的最大时钟偏差，如验证登录会话的过期时间。</span><span class="sxs-lookup"><span data-stu-id="6220f-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="6220f-121">默认值为5分钟 "00:05:00"。</span><span class="sxs-lookup"><span data-stu-id="6220f-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="6220f-122">有关如何指定值的详细信息 <xref:System.TimeSpan> ，请参阅[Timespan 值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6220f-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="6220f-123">通过在元素上设置属性，还可以对令牌处理程序集合设置最大时钟偏差 `maximumClockSkew` [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="6220f-123">The maximum clock skew may also be set on a token handler collection by setting the `maximumClockSkew` attribute on the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span> <span data-ttu-id="6220f-124">标记处理程序集合上设置的值将覆盖在服务上设置的值。</span><span class="sxs-lookup"><span data-stu-id="6220f-124">A value set on the token handler collection overrides the value set on the service.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6220f-125">子元素</span><span class="sxs-lookup"><span data-stu-id="6220f-125">Child Elements</span></span>

|<span data-ttu-id="6220f-126">元素</span><span class="sxs-lookup"><span data-stu-id="6220f-126">Element</span></span>|<span data-ttu-id="6220f-127">描述</span><span class="sxs-lookup"><span data-stu-id="6220f-127">Description</span></span>|
|-------------|-----------------|
|[\<caches>](caches.md)|<span data-ttu-id="6220f-128">注册用于会话令牌和令牌重播检测的缓存。</span><span class="sxs-lookup"><span data-stu-id="6220f-128">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="6220f-129">可在服务级别或安全标记处理程序集合上指定。</span><span class="sxs-lookup"><span data-stu-id="6220f-129">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="6220f-130">可选。</span><span class="sxs-lookup"><span data-stu-id="6220f-130">Optional.</span></span>|
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="6220f-131">控制标记处理程序用于验证证书的设置。</span><span class="sxs-lookup"><span data-stu-id="6220f-131">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="6220f-132">可在服务级别或安全标记处理程序集合上指定。</span><span class="sxs-lookup"><span data-stu-id="6220f-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="6220f-133">可选。</span><span class="sxs-lookup"><span data-stu-id="6220f-133">Optional.</span></span>|
|[\<claimsAuthenticationManager>](claimsauthenticationmanager.md)|<span data-ttu-id="6220f-134">为传入声明注册声明身份验证管理器。</span><span class="sxs-lookup"><span data-stu-id="6220f-134">Registers a claims authentication manager for the incoming claims.</span></span> <span data-ttu-id="6220f-135">可选。</span><span class="sxs-lookup"><span data-stu-id="6220f-135">Optional.</span></span>|
|[\<claimsAuthorizationManager>](claimsauthorizationmanager.md)|<span data-ttu-id="6220f-136">为传入声明注册声明授权管理器。</span><span class="sxs-lookup"><span data-stu-id="6220f-136">Registers a claims authorization manager for the incoming claims.</span></span> <span data-ttu-id="6220f-137">可选。</span><span class="sxs-lookup"><span data-stu-id="6220f-137">Optional.</span></span>|
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="6220f-138">指定传入安全令牌所需的声明集。</span><span class="sxs-lookup"><span data-stu-id="6220f-138">Specifies the set of required claims for incoming security tokens.</span></span> <span data-ttu-id="6220f-139">可选。</span><span class="sxs-lookup"><span data-stu-id="6220f-139">Optional.</span></span>|
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="6220f-140">指定安全令牌处理程序的集合。</span><span class="sxs-lookup"><span data-stu-id="6220f-140">Specifies a collection of security token handlers.</span></span> <span data-ttu-id="6220f-141">可以指定零个或多个安全标记处理程序集合。</span><span class="sxs-lookup"><span data-stu-id="6220f-141">Zero or more collections of security token handlers can be specified.</span></span> <span data-ttu-id="6220f-142">可选。</span><span class="sxs-lookup"><span data-stu-id="6220f-142">Optional.</span></span>|
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="6220f-143">启用令牌重播检测并指定令牌的过期时间。</span><span class="sxs-lookup"><span data-stu-id="6220f-143">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="6220f-144">可在服务级别或安全标记处理程序集合上指定。</span><span class="sxs-lookup"><span data-stu-id="6220f-144">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="6220f-145">可选。</span><span class="sxs-lookup"><span data-stu-id="6220f-145">Optional.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6220f-146">父元素</span><span class="sxs-lookup"><span data-stu-id="6220f-146">Parent Elements</span></span>

|<span data-ttu-id="6220f-147">元素</span><span class="sxs-lookup"><span data-stu-id="6220f-147">Element</span></span>|<span data-ttu-id="6220f-148">描述</span><span class="sxs-lookup"><span data-stu-id="6220f-148">Description</span></span>|
|-------------|-----------------|
|[\<system.identityModel>](system-identitymodel.md)|<span data-ttu-id="6220f-149">为在应用程序中启用 Windows Identity Foundation （WIF）选项提供配置。</span><span class="sxs-lookup"><span data-stu-id="6220f-149">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6220f-150">注解</span><span class="sxs-lookup"><span data-stu-id="6220f-150">Remarks</span></span>

<span data-ttu-id="6220f-151">可以定义多个标识配置，每个配置都具有唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="6220f-151">Multiple identity configurations may be defined, each with a unique name.</span></span> <span data-ttu-id="6220f-152">此行为如下所示：</span><span class="sxs-lookup"><span data-stu-id="6220f-152">The behavior is as follows:</span></span>

1. <span data-ttu-id="6220f-153">如果未 `<identityConfiguration>` 指定元素，则为。</span><span class="sxs-lookup"><span data-stu-id="6220f-153">If no `<identityConfiguration>` element is specified.</span></span> <span data-ttu-id="6220f-154">默认标识配置是在运行时创建的，并使用默认值进行填充。</span><span class="sxs-lookup"><span data-stu-id="6220f-154">A default identity configuration is created at runtime and populated with default values.</span></span>

2. <span data-ttu-id="6220f-155">如果指定单个 `<identityConfiguration>` 元素，则为。</span><span class="sxs-lookup"><span data-stu-id="6220f-155">If a single `<identityConfiguration>` element is specified.</span></span> <span data-ttu-id="6220f-156">这是默认的标识配置。</span><span class="sxs-lookup"><span data-stu-id="6220f-156">It is the default identity configuration.</span></span> <span data-ttu-id="6220f-157">这并不重要。</span><span class="sxs-lookup"><span data-stu-id="6220f-157">It does not matter whether it is named or unnamed.</span></span>

3. <span data-ttu-id="6220f-158">如果 `<identityConfiguration>` 指定了多个元素。</span><span class="sxs-lookup"><span data-stu-id="6220f-158">If multiple `<identityConfiguration>` elements are specified.</span></span> <span data-ttu-id="6220f-159">未命名元素指定默认标识配置。</span><span class="sxs-lookup"><span data-stu-id="6220f-159">The unnamed element specifies the default identity configuration.</span></span> <span data-ttu-id="6220f-160">建议在指定多个 `<identityConfiguration>` 元素时，其中一项应为未命名元素。</span><span class="sxs-lookup"><span data-stu-id="6220f-160">It is recommended that when you specify multiple `<identityConfiguration>` elements, one of them should be unnamed.</span></span>

> [!WARNING]
> <span data-ttu-id="6220f-161">如果指定多个 `<identityConfiguration>` 元素，则其中一个元素应该是未命名元素。</span><span class="sxs-lookup"><span data-stu-id="6220f-161">If you specify multiple `<identityConfiguration>` elements, one of them should be unnamed.</span></span> <span data-ttu-id="6220f-162">未命名的元素将是默认的标识配置。</span><span class="sxs-lookup"><span data-stu-id="6220f-162">The unnamed element will be the default identity configuration.</span></span>

 <span data-ttu-id="6220f-163">元素中指定的某些设置 `<identityConfiguration>` 可由安全令牌处理程序集合上的设置重写，或由单个安全令牌处理程序上的设置重写。</span><span class="sxs-lookup"><span data-stu-id="6220f-163">Some of the settings specified in the `<identityConfiguration>` element can be overridden by settings on a security token handler collection or by settings on individual security token handlers.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6220f-164">当使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 类在代码中提供基于声明的访问控制时，元素引用的标识配置将 `<federationConfiguration>` 配置用于做出授权决定的声明授权管理器和策略。</span><span class="sxs-lookup"><span data-stu-id="6220f-164">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="6220f-165">即使在非被动 Web 方案（例如 Windows Communication Foundation （WCF）应用程序或不是基于 Web 的应用程序）情况下，也是如此。</span><span class="sxs-lookup"><span data-stu-id="6220f-165">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="6220f-166">如果应用程序不是被动 Web 应用程序，则 [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) 仅应用所引用标识配置的元素（及其子策略元素，如果存在）。</span><span class="sxs-lookup"><span data-stu-id="6220f-166">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="6220f-167">忽略所有其他设置。</span><span class="sxs-lookup"><span data-stu-id="6220f-167">All other settings are ignored.</span></span> <span data-ttu-id="6220f-168">有关详细信息，请参阅 [\<federationConfiguration>](federationconfiguration.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="6220f-168">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>

<span data-ttu-id="6220f-169">`<identityConfiguration>`元素由 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> 类表示。</span><span class="sxs-lookup"><span data-stu-id="6220f-169">The `<identityConfiguration>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> class.</span></span> <span data-ttu-id="6220f-170">标识配置部分由 <xref:System.IdentityModel.Configuration.IdentityConfiguration> 类表示。</span><span class="sxs-lookup"><span data-stu-id="6220f-170">An identity configuration section is represented by the <xref:System.IdentityModel.Configuration.IdentityConfiguration> class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6220f-171">将以下元素指定为元素的子元素 `<identityConfiguration>` 已被弃用，但仍支持此行为以实现向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="6220f-171">Specifying the following elements as child elements of the `<identityConfiguration>` element has been deprecated, although the behavior is still supported for backward compatibility.</span></span> <span data-ttu-id="6220f-172">应改为在元素下指定这些元素 [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="6220f-172">These elements should, instead, be specified under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span>
>
> - [\<audienceUris>](audienceuris.md)
> - [\<issuerNameRegistry>](issuernameregistry.md)
> - [\<issuerTokenResolver>](issuertokenresolver.md)
> - [\<serviceTokenResolver>](servicetokenresolver.md)

## <a name="example"></a><span data-ttu-id="6220f-173">示例</span><span class="sxs-lookup"><span data-stu-id="6220f-173">Example</span></span>

<span data-ttu-id="6220f-174">以下示例创建名为 "alternateConfiguration" 的标识配置。</span><span class="sxs-lookup"><span data-stu-id="6220f-174">The following example creates an identity configuration named "alternateConfiguration".</span></span> <span data-ttu-id="6220f-175">标识配置指定默认设置。</span><span class="sxs-lookup"><span data-stu-id="6220f-175">The identity configuration specifies default settings.</span></span>

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a><span data-ttu-id="6220f-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6220f-176">See also</span></span>

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
