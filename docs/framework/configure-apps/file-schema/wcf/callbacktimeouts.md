---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 98523489aacebf910bcf5d81c479819183887dff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198881"
---
# \<callbackTimeouts>

<span data-ttu-id="dc6de-101">在双工回调协定方案中指定使事务从服务器流动到客户端时的超时值。</span><span class="sxs-lookup"><span data-stu-id="dc6de-101">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="dc6de-102">语法</span><span class="sxs-lookup"><span data-stu-id="dc6de-102">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="dc6de-103">类型</span><span class="sxs-lookup"><span data-stu-id="dc6de-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc6de-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="dc6de-104">Attributes and Elements</span></span>  

 <span data-ttu-id="dc6de-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dc6de-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc6de-106">特性</span><span class="sxs-lookup"><span data-stu-id="dc6de-106">Attributes</span></span>  
  
|<span data-ttu-id="dc6de-107">属性</span><span class="sxs-lookup"><span data-stu-id="dc6de-107">Attribute</span></span>|<span data-ttu-id="dc6de-108">描述</span><span class="sxs-lookup"><span data-stu-id="dc6de-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="dc6de-109">一个 <xref:System.TimeSpan> 值，指定时间间隔，事务必须在此期间完成，否则会自动终止。</span><span class="sxs-lookup"><span data-stu-id="dc6de-109">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="dc6de-110">默认值为 "00:00:00"。</span><span class="sxs-lookup"><span data-stu-id="dc6de-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc6de-111">子元素</span><span class="sxs-lookup"><span data-stu-id="dc6de-111">Child Elements</span></span>  

 <span data-ttu-id="dc6de-112">无。</span><span class="sxs-lookup"><span data-stu-id="dc6de-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc6de-113">父元素</span><span class="sxs-lookup"><span data-stu-id="dc6de-113">Parent Elements</span></span>  
  
|<span data-ttu-id="dc6de-114">元素</span><span class="sxs-lookup"><span data-stu-id="dc6de-114">Element</span></span>|<span data-ttu-id="dc6de-115">描述</span><span class="sxs-lookup"><span data-stu-id="dc6de-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="dc6de-116">指定终结点行为。</span><span class="sxs-lookup"><span data-stu-id="dc6de-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc6de-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="dc6de-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
