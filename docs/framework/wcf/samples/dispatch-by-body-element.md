---
title: 按正文元素调度
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 19913cdaa47d766f62a313e216a653ac69633a99
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594694"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="00815-102">按正文元素调度</span><span class="sxs-lookup"><span data-stu-id="00815-102">Dispatch by Body Element</span></span>
<span data-ttu-id="00815-103">本示例演示如何实现用于将传入消息分配到操作的可选算法。</span><span class="sxs-lookup"><span data-stu-id="00815-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="00815-104">默认情况下，服务模型调度程序会根据消息的 WS-Addressing“Action”标头或 HTTP SOAP 请求中的等效信息为传入消息选择适当的处理方法。</span><span class="sxs-lookup"><span data-stu-id="00815-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="00815-105">有些不遵循 WS-I Basic Profile 1.1 准则的 SOAP 1.1 Web 服务堆栈并不根据 Action URI 来调度消息，而是根据 SOAP 正文内第一个元素的 XML 限定名来调度消息。</span><span class="sxs-lookup"><span data-stu-id="00815-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="00815-106">同样，这些堆栈的客户端可能会发送具有空标头或任意 HTTP SoapAction 标头的消息，这是 SOAP 1.1 规范所允许的。</span><span class="sxs-lookup"><span data-stu-id="00815-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="00815-107">为了更改向方法调度消息的方式，此示例在 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 上实现 `DispatchByBodyElementOperationSelector` 扩展性接口。</span><span class="sxs-lookup"><span data-stu-id="00815-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="00815-108">此类根据消息正文的第一个元素来选择操作。</span><span class="sxs-lookup"><span data-stu-id="00815-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="00815-109">类构造函数需要一个用 `XmlQualifiedName` 和字符串对填充的字典，其中限定名称指示 SOAP 正文的第一个子级的名称，而字符串指示匹配的操作名称。</span><span class="sxs-lookup"><span data-stu-id="00815-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="00815-110">`defaultOperationName` 是操作的名称，该操作接收无法与此字典匹配的所有消息：</span><span class="sxs-lookup"><span data-stu-id="00815-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
```csharp
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
}
```  
  
 <span data-ttu-id="00815-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 实现的生成非常简单，因为在接口上只有一个方法：<xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>。</span><span class="sxs-lookup"><span data-stu-id="00815-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="00815-112">此方法的任务是检查传入消息并返回一个字符串，该字符串为当前终结点服务协定上的方法的名称。</span><span class="sxs-lookup"><span data-stu-id="00815-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="00815-113">在此示例中，操作选择器使用 <xref:System.Xml.XmlDictionaryReader> 获取传入消息正文的 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>。</span><span class="sxs-lookup"><span data-stu-id="00815-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="00815-114">此方法已经将读取器定位在消息正文的第一个子级上，因此完全可以获取当前元素的名称和命名空间 URI 并将它们结合成 `XmlQualifiedName`，然后用它来从操作选择器保存的字典中查找相应的操作。</span><span class="sxs-lookup"><span data-stu-id="00815-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
