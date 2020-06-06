---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: a1c2ee68fb039e24e1462148cb52daf1bb57f8ed
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398111"
---
# \<clientVia>
<span data-ttu-id="80967-101">指定应为其创建传输通道的 URI。</span><span class="sxs-lookup"><span data-stu-id="80967-101">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="80967-102">有关详细信息，请参阅 <xref:System.ServiceModel.Description.ClientViaBehavior>。</span><span class="sxs-lookup"><span data-stu-id="80967-102">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="80967-103">语法</span><span class="sxs-lookup"><span data-stu-id="80967-103">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80967-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="80967-104">Attributes and Elements</span></span>  
 <span data-ttu-id="80967-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="80967-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80967-106">特性</span><span class="sxs-lookup"><span data-stu-id="80967-106">Attributes</span></span>  
  
|<span data-ttu-id="80967-107">属性</span><span class="sxs-lookup"><span data-stu-id="80967-107">Attribute</span></span>|<span data-ttu-id="80967-108">说明</span><span class="sxs-lookup"><span data-stu-id="80967-108">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="80967-109">一个指定 URI 的字符串，此 URI 指示消息应采用的路由。</span><span class="sxs-lookup"><span data-stu-id="80967-109">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80967-110">子元素</span><span class="sxs-lookup"><span data-stu-id="80967-110">Child Elements</span></span>  
 <span data-ttu-id="80967-111">无</span><span class="sxs-lookup"><span data-stu-id="80967-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80967-112">父元素</span><span class="sxs-lookup"><span data-stu-id="80967-112">Parent Elements</span></span>  
  
|<span data-ttu-id="80967-113">元素</span><span class="sxs-lookup"><span data-stu-id="80967-113">Element</span></span>|<span data-ttu-id="80967-114">描述</span><span class="sxs-lookup"><span data-stu-id="80967-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="80967-115">指定终结点行为。</span><span class="sxs-lookup"><span data-stu-id="80967-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80967-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="80967-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
