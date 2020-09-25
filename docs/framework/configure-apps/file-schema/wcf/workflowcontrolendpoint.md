---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 572ff7e119828897860944a430e5f51f5d1c3cad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194838"
---
# \<workflowControlEndpoint>

<span data-ttu-id="ba17b-101">此配置元素定义用于控制工作流实例的执行（创建、运行、挂起、终止等）的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="ba17b-101">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="ba17b-102">语法</span><span class="sxs-lookup"><span data-stu-id="ba17b-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba17b-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ba17b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ba17b-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ba17b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba17b-105">特性</span><span class="sxs-lookup"><span data-stu-id="ba17b-105">Attributes</span></span>  
  
|<span data-ttu-id="ba17b-106">属性</span><span class="sxs-lookup"><span data-stu-id="ba17b-106">Attribute</span></span>|<span data-ttu-id="ba17b-107">说明</span><span class="sxs-lookup"><span data-stu-id="ba17b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba17b-108">name</span><span class="sxs-lookup"><span data-stu-id="ba17b-108">name</span></span>|<span data-ttu-id="ba17b-109">一个字符串，指定标准终结点的配置的名称。</span><span class="sxs-lookup"><span data-stu-id="ba17b-109">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="ba17b-110">此名称在服务终结点的 `endpointConfiguration` 特性中用于将标准终结点链接到其配置。</span><span class="sxs-lookup"><span data-stu-id="ba17b-110">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba17b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ba17b-111">Child Elements</span></span>  

 <span data-ttu-id="ba17b-112">无。</span><span class="sxs-lookup"><span data-stu-id="ba17b-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba17b-113">父元素</span><span class="sxs-lookup"><span data-stu-id="ba17b-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ba17b-114">元素</span><span class="sxs-lookup"><span data-stu-id="ba17b-114">Element</span></span>|<span data-ttu-id="ba17b-115">描述</span><span class="sxs-lookup"><span data-stu-id="ba17b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="ba17b-116">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="ba17b-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba17b-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="ba17b-117">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
