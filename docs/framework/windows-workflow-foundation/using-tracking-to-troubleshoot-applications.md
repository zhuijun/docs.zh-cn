---
title: 使用跟踪对应用程序进行故障排除
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: fc9427d0c06ed67ea69669cab2aae64f39f7c10c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551283"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="f3951-102">使用跟踪对应用程序进行故障排除</span><span class="sxs-lookup"><span data-stu-id="f3951-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="f3951-103">使用 (WF) ，可以跟踪与工作流相关的信息，以提供有关执行 Windows Workflow Foundation 应用程序或服务的详细信息。 Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="f3951-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="f3951-104">Windows Workflow Foundation 主机能够在工作流实例执行期间捕获工作流事件。</span><span class="sxs-lookup"><span data-stu-id="f3951-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="f3951-105">如果工作流生成错误或异常，则可以使用 Windows Workflow Foundation 跟踪详细信息对其处理进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="f3951-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="f3951-106">使用 WF 跟踪对 WF 进行故障诊断</span><span class="sxs-lookup"><span data-stu-id="f3951-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="f3951-107">若要检测 Windows Workflow Foundation 活动的处理中的故障，可以使用跟踪配置文件来启用跟踪，该跟踪配置文件查询 <xref:System.Activities.Tracking.ActivityStateRecord> 状态为 "出错"。</span><span class="sxs-lookup"><span data-stu-id="f3951-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="f3951-108">在以下代码中指定了相应的查询。</span><span class="sxs-lookup"><span data-stu-id="f3951-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="f3951-109">如果某个错误发生传播并且在错误处理程序（如 <xref:System.Activities.Statements.TryCatch> 活动）中得到了处理，则可以使用 <xref:System.Activities.Tracking.FaultPropagationRecord> 检测到此错误。</span><span class="sxs-lookup"><span data-stu-id="f3951-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="f3951-110"><xref:System.Activities.Tracking.FaultPropagationRecord> 可指示错误的源活动以及错误处理程序的名称。</span><span class="sxs-lookup"><span data-stu-id="f3951-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="f3951-111"><xref:System.Activities.Tracking.FaultPropagationRecord>包含错误的异常堆栈形式的错误详细信息。</span><span class="sxs-lookup"><span data-stu-id="f3951-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.</span></span> <span data-ttu-id="f3951-112">下面的示例演示了用于订阅的查询 <xref:System.Activities.Tracking.FaultPropagationRecord> 。</span><span class="sxs-lookup"><span data-stu-id="f3951-112">The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="f3951-113">如果某个错误未在工作流中处理，则它会导致工作流实例出现未经处理的异常并且工作流实例被中止。</span><span class="sxs-lookup"><span data-stu-id="f3951-113">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="f3951-114">若要了解未经处理的异常的详细信息，跟踪配置文件必须查询具有以下示例中指定的 `state name="UnhandledException"` 的工作流实例记录。</span><span class="sxs-lookup"><span data-stu-id="f3951-114">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="f3951-115">当工作流实例遇到未经处理的异常时， <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> 如果已启用 Windows Workflow Foundation 跟踪，则会发出对象。</span><span class="sxs-lookup"><span data-stu-id="f3951-115">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="f3951-116">此跟踪记录包含异常堆栈形式的错误详细信息。</span><span class="sxs-lookup"><span data-stu-id="f3951-116">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="f3951-117">它包含错误 (源的详细信息，例如，出错并导致未经处理的异常的活动) 。若要从 Windows Workflow Foundation 订阅错误事件，请通过添加跟踪参与者来启用跟踪。</span><span class="sxs-lookup"><span data-stu-id="f3951-117">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="f3951-118">通过查询 `ActivityStateQuery (state="Faulted")`、<xref:System.Activities.Tracking.FaultPropagationRecord> 和 `WorkflowInstanceQuery (state="UnhandledException")` 的跟踪配置文件配置此参与者。</span><span class="sxs-lookup"><span data-stu-id="f3951-118">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="f3951-119">如果使用 ETW 跟踪参与者启用跟踪，则会向 ETW 会话发出错误事件。</span><span class="sxs-lookup"><span data-stu-id="f3951-119">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="f3951-120">可以使用事件查看器查看这些事件。</span><span class="sxs-lookup"><span data-stu-id="f3951-120">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="f3951-121">这可以在分析通道中的节点 **事件查看器 >应用程序和服务日志->Microsoft >Windows >应用程序服务器-应用程序** "下找到。</span><span class="sxs-lookup"><span data-stu-id="f3951-121">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3951-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="f3951-122">See also</span></span>

- <span data-ttu-id="f3951-123">[Windows Server App Fabric 监视](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f3951-123">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="f3951-124">[用 App Fabric 监视应用程序](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f3951-124">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