```csharp
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 <span data-ttu-id="00815-115">访问消息正文时，不管使用的是 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> 还是可以访问消息正文内容的任何其他方法，都将导致该消息被标记为“已读”，这意味着该消息不能进行任何进一步处理。</span><span class="sxs-lookup"><span data-stu-id="00815-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="00815-116">因此，操作选择器将使用下面代码演示的方法创建传入消息的副本。</span><span class="sxs-lookup"><span data-stu-id="00815-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="00815-117">因为在检查过程中读取器的位置没有更改，可以由新创建的消息引用，消息属性和消息头也会复制到新创建的消息中，因此可以得到与原始消息完全相同的克隆：</span><span class="sxs-lookup"><span data-stu-id="00815-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
```csharp
private Message CreateMessageCopy(Message message,
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="00815-118">向服务添加操作选择器</span><span class="sxs-lookup"><span data-stu-id="00815-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="00815-119">服务调度操作选择器是对 Windows Communication Foundation （WCF）调度程序的扩展。</span><span class="sxs-lookup"><span data-stu-id="00815-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="00815-120">在双工协定回调通道上选择方法时，还可以使用客户端操作选择器，其工作方式类似于本文说明的调度操作选择器，但未显式包括在此示例中。</span><span class="sxs-lookup"><span data-stu-id="00815-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="00815-121">和多数服务模型扩展一样，调度操作选择器通过使用行为来添加到调度程序。</span><span class="sxs-lookup"><span data-stu-id="00815-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="00815-122">*行为*是配置对象，它将一个或多个扩展添加到调度运行时（或客户端运行时），或者更改其设置。</span><span class="sxs-lookup"><span data-stu-id="00815-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="00815-123">由于操作选择器具有协定范围，因此本示例要实现的适当行为是 <xref:System.ServiceModel.Description.IContractBehavior>。</span><span class="sxs-lookup"><span data-stu-id="00815-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="00815-124">由于接口是在 <xref:System.Attribute> 派生类上实现的（如下面的代码所示），因此可以以声明方式将行为添加到任何服务协定。</span><span class="sxs-lookup"><span data-stu-id="00815-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="00815-125">每当打开 <xref:System.ServiceModel.ServiceHost> 并生成调度运行时时，都会自动添加作为协定、操作和服务实现上的属性的所有行为或作为服务配置中的元素的所有行为，随后要求这些行为提供扩展或修改默认设置。</span><span class="sxs-lookup"><span data-stu-id="00815-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="00815-126">为了简洁起见，下面的代码摘录仅演示 <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> 方法的实现，此方法影响本示例中调度程序的配置更改。</span><span class="sxs-lookup"><span data-stu-id="00815-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="00815-127">未演示其他方法，因为它们不执行任何操作就返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="00815-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="00815-128">首先，<xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> 实现通过遍历服务终结点的 <xref:System.ServiceModel.Description.OperationDescription> 中的 <xref:System.ServiceModel.Description.ContractDescription> 元素为操作选择器设置查找字典。</span><span class="sxs-lookup"><span data-stu-id="00815-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="00815-129">然后检查每个操作说明是否存在 `DispatchBodyElementAttribute` 行为，即也在此示例中定义的 <xref:System.ServiceModel.Description.IOperationBehavior> 的实现。</span><span class="sxs-lookup"><span data-stu-id="00815-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="00815-130">虽然此类也是一种行为，但它是被动行为，不会主动向调度运行时提供任何配置更改。</span><span class="sxs-lookup"><span data-stu-id="00815-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="00815-131">其所有方法都不执行任何操作就返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="00815-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="00815-132">此操作行为的存在只是为了新调度机制所要求的元数据（即在存在时将会选择一种操作的正文元素的限定名）可以与相应的操作相关联。</span><span class="sxs-lookup"><span data-stu-id="00815-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="00815-133">如果找到这样的行为，将会向字典添加使用 XML 限定名（`QName` 属性）和操作名（`Name` 属性）创建的值对。</span><span class="sxs-lookup"><span data-stu-id="00815-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="00815-134">填充字典后，将使用此信息构造一个新的 `DispatchByBodyElementOperationSelector` 并将其设置为调度运行时的操作选择器：</span><span class="sxs-lookup"><span data-stu-id="00815-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
```csharp
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a><span data-ttu-id="00815-135">实现服务</span><span class="sxs-lookup"><span data-stu-id="00815-135">Implementing the Service</span></span>  
 <span data-ttu-id="00815-136">本示例中实现的行为直接影响如何解释和调度来自网络的消息，这是服务协定的功能。</span><span class="sxs-lookup"><span data-stu-id="00815-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="00815-137">因此，在选择使用该行为的任何服务实现中，均应在服务协定级别声明该行为。</span><span class="sxs-lookup"><span data-stu-id="00815-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="00815-138">示例项目服务将 `DispatchByBodyElementBehaviorAttribute` 协定行为应用于 `IDispatchedByBody` 服务协定，并标记两个操作 `OperationForBodyA()` 和 `OperationForBodyB()` 一个 `DispatchBodyElementAttribute` 操作行为。</span><span class="sxs-lookup"><span data-stu-id="00815-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="00815-139">如前面所述，在打开实现此协定的服务的服务主机时，调度程序生成器将选取此元数据。</span><span class="sxs-lookup"><span data-stu-id="00815-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="00815-140">由于操作选择器只根据消息正文元素进行调度并忽略“Action”，因此需要通过将通配符“\*”分配给 `ReplyAction` 的 <xref:System.ServiceModel.OperationContractAttribute> 属性来告诉运行时不要对返回的答复检查“Action”标头。</span><span class="sxs-lookup"><span data-stu-id="00815-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="00815-141">此外，需要将 "Action" 属性的默认操作设置为通配符 " \* "。</span><span class="sxs-lookup"><span data-stu-id="00815-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="00815-142">此默认操作接收所有无法调度的消息并且没有 `DispatchBodyElementAttribute`：</span><span class="sxs-lookup"><span data-stu-id="00815-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 <span data-ttu-id="00815-143">示例服务的实现非常简单。</span><span class="sxs-lookup"><span data-stu-id="00815-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="00815-144">每个方法都可将接收的消息包装成答复消息并将其回送到客户端。</span><span class="sxs-lookup"><span data-stu-id="00815-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="00815-145">运行和生成示例</span><span class="sxs-lookup"><span data-stu-id="00815-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="00815-146">运行示例时，操作响应的正文内容将显示在客户端控制台窗口中，类似于下面的（格式化）输出。</span><span class="sxs-lookup"><span data-stu-id="00815-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="00815-147">客户端向服务发送三个消息，它们的正文内容元素分别命名为 `bodyA`、`bodyB` 和 `bodyX`。</span><span class="sxs-lookup"><span data-stu-id="00815-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="00815-148">从前面的说明和演示的服务协定可以推断，带有 `bodyA` 元素的传入消息将调度到 `OperationForBodyA()` 方法。</span><span class="sxs-lookup"><span data-stu-id="00815-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="00815-149">因为对于带有 `bodyX` 正文元素的消息没有显式调度目标，因此该消息将被调度到 `DefaultOperation()`。</span><span class="sxs-lookup"><span data-stu-id="00815-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="00815-150">每个服务操作都会将接收到的消息正文包装成特定于方法的元素并返回此元素，对于本示例，这样做是为了明确地关联输入和输出消息：</span><span class="sxs-lookup"><span data-stu-id="00815-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="00815-151">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="00815-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="00815-152">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="00815-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="00815-153">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="00815-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="00815-154">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="00815-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="00815-155">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="00815-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="00815-156">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="00815-156">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="00815-157">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="00815-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="00815-158">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="00815-158">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
