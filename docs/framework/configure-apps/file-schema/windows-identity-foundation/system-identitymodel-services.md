---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152499"
---
# \<system.identityModel.services>
<span data-ttu-id="952d4-102">使用 WS 联合身份验证协议进行身份验证的配置节。</span><span class="sxs-lookup"><span data-stu-id="952d4-102">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a><span data-ttu-id="952d4-103">语法</span><span class="sxs-lookup"><span data-stu-id="952d4-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="952d4-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="952d4-104">Attributes and Elements</span></span>  
 <span data-ttu-id="952d4-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="952d4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="952d4-106">特性</span><span class="sxs-lookup"><span data-stu-id="952d4-106">Attributes</span></span>  
 <span data-ttu-id="952d4-107">无</span><span class="sxs-lookup"><span data-stu-id="952d4-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="952d4-108">子元素</span><span class="sxs-lookup"><span data-stu-id="952d4-108">Child Elements</span></span>  
  
|<span data-ttu-id="952d4-109">元素</span><span class="sxs-lookup"><span data-stu-id="952d4-109">Element</span></span>|<span data-ttu-id="952d4-110">说明</span><span class="sxs-lookup"><span data-stu-id="952d4-110">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="952d4-111">包含配置 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> （WSFAM）和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM） HTTP 模块的设置。</span><span class="sxs-lookup"><span data-stu-id="952d4-111">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="952d4-112">父元素</span><span class="sxs-lookup"><span data-stu-id="952d4-112">Parent Elements</span></span>  
 <span data-ttu-id="952d4-113">无</span><span class="sxs-lookup"><span data-stu-id="952d4-113">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="952d4-114">备注</span><span class="sxs-lookup"><span data-stu-id="952d4-114">Remarks</span></span>  
 <span data-ttu-id="952d4-115">将 `<system.identityModel.services>` 部分添加到应用程序的配置文件，以提供 SAM 和 WSFAM 的设置。</span><span class="sxs-lookup"><span data-stu-id="952d4-115">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="952d4-116">当使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 类在代码中提供基于声明的访问控制时，将 <xref:System.Security.Claims.ClaimsAuthorizationManager> 通过 `<identityConfiguration>` `<federationConfiguration>` 此部分中的元素隐式或显式引用的元素来配置用于做出授权决策的声明授权管理器（）和策略。</span><span class="sxs-lookup"><span data-stu-id="952d4-116">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="952d4-117">有关详细信息，请参阅元素下的 "**备注**" [\<federationConfiguration>](federationconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="952d4-117">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="952d4-118">`<system.identityModel.services>`部分由 <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> 类表示。</span><span class="sxs-lookup"><span data-stu-id="952d4-118">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="952d4-119">`<federationConfiguration>`在部分中配置的子元素的集合由 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> 类表示。</span><span class="sxs-lookup"><span data-stu-id="952d4-119">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="952d4-120">示例</span><span class="sxs-lookup"><span data-stu-id="952d4-120">Example</span></span>  
 <span data-ttu-id="952d4-121">下面的 XML 演示如何将节添加 `<system.identityModel.services>` 到配置文件。</span><span class="sxs-lookup"><span data-stu-id="952d4-121">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="952d4-122">必须首先为节和部分添加节声明 `<system.identityModel.services>` `<system.identityModel>` 。</span><span class="sxs-lookup"><span data-stu-id="952d4-122">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="952d4-123">（添加 `<system.identityModel.services>` 部分时，还应为节添加声明， `<system.identityModel>` 以确保 `<identityConfiguration>` 运行时可以根据需要创建默认节。）添加了节声明后，可以在元素下配置联合身份验证设置 `<system.identityModel.services>` 。</span><span class="sxs-lookup"><span data-stu-id="952d4-123">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
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
  
</configuration>  
```
