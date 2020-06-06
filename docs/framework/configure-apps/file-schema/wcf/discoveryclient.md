---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 71305720cad0206ec3dabb1863e2f1cd72eb85f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739036"
---
# \<discoveryClient>
<span data-ttu-id="aecac-101">一个用于创建自定义绑定的配置元素，通过该绑定，客户端应用程序能够自动搜索可检测服务，并能够在运行时查找服务地址。</span><span class="sxs-lookup"><span data-stu-id="aecac-101">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="aecac-102">语法</span><span class="sxs-lookup"><span data-stu-id="aecac-102">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aecac-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="aecac-103">Attributes and Elements</span></span>  
 <span data-ttu-id="aecac-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="aecac-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aecac-105">特性</span><span class="sxs-lookup"><span data-stu-id="aecac-105">Attributes</span></span>  
  
|<span data-ttu-id="aecac-106">属性</span><span class="sxs-lookup"><span data-stu-id="aecac-106">Attribute</span></span>|<span data-ttu-id="aecac-107">说明</span><span class="sxs-lookup"><span data-stu-id="aecac-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aecac-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="aecac-108">discoveryEndpoint</span></span>|<span data-ttu-id="aecac-109">一个包含发现终结点名称的字符串。通过此终结点，客户端应用程序能够自动搜索可检测服务，并能够在运行时查找服务地址。</span><span class="sxs-lookup"><span data-stu-id="aecac-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aecac-110">子元素</span><span class="sxs-lookup"><span data-stu-id="aecac-110">Child Elements</span></span>  
  
|<span data-ttu-id="aecac-111">元素</span><span class="sxs-lookup"><span data-stu-id="aecac-111">Element</span></span>|<span data-ttu-id="aecac-112">描述</span><span class="sxs-lookup"><span data-stu-id="aecac-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="aecac-113">一个配置元素，提供客户端应用程序用于搜索发现服务的一组条件。</span><span class="sxs-lookup"><span data-stu-id="aecac-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="aecac-114">可将这些条件划分为搜索条件（指定要查找的服务）和查找终止条件（搜索应持续的时长）。</span><span class="sxs-lookup"><span data-stu-id="aecac-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aecac-115">父元素</span><span class="sxs-lookup"><span data-stu-id="aecac-115">Parent Elements</span></span>  
  
|<span data-ttu-id="aecac-116">元素</span><span class="sxs-lookup"><span data-stu-id="aecac-116">Element</span></span>|<span data-ttu-id="aecac-117">描述</span><span class="sxs-lookup"><span data-stu-id="aecac-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="aecac-118">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="aecac-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aecac-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aecac-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
