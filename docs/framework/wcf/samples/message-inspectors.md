---
title: 消息检查器
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 1a5519e815a6714e087a77c69e943a3a8c65db68
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585073"
---
# <a name="message-inspectors"></a><span data-ttu-id="8e86f-102">消息检查器</span><span class="sxs-lookup"><span data-stu-id="8e86f-102">Message Inspectors</span></span>
<span data-ttu-id="8e86f-103">本示例演示如何实现和配置客户端和服务消息检查器。</span><span class="sxs-lookup"><span data-stu-id="8e86f-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="8e86f-104">消息检查器是一个扩展性对象，可以编程方式或通过配置用于服务模型的客户端运行时和调度运行时，并可以在接收消息之后或发送消息之前检查和更改消息。</span><span class="sxs-lookup"><span data-stu-id="8e86f-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="8e86f-105">本示例实现基本客户端和服务消息验证机制，该机制基于一组可配置的 XML 架构文档验证传入消息。</span><span class="sxs-lookup"><span data-stu-id="8e86f-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="8e86f-106">请注意，本示例并不验证每个操作的消息。</span><span class="sxs-lookup"><span data-stu-id="8e86f-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="8e86f-107">这是一种有意的简化。</span><span class="sxs-lookup"><span data-stu-id="8e86f-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="8e86f-108">消息检查器</span><span class="sxs-lookup"><span data-stu-id="8e86f-108">Message Inspector</span></span>  
 <span data-ttu-id="8e86f-109">客户端消息检查器实现 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> 接口，而服务消息检查器实现 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> 接口。</span><span class="sxs-lookup"><span data-stu-id="8e86f-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="8e86f-110">可以将这两种实现合并到单个类中以形成适用于两端的消息检查器。</span><span class="sxs-lookup"><span data-stu-id="8e86f-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="8e86f-111">本示例实现这样的合并消息检查器。</span><span class="sxs-lookup"><span data-stu-id="8e86f-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="8e86f-112">该检查器通过传入一组架构来创建，基于这组架构验证传入和传出消息，并允许开发人员指定是否验证传入或传出消息以及检查器是处于调度模式还是客户端模式，所处的模式将影响错误的处理，如本主题后面的论述。</span><span class="sxs-lookup"><span data-stu-id="8e86f-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
```csharp
public class SchemaValidationMessageInspector : IClientMessageInspector, IDispatchMessageInspector  
{  
    XmlSchemaSet schemaSet;  
    bool validateRequest;  
    bool validateReply;  
    bool isClientSide;  
    [ThreadStatic]  
    bool isRequest;  
  
    public SchemaValidationMessageInspector(XmlSchemaSet schemaSet,  
         bool validateRequest, bool validateReply, bool isClientSide)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = validateReply;  
        this.validateRequest = validateRequest;  
        this.isClientSide = isClientSide;  
    }  
```  
  
 <span data-ttu-id="8e86f-113">任何服务（调度程序）消息检查器都必须实现两个 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> 方法：<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 和 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>。</span><span class="sxs-lookup"><span data-stu-id="8e86f-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="8e86f-114">当通道堆栈接收到消息、处理消息并将消息分配给服务后且在将消息反序列化并调度到操作之前，调度程序将调用 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>。</span><span class="sxs-lookup"><span data-stu-id="8e86f-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="8e86f-115">如果传入消息是加密的消息，则在消息到达消息检查器之时，已经对消息解密。</span><span class="sxs-lookup"><span data-stu-id="8e86f-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="8e86f-116">该方法获取作为引用参数进行传递的 `request` 消息，这允许根据需要检查、操作或替换消息。</span><span class="sxs-lookup"><span data-stu-id="8e86f-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="8e86f-117">返回值可以是任何对象，并可用作服务对当前消息返回答复时传递给 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> 的相关状态对象。</span><span class="sxs-lookup"><span data-stu-id="8e86f-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="8e86f-118">在本示例中，<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 将消息的检查（验证）委托给本地私有方法 `ValidateMessageBody` 而不返回相关状态对象。</span><span class="sxs-lookup"><span data-stu-id="8e86f-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="8e86f-119">此方法可确保不会将无效的消息传入服务。</span><span class="sxs-lookup"><span data-stu-id="8e86f-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
