---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855164"
---
# \<findCriteria>
<span data-ttu-id="17909-101">一个配置元素，提供客户端应用程序用于搜索发现服务的一组条件。</span><span class="sxs-lookup"><span data-stu-id="17909-101">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="17909-102">可将这些条件划分为搜索条件（指定要查找的服务）和查找终止条件（搜索应持续的时长）。</span><span class="sxs-lookup"><span data-stu-id="17909-102">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**  
  
## <a name="syntax"></a><span data-ttu-id="17909-103">语法</span><span class="sxs-lookup"><span data-stu-id="17909-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17909-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="17909-104">Attributes and Elements</span></span>  
 <span data-ttu-id="17909-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="17909-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17909-106">特性</span><span class="sxs-lookup"><span data-stu-id="17909-106">Attributes</span></span>  
  
|<span data-ttu-id="17909-107">属性</span><span class="sxs-lookup"><span data-stu-id="17909-107">Attribute</span></span>|<span data-ttu-id="17909-108">说明</span><span class="sxs-lookup"><span data-stu-id="17909-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17909-109">duration</span><span class="sxs-lookup"><span data-stu-id="17909-109">duration</span></span>|<span data-ttu-id="17909-110">一个 Timespan 值，指定等待网络上的服务所发送的答复的最长时间。</span><span class="sxs-lookup"><span data-stu-id="17909-110">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="17909-111">默认持续时间为 20 秒。</span><span class="sxs-lookup"><span data-stu-id="17909-111">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="17909-112">maxResults</span><span class="sxs-lookup"><span data-stu-id="17909-112">maxResults</span></span>|<span data-ttu-id="17909-113">一个整数，指定等待网络或 Internet 上的服务所发送的最大答复数。</span><span class="sxs-lookup"><span data-stu-id="17909-113">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="17909-114">如果在经过 `duration` 特性指定的值之前收到的答复达到了最大数目，则查找操作将结束。</span><span class="sxs-lookup"><span data-stu-id="17909-114">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="17909-115">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="17909-115">scopeMatchBy</span></span>|<span data-ttu-id="17909-116">一个 URI，指定当对 Probe 消息中的范围和终结点中的范围进行匹配时采用的匹配算法。</span><span class="sxs-lookup"><span data-stu-id="17909-116">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="17909-117">支持五种范围匹配规则。</span><span class="sxs-lookup"><span data-stu-id="17909-117">There are five supported scope-matching rules.</span></span> <span data-ttu-id="17909-118">如果未指定范围匹配规则，则使用 `ScopeMatchByPrefix`。</span><span class="sxs-lookup"><span data-stu-id="17909-118">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="17909-119">有关这方面的更多信息，请参见 <xref:System.ServiceModel.Discovery.FindCriteria>。</span><span class="sxs-lookup"><span data-stu-id="17909-119">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17909-120">子元素</span><span class="sxs-lookup"><span data-stu-id="17909-120">Child Elements</span></span>  
  
|<span data-ttu-id="17909-121">元素</span><span class="sxs-lookup"><span data-stu-id="17909-121">Element</span></span>|<span data-ttu-id="17909-122">描述</span><span class="sxs-lookup"><span data-stu-id="17909-122">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="17909-123">一个配置元素的集合，这些元素包含工作流服务协定类型的名称。</span><span class="sxs-lookup"><span data-stu-id="17909-123">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="17909-124">\<extensions> 的 \<findCriteria></span><span class="sxs-lookup"><span data-stu-id="17909-124">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="17909-125">一个 XML 元素对象集合，这些对象提供扩展。</span><span class="sxs-lookup"><span data-stu-id="17909-125">A collection of XML element objects that provide extensions.</span></span>|  
|[\<scopes>](scopes.md)|<span data-ttu-id="17909-126">一个对象集合，这些对象包含在查找操作过程中用于查找一个或多个特定服务的绝对 URI。</span><span class="sxs-lookup"><span data-stu-id="17909-126">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="17909-127">如果找到特定服务，则表示已在服务 URI 和范围 URI 之间进行了成功的匹配，此匹配操作有时是借助处理匹配复杂性的范围规则完成的。</span><span class="sxs-lookup"><span data-stu-id="17909-127">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17909-128">父元素</span><span class="sxs-lookup"><span data-stu-id="17909-128">Parent Elements</span></span>  
  
|<span data-ttu-id="17909-129">元素</span><span class="sxs-lookup"><span data-stu-id="17909-129">Element</span></span>|<span data-ttu-id="17909-130">描述</span><span class="sxs-lookup"><span data-stu-id="17909-130">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="17909-131">包含应用程序以客户端形式参与服务发现过程所需的设置。</span><span class="sxs-lookup"><span data-stu-id="17909-131">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17909-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17909-132">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
