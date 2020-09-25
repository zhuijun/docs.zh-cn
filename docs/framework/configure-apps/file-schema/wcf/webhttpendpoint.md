---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 3282871bf8dbd25726ada7003d3066b9a42e2366
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177977"
---
# \<webHttpEndpoint>

<span data-ttu-id="f5090-101">此配置元素定义具有 [\<webHttpBinding>](webhttpbinding.md) 自动添加行为的固定绑定的标准终结点 [\<webHttp>](webhttp.md) 。</span><span class="sxs-lookup"><span data-stu-id="f5090-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="f5090-102">在编写 REST 服务时，请使用此终结点。</span><span class="sxs-lookup"><span data-stu-id="f5090-102">Use this endpoint when writing a REST service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="f5090-103">语法</span><span class="sxs-lookup"><span data-stu-id="f5090-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5090-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f5090-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f5090-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f5090-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5090-106">特性</span><span class="sxs-lookup"><span data-stu-id="f5090-106">Attributes</span></span>  
  
|<span data-ttu-id="f5090-107">属性</span><span class="sxs-lookup"><span data-stu-id="f5090-107">Attribute</span></span>|<span data-ttu-id="f5090-108">描述</span><span class="sxs-lookup"><span data-stu-id="f5090-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5090-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="f5090-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="f5090-110">一个布尔值，指示是否启用自动格式选择。</span><span class="sxs-lookup"><span data-stu-id="f5090-110">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="f5090-111">如果启用了自动格式选择，基础结构将分析请求消息的 `Accept` 标头，并确定最适合的响应格式。</span><span class="sxs-lookup"><span data-stu-id="f5090-111">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="f5090-112">如果 `Accept` 标头未指定适合的响应格式，则基础结构将使用请求消息的 `Content-Type`，或使用操作的默认响应格式。</span><span class="sxs-lookup"><span data-stu-id="f5090-112">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="f5090-113">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="f5090-113">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="f5090-114">一个指定默认传出响应格式的特性。</span><span class="sxs-lookup"><span data-stu-id="f5090-114">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="f5090-115">此特性的类型为 <xref:System.ServiceModel.Web.WebMessageFormat></span><span class="sxs-lookup"><span data-stu-id="f5090-115">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="f5090-116">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="f5090-116">helpEnabled</span></span>|<span data-ttu-id="f5090-117">一个布尔值，指示是否为终结点启用了 HTTP 帮助页。</span><span class="sxs-lookup"><span data-stu-id="f5090-117">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="f5090-118">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="f5090-118">webEndpointType</span></span>|<span data-ttu-id="f5090-119">一个字符串，指定终结点的类型。</span><span class="sxs-lookup"><span data-stu-id="f5090-119">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5090-120">子元素</span><span class="sxs-lookup"><span data-stu-id="f5090-120">Child Elements</span></span>  

 <span data-ttu-id="f5090-121">无。</span><span class="sxs-lookup"><span data-stu-id="f5090-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5090-122">父元素</span><span class="sxs-lookup"><span data-stu-id="f5090-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f5090-123">元素</span><span class="sxs-lookup"><span data-stu-id="f5090-123">Element</span></span>|<span data-ttu-id="f5090-124">描述</span><span class="sxs-lookup"><span data-stu-id="f5090-124">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="f5090-125">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="f5090-125">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5090-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="f5090-126">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
