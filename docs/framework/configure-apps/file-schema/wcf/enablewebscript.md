---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400389"
---
# \<enableWebScript>
<span data-ttu-id="113be-101">通过此元素启用的终结点行为可以使用 ASP.NET AJAX 网页中的服务。</span><span class="sxs-lookup"><span data-stu-id="113be-101">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="113be-102">语法</span><span class="sxs-lookup"><span data-stu-id="113be-102">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="113be-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="113be-103">Attributes and Elements</span></span>  
 <span data-ttu-id="113be-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="113be-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="113be-105">特性</span><span class="sxs-lookup"><span data-stu-id="113be-105">Attributes</span></span>  
 <span data-ttu-id="113be-106">无。</span><span class="sxs-lookup"><span data-stu-id="113be-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="113be-107">子元素</span><span class="sxs-lookup"><span data-stu-id="113be-107">Child Elements</span></span>  
 <span data-ttu-id="113be-108">无。</span><span class="sxs-lookup"><span data-stu-id="113be-108">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="113be-109">父元素</span><span class="sxs-lookup"><span data-stu-id="113be-109">Parent Elements</span></span>  
  
|<span data-ttu-id="113be-110">元素</span><span class="sxs-lookup"><span data-stu-id="113be-110">Element</span></span>|<span data-ttu-id="113be-111">说明</span><span class="sxs-lookup"><span data-stu-id="113be-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="113be-112">指定终结点行为集。</span><span class="sxs-lookup"><span data-stu-id="113be-112">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="113be-113">注解</span><span class="sxs-lookup"><span data-stu-id="113be-113">Remarks</span></span>  
 <span data-ttu-id="113be-114">此行为只应与 [\<webHttpBinding>](webhttpbinding.md) 标准绑定或 [\<webMessageEncoding>](webmessageencoding.md) 绑定元素一起使用。</span><span class="sxs-lookup"><span data-stu-id="113be-114">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="113be-115">有关此行为的更多信息，请参见 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。</span><span class="sxs-lookup"><span data-stu-id="113be-115">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="113be-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="113be-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="113be-117">AJAX 集成和 JSON 支持</span><span class="sxs-lookup"><span data-stu-id="113be-117">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
