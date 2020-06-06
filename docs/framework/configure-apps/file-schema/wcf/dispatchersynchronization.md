---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398000"
---
# \<dispatcherSynchronization>
  
<span data-ttu-id="fc9b3-101">指定允许服务进行异步答复的终结点行为。</span><span class="sxs-lookup"><span data-stu-id="fc9b3-101">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a><span data-ttu-id="fc9b3-102">语法</span><span class="sxs-lookup"><span data-stu-id="fc9b3-102">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="fc9b3-103">类型</span><span class="sxs-lookup"><span data-stu-id="fc9b3-103">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc9b3-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="fc9b3-104">Attributes and elements</span></span>  
  
<span data-ttu-id="fc9b3-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fc9b3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc9b3-106">特性</span><span class="sxs-lookup"><span data-stu-id="fc9b3-106">Attributes</span></span>

| <span data-ttu-id="fc9b3-107">属性</span><span class="sxs-lookup"><span data-stu-id="fc9b3-107">Attribute</span></span>               | <span data-ttu-id="fc9b3-108">说明</span><span class="sxs-lookup"><span data-stu-id="fc9b3-108">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="fc9b3-109">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="fc9b3-109">asynchronousSendEnabled</span></span> | <span data-ttu-id="fc9b3-110">一个布尔值，指定是否启用异步发送行为。</span><span class="sxs-lookup"><span data-stu-id="fc9b3-110">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="fc9b3-111">一个整数，指定可在每个通道上执行的并发接收数。</span><span class="sxs-lookup"><span data-stu-id="fc9b3-111">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="fc9b3-112">仅当已正确配置服务限制行为之后，才能配置此值。</span><span class="sxs-lookup"><span data-stu-id="fc9b3-112">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="fc9b3-113">子元素</span><span class="sxs-lookup"><span data-stu-id="fc9b3-113">Child elements</span></span>

<span data-ttu-id="fc9b3-114">无。</span><span class="sxs-lookup"><span data-stu-id="fc9b3-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc9b3-115">父元素</span><span class="sxs-lookup"><span data-stu-id="fc9b3-115">Parent elements</span></span>

| <span data-ttu-id="fc9b3-116">元素</span><span class="sxs-lookup"><span data-stu-id="fc9b3-116">Element</span></span> | <span data-ttu-id="fc9b3-117">描述</span><span class="sxs-lookup"><span data-stu-id="fc9b3-117">Description</span></span> |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="fc9b3-118">指定终结点行为。</span><span class="sxs-lookup"><span data-stu-id="fc9b3-118">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="fc9b3-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc9b3-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
