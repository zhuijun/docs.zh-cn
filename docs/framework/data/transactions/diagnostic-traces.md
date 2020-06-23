---
title: 诊断跟踪
description: 了解 .NET 中的诊断跟踪。 跟踪是指发布在执行应用程序期间生成的特定消息。
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 5de8fdf7b95cf01b119118dac75d373c32949dcd
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141806"
---
# <a name="diagnostic-traces"></a><span data-ttu-id="5fddb-104">诊断跟踪</span><span class="sxs-lookup"><span data-stu-id="5fddb-104">Diagnostic Traces</span></span>
<span data-ttu-id="5fddb-105">跟踪是指发布在执行应用程序期间生成的特定消息。</span><span class="sxs-lookup"><span data-stu-id="5fddb-105">Traces are the publishing of specific messages that are generated during application execution.</span></span> <span data-ttu-id="5fddb-106">使用跟踪时，必须具有收集和记录所发送消息的机制。</span><span class="sxs-lookup"><span data-stu-id="5fddb-106">When using tracing, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="5fddb-107">跟踪消息由侦听器来接收。</span><span class="sxs-lookup"><span data-stu-id="5fddb-107">Trace messages are received by listeners.</span></span> <span data-ttu-id="5fddb-108">侦听器的用途是收集、存储和路由跟踪消息。</span><span class="sxs-lookup"><span data-stu-id="5fddb-108">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="5fddb-109">侦听器会将跟踪输出定向到适当的目标，如日志、窗口或文本文件。</span><span class="sxs-lookup"><span data-stu-id="5fddb-109">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="5fddb-110"><xref:System.Diagnostics.DefaultTraceListener> 就是一个这样的侦听器，在启用跟踪后将自动创建并初始化它。</span><span class="sxs-lookup"><span data-stu-id="5fddb-110">One such listener, the <xref:System.Diagnostics.DefaultTraceListener>, is automatically created and initialized when tracing is enabled.</span></span> <span data-ttu-id="5fddb-111">如果要将跟踪输出定向到任何其他源，则必须创建并初始化其他跟踪侦听器。</span><span class="sxs-lookup"><span data-stu-id="5fddb-111">If you want trace output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span> <span data-ttu-id="5fddb-112">所创建的侦听器应反映您的具体需要。</span><span class="sxs-lookup"><span data-stu-id="5fddb-112">The listeners you create should reflect your individual needs.</span></span> <span data-ttu-id="5fddb-113">例如，您可能需要所有跟踪输出的文本记录。</span><span class="sxs-lookup"><span data-stu-id="5fddb-113">For example, you might want a text record of all trace output.</span></span> <span data-ttu-id="5fddb-114">在这种情况下，可以创建一个侦听器，使其在启用时将所有输出写入一个新的文本文件。</span><span class="sxs-lookup"><span data-stu-id="5fddb-114">In this case, you would create a listener that wrote all output to a new text file when enabled.</span></span> <span data-ttu-id="5fddb-115">另一方面，您可能只需要在执行应用程序的过程中查看输出。</span><span class="sxs-lookup"><span data-stu-id="5fddb-115">On the other hand, you might only want to view output during application execution.</span></span> <span data-ttu-id="5fddb-116">在这种情况下，可以创建一个侦听器，使其将所有输出定向到一个控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="5fddb-116">In that case, you might create a listener that directed all output to a console window.</span></span> <span data-ttu-id="5fddb-117"><xref:System.Diagnostics.EventLogTraceListener> 可将跟踪输出定向到事件日志，而 <xref:System.Diagnostics.TextWriterTraceListener> 可将跟踪输出写入流中。</span><span class="sxs-lookup"><span data-stu-id="5fddb-117">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log, and the <xref:System.Diagnostics.TextWriterTraceListener> can write trace output to a stream.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="5fddb-118">启用跟踪</span><span class="sxs-lookup"><span data-stu-id="5fddb-118">Enabling Tracing</span></span>  
 <span data-ttu-id="5fddb-119">若要在事务处理期间启用跟踪，应编辑应用程序的配置文件。</span><span class="sxs-lookup"><span data-stu-id="5fddb-119">To enable traces during transaction processing, you should edit your application’s configuration file.</span></span> <span data-ttu-id="5fddb-120">下面是一个示例。</span><span class="sxs-lookup"><span data-stu-id="5fddb-120">The following is an example.</span></span>  
  
