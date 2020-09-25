---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 16d4546bce461b55695e0deed093396ce1c2b0b6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189560"
---
# \<bufferReceive>

<span data-ttu-id="c467c-101">一种服务行为，允许服务使用缓冲接收处理，以使工作流服务能够处理无序消息。</span><span class="sxs-lookup"><span data-stu-id="c467c-101">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="c467c-102">语法</span><span class="sxs-lookup"><span data-stu-id="c467c-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c467c-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c467c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="c467c-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c467c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c467c-105">特性</span><span class="sxs-lookup"><span data-stu-id="c467c-105">Attributes</span></span>  
  
|<span data-ttu-id="c467c-106">属性</span><span class="sxs-lookup"><span data-stu-id="c467c-106">Attribute</span></span>|<span data-ttu-id="c467c-107">描述</span><span class="sxs-lookup"><span data-stu-id="c467c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c467c-108">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="c467c-108">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="c467c-109">一个整数，指定每个通道允许的最大挂起消息数。</span><span class="sxs-lookup"><span data-stu-id="c467c-109">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="c467c-110">默认值为 512。</span><span class="sxs-lookup"><span data-stu-id="c467c-110">The default value is 512.</span></span> <span data-ttu-id="c467c-111">此属性限制工作流服务可接收的无序消息数。</span><span class="sxs-lookup"><span data-stu-id="c467c-111">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c467c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c467c-112">Child Elements</span></span>  

 <span data-ttu-id="c467c-113">无。</span><span class="sxs-lookup"><span data-stu-id="c467c-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c467c-114">父元素</span><span class="sxs-lookup"><span data-stu-id="c467c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c467c-115">元素</span><span class="sxs-lookup"><span data-stu-id="c467c-115">Element</span></span>|<span data-ttu-id="c467c-116">描述</span><span class="sxs-lookup"><span data-stu-id="c467c-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c467c-117">\<serviceBehaviors> 的 \<behavior></span><span class="sxs-lookup"><span data-stu-id="c467c-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c467c-118">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="c467c-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c467c-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="c467c-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
