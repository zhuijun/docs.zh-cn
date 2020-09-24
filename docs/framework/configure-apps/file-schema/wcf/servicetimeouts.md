---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 92d3de42daf6f7baf288e3e74242381a60e76618
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153594"
---
# \<serviceTimeouts>

<span data-ttu-id="21a3f-101">指定服务的超时。</span><span class="sxs-lookup"><span data-stu-id="21a3f-101">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="21a3f-102">语法</span><span class="sxs-lookup"><span data-stu-id="21a3f-102">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="21a3f-103">类型</span><span class="sxs-lookup"><span data-stu-id="21a3f-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21a3f-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="21a3f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="21a3f-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="21a3f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21a3f-106">特性</span><span class="sxs-lookup"><span data-stu-id="21a3f-106">Attributes</span></span>  
  
|<span data-ttu-id="21a3f-107">属性</span><span class="sxs-lookup"><span data-stu-id="21a3f-107">Attribute</span></span>|<span data-ttu-id="21a3f-108">描述</span><span class="sxs-lookup"><span data-stu-id="21a3f-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="21a3f-109">一个 <xref:System.TimeSpan> 值，指定事务从客户端流动到服务器所必须经历的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="21a3f-109">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="21a3f-110">默认值为 "00:00:00"。</span><span class="sxs-lookup"><span data-stu-id="21a3f-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21a3f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="21a3f-111">Child Elements</span></span>  

 <span data-ttu-id="21a3f-112">无。</span><span class="sxs-lookup"><span data-stu-id="21a3f-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21a3f-113">父元素</span><span class="sxs-lookup"><span data-stu-id="21a3f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="21a3f-114">元素</span><span class="sxs-lookup"><span data-stu-id="21a3f-114">Element</span></span>|<span data-ttu-id="21a3f-115">描述</span><span class="sxs-lookup"><span data-stu-id="21a3f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="21a3f-116">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="21a3f-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21a3f-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="21a3f-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
