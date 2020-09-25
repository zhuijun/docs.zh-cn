---
title: <add> 的 <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: cd0ef5cc5f0f809bdafa23bd312e7e30fcdccc21
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181604"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="cdfb1-102">\<add> 的 \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="cdfb1-102">\<add> of \<baseAddresses></span></span>

<span data-ttu-id="cdfb1-103">表示一个配置元素，该元素指定服务主机所使用的基址。</span><span class="sxs-lookup"><span data-stu-id="cdfb1-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="cdfb1-104">语法</span><span class="sxs-lookup"><span data-stu-id="cdfb1-104">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="cdfb1-105">类型</span><span class="sxs-lookup"><span data-stu-id="cdfb1-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdfb1-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cdfb1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cdfb1-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cdfb1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdfb1-108">特性</span><span class="sxs-lookup"><span data-stu-id="cdfb1-108">Attributes</span></span>  
  
|<span data-ttu-id="cdfb1-109">属性</span><span class="sxs-lookup"><span data-stu-id="cdfb1-109">Attribute</span></span>|<span data-ttu-id="cdfb1-110">描述</span><span class="sxs-lookup"><span data-stu-id="cdfb1-110">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="cdfb1-111">一个字符串，指定服务主机所使用的基址。</span><span class="sxs-lookup"><span data-stu-id="cdfb1-111">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdfb1-112">子元素</span><span class="sxs-lookup"><span data-stu-id="cdfb1-112">Child Elements</span></span>  

 <span data-ttu-id="cdfb1-113">无。</span><span class="sxs-lookup"><span data-stu-id="cdfb1-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cdfb1-114">父元素</span><span class="sxs-lookup"><span data-stu-id="cdfb1-114">Parent Elements</span></span>  
  
|<span data-ttu-id="cdfb1-115">元素</span><span class="sxs-lookup"><span data-stu-id="cdfb1-115">Element</span></span>|<span data-ttu-id="cdfb1-116">描述</span><span class="sxs-lookup"><span data-stu-id="cdfb1-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="cdfb1-117">一个 `baseAddress` 元素集合。</span><span class="sxs-lookup"><span data-stu-id="cdfb1-117">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cdfb1-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="cdfb1-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="cdfb1-119">承载</span><span class="sxs-lookup"><span data-stu-id="cdfb1-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
