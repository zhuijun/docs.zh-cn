---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: dcc32f5aa055942408a3f01d37b5aa27ac0f51ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173765"
---
# \<service>

<span data-ttu-id="11b3c-101">`service` 元素包含 Windows Communication Foundation (WCF) 服务的设置。</span><span class="sxs-lookup"><span data-stu-id="11b3c-101">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="11b3c-102">它还包含公开此服务的终结点。</span><span class="sxs-lookup"><span data-stu-id="11b3c-102">It also contains endpoints that expose the service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**  
  
## <a name="syntax"></a><span data-ttu-id="11b3c-103">语法</span><span class="sxs-lookup"><span data-stu-id="11b3c-103">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11b3c-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="11b3c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="11b3c-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="11b3c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11b3c-106">特性</span><span class="sxs-lookup"><span data-stu-id="11b3c-106">Attributes</span></span>  
  
|<span data-ttu-id="11b3c-107">属性</span><span class="sxs-lookup"><span data-stu-id="11b3c-107">Attribute</span></span>|<span data-ttu-id="11b3c-108">描述</span><span class="sxs-lookup"><span data-stu-id="11b3c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11b3c-109">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="11b3c-109">behaviorConfiguration</span></span>|<span data-ttu-id="11b3c-110">一个字符串，其中包含要用于实例化服务的行为的行为名。</span><span class="sxs-lookup"><span data-stu-id="11b3c-110">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="11b3c-111">定义服务时，该行为名必须在作用域内。</span><span class="sxs-lookup"><span data-stu-id="11b3c-111">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="11b3c-112">默认值为一个空字符串。</span><span class="sxs-lookup"><span data-stu-id="11b3c-112">The default value is an empty string.</span></span>|  
|<span data-ttu-id="11b3c-113">name</span><span class="sxs-lookup"><span data-stu-id="11b3c-113">name</span></span>|<span data-ttu-id="11b3c-114">必需的字符串属性，此属性指定要进行实例化的服务的类型。</span><span class="sxs-lookup"><span data-stu-id="11b3c-114">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="11b3c-115">此设置必须等同于一个有效类型。</span><span class="sxs-lookup"><span data-stu-id="11b3c-115">This setting must equate to a valid type.</span></span> <span data-ttu-id="11b3c-116">格式应为 `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="11b3c-116">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11b3c-117">子元素</span><span class="sxs-lookup"><span data-stu-id="11b3c-117">Child Elements</span></span>  
  
|<span data-ttu-id="11b3c-118">元素</span><span class="sxs-lookup"><span data-stu-id="11b3c-118">Element</span></span>|<span data-ttu-id="11b3c-119">描述</span><span class="sxs-lookup"><span data-stu-id="11b3c-119">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="11b3c-120">公开此服务的 `endpoint` 元素的集合。</span><span class="sxs-lookup"><span data-stu-id="11b3c-120">A collection of `endpoint` elements that expose this service.</span></span>|  
|[\<host>](host.md)|<span data-ttu-id="11b3c-121">指定此服务实例的主机。</span><span class="sxs-lookup"><span data-stu-id="11b3c-121">Specifies the host of this service instance.</span></span> <span data-ttu-id="11b3c-122">此元素的类型为 <xref:System.ServiceModel.Configuration.HostElement>。</span><span class="sxs-lookup"><span data-stu-id="11b3c-122">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11b3c-123">父元素</span><span class="sxs-lookup"><span data-stu-id="11b3c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="11b3c-124">元素</span><span class="sxs-lookup"><span data-stu-id="11b3c-124">Element</span></span>|<span data-ttu-id="11b3c-125">描述</span><span class="sxs-lookup"><span data-stu-id="11b3c-125">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services.md)|<span data-ttu-id="11b3c-126">所有 WCF 配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="11b3c-126">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11b3c-127">备注</span><span class="sxs-lookup"><span data-stu-id="11b3c-127">Remarks</span></span>  

 <span data-ttu-id="11b3c-128">服务是在配置文件的 `services` 节中定义的。</span><span class="sxs-lookup"><span data-stu-id="11b3c-128">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="11b3c-129">程序集可以包含任意多个服务。</span><span class="sxs-lookup"><span data-stu-id="11b3c-129">An assembly can contain any number of services.</span></span> <span data-ttu-id="11b3c-130">每个服务都有自己的 `service` 配置节。</span><span class="sxs-lookup"><span data-stu-id="11b3c-130">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="11b3c-131">本节及其内容定义特定服务的服务协定、行为和终结点。</span><span class="sxs-lookup"><span data-stu-id="11b3c-131">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="11b3c-132">`behaviorConfiguration` 元素也是可选的。</span><span class="sxs-lookup"><span data-stu-id="11b3c-132">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="11b3c-133">它标识服务使用的行为。</span><span class="sxs-lookup"><span data-stu-id="11b3c-133">It identifies the behavior the service uses.</span></span> <span data-ttu-id="11b3c-134">在此属性中指定的行为必须链接到同一配置文件中的作用域内的行为。</span><span class="sxs-lookup"><span data-stu-id="11b3c-134">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="11b3c-135">每个服务都将公开一个或多个终结点，每个终结点具有自己的地址和绑定。</span><span class="sxs-lookup"><span data-stu-id="11b3c-135">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="11b3c-136">配置文件中使用的所有绑定都必须在该文件的范围内定义。</span><span class="sxs-lookup"><span data-stu-id="11b3c-136">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="11b3c-137">绑定通过 `name` 和 `bindingConfiguration` 属性的组合链接到终结点。</span><span class="sxs-lookup"><span data-stu-id="11b3c-137">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="11b3c-138">`name` 特性说明在哪个节中定义绑定。</span><span class="sxs-lookup"><span data-stu-id="11b3c-138">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="11b3c-139">`bindingConfiguration` 特性定义使用绑定节中的哪个配置。</span><span class="sxs-lookup"><span data-stu-id="11b3c-139">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="11b3c-140">绑定节可以定义若干个配置。</span><span class="sxs-lookup"><span data-stu-id="11b3c-140">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11b3c-141">示例</span><span class="sxs-lookup"><span data-stu-id="11b3c-141">Example</span></span>  

 <span data-ttu-id="11b3c-142">这是服务配置的一个示例。</span><span class="sxs-lookup"><span data-stu-id="11b3c-142">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a><span data-ttu-id="11b3c-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="11b3c-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="11b3c-144">正在配置服务</span><span class="sxs-lookup"><span data-stu-id="11b3c-144">Configuring Services</span></span>](../../../wcf/configuring-services.md)
