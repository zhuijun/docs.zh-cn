---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: 5e3ca9c4a43432d7f5da6d8816b6a2b984851050
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177834"
---
# \<webScriptEndpoint>

<span data-ttu-id="30001-101">此配置元素定义具有 [\<webHttpBinding>](webhttpbinding.md) 自动添加行为的固定绑定的标准终结点 [\<enableWebScript>](enablewebscript.md) 。</span><span class="sxs-lookup"><span data-stu-id="30001-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="30001-102">在编写从 ASP.NET AJAX 应用程序中调用的服务时，请使用此终结点。</span><span class="sxs-lookup"><span data-stu-id="30001-102">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="30001-103">语法</span><span class="sxs-lookup"><span data-stu-id="30001-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30001-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="30001-104">Attributes and Elements</span></span>  

 <span data-ttu-id="30001-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="30001-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30001-106">特性</span><span class="sxs-lookup"><span data-stu-id="30001-106">Attributes</span></span>  
  
|<span data-ttu-id="30001-107">属性</span><span class="sxs-lookup"><span data-stu-id="30001-107">Attribute</span></span>|<span data-ttu-id="30001-108">描述</span><span class="sxs-lookup"><span data-stu-id="30001-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30001-109">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="30001-109">webEndpointType</span></span>|<span data-ttu-id="30001-110">一个字符串，指定终结点的类型。</span><span class="sxs-lookup"><span data-stu-id="30001-110">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30001-111">子元素</span><span class="sxs-lookup"><span data-stu-id="30001-111">Child Elements</span></span>  

 <span data-ttu-id="30001-112">无。</span><span class="sxs-lookup"><span data-stu-id="30001-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30001-113">父元素</span><span class="sxs-lookup"><span data-stu-id="30001-113">Parent Elements</span></span>  
  
|<span data-ttu-id="30001-114">元素</span><span class="sxs-lookup"><span data-stu-id="30001-114">Element</span></span>|<span data-ttu-id="30001-115">描述</span><span class="sxs-lookup"><span data-stu-id="30001-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="30001-116">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="30001-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30001-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="30001-117">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