```xml  
<configuration>  
<system.diagnostics>  
     <sources>  
          <source name="System.Transactions" switchValue="Warning">  
               <listeners>  
                    <add name="tx"
                     type="System.Diagnostics.XmlWriterTraceListener"
                     initializeData= "tx.log" />  
               </listeners>  
          </source>  
     </sources>  
</system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="5fddb-121"><xref:System.Transactions> 跟踪将写入到一个名为“System.Transactions”的源。</span><span class="sxs-lookup"><span data-stu-id="5fddb-121"><xref:System.Transactions> traces are written to the source named "System.Transactions".</span></span> <span data-ttu-id="5fddb-122">可以使用 `add` 指定要使用的跟踪侦听器的名称和类型。</span><span class="sxs-lookup"><span data-stu-id="5fddb-122">You can use `add` to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="5fddb-123">在示例配置中，将侦听器命名为“tx”并添加了标准 .NET Framework 跟踪侦听器 (<xref:System.Diagnostics.XmlWriterTraceListener>) 作为要使用的类型。</span><span class="sxs-lookup"><span data-stu-id="5fddb-123">In our example configuration, we named the Listener "tx" and added the standard .NET Framework trace listener (<xref:System.Diagnostics.XmlWriterTraceListener>) as the type we want to use.</span></span> <span data-ttu-id="5fddb-124">使用 `initializeData` 设置该侦听器的日志文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5fddb-124">Use `initializeData` to set the name of the log file for that listener.</span></span> <span data-ttu-id="5fddb-125">此外，还可以用一个简单文件名来替换完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="5fddb-125">In addition, you can substitute a fully qualified path for a simple file name.</span></span>  
  
 <span data-ttu-id="5fddb-126">每个跟踪消息类型都分配有一个指示其重要程度的级别。</span><span class="sxs-lookup"><span data-stu-id="5fddb-126">Each trace message type is assigned a level to indicate its degree of importance.</span></span> <span data-ttu-id="5fddb-127">如果应用程序域的跟踪级别等于或小于事件类型的级别，就会生成该消息。</span><span class="sxs-lookup"><span data-stu-id="5fddb-127">If the app-domain’s trace level is equal or lower than the level of an event type, then that message is generated.</span></span> <span data-ttu-id="5fddb-128">跟踪级别由配置文件中的 `switchValue` 设置控制。</span><span class="sxs-lookup"><span data-stu-id="5fddb-128">The tracing level is controlled by the `switchValue` setting in the configuration file.</span></span> <span data-ttu-id="5fddb-129">下表定义了与诊断跟踪消息关联的级别。</span><span class="sxs-lookup"><span data-stu-id="5fddb-129">The levels that are associated with diagnostic trace messages are defined in the following table.</span></span>  
  
|<span data-ttu-id="5fddb-130">跟踪级别</span><span class="sxs-lookup"><span data-stu-id="5fddb-130">Trace Level</span></span>|<span data-ttu-id="5fddb-131">说明</span><span class="sxs-lookup"><span data-stu-id="5fddb-131">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5fddb-132">严重</span><span class="sxs-lookup"><span data-stu-id="5fddb-132">Critical</span></span>|<span data-ttu-id="5fddb-133">表示发生了类似于下面的严重故障：</span><span class="sxs-lookup"><span data-stu-id="5fddb-133">Serious failures, such as the following, have occurred:</span></span><br /><br /> <span data-ttu-id="5fddb-134">-可能导致用户功能立即丢失的错误。</span><span class="sxs-lookup"><span data-stu-id="5fddb-134">-   An error that can cause an immediate loss in user functionality.</span></span><br /><span data-ttu-id="5fddb-135">-一个事件，要求管理员采取措施以避免功能丢失。</span><span class="sxs-lookup"><span data-stu-id="5fddb-135">-   An event that requires an administrator to take action to avoid loss of functionality.</span></span><br /><span data-ttu-id="5fddb-136">-代码挂起。</span><span class="sxs-lookup"><span data-stu-id="5fddb-136">-   Code hangs.</span></span><br /><span data-ttu-id="5fddb-137">-此跟踪级别还可以提供足够的上下文来解释其他关键跟踪。</span><span class="sxs-lookup"><span data-stu-id="5fddb-137">-   This tracing level can also provide sufficient context for interpreting other critical traces.</span></span> <span data-ttu-id="5fddb-138">这可以帮助确定导致严重故障的操作序列。</span><span class="sxs-lookup"><span data-stu-id="5fddb-138">This can help to identify the sequence of operations leading to a serious failure.</span></span>|  
|<span data-ttu-id="5fddb-139">错误</span><span class="sxs-lookup"><span data-stu-id="5fddb-139">Error</span></span>|<span data-ttu-id="5fddb-140">发生了可能会导致用户功能丧失的错误（如无效的配置或网络行为）。</span><span class="sxs-lookup"><span data-stu-id="5fddb-140">An error (for example, invalid configuration or network behavior) has occurred that can result in a loss of user functionality.</span></span>|  
|<span data-ttu-id="5fddb-141">警告</span><span class="sxs-lookup"><span data-stu-id="5fddb-141">Warning</span></span>|<span data-ttu-id="5fddb-142">存在一种状况，它可能会在以后导致错误或严重故障（例如，分配失败或达到限制）。</span><span class="sxs-lookup"><span data-stu-id="5fddb-142">A condition exists that can subsequently result in an error or critical failure (for example, allocation failing or approaching a limit).</span></span> <span data-ttu-id="5fddb-143">对用户代码中的错误（例如，事务中止、超时、身份验证失败）的正常处理也可能会生成警告。</span><span class="sxs-lookup"><span data-stu-id="5fddb-143">Normal processing of errors from user code (for example, transaction aborted, timeouts, authentication failed) can also generate a warning.</span></span>|  
|<span data-ttu-id="5fddb-144">信息</span><span class="sxs-lookup"><span data-stu-id="5fddb-144">Information</span></span>|<span data-ttu-id="5fddb-145">生成对监视和诊断系统状态、测量性能或执行分析十分有用的消息。</span><span class="sxs-lookup"><span data-stu-id="5fddb-145">Messages helpful for monitoring and diagnosing system status, measuring performance, or profiling are generated.</span></span> <span data-ttu-id="5fddb-146">这些消息可包括事务和登记生存期事件，如创建或提交事务、跨重要边界或分配重要资源等。</span><span class="sxs-lookup"><span data-stu-id="5fddb-146">These can include transaction and enlistment lifetime events, such as a transaction being created or committed, the crossing of a significant boundary, or the allocation of significant resources.</span></span> <span data-ttu-id="5fddb-147">开发人员可利用此类信息规划容量和管理性能。</span><span class="sxs-lookup"><span data-stu-id="5fddb-147">A developer can then utilize such information for capacity planning and performance management.</span></span>|  
  
## <a name="trace-codes"></a><span data-ttu-id="5fddb-148">跟踪代码</span><span class="sxs-lookup"><span data-stu-id="5fddb-148">Trace Codes</span></span>  
 <span data-ttu-id="5fddb-149">下表列出了由 <xref:System.Transactions> 基础结构生成的跟踪代码。</span><span class="sxs-lookup"><span data-stu-id="5fddb-149">The following table lists the trace codes that are generated by the <xref:System.Transactions> infrastructure.</span></span> <span data-ttu-id="5fddb-150">表中包含的是跟踪代码标识符、跟踪的 <xref:System.Diagnostics.EventTypeFilter.EventType%2A> 枚举级别以及用于跟踪的**TraceRecord**中包含的额外数据。</span><span class="sxs-lookup"><span data-stu-id="5fddb-150">Included in the table are the trace code identifier, the <xref:System.Diagnostics.EventTypeFilter.EventType%2A> enumeration level for the trace, and the extra data contained in the **TraceRecord** for the trace.</span></span> <span data-ttu-id="5fddb-151">此外，跟踪的相应跟踪级别也存储在**TraceRecord**中。</span><span class="sxs-lookup"><span data-stu-id="5fddb-151">In addition, the corresponding trace level of the trace is also stored in the **TraceRecord**.</span></span>  
  
|<span data-ttu-id="5fddb-152">TraceCode</span><span class="sxs-lookup"><span data-stu-id="5fddb-152">TraceCode</span></span>|<span data-ttu-id="5fddb-153">EventType</span><span class="sxs-lookup"><span data-stu-id="5fddb-153">EventType</span></span>|<span data-ttu-id="5fddb-154">TraceRecord 中的额外数据</span><span class="sxs-lookup"><span data-stu-id="5fddb-154">Extra data in TraceRecord</span></span>|  
|---------------|---------------|-------------------------------|  
|<span data-ttu-id="5fddb-155">TransactionCreated</span><span class="sxs-lookup"><span data-stu-id="5fddb-155">TransactionCreated</span></span>|<span data-ttu-id="5fddb-156">信息</span><span class="sxs-lookup"><span data-stu-id="5fddb-156">Info</span></span>|<span data-ttu-id="5fddb-157">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="5fddb-157">TransactionTraceId</span></span>|  
|<span data-ttu-id="5fddb-158">TransactionPromoted</span><span class="sxs-lookup"><span data-stu-id="5fddb-158">TransactionPromoted</span></span>|<span data-ttu-id="5fddb-159">信息</span><span class="sxs-lookup"><span data-stu-id="5fddb-159">Info</span></span>|<span data-ttu-id="5fddb-160">Local TransactionTraceId、Distributed TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="5fddb-160">Local TransactionTraceId, Distributed TransactionTraceId</span></span>|  
|<span data-ttu-id="5fddb-161">EnlistmentCreated</span><span class="sxs-lookup"><span data-stu-id="5fddb-161">EnlistmentCreated</span></span>|<span data-ttu-id="5fddb-162">信息</span><span class="sxs-lookup"><span data-stu-id="5fddb-162">Info</span></span>|<span data-ttu-id="5fddb-163">TransactionTraceId、EnlistmentTraceId、EnlistmentType（持久/可变）、EnlistmentOptions</span><span class="sxs-lookup"><span data-stu-id="5fddb-163">TransactionTraceId, EnlistmentTraceId, EnlistmentType (durable/volatile), EnlistmentOptions</span></span>|  
|<span data-ttu-id="5fddb-164">EnlistmentCallbackNegative</span><span class="sxs-lookup"><span data-stu-id="5fddb-164">EnlistmentCallbackNegative</span></span>|<span data-ttu-id="5fddb-165">警告</span><span class="sxs-lookup"><span data-stu-id="5fddb-165">Warning</span></span>|<span data-ttu-id="5fddb-166">TransactionTraceId、EnlistmentTraceId</span><span class="sxs-lookup"><span data-stu-id="5fddb-166">TransactionTraceId, EnlistmentTraceId,</span></span><br /><br /> <span data-ttu-id="5fddb-167">Callback (forcerollback/aborted/indoubt)</span><span class="sxs-lookup"><span data-stu-id="5fddb-167">Callback (forcerollback/aborted/indoubt)</span></span>|  
|<span data-ttu-id="5fddb-168">TransactionRollbackCalled</span><span class="sxs-lookup"><span data-stu-id="5fddb-168">TransactionRollbackCalled</span></span>|<span data-ttu-id="5fddb-169">警告</span><span class="sxs-lookup"><span data-stu-id="5fddb-169">Warning</span></span>|<span data-ttu-id="5fddb-170">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="5fddb-170">TransactionTraceId</span></span>|  
|<span data-ttu-id="5fddb-171">TransactionAborted</span><span class="sxs-lookup"><span data-stu-id="5fddb-171">TransactionAborted</span></span>|<span data-ttu-id="5fddb-172">警告</span><span class="sxs-lookup"><span data-stu-id="5fddb-172">Warning</span></span>|<span data-ttu-id="5fddb-173">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="5fddb-173">TransactionTraceId</span></span>|  
|<span data-ttu-id="5fddb-174">TransactionInDoubt</span><span class="sxs-lookup"><span data-stu-id="5fddb-174">TransactionInDoubt</span></span>|<span data-ttu-id="5fddb-175">警告</span><span class="sxs-lookup"><span data-stu-id="5fddb-175">Warning</span></span>|<span data-ttu-id="5fddb-176">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="5fddb-176">TransactionTraceId</span></span>|  
|<span data-ttu-id="5fddb-177">TransactionScopeCreated</span><span class="sxs-lookup"><span data-stu-id="5fddb-177">TransactionScopeCreated</span></span>|<span data-ttu-id="5fddb-178">信息</span><span class="sxs-lookup"><span data-stu-id="5fddb-178">Info</span></span>|<span data-ttu-id="5fddb-179">TransactionScopeResult，可为以下各项：</span><span class="sxs-lookup"><span data-stu-id="5fddb-179">TransactionScopeResult, which can be the following:</span></span><br /><br /> <span data-ttu-id="5fddb-180">-新事务。</span><span class="sxs-lookup"><span data-stu-id="5fddb-180">-   New transaction.</span></span><br /><span data-ttu-id="5fddb-181">-事务已通过。</span><span class="sxs-lookup"><span data-stu-id="5fddb-181">-   Transaction passed.</span></span><br /><span data-ttu-id="5fddb-182">从属事务已通过。</span><span class="sxs-lookup"><span data-stu-id="5fddb-182">-   Dependent transaction passed.</span></span><br /><span data-ttu-id="5fddb-183">-使用当前事务。</span><span class="sxs-lookup"><span data-stu-id="5fddb-183">-   Using current transaction.</span></span><br /><span data-ttu-id="5fddb-184">-无事务。</span><span class="sxs-lookup"><span data-stu-id="5fddb-184">-   No transaction.</span></span><br /><br /> <span data-ttu-id="5fddb-185">新的当前 TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="5fddb-185">new current TransactionTraceId</span></span>|  
|<span data-ttu-id="5fddb-186">TransactionScopeDisposed</span><span class="sxs-lookup"><span data-stu-id="5fddb-186">TransactionScopeDisposed</span></span>|<span data-ttu-id="5fddb-187">信息</span><span class="sxs-lookup"><span data-stu-id="5fddb-187">Info</span></span>|<span data-ttu-id="5fddb-188">作用域的 "预期" 当前事务的 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="5fddb-188">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="5fddb-189">TransactionScopeIncomplete</span><span class="sxs-lookup"><span data-stu-id="5fddb-189">TransactionScopeIncomplete</span></span>|<span data-ttu-id="5fddb-190">警告</span><span class="sxs-lookup"><span data-stu-id="5fddb-190">Warning</span></span>|<span data-ttu-id="5fddb-191">作用域的 "预期" 当前事务的 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="5fddb-191">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="5fddb-192">TransactionScopeNestedIncorrectly</span><span class="sxs-lookup"><span data-stu-id="5fddb-192">TransactionScopeNestedIncorrectly</span></span>|<span data-ttu-id="5fddb-193">警告</span><span class="sxs-lookup"><span data-stu-id="5fddb-193">Warning</span></span>|<span data-ttu-id="5fddb-194">作用域的 "预期" 当前事务的 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="5fddb-194">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="5fddb-195">TransactionScopeCurrentTransactionChanged</span><span class="sxs-lookup"><span data-stu-id="5fddb-195">TransactionScopeCurrentTransactionChanged</span></span>|<span data-ttu-id="5fddb-196">警告</span><span class="sxs-lookup"><span data-stu-id="5fddb-196">Warning</span></span>|<span data-ttu-id="5fddb-197">旧的当前 TransactionTraceId、其他 TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="5fddb-197">Old current TransactionTraceId, other TransactionTraceId</span></span>|  
|<span data-ttu-id="5fddb-198">TransactionScopeTimeout</span><span class="sxs-lookup"><span data-stu-id="5fddb-198">TransactionScopeTimeout</span></span>|<span data-ttu-id="5fddb-199">警告</span><span class="sxs-lookup"><span data-stu-id="5fddb-199">Warning</span></span>|<span data-ttu-id="5fddb-200">作用域的 "预期" 当前事务的 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="5fddb-200">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="5fddb-201">DependentCloneCreated</span><span class="sxs-lookup"><span data-stu-id="5fddb-201">DependentCloneCreated</span></span>|<span data-ttu-id="5fddb-202">信息</span><span class="sxs-lookup"><span data-stu-id="5fddb-202">Info</span></span>|<span data-ttu-id="5fddb-203">TransactionTraceId、已创建的依赖事务的类型 (RollbackIfNotComplete/BlockCommitUntilComplete)</span><span class="sxs-lookup"><span data-stu-id="5fddb-203">TransactionTraceId, type of dependent transaction created (RollbackIfNotComplete/BlockCommitUntilComplete)</span></span>|  
|<span data-ttu-id="5fddb-204">DependentCloneComplete</span><span class="sxs-lookup"><span data-stu-id="5fddb-204">DependentCloneComplete</span></span>|<span data-ttu-id="5fddb-205">信息</span><span class="sxs-lookup"><span data-stu-id="5fddb-205">Info</span></span>|<span data-ttu-id="5fddb-206">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="5fddb-206">TransactionTraceId</span></span>|  
|<span data-ttu-id="5fddb-207">RecoveryComplete</span><span class="sxs-lookup"><span data-stu-id="5fddb-207">RecoveryComplete</span></span>|<span data-ttu-id="5fddb-208">信息</span><span class="sxs-lookup"><span data-stu-id="5fddb-208">Info</span></span>|<span data-ttu-id="5fddb-209">资源管理器 GUID（来自基类型）</span><span class="sxs-lookup"><span data-stu-id="5fddb-209">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="5fddb-210">Reenlist</span><span class="sxs-lookup"><span data-stu-id="5fddb-210">Reenlist</span></span>|<span data-ttu-id="5fddb-211">信息</span><span class="sxs-lookup"><span data-stu-id="5fddb-211">Info</span></span>|<span data-ttu-id="5fddb-212">资源管理器 GUID（来自基类型）</span><span class="sxs-lookup"><span data-stu-id="5fddb-212">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="5fddb-213">TransactionSerialized</span><span class="sxs-lookup"><span data-stu-id="5fddb-213">TransactionSerialized</span></span>|<span data-ttu-id="5fddb-214">信息</span><span class="sxs-lookup"><span data-stu-id="5fddb-214">Info</span></span>|<span data-ttu-id="5fddb-215">TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="5fddb-215">TransactionTraceId.</span></span>|  
|<span data-ttu-id="5fddb-216">TransactionException</span><span class="sxs-lookup"><span data-stu-id="5fddb-216">TransactionException</span></span>|<span data-ttu-id="5fddb-217">错误</span><span class="sxs-lookup"><span data-stu-id="5fddb-217">Error</span></span>|<span data-ttu-id="5fddb-218">异常消息</span><span class="sxs-lookup"><span data-stu-id="5fddb-218">Exception message</span></span>|  
|<span data-ttu-id="5fddb-219">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="5fddb-219">InvalidOperationException</span></span>|<span data-ttu-id="5fddb-220">错误</span><span class="sxs-lookup"><span data-stu-id="5fddb-220">Error</span></span>|<span data-ttu-id="5fddb-221">异常消息</span><span class="sxs-lookup"><span data-stu-id="5fddb-221">Exception message</span></span>|  
|<span data-ttu-id="5fddb-222">InternalError</span><span class="sxs-lookup"><span data-stu-id="5fddb-222">InternalError</span></span>|<span data-ttu-id="5fddb-223">严重</span><span class="sxs-lookup"><span data-stu-id="5fddb-223">Critical</span></span>|<span data-ttu-id="5fddb-224">异常消息</span><span class="sxs-lookup"><span data-stu-id="5fddb-224">Exception message</span></span>|  
|<span data-ttu-id="5fddb-225">TransferEvent</span><span class="sxs-lookup"><span data-stu-id="5fddb-225">TransferEvent</span></span>||<span data-ttu-id="5fddb-226">当事务反序列化或者从 <xref:System.Transactions> 事务提升为分布式事务时，将写入 ExecutionContext 中的当前 ActivityID 以及分布式事务 ID。</span><span class="sxs-lookup"><span data-stu-id="5fddb-226">When a transaction is deserialized, or promoted from a <xref:System.Transactions> transaction to a distributed one, the current ActivityID from the ExecutionContext and the distributed transaction ID are written.</span></span><br /><br /> <span data-ttu-id="5fddb-227">当 DTC 回调到托管代码中时，分布式事务 ID 会在回调期间设置为 ExecutionContext 中的 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="5fddb-227">When the DTC calls back into managed code, the distributed transaction ID is set as the ActivityID in the ExecutionContext for the duration of the callback.</span></span>|  
|<span data-ttu-id="5fddb-228">ConfiguredDefaultTimeoutAdjusted</span><span class="sxs-lookup"><span data-stu-id="5fddb-228">ConfiguredDefaultTimeoutAdjusted</span></span>|<span data-ttu-id="5fddb-229">警告</span><span class="sxs-lookup"><span data-stu-id="5fddb-229">Warning</span></span>|<span data-ttu-id="5fddb-230">没有额外数据</span><span class="sxs-lookup"><span data-stu-id="5fddb-230">No extra data</span></span>|  
|<span data-ttu-id="5fddb-231">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="5fddb-231">TransactionTimeout</span></span>|<span data-ttu-id="5fddb-232">警告</span><span class="sxs-lookup"><span data-stu-id="5fddb-232">Warning</span></span>|<span data-ttu-id="5fddb-233">正在超时的事务的 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="5fddb-233">The TransactionTraceId of the transaction being timed out.</span></span>|  
  
 <span data-ttu-id="5fddb-234">上述每个额外数据项的 XML 架构采用以下格式。</span><span class="sxs-lookup"><span data-stu-id="5fddb-234">The XML schema for each of the preceding extra data items has the following format.</span></span>  
  
### <a name="transactiontraceidentifier"></a><span data-ttu-id="5fddb-235">TransactionTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="5fddb-235">TransactionTraceIdentifier</span></span>  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a><span data-ttu-id="5fddb-236">EnlistmentTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="5fddb-236">EnlistmentTraceIdentifier</span></span>  
 `<EnlistmentTraceIdentifier>`  
  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `<CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<EnlistmentIdentifier>`  
  
 `the enlistment id number`  
  
 `</EnlistmentIdentifier>`  
  
 `</EnlistmentTraceIdentifier>`  
  
### <a name="resource-manager-identifier"></a><span data-ttu-id="5fddb-237">资源管理器标识符</span><span class="sxs-lookup"><span data-stu-id="5fddb-237">Resource Manager Identifier</span></span>  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
## <a name="security-issues-for-tracing"></a><span data-ttu-id="5fddb-238">跟踪的安全问题</span><span class="sxs-lookup"><span data-stu-id="5fddb-238">Security Issues For Tracing</span></span>  
 <span data-ttu-id="5fddb-239">当您以管理员身份启用跟踪时，可能会向默认情况下可公开查看的跟踪日志写入敏感信息。</span><span class="sxs-lookup"><span data-stu-id="5fddb-239">When you as an administrator turn on tracing, sensitive information might be written to a trace log that is publicly viewable by default.</span></span> <span data-ttu-id="5fddb-240">若要消除任何可能的安全威胁，应考虑将该跟踪日志存储在一个由共享和文件系统访问权限控制的安全位置。</span><span class="sxs-lookup"><span data-stu-id="5fddb-240">To mitigate any possible security threat, you should consider storing the trace log in a secure location controlled by share and file system access permissions.</span></span>
