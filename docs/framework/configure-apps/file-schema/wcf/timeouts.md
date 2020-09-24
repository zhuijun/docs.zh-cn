---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: f7e513bb5c486fa5f7c39c9b2e3cfcd26bd7c219
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157091"
---
# \<timeOuts>

<span data-ttu-id="4f8c4-101">表示一个配置元素，该元素指定允许服务主机打开或关闭的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="4f8c4-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="4f8c4-102">语法</span><span class="sxs-lookup"><span data-stu-id="4f8c4-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f8c4-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4f8c4-103">Attributes and Elements</span></span>  

 <span data-ttu-id="4f8c4-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4f8c4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f8c4-105">特性</span><span class="sxs-lookup"><span data-stu-id="4f8c4-105">Attributes</span></span>  
  
|<span data-ttu-id="4f8c4-106">属性</span><span class="sxs-lookup"><span data-stu-id="4f8c4-106">Attribute</span></span>|<span data-ttu-id="4f8c4-107">描述</span><span class="sxs-lookup"><span data-stu-id="4f8c4-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="4f8c4-108">一个 <xref:System.TimeSpan> 值，指定为关闭服务主机预留的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="4f8c4-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="4f8c4-109">一个 <xref:System.TimeSpan> 值，指定为打开或关闭服务主机预留的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="4f8c4-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f8c4-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4f8c4-110">Child Elements</span></span>  

 <span data-ttu-id="4f8c4-111">无。</span><span class="sxs-lookup"><span data-stu-id="4f8c4-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f8c4-112">父元素</span><span class="sxs-lookup"><span data-stu-id="4f8c4-112">Parent Elements</span></span>  
  
|<span data-ttu-id="4f8c4-113">元素</span><span class="sxs-lookup"><span data-stu-id="4f8c4-113">Element</span></span>|<span data-ttu-id="4f8c4-114">描述</span><span class="sxs-lookup"><span data-stu-id="4f8c4-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="4f8c4-115">一个指定服务主机设置的配置元素。</span><span class="sxs-lookup"><span data-stu-id="4f8c4-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f8c4-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="4f8c4-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="4f8c4-117">承载</span><span class="sxs-lookup"><span data-stu-id="4f8c4-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
