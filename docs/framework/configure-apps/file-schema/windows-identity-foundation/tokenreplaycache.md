---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5e695bb56b59da40ce9e83f9f4f77d0d22d0b40f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202417"
---
# \<tokenReplayCache>

<span data-ttu-id="4d1b4-101">向服务或安全标记处理程序集合注册令牌重播缓存。</span><span class="sxs-lookup"><span data-stu-id="4d1b4-101">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="4d1b4-102">语法</span><span class="sxs-lookup"><span data-stu-id="4d1b4-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d1b4-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4d1b4-103">Attributes and Elements</span></span>  

 <span data-ttu-id="4d1b4-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4d1b4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d1b4-105">特性</span><span class="sxs-lookup"><span data-stu-id="4d1b4-105">Attributes</span></span>  
  
|<span data-ttu-id="4d1b4-106">属性</span><span class="sxs-lookup"><span data-stu-id="4d1b4-106">Attribute</span></span>|<span data-ttu-id="4d1b4-107">说明</span><span class="sxs-lookup"><span data-stu-id="4d1b4-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d1b4-108">type</span><span class="sxs-lookup"><span data-stu-id="4d1b4-108">type</span></span>|<span data-ttu-id="4d1b4-109">派生自类的类型 <xref:System.IdentityModel.Tokens.TokenReplayCache> 。</span><span class="sxs-lookup"><span data-stu-id="4d1b4-109">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="4d1b4-110">有关如何指定自定义的详细信息 `type` ，请参阅 [自定义类型引用]。</span><span class="sxs-lookup"><span data-stu-id="4d1b4-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="4d1b4-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4d1b4-111">Child Elements</span></span>  

 <span data-ttu-id="4d1b4-112">无</span><span class="sxs-lookup"><span data-stu-id="4d1b4-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d1b4-113">父元素</span><span class="sxs-lookup"><span data-stu-id="4d1b4-113">Parent Elements</span></span>  
  
|<span data-ttu-id="4d1b4-114">元素</span><span class="sxs-lookup"><span data-stu-id="4d1b4-114">Element</span></span>|<span data-ttu-id="4d1b4-115">描述</span><span class="sxs-lookup"><span data-stu-id="4d1b4-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="4d1b4-116">注册服务使用的缓存或安全标记处理程序集合。</span><span class="sxs-lookup"><span data-stu-id="4d1b4-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d1b4-117">备注</span><span class="sxs-lookup"><span data-stu-id="4d1b4-117">Remarks</span></span>  

 <span data-ttu-id="4d1b4-118">令牌重播缓存用于检测重播的标记。</span><span class="sxs-lookup"><span data-stu-id="4d1b4-118">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="4d1b4-119">令牌重播检测由 [\<tokenReplayDetection>](tokenreplaydetection.md) 元素启用，该元素还指定了令牌的最长到期时间。</span><span class="sxs-lookup"><span data-stu-id="4d1b4-119">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d1b4-120">示例</span><span class="sxs-lookup"><span data-stu-id="4d1b4-120">Example</span></span>  

 <span data-ttu-id="4d1b4-121">下面的 XML 演示了用于检测重播令牌的自定义缓存配置。</span><span class="sxs-lookup"><span data-stu-id="4d1b4-121">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d1b4-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="4d1b4-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
