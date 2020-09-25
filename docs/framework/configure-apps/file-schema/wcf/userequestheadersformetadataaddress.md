---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: a323e6da0eb173e303d70cc3b7309b898a805573
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172809"
---
# \<useRequestHeadersForMetadataAddress>

<span data-ttu-id="ce7ac-101">允许从请求消息头中检索元数据地址信息。</span><span class="sxs-lookup"><span data-stu-id="ce7ac-101">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="ce7ac-102">语法</span><span class="sxs-lookup"><span data-stu-id="ce7ac-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce7ac-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ce7ac-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ce7ac-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ce7ac-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce7ac-105">特性</span><span class="sxs-lookup"><span data-stu-id="ce7ac-105">Attributes</span></span>  

 <span data-ttu-id="ce7ac-106">无。</span><span class="sxs-lookup"><span data-stu-id="ce7ac-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ce7ac-107">子元素</span><span class="sxs-lookup"><span data-stu-id="ce7ac-107">Child Elements</span></span>  
  
|<span data-ttu-id="ce7ac-108">元素</span><span class="sxs-lookup"><span data-stu-id="ce7ac-108">Element</span></span>|<span data-ttu-id="ce7ac-109">描述</span><span class="sxs-lookup"><span data-stu-id="ce7ac-109">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="ce7ac-110">一个默认端口集合，列出客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="ce7ac-110">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce7ac-111">父元素</span><span class="sxs-lookup"><span data-stu-id="ce7ac-111">Parent Elements</span></span>  
  
|<span data-ttu-id="ce7ac-112">元素</span><span class="sxs-lookup"><span data-stu-id="ce7ac-112">Element</span></span>|<span data-ttu-id="ce7ac-113">描述</span><span class="sxs-lookup"><span data-stu-id="ce7ac-113">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ce7ac-114">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="ce7ac-114">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce7ac-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="ce7ac-115">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
