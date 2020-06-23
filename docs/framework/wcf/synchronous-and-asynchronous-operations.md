---
title: 同步和异步操作
description: 了解如何实现和调用异步服务操作。 WCF 服务和客户端可以在应用程序的两个级别使用异步操作。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: f52f2613c96c0149c330bb75f80c6738f8d41146
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245908"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="6f09e-104">同步和异步操作</span><span class="sxs-lookup"><span data-stu-id="6f09e-104">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="6f09e-105">本主题讨论实现和调用异步服务操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-105">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="6f09e-106">许多应用程序都以异步方式调用方法，因为这样允许应用程序在运行方法调用时继续执行有用的工作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-106">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="6f09e-107">Windows Communication Foundation (WCF) 服务和客户端可以在两个不同的应用程序级别参与异步操作调用，这会为 WCF 应用程序在最大程度提高针对交互性而平衡的吞吐量方面提供更好的灵活性。</span><span class="sxs-lookup"><span data-stu-id="6f09e-107">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="6f09e-108">异步操作的类型</span><span class="sxs-lookup"><span data-stu-id="6f09e-108">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="6f09e-109">无论参数类型和返回值如何，WCF 中的所有服务协定都使用 WCF 特性来指定客户端和服务之间的特殊消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="6f09e-109">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="6f09e-110">WCF 自动将入站和出站消息路由到相应的服务操作或正在运行的客户端代码。</span><span class="sxs-lookup"><span data-stu-id="6f09e-110">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="6f09e-111">客户端仅拥有为特殊操作指定消息交换模式的服务协定。</span><span class="sxs-lookup"><span data-stu-id="6f09e-111">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="6f09e-112">客户端可以为开发人员提供他们所选择的任何编程模型，但前提是找到了基础消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="6f09e-112">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="6f09e-113">因此，只要找到了指定的消息模式，服务也可以按任何方式来实现操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-113">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="6f09e-114">如果服务协定独立于服务或客户端实现，则可以在 WCF 应用程序中实现下列形式的异步执行：</span><span class="sxs-lookup"><span data-stu-id="6f09e-114">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
- <span data-ttu-id="6f09e-115">客户端可以使用同步消息交换以异步方式调用请求/响应操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-115">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="6f09e-116">服务可以使用同步消息交换以异步方式实现请求/响应操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-116">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="6f09e-117">消息交换可以是单向的，而与客户端或服务的实现无关。</span><span class="sxs-lookup"><span data-stu-id="6f09e-117">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="6f09e-118">建议的异步方案</span><span class="sxs-lookup"><span data-stu-id="6f09e-118">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="6f09e-119">如果操作服务实现执行阻止调用（如执行 I/O 工作），则在该服务操作实现中使用异步方法。</span><span class="sxs-lookup"><span data-stu-id="6f09e-119">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="6f09e-120">在异步操作实现中，可尝试调用异步操作和方法来尽可能远地扩展异步调用路径。</span><span class="sxs-lookup"><span data-stu-id="6f09e-120">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="6f09e-121">例如，从 `BeginOperationTwo()` 中调用 `BeginOperationOne()`。</span><span class="sxs-lookup"><span data-stu-id="6f09e-121">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
- <span data-ttu-id="6f09e-122">在下列情况下，可在客户端应用程序或调用应用程序中使用异步方法：</span><span class="sxs-lookup"><span data-stu-id="6f09e-122">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
- <span data-ttu-id="6f09e-123">如果从中间层应用程序调用操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-123">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="6f09e-124">（有关此类方案的详细信息，请参阅[中间层客户端应用程序](./feature-details/middle-tier-client-applications.md)。）</span><span class="sxs-lookup"><span data-stu-id="6f09e-124">(For more information about such scenarios, see [Middle-Tier Client Applications](./feature-details/middle-tier-client-applications.md).)</span></span>  
  
