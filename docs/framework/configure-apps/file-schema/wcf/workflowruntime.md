---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 43cdec2403e8d80256279388a1adf7cf3cedbb73
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558779"
---
# \<workflowRuntime>
<span data-ttu-id="06fc5-101">指定 <xref:System.Workflow.Runtime.WorkflowRuntime> 用于承载基于工作流的 Windows Communication Foundation (WCF) 服务的设置。</span><span class="sxs-lookup"><span data-stu-id="06fc5-101">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
## <a name="syntax"></a><span data-ttu-id="06fc5-102">语法</span><span class="sxs-lookup"><span data-stu-id="06fc5-102">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06fc5-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="06fc5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="06fc5-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="06fc5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06fc5-105">特性</span><span class="sxs-lookup"><span data-stu-id="06fc5-105">Attributes</span></span>  
  
|<span data-ttu-id="06fc5-106">属性</span><span class="sxs-lookup"><span data-stu-id="06fc5-106">Attribute</span></span>|<span data-ttu-id="06fc5-107">说明</span><span class="sxs-lookup"><span data-stu-id="06fc5-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06fc5-108">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="06fc5-108">cachedInstanceExpiration</span></span>|<span data-ttu-id="06fc5-109">可选的 <xref:System.TimeSpan> 值，指定工作流实例可以在内存中保持空闲状态的最大时长，当超过这一时长后，将强制卸载或中止此实例。</span><span class="sxs-lookup"><span data-stu-id="06fc5-109">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="06fc5-110">如果 workflowruntime 具有执行 unloadOnIdle 的 `PersistenceService`，则忽略此属性。</span><span class="sxs-lookup"><span data-stu-id="06fc5-110">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="06fc5-111">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="06fc5-111">enablePerformanceCounters</span></span>|<span data-ttu-id="06fc5-112">一个可选的布尔值，指定是否启用性能计数器。</span><span class="sxs-lookup"><span data-stu-id="06fc5-112">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="06fc5-113">性能计数器提供各种与工作流相关的统计信息，但在工作流运行时引擎启动和工作流实例运行时会造成性能下降。</span><span class="sxs-lookup"><span data-stu-id="06fc5-113">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="06fc5-114">默认值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="06fc5-114">The default value is `true`.</span></span>|  
|<span data-ttu-id="06fc5-115">name</span><span class="sxs-lookup"><span data-stu-id="06fc5-115">name</span></span>|<span data-ttu-id="06fc5-116">一个包含工作流运行时引擎的名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="06fc5-116">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="06fc5-117">该名称在输出中使用，以便将此运行时与可能正在系统（例如，性能计数器）中运行的其他运行时区别开来。</span><span class="sxs-lookup"><span data-stu-id="06fc5-117">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="06fc5-118">默认值为一个空字符串。</span><span class="sxs-lookup"><span data-stu-id="06fc5-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="06fc5-119">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="06fc5-119">validateOnCreate</span></span>|<span data-ttu-id="06fc5-120">一个可选的布尔值，指定在打开 WorkflowServiceHost 时是否进行工作流定义验证。</span><span class="sxs-lookup"><span data-stu-id="06fc5-120">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="06fc5-121">如果将此属性设置为 `true`，则在每次调用 `WorkflowServiceHost.Open` 时，都会执行工作流验证。</span><span class="sxs-lookup"><span data-stu-id="06fc5-121">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="06fc5-122">如果发现验证错误，则引发 <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> 错误。</span><span class="sxs-lookup"><span data-stu-id="06fc5-122">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="06fc5-123">如果将此属性设置为 `false`，则不进行工作流定义验证。</span><span class="sxs-lookup"><span data-stu-id="06fc5-123">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="06fc5-124">此属性的默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="06fc5-124">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06fc5-125">子元素</span><span class="sxs-lookup"><span data-stu-id="06fc5-125">Child Elements</span></span>  
  
|<span data-ttu-id="06fc5-126">元素</span><span class="sxs-lookup"><span data-stu-id="06fc5-126">Element</span></span>|<span data-ttu-id="06fc5-127">说明</span><span class="sxs-lookup"><span data-stu-id="06fc5-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06fc5-128">commonParameters</span><span class="sxs-lookup"><span data-stu-id="06fc5-128">commonParameters</span></span>|<span data-ttu-id="06fc5-129">服务使用的公用参数的集合。</span><span class="sxs-lookup"><span data-stu-id="06fc5-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="06fc5-130">此集合通常将包括可由持久性服务共享的数据库连接字符串。</span><span class="sxs-lookup"><span data-stu-id="06fc5-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="06fc5-131">services</span><span class="sxs-lookup"><span data-stu-id="06fc5-131">services</span></span>|<span data-ttu-id="06fc5-132">将添加到 <xref:System.Workflow.Runtime.WorkflowRuntime> 引擎的服务的集合。</span><span class="sxs-lookup"><span data-stu-id="06fc5-132">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="06fc5-133">这些元素的类型为 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="06fc5-133">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="06fc5-134">在集合中指定的服务将由工作流运行时引擎初始化，并在调用适当的 <xref:System.Workflow.Runtime.WorkflowRuntime> 构造函数时添加到工作流运行时引擎服务中。</span><span class="sxs-lookup"><span data-stu-id="06fc5-134">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="06fc5-135">因此，在集合中指定的服务必须遵循关于其构造函数的签名的某些规则。</span><span class="sxs-lookup"><span data-stu-id="06fc5-135">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="06fc5-136">有关更多信息，请参见<xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="06fc5-136">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06fc5-137">父元素</span><span class="sxs-lookup"><span data-stu-id="06fc5-137">Parent Elements</span></span>  
  
|<span data-ttu-id="06fc5-138">元素</span><span class="sxs-lookup"><span data-stu-id="06fc5-138">Element</span></span>|<span data-ttu-id="06fc5-139">说明</span><span class="sxs-lookup"><span data-stu-id="06fc5-139">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="06fc5-140">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="06fc5-140">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06fc5-141">备注</span><span class="sxs-lookup"><span data-stu-id="06fc5-141">Remarks</span></span>  
 <span data-ttu-id="06fc5-142">有关使用配置文件控制 Windows Workflow Foundation 主机应用程序的对象的行为的详细信息 <xref:System.Workflow.Runtime.WorkflowRuntime> ，请参阅 [工作流配置文件](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="06fc5-142">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06fc5-143">示例</span><span class="sxs-lookup"><span data-stu-id="06fc5-143">Example</span></span>  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="06fc5-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="06fc5-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="06fc5-145">[工作流配置文件](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="06fc5-145">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
