---
title: <routing> 的 <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: cd53b720bad5752189f1c30d9e4acd3a66830396
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150877"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="93243-102">\<routing> 的 \<serviceBehavior></span><span class="sxs-lookup"><span data-stu-id="93243-102">\<routing> of \<serviceBehavior></span></span>

<span data-ttu-id="93243-103">提供对路由服务的运行时访问以允许对路由配置进行动态修改。</span><span class="sxs-lookup"><span data-stu-id="93243-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
## <a name="syntax"></a><span data-ttu-id="93243-104">语法</span><span class="sxs-lookup"><span data-stu-id="93243-104">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93243-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="93243-105">Attributes and Elements</span></span>  

 <span data-ttu-id="93243-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="93243-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93243-107">特性</span><span class="sxs-lookup"><span data-stu-id="93243-107">Attributes</span></span>  
  
|<span data-ttu-id="93243-108">属性</span><span class="sxs-lookup"><span data-stu-id="93243-108">Attribute</span></span>|<span data-ttu-id="93243-109">描述</span><span class="sxs-lookup"><span data-stu-id="93243-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93243-110">filterTable</span><span class="sxs-lookup"><span data-stu-id="93243-110">filterTable</span></span>|<span data-ttu-id="93243-111">一个字符串，指定路由服务要计算的筛选器所在的路由表的名称。</span><span class="sxs-lookup"><span data-stu-id="93243-111">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="93243-112">此值必须与 `name` [\<filterTable>](filtertable.md) 部分中元素的属性相匹配 [\<filterTables>](filtertables.md) 。</span><span class="sxs-lookup"><span data-stu-id="93243-112">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="93243-113">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="93243-113">routeOnHeaderOnly</span></span>|<span data-ttu-id="93243-114">一个布尔值，指定筛选器将同时检查消息正文和标头，还是仅检查标头。</span><span class="sxs-lookup"><span data-stu-id="93243-114">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="93243-115">默认为 `true`。</span><span class="sxs-lookup"><span data-stu-id="93243-115">The default is `true`.</span></span>|  
|<span data-ttu-id="93243-116">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="93243-116">soapProcessingEnabled</span></span>|<span data-ttu-id="93243-117">一个布尔值，指定是否应进行 SOAP 处理。</span><span class="sxs-lookup"><span data-stu-id="93243-117">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93243-118">子元素</span><span class="sxs-lookup"><span data-stu-id="93243-118">Child Elements</span></span>  

 <span data-ttu-id="93243-119">无。</span><span class="sxs-lookup"><span data-stu-id="93243-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93243-120">父元素</span><span class="sxs-lookup"><span data-stu-id="93243-120">Parent Elements</span></span>  
  
|<span data-ttu-id="93243-121">元素</span><span class="sxs-lookup"><span data-stu-id="93243-121">Element</span></span>|<span data-ttu-id="93243-122">描述</span><span class="sxs-lookup"><span data-stu-id="93243-122">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="93243-123">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="93243-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93243-124">备注</span><span class="sxs-lookup"><span data-stu-id="93243-124">Remarks</span></span>  

 <span data-ttu-id="93243-125">将此配置元素添加到服务的行为配置中后，此配置元素将对该服务启用路由。</span><span class="sxs-lookup"><span data-stu-id="93243-125">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="93243-126">您可以在此元素中指定服务要使用的实际路由表。</span><span class="sxs-lookup"><span data-stu-id="93243-126">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="93243-127">通过使用此配置节，您可以在部署模式发生更改时动态更改路由设置。</span><span class="sxs-lookup"><span data-stu-id="93243-127">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="93243-128">在运行时，您可以使用新的路由设置注册自己的路由扩展，路由服务将开始对新消息和会话使用更新后的配置信息，而使正在实施的消息/会话使用启动时的任何现有规则。</span><span class="sxs-lookup"><span data-stu-id="93243-128">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="93243-129">这样，您可以在运行时对路由服务进行会话安全的无回收重新配置。</span><span class="sxs-lookup"><span data-stu-id="93243-129">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