- <span data-ttu-id="6f09e-125">如果在 ASP.NET 页中调用操作，可使用异步页。</span><span class="sxs-lookup"><span data-stu-id="6f09e-125">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
- <span data-ttu-id="6f09e-126">如果从任何单线程的应用程序（如 Windows 窗体或 Windows Presentation Foundation (WPF)）调用操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-126">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="6f09e-127">使用基于事件的异步调用模型时，将在 UI 线程上引发结果事件，从而向应用程序添加响应性而无需您自己处理多个线程。</span><span class="sxs-lookup"><span data-stu-id="6f09e-127">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
- <span data-ttu-id="6f09e-128">通常，如果可在同步调用和异步调用之间进行选择，应选择异步调用。</span><span class="sxs-lookup"><span data-stu-id="6f09e-128">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="6f09e-129">实现异步服务操作</span><span class="sxs-lookup"><span data-stu-id="6f09e-129">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="6f09e-130">可以通过使用下列三种方法之一实现异步操作：</span><span class="sxs-lookup"><span data-stu-id="6f09e-130">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1. <span data-ttu-id="6f09e-131">基于任务的异步模式</span><span class="sxs-lookup"><span data-stu-id="6f09e-131">The task-based asynchronous pattern</span></span>  
  
2. <span data-ttu-id="6f09e-132">基于事件的异步模式</span><span class="sxs-lookup"><span data-stu-id="6f09e-132">The event-based asynchronous pattern</span></span>  
  
3. <span data-ttu-id="6f09e-133">IAsyncResult 异步模式</span><span class="sxs-lookup"><span data-stu-id="6f09e-133">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="6f09e-134">基于任务的异步模式</span><span class="sxs-lookup"><span data-stu-id="6f09e-134">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="6f09e-135">基于任务的异步模式是实现异步操作的首选方法，因为它最简单且最直接。</span><span class="sxs-lookup"><span data-stu-id="6f09e-135">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="6f09e-136">若要使用此方法，只需实现服务操作并指定任务的返回类型 \<T> ，其中 T 是逻辑运算返回的类型。</span><span class="sxs-lookup"><span data-stu-id="6f09e-136">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="6f09e-137">例如：</span><span class="sxs-lookup"><span data-stu-id="6f09e-137">For example:</span></span>  
  