```csharp  
object IDispatchMessageInspector.AfterReceiveRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel, System.ServiceModel.InstanceContext instanceContext)  
{  
    if (validateRequest)  
    {  
        // inspect the message. If a validation error occurs,  
        // the thrown fault exception bubbles up.  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <span data-ttu-id="8e86f-120">每当准备好要发回客户端的答复时，或在单向消息的情况下已处理完传入消息时，均会调用 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>。</span><span class="sxs-lookup"><span data-stu-id="8e86f-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="8e86f-121">这允许对称地调用所需的扩展，而不管 MEP 如何。</span><span class="sxs-lookup"><span data-stu-id="8e86f-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="8e86f-122">与 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 一样，消息作为引用参数进行传递，并可以进行检查、修改或替换。</span><span class="sxs-lookup"><span data-stu-id="8e86f-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="8e86f-123">在本示例中执行的消息验证也委托给 `ValidMessageBody` 方法，但本例中处理验证错误的方式略有不同。</span><span class="sxs-lookup"><span data-stu-id="8e86f-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="8e86f-124">如果在服务上发生验证错误，则 `ValidateMessageBody` 方法将引发从 <xref:System.ServiceModel.FaultException> 派生的异常。</span><span class="sxs-lookup"><span data-stu-id="8e86f-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="8e86f-125">在 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 中，可以将这些异常放入服务模型基础结构中，异常在基础结构中将自动转换为 SOAP 错误并中继到客户端。</span><span class="sxs-lookup"><span data-stu-id="8e86f-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="8e86f-126">在 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> 中，不能将 <xref:System.ServiceModel.FaultException> 异常放入基础结构中，因为由服务引发的错误异常的转换将在调用消息检查器之前发生。</span><span class="sxs-lookup"><span data-stu-id="8e86f-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="8e86f-127">因此，下面的实现捕捉已知的 `ReplyValidationFault` 异常并用显式错误消息替换答复消息。</span><span class="sxs-lookup"><span data-stu-id="8e86f-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="8e86f-128">此方法可确保服务实现不会返回无效的消息。</span><span class="sxs-lookup"><span data-stu-id="8e86f-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
```csharp  
void IDispatchMessageInspector.BeforeSendReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        // Inspect the reply, catch a possible validation error
        try  
        {  
            ValidateMessageBody(ref reply, false);  
        }  
        catch (ReplyValidationFault fault)  
        {  
            // if a validation error occurred, the message is replaced  
            // with the validation fault.  
            reply = Message.CreateMessage(reply.Version,
                    fault.CreateMessageFault(), reply.Headers.Action);  
        }  
    }  
