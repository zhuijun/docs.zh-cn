---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 89ebad118c1c9210357d8fd281c9216b7f64b450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398072"
---
# \<defaultPorts>
<span data-ttu-id="1abdc-101">一个默认端口集合，列出客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="1abdc-101">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="1abdc-102">语法</span><span class="sxs-lookup"><span data-stu-id="1abdc-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1abdc-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1abdc-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1abdc-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1abdc-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1abdc-105">特性</span><span class="sxs-lookup"><span data-stu-id="1abdc-105">Attributes</span></span>  
 <span data-ttu-id="1abdc-106">无。</span><span class="sxs-lookup"><span data-stu-id="1abdc-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1abdc-107">子元素</span><span class="sxs-lookup"><span data-stu-id="1abdc-107">Child Elements</span></span>  
  
|<span data-ttu-id="1abdc-108">元素</span><span class="sxs-lookup"><span data-stu-id="1abdc-108">Element</span></span>|<span data-ttu-id="1abdc-109">说明</span><span class="sxs-lookup"><span data-stu-id="1abdc-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1abdc-110">\<add>个\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="1abdc-110">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="1abdc-111">客户端应用程序侦听的默认通信终结点。</span><span class="sxs-lookup"><span data-stu-id="1abdc-111">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1abdc-112">父元素</span><span class="sxs-lookup"><span data-stu-id="1abdc-112">Parent Elements</span></span>  
  
|<span data-ttu-id="1abdc-113">元素</span><span class="sxs-lookup"><span data-stu-id="1abdc-113">Element</span></span>|<span data-ttu-id="1abdc-114">说明</span><span class="sxs-lookup"><span data-stu-id="1abdc-114">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="1abdc-115">默认端口列表。</span><span class="sxs-lookup"><span data-stu-id="1abdc-115">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1abdc-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1abdc-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
