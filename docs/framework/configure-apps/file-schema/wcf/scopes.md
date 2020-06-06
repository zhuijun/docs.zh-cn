---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399931"
---
# \<scopes>
<span data-ttu-id="91311-101">包含一个配置元素集合，这些元素指定可用于在查询时筛选服务终结点的自定义范围 URI。</span><span class="sxs-lookup"><span data-stu-id="91311-101">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**  
  
## <a name="syntax"></a><span data-ttu-id="91311-102">语法</span><span class="sxs-lookup"><span data-stu-id="91311-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91311-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="91311-103">Attributes and Elements</span></span>  
 <span data-ttu-id="91311-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="91311-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91311-105">特性</span><span class="sxs-lookup"><span data-stu-id="91311-105">Attributes</span></span>  
 <span data-ttu-id="91311-106">无。</span><span class="sxs-lookup"><span data-stu-id="91311-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91311-107">子元素</span><span class="sxs-lookup"><span data-stu-id="91311-107">Child Elements</span></span>  
  
|<span data-ttu-id="91311-108">属性</span><span class="sxs-lookup"><span data-stu-id="91311-108">Attribute</span></span>|<span data-ttu-id="91311-109">说明</span><span class="sxs-lookup"><span data-stu-id="91311-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|<span data-ttu-id="91311-110">添加可在匹配条件以查找服务时使用的终结点的范围信息。</span><span class="sxs-lookup"><span data-stu-id="91311-110">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91311-111">父元素</span><span class="sxs-lookup"><span data-stu-id="91311-111">Parent Elements</span></span>  
  
|<span data-ttu-id="91311-112">元素</span><span class="sxs-lookup"><span data-stu-id="91311-112">Element</span></span>|<span data-ttu-id="91311-113">描述</span><span class="sxs-lookup"><span data-stu-id="91311-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="91311-114">指定终结点的各种发现设置，例如终结点的可发现性、范围以及对终结点元数据的任何自定义扩展。</span><span class="sxs-lookup"><span data-stu-id="91311-114">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91311-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91311-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