```  
  
 <span data-ttu-id="8e86f-129">客户端消息检查器非常相似。</span><span class="sxs-lookup"><span data-stu-id="8e86f-129">The client message inspector is very similar.</span></span> <span data-ttu-id="8e86f-130">必须从 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> 实现的两个方法是 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> 和 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>。</span><span class="sxs-lookup"><span data-stu-id="8e86f-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="8e86f-131">客户端应用程序或操作格式化程序在撰写消息后将调用 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>。</span><span class="sxs-lookup"><span data-stu-id="8e86f-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="8e86f-132">与调度程序消息检查器一样，可以只检查消息，也可以完全替换消息。</span><span class="sxs-lookup"><span data-stu-id="8e86f-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="8e86f-133">在本示例中，检查器向同一本地 `ValidateMessageBody` 帮助器方法进行委托，该方法也可用于调度消息检查器。</span><span class="sxs-lookup"><span data-stu-id="8e86f-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="8e86f-134">客户端验证和服务验证（在构造函数中指定）之间的行为差异是客户端验证引发放在用户代码中的本地异常，因为这些异常发生在本地而不是由于服务失败造成的。</span><span class="sxs-lookup"><span data-stu-id="8e86f-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="8e86f-135">一般规则是服务调度程序检查器引发错误，而客户端检查器引发异常。</span><span class="sxs-lookup"><span data-stu-id="8e86f-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="8e86f-136">此 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> 实现可确保不会向服务发送无效的消息。</span><span class="sxs-lookup"><span data-stu-id="8e86f-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
```csharp  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <span data-ttu-id="8e86f-137">`AfterReceiveReply` 实现可确保不会将从服务接收的无效消息中继到客户端用户代码中。</span><span class="sxs-lookup"><span data-stu-id="8e86f-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="8e86f-138">此特定消息检查器的核心是 `ValidateMessageBody` 方法。</span><span class="sxs-lookup"><span data-stu-id="8e86f-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="8e86f-139">为了执行工作，检查器会在所传递消息的正文内容子树周围包装一个验证 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="8e86f-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="8e86f-140">将用消息检查器包含的一组架构填充该读取器，并会将验证回调设置为引用与此方法并排定义的 `InspectionValidationHandler` 的委托。</span><span class="sxs-lookup"><span data-stu-id="8e86f-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="8e86f-141">为了执行验证，将随后读取消息并后台处理到受内存流支持的 <xref:System.Xml.XmlDictionaryWriter> 中。</span><span class="sxs-lookup"><span data-stu-id="8e86f-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="8e86f-142">如果在进程中发生验证错误或警告，则调用回调方法。</span><span class="sxs-lookup"><span data-stu-id="8e86f-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="8e86f-143">如果不发生错误，则构造新消息，该消息复制原始消息中的属性和标头并使用内存流中经过验证的信息集，该信息集由一个 <xref:System.Xml.XmlDictionaryReader> 包装并添加到替换消息中。</span><span class="sxs-lookup"><span data-stu-id="8e86f-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
```csharp  
void ValidateMessageBody(ref System.ServiceModel.Channels.Message message, bool isRequest)  
{  
    if (!message.IsFault)  
    {  
        XmlDictionaryReaderQuotas quotas =
                new XmlDictionaryReaderQuotas();  
        XmlReader bodyReader =
            message.GetReaderAtBodyContents().ReadSubtree();  
        XmlReaderSettings wrapperSettings =
                              new XmlReaderSettings();  
        wrapperSettings.CloseInput = true;  
        wrapperSettings.Schemas = schemaSet;  
        wrapperSettings.ValidationFlags =
                                XmlSchemaValidationFlags.None;  
        wrapperSettings.ValidationType = ValidationType.Schema;  
        wrapperSettings.ValidationEventHandler += new
           ValidationEventHandler(InspectionValidationHandler);  
        XmlReader wrappedReader = XmlReader.Create(bodyReader,
                                            wrapperSettings);  
  
        // pull body into a memory backed writer to validate  
        this.isRequest = isRequest;  
        MemoryStream memStream = new MemoryStream();  
        XmlDictionaryWriter xdw =  
              XmlDictionaryWriter.CreateBinaryWriter(memStream);  
        xdw.WriteNode(wrappedReader, false);  
        xdw.Flush(); memStream.Position = 0;  
        XmlDictionaryReader xdr =
        XmlDictionaryReader.CreateBinaryReader(memStream, quotas);  
  
        // reconstruct the message with the validated body  
        Message replacedMessage =
            Message.CreateMessage(message.Version, null, xdr);  
        replacedMessage.Headers.CopyHeadersFrom(message.Headers);  
        replacedMessage.Properties.CopyProperties(message.Properties);  
        message = replacedMessage;  
    }  
}  
```  
  
 <span data-ttu-id="8e86f-144">每当发生架构验证错误或警告时，验证 `InspectionValidationHandler` 就会调用 <xref:System.Xml.XmlReader> 方法。</span><span class="sxs-lookup"><span data-stu-id="8e86f-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="8e86f-145">下面的实现仅处理错误，而忽略所有警告。</span><span class="sxs-lookup"><span data-stu-id="8e86f-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="8e86f-146">首先需要考虑的是，有可能使用消息检查器将验证 <xref:System.Xml.XmlReader> 插入到消息中并在处理消息时执行验证且不对消息进行缓冲处理。</span><span class="sxs-lookup"><span data-stu-id="8e86f-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="8e86f-147">但这意味着在检测到无效 XML 节点时，此回调将在服务模型基础结构或用户代码中的某处引发验证异常，从而导致无法预料的行为。</span><span class="sxs-lookup"><span data-stu-id="8e86f-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="8e86f-148">缓存方法可彻底防止用户代码中出现无效消息。</span><span class="sxs-lookup"><span data-stu-id="8e86f-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="8e86f-149">如前面所述，由处理程序引发的异常在客户端和服务之间有所不同。</span><span class="sxs-lookup"><span data-stu-id="8e86f-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="8e86f-150">在服务上，异常派生自 <xref:System.ServiceModel.FaultException>，而在客户端，异常是常规自定义异常。</span><span class="sxs-lookup"><span data-stu-id="8e86f-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
