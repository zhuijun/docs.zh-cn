---
title: < system.serviceModel >
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 2125ce00b0e23f2e93ff251549f9c1276892b16b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399444"
---
# \<system.serviceModel>
<span data-ttu-id="3ce15-102">此配置节包含所有 Windows Communication Foundation （WCF）配置元素。</span><span class="sxs-lookup"><span data-stu-id="3ce15-102">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="3ce15-103">语法</span><span class="sxs-lookup"><span data-stu-id="3ce15-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
  </behaviors>
  <bindings>
  </bindings>
  <client>
  </client>
  <comContracts>
  </comContracts>
  <commonBehaviors>
  </commonBehaviors>
  <diagnostics>
  </diagnostics>
  <extensions>
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>
  <serviceHostingEnvironment>
  </serviceHostingEnvironment>
  <services>
  </services>
  <standardEndpoints>
  </standardEndpoints>
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ce15-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3ce15-104">Attributes and Elements</span></span>  
 <span data-ttu-id="3ce15-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3ce15-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ce15-106">特性</span><span class="sxs-lookup"><span data-stu-id="3ce15-106">Attributes</span></span>  
 <span data-ttu-id="3ce15-107">无</span><span class="sxs-lookup"><span data-stu-id="3ce15-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3ce15-108">子元素</span><span class="sxs-lookup"><span data-stu-id="3ce15-108">Child Elements</span></span>  
  
|<span data-ttu-id="3ce15-109">元素</span><span class="sxs-lookup"><span data-stu-id="3ce15-109">Element</span></span>|<span data-ttu-id="3ce15-110">说明</span><span class="sxs-lookup"><span data-stu-id="3ce15-110">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|<span data-ttu-id="3ce15-111">此节定义名为 `endpointBehaviors` 和 `serviceBehaviors` 的两个子集合。</span><span class="sxs-lookup"><span data-stu-id="3ce15-111">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="3ce15-112">每个集合分别定义终结点和服务所使用的行为元素。</span><span class="sxs-lookup"><span data-stu-id="3ce15-112">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="3ce15-113">每个行为元素由其唯一的 `name` 属性标识。</span><span class="sxs-lookup"><span data-stu-id="3ce15-113">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[\<bindings>](bindings.md)|<span data-ttu-id="3ce15-114">此节包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="3ce15-114">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="3ce15-115">每一项均由其唯一的 `name` 进行标识。</span><span class="sxs-lookup"><span data-stu-id="3ce15-115">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="3ce15-116">服务通过用 `name` 与绑定进行链接来使用绑定。</span><span class="sxs-lookup"><span data-stu-id="3ce15-116">Services use bindings by linking them using the `name`.</span></span>|  
|[\<client>](client.md)|<span data-ttu-id="3ce15-117">此节包含客户端用来连接到服务的终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="3ce15-117">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[\<comContracts>](comcontracts.md)|<span data-ttu-id="3ce15-118">此节定义支持 WCF 和 COM 互操作的 COM 协定。</span><span class="sxs-lookup"><span data-stu-id="3ce15-118">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[\<commonBehaviors>](commonbehaviors.md)|<span data-ttu-id="3ce15-119">此节只能在 machine.config 文件中定义。</span><span class="sxs-lookup"><span data-stu-id="3ce15-119">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="3ce15-120">它定义了名为 `endpointBehaviors` 和 `serviceBehaviors` 的两个子集合。</span><span class="sxs-lookup"><span data-stu-id="3ce15-120">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="3ce15-121">每个集合分别定义计算机上所有 WCF 终结点和服务所使用的行为元素。</span><span class="sxs-lookup"><span data-stu-id="3ce15-121">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="3ce15-122">如果在 `<commonBehaviors>` 和 `<behaviors>` 节中都定义某行为，则 \<behaviors> 节中的行为优先。</span><span class="sxs-lookup"><span data-stu-id="3ce15-122">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="3ce15-123">此节包含 WCF 的诊断功能设置。</span><span class="sxs-lookup"><span data-stu-id="3ce15-123">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="3ce15-124">用户可以启用/禁用跟踪、性能计数器和 WMI 提供程序，还可以添加自定义消息筛选器。</span><span class="sxs-lookup"><span data-stu-id="3ce15-124">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[\<extensions>](extensions-section.md)|<span data-ttu-id="3ce15-125">此节包含一个扩展集合，这些扩展使用户能够创建扩展的用户定义绑定、行为和其他方面。</span><span class="sxs-lookup"><span data-stu-id="3ce15-125">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="3ce15-126">此节定义传输协议方案（如 http、net.tcp、net.pipe 等）和 WCF 绑定之间的一组默认协议映射。</span><span class="sxs-lookup"><span data-stu-id="3ce15-126">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[\<routing>](routing.md)|<span data-ttu-id="3ce15-127">本节定义一组路由筛选器，这些筛选器确定计算传入消息时使用的 Windows Communication Foundation （WCF）的类型，以及用于 <xref:System.ServiceModel.Dispatcher.MessageFilter> 定义在筛选器匹配时要将消息发送到的目标终结点的路由表。</span><span class="sxs-lookup"><span data-stu-id="3ce15-127">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="3ce15-128">此节定义服务承载环境要为特定传输实例化的类型。</span><span class="sxs-lookup"><span data-stu-id="3ce15-128">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="3ce15-129">如果此节为空，则使用默认类型。</span><span class="sxs-lookup"><span data-stu-id="3ce15-129">If this section is empty, the default type is used.</span></span>|  
|[\<services>](services.md)|<span data-ttu-id="3ce15-130">此节包含服务的集合。</span><span class="sxs-lookup"><span data-stu-id="3ce15-130">The section contains a collection of services.</span></span> <span data-ttu-id="3ce15-131">对于程序集中定义的每个服务，此元素包含一个为服务指定设置的 `service` 元素。</span><span class="sxs-lookup"><span data-stu-id="3ce15-131">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="3ce15-132">此节定义一个标准终结点集合，这些终结点是预配置的可重用终结点。</span><span class="sxs-lookup"><span data-stu-id="3ce15-132">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="3ce15-133">标准终结点具有一个或多个设置为固定值的地址、绑定和协定特性。</span><span class="sxs-lookup"><span data-stu-id="3ce15-133">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="3ce15-134">例如，发现终结点具有固定的协定。</span><span class="sxs-lookup"><span data-stu-id="3ce15-134">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="3ce15-135">此外，还可以使用标准终结点用新属性扩展服务终结点，这与定义自定义绑定相似。</span><span class="sxs-lookup"><span data-stu-id="3ce15-135">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[\<tracking>](tracking-of-wcf.md)|<span data-ttu-id="3ce15-136">本部分为工作流服务定义跟踪设置。</span><span class="sxs-lookup"><span data-stu-id="3ce15-136">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3ce15-137">父元素</span><span class="sxs-lookup"><span data-stu-id="3ce15-137">Parent Elements</span></span>  
  
