---
title: <synchronousReceive> 元素
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399499"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="6f467-102">\<synchronousReceive> 元素</span><span class="sxs-lookup"><span data-stu-id="6f467-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="6f467-103">此配置元素用于指定服务或客户端应用程序中用来接收消息的运行时行为。</span><span class="sxs-lookup"><span data-stu-id="6f467-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="6f467-104">它不具有任何属性或子元素。</span><span class="sxs-lookup"><span data-stu-id="6f467-104">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="6f467-105">语法</span><span class="sxs-lookup"><span data-stu-id="6f467-105">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f467-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6f467-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6f467-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6f467-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f467-108">特性</span><span class="sxs-lookup"><span data-stu-id="6f467-108">Attributes</span></span>  
 <span data-ttu-id="6f467-109">无。</span><span class="sxs-lookup"><span data-stu-id="6f467-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f467-110">子元素</span><span class="sxs-lookup"><span data-stu-id="6f467-110">Child Elements</span></span>  
 <span data-ttu-id="6f467-111">无。</span><span class="sxs-lookup"><span data-stu-id="6f467-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f467-112">父元素</span><span class="sxs-lookup"><span data-stu-id="6f467-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6f467-113">元素</span><span class="sxs-lookup"><span data-stu-id="6f467-113">Element</span></span>|<span data-ttu-id="6f467-114">说明</span><span class="sxs-lookup"><span data-stu-id="6f467-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6f467-115">指定终结点行为。</span><span class="sxs-lookup"><span data-stu-id="6f467-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f467-116">注解</span><span class="sxs-lookup"><span data-stu-id="6f467-116">Remarks</span></span>  
 <span data-ttu-id="6f467-117">使用此行为可指示通道侦听器使用同步接收，而非默认的异步接受。</span><span class="sxs-lookup"><span data-stu-id="6f467-117">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="6f467-118">Windows Communication Foundation （WCF）为每个接受的通道发出一个新线程来泵。</span><span class="sxs-lookup"><span data-stu-id="6f467-118">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="6f467-119">如果有许多通道，则可能出现线程溢出的情况。</span><span class="sxs-lookup"><span data-stu-id="6f467-119">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f467-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f467-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