```csharp  
public class SampleService:ISampleService
{
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)
   {
      return Task<string>.Factory.StartNew(() =>
      {
         return msg;
      });
   }  
   // ...  
}  
```  
  
 <span data-ttu-id="6f09e-138">SampleMethodTaskAsync 操作返回任务， \<string> 因为逻辑操作返回一个字符串。</span><span class="sxs-lookup"><span data-stu-id="6f09e-138">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="6f09e-139">有关基于任务的异步模式的更多信息，请参见[基于任务的异步模式](https://go.microsoft.com/fwlink/?LinkId=232504)。</span><span class="sxs-lookup"><span data-stu-id="6f09e-139">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="6f09e-140">在使用基于任务的异步模式时，如果在等待操作完成时发生异常，可能会引发 T:System.AggregateException。</span><span class="sxs-lookup"><span data-stu-id="6f09e-140">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="6f09e-141">该异常可在客户端或服务上发生</span><span class="sxs-lookup"><span data-stu-id="6f09e-141">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="6f09e-142">基于事件的异步模式</span><span class="sxs-lookup"><span data-stu-id="6f09e-142">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="6f09e-143">支持基于事件的异步模式的服务将有一个或多个名为 MethodNameAsync 的操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-143">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="6f09e-144">这些方法可能会创建同步版本的镜像，这些同步版本会在当前线程上执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-144">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="6f09e-145">该类还可能具有 MethodNameCompleted 事件，并且可能会具有 MethodNameAsyncCancel（或只是 CancelAsync）方法。</span><span class="sxs-lookup"><span data-stu-id="6f09e-145">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="6f09e-146">希望调用操作的客户端将定义操作完成时要调用的事件处理程序，</span><span class="sxs-lookup"><span data-stu-id="6f09e-146">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="6f09e-147">下面的代码段演示如何使用基于事件的异步模式声明异步操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-147">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="6f09e-148">有关基于事件的异步模式的更多信息，请参见[基于事件的异步模式](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6f09e-148">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="6f09e-149">IAsyncResult 异步模式</span><span class="sxs-lookup"><span data-stu-id="6f09e-149">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="6f09e-150">服务操作可以使用 .NET Framework 异步编程模式，并标记 `<Begin>` 属性设置为的方法，以异步方式实现 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> `true` 。</span><span class="sxs-lookup"><span data-stu-id="6f09e-150">A service operation can be implemented in an asynchronous fashion using the .NET Framework asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="6f09e-151">在这种情况下，异步操作将以与同步操作相同的方式在元数据中公开，即作为单个操作随请求消息和相关的响应消息来公开。</span><span class="sxs-lookup"><span data-stu-id="6f09e-151">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="6f09e-152">随后，客户端编程模型可以进行选择。</span><span class="sxs-lookup"><span data-stu-id="6f09e-152">Client programming models then have a choice.</span></span> <span data-ttu-id="6f09e-153">客户端编程模型可以将这种模式表示为同步操作，也可以表示为异步操作，但前提是调用该服务时发生了请求-响应消息交换。</span><span class="sxs-lookup"><span data-stu-id="6f09e-153">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="6f09e-154">通常，考虑到系统的异步特性，您不应依赖于线程。</span><span class="sxs-lookup"><span data-stu-id="6f09e-154">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="6f09e-155">将数据传递到操作调度处理的各个阶段的最可靠方式是使用扩展。</span><span class="sxs-lookup"><span data-stu-id="6f09e-155">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="6f09e-156">有关示例，请参见[如何：实现异步服务操作](how-to-implement-an-asynchronous-service-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="6f09e-156">For an example, see [How to: Implement an Asynchronous Service Operation](how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="6f09e-157">定义一个异步执行（而不考虑它在客户端应用程序中的调用方式）的协定操作 `X`：</span><span class="sxs-lookup"><span data-stu-id="6f09e-157">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
- <span data-ttu-id="6f09e-158">使用 `BeginOperation` 和 `EndOperation` 模式定义两个方法。</span><span class="sxs-lookup"><span data-stu-id="6f09e-158">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
- <span data-ttu-id="6f09e-159">`BeginOperation` 方法包括该操作的 `in` 和 `ref` 参数，并返回一个 <xref:System.IAsyncResult> 类型。</span><span class="sxs-lookup"><span data-stu-id="6f09e-159">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
- <span data-ttu-id="6f09e-160">`EndOperation` 方法包括一个 <xref:System.IAsyncResult> 参数以及 `out` 和 `ref` 参数，并返回操作的返回类型。</span><span class="sxs-lookup"><span data-stu-id="6f09e-160">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="6f09e-161">有关示例，请参见下面的方法。</span><span class="sxs-lookup"><span data-stu-id="6f09e-161">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="6f09e-162">若要创建异步操作，这两种方法应为：</span><span class="sxs-lookup"><span data-stu-id="6f09e-162">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
> <span data-ttu-id="6f09e-163"><xref:System.ServiceModel.OperationContractAttribute> 属性仅适用于 `BeginDoWork` 方法。</span><span class="sxs-lookup"><span data-stu-id="6f09e-163">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="6f09e-164">所得到的协定具有一个名为 `DoWork` 的 WSDL 操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-164">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="6f09e-165">客户端异步调用</span><span class="sxs-lookup"><span data-stu-id="6f09e-165">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="6f09e-166">WCF 客户端应用程序可使用之前介绍的三个异步调用模型中的任意一个</span><span class="sxs-lookup"><span data-stu-id="6f09e-166">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="6f09e-167">在使用基于任务的模型时，只需使用 await 关键字调用操作，如下面的代码段所示。</span><span class="sxs-lookup"><span data-stu-id="6f09e-167">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="6f09e-168">使用基于事件的异步模式只需添加事件处理程序，即可接收响应的通知 -- 将在用户界面线程上自动引发生成的事件。</span><span class="sxs-lookup"><span data-stu-id="6f09e-168">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="6f09e-169">若要使用此方法，请使用 [ServiceModel 元数据实用工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) 并同时指定 /async\*\*\*\* 和 /tcv:Version35\*\*\*\* 命令选项，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6f09e-169">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="6f09e-170">完成此操作后，Svcutil.exe 将生成带有事件基础结构的 WCF 客户端类，该事件基础结构使调用应用程序可以实现和分配事件处理程序，以便接收响应和采取相应的操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-170">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="6f09e-171">有关完整示例，请参见[如何：以异步方式调用服务操作](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="6f09e-171">For a complete example, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="6f09e-172">不过，基于事件的异步模型仅在 .NET Framework 3.5 中提供。</span><span class="sxs-lookup"><span data-stu-id="6f09e-172">The event-based asynchronous model, however, is only available in .NET Framework 3.5.</span></span> <span data-ttu-id="6f09e-173">此外，如果使用创建 WCF 客户端通道，则不支持此方法，即使在 .NET Framework 3.5 中也是如此 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="6f09e-173">In addition, it is not supported even in .NET Framework 3.5 when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6f09e-174">使用 WCF 客户端通道对象时，必须使用 <xref:System.IAsyncResult?displayProperty=nameWithType> 对象异步调用操作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-174">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="6f09e-175">若要使用此方法，请使用 [ServiceModel 元数据实用工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) 并指定 /async\*\*\*\* 命令选项，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6f09e-175">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async
```  
  
 <span data-ttu-id="6f09e-176">这会生成一个服务协定，在该服务协定中，每个操作都作为 `<Begin>` 方法（其 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> 属性设置为 `true`）和相应的 `<End>` 方法来建模。</span><span class="sxs-lookup"><span data-stu-id="6f09e-176">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="6f09e-177">有关使用 <xref:System.ServiceModel.ChannelFactory%601> 的完整示例，请参见[如何：使用通道工厂以异步方式调用操作](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)。</span><span class="sxs-lookup"><span data-stu-id="6f09e-177">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="6f09e-178">在任何一种情况下，即使服务是以同步方式实现的，应用程序也可以异步方式调用操作，就如同应用程序可以使用同一个模式以异步方式调用本地同步方法一样。</span><span class="sxs-lookup"><span data-stu-id="6f09e-178">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="6f09e-179">操作的实现方式对于客户端而言并不重要;当响应消息到达时，会将其内容分派给客户端的异步 <`End`> 方法，客户端将检索此信息。</span><span class="sxs-lookup"><span data-stu-id="6f09e-179">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="6f09e-180">单向消息交换模式</span><span class="sxs-lookup"><span data-stu-id="6f09e-180">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="6f09e-181">还可以创建一个异步消息交换模式，在该模式下，单向操作（其 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> 为 `true` 的操作，该操作没有相关的响应）可以由客户端或服务独立于另一端来单向发送。</span><span class="sxs-lookup"><span data-stu-id="6f09e-181">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="6f09e-182">（这会将双工消息交换模式用于单向消息。）在这种情况下，服务协定指定单向消息交换，无论是哪种情况，都可以根据需要将其任意一方实现为异步调用或实现。</span><span class="sxs-lookup"><span data-stu-id="6f09e-182">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="6f09e-183">通常，当服务协定是单向消息交换时，这些实现极有可能是异步的，因为在发送消息之后，应用程序不会等待答复，而是继续执行其他工作。</span><span class="sxs-lookup"><span data-stu-id="6f09e-183">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="6f09e-184">基于事件的异步模式客户端和消息协定</span><span class="sxs-lookup"><span data-stu-id="6f09e-184">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="6f09e-185">基于事件的异步模型设计准则规定，如果返回了多个值，则一个值会作为 `Result` 属性返回，其他值会作为 <xref:System.EventArgs> 对象上的属性返回。</span><span class="sxs-lookup"><span data-stu-id="6f09e-185">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="6f09e-186">因此产生的结果之一是，如果客户端使用基于事件的异步命令选项导入元数据，且该操作返回多个值，则默认的 <xref:System.EventArgs> 对象将返回一个值作为 `Result` 属性，返回的其余值是 <xref:System.EventArgs> 对象的属性。</span><span class="sxs-lookup"><span data-stu-id="6f09e-186">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="6f09e-187">如果要将消息对象作为 `Result` 属性来接收并要使返回的值作为该对象上的属性，请使用 /messageContract\*\*\*\* 命令选项。</span><span class="sxs-lookup"><span data-stu-id="6f09e-187">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="6f09e-188">这会生成一个签名，该签名会将响应消息作为 `Result` 对象上的 <xref:System.EventArgs> 属性返回。</span><span class="sxs-lookup"><span data-stu-id="6f09e-188">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="6f09e-189">然后，所有内部返回值就都是响应消息对象的属性了。</span><span class="sxs-lookup"><span data-stu-id="6f09e-189">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f09e-190">请参阅</span><span class="sxs-lookup"><span data-stu-id="6f09e-190">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