|<span data-ttu-id="3ce15-138">元素</span><span class="sxs-lookup"><span data-stu-id="3ce15-138">Element</span></span>|<span data-ttu-id="3ce15-139">说明</span><span class="sxs-lookup"><span data-stu-id="3ce15-139">Description</span></span>|  
|-------------|-----------------|  
|\<configuration>|<span data-ttu-id="3ce15-140">.NET 配置文件中的所有配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="3ce15-140">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ce15-141">注解</span><span class="sxs-lookup"><span data-stu-id="3ce15-141">Remarks</span></span>  
 <span data-ttu-id="3ce15-142">WCF 不会向其他产品的配置节添加元素。</span><span class="sxs-lookup"><span data-stu-id="3ce15-142">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="3ce15-143">WCF 服务在 `services` 配置文件的部分中定义。</span><span class="sxs-lookup"><span data-stu-id="3ce15-143">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="3ce15-144">程序集可以包含任意多个服务。</span><span class="sxs-lookup"><span data-stu-id="3ce15-144">An assembly can contain any number of services.</span></span> <span data-ttu-id="3ce15-145">每个服务都有自己的 `service` 配置节。</span><span class="sxs-lookup"><span data-stu-id="3ce15-145">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="3ce15-146">本节及其内容定义特定服务的服务协定、行为和终结点。</span><span class="sxs-lookup"><span data-stu-id="3ce15-146">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="3ce15-147">只有服务的 `name` 属性是必需的。</span><span class="sxs-lookup"><span data-stu-id="3ce15-147">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="3ce15-148">默认情况下，服务的名称描述用于实现服务的基础 CLR 类型；但是，您可以更改 <xref:System.ServiceModel.ServiceContractAttribute> 上的 ConfigurationName 属性以重写 CLR 类型需求。</span><span class="sxs-lookup"><span data-stu-id="3ce15-148">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="3ce15-149">`behaviorConfiguration` 属性是可选项。</span><span class="sxs-lookup"><span data-stu-id="3ce15-149">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="3ce15-150">它标识服务所使用的服务行为。</span><span class="sxs-lookup"><span data-stu-id="3ce15-150">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="3ce15-151">此属性指定的行为必须链接到同一配置文件的范围（即，同一文件或父文件）中定义的服务行为。</span><span class="sxs-lookup"><span data-stu-id="3ce15-151">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="3ce15-152">每个服务将公开 `endpoint` 元素中定义的一个或多个终结点。</span><span class="sxs-lookup"><span data-stu-id="3ce15-152">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="3ce15-153">每个终结点都具有自己的地址和绑定。</span><span class="sxs-lookup"><span data-stu-id="3ce15-153">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="3ce15-154">配置文件中使用的所有绑定都必须在该文件的范围内定义。</span><span class="sxs-lookup"><span data-stu-id="3ce15-154">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="3ce15-155">绑定通过 `name` 和 `bindingConfiguration` 属性的组合链接到终结点。</span><span class="sxs-lookup"><span data-stu-id="3ce15-155">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="3ce15-156">`binding` 属性定义在哪个节中定义绑定。</span><span class="sxs-lookup"><span data-stu-id="3ce15-156">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="3ce15-157">`bindingConfiguration` 属性定义使用绑定节中的哪个已配置绑定。</span><span class="sxs-lookup"><span data-stu-id="3ce15-157">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="3ce15-158">绑定节可以定义若干个已配置的绑定。</span><span class="sxs-lookup"><span data-stu-id="3ce15-158">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ce15-159">示例</span><span class="sxs-lookup"><span data-stu-id="3ce15-159">Example</span></span>  
 <span data-ttu-id="3ce15-160">下面是 WCF 配置文件的示例。</span><span class="sxs-lookup"><span data-stu-id="3ce15-160">This is an example of a WCF configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <!-- List of Behaviors -->
    </behaviors>
    <client>
      <!-- List of Endpoints -->
    </client>
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
    </diagnostics>
    <serviceHostingEnvironment>
      <!-- List of entries -->
    </serviceHostingEnvironment>
    <comContracts>
      <!-- List of COM+ Contracts -->
    </comContracts>
    <services>
      <!-- List of Services -->
    </services>
    <bindings>
      <!-- List of Bindings -->
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="3ce15-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ce15-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
