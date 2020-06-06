---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152562"
---
# \<securityTokenHandlerConfiguration>
<span data-ttu-id="1c5db-101">为标记处理程序的集合提供配置。</span><span class="sxs-lookup"><span data-stu-id="1c5db-101">Provides configuration for the collection of token handlers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="1c5db-102">语法</span><span class="sxs-lookup"><span data-stu-id="1c5db-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c5db-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1c5db-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1c5db-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1c5db-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c5db-105">特性</span><span class="sxs-lookup"><span data-stu-id="1c5db-105">Attributes</span></span>  
  
|<span data-ttu-id="1c5db-106">属性</span><span class="sxs-lookup"><span data-stu-id="1c5db-106">Attribute</span></span>|<span data-ttu-id="1c5db-107">说明</span><span class="sxs-lookup"><span data-stu-id="1c5db-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c5db-108">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="1c5db-108">saveBootstrapContext</span></span>|<span data-ttu-id="1c5db-109">指定是否应在会话令牌中包含启动令牌。</span><span class="sxs-lookup"><span data-stu-id="1c5db-109">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="1c5db-110">还可以通过在元素上设置属性，在令牌处理程序集合上设置值 `saveBootstrapContext` [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="1c5db-110">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="1c5db-111">标记处理程序集合上设置的值将覆盖在服务上设置的值。</span><span class="sxs-lookup"><span data-stu-id="1c5db-111">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="1c5db-112">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="1c5db-112">maximumClockSkew</span></span>|<span data-ttu-id="1c5db-113">一个 <xref:System.TimeSpan> ，它指定允许的最大时钟偏差。</span><span class="sxs-lookup"><span data-stu-id="1c5db-113">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="1c5db-114">控制执行区分时间的操作时允许的最大时钟偏差，如验证登录会话的过期时间。</span><span class="sxs-lookup"><span data-stu-id="1c5db-114">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="1c5db-115">默认值为5分钟 "00:05:00"。</span><span class="sxs-lookup"><span data-stu-id="1c5db-115">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="1c5db-116">有关如何指定值的详细信息 <xref:System.TimeSpan> ，请参阅[Timespan 值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1c5db-116">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="1c5db-117">通过在元素上设置属性，还可以在服务级别设置最大时钟偏差 `maximumClockSkew` [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="1c5db-117">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="1c5db-118">标记处理程序集合上设置的值将覆盖在服务上设置的值。</span><span class="sxs-lookup"><span data-stu-id="1c5db-118">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c5db-119">子元素</span><span class="sxs-lookup"><span data-stu-id="1c5db-119">Child Elements</span></span>  
  
|<span data-ttu-id="1c5db-120">元素</span><span class="sxs-lookup"><span data-stu-id="1c5db-120">Element</span></span>|<span data-ttu-id="1c5db-121">描述</span><span class="sxs-lookup"><span data-stu-id="1c5db-121">Description</span></span>|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|<span data-ttu-id="1c5db-122">指定作为此信赖方的可接受标识符的 Uri 集。</span><span class="sxs-lookup"><span data-stu-id="1c5db-122">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="1c5db-123">可选。</span><span class="sxs-lookup"><span data-stu-id="1c5db-123">Optional.</span></span>|  
|[\<caches>](caches.md)|<span data-ttu-id="1c5db-124">注册用于会话令牌和令牌重播检测的缓存。</span><span class="sxs-lookup"><span data-stu-id="1c5db-124">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="1c5db-125">可在服务级别或安全标记处理程序集合上指定。</span><span class="sxs-lookup"><span data-stu-id="1c5db-125">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="1c5db-126">可选。</span><span class="sxs-lookup"><span data-stu-id="1c5db-126">Optional.</span></span>|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="1c5db-127">控制标记处理程序用于验证证书的设置。</span><span class="sxs-lookup"><span data-stu-id="1c5db-127">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="1c5db-128">可在服务级别或安全标记处理程序集合上指定。</span><span class="sxs-lookup"><span data-stu-id="1c5db-128">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="1c5db-129">如果为特定处理程序配置了其自己的验证程序，则会重写这些设置。</span><span class="sxs-lookup"><span data-stu-id="1c5db-129">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="1c5db-130">可选。</span><span class="sxs-lookup"><span data-stu-id="1c5db-130">Optional.</span></span>|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="1c5db-131">配置标记处理程序集合中的处理程序使用的颁发者名称注册表。</span><span class="sxs-lookup"><span data-stu-id="1c5db-131">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="1c5db-132">可选。</span><span class="sxs-lookup"><span data-stu-id="1c5db-132">Optional.</span></span>|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|<span data-ttu-id="1c5db-133">注册由标记处理程序集合中的处理程序使用的颁发者令牌解析程序。</span><span class="sxs-lookup"><span data-stu-id="1c5db-133">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="1c5db-134">颁发者令牌解析器用于解析传入令牌和消息的签名令牌。</span><span class="sxs-lookup"><span data-stu-id="1c5db-134">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="1c5db-135">可选。</span><span class="sxs-lookup"><span data-stu-id="1c5db-135">Optional.</span></span>|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|<span data-ttu-id="1c5db-136">注册令牌处理程序集合中的处理程序使用的服务令牌解析程序。</span><span class="sxs-lookup"><span data-stu-id="1c5db-136">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="1c5db-137">服务令牌解析器用于解析传入令牌和消息的加密令牌。</span><span class="sxs-lookup"><span data-stu-id="1c5db-137">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="1c5db-138">可选。</span><span class="sxs-lookup"><span data-stu-id="1c5db-138">Optional.</span></span>|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="1c5db-139">启用令牌重播检测并指定令牌的过期时间。</span><span class="sxs-lookup"><span data-stu-id="1c5db-139">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="1c5db-140">可在服务级别或安全标记处理程序集合上指定。</span><span class="sxs-lookup"><span data-stu-id="1c5db-140">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="1c5db-141">可选。</span><span class="sxs-lookup"><span data-stu-id="1c5db-141">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c5db-142">父元素</span><span class="sxs-lookup"><span data-stu-id="1c5db-142">Parent Elements</span></span>  
  
|<span data-ttu-id="1c5db-143">元素</span><span class="sxs-lookup"><span data-stu-id="1c5db-143">Element</span></span>|<span data-ttu-id="1c5db-144">描述</span><span class="sxs-lookup"><span data-stu-id="1c5db-144">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="1c5db-145">指定注册到终结点的安全令牌处理程序的集合。</span><span class="sxs-lookup"><span data-stu-id="1c5db-145">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c5db-146">注解</span><span class="sxs-lookup"><span data-stu-id="1c5db-146">Remarks</span></span>  
 <span data-ttu-id="1c5db-147">本部分提供对象的属性值 <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> 。</span><span class="sxs-lookup"><span data-stu-id="1c5db-147">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="1c5db-148">此部分中配置的设置将覆盖在服务上配置的设置。</span><span class="sxs-lookup"><span data-stu-id="1c5db-148">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="1c5db-149">其中的某些设置可以通过在将处理程序添加到安全标记处理程序集合时指定的设置重写。</span><span class="sxs-lookup"><span data-stu-id="1c5db-149">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c5db-150">示例</span><span class="sxs-lookup"><span data-stu-id="1c5db-150">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
