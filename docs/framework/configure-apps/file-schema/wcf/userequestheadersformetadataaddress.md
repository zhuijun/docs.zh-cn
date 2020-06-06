---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399207"
---
# \<useRequestHeadersForMetadataAddress>
<span data-ttu-id="42fbf-101">允许从请求消息头中检索元数据地址信息。</span><span class="sxs-lookup"><span data-stu-id="42fbf-101">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="42fbf-102">语法</span><span class="sxs-lookup"><span data-stu-id="42fbf-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42fbf-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="42fbf-103">Attributes and Elements</span></span>  
 <span data-ttu-id="42fbf-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="42fbf-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42fbf-105">特性</span><span class="sxs-lookup"><span data-stu-id="42fbf-105">Attributes</span></span>  
 <span data-ttu-id="42fbf-106">无。</span><span class="sxs-lookup"><span data-stu-id="42fbf-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="42fbf-107">子元素</span><span class="sxs-lookup"><span data-stu-id="42fbf-107">Child Elements</span></span>  
  
|<span data-ttu-id="42fbf-108">元素</span><span class="sxs-lookup"><span data-stu-id="42fbf-108">Element</span></span>|<span data-ttu-id="42fbf-109">说明</span><span class="sxs-lookup"><span data-stu-id="42fbf-109">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="42fbf-110">一个默认端口集合，列出客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="42fbf-110">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="42fbf-111">父元素</span><span class="sxs-lookup"><span data-stu-id="42fbf-111">Parent Elements</span></span>  
  
|<span data-ttu-id="42fbf-112">元素</span><span class="sxs-lookup"><span data-stu-id="42fbf-112">Element</span></span>|<span data-ttu-id="42fbf-113">说明</span><span class="sxs-lookup"><span data-stu-id="42fbf-113">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="42fbf-114">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="42fbf-114">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42fbf-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42fbf-115">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