```csharp  
        void InspectionValidationHandler(object sender, ValidationEventArgs e)  
{  
    if (e.Severity == XmlSeverityType.Error)  
    {  
        // We are treating client and service side validation errors  
        // differently here. Client side errors cause exceptions  
        // and are thrown straight up to the user code. Service side  
        // validations cause faults.  
        if (isClientSide)  
        {  
            if (isRequest)  
            {  
                throw new RequestClientValidationException(e.Message);  
            }  
            else  
            {  
                throw new ReplyClientValidationException(e.Message);  
            }  
        }  
        else  
        {  
            if (isRequest)  
            {  
                // this fault is caught by the ServiceModel
                // infrastructure and turned into a fault reply.  
                throw new RequestValidationFault(e.Message);  
             }  
             else  
             {  
                // this fault is caught and turned into a fault message  
                // in BeforeSendReply in this class  
                throw new ReplyValidationFault(e.Message);  
              }  
          }  
      }  
    }  
```  
  
## <a name="behavior"></a><span data-ttu-id="8e86f-151">行为</span><span class="sxs-lookup"><span data-stu-id="8e86f-151">Behavior</span></span>  
 <span data-ttu-id="8e86f-152">消息检查器是客户端运行时或调度运行时的扩展。</span><span class="sxs-lookup"><span data-stu-id="8e86f-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="8e86f-153">此类扩展使用*行为*进行配置。</span><span class="sxs-lookup"><span data-stu-id="8e86f-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="8e86f-154">行为是通过更改默认配置或添加扩展（如消息检查器）来更改服务模型运行时行为的类。</span><span class="sxs-lookup"><span data-stu-id="8e86f-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="8e86f-155">下面的 `SchemaValidationBehavior` 类是用于将本示例的消息检查器添加到客户端运行时或调度运行时的行为。</span><span class="sxs-lookup"><span data-stu-id="8e86f-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="8e86f-156">该实现在这两种情况下都是相当基础的行为。</span><span class="sxs-lookup"><span data-stu-id="8e86f-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="8e86f-157">在 <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> 和 <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A> 中，将创建消息检查器并将其添加到各自运行时的 <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> 集合中。</span><span class="sxs-lookup"><span data-stu-id="8e86f-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
```csharp
public class SchemaValidationBehavior : IEndpointBehavior  
{  
    XmlSchemaSet schemaSet;
    bool validateRequest;
    bool validateReply;  
  
    public SchemaValidationBehavior(XmlSchemaSet schemaSet, bool
                           inspectRequest, bool inspectReply)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = inspectReply;  
        this.validateRequest = inspectRequest;  
    }  
    #region IEndpointBehavior Members  
  
    public void AddBindingParameters(ServiceEndpoint endpoint,
       System.ServiceModel.Channels.BindingParameterCollection
                                            bindingParameters)  
    {  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint,
            System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
    {  
        SchemaValidationMessageInspector inspector =
           new SchemaValidationMessageInspector(schemaSet,
                      validateRequest, validateReply, true);  
            clientRuntime.MessageInspectors.Add(inspector);  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint,
         System.ServiceModel.Dispatcher.EndpointDispatcher
                                          endpointDispatcher)  
    {  
        SchemaValidationMessageInspector inspector =
           new SchemaValidationMessageInspector(schemaSet,
                        validateRequest, validateReply, false);  
   endpointDispatcher.DispatchRuntime.MessageInspectors.Add(inspector);  
    }  
  
   public void Validate(ServiceEndpoint endpoint)  
   {  
   }  
  
    #endregion  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="8e86f-158">此特定行为不能复制为属性，因此不能以声明性方式添加到服务类型的协定类型上。</span><span class="sxs-lookup"><span data-stu-id="8e86f-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="8e86f-159">这是设计使然，由于架构集合不能加载到属性声明中，因此引用此属性中的其他配置位置（例如引用应用程序设置）意味着会创建与服务模型配置的其余元素不一致的配置元素。</span><span class="sxs-lookup"><span data-stu-id="8e86f-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="8e86f-160">因此，只能通过代码和通过服务模型配置扩展强制添加此行为。</span><span class="sxs-lookup"><span data-stu-id="8e86f-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="8e86f-161">通过配置添加消息检查器</span><span class="sxs-lookup"><span data-stu-id="8e86f-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="8e86f-162">若要在应用程序配置文件中的终结点上配置自定义行为，服务模型要求实现者创建由派生自的类表示的配置*扩展元素* <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 。</span><span class="sxs-lookup"><span data-stu-id="8e86f-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="8e86f-163">然后，必须将此扩展添加到服务模型的配置节作为扩展，如本节讨论的以下扩展所示。</span><span class="sxs-lookup"><span data-stu-id="8e86f-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
```xml  
<system.serviceModel>  
…  
   <extensions>  
      <behaviorExtensions>  
        <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
      </behaviorExtensions>  
    </extensions>  
