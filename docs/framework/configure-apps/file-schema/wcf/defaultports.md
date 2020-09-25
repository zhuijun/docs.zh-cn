---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 08ca8a2bfcf5b905152f7e64a45cbae4992a7b78
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192368"
---
# \<defaultPorts>

<span data-ttu-id="0bbae-101">一个默认端口集合，列出客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="0bbae-101">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="0bbae-102">语法</span><span class="sxs-lookup"><span data-stu-id="0bbae-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bbae-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0bbae-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0bbae-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0bbae-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bbae-105">特性</span><span class="sxs-lookup"><span data-stu-id="0bbae-105">Attributes</span></span>  

 <span data-ttu-id="0bbae-106">无。</span><span class="sxs-lookup"><span data-stu-id="0bbae-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0bbae-107">子元素</span><span class="sxs-lookup"><span data-stu-id="0bbae-107">Child Elements</span></span>  
  
|<span data-ttu-id="0bbae-108">元素</span><span class="sxs-lookup"><span data-stu-id="0bbae-108">Element</span></span>|<span data-ttu-id="0bbae-109">描述</span><span class="sxs-lookup"><span data-stu-id="0bbae-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bbae-110">\<defaultPorts> 的 \<add></span><span class="sxs-lookup"><span data-stu-id="0bbae-110">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="0bbae-111">客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="0bbae-111">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0bbae-112">父元素</span><span class="sxs-lookup"><span data-stu-id="0bbae-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0bbae-113">元素</span><span class="sxs-lookup"><span data-stu-id="0bbae-113">Element</span></span>|<span data-ttu-id="0bbae-114">描述</span><span class="sxs-lookup"><span data-stu-id="0bbae-114">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="0bbae-115">默认端口列表。</span><span class="sxs-lookup"><span data-stu-id="0bbae-115">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bbae-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="0bbae-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
