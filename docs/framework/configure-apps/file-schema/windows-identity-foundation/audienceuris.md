---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252172"
---
# \<audienceUris>
<span data-ttu-id="ee25e-101">指定可接受的信赖方（RP）标识符的 Uri 集。</span><span class="sxs-lookup"><span data-stu-id="ee25e-101">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="ee25e-102">除非已针对允许的某个受众 URI 确定了令牌的范围，否则不会接受令牌。</span><span class="sxs-lookup"><span data-stu-id="ee25e-102">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="ee25e-103">语法</span><span class="sxs-lookup"><span data-stu-id="ee25e-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee25e-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ee25e-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ee25e-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ee25e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee25e-106">特性</span><span class="sxs-lookup"><span data-stu-id="ee25e-106">Attributes</span></span>  
  
|<span data-ttu-id="ee25e-107">属性</span><span class="sxs-lookup"><span data-stu-id="ee25e-107">Attribute</span></span>|<span data-ttu-id="ee25e-108">说明</span><span class="sxs-lookup"><span data-stu-id="ee25e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee25e-109">模式</span><span class="sxs-lookup"><span data-stu-id="ee25e-109">mode</span></span>|<span data-ttu-id="ee25e-110">一个 <xref:System.IdentityModel.Selectors.AudienceUriMode> 值，该值指定是否应将受众限制应用于传入令牌。</span><span class="sxs-lookup"><span data-stu-id="ee25e-110">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="ee25e-111">可能的值为 "始终"、"从不" 和 "BearerKeyOnly"。</span><span class="sxs-lookup"><span data-stu-id="ee25e-111">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="ee25e-112">默认值为 "Always"。</span><span class="sxs-lookup"><span data-stu-id="ee25e-112">The default is "Always".</span></span> <span data-ttu-id="ee25e-113">可选。</span><span class="sxs-lookup"><span data-stu-id="ee25e-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee25e-114">子元素</span><span class="sxs-lookup"><span data-stu-id="ee25e-114">Child Elements</span></span>  
  
|<span data-ttu-id="ee25e-115">元素</span><span class="sxs-lookup"><span data-stu-id="ee25e-115">Element</span></span>|<span data-ttu-id="ee25e-116">描述</span><span class="sxs-lookup"><span data-stu-id="ee25e-116">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="ee25e-117">将属性指定的 URI 添加 `value` 到 audienceUris 集合。</span><span class="sxs-lookup"><span data-stu-id="ee25e-117">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="ee25e-118">需要 `value` 属性。</span><span class="sxs-lookup"><span data-stu-id="ee25e-118">The `value` attribute is required.</span></span> <span data-ttu-id="ee25e-119">URI 区分大小写。</span><span class="sxs-lookup"><span data-stu-id="ee25e-119">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="ee25e-120">清除 audienceUris 集合。</span><span class="sxs-lookup"><span data-stu-id="ee25e-120">Clears the audienceUris collection.</span></span> <span data-ttu-id="ee25e-121">所有标识符都将从集合中删除。</span><span class="sxs-lookup"><span data-stu-id="ee25e-121">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="ee25e-122">`value`从 audienceUris 集合中移除特性指定的 URI。</span><span class="sxs-lookup"><span data-stu-id="ee25e-122">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="ee25e-123">需要 `value` 属性。</span><span class="sxs-lookup"><span data-stu-id="ee25e-123">The `value` attribute is required.</span></span> <span data-ttu-id="ee25e-124">URI 区分大小写。</span><span class="sxs-lookup"><span data-stu-id="ee25e-124">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee25e-125">父元素</span><span class="sxs-lookup"><span data-stu-id="ee25e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ee25e-126">元素</span><span class="sxs-lookup"><span data-stu-id="ee25e-126">Element</span></span>|<span data-ttu-id="ee25e-127">描述</span><span class="sxs-lookup"><span data-stu-id="ee25e-127">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="ee25e-128">为安全标记处理程序的集合提供配置。</span><span class="sxs-lookup"><span data-stu-id="ee25e-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee25e-129">注解</span><span class="sxs-lookup"><span data-stu-id="ee25e-129">Remarks</span></span>  
 <span data-ttu-id="ee25e-130">默认情况下，集合为空;使用 `<add>` 、 `<clear>` 和 `<remove>` 元素可修改集合。</span><span class="sxs-lookup"><span data-stu-id="ee25e-130">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="ee25e-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>和 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 对象使用受众 uri 集合中的值来配置对象中允许的受众 uri 限制 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 。</span><span class="sxs-lookup"><span data-stu-id="ee25e-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="ee25e-132">`<audienceUris>`元素由 <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> 类表示。</span><span class="sxs-lookup"><span data-stu-id="ee25e-132">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="ee25e-133">添加到集合中的单个 URI 由 <xref:System.IdentityModel.Configuration.AudienceUriElement> 类表示。</span><span class="sxs-lookup"><span data-stu-id="ee25e-133">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee25e-134">使用 `<audienceUris>` 元素作为元素的子元素 [\<identityConfiguration>](identityconfiguration.md) 已被弃用，但仍支持向后兼容。</span><span class="sxs-lookup"><span data-stu-id="ee25e-134">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="ee25e-135">元素上的设置将 `<securityTokenHandlerConfiguration>` 替代元素上的设置 `<identityConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="ee25e-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee25e-136">示例</span><span class="sxs-lookup"><span data-stu-id="ee25e-136">Example</span></span>  
 <span data-ttu-id="ee25e-137">下面的 XML 演示如何配置应用程序的可接受受众 Uri。</span><span class="sxs-lookup"><span data-stu-id="ee25e-137">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="ee25e-138">此示例配置单个 URI。</span><span class="sxs-lookup"><span data-stu-id="ee25e-138">This example configures a single URI.</span></span> <span data-ttu-id="ee25e-139">将接受范围为此 URI 的标记，所有其他标记将被拒绝。</span><span class="sxs-lookup"><span data-stu-id="ee25e-139">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
