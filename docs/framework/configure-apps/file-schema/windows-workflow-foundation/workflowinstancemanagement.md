---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 532d4c31a582b2b0cd90f6f42b20e00790f9ab02
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148654"
---
# \<workflowInstanceManagement>

<span data-ttu-id="a06e1-101">一种服务行为，可用于指定控制工作流实例如何运行的设置，包括持久性、未经处理的异常行为和空闲行为。</span><span class="sxs-lookup"><span data-stu-id="a06e1-101">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="a06e1-102">语法</span><span class="sxs-lookup"><span data-stu-id="a06e1-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a06e1-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a06e1-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a06e1-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a06e1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a06e1-105">特性</span><span class="sxs-lookup"><span data-stu-id="a06e1-105">Attributes</span></span>  
  
|<span data-ttu-id="a06e1-106">属性</span><span class="sxs-lookup"><span data-stu-id="a06e1-106">Attribute</span></span>|<span data-ttu-id="a06e1-107">描述</span><span class="sxs-lookup"><span data-stu-id="a06e1-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a06e1-108">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="a06e1-108">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="a06e1-109">子元素</span><span class="sxs-lookup"><span data-stu-id="a06e1-109">Child Elements</span></span>  

 <span data-ttu-id="a06e1-110">无。</span><span class="sxs-lookup"><span data-stu-id="a06e1-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a06e1-111">父元素</span><span class="sxs-lookup"><span data-stu-id="a06e1-111">Parent Elements</span></span>  
  
|<span data-ttu-id="a06e1-112">元素</span><span class="sxs-lookup"><span data-stu-id="a06e1-112">Element</span></span>|<span data-ttu-id="a06e1-113">描述</span><span class="sxs-lookup"><span data-stu-id="a06e1-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a06e1-114">\<serviceBehaviors> 的 \<behavior></span><span class="sxs-lookup"><span data-stu-id="a06e1-114">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="a06e1-115">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="a06e1-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a06e1-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="a06e1-116">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
