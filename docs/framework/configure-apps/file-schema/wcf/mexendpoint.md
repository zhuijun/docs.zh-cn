---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855111"
---
# \<mexEndpoint>
<span data-ttu-id="1cba4-101">此配置元素定义具有固定 IMetadataExchange 协定的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="1cba4-101">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="1cba4-102">由于所有元数据交换终结点都指定 IMetadataExchange 作为其协定，因此可以使用此标准终结点，而不必定义您自己的终结点。</span><span class="sxs-lookup"><span data-stu-id="1cba4-102">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="1cba4-103">语法</span><span class="sxs-lookup"><span data-stu-id="1cba4-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1cba4-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1cba4-104">Attributes and Elements</span></span>  
 <span data-ttu-id="1cba4-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1cba4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1cba4-106">特性</span><span class="sxs-lookup"><span data-stu-id="1cba4-106">Attributes</span></span>  
  
|<span data-ttu-id="1cba4-107">属性</span><span class="sxs-lookup"><span data-stu-id="1cba4-107">Attribute</span></span>|<span data-ttu-id="1cba4-108">说明</span><span class="sxs-lookup"><span data-stu-id="1cba4-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1cba4-109">name</span><span class="sxs-lookup"><span data-stu-id="1cba4-109">name</span></span>|<span data-ttu-id="1cba4-110">一个字符串，指定标准终结点的配置的名称。</span><span class="sxs-lookup"><span data-stu-id="1cba4-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="1cba4-111">此名称在服务终结点的 `endpointConfiguration` 特性中用于将标准终结点链接到其配置。</span><span class="sxs-lookup"><span data-stu-id="1cba4-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1cba4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1cba4-112">Child Elements</span></span>  
 <span data-ttu-id="1cba4-113">无。</span><span class="sxs-lookup"><span data-stu-id="1cba4-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1cba4-114">父元素</span><span class="sxs-lookup"><span data-stu-id="1cba4-114">Parent Elements</span></span>  
  
|<span data-ttu-id="1cba4-115">元素</span><span class="sxs-lookup"><span data-stu-id="1cba4-115">Element</span></span>|<span data-ttu-id="1cba4-116">描述</span><span class="sxs-lookup"><span data-stu-id="1cba4-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="1cba4-117">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="1cba4-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
