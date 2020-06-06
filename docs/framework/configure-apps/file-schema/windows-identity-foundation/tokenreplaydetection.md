---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a4454042e1d97fb3cc2d6f2735104dadda6e7b5a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251773"
---
# \<tokenReplayDetection>
<span data-ttu-id="f15e5-101">启用令牌重播检测并指定令牌的过期时间。</span><span class="sxs-lookup"><span data-stu-id="f15e5-101">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**  
  
## <a name="syntax"></a><span data-ttu-id="f15e5-102">语法</span><span class="sxs-lookup"><span data-stu-id="f15e5-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="f15e5-103">类型</span><span class="sxs-lookup"><span data-stu-id="f15e5-103">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f15e5-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f15e5-104">Attributes and Elements</span></span>  
 <span data-ttu-id="f15e5-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f15e5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f15e5-106">特性</span><span class="sxs-lookup"><span data-stu-id="f15e5-106">Attributes</span></span>  
  
|<span data-ttu-id="f15e5-107">属性</span><span class="sxs-lookup"><span data-stu-id="f15e5-107">Attribute</span></span>|<span data-ttu-id="f15e5-108">说明</span><span class="sxs-lookup"><span data-stu-id="f15e5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f15e5-109">已启用</span><span class="sxs-lookup"><span data-stu-id="f15e5-109">enabled</span></span>|<span data-ttu-id="f15e5-110">一个值，该值指定是否启用令牌重放检测;"true" 表示启用令牌重播检测。</span><span class="sxs-lookup"><span data-stu-id="f15e5-110">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="f15e5-111">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="f15e5-111">expirationPeriod</span></span>|<span data-ttu-id="f15e5-112">一个 <xref:System.TimeSpan> ，指定项目被视为过期并从缓存中删除之前的最大时间量。</span><span class="sxs-lookup"><span data-stu-id="f15e5-112">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="f15e5-113">有关如何指定值的详细信息 <xref:System.TimeSpan> ，请参阅[Timespan 值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f15e5-113">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f15e5-114">子元素</span><span class="sxs-lookup"><span data-stu-id="f15e5-114">Child Elements</span></span>  
 <span data-ttu-id="f15e5-115">无</span><span class="sxs-lookup"><span data-stu-id="f15e5-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f15e5-116">父元素</span><span class="sxs-lookup"><span data-stu-id="f15e5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f15e5-117">元素</span><span class="sxs-lookup"><span data-stu-id="f15e5-117">Element</span></span>|<span data-ttu-id="f15e5-118">描述</span><span class="sxs-lookup"><span data-stu-id="f15e5-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="f15e5-119">指定服务级别标识设置。</span><span class="sxs-lookup"><span data-stu-id="f15e5-119">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="f15e5-120">为安全标记处理程序的集合提供配置。</span><span class="sxs-lookup"><span data-stu-id="f15e5-120">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f15e5-121">注解</span><span class="sxs-lookup"><span data-stu-id="f15e5-121">Remarks</span></span>  
 <span data-ttu-id="f15e5-122">可以在元素 `<tokenReplayDetection>` 下的服务级别指定元素， `<identityConfiguration>` 或在元素下的安全令牌处理程序集合级别指定元素 `<securityTokenHandlerConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="f15e5-122">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="f15e5-123">标记处理程序集合上的设置将重写服务上指定的设置。</span><span class="sxs-lookup"><span data-stu-id="f15e5-123">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="f15e5-124">令牌重播缓存的类型由 [\<tokenReplayCache>](tokenreplaycache.md) 元素指定。</span><span class="sxs-lookup"><span data-stu-id="f15e5-124">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
