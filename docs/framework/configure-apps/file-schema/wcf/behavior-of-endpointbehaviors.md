---
title: <behavior> 的 <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: d191b968e1c3fd1db0837ba7e03f210a1b00062d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201494"
---
# <a name="behavior-of-endpointbehaviors"></a><span data-ttu-id="103ab-102">\<behavior> 的 \<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="103ab-102">\<behavior> of \<endpointBehaviors></span></span>

<span data-ttu-id="103ab-103">`behavior` 元素包含终结点行为的设置集合。</span><span class="sxs-lookup"><span data-stu-id="103ab-103">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="103ab-104">每个行为都按其 `name` 进行索引。</span><span class="sxs-lookup"><span data-stu-id="103ab-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="103ab-105">终结点可以通过此名称链接到每个行为。</span><span class="sxs-lookup"><span data-stu-id="103ab-105">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="103ab-106">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="103ab-106">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="103ab-107">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="103ab-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="103ab-108">语法</span><span class="sxs-lookup"><span data-stu-id="103ab-108">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="103ab-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="103ab-109">Attributes and Elements</span></span>  

 <span data-ttu-id="103ab-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="103ab-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="103ab-111">特性</span><span class="sxs-lookup"><span data-stu-id="103ab-111">Attributes</span></span>  
  
|<span data-ttu-id="103ab-112">属性</span><span class="sxs-lookup"><span data-stu-id="103ab-112">Attribute</span></span>|<span data-ttu-id="103ab-113">说明</span><span class="sxs-lookup"><span data-stu-id="103ab-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="103ab-114">name</span><span class="sxs-lookup"><span data-stu-id="103ab-114">name</span></span>|<span data-ttu-id="103ab-115">一个包含行为的配置名称的唯一字符串。</span><span class="sxs-lookup"><span data-stu-id="103ab-115">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="103ab-116">此值是用户定义的一个字符串，该字符串必须是唯一的，因为它将充当元素的标识字符串。</span><span class="sxs-lookup"><span data-stu-id="103ab-116">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="103ab-117">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="103ab-117">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="103ab-118">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="103ab-118">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="103ab-119">子元素</span><span class="sxs-lookup"><span data-stu-id="103ab-119">Child Elements</span></span>  
  
|<span data-ttu-id="103ab-120">元素</span><span class="sxs-lookup"><span data-stu-id="103ab-120">Element</span></span>|<span data-ttu-id="103ab-121">描述</span><span class="sxs-lookup"><span data-stu-id="103ab-121">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="103ab-122">指定用于向服务验证客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="103ab-122">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[\<callbackDebug>](callbackdebug.md)|<span data-ttu-id="103ab-123">指定 Windows Communication Foundation (WCF) 回调对象的服务调试。</span><span class="sxs-lookup"><span data-stu-id="103ab-123">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>|  
|[\<callbackTimeouts>](callbacktimeouts.md)|<span data-ttu-id="103ab-124">指定客户端回调的超时。</span><span class="sxs-lookup"><span data-stu-id="103ab-124">Specifies the timeout for the client callback.</span></span>|  
|[\<clientVia>](clientvia.md)|<span data-ttu-id="103ab-125">指定消息应采用的路由。</span><span class="sxs-lookup"><span data-stu-id="103ab-125">Specifies the route a message should take.</span></span>|  
|[\<dataContractSerializer>](datacontractserializer.md)|<span data-ttu-id="103ab-126">包含 DataContractSerializer 的配置数据。</span><span class="sxs-lookup"><span data-stu-id="103ab-126">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|<span data-ttu-id="103ab-127">指定允许服务进行异步答复的终结点行为。</span><span class="sxs-lookup"><span data-stu-id="103ab-127">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[\<enableWebScript>](enablewebscript.md)|<span data-ttu-id="103ab-128">启用终结点行为，此行为使得可以使用 ASP.NET AJAX 网页中的服务。</span><span class="sxs-lookup"><span data-stu-id="103ab-128">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="103ab-129">该行为只应与 \<webHttpBinding> 标准绑定或 \<webMessageEncoding> 绑定元素一起使用。</span><span class="sxs-lookup"><span data-stu-id="103ab-129">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="103ab-130">指定终结点的各种发现设置，例如终结点的可发现性、范围以及对终结点元数据的任何自定义扩展。</span><span class="sxs-lookup"><span data-stu-id="103ab-130">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[\<soapProcessing>](soapprocessing.md)|<span data-ttu-id="103ab-131">定义用于封送不同绑定类型和消息版本之间消息的客户端终结点行为。</span><span class="sxs-lookup"><span data-stu-id="103ab-131">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[\<synchronousReceive>](synchronousreceive-element.md)|<span data-ttu-id="103ab-132">指定服务或客户端应用程序中用于接收消息的运行时行为。</span><span class="sxs-lookup"><span data-stu-id="103ab-132">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="103ab-133">它不具有任何属性或子元素。</span><span class="sxs-lookup"><span data-stu-id="103ab-133">It does not have any attributes or child elements.</span></span>|  
|[\<transactedBatching>](transactedbatching.md)|<span data-ttu-id="103ab-134">指定接收操作是否支持事务批处理。</span><span class="sxs-lookup"><span data-stu-id="103ab-134">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[\<webHttp>](webhttp.md)|<span data-ttu-id="103ab-135">通过配置指定终结点上的 WebHttpBehavior。</span><span class="sxs-lookup"><span data-stu-id="103ab-135">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="103ab-136">此行为与标准绑定结合使用时 \<webHttpBinding> ，将为 WCF 服务启用 Web 编程模型。</span><span class="sxs-lookup"><span data-stu-id="103ab-136">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a WCF service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="103ab-137">父元素</span><span class="sxs-lookup"><span data-stu-id="103ab-137">Parent Elements</span></span>  
  
|<span data-ttu-id="103ab-138">元素</span><span class="sxs-lookup"><span data-stu-id="103ab-138">Element</span></span>|<span data-ttu-id="103ab-139">描述</span><span class="sxs-lookup"><span data-stu-id="103ab-139">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="103ab-140">终结点行为元素的集合。</span><span class="sxs-lookup"><span data-stu-id="103ab-140">A collection of endpoint behavior elements.</span></span>|
