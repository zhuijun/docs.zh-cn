---
title: 使用消息约定
description: 了解如何使用消息协定属性在 WFC 中指定 SOAP 消息的结构。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 0a75298b50df74ddf15904af43a0eb62c5ba8496
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244707"
---
# <a name="using-message-contracts"></a><span data-ttu-id="157be-103">使用消息约定</span><span class="sxs-lookup"><span data-stu-id="157be-103">Using Message Contracts</span></span>
<span data-ttu-id="157be-104">通常，当构建 Windows Communication Foundation （WCF）应用程序时，开发人员会密切关注数据结构和序列化问题，而无需考虑在其中携带数据的消息的结构。</span><span class="sxs-lookup"><span data-stu-id="157be-104">Typically when building Windows Communication Foundation (WCF) applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="157be-105">对于这些应用程序，为参数或返回值创建数据协定的过程很简单。</span><span class="sxs-lookup"><span data-stu-id="157be-105">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="157be-106">（有关详细信息，请参阅[在服务协定中指定数据传输](specifying-data-transfer-in-service-contracts.md)。）</span><span class="sxs-lookup"><span data-stu-id="157be-106">(For more information, see [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="157be-107">但是，有时完全控制 SOAP 消息的结构与控制其内容一样重要。</span><span class="sxs-lookup"><span data-stu-id="157be-107">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="157be-108">当必须提供互操作性或需要在消息或消息部分级别特别控制安全问题时，更是如此。</span><span class="sxs-lookup"><span data-stu-id="157be-108">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="157be-109">在这些情况下，你可以创建一个*消息协定*，使你能够指定所需的精确 SOAP 消息的结构。</span><span class="sxs-lookup"><span data-stu-id="157be-109">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="157be-110">本主题讨论如何使用各种消息协定属性为操作创建特定消息协定。</span><span class="sxs-lookup"><span data-stu-id="157be-110">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="157be-111">在操作中使用消息协定</span><span class="sxs-lookup"><span data-stu-id="157be-111">Using Message Contracts in Operations</span></span>  
 <span data-ttu-id="157be-112">WCF 支持在*远程过程调用（RPC）样式*或*消息传递样式*上建模的操作。</span><span class="sxs-lookup"><span data-stu-id="157be-112">WCF supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="157be-113">在 RPC 样式的操作中，可以使用任何可序列化的类型并可以访问可用于本地调用的功能，如多个参数以及 `ref` 和 `out` 参数。</span><span class="sxs-lookup"><span data-stu-id="157be-113">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="157be-114">在此样式中，所选序列化的格式控制基础消息中的数据结构，WCF 运行时创建消息来支持该操作。</span><span class="sxs-lookup"><span data-stu-id="157be-114">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the WCF runtime creates the messages to support the operation.</span></span> <span data-ttu-id="157be-115">这使对 SOAP 和 SOAP 消息不熟悉的开发人员能够快速容易地创建和使用服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="157be-115">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="157be-116">下面的代码示例演示在 RPC 样式上建模的服务操作。</span><span class="sxs-lookup"><span data-stu-id="157be-116">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="157be-117">通常，定义消息的架构时使用数据协定就足够了。</span><span class="sxs-lookup"><span data-stu-id="157be-117">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="157be-118">例如，在前面的示例中，如果 `BankingTransaction` 和 `BankingTransactionResponse` 具有定义基础 SOAP 消息内容的数据协定，则对于大多数应用程序就足够了。</span><span class="sxs-lookup"><span data-stu-id="157be-118">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="157be-119">有关数据协定的详细信息，请参阅[使用数据协定](using-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="157be-119">For more information about data contracts, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="157be-120">但是，有时需要精确控制 SOAP 消息的结构如何通过网络进行传输。</span><span class="sxs-lookup"><span data-stu-id="157be-120">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="157be-121">对于这种情况，最常见的方案是插入自定义 SOAP 标头。</span><span class="sxs-lookup"><span data-stu-id="157be-121">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="157be-122">另一种常见方案是定义消息头和正文的安全属性，也就是说，确定是否对这些元素进行数字签名和加密。</span><span class="sxs-lookup"><span data-stu-id="157be-122">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="157be-123">最后，一些第三方 SOAP 堆栈要求消息采用特定的格式。</span><span class="sxs-lookup"><span data-stu-id="157be-123">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="157be-124">消息样式的操作可提供这种控制。</span><span class="sxs-lookup"><span data-stu-id="157be-124">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="157be-125">消息样式的操作最多具有一个参数和一个返回值，其中参数和返回值的类型都是消息类型；也就是说，这两种类型可直接序列化为指定的 SOAP 消息结构。</span><span class="sxs-lookup"><span data-stu-id="157be-125">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="157be-126">这可以是用 <xref:System.ServiceModel.MessageContractAttribute> 标记的任何类型或 <xref:System.ServiceModel.Channels.Message> 类型。</span><span class="sxs-lookup"><span data-stu-id="157be-126">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="157be-127">下面的代码示例演示类似于前面 RPC 样式的操作，但此操作使用消息样式。</span><span class="sxs-lookup"><span data-stu-id="157be-127">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="157be-128">例如，如果 `BankingTransaction` 和 `BankingTransactionResponse` 都是作为消息协定的类型，则以下操作中的代码有效。</span><span class="sxs-lookup"><span data-stu-id="157be-128">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="157be-129">但下面的代码无效。</span><span class="sxs-lookup"><span data-stu-id="157be-129">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="157be-130">对于涉及消息协定类型且不符合有效模式之一的任何操作会引发异常。</span><span class="sxs-lookup"><span data-stu-id="157be-130">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="157be-131">当然，不涉及消息协定类型的操作不受这些限制的约束。</span><span class="sxs-lookup"><span data-stu-id="157be-131">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="157be-132">如果一个类型既有消息协定又有数据协定，则在操作中使用此类型时只考虑其消息协定。</span><span class="sxs-lookup"><span data-stu-id="157be-132">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="157be-133">定义消息协定</span><span class="sxs-lookup"><span data-stu-id="157be-133">Defining Message Contracts</span></span>  
 <span data-ttu-id="157be-134">若要为某一类型定义消息协定（即定义该类型和 SOAP 信封之间的映射），请对该类型应用 <xref:System.ServiceModel.MessageContractAttribute>。</span><span class="sxs-lookup"><span data-stu-id="157be-134">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="157be-135">然后对该类型中要成为 SOAP 标头的成员应用 <xref:System.ServiceModel.MessageHeaderAttribute>，并对要成为消息的 SOAP 正文部分的成员应用 <xref:System.ServiceModel.MessageBodyMemberAttribute>。</span><span class="sxs-lookup"><span data-stu-id="157be-135">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="157be-136">下面的代码提供了一个使用消息协定的示例。</span><span class="sxs-lookup"><span data-stu-id="157be-136">The following code provides an example of using a message contract.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader] public DateTime transactionDate;  
  [MessageBodyMember] private Account sourceAccount;  
  [MessageBodyMember] private Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="157be-137">使用此类型作为操作参数时，会生成以下的 SOAP 信封：</span><span class="sxs-lookup"><span data-stu-id="157be-137">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
    <h:transactionDate xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">2012-02-16T16:10:00</h:transactionDate>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <BankingTransaction xmlns="http://tempuri.org/">  
      <amount>0</amount>  
      <sourceAccount xsi:nil="true"/>  
      <targetAccount xsi:nil="true"/>  
    </BankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="157be-138">请注意，`operation` 和 `transactionDate` 显示为 SOAP 标头，而 SOAP 正文由包装元素 `BankingTransaction` 组成，其中包括 `sourceAccount`、`targetAccount` 和 `amount`。</span><span class="sxs-lookup"><span data-stu-id="157be-138">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="157be-139">可以对所有字段、属性和事件应用 <xref:System.ServiceModel.MessageHeaderAttribute> 和 <xref:System.ServiceModel.MessageBodyMemberAttribute>，而不管这些字段、属性和事件是公用的、私有的、受保护的还是内部的。</span><span class="sxs-lookup"><span data-stu-id="157be-139">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="157be-140"><xref:System.ServiceModel.MessageContractAttribute> 允许您指定 WrapperName 和 WrapperNamespace 特性，这些特性控制 SOAP 消息的正文中包装元素的名称。</span><span class="sxs-lookup"><span data-stu-id="157be-140">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="157be-141">默认情况下，消息协定类型的名称用于包装，而在其中定义消息协定的命名空间 `http://tempuri.org/` 用作默认的命名空间。</span><span class="sxs-lookup"><span data-stu-id="157be-141">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined `http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="157be-142">消息协定中会忽略 <xref:System.Runtime.Serialization.KnownTypeAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="157be-142"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="157be-143">如果需要 <xref:System.Runtime.Serialization.KnownTypeAttribute>，可以将其放在使用所述消息协定的操作上。</span><span class="sxs-lookup"><span data-stu-id="157be-143">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="157be-144">控制标头和正文部分的名称和命名空间</span><span class="sxs-lookup"><span data-stu-id="157be-144">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="157be-145">在消息协定的 SOAP 表示形式中，每个标头和正文部分都映射为一个具有名称和命名空间的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="157be-145">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="157be-146">默认情况下，命名空间与消息加入的服务协定的命名空间相同，名称由应用 <xref:System.ServiceModel.MessageHeaderAttribute> 或 <xref:System.ServiceModel.MessageBodyMemberAttribute> 属性的成员名称确定。</span><span class="sxs-lookup"><span data-stu-id="157be-146">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="157be-147">通过操作 <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> 和 <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType>（在 <xref:System.ServiceModel.MessageHeaderAttribute> 和 <xref:System.ServiceModel.MessageBodyMemberAttribute> 特性的父类上）可以更改这些默认值。</span><span class="sxs-lookup"><span data-stu-id="157be-147">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="157be-148">考虑下面代码示例中的类。</span><span class="sxs-lookup"><span data-stu-id="157be-148">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="157be-149">在此示例中，`IsAudited` 标头位于代码中指定的命名空间中，表示 `theData` 成员的正文部分由名为 `transactionData` 的 XML 元素表示。</span><span class="sxs-lookup"><span data-stu-id="157be-149">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="157be-150">下面显示了为此消息协定生成的 XML。</span><span class="sxs-lookup"><span data-stu-id="157be-150">The following shows the XML generated for this message contract.</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:IsAudited xmlns:h="http://schemas.contoso.com/auditing/2005" xmlns="http://schemas.contoso.com/auditing/2005">false</h:IsAudited>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <AuditedBankingTransaction xmlns="http://tempuri.org/">  
      <transactionData/>  
    </AuditedBankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="157be-151">控制是否包装 SOAP 正文部分</span><span class="sxs-lookup"><span data-stu-id="157be-151">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="157be-152">默认情况下，SOAP 正文部分会在包装元素内部进行序列化。</span><span class="sxs-lookup"><span data-stu-id="157be-152">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="157be-153">例如，下面的代码演示从 `HelloGreetingMessage` 消息的消息协定中的 <xref:System.ServiceModel.MessageContractAttribute> 类型的名称生成的 `HelloGreetingMessage` 包装元素。</span><span class="sxs-lookup"><span data-stu-id="157be-153">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="157be-154">若要取消包装元素，请将 <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> 属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="157be-154">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="157be-155">若要控制包装元素的名称和命名空间，请使用 <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> 和 <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="157be-155">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="157be-156">消息中具有多个未包装的消息正文部分不符合 WS-I 基本配置文件 1.1 的规定，在设计新消息协定时不建议这样做。</span><span class="sxs-lookup"><span data-stu-id="157be-156">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="157be-157">但是，在某些特定的互操作性方案中，必需要具有多个未包装的消息正文部分。</span><span class="sxs-lookup"><span data-stu-id="157be-157">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="157be-158">如果要在消息正文中传输多段数据，则建议使用默认（包装）模式。</span><span class="sxs-lookup"><span data-stu-id="157be-158">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="157be-159">未包装的消息中具有多个消息头是完全可以的。</span><span class="sxs-lookup"><span data-stu-id="157be-159">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="157be-160">在消息协定内部使用自定义类型</span><span class="sxs-lookup"><span data-stu-id="157be-160">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="157be-161">每个单独的消息头和消息正文部分均使用为消息所使用的服务协定选择的序列化引擎进行序列化（转换为 XML）。</span><span class="sxs-lookup"><span data-stu-id="157be-161">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="157be-162">默认序列化引擎  可以显式处理（通过具有 ）或隐式处理（通过作为基元类型而具有 等）具有数据协定的任何类型。</span><span class="sxs-lookup"><span data-stu-id="157be-162">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="157be-163">有关详细信息，请参阅[使用数据协定](using-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="157be-163">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="157be-164">在前面的示例中，`Operation` 和 `BankingTransactionData` 类型必须具有数据约，定且 `transactionDate` 可序列化，因为 <xref:System.DateTime> 是基元类型（因此具有隐式数据协定）。</span><span class="sxs-lookup"><span data-stu-id="157be-164">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="157be-165">不过，也可以切换到另一个序列化引擎 `XmlSerializer`。</span><span class="sxs-lookup"><span data-stu-id="157be-165">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="157be-166">如果进行切换，应确保用于消息头和正文部分的所有类型都可以使用 `XmlSerializer` 进行序列化。</span><span class="sxs-lookup"><span data-stu-id="157be-166">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="157be-167">在消息协定内部使用数组</span><span class="sxs-lookup"><span data-stu-id="157be-167">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="157be-168">可以采用两种方式在消息协定中使用重复元素的数组。</span><span class="sxs-lookup"><span data-stu-id="157be-168">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="157be-169">第一种方式是直接在数组上使用 <xref:System.ServiceModel.MessageHeaderAttribute> 或 <xref:System.ServiceModel.MessageBodyMemberAttribute>。</span><span class="sxs-lookup"><span data-stu-id="157be-169">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="157be-170">在这种情况下，整个数组序列化为一个具有多个子元素的元素（即一个标头或一个正文部分）。</span><span class="sxs-lookup"><span data-stu-id="157be-170">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="157be-171">考虑下面示例中的类。</span><span class="sxs-lookup"><span data-stu-id="157be-171">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="157be-172">这会使 SOAP 标头类似于下面所示。</span><span class="sxs-lookup"><span data-stu-id="157be-172">This results in SOAP headers is similar to the following.</span></span>  
  
```xml  
<BankingDepositLog>  
<numRecords>3</numRecords>  
<records>  
  <DepositRecord>Record1</DepositRecord>  
  <DepositRecord>Record2</DepositRecord>  
  <DepositRecord>Record3</DepositRecord>  
</records>  
<branchID>20643</branchID>  
</BankingDepositLog>  
```  
  
 <span data-ttu-id="157be-173">另一种方式是使用 <xref:System.ServiceModel.MessageHeaderArrayAttribute>。</span><span class="sxs-lookup"><span data-stu-id="157be-173">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="157be-174">在这种情况下，每个数组元素都单独序列化，从而使每个数组元素都具有一个标头，类似于下面所示。</span><span class="sxs-lookup"><span data-stu-id="157be-174">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="157be-175">数组项的默认名称是对其应用 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 属性的成员的名称。</span><span class="sxs-lookup"><span data-stu-id="157be-175">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="157be-176"><xref:System.ServiceModel.MessageHeaderArrayAttribute> 属性继承自 <xref:System.ServiceModel.MessageHeaderAttribute>。</span><span class="sxs-lookup"><span data-stu-id="157be-176">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="157be-177">它具有与非数组属性相同的一组功能，例如，可以像设置单一标头的顺序、名称和命名空间那样设置标头数组的顺序、名称和命名空间。</span><span class="sxs-lookup"><span data-stu-id="157be-177">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="157be-178">在对数组使用 `Order` 属性时，该属性将应用于整个数组。</span><span class="sxs-lookup"><span data-stu-id="157be-178">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="157be-179">可以将 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 只应用于数组，而不应用于集合。</span><span class="sxs-lookup"><span data-stu-id="157be-179">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="157be-180">在消息协定中使用字节数组</span><span class="sxs-lookup"><span data-stu-id="157be-180">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="157be-181">与非数组属性（<xref:System.ServiceModel.MessageBodyMemberAttribute> 和 <xref:System.ServiceModel.MessageHeaderAttribute>）一起使用时，字节数组不被视为数组，而被视为一种特殊的基元类型，在生成的 XML 中表示为 Base64 编码的数据。</span><span class="sxs-lookup"><span data-stu-id="157be-181">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="157be-182">在将字节数组与数组属性 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 一起使用时，结果取决于正在使用的序列化程序。</span><span class="sxs-lookup"><span data-stu-id="157be-182">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="157be-183">如果使用默认序列化程序，会将数组表示为每个字节一个单独项。</span><span class="sxs-lookup"><span data-stu-id="157be-183">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="157be-184">但如果选择 `XmlSerializer`（在服务协定上使用 <xref:System.ServiceModel.XmlSerializerFormatAttribute>），则会将字节数组视为 Base64 数据，而不管是使用数组属性还是非数组属性。</span><span class="sxs-lookup"><span data-stu-id="157be-184">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="157be-185">对消息部分进行签名和加密</span><span class="sxs-lookup"><span data-stu-id="157be-185">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="157be-186">消息协定可以指示消息头和/或正文是否应进行数字签名和加密。</span><span class="sxs-lookup"><span data-stu-id="157be-186">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="157be-187">这可以通过在 <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> 和 <xref:System.ServiceModel.MessageHeaderAttribute> 特性上设置 <xref:System.ServiceModel.MessageBodyMemberAttribute> 属性来完成。</span><span class="sxs-lookup"><span data-stu-id="157be-187">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="157be-188">该属性是 <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> 类型的枚举，可以设置为 <xref:System.Net.Security.ProtectionLevel.None>（不加密或签名）、<xref:System.Net.Security.ProtectionLevel.Sign>（仅数字签名）或 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>（加密并数字签名）。</span><span class="sxs-lookup"><span data-stu-id="157be-188">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="157be-189">默认值为 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>。</span><span class="sxs-lookup"><span data-stu-id="157be-189">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="157be-190">若要让这些安全功能起作用，必须正确配置绑定和行为。</span><span class="sxs-lookup"><span data-stu-id="157be-190">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="157be-191">如果在没有正确配置的情况下使用这些安全功能（例如，在不提供凭据的情况下试图对消息进行签名），则会在验证时引发异常。</span><span class="sxs-lookup"><span data-stu-id="157be-191">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="157be-192">对于消息头，会分别为每个消息头确定其保护级别。</span><span class="sxs-lookup"><span data-stu-id="157be-192">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="157be-193">对于消息正文部分，保护级别可理解为“最低保护级别”。</span><span class="sxs-lookup"><span data-stu-id="157be-193">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="157be-194">无论包含几个正文部分，正文都只有一个保护级别。</span><span class="sxs-lookup"><span data-stu-id="157be-194">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="157be-195">正文的保护级别由所有正文部分的最高 <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> 属性设置确定。</span><span class="sxs-lookup"><span data-stu-id="157be-195">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="157be-196">不过，您应该将每个正文部分的保护级别设置为实际要求的最低保护级别。</span><span class="sxs-lookup"><span data-stu-id="157be-196">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="157be-197">考虑下面代码示例中的类。</span><span class="sxs-lookup"><span data-stu-id="157be-197">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PatientRecord  
{  
   [MessageHeader(ProtectionLevel=None)] public int recordID;  
   [MessageHeader(ProtectionLevel=Sign)] public string patientName;  
   [MessageHeader(ProtectionLevel=EncryptAndSign)] public string SSN;  
   [MessageBodyMember(ProtectionLevel=None)] public string comments;  
   [MessageBodyMember(ProtectionLevel=Sign)] public string diagnosis;  
   [MessageBodyMember(ProtectionLevel=EncryptAndSign)] public string medicalHistory;  
}  
```  
  
 <span data-ttu-id="157be-198">在此示例中，`recordID` 标头未受保护，`patientName` 为 `signed`，`SSN` 进行了加密和签名。</span><span class="sxs-lookup"><span data-stu-id="157be-198">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="157be-199">至少有一个正文部分 `medicalHistory` 已应用 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>，因此将对整个消息正文进行加密和签名，即使 comments 和 diagnosis 正文部分指定了较低的保护级别。</span><span class="sxs-lookup"><span data-stu-id="157be-199">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="157be-200">SOAP 操作</span><span class="sxs-lookup"><span data-stu-id="157be-200">SOAP Action</span></span>  
 <span data-ttu-id="157be-201">SOAP 和相关 Web 服务标准定义了一个名为 `Action` 的属性，该属性可用于发送的每个 SOAP 消息。</span><span class="sxs-lookup"><span data-stu-id="157be-201">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="157be-202">操作的 <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> 和 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> 属性控制此属性的值。</span><span class="sxs-lookup"><span data-stu-id="157be-202">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="157be-203">SOAP 标头属性</span><span class="sxs-lookup"><span data-stu-id="157be-203">SOAP Header Attributes</span></span>  
 <span data-ttu-id="157be-204">SOAP 标准定义了下列可存在于标头上的属性：</span><span class="sxs-lookup"><span data-stu-id="157be-204">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
- <span data-ttu-id="157be-205">`Actor/Role`（在 SOAP 1.1 中为 `Actor`，在 SOAP 1.2 中为 `Role`）</span><span class="sxs-lookup"><span data-stu-id="157be-205">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
- `MustUnderstand`  
  
- `Relay`  
  
 <span data-ttu-id="157be-206">`Actor` 或 `Role` 属性指定要使用给定标头的节点的统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="157be-206">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="157be-207">`MustUnderstand` 属性指定处理标头的节点是否必须理解该标头。</span><span class="sxs-lookup"><span data-stu-id="157be-207">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="157be-208">`Relay` 特性指定标头是否要中继到下游节点。</span><span class="sxs-lookup"><span data-stu-id="157be-208">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> <span data-ttu-id="157be-209">除了 `MustUnderstand` 本主题后面的 "消息协定版本管理" 一节中所述，WCF 不对传入消息执行这些特性的任何处理。</span><span class="sxs-lookup"><span data-stu-id="157be-209">WCF does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="157be-210">但它允许您根据需要读取和写入这些属性，如下所述。</span><span class="sxs-lookup"><span data-stu-id="157be-210">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="157be-211">发送消息时，默认情况下不会发出这些属性。</span><span class="sxs-lookup"><span data-stu-id="157be-211">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="157be-212">您可以采取两种方式更改这一行为。</span><span class="sxs-lookup"><span data-stu-id="157be-212">You can change this in two ways.</span></span> <span data-ttu-id="157be-213">第一种方式是通过更改 <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>、<xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType> 和 <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> 属性，以静态方式将这些特性设置为任何需要的值，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="157be-213">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="157be-214">（请注意，没有 `Role` 属性；如果使用 SOAP 1.2，则设置 <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> 属性会发出 `Role` 特性）。</span><span class="sxs-lookup"><span data-stu-id="157be-214">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="157be-215">第二种方式是通过代码以动态方式控制这些属性。</span><span class="sxs-lookup"><span data-stu-id="157be-215">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="157be-216">为此，您可以将所需的标头包装在 <xref:System.ServiceModel.MessageHeader%601> 类型中（切勿将此类型与非泛型版本混淆），并与 <xref:System.ServiceModel.MessageHeaderAttribute> 一起使用该类型。</span><span class="sxs-lookup"><span data-stu-id="157be-216">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="157be-217">然后，可以在 <xref:System.ServiceModel.MessageHeader%601> 上使用属性来设置 SOAP 特性，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="157be-217">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public MessageHeader<bool> IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
// application code:  
BankingTransaction bt = new BankingTransaction();  
bt.IsAudited = new MessageHeader<bool>();  
bt.IsAudited.Content = false; // Set IsAudited header value to "false"  
bt.IsAudited.Actor="http://auditingservice.contoso.com";  
bt.IsAudited.MustUnderstand=true;  
```  
  
 <span data-ttu-id="157be-218">如果同时使用动态和静态控制机制，则静态设置用作默认设置，但可以在以后使用动态机制重写，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="157be-218">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="157be-219">允许创建具有动态属性控制的重复标头，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="157be-219">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="157be-220">在接收端，仅当对类型中的标头使用 <xref:System.ServiceModel.MessageHeader%601> 类时才能读取这些 SOAP 属性。</span><span class="sxs-lookup"><span data-stu-id="157be-220">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="157be-221">请检查 `Actor` 类型的标头的 `Relay`、`MustUnderstand` 或 <xref:System.ServiceModel.MessageHeader%601> 属性 (Property) 以发现所接收消息的属性 (Attribute) 设置。</span><span class="sxs-lookup"><span data-stu-id="157be-221">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="157be-222">当接收到消息然后发回该消息时，SOAP 属性设置仅对 <xref:System.ServiceModel.MessageHeader%601> 类型的标头往返一次。</span><span class="sxs-lookup"><span data-stu-id="157be-222">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="157be-223">SOAP 正文部分的顺序</span><span class="sxs-lookup"><span data-stu-id="157be-223">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="157be-224">在某些情况下，可能需要控制正文部分的顺序。</span><span class="sxs-lookup"><span data-stu-id="157be-224">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="157be-225">默认情况下，正文元素采用字母顺序，但可以通过 <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> 属性进行控制。</span><span class="sxs-lookup"><span data-stu-id="157be-225">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="157be-226">此属性具有与 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> 属性相同的语义，但在继承方案中的行为除外（在消息协定中，基类型正文成员不排列在派生类型正文成员之前）。</span><span class="sxs-lookup"><span data-stu-id="157be-226">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="157be-227">有关详细信息，请参阅[数据成员顺序](data-member-order.md)。</span><span class="sxs-lookup"><span data-stu-id="157be-227">For more information, see [Data Member Order](data-member-order.md).</span></span>  
  
 <span data-ttu-id="157be-228">在下面的示例中，`amount` 通常排在第一位，因为按字母顺序它排在第一位。</span><span class="sxs-lookup"><span data-stu-id="157be-228">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="157be-229">但 <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> 属性将它放在了第三位。</span><span class="sxs-lookup"><span data-stu-id="157be-229">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember(Order=1)] public Account sourceAccount;  
  [MessageBodyMember(Order=2)] public Account targetAccount;  
  [MessageBodyMember(Order=3)] public int amount;  
}  
```  
  
## <a name="message-contract-versioning"></a><span data-ttu-id="157be-230">消息协定版本管理</span><span class="sxs-lookup"><span data-stu-id="157be-230">Message Contract Versioning</span></span>  
 <span data-ttu-id="157be-231">有时，您可能需要更改消息协定。</span><span class="sxs-lookup"><span data-stu-id="157be-231">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="157be-232">例如，应用程序的新版本可能会向消息中添加额外的标头。</span><span class="sxs-lookup"><span data-stu-id="157be-232">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="157be-233">在从新版本应用程序向旧版本应用程序发送消息时，系统必须处理额外的标头；同样，反方向操作时系统必须处理缺少的标头。</span><span class="sxs-lookup"><span data-stu-id="157be-233">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="157be-234">下面的规则适用于标头的版本管理：</span><span class="sxs-lookup"><span data-stu-id="157be-234">The following rules apply for versioning headers:</span></span>  
  
- <span data-ttu-id="157be-235">WCF 不会将对象移到缺少的标头，相应的成员将保留其默认值。</span><span class="sxs-lookup"><span data-stu-id="157be-235">WCF does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
- <span data-ttu-id="157be-236">WCF 还忽略意外的额外标头。</span><span class="sxs-lookup"><span data-stu-id="157be-236">WCF also ignores unexpected extra headers.</span></span> <span data-ttu-id="157be-237">此规则的一种例外情况是在传入的 SOAP 消息中，额外标头的 `MustUnderstand` 属性设置为 `true`。在这种情况下，由于存在一个无法处理但必须理解的标头，因此会引发异常。</span><span class="sxs-lookup"><span data-stu-id="157be-237">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="157be-238">消息正文具有类似的版本管理规则，即忽略缺少和附加的消息正文部分。</span><span class="sxs-lookup"><span data-stu-id="157be-238">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="157be-239">继承注意事项</span><span class="sxs-lookup"><span data-stu-id="157be-239">Inheritance Considerations</span></span>  
 <span data-ttu-id="157be-240">消息协定类型可以继承自另一个类型，前提是基类型也具有消息协定。</span><span class="sxs-lookup"><span data-stu-id="157be-240">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="157be-241">在使用继承自其他消息协定类型的消息协定类型创建或访问消息时，下面的规则适用：</span><span class="sxs-lookup"><span data-stu-id="157be-241">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
- <span data-ttu-id="157be-242">继承层次结构中的所有消息头集合在一起构成消息头的完整集合。</span><span class="sxs-lookup"><span data-stu-id="157be-242">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
- <span data-ttu-id="157be-243">继承层次结构中的所有消息正文部分集合在一起构成消息正文的完整集合。</span><span class="sxs-lookup"><span data-stu-id="157be-243">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="157be-244">正文部分按照通常排序规则排列（按 <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> 属性，然后按字母顺序排序），与它们在继承层次结构中的位置无关。</span><span class="sxs-lookup"><span data-stu-id="157be-244">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="157be-245">在使用消息协定继承时，强烈建议消息正文部分不要出现在继承树的多个级别上。</span><span class="sxs-lookup"><span data-stu-id="157be-245">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="157be-246">如果基类和派生类用相同的名称定义标头或正文部分，则使用最基础的类中的成员来存储该标头或正文部分的值。</span><span class="sxs-lookup"><span data-stu-id="157be-246">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="157be-247">考虑下面代码示例中的类。</span><span class="sxs-lookup"><span data-stu-id="157be-247">Consider the classes in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PersonRecord  
{  
  [MessageHeader(Name="ID")] public int personID;  
  [MessageBodyMember] public string patientName;  
}  
  
[MessageContract]  
public class PatientRecord : PersonRecord  
{  
  [MessageHeader(Name="ID")] public int patientID;  
  [MessageBodyMember] public string diagnosis;  
}  
```  
  
 <span data-ttu-id="157be-248">`PatientRecord` 类描述了一个消息，该消息具有一个名为 `ID` 的标头。</span><span class="sxs-lookup"><span data-stu-id="157be-248">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="157be-249">该标头对应于 `personID` 而不对应于 `patientID` 成员，因为选择了最基础的成员。</span><span class="sxs-lookup"><span data-stu-id="157be-249">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="157be-250">因此，在这种情况下，`patientID` 字段无用。</span><span class="sxs-lookup"><span data-stu-id="157be-250">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="157be-251">消息正文包含 `diagnosis` 元素，后面跟随 `patientName` 元素，因为这是这些元素的字母顺序。</span><span class="sxs-lookup"><span data-stu-id="157be-251">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="157be-252">表注意，该示例演示了一种强烈建议不要使用的模式：基消息协定和派生消息协定都具有消息正文部分。</span><span class="sxs-lookup"><span data-stu-id="157be-252">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="157be-253">WSDL 注意事项</span><span class="sxs-lookup"><span data-stu-id="157be-253">WSDL Considerations</span></span>  
 <span data-ttu-id="157be-254">在从使用消息协定的服务生成 Web 服务描述语言 (WSDL) 协定时，必须记住生成的 WSDL 中并不会反映所有的消息协定功能。</span><span class="sxs-lookup"><span data-stu-id="157be-254">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="157be-255">请考虑以下要点：</span><span class="sxs-lookup"><span data-stu-id="157be-255">Consider the following points:</span></span>  
  
- <span data-ttu-id="157be-256">WSDL 无法表示标头数组的概念。</span><span class="sxs-lookup"><span data-stu-id="157be-256">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="157be-257">使用 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 创建具有标头数组的消息时，生成的 WSDL 只反映一个标头而不是该数组。</span><span class="sxs-lookup"><span data-stu-id="157be-257">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
- <span data-ttu-id="157be-258">生成的 WSDL 文档可能不反映某些保护级别信息。</span><span class="sxs-lookup"><span data-stu-id="157be-258">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
- <span data-ttu-id="157be-259">在 WSDL 中生成的消息类型的名称与消息协定类型的类名称相同。</span><span class="sxs-lookup"><span data-stu-id="157be-259">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
- <span data-ttu-id="157be-260">在多个操作中使用同一个消息协定时，会在 WSDL 文档中生成多个消息类型。</span><span class="sxs-lookup"><span data-stu-id="157be-260">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="157be-261">对于后续使用，会在名称中添加数字“2”、“3”等以使名称唯一。</span><span class="sxs-lookup"><span data-stu-id="157be-261">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="157be-262">在导回 WSDL 时，会创建多个消息协定类型，除了名称不同外，这些消息协定类型完全相同。</span><span class="sxs-lookup"><span data-stu-id="157be-262">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="157be-263">SOAP 编码注意事项</span><span class="sxs-lookup"><span data-stu-id="157be-263">SOAP Encoding Considerations</span></span>  
 <span data-ttu-id="157be-264">WCF 允许使用 XML 的旧版 SOAP 编码样式，但是不建议使用它。</span><span class="sxs-lookup"><span data-stu-id="157be-264">WCF allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="157be-265">使用这种样式时（在应用于服务协定的 `Use` 上将 `Encoded` 属性设置为 <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>），下面的附加注意事项适用：</span><span class="sxs-lookup"><span data-stu-id="157be-265">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
- <span data-ttu-id="157be-266">不支持消息头；这意味着属性 <xref:System.ServiceModel.MessageHeaderAttribute> 和数组属性 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 与 SOAP 编码不兼容。</span><span class="sxs-lookup"><span data-stu-id="157be-266">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
- <span data-ttu-id="157be-267">如果未包装消息协定，即如果属性 <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> 设置为 `false`，则消息协定只能具有一个正文部分。</span><span class="sxs-lookup"><span data-stu-id="157be-267">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
- <span data-ttu-id="157be-268">请求消息协定的包装元素的名称必须与操作名称匹配。</span><span class="sxs-lookup"><span data-stu-id="157be-268">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="157be-269">为此请使用消息协定的 `WrapperName` 属性。</span><span class="sxs-lookup"><span data-stu-id="157be-269">Use the `WrapperName` property of the message contract for this.</span></span>  
  
- <span data-ttu-id="157be-270">响应消息协定的包装元素的名称必须与具有“Response”后缀的操作名称相同。</span><span class="sxs-lookup"><span data-stu-id="157be-270">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="157be-271">为此请使用消息协定的 <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="157be-271">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
- <span data-ttu-id="157be-272">SOAP 编码保留对象引用。</span><span class="sxs-lookup"><span data-stu-id="157be-272">SOAP encoding preserves object references.</span></span> <span data-ttu-id="157be-273">例如，考虑下面的代码。</span><span class="sxs-lookup"><span data-stu-id="157be-273">For example, consider the following code.</span></span>  
  
    ```csharp  
    [MessageContract(WrapperName="updateChangeRecord")]  
    public class ChangeRecordRequest  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    [MessageContract(WrapperName="updateChangeRecordResponse")]  
    public class ChangeRecordResponse  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    // application code:  
    ChangeRecordRequest cr = new ChangeRecordRequest();  
    Person p = new Person("John Doe");  
    cr.changedBy=p;  
    cr.changedFrom=p;  
    cr.changedTo=p;  
    ```  
  
 <span data-ttu-id="157be-274">使用 SOAP 编码序列化消息后，`changedFrom` 和 `changedTo` 不包含其自己的 `p` 副本，而是指向 `changedBy` 元素内的副本。</span><span class="sxs-lookup"><span data-stu-id="157be-274">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="157be-275">性能注意事项</span><span class="sxs-lookup"><span data-stu-id="157be-275">Performance Considerations</span></span>  
 <span data-ttu-id="157be-276">每个消息头和消息正文部分相互独立地进行序列化。</span><span class="sxs-lookup"><span data-stu-id="157be-276">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="157be-277">因此，可以为每个标头和正文部分重新声明相同的命名空间。</span><span class="sxs-lookup"><span data-stu-id="157be-277">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="157be-278">为了提高性能，特别是对于消息在网络上的大小，请将多个标头和正文部分合并成一个标头或正文部分。</span><span class="sxs-lookup"><span data-stu-id="157be-278">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="157be-279">例如，不要使用下面代码：</span><span class="sxs-lookup"><span data-stu-id="157be-279">For example, instead of the following code:</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public Account sourceAccount;  
  [MessageBodyMember] public Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="157be-280">请使用此代码。</span><span class="sxs-lookup"><span data-stu-id="157be-280">Use this code.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public OperationDetails details;  
}  
  
[DataContract]  
public class OperationDetails  
{  
  [DataMember] public Account sourceAccount;  
  [DataMember] public Account targetAccount;  
  [DataMember] public int amount;  
}  
```  
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="157be-281">基于事件的异步协定和消息协定</span><span class="sxs-lookup"><span data-stu-id="157be-281">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="157be-282">基于事件的异步模型设计准则规定，如果返回了多个值，则一个值会作为 `Result` 属性返回，其他值会作为 <xref:System.EventArgs> 对象上的属性返回。</span><span class="sxs-lookup"><span data-stu-id="157be-282">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="157be-283">因此产生的结果之一是，如果客户端使用基于事件的异步命令选项导入元数据，且该操作返回多个值，则默认的 <xref:System.EventArgs> 对象将返回一个值作为 `Result` 属性，返回的其余值是 <xref:System.EventArgs> 对象的属性。</span><span class="sxs-lookup"><span data-stu-id="157be-283">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="157be-284">如果要将消息对象作为 `Result` 属性来接收并要使返回的值作为该对象上的属性，请使用 `/messageContract` 命令选项。</span><span class="sxs-lookup"><span data-stu-id="157be-284">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="157be-285">这会生成一个签名，该签名会将响应消息作为 `Result` 对象上的 <xref:System.EventArgs> 属性返回。</span><span class="sxs-lookup"><span data-stu-id="157be-285">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="157be-286">然后，所有内部返回值就都是响应消息对象的属性了。</span><span class="sxs-lookup"><span data-stu-id="157be-286">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="157be-287">请参阅</span><span class="sxs-lookup"><span data-stu-id="157be-287">See also</span></span>

- [<span data-ttu-id="157be-288">使用数据协定</span><span class="sxs-lookup"><span data-stu-id="157be-288">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="157be-289">设计和实现服务</span><span class="sxs-lookup"><span data-stu-id="157be-289">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
