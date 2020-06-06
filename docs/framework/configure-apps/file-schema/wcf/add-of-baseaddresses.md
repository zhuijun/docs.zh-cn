---
title: <add> 的 <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850585"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="50267-102">\<add> 的 \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="50267-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="50267-103">表示一个配置元素，该元素指定服务主机所使用的基址。</span><span class="sxs-lookup"><span data-stu-id="50267-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="50267-104">语法</span><span class="sxs-lookup"><span data-stu-id="50267-104">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="50267-105">类型</span><span class="sxs-lookup"><span data-stu-id="50267-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50267-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="50267-106">Attributes and Elements</span></span>  
 <span data-ttu-id="50267-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="50267-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50267-108">特性</span><span class="sxs-lookup"><span data-stu-id="50267-108">Attributes</span></span>  
  
|<span data-ttu-id="50267-109">属性</span><span class="sxs-lookup"><span data-stu-id="50267-109">Attribute</span></span>|<span data-ttu-id="50267-110">说明</span><span class="sxs-lookup"><span data-stu-id="50267-110">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="50267-111">一个字符串，指定服务主机所使用的基址。</span><span class="sxs-lookup"><span data-stu-id="50267-111">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50267-112">子元素</span><span class="sxs-lookup"><span data-stu-id="50267-112">Child Elements</span></span>  
 <span data-ttu-id="50267-113">无。</span><span class="sxs-lookup"><span data-stu-id="50267-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50267-114">父元素</span><span class="sxs-lookup"><span data-stu-id="50267-114">Parent Elements</span></span>  
  
|<span data-ttu-id="50267-115">元素</span><span class="sxs-lookup"><span data-stu-id="50267-115">Element</span></span>|<span data-ttu-id="50267-116">描述</span><span class="sxs-lookup"><span data-stu-id="50267-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="50267-117">一个 `baseAddress` 元素集合。</span><span class="sxs-lookup"><span data-stu-id="50267-117">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50267-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50267-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="50267-119">承载</span><span class="sxs-lookup"><span data-stu-id="50267-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
