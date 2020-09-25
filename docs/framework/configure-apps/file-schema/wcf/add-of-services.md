---
title: <add> 的 <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 31a4d2a5a3baf3d53cf18ab6e37edfaf7acb8540
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204978"
---
# <a name="add-of-services"></a><span data-ttu-id="b44bd-102">\<add> 的 \<services></span><span class="sxs-lookup"><span data-stu-id="b44bd-102">\<add> of \<services></span></span>

<span data-ttu-id="b44bd-103">指定 <xref:System.Workflow.Runtime.WorkflowRuntime> 用于承载基于工作流的 Windows Communication Foundation (WCF) 服务的设置。</span><span class="sxs-lookup"><span data-stu-id="b44bd-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="b44bd-104">此元素的类型为 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="b44bd-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="b44bd-105">语法</span><span class="sxs-lookup"><span data-stu-id="b44bd-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b44bd-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b44bd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b44bd-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b44bd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b44bd-108">特性</span><span class="sxs-lookup"><span data-stu-id="b44bd-108">Attributes</span></span>  
  
|<span data-ttu-id="b44bd-109">属性</span><span class="sxs-lookup"><span data-stu-id="b44bd-109">Attribute</span></span>|<span data-ttu-id="b44bd-110">说明</span><span class="sxs-lookup"><span data-stu-id="b44bd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b44bd-111">type</span><span class="sxs-lookup"><span data-stu-id="b44bd-111">type</span></span>|<span data-ttu-id="b44bd-112">一个字符串，指定要进行初始化的服务的程序集限定类型名称。</span><span class="sxs-lookup"><span data-stu-id="b44bd-112">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="b44bd-113">指定的服务必须遵循关于其构造函数的签名的某些规则。</span><span class="sxs-lookup"><span data-stu-id="b44bd-113">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="b44bd-114">有关详细信息，请参阅 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> 。</span><span class="sxs-lookup"><span data-stu-id="b44bd-114">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b44bd-115">子元素</span><span class="sxs-lookup"><span data-stu-id="b44bd-115">Child Elements</span></span>  

 <span data-ttu-id="b44bd-116">无。</span><span class="sxs-lookup"><span data-stu-id="b44bd-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b44bd-117">父元素</span><span class="sxs-lookup"><span data-stu-id="b44bd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b44bd-118">元素</span><span class="sxs-lookup"><span data-stu-id="b44bd-118">Element</span></span>|<span data-ttu-id="b44bd-119">描述</span><span class="sxs-lookup"><span data-stu-id="b44bd-119">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services-of-workflowruntime.md)|<span data-ttu-id="b44bd-120">将添加到 <xref:System.Workflow.Runtime.WorkflowRuntime> 引擎的服务的集合。</span><span class="sxs-lookup"><span data-stu-id="b44bd-120">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="b44bd-121">这些元素的类型为 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="b44bd-121">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="b44bd-122">在集合中指定的服务将由工作流运行时引擎初始化，并在调用适当的 <xref:System.Workflow.Runtime.WorkflowRuntime> 构造函数时添加到工作流运行时引擎服务中。</span><span class="sxs-lookup"><span data-stu-id="b44bd-122">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="b44bd-123">因此，在集合中指定的服务必须遵循关于其构造函数的签名的某些规则。</span><span class="sxs-lookup"><span data-stu-id="b44bd-123">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="b44bd-124">有关详细信息，请参阅 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> 。</span><span class="sxs-lookup"><span data-stu-id="b44bd-124">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b44bd-125">备注</span><span class="sxs-lookup"><span data-stu-id="b44bd-125">Remarks</span></span>  

 <span data-ttu-id="b44bd-126">在此元素中指定的服务将由工作流运行时引擎初始化，并在调用适当的 <xref:System.Workflow.Runtime.WorkflowRuntime> 构造函数时添加到工作流运行时引擎服务中。</span><span class="sxs-lookup"><span data-stu-id="b44bd-126">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="b44bd-127">因此，指定的服务必须遵循关于其构造函数的签名的某些规则。</span><span class="sxs-lookup"><span data-stu-id="b44bd-127">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="b44bd-128">有关详细信息，请参阅 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> 。</span><span class="sxs-lookup"><span data-stu-id="b44bd-128">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b44bd-129">示例</span><span class="sxs-lookup"><span data-stu-id="b44bd-129">Example</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="ServiceBehavior">
    <workflowRuntime name="WorkflowServiceHostRuntime"
                     validateOnCreate="true"
                     enablePerformanceCounters="true">
      <services>
        <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common" />
      </services>
    </workflowRuntime>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="b44bd-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="b44bd-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="b44bd-131">[工作流配置文件](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b44bd-131">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
