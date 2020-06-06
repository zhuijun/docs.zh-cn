---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398568"
---
# \<workflowUnhandledException>
<span data-ttu-id="eb3fe-101">一种服务行为，可用于指定工作流服务中发生未经处理的异常时所采取的操作。</span><span class="sxs-lookup"><span data-stu-id="eb3fe-101">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="eb3fe-102">语法</span><span class="sxs-lookup"><span data-stu-id="eb3fe-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb3fe-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="eb3fe-103">Attributes and Elements</span></span>  
 <span data-ttu-id="eb3fe-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="eb3fe-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb3fe-105">特性</span><span class="sxs-lookup"><span data-stu-id="eb3fe-105">Attributes</span></span>  
  
|<span data-ttu-id="eb3fe-106">属性</span><span class="sxs-lookup"><span data-stu-id="eb3fe-106">Attribute</span></span>|<span data-ttu-id="eb3fe-107">说明</span><span class="sxs-lookup"><span data-stu-id="eb3fe-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb3fe-108">action</span><span class="sxs-lookup"><span data-stu-id="eb3fe-108">action</span></span>|<span data-ttu-id="eb3fe-109">一个字符串，指定发生未经处理的异常时所采取的操作。</span><span class="sxs-lookup"><span data-stu-id="eb3fe-109">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="eb3fe-110">此特性的类型为 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="eb3fe-110">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb3fe-111">子元素</span><span class="sxs-lookup"><span data-stu-id="eb3fe-111">Child Elements</span></span>  
 <span data-ttu-id="eb3fe-112">无。</span><span class="sxs-lookup"><span data-stu-id="eb3fe-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb3fe-113">父元素</span><span class="sxs-lookup"><span data-stu-id="eb3fe-113">Parent Elements</span></span>  
  
|<span data-ttu-id="eb3fe-114">元素</span><span class="sxs-lookup"><span data-stu-id="eb3fe-114">Element</span></span>|<span data-ttu-id="eb3fe-115">描述</span><span class="sxs-lookup"><span data-stu-id="eb3fe-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb3fe-116">\<behavior>个\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="eb3fe-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="eb3fe-117">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="eb3fe-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb3fe-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb3fe-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