…  
</system.serviceModel>  
```  
  
 <span data-ttu-id="8e86f-164">可以将扩展添加到应用程序或 ASP.NET 配置文件中，这是最常见的选择，也可以添加到计算机配置文件中。</span><span class="sxs-lookup"><span data-stu-id="8e86f-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="8e86f-165">在将扩展添加到配置范围时，可以将行为添加到行为配置中，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="8e86f-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="8e86f-166">行为配置是可以重复使用的元素，可以根据需要应用于多个终结点。</span><span class="sxs-lookup"><span data-stu-id="8e86f-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="8e86f-167">由于此处要配置的特定行为可实现 <xref:System.ServiceModel.Description.IEndpointBehavior>，因此该行为仅在配置文件的相应配置节中有效。</span><span class="sxs-lookup"><span data-stu-id="8e86f-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
   <behaviors>  
      …  
     <endpointBehaviors>  
        <behavior name="HelloServiceEndpointBehavior">  
          <schemaValidator validateRequest="True" validateReply="True">  
            <schemas>  
              <add location="messages.xsd" />
            </schemas>  
          </schemaValidator>  
        </behavior>  
      </endpointBehaviors>  
      …  
    </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="8e86f-168">用于配置消息检查器的 `<schemaValidator>` 元素由 `SchemaValidationBehaviorExtensionElement` 类提供支持。</span><span class="sxs-lookup"><span data-stu-id="8e86f-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="8e86f-169">此类公开两个名为 `ValidateRequest` 和 `ValidateReply` 的布尔型公共属性。</span><span class="sxs-lookup"><span data-stu-id="8e86f-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="8e86f-170">这两个属性均使用 <xref:System.Configuration.ConfigurationPropertyAttribute> 进行标记。</span><span class="sxs-lookup"><span data-stu-id="8e86f-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="8e86f-171">此属性 (attribute) 构成代码属性 (property) 和 XML 属性 (attribute) 之间的链接，这可以在前面的 XML 配置元素上看到。</span><span class="sxs-lookup"><span data-stu-id="8e86f-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="8e86f-172">此类还有一个额外使用 `Schemas` 进行标记的 <xref:System.Configuration.ConfigurationCollectionAttribute> 属性，其类型为 `SchemaCollection`，此属性也是本示例的组成部分，但为了简便起见，本文档中省略了此属性。</span><span class="sxs-lookup"><span data-stu-id="8e86f-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="8e86f-173">此属性以及集合和集合元素类 `SchemaConfigElement` 支持前面配置代码段中的 `<schemas>` 元素，并允许将架构集合添加到验证集中。</span><span class="sxs-lookup"><span data-stu-id="8e86f-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="8e86f-174">重写的 `CreateBehavior` 方法会在运行时为生成客户端或终结点而计算配置数据时将配置数据转换为行为对象。</span><span class="sxs-lookup"><span data-stu-id="8e86f-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
```csharp
public class SchemaValidationBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public SchemaValidationBehaviorExtensionElement()  
    {  
    }  
  
    public override Type BehaviorType
    {
        get  
        {  
            return typeof(SchemaValidationBehavior);  
        }
    }  
  
    protected override object CreateBehavior()  
    {  
        XmlSchemaSet schemaSet = new XmlSchemaSet();  
        foreach (SchemaConfigElement schemaCfg in this.Schemas)  
        {  
            Uri baseSchema = new
                Uri(AppDomain.CurrentDomain.BaseDirectory);  
            string location = new
                Uri(baseSchema,schemaCfg.Location).ToString();  
            XmlSchema schema =
                XmlSchema.Read(new XmlTextReader(location), null);  
            schemaSet.Add(schema);  
        }  
     return new
     SchemaValidationBehavior(schemaSet,ValidateRequest,ValidateReply);  
    }  
  
