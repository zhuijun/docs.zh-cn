---
title: <synchronousReceive> 元素
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: 2073d115dd87d513a6e48b8b585fed4b49d5bb32
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157169"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="385ed-102">\<synchronousReceive> 元素</span><span class="sxs-lookup"><span data-stu-id="385ed-102">\<synchronousReceive> element</span></span>

<span data-ttu-id="385ed-103">此配置元素用于指定服务或客户端应用程序中用来接收消息的运行时行为。</span><span class="sxs-lookup"><span data-stu-id="385ed-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="385ed-104">它不具有任何属性或子元素。</span><span class="sxs-lookup"><span data-stu-id="385ed-104">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="385ed-105">语法</span><span class="sxs-lookup"><span data-stu-id="385ed-105">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="385ed-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="385ed-106">Attributes and Elements</span></span>  

 <span data-ttu-id="385ed-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="385ed-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="385ed-108">特性</span><span class="sxs-lookup"><span data-stu-id="385ed-108">Attributes</span></span>  

 <span data-ttu-id="385ed-109">无。</span><span class="sxs-lookup"><span data-stu-id="385ed-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="385ed-110">子元素</span><span class="sxs-lookup"><span data-stu-id="385ed-110">Child Elements</span></span>  

 <span data-ttu-id="385ed-111">无。</span><span class="sxs-lookup"><span data-stu-id="385ed-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="385ed-112">父元素</span><span class="sxs-lookup"><span data-stu-id="385ed-112">Parent Elements</span></span>  
  
|<span data-ttu-id="385ed-113">元素</span><span class="sxs-lookup"><span data-stu-id="385ed-113">Element</span></span>|<span data-ttu-id="385ed-114">描述</span><span class="sxs-lookup"><span data-stu-id="385ed-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="385ed-115">指定终结点行为。</span><span class="sxs-lookup"><span data-stu-id="385ed-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="385ed-116">备注</span><span class="sxs-lookup"><span data-stu-id="385ed-116">Remarks</span></span>  

 <span data-ttu-id="385ed-117">使用此行为可指示通道侦听器使用同步接收，而非默认的异步接受。</span><span class="sxs-lookup"><span data-stu-id="385ed-117">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="385ed-118">Windows Communication Foundation (WCF) 发出一个新线程，以便为每个接受的通道抽取。</span><span class="sxs-lookup"><span data-stu-id="385ed-118">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="385ed-119">如果有许多通道，则可能出现线程溢出的情况。</span><span class="sxs-lookup"><span data-stu-id="385ed-119">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385ed-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="385ed-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
