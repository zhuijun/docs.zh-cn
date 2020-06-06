---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251782"
---
# \<tokenReplayCache>
<span data-ttu-id="d161e-101">向服务或安全标记处理程序集合注册令牌重播缓存。</span><span class="sxs-lookup"><span data-stu-id="d161e-101">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="d161e-102">语法</span><span class="sxs-lookup"><span data-stu-id="d161e-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d161e-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d161e-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d161e-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d161e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d161e-105">特性</span><span class="sxs-lookup"><span data-stu-id="d161e-105">Attributes</span></span>  
  
|<span data-ttu-id="d161e-106">属性</span><span class="sxs-lookup"><span data-stu-id="d161e-106">Attribute</span></span>|<span data-ttu-id="d161e-107">说明</span><span class="sxs-lookup"><span data-stu-id="d161e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d161e-108">type</span><span class="sxs-lookup"><span data-stu-id="d161e-108">type</span></span>|<span data-ttu-id="d161e-109">派生自类的类型 <xref:System.IdentityModel.Tokens.TokenReplayCache> 。</span><span class="sxs-lookup"><span data-stu-id="d161e-109">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="d161e-110">有关如何指定自定义的详细信息 `type` ，请参阅 [自定义类型引用]。</span><span class="sxs-lookup"><span data-stu-id="d161e-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="d161e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d161e-111">Child Elements</span></span>  
 <span data-ttu-id="d161e-112">无</span><span class="sxs-lookup"><span data-stu-id="d161e-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d161e-113">父元素</span><span class="sxs-lookup"><span data-stu-id="d161e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d161e-114">元素</span><span class="sxs-lookup"><span data-stu-id="d161e-114">Element</span></span>|<span data-ttu-id="d161e-115">描述</span><span class="sxs-lookup"><span data-stu-id="d161e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="d161e-116">注册服务使用的缓存或安全标记处理程序集合。</span><span class="sxs-lookup"><span data-stu-id="d161e-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d161e-117">注解</span><span class="sxs-lookup"><span data-stu-id="d161e-117">Remarks</span></span>  
 <span data-ttu-id="d161e-118">令牌重播缓存用于检测重播的标记。</span><span class="sxs-lookup"><span data-stu-id="d161e-118">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="d161e-119">令牌重播检测由 [\<tokenReplayDetection>](tokenreplaydetection.md) 元素启用，该元素还指定了令牌的最长到期时间。</span><span class="sxs-lookup"><span data-stu-id="d161e-119">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d161e-120">示例</span><span class="sxs-lookup"><span data-stu-id="d161e-120">Example</span></span>  
 <span data-ttu-id="d161e-121">下面的 XML 演示了用于检测重播令牌的自定义缓存配置。</span><span class="sxs-lookup"><span data-stu-id="d161e-121">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d161e-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d161e-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