[ConfigurationProperty("validateRequest",DefaultValue=false,IsRequired=false)]  
public bool ValidateRequest  
{  
    get { return (bool)base["validateRequest"]; }  
    set { base["validateRequest"] = value; }  
}  
  
[ConfigurationProperty("validateReply", DefaultValue = false, IsRequired = false)]  
        public bool ValidateReply  
        {  
            get { return (bool)base["validateReply"]; }  
            set { base["validateReply"] = value; }  
        }  
  
     //Declare the Schema collection property.  
     //Note: the "IsDefaultCollection = false" instructs
     //.NET Framework to build a nested section of
     //the kind <Schema> ...</Schema>.  
    [ConfigurationProperty("schemas", IsDefaultCollection = true)]  
    [ConfigurationCollection(typeof(SchemasCollection),  
        AddItemName = "add",  
        ClearItemsName = "clear",  
        RemoveItemName = "remove")]  
    public SchemasCollection Schemas  
    {  
        get  
        {  
            SchemasCollection SchemasCollection =  
            (SchemasCollection)base["schemas"];  
            return SchemasCollection;  
        }  
    }  
}  
```  
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="8e86f-175">强制添加消息检查器</span><span class="sxs-lookup"><span data-stu-id="8e86f-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="8e86f-176">除了通过属性（由于前述原因本示例中不支持属性）和配置添加行为外，使用命令性代码也可以很容易地将行为添加到客户端和服务运行时。</span><span class="sxs-lookup"><span data-stu-id="8e86f-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="8e86f-177">在本示例中，在客户端应用程序中完成此操作以测试客户端消息检查器。</span><span class="sxs-lookup"><span data-stu-id="8e86f-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="8e86f-178">`GenericClient` 类派生自 <xref:System.ServiceModel.ClientBase%601>，可向用户代码公开终结点配置。</span><span class="sxs-lookup"><span data-stu-id="8e86f-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="8e86f-179">在隐式打开客户端之前，可以更改终结点配置（例如通过添加行为），如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="8e86f-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="8e86f-180">在服务上添加行为在很大程度上等效于此处所示的客户端技术，并且必须在打开服务主机之前执行。</span><span class="sxs-lookup"><span data-stu-id="8e86f-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
```csharp  
try  
{  
    Console.WriteLine("*** Call 'Hello' with generic client, with client behavior");  
    GenericClient client = new GenericClient();  
  
    // Configure client programmatically, adding behavior  
    XmlSchema schema = XmlSchema.Read(new StreamReader("messages.xsd"),
                                                          null);  
    XmlSchemaSet schemaSet = new XmlSchemaSet();  
    schemaSet.Add(schema);  
    client.Endpoint.Behaviors.Add(new
                SchemaValidationBehavior(schemaSet, true, true));  
  
    Console.WriteLine("--- Sending valid client request:");  
    GenericCallValid(client, helloAction);  
    Console.WriteLine("--- Sending invalid client request:");  
    GenericCallInvalid(client, helloAction);  
  
    client.Close();  
}  
catch (Exception e)  
{  
    DumpException(e);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8e86f-181">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="8e86f-181">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8e86f-182">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="8e86f-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8e86f-183">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="8e86f-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8e86f-184">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="8e86f-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8e86f-185">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="8e86f-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8e86f-186">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="8e86f-186">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8e86f-187">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="8e86f-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8e86f-188">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="8e86f-188">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
