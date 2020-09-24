---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 347d1a1cba95bbd4992de95d6617e8828f4fc374
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156896"
---
# \<sessionSecurityTokenCache>

<span data-ttu-id="f6968-101">使用服务或安全标记处理程序集合为会话令牌注册缓存。</span><span class="sxs-lookup"><span data-stu-id="f6968-101">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**  
  
## <a name="syntax"></a><span data-ttu-id="f6968-102">语法</span><span class="sxs-lookup"><span data-stu-id="f6968-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6968-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f6968-103">Attributes and Elements</span></span>  

 <span data-ttu-id="f6968-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f6968-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6968-105">特性</span><span class="sxs-lookup"><span data-stu-id="f6968-105">Attributes</span></span>  
  
|<span data-ttu-id="f6968-106">属性</span><span class="sxs-lookup"><span data-stu-id="f6968-106">Attribute</span></span>|<span data-ttu-id="f6968-107">说明</span><span class="sxs-lookup"><span data-stu-id="f6968-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6968-108">type</span><span class="sxs-lookup"><span data-stu-id="f6968-108">type</span></span>|<span data-ttu-id="f6968-109">派生自类的类型 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> 。</span><span class="sxs-lookup"><span data-stu-id="f6968-109">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6968-110">子元素</span><span class="sxs-lookup"><span data-stu-id="f6968-110">Child Elements</span></span>  

 <span data-ttu-id="f6968-111">无</span><span class="sxs-lookup"><span data-stu-id="f6968-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6968-112">父元素</span><span class="sxs-lookup"><span data-stu-id="f6968-112">Parent Elements</span></span>  
  
|<span data-ttu-id="f6968-113">元素</span><span class="sxs-lookup"><span data-stu-id="f6968-113">Element</span></span>|<span data-ttu-id="f6968-114">描述</span><span class="sxs-lookup"><span data-stu-id="f6968-114">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="f6968-115">注册服务使用的缓存或安全标记处理程序集合。</span><span class="sxs-lookup"><span data-stu-id="f6968-115">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f6968-116">示例</span><span class="sxs-lookup"><span data-stu-id="f6968-116">Example</span></span>  

 <span data-ttu-id="f6968-117">下面的 XML 演示了如何配置自定义缓存，用于保存)  (的会话安全令牌 <xref:System.IdentityModel.Tokens.SessionSecurityToken> 。</span><span class="sxs-lookup"><span data-stu-id="f6968-117">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="f6968-118">此配置取自 `ClaimsAwareWebFarm` 示例。</span><span class="sxs-lookup"><span data-stu-id="f6968-118">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="f6968-119">有关此示例的详细信息，请参阅 [WIF 代码示例索引](/previous-versions/dotnet/framework/security/wif-code-sample-index)。</span><span class="sxs-lookup"><span data-stu-id="f6968-119">For more information about this sample, see [WIF Code Sample Index](/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6968-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="f6968-120">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
