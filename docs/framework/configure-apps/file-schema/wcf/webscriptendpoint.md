---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854813"
---
# \<webScriptEndpoint>
<span data-ttu-id="50154-101">此配置元素定义具有 [\<webHttpBinding>](webhttpbinding.md) 自动添加行为的固定绑定的标准终结点 [\<enableWebScript>](enablewebscript.md) 。</span><span class="sxs-lookup"><span data-stu-id="50154-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="50154-102">在编写从 ASP.NET AJAX 应用程序中调用的服务时，请使用此终结点。</span><span class="sxs-lookup"><span data-stu-id="50154-102">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="50154-103">语法</span><span class="sxs-lookup"><span data-stu-id="50154-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50154-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="50154-104">Attributes and Elements</span></span>  
 <span data-ttu-id="50154-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="50154-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50154-106">特性</span><span class="sxs-lookup"><span data-stu-id="50154-106">Attributes</span></span>  
  
|<span data-ttu-id="50154-107">属性</span><span class="sxs-lookup"><span data-stu-id="50154-107">Attribute</span></span>|<span data-ttu-id="50154-108">说明</span><span class="sxs-lookup"><span data-stu-id="50154-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50154-109">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="50154-109">webEndpointType</span></span>|<span data-ttu-id="50154-110">一个字符串，指定终结点的类型。</span><span class="sxs-lookup"><span data-stu-id="50154-110">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50154-111">子元素</span><span class="sxs-lookup"><span data-stu-id="50154-111">Child Elements</span></span>  
 <span data-ttu-id="50154-112">无。</span><span class="sxs-lookup"><span data-stu-id="50154-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50154-113">父元素</span><span class="sxs-lookup"><span data-stu-id="50154-113">Parent Elements</span></span>  
  
|<span data-ttu-id="50154-114">元素</span><span class="sxs-lookup"><span data-stu-id="50154-114">Element</span></span>|<span data-ttu-id="50154-115">描述</span><span class="sxs-lookup"><span data-stu-id="50154-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="50154-116">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="50154-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50154-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50154-117">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
