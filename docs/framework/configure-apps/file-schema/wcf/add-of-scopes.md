---
title: <add> 的 <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: 1f5b5ea621614880286181c7584863ea024b3d04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149005"
---
# <a name="add-of-scopes"></a><span data-ttu-id="ede12-102">\<add> 的 \<scopes></span><span class="sxs-lookup"><span data-stu-id="ede12-102">\<add> of \<scopes></span></span>

<span data-ttu-id="ede12-103">添加可用于在查询时筛选服务终结点的自定义范围 URI。</span><span class="sxs-lookup"><span data-stu-id="ede12-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ede12-104">语法</span><span class="sxs-lookup"><span data-stu-id="ede12-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ede12-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ede12-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ede12-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ede12-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ede12-107">特性</span><span class="sxs-lookup"><span data-stu-id="ede12-107">Attributes</span></span>  
  
|<span data-ttu-id="ede12-108">属性</span><span class="sxs-lookup"><span data-stu-id="ede12-108">Attribute</span></span>|<span data-ttu-id="ede12-109">描述</span><span class="sxs-lookup"><span data-stu-id="ede12-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ede12-110">scope</span><span class="sxs-lookup"><span data-stu-id="ede12-110">scope</span></span>|<span data-ttu-id="ede12-111">一个 URI，包含在匹配条件以查找服务时可使用的终结点的范围信息。</span><span class="sxs-lookup"><span data-stu-id="ede12-111">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ede12-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ede12-112">Child Elements</span></span>  

 <span data-ttu-id="ede12-113">无。</span><span class="sxs-lookup"><span data-stu-id="ede12-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ede12-114">父元素</span><span class="sxs-lookup"><span data-stu-id="ede12-114">Parent Elements</span></span>  
  
|<span data-ttu-id="ede12-115">元素</span><span class="sxs-lookup"><span data-stu-id="ede12-115">Element</span></span>|<span data-ttu-id="ede12-116">描述</span><span class="sxs-lookup"><span data-stu-id="ede12-116">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="ede12-117">包含一个配置元素集合，这些元素指定可用于在查询时筛选服务终结点的自定义范围 URI。</span><span class="sxs-lookup"><span data-stu-id="ede12-117">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ede12-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="ede12-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
