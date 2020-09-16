---
title: <add> 的 <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 8328b6d08c1b57ad7a899c8cb489e07037e5af09
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558156"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="0443e-102">\<add> 的 \<commonParameters></span><span class="sxs-lookup"><span data-stu-id="0443e-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="0443e-103">指定在多个服务之间全局使用的参数的名称/值对。</span><span class="sxs-lookup"><span data-stu-id="0443e-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="0443e-104">此参数通常包括可由持久性服务共享的数据库连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0443e-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="0443e-105">语法</span><span class="sxs-lookup"><span data-stu-id="0443e-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0443e-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0443e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="0443e-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0443e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0443e-108">特性</span><span class="sxs-lookup"><span data-stu-id="0443e-108">Attributes</span></span>  
  
|<span data-ttu-id="0443e-109">属性</span><span class="sxs-lookup"><span data-stu-id="0443e-109">Attribute</span></span>|<span data-ttu-id="0443e-110">说明</span><span class="sxs-lookup"><span data-stu-id="0443e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0443e-111">name</span><span class="sxs-lookup"><span data-stu-id="0443e-111">name</span></span>|<span data-ttu-id="0443e-112">为服务指定的参数的名称。</span><span class="sxs-lookup"><span data-stu-id="0443e-112">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="0443e-113">值</span><span class="sxs-lookup"><span data-stu-id="0443e-113">value</span></span>|<span data-ttu-id="0443e-114">为服务指定的参数的值。</span><span class="sxs-lookup"><span data-stu-id="0443e-114">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0443e-115">子元素</span><span class="sxs-lookup"><span data-stu-id="0443e-115">Child Elements</span></span>  
 <span data-ttu-id="0443e-116">无。</span><span class="sxs-lookup"><span data-stu-id="0443e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0443e-117">父元素</span><span class="sxs-lookup"><span data-stu-id="0443e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0443e-118">元素</span><span class="sxs-lookup"><span data-stu-id="0443e-118">Element</span></span>|<span data-ttu-id="0443e-119">说明</span><span class="sxs-lookup"><span data-stu-id="0443e-119">Description</span></span>|  
|-------------|-----------------|  
|[\<commonParameters>](commonparameters.md)|<span data-ttu-id="0443e-120">服务使用的公用参数的集合。</span><span class="sxs-lookup"><span data-stu-id="0443e-120">A collection of common parameters used by services.</span></span> <span data-ttu-id="0443e-121">此集合通常将包括可由持久性服务共享的数据库连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0443e-121">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0443e-122">备注</span><span class="sxs-lookup"><span data-stu-id="0443e-122">Remarks</span></span>  
 <span data-ttu-id="0443e-123">`<commonParameters>` 元素定义在多个服务之间全局使用的任何参数，例如，使用 `ConnectionString` 时的<xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>。</span><span class="sxs-lookup"><span data-stu-id="0443e-123">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="0443e-124">对于提交批处理工作进行永久性存储的服务，如 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> 和 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>，可以通过使用 `EnableRetries` 参数来允许它们重试其事务，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="0443e-124">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="0443e-125">请注意， `EnableRetries` 参数可以在全局级别 (如 *CommonParameters* 部分中所示) 或支持 (的单个服务， `EnableRetries` 如 " *服务* " 部分) 中所示。</span><span class="sxs-lookup"><span data-stu-id="0443e-125">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="0443e-126">有关使用配置文件控制 Windows Workflow Foundation 主机应用程序的对象的行为的详细信息 <xref:System.Workflow.Runtime.WorkflowRuntime> ，请参阅 [工作流配置文件](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="0443e-126">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0443e-127">示例</span><span class="sxs-lookup"><span data-stu-id="0443e-127">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="0443e-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="0443e-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="0443e-129">[工作流配置文件](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0443e-129">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<commonParameters>](commonparameters.md)
