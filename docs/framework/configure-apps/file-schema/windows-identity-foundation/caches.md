---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 791c5be8aa48db2b17a42a216ad2bf5e7b5a4bc1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189872"
---
# \<caches>

<span data-ttu-id="de262-101">注册用于会话令牌和令牌重播检测的缓存。</span><span class="sxs-lookup"><span data-stu-id="de262-101">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="de262-102">语法</span><span class="sxs-lookup"><span data-stu-id="de262-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de262-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="de262-103">Attributes and Elements</span></span>  

 <span data-ttu-id="de262-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="de262-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de262-105">特性</span><span class="sxs-lookup"><span data-stu-id="de262-105">Attributes</span></span>  

 <span data-ttu-id="de262-106">无</span><span class="sxs-lookup"><span data-stu-id="de262-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de262-107">子元素</span><span class="sxs-lookup"><span data-stu-id="de262-107">Child Elements</span></span>  
  
|<span data-ttu-id="de262-108">元素</span><span class="sxs-lookup"><span data-stu-id="de262-108">Element</span></span>|<span data-ttu-id="de262-109">描述</span><span class="sxs-lookup"><span data-stu-id="de262-109">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="de262-110">使用服务或安全标记处理程序集合为会话令牌注册缓存。</span><span class="sxs-lookup"><span data-stu-id="de262-110">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="de262-111">向服务或安全标记处理程序集合注册令牌重播缓存。</span><span class="sxs-lookup"><span data-stu-id="de262-111">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de262-112">父元素</span><span class="sxs-lookup"><span data-stu-id="de262-112">Parent Elements</span></span>  
  
|<span data-ttu-id="de262-113">元素</span><span class="sxs-lookup"><span data-stu-id="de262-113">Element</span></span>|<span data-ttu-id="de262-114">描述</span><span class="sxs-lookup"><span data-stu-id="de262-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="de262-115">指定服务级别标识设置。</span><span class="sxs-lookup"><span data-stu-id="de262-115">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="de262-116">为安全标记处理程序的集合提供配置。</span><span class="sxs-lookup"><span data-stu-id="de262-116">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de262-117">备注</span><span class="sxs-lookup"><span data-stu-id="de262-117">Remarks</span></span>  

 <span data-ttu-id="de262-118">可以在元素 `<caches>` 下的服务级别指定元素， `<identityConfiguration>` 或在元素下的安全令牌处理程序集合级别指定元素 `<securityTokenHandlerConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="de262-118">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="de262-119">标记处理程序集合上的设置将重写服务上指定的设置。</span><span class="sxs-lookup"><span data-stu-id="de262-119">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="de262-120">`<caches>`元素由 <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> 类表示。</span><span class="sxs-lookup"><span data-stu-id="de262-120">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="de262-121">配置的缓存由 <xref:System.IdentityModel.Configuration.IdentityModelCaches> 类表示。</span><span class="sxs-lookup"><span data-stu-id="de262-121">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de262-122">示例</span><span class="sxs-lookup"><span data-stu-id="de262-122">Example</span></span>  

 <span data-ttu-id="de262-123">下面的 XML 演示了如何配置自定义缓存，用于保存)  (的会话安全令牌 <xref:System.IdentityModel.Tokens.SessionSecurityToken> 。</span><span class="sxs-lookup"><span data-stu-id="de262-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="de262-124">此配置取自 `ClaimsAwareWebFarm` 示例。</span><span class="sxs-lookup"><span data-stu-id="de262-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
