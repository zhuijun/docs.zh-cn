---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855213"
---
# \<host>
<span data-ttu-id="937a7-101">指定服务主机的设置。</span><span class="sxs-lookup"><span data-stu-id="937a7-101">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="937a7-102">语法</span><span class="sxs-lookup"><span data-stu-id="937a7-102">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="937a7-103">类型</span><span class="sxs-lookup"><span data-stu-id="937a7-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="937a7-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="937a7-104">Attributes and Elements</span></span>  
 <span data-ttu-id="937a7-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="937a7-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="937a7-106">特性</span><span class="sxs-lookup"><span data-stu-id="937a7-106">Attributes</span></span>  
 <span data-ttu-id="937a7-107">无。</span><span class="sxs-lookup"><span data-stu-id="937a7-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="937a7-108">子元素</span><span class="sxs-lookup"><span data-stu-id="937a7-108">Child Elements</span></span>  
  
|<span data-ttu-id="937a7-109">元素</span><span class="sxs-lookup"><span data-stu-id="937a7-109">Element</span></span>|<span data-ttu-id="937a7-110">说明</span><span class="sxs-lookup"><span data-stu-id="937a7-110">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="937a7-111">`baseAddress` 元素的集合，指定服务主机所使用的基址。</span><span class="sxs-lookup"><span data-stu-id="937a7-111">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="937a7-112">一个配置元素，指定为打开或关闭服务主机预留的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="937a7-112">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="937a7-113">父元素</span><span class="sxs-lookup"><span data-stu-id="937a7-113">Parent Elements</span></span>  
  
|<span data-ttu-id="937a7-114">元素</span><span class="sxs-lookup"><span data-stu-id="937a7-114">Element</span></span>|<span data-ttu-id="937a7-115">说明</span><span class="sxs-lookup"><span data-stu-id="937a7-115">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="937a7-116">指定 Windows Communication Foundation （WCF）服务的设置。</span><span class="sxs-lookup"><span data-stu-id="937a7-116">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="937a7-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="937a7-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="937a7-118">承载</span><span class="sxs-lookup"><span data-stu-id="937a7-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
