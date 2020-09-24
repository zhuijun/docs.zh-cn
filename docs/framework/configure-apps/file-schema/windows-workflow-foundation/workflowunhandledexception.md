---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 6e3993e43aac746f380a30341fe4ebffcd257c5f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148511"
---
# \<workflowUnhandledException>

<span data-ttu-id="b6c6c-101">一种服务行为，可用于指定工作流服务中发生未经处理的异常时所采取的操作。</span><span class="sxs-lookup"><span data-stu-id="b6c6c-101">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="b6c6c-102">语法</span><span class="sxs-lookup"><span data-stu-id="b6c6c-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6c6c-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b6c6c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="b6c6c-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b6c6c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6c6c-105">特性</span><span class="sxs-lookup"><span data-stu-id="b6c6c-105">Attributes</span></span>  
  
|<span data-ttu-id="b6c6c-106">属性</span><span class="sxs-lookup"><span data-stu-id="b6c6c-106">Attribute</span></span>|<span data-ttu-id="b6c6c-107">描述</span><span class="sxs-lookup"><span data-stu-id="b6c6c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6c6c-108">action</span><span class="sxs-lookup"><span data-stu-id="b6c6c-108">action</span></span>|<span data-ttu-id="b6c6c-109">一个字符串，指定发生未经处理的异常时所采取的操作。</span><span class="sxs-lookup"><span data-stu-id="b6c6c-109">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="b6c6c-110">此特性的类型为 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="b6c6c-110">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6c6c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b6c6c-111">Child Elements</span></span>  

 <span data-ttu-id="b6c6c-112">无。</span><span class="sxs-lookup"><span data-stu-id="b6c6c-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6c6c-113">父元素</span><span class="sxs-lookup"><span data-stu-id="b6c6c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b6c6c-114">元素</span><span class="sxs-lookup"><span data-stu-id="b6c6c-114">Element</span></span>|<span data-ttu-id="b6c6c-115">描述</span><span class="sxs-lookup"><span data-stu-id="b6c6c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6c6c-116">\<serviceBehaviors> 的 \<behavior></span><span class="sxs-lookup"><span data-stu-id="b6c6c-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b6c6c-117">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="b6c6c-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6c6c-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="b6c6c-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
