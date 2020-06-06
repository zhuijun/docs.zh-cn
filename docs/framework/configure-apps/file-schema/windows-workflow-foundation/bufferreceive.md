---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398837"
---
# \<bufferReceive>
<span data-ttu-id="98838-101">一种服务行为，允许服务使用缓冲接收处理，以使工作流服务能够处理无序消息。</span><span class="sxs-lookup"><span data-stu-id="98838-101">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="98838-102">语法</span><span class="sxs-lookup"><span data-stu-id="98838-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98838-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="98838-103">Attributes and Elements</span></span>  
 <span data-ttu-id="98838-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="98838-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98838-105">特性</span><span class="sxs-lookup"><span data-stu-id="98838-105">Attributes</span></span>  
  
|<span data-ttu-id="98838-106">属性</span><span class="sxs-lookup"><span data-stu-id="98838-106">Attribute</span></span>|<span data-ttu-id="98838-107">说明</span><span class="sxs-lookup"><span data-stu-id="98838-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98838-108">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="98838-108">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="98838-109">一个整数，指定每个通道允许的最大挂起消息数。</span><span class="sxs-lookup"><span data-stu-id="98838-109">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="98838-110">默认值为 512。</span><span class="sxs-lookup"><span data-stu-id="98838-110">The default value is 512.</span></span> <span data-ttu-id="98838-111">此属性限制工作流服务可接收的无序消息数。</span><span class="sxs-lookup"><span data-stu-id="98838-111">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98838-112">子元素</span><span class="sxs-lookup"><span data-stu-id="98838-112">Child Elements</span></span>  
 <span data-ttu-id="98838-113">无。</span><span class="sxs-lookup"><span data-stu-id="98838-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98838-114">父元素</span><span class="sxs-lookup"><span data-stu-id="98838-114">Parent Elements</span></span>  
  
|<span data-ttu-id="98838-115">元素</span><span class="sxs-lookup"><span data-stu-id="98838-115">Element</span></span>|<span data-ttu-id="98838-116">描述</span><span class="sxs-lookup"><span data-stu-id="98838-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98838-117">\<behavior>个\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="98838-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="98838-118">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="98838-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98838-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98838-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
