---
title: <add> 的 <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 2572a6ee6763ae26fe5c56669e10f8c9aef8a280
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811790"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="459c9-102">\<add> 的 \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="459c9-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="459c9-103">表示一个配置元素，该元素指定传递筛选器，该筛选器提供一种机制，用于在 IIS 中承载 Windows Communication Foundation (WCF) 应用程序时，选择适当的 Internet Information Services (IIS) 绑定。</span><span class="sxs-lookup"><span data-stu-id="459c9-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="459c9-104">语法</span><span class="sxs-lookup"><span data-stu-id="459c9-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="459c9-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="459c9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="459c9-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="459c9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="459c9-107">特性</span><span class="sxs-lookup"><span data-stu-id="459c9-107">Attributes</span></span>  
  
|<span data-ttu-id="459c9-108">特性</span><span class="sxs-lookup"><span data-stu-id="459c9-108">Attribute</span></span>|<span data-ttu-id="459c9-109">说明</span><span class="sxs-lookup"><span data-stu-id="459c9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="459c9-110">前缀</span><span class="sxs-lookup"><span data-stu-id="459c9-110">prefix</span></span>|<span data-ttu-id="459c9-111">用于与基址的一部分进行匹配的 URI。</span><span class="sxs-lookup"><span data-stu-id="459c9-111">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="459c9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="459c9-112">Child Elements</span></span>  
 <span data-ttu-id="459c9-113">无。</span><span class="sxs-lookup"><span data-stu-id="459c9-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="459c9-114">父元素</span><span class="sxs-lookup"><span data-stu-id="459c9-114">Parent Elements</span></span>  
  
|<span data-ttu-id="459c9-115">元素</span><span class="sxs-lookup"><span data-stu-id="459c9-115">Element</span></span>|<span data-ttu-id="459c9-116">说明</span><span class="sxs-lookup"><span data-stu-id="459c9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="459c9-117">用于指定传递筛选器的配置元素的集合，这些筛选器提供一种机制，用于在 IIS 中承载 Windows Communication Foundation (WCF) 应用程序时选取适当的 IIS 绑定。</span><span class="sxs-lookup"><span data-stu-id="459c9-117">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="459c9-118">注解</span><span class="sxs-lookup"><span data-stu-id="459c9-118">Remarks</span></span>  
 <span data-ttu-id="459c9-119">前缀筛选器为共享的宿主提供程序提供一种指定服务要使用的 URI 的方法。</span><span class="sxs-lookup"><span data-stu-id="459c9-119">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="459c9-120">它使得共享主机可以在同一站点上通过同一方案的不同基址承载多个应用程序。</span><span class="sxs-lookup"><span data-stu-id="459c9-120">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="459c9-121">IIS 网站是包含虚拟目录的虚拟应用程序的容器。</span><span class="sxs-lookup"><span data-stu-id="459c9-121">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="459c9-122">可通过一个或多个 IIS 绑定访问站点上的应用程序。</span><span class="sxs-lookup"><span data-stu-id="459c9-122">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="459c9-123">IIS 绑定提供两条信息：绑定协议和绑定信息。</span><span class="sxs-lookup"><span data-stu-id="459c9-123">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="459c9-124">绑定协议（例如 HTTP）定义发生通信所基于的方案，而绑定信息（例如 IP 地址、端口、主机头）包含用于访问站点的数据。</span><span class="sxs-lookup"><span data-stu-id="459c9-124">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="459c9-125">IIS 支持为每个站点指定多个 IIS 绑定，这会导致每个方案有多个基址。</span><span class="sxs-lookup"><span data-stu-id="459c9-125">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="459c9-126">因为在站点下承载的 WCF 服务只允许绑定到每个方案的一个基址，所以您可以使用前缀筛选器功能选取所需的承载服务的基址。</span><span class="sxs-lookup"><span data-stu-id="459c9-126">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="459c9-127">根据可选前缀列表筛选器筛选 IIS 提供的传入基址。</span><span class="sxs-lookup"><span data-stu-id="459c9-127">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="459c9-128">例如，你的站点可包含以下基址：</span><span class="sxs-lookup"><span data-stu-id="459c9-128">For example, your site can contain the following base addresses:</span></span>
  
```http
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="459c9-129">可以使用下面的配置文件在 appdomain 级指定前缀筛选器。</span><span class="sxs-lookup"><span data-stu-id="459c9-129">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 <span data-ttu-id="459c9-130">在此示例中，`net.tcp://test1.fabrikam.com:8000` 和 `http://test2.fabrikam.com:9000` 是允许传递的各自方案的唯一基址。</span><span class="sxs-lookup"><span data-stu-id="459c9-130">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="459c9-131">默认情况下，未指定前缀时，将传递所有地址。</span><span class="sxs-lookup"><span data-stu-id="459c9-131">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="459c9-132">而指定前缀后，将只允许传递该方案的匹配基址。</span><span class="sxs-lookup"><span data-stu-id="459c9-132">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="459c9-133">筛选器不支持任何通配符。</span><span class="sxs-lookup"><span data-stu-id="459c9-133">The filter does not support any wildcards.</span></span> <span data-ttu-id="459c9-134">此外，IIS 提供的基址可能有绑定到在 `baseAddressPrefixFilters` 列表中未列出的其他方案的地址。</span><span class="sxs-lookup"><span data-stu-id="459c9-134">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="459c9-135">不会筛选出这些地址。</span><span class="sxs-lookup"><span data-stu-id="459c9-135">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459c9-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="459c9-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="459c9-137">承载</span><span class="sxs-lookup"><span data-stu-id="459c9-137">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
