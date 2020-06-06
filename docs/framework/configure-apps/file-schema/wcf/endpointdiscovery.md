---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398021"
---
# \<endpointDiscovery>
<span data-ttu-id="efe42-101">指定终结点的各种发现设置，例如终结点的可发现性、范围以及对终结点元数据的任何自定义扩展。</span><span class="sxs-lookup"><span data-stu-id="efe42-101">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="efe42-102">语法</span><span class="sxs-lookup"><span data-stu-id="efe42-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efe42-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="efe42-103">Attributes and Elements</span></span>  
 <span data-ttu-id="efe42-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="efe42-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efe42-105">特性</span><span class="sxs-lookup"><span data-stu-id="efe42-105">Attributes</span></span>  
  
|<span data-ttu-id="efe42-106">属性</span><span class="sxs-lookup"><span data-stu-id="efe42-106">Attribute</span></span>|<span data-ttu-id="efe42-107">说明</span><span class="sxs-lookup"><span data-stu-id="efe42-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efe42-108">已启用</span><span class="sxs-lookup"><span data-stu-id="efe42-108">enabled</span></span>|<span data-ttu-id="efe42-109">一个布尔值，指定是否在此终结点上启用可发现性。</span><span class="sxs-lookup"><span data-stu-id="efe42-109">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="efe42-110">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="efe42-110">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efe42-111">子元素</span><span class="sxs-lookup"><span data-stu-id="efe42-111">Child Elements</span></span>  
  
|<span data-ttu-id="efe42-112">元素</span><span class="sxs-lookup"><span data-stu-id="efe42-112">Element</span></span>|<span data-ttu-id="efe42-113">描述</span><span class="sxs-lookup"><span data-stu-id="efe42-113">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="efe42-114">终结点的范围 URI 集合。</span><span class="sxs-lookup"><span data-stu-id="efe42-114">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="efe42-115">一个终结点可以与多个范围 URI 关联。</span><span class="sxs-lookup"><span data-stu-id="efe42-115">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="efe42-116">[\<extensions>](extensions.md)[of \<endpointDiscovery> ]</span><span class="sxs-lookup"><span data-stu-id="efe42-116">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="efe42-117">一个 XML 元素集合，用于指定要对终结点发布的自定义元数据。</span><span class="sxs-lookup"><span data-stu-id="efe42-117">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|\<types>|<span data-ttu-id="efe42-118">要搜索的接口集合。</span><span class="sxs-lookup"><span data-stu-id="efe42-118">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="efe42-119">父元素</span><span class="sxs-lookup"><span data-stu-id="efe42-119">Parent Elements</span></span>  
  
|<span data-ttu-id="efe42-120">元素</span><span class="sxs-lookup"><span data-stu-id="efe42-120">Element</span></span>|<span data-ttu-id="efe42-121">描述</span><span class="sxs-lookup"><span data-stu-id="efe42-121">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="efe42-122">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="efe42-122">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="efe42-123">注解</span><span class="sxs-lookup"><span data-stu-id="efe42-123">Remarks</span></span>  
 <span data-ttu-id="efe42-124">如果将此配置元素添加到终结点的行为配置，并将 `enabled` 特性设置为 `true`，此配置元素将启用该终结点的可发现性。</span><span class="sxs-lookup"><span data-stu-id="efe42-124">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="efe42-125">此外，还可以使用 [\<scopes>](scopes.md) 子元素指定可用于在查询期间筛选服务终结点的自定义范围 uri，并使用 [\<extensions>](extensions.md) 子元素指定应随标准可发现元数据（EPR、ContractTypeName、BindingName、Scope 和 ListenURI）一起发布的自定义元数据。</span><span class="sxs-lookup"><span data-stu-id="efe42-125">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="efe42-126">此配置元素依赖于 [\<serviceDiscovery>](servicediscovery.md) 提供可发现性服务级别控制的元素。</span><span class="sxs-lookup"><span data-stu-id="efe42-126">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="efe42-127">这意味着，如果 [\<serviceDiscovery>](servicediscovery.md) 配置中不存在此元素的设置，则会将其忽略。</span><span class="sxs-lookup"><span data-stu-id="efe42-127">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efe42-128">示例</span><span class="sxs-lookup"><span data-stu-id="efe42-128">Example</span></span>  
 <span data-ttu-id="efe42-129">下面的配置示例指定要对终结点发布的筛选范围和扩展元数据。</span><span class="sxs-lookup"><span data-stu-id="efe42-129">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="efe42-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="efe42-130">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
