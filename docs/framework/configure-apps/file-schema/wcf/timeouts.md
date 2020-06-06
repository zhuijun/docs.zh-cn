---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854967"
---
# \<timeOuts>
<span data-ttu-id="57daf-101">表示一个配置元素，该元素指定允许服务主机打开或关闭的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="57daf-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="57daf-102">语法</span><span class="sxs-lookup"><span data-stu-id="57daf-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57daf-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="57daf-103">Attributes and Elements</span></span>  
 <span data-ttu-id="57daf-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="57daf-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57daf-105">特性</span><span class="sxs-lookup"><span data-stu-id="57daf-105">Attributes</span></span>  
  
|<span data-ttu-id="57daf-106">属性</span><span class="sxs-lookup"><span data-stu-id="57daf-106">Attribute</span></span>|<span data-ttu-id="57daf-107">说明</span><span class="sxs-lookup"><span data-stu-id="57daf-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="57daf-108">一个 <xref:System.TimeSpan> 值，指定为关闭服务主机预留的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="57daf-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="57daf-109">一个 <xref:System.TimeSpan> 值，指定为打开或关闭服务主机预留的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="57daf-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57daf-110">子元素</span><span class="sxs-lookup"><span data-stu-id="57daf-110">Child Elements</span></span>  
 <span data-ttu-id="57daf-111">无。</span><span class="sxs-lookup"><span data-stu-id="57daf-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57daf-112">父元素</span><span class="sxs-lookup"><span data-stu-id="57daf-112">Parent Elements</span></span>  
  
|<span data-ttu-id="57daf-113">元素</span><span class="sxs-lookup"><span data-stu-id="57daf-113">Element</span></span>|<span data-ttu-id="57daf-114">描述</span><span class="sxs-lookup"><span data-stu-id="57daf-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="57daf-115">一个指定服务主机设置的配置元素。</span><span class="sxs-lookup"><span data-stu-id="57daf-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57daf-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57daf-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="57daf-117">承载</span><span class="sxs-lookup"><span data-stu-id="57daf-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
