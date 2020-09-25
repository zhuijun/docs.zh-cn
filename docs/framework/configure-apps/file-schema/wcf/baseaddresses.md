---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 3b6cebd178ac5cd30fa034bd961d2d08075771d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201533"
---
# \<baseAddresses>

<span data-ttu-id="258b0-101">表示一个 `baseAddress` 元素集合，这些元素是自承载环境中服务主机的基址。</span><span class="sxs-lookup"><span data-stu-id="258b0-101">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="258b0-102">如果存在基址，则可以使用相对于基址的地址配置终结点。</span><span class="sxs-lookup"><span data-stu-id="258b0-102">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**  
  
## <a name="syntax"></a><span data-ttu-id="258b0-103">语法</span><span class="sxs-lookup"><span data-stu-id="258b0-103">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="258b0-104">类型</span><span class="sxs-lookup"><span data-stu-id="258b0-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="258b0-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="258b0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="258b0-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="258b0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="258b0-107">特性</span><span class="sxs-lookup"><span data-stu-id="258b0-107">Attributes</span></span>  

 <span data-ttu-id="258b0-108">无。</span><span class="sxs-lookup"><span data-stu-id="258b0-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="258b0-109">子元素</span><span class="sxs-lookup"><span data-stu-id="258b0-109">Child Elements</span></span>  
  
|<span data-ttu-id="258b0-110">元素</span><span class="sxs-lookup"><span data-stu-id="258b0-110">Element</span></span>|<span data-ttu-id="258b0-111">描述</span><span class="sxs-lookup"><span data-stu-id="258b0-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|<span data-ttu-id="258b0-112">一个配置元素，指定服务主机所使用的基址。</span><span class="sxs-lookup"><span data-stu-id="258b0-112">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="258b0-113">父元素</span><span class="sxs-lookup"><span data-stu-id="258b0-113">Parent Elements</span></span>  
  
|<span data-ttu-id="258b0-114">元素</span><span class="sxs-lookup"><span data-stu-id="258b0-114">Element</span></span>|<span data-ttu-id="258b0-115">描述</span><span class="sxs-lookup"><span data-stu-id="258b0-115">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="258b0-116">一个指定服务主机设置的配置元素。</span><span class="sxs-lookup"><span data-stu-id="258b0-116">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="258b0-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="258b0-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="258b0-118">承载</span><span class="sxs-lookup"><span data-stu-id="258b0-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
