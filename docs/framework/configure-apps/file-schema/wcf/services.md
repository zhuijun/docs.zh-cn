---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 02d1d530f37f5082153c9aa6b9993fc4009917f5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854977"
---
# \<services>
<span data-ttu-id="ab6a5-101">服务是在配置文件的 `services` 节中定义的。</span><span class="sxs-lookup"><span data-stu-id="ab6a5-101">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="ab6a5-102">每个服务都有自己的 `service` 配置节。</span><span class="sxs-lookup"><span data-stu-id="ab6a5-102">Each service has its own `service` configuration section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**  
  
## <a name="syntax"></a><span data-ttu-id="ab6a5-103">语法</span><span class="sxs-lookup"><span data-stu-id="ab6a5-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab6a5-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ab6a5-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ab6a5-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ab6a5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab6a5-106">特性</span><span class="sxs-lookup"><span data-stu-id="ab6a5-106">Attributes</span></span>  
 <span data-ttu-id="ab6a5-107">无</span><span class="sxs-lookup"><span data-stu-id="ab6a5-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab6a5-108">子元素</span><span class="sxs-lookup"><span data-stu-id="ab6a5-108">Child Elements</span></span>  
  
|<span data-ttu-id="ab6a5-109">元素</span><span class="sxs-lookup"><span data-stu-id="ab6a5-109">Element</span></span>|<span data-ttu-id="ab6a5-110">说明</span><span class="sxs-lookup"><span data-stu-id="ab6a5-110">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="ab6a5-111">定义特定服务的服务协定、行为和终结点。</span><span class="sxs-lookup"><span data-stu-id="ab6a5-111">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab6a5-112">父元素</span><span class="sxs-lookup"><span data-stu-id="ab6a5-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ab6a5-113">元素</span><span class="sxs-lookup"><span data-stu-id="ab6a5-113">Element</span></span>|<span data-ttu-id="ab6a5-114">说明</span><span class="sxs-lookup"><span data-stu-id="ab6a5-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="ab6a5-115">所有 Windows Communication Foundation (WCF) 配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="ab6a5-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab6a5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab6a5-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
