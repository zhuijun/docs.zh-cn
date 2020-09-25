---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 11378e6cc8cbe8e631fd77ab74c91a616099df52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190080"
---
# \<enableWebScript>

<span data-ttu-id="1ce5b-101">通过此元素启用的终结点行为可以使用 ASP.NET AJAX 网页中的服务。</span><span class="sxs-lookup"><span data-stu-id="1ce5b-101">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="1ce5b-102">语法</span><span class="sxs-lookup"><span data-stu-id="1ce5b-102">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ce5b-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1ce5b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="1ce5b-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1ce5b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ce5b-105">特性</span><span class="sxs-lookup"><span data-stu-id="1ce5b-105">Attributes</span></span>  

 <span data-ttu-id="1ce5b-106">无。</span><span class="sxs-lookup"><span data-stu-id="1ce5b-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1ce5b-107">子元素</span><span class="sxs-lookup"><span data-stu-id="1ce5b-107">Child Elements</span></span>  

 <span data-ttu-id="1ce5b-108">无。</span><span class="sxs-lookup"><span data-stu-id="1ce5b-108">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ce5b-109">父元素</span><span class="sxs-lookup"><span data-stu-id="1ce5b-109">Parent Elements</span></span>  
  
|<span data-ttu-id="1ce5b-110">元素</span><span class="sxs-lookup"><span data-stu-id="1ce5b-110">Element</span></span>|<span data-ttu-id="1ce5b-111">描述</span><span class="sxs-lookup"><span data-stu-id="1ce5b-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1ce5b-112">指定终结点行为集。</span><span class="sxs-lookup"><span data-stu-id="1ce5b-112">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ce5b-113">备注</span><span class="sxs-lookup"><span data-stu-id="1ce5b-113">Remarks</span></span>  

 <span data-ttu-id="1ce5b-114">此行为只应与 [\<webHttpBinding>](webhttpbinding.md) 标准绑定或 [\<webMessageEncoding>](webmessageencoding.md) 绑定元素一起使用。</span><span class="sxs-lookup"><span data-stu-id="1ce5b-114">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="1ce5b-115">有关此行为的更多信息，请参见 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。</span><span class="sxs-lookup"><span data-stu-id="1ce5b-115">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce5b-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="1ce5b-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="1ce5b-117">AJAX 集成和 JSON 支持</span><span class="sxs-lookup"><span data-stu-id="1ce5b-117">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
