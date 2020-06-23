---
title: 设计服务协定
description: 了解服务约定，包括如何在 WCF 编程中创建服务协定、可用的操作和数据类型以及服务协定的其他方面。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 366157b86ed7c420aed9a3a70838b4d6cd1e451f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245383"
---
# <a name="designing-service-contracts"></a><span data-ttu-id="ef9b1-103">设计服务协定</span><span class="sxs-lookup"><span data-stu-id="ef9b1-103">Designing Service Contracts</span></span>
<span data-ttu-id="ef9b1-104">本主题介绍什么是服务协定、如何定义服务协定、可用的操作（以及基础消息交换的含义）、使用的数据类型以及可帮助您设计能满足方案需求的操作的其他问题。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-104">This topic describes what service contracts are, how they are defined, what operations are available (and the implications for the underlying message exchanges), what data types are used, and other issues that help you design operations that satisfy the requirements of your scenario.</span></span>  
  
## <a name="creating-a-service-contract"></a><span data-ttu-id="ef9b1-105">创建服务协定</span><span class="sxs-lookup"><span data-stu-id="ef9b1-105">Creating a Service Contract</span></span>  
 <span data-ttu-id="ef9b1-106">服务公开一系列操作。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-106">Services expose a number of operations.</span></span> <span data-ttu-id="ef9b1-107">在 Windows Communication Foundation （WCF）应用程序中，通过创建方法并使用特性标记操作来定义操作 <xref:System.ServiceModel.OperationContractAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-107">In Windows Communication Foundation (WCF) applications, define the operations by creating a method and marking it with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> <span data-ttu-id="ef9b1-108">然后，若要创建服务协定，需要将操作组合到一起，具体方法是在使用 <xref:System.ServiceModel.ServiceContractAttribute> 属性标记的接口中声明这些操作，或在使用同一属性进行标记的类中定义它们。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-108">Then, to create a service contract, group together your operations, either by declaring them within an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute, or by defining them in a class marked with the same attribute.</span></span> <span data-ttu-id="ef9b1-109">（有关基本示例，请参阅[如何：定义服务协定](how-to-define-a-wcf-service-contract.md)。）</span><span class="sxs-lookup"><span data-stu-id="ef9b1-109">(For a basic example, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md).)</span></span>  
  
 <span data-ttu-id="ef9b1-110">没有属性的任何方法 <xref:System.ServiceModel.OperationContractAttribute> 都不是服务操作，并且不是由 WCF 服务公开的。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-110">Any methods that do not have a <xref:System.ServiceModel.OperationContractAttribute> attribute are not service operations and are not exposed by WCF services.</span></span>  
  
 <span data-ttu-id="ef9b1-111">本主题介绍设计服务协定时的以下决策要点：</span><span class="sxs-lookup"><span data-stu-id="ef9b1-111">This topic describes the following decision points when designing a service contract:</span></span>  
  
- <span data-ttu-id="ef9b1-112">是否使用类或接口。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-112">Whether to use classes or interfaces.</span></span>  
  
- <span data-ttu-id="ef9b1-113">如何指定要交换的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-113">How to specify the data types you want to exchange.</span></span>  
  
- <span data-ttu-id="ef9b1-114">您可以使用的交换模式类型。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-114">The types of exchange patterns you can use.</span></span>  
  
- <span data-ttu-id="ef9b1-115">是否可以将显式安全要求作为协定的一部分。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-115">Whether you can make explicit security requirements part of the contract.</span></span>  
  
- <span data-ttu-id="ef9b1-116">对操作输入和输出的限制。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-116">The restrictions for operation inputs and outputs.</span></span>  
  
## <a name="classes-or-interfaces"></a><span data-ttu-id="ef9b1-117">类或接口</span><span class="sxs-lookup"><span data-stu-id="ef9b1-117">Classes or Interfaces</span></span>  
 <span data-ttu-id="ef9b1-118">类和接口都表示一组功能，因此，这两个接口都可用于定义 WCF 服务协定。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-118">Both classes and interfaces represent a grouping of functionality and, therefore, both can be used to define a WCF service contract.</span></span> <span data-ttu-id="ef9b1-119">但是，建议您使用接口，因为接口可以直接对服务协定建模。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-119">However, it is recommended that you use interfaces because they directly model service contracts.</span></span> <span data-ttu-id="ef9b1-120">如果不经过实现，接口的作用只是根据特定签名对一组方法进行定义。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-120">Without an implementation, interfaces do no more than define a grouping of methods with certain signatures.</span></span> <span data-ttu-id="ef9b1-121">实现服务协定接口，并已实现 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-121">Implement a service contract interface and you have implemented a WCF service.</span></span>  
  
 <span data-ttu-id="ef9b1-122">服务协定接口具有托管接口的所有优点：</span><span class="sxs-lookup"><span data-stu-id="ef9b1-122">All the benefits of managed interfaces apply to service contract interfaces:</span></span>  
  
- <span data-ttu-id="ef9b1-123">服务协定接口可以扩展任何数量的其他服务协定接口。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-123">Service contract interfaces can extend any number of other service contract interfaces.</span></span>  
  
- <span data-ttu-id="ef9b1-124">一个类可以通过实现服务协定接口来实现任意数量的服务协定。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-124">A single class can implement any number of service contracts by implementing those service contract interfaces.</span></span>  
  
- <span data-ttu-id="ef9b1-125">您可以通过更改接口实现来修改服务协定的实现，而让服务协定保持不变。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-125">You can modify the implementation of a service contract by changing the interface implementation, while the service contract remains the same.</span></span>  
  
- <span data-ttu-id="ef9b1-126">您可以通过实现旧接口和新接口来确定服务的版本。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-126">You can version your service by implementing the old interface and the new one.</span></span> <span data-ttu-id="ef9b1-127">老客户端连接到原始版本，而新客户端则可以连接到较新的版本。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-127">Old clients connect to the original version, while newer clients can connect to the newer version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef9b1-128">从其他服务协定接口中继承时，不能重写操作属性，例如名称或命名空间。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-128">When inheriting from other service contract interfaces, you cannot override operation properties, such as the name or namespace.</span></span> <span data-ttu-id="ef9b1-129">如果试图执行该操作，应在当前服务协定中创建新操作。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-129">If you attempt to do so, you create a new operation in the current service contract.</span></span>  
  
 <span data-ttu-id="ef9b1-130">有关使用接口创建服务协定的示例，请参阅[如何：使用协定接口创建服务](./feature-details/how-to-create-a-service-with-a-contract-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-130">For an example of using an interface to create a service contract, see [How to: Create a Service with a Contract Interface](./feature-details/how-to-create-a-service-with-a-contract-interface.md).</span></span>  
  
 <span data-ttu-id="ef9b1-131">不过，您可以使用类来定义服务协定，并同时实现该协定。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-131">You can, however, use a class to define a service contract and implement that contract at the same time.</span></span> <span data-ttu-id="ef9b1-132">可以通过直接向类和类上的方法分别应用 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 来创建服务，这种方法的优点是快速且简便。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-132">The advantage of creating your services by applying <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> directly to the class and the methods on the class, respectively, is speed and simplicity.</span></span> <span data-ttu-id="ef9b1-133">缺点是托管类不支持多个继承，因此，一次只能实现一个服务协定。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-133">The disadvantages are that managed classes do not support multiple inheritance, and as a result they can only implement one service contract at a time.</span></span> <span data-ttu-id="ef9b1-134">此外，对类或方法签名的任何修改都将修改该服务的公开协定，这可以防止未进行修改的客户端使用您的服务。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-134">In addition, any modification to the class or method signatures modifies the public contract for that service, which can prevent unmodified clients from using your service.</span></span> <span data-ttu-id="ef9b1-135">有关详细信息，请参阅[实现服务协定](implementing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-135">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
 <span data-ttu-id="ef9b1-136">有关使用类创建服务协定并同时实现该协定的示例，请参阅[如何：创建具有协定类的服务](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-136">For an example that uses a class to create a service contract and implements it at the same time, see [How to: Create a Service with a Contract Class](./feature-details/how-to-create-a-wcf-contract-with-a-class.md).</span></span>  
  
 <span data-ttu-id="ef9b1-137">此时，您应了解使用接口定义服务协定与使用类定义服务协定之间的区别。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-137">At this point, you should understand the difference between defining your service contract by using an interface and by using a class.</span></span> <span data-ttu-id="ef9b1-138">下一步将确定可在服务及其客户端之间往返传递的数据。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-138">The next step is deciding what data can be passed back and forth between a service and its clients.</span></span>  
  
## <a name="parameters-and-return-values"></a><span data-ttu-id="ef9b1-139">参数和返回值</span><span class="sxs-lookup"><span data-stu-id="ef9b1-139">Parameters and Return Values</span></span>  
 <span data-ttu-id="ef9b1-140">每个操作都有一个返回值和一个参数，即使它们为 `void`。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-140">Each operation has a return value and a parameter, even if these are `void`.</span></span> <span data-ttu-id="ef9b1-141">您可以使用局部方法将对对象的引用从一个对象传递到另一个对象，但与局部方法不同的是，服务操作不会传递对对象的引用，</span><span class="sxs-lookup"><span data-stu-id="ef9b1-141">However, unlike a local method, in which you can pass references to objects from one object to another, service operations do not pass references to objects.</span></span> <span data-ttu-id="ef9b1-142">它们传递的只是对象的副本。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-142">Instead, they pass copies of the objects.</span></span>  
  
 <span data-ttu-id="ef9b1-143">这一点很重要，这是因为参数或返回值中使用的每个类型都必须是可序列化的，换言之，该类型的对象必须能够转换为字节流，并能够从字节流转换为对象。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-143">This is significant because each type used in a parameter or return value must be serializable; that is, it must be possible to convert an object of that type into a stream of bytes and from a stream of bytes into an object.</span></span>  
  
 <span data-ttu-id="ef9b1-144">默认情况下，基元类型是可序列化的，.NET Framework 中的很多类型都是可序列化的。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-144">Primitive types are serializable by default, as are many types in the .NET Framework.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef9b1-145">操作签名中的参数名称值是协定的一部分且区分大小写。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-145">The value of the parameter names in the operation signature are part of the contract and are case sensitive.</span></span> <span data-ttu-id="ef9b1-146">如果要在本地使用相同的参数名称，但是要在已发布的元数据中修改名称，请参见 <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-146">If you want to use the same parameter name locally but modify the name in the published metadata, see the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.</span></span>  
  
#### <a name="data-contracts"></a><span data-ttu-id="ef9b1-147">数据协定</span><span class="sxs-lookup"><span data-stu-id="ef9b1-147">Data Contracts</span></span>  
 <span data-ttu-id="ef9b1-148">面向服务的应用程序（例如 Windows Communication Foundation （WCF）应用程序）旨在与 Microsoft 和非 Microsoft 平台上的尽可能多的客户端应用程序进行互操作。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-148">Service-oriented applications like Windows Communication Foundation (WCF) applications are designed to interoperate with the widest possible number of client applications on both Microsoft and non-Microsoft platforms.</span></span> <span data-ttu-id="ef9b1-149">为了获得最大可能的互操作性，建议您使用 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性对您的类型进行标记，以创建数据协定。数据协定是服务协定的一部分，用于描述您的服务操作交换的数据。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-149">For the widest possible interoperability, it is recommended that you mark your types with the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to create a data contract, which is the portion of the service contract that describes the data that your service operations exchange.</span></span>  
  
 <span data-ttu-id="ef9b1-150">数据协定是可选的样式协定：除非您显式应用数据协定属性，否则不会序列化任何类型或数据成员。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-150">Data contracts are opt-in style contracts: No type or data member is serialized unless you explicitly apply the data contract attribute.</span></span> <span data-ttu-id="ef9b1-151">数据协定与托管代码的访问范围无关：可以对私有数据成员进行序列化，并将其发送到其他位置，以便可以公开访问它们。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-151">Data contracts are unrelated to the access scope of the managed code: Private data members can be serialized and sent elsewhere to be accessed publicly.</span></span> <span data-ttu-id="ef9b1-152">（有关数据协定的基本示例，请参阅[如何：为类或结构创建基本数据协定](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)。）WCF 处理基础 SOAP 消息的定义，这些消息可实现操作的功能，以及将数据类型序列化到消息的正文中。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-152">(For a basic example of a data contract, see [How to: Create a Basic Data Contract for a Class or Structure](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF handles the definition of the underlying SOAP messages that enable the operation's functionality as well as the serialization of your data types into and out of the body of the messages.</span></span> <span data-ttu-id="ef9b1-153">只要数据类型可序列化，您就无需在设计操作时考虑基础消息交换基础结构。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-153">As long as your data types are serializable, you do not need to think about the underlying message exchange infrastructure when designing your operations.</span></span>  
  
 <span data-ttu-id="ef9b1-154">尽管典型的 WCF 应用程序使用 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性为操作创建数据协定，但你可以使用其他序列化机制。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-154">Although the typical WCF application uses the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to create data contracts for operations, you can use other serialization mechanisms.</span></span> <span data-ttu-id="ef9b1-155">标准 <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.IXmlSerializable> 机制都可用于处理数据类型到基础 SOAP 消息的序列化，这些消息可将数据类型从一个应用程序带到另一个应用程序。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-155">The standard <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> and <xref:System.Xml.Serialization.IXmlSerializable> mechanisms all work to handle the serialization of your data types into the underlying SOAP messages that carry them from one application to another.</span></span> <span data-ttu-id="ef9b1-156">如果您的数据类型需要特别支持，您可以采用多个序列化策略。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-156">You can employ more serialization strategies if your data types require special support.</span></span> <span data-ttu-id="ef9b1-157">有关在 WCF 应用程序中序列化数据类型的选项的详细信息，请参阅[在服务协定中指定数据传输](./feature-details/specifying-data-transfer-in-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-157">For more information about the choices for serialization of data types in WCF applications, see [Specifying Data Transfer in Service Contracts](./feature-details/specifying-data-transfer-in-service-contracts.md).</span></span>  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a><span data-ttu-id="ef9b1-158">将参数和返回值映射到消息交换</span><span class="sxs-lookup"><span data-stu-id="ef9b1-158">Mapping Parameters and Return Values to Message Exchanges</span></span>  
 <span data-ttu-id="ef9b1-159">除了应用程序支持特定标准安全、事务和与会话相关的功能时所需的数据之外，对应用程序数据进行往返传输的 SOAP 消息的基础交换还支持服务操作。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-159">Service operations are supported by an underlying exchange of SOAP messages that transfer application data back and forth, in addition to the data required by the application to support certain standard security, transaction, and session-related features.</span></span> <span data-ttu-id="ef9b1-160">因为在这种情况下，服务操作的签名会指示特定的基础*消息交换模式*（MEP），该模式可以支持数据传输和操作所需的功能。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-160">Because this is the case, the signature of a service operation dictates a certain underlying *message exchange pattern* (MEP) that can support the data transfer and the features an operation requires.</span></span> <span data-ttu-id="ef9b1-161">可以在 WCF 编程模型中指定三种模式：请求/答复、单向和双工消息模式。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-161">You can specify three patterns in the WCF programming model: request/reply, one-way, and duplex message patterns.</span></span>  
  
##### <a name="requestreply"></a><span data-ttu-id="ef9b1-162">请求/答复</span><span class="sxs-lookup"><span data-stu-id="ef9b1-162">Request/Reply</span></span>  
 <span data-ttu-id="ef9b1-163">通过请求/答复模式，请求发送方（客户端应用程序）将接收与请求相关的答复。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-163">A request/reply pattern is one in which a request sender (a client application) receives a reply with which the request is correlated.</span></span> <span data-ttu-id="ef9b1-164">这是默认的 MEP，因为它既支持传入操作（一个或多个参数传递到该操作中），也支持将返回值传回给调用方。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-164">This is the default MEP because it supports an operation in which one or more parameters are passed to the operation and a return value is passed back to the caller.</span></span> <span data-ttu-id="ef9b1-165">例如，下面的 C# 代码示例演示一个基本的服务操作，即先接收一个字符串，再返回一个字符串。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-165">For example, the following C# code example shows a basic service operation that takes one string and returns a string.</span></span>  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 <span data-ttu-id="ef9b1-166">下面是等效的 Visual Basic 代码。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-166">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 <span data-ttu-id="ef9b1-167">此操作签名指示基础消息交换的形式。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-167">This operation signature dictates the form of underlying message exchange.</span></span> <span data-ttu-id="ef9b1-168">如果没有相关关系，WCF 将无法确定返回值所需的操作。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-168">If no correlation existed, WCF cannot determine for which operation the return value is intended.</span></span>  
  
 <span data-ttu-id="ef9b1-169">请注意，除非指定了其他基础消息模式，否则，即使在 Visual Basic 中返回的服务操作 `void` `Nothing` 也是请求/答复消息交换。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-169">Note that unless you specify a different underlying message pattern, even service operations that return `void` (`Nothing` in Visual Basic) are request/reply message exchanges.</span></span> <span data-ttu-id="ef9b1-170">您操作的结果是：除非客户端异步调用操作，否则客户端将停止处理，直到收到返回消息，即使该消息正常情况下为空时也是如此。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-170">The result for your operation is that unless a client invokes the operation asynchronously, the client stops processing until the return message is received, even though that message is empty in the normal case.</span></span> <span data-ttu-id="ef9b1-171">下面的 C# 代码示例演示的操作在客户端收到空的响应消息后才返回值。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-171">The following C# code example shows an operation that does not return until the client has received an empty message in response.</span></span>  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 <span data-ttu-id="ef9b1-172">下面是等效的 Visual Basic 代码。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-172">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 <span data-ttu-id="ef9b1-173">如果执行操作需要很长的时间，则上面的示例会降低客户端性能和响应能力，但是，即使在请求/答复操作返回 `void` 时，这种操作仍有优势。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-173">The preceding example can slow client performance and responsiveness if the operation takes a long time to perform, but there are advantages to request/reply operations even when they return `void`.</span></span> <span data-ttu-id="ef9b1-174">最明显的优势在于，响应消息中可返回 SOAP 错误，这表明可能在通信或处理中发生了一些与服务有关的错误状况。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-174">The most obvious one is that SOAP faults can be returned in the response message, which indicates that some service-related error condition has occurred, whether in communication or processing.</span></span> <span data-ttu-id="ef9b1-175">在服务协定中指定的 SOAP 错误将作为 <xref:System.ServiceModel.FaultException%601> 对象传递到客户端应用程序，其中类型参数是在服务协定中指定的类型。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-175">SOAP faults that are specified in a service contract are passed to the client application as a <xref:System.ServiceModel.FaultException%601> object, where the type parameter is the type specified in the service contract.</span></span> <span data-ttu-id="ef9b1-176">这样就可以轻松地在 WCF 服务中向客户端通知错误情况。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-176">This makes notifying clients about error conditions in WCF services easy.</span></span> <span data-ttu-id="ef9b1-177">有关异常、SOAP 错误和错误处理的详细信息，请参阅[在协定和服务中指定和处理错误](specifying-and-handling-faults-in-contracts-and-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-177">For more information about exceptions, SOAP faults, and error handling, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span> <span data-ttu-id="ef9b1-178">若要查看请求/答复服务和客户端的示例，请参阅[如何：创建请求-答复协定](./feature-details/how-to-create-a-request-reply-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-178">To see an example of a request/reply service and client, see [How to: Create a Request-Reply Contract](./feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="ef9b1-179">有关请求-答复模式问题的详细信息，请参阅[请求-答复服务](./feature-details/request-reply-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-179">For more information about issues with the request-reply pattern, see [Request-Reply Services](./feature-details/request-reply-services.md).</span></span>  
  
##### <a name="one-way"></a><span data-ttu-id="ef9b1-180">单向</span><span class="sxs-lookup"><span data-stu-id="ef9b1-180">One-way</span></span>  
 <span data-ttu-id="ef9b1-181">如果 WCF 服务应用程序的客户端不应等待操作完成并且不处理 SOAP 错误，则操作可以指定单向消息模式。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-181">If the client of a WCF service application should not wait for the operation to complete and does not process SOAP faults, the operation can specify a one-way message pattern.</span></span> <span data-ttu-id="ef9b1-182">单向操作是：客户端在其中调用操作并在 WCF 将消息写入网络后继续处理。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-182">A one-way operation is one in which a client invokes an operation and continues processing after WCF writes the message to the network.</span></span> <span data-ttu-id="ef9b1-183">通常这意味着，除非在出站消息中发送的数据极其庞大，否则客户端几乎立即继续运行（除非发送数据时出错）。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-183">Typically this means that unless the data being sent in the outbound message is extremely large the client continues running almost immediately (unless there is an error sending the data).</span></span> <span data-ttu-id="ef9b1-184">此种类型的消息交换模式支持从客户端到服务应用程序的类似于事件的行为。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-184">This type of message exchange pattern supports event-like behavior from a client to a service application.</span></span>  
  
 <span data-ttu-id="ef9b1-185">发送一条消息而未接收任何消息的消息交换无法支持指定非 `void` 的返回值的服务操作；在这种情况下，将引发一个 <xref:System.InvalidOperationException> 异常。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-185">A message exchange in which one message is sent and none are received cannot support a service operation that specifies a return value other than `void`; in this case an <xref:System.InvalidOperationException> exception is thrown.</span></span>  
  
 <span data-ttu-id="ef9b1-186">没有返回消息还意味着可能没有返回表明处理或通信中任何错误的 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-186">No return message also means that there can be no SOAP fault returned to indicate any errors in processing or communication.</span></span> <span data-ttu-id="ef9b1-187">（操作是单向操作而要求双工消息交换模式时，会产生通信错误信息。）</span><span class="sxs-lookup"><span data-stu-id="ef9b1-187">(Communicating error information when operations are one-way operations requires a duplex message exchange pattern.)</span></span>  
  
 <span data-ttu-id="ef9b1-188">若要为返回 `void` 的操作指定单向消息交换，请将 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 属性设置为 `true`，如下面的 C# 代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-188">To specify a one-way message exchange for an operation that returns `void`, set the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`, as in the following C# code example.</span></span>  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 <span data-ttu-id="ef9b1-189">下面是等效的 Visual Basic 代码。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-189">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 <span data-ttu-id="ef9b1-190">此方法与前面的请求/答复示例相同，但是，将 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 属性设置为 `true` 意味着尽管方法相同，服务操作也不会发送返回消息，而客户端将在出站消息抵达通道层时立即返回。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-190">This method is identical to the preceding request/reply example, but setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` means that although the method is identical, the service operation does not send a return message and clients return immediately once the outbound message has been handed to the channel layer.</span></span> <span data-ttu-id="ef9b1-191">有关示例，请参阅[如何：创建单向协定](./feature-details/how-to-create-a-one-way-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-191">For an example, see [How to: Create a One-Way Contract](./feature-details/how-to-create-a-one-way-contract.md).</span></span> <span data-ttu-id="ef9b1-192">有关单向模式的详细信息，请参阅单向[服务](./feature-details/one-way-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-192">For more information about the one-way pattern, see [One-Way Services](./feature-details/one-way-services.md).</span></span>  
  
##### <a name="duplex"></a><span data-ttu-id="ef9b1-193">双工</span><span class="sxs-lookup"><span data-stu-id="ef9b1-193">Duplex</span></span>  
 <span data-ttu-id="ef9b1-194">双工模式的特点是，无论使用单向消息发送还是请求/答复消息发送方式，服务和客户端均能够独立地向对方发送消息。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-194">A duplex pattern is characterized by the ability of both the service and the client to send messages to each other independently whether using one-way or request/reply messaging.</span></span> <span data-ttu-id="ef9b1-195">对于必须直接与客户端通信或向消息交换的任意一方提供异步体验（包括类似于事件的行为）的服务来说，这种双向通信形式非常有用。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-195">This form of two-way communication is useful for services that must communicate directly to the client or for providing an asynchronous experience to either side of a message exchange, including event-like behavior.</span></span>  
  
 <span data-ttu-id="ef9b1-196">由于存在与客户端通信的附加机制，双向模式比请求/答复或单向模式要略为复杂。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-196">The duplex pattern is slightly more complex than the request/reply or one-way patterns because of the additional mechanism for communicating with the client.</span></span>  
  
 <span data-ttu-id="ef9b1-197">若要设计双工协定，还必须设计回调协定，并将该回调协定的类型分配给标记服务协定的 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> 属性 (Attribute) 的 <xref:System.ServiceModel.ServiceContractAttribute> 属性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-197">To design a duplex contract, you must also design a callback contract and assign the type of that callback contract to the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property of the <xref:System.ServiceModel.ServiceContractAttribute> attribute that marks your service contract.</span></span>  
  
 <span data-ttu-id="ef9b1-198">若要实现双工模式，您必须创建第二个接口，该接口包含在客户端调用的方法声明。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-198">To implement a duplex pattern, you must create a second interface that contains the method declarations that are called on the client.</span></span>  
  
 <span data-ttu-id="ef9b1-199">有关创建服务和访问该服务的客户端的示例，请参阅[如何：创建双工协定](./feature-details/how-to-create-a-duplex-contract.md)和[如何：使用双工协定访问服务](./feature-details/how-to-access-services-with-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-199">For an example of creating a service, and a client that accesses that service, see [How to: Create a Duplex Contract](./feature-details/how-to-create-a-duplex-contract.md) and [How to: Access Services with a Duplex Contract](./feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="ef9b1-200">有关工作示例，请参阅[双工](./samples/duplex.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-200">For a working sample, see [Duplex](./samples/duplex.md).</span></span> <span data-ttu-id="ef9b1-201">有关使用双工协定的问题的详细信息，请参阅[双工服务](./feature-details/duplex-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-201">For more information about issues using duplex contracts, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="ef9b1-202">当服务接收双工消息时，它会在该传入消息中查找 `ReplyTo` 元素，以确定要发送答复的位置。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-202">When a service receives a duplex message, it looks at the `ReplyTo` element in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="ef9b1-203">如果用于接收消息的通道不安全，则不受信任的客户端可能使用目标计算机的 `ReplyTo` 发送恶意消息，从而导致该目标计算机发生拒绝服务 (DOS)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-203">If the channel that is used to receive the message is not secured, then an untrusted client could send a malicious message with a target machine's `ReplyTo`, leading to a denial of service (DOS) of that target machine.</span></span>  
  
##### <a name="out-and-ref-parameters"></a><span data-ttu-id="ef9b1-204">Out 和 Ref 参数</span><span class="sxs-lookup"><span data-stu-id="ef9b1-204">Out and Ref Parameters</span></span>  
 <span data-ttu-id="ef9b1-205">在大多数情况下，可以使用 `in` 参数（ `ByVal` 在 Visual Basic 中） `out` 和 `ref` 参数（ `ByRef` 在 Visual Basic 中）。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-205">In most cases, you can use `in` parameters (`ByVal` in Visual Basic) and `out` and `ref` parameters (`ByRef` in Visual Basic).</span></span> <span data-ttu-id="ef9b1-206">由于 `out` 和 `ref` 参数都指示数据是从操作返回的，类似如下的操作签名会指定需要请求/答复操作，即使操作签名返回 `void` 也是如此。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-206">Because both `out` and `ref` parameters indicate that data is returned from an operation, an operation signature such as the following specifies that a request/reply operation is required even though the operation signature returns `void`.</span></span>  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 <span data-ttu-id="ef9b1-207">下面是等效的 Visual Basic 代码。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-207">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 <span data-ttu-id="ef9b1-208">唯一的例外是当您的签名具有特定结构时。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-208">The only exceptions are those cases in which your signature has a particular structure.</span></span> <span data-ttu-id="ef9b1-209">例如，只有当用于声明操作的方法返回 <xref:System.ServiceModel.NetMsmqBinding> 时，才能使用 `void` 绑定与客户端通信；不能有任何输出值，无论它是返回值、`ref`，还是 `out` 参数。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-209">For example, you can use the <xref:System.ServiceModel.NetMsmqBinding> binding to communicate with clients only if the method used to declare an operation returns `void`; there can be no output value, whether it is a return value, `ref`, or `out` parameter.</span></span>  
  
 <span data-ttu-id="ef9b1-210">此外，使用 `out` 或 `ref` 参数要求操作具有基础响应消息，才可以将已修改的对象传回。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-210">In addition, using `out` or `ref` parameters requires that the operation have an underlying response message to carry back the modified object.</span></span> <span data-ttu-id="ef9b1-211">如果操作是单向操作，则将在运行时引发 <xref:System.InvalidOperationException> 异常。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-211">If your operation is a one-way operation, an <xref:System.InvalidOperationException> exception is thrown at runtime.</span></span>  
  
### <a name="specify-message-protection-level-on-the-contract"></a><span data-ttu-id="ef9b1-212">指定协定上的消息保护级别</span><span class="sxs-lookup"><span data-stu-id="ef9b1-212">Specify Message Protection Level on the Contract</span></span>  
 <span data-ttu-id="ef9b1-213">设计协定时，还必须确定实现您的协定的服务的消息保护级别。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-213">When designing your contract, you must also decide the message protection level of services that implement your contract.</span></span> <span data-ttu-id="ef9b1-214">仅当消息安全应用于协定终结点中的绑定时，才有必要这么做。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-214">This is necessary only if message security is applied to the binding in the contract's endpoint.</span></span> <span data-ttu-id="ef9b1-215">如果绑定将安全关闭（也就是说，如果系统提供的绑定将 <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> 设置为值 <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>），则不必确定协定的消息保护级别。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-215">If the binding has security turned off (that is, if the system-provided binding sets the <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> to the value <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>) then you do not have to decide on the message protection level for the contract.</span></span> <span data-ttu-id="ef9b1-216">大部分情况下，系统提供的绑定应用的是消息级别的安全，可提供充分的保护级别，你不必考虑每个操作或每条消息的保护级别。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-216">In most cases, system-provided bindings with message-level security applied provide a sufficient protection level and you do not have to consider the protection level for each operation or for each message.</span></span>  
  
 <span data-ttu-id="ef9b1-217">保护级别是一个值，它指定了支持服务的消息（或消息部分）是进行签名、签名并加密，还是未经签名或加密即发送。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-217">The protection level is a value that specifies whether the messages (or message parts) that support a service are signed, signed and encrypted, or sent without signatures or encryption.</span></span> <span data-ttu-id="ef9b1-218">可以在以下多个范围设置保护级别：服务级别、针对特定操作、针对该操作内的消息或消息部分。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-218">The protection level can be set at various scopes: At the service level, for a particular operation, for a message within that operation, or a message part.</span></span> <span data-ttu-id="ef9b1-219">在一个范围设置的值会成为比该范围小的范围的默认值（除非显式重写该值）。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-219">Values set at one scope become the default value for smaller scopes unless explicitly overridden.</span></span> <span data-ttu-id="ef9b1-220">如果绑定配置无法提供协定中要求的最小保护级别，则将引发异常。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-220">If a binding configuration cannot provide the required minimum protection level for the contract, an exception is thrown.</span></span> <span data-ttu-id="ef9b1-221">如果未在协定上显式设置保护级别值，并且绑定具有消息安全，则绑定配置将控制所有消息的保护级别。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-221">And when no protection level values are explicitly set on the contract, the binding configuration controls the protection level for all messages if the binding has message security.</span></span> <span data-ttu-id="ef9b1-222">这是默认行为。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-222">This is the default behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ef9b1-223">确定是否将协定的各种范围显式设置为小于 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> 的完全保护级别的过程，通常就是牺牲部分程度的安全性来换取改善性能的过程。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-223">Deciding whether to explicitly set various scopes of a contract to less than the full protection level of <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> is generally a decision that trades some degree of security for increased performance.</span></span> <span data-ttu-id="ef9b1-224">在这种情况下，您的决策必须围绕您的操作以及它们所交换的数据值进行。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-224">In these cases, your decisions must revolve around your operations and the value of the data they exchange.</span></span> <span data-ttu-id="ef9b1-225">有关详细信息，请参阅[保护服务](securing-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-225">For more information, see [Securing Services](securing-services.md).</span></span>  
  
 <span data-ttu-id="ef9b1-226">例如，下面的代码示例不会设置协定的 <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> 或 <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-226">For example, the following code example does not set either the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> or the <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> property on the contract.</span></span>  
  
```csharp  
[ServiceContract]  
public interface ISampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute]  
  public int GetInt();
}  
```  
  
 <span data-ttu-id="ef9b1-227">下面是等效的 Visual Basic 代码。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-227">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 <span data-ttu-id="ef9b1-228">当使用默认的 `ISampleService`（其默认的 <xref:System.ServiceModel.WSHttpBinding> 是 <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>）在终结点中与 <xref:System.ServiceModel.SecurityMode.Message> 实现交互时，将对所有消息加密并签名，因为这是默认的保护级别。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-228">When interacting with an `ISampleService` implementation in an endpoint with a default <xref:System.ServiceModel.WSHttpBinding> (the default <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, which is <xref:System.ServiceModel.SecurityMode.Message>), all messages are encrypted and signed because this is the default protection level.</span></span> <span data-ttu-id="ef9b1-229">但是，当 `ISampleService` 服务与默认 <xref:System.ServiceModel.BasicHttpBinding>（其默认的 <xref:System.ServiceModel.SecurityMode> 是 <xref:System.ServiceModel.SecurityMode.None>）一起使用时，所有消息都将以文本的形式发送，这是因为此绑定没有安全性，因此将忽略保护级别（也就是说，不会对消息加密和签名）。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-229">However, when an `ISampleService` service is used with a default <xref:System.ServiceModel.BasicHttpBinding> (the default <xref:System.ServiceModel.SecurityMode>, which is <xref:System.ServiceModel.SecurityMode.None>), all messages are sent as text because there is no security for this binding and so the protection level is ignored (that is, the messages are neither encrypted nor signed).</span></span> <span data-ttu-id="ef9b1-230">如果 <xref:System.ServiceModel.SecurityMode> 更改为 <xref:System.ServiceModel.SecurityMode.Message>，则将对这些消息加密并签名（因为它现在将成为绑定的默认保护级别）。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-230">If the <xref:System.ServiceModel.SecurityMode> was changed to <xref:System.ServiceModel.SecurityMode.Message>, then these messages would be encrypted and signed (because that would now be the binding's default protection level).</span></span>  
  
 <span data-ttu-id="ef9b1-231">如果要显式指定或调整协定的保护要求，请将 <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> 属性（或较小范围的任意 `ProtectionLevel` 属性）设置为您的服务协定所要求的级别。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-231">If you want to explicitly specify or adjust the protection requirements for your contract, set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property (or any of the `ProtectionLevel` properties at a smaller scope) to the level your service contract requires.</span></span> <span data-ttu-id="ef9b1-232">在这种情况下，使用显式设置要求绑定在所用的最小范围内支持该设置。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-232">In this case, using an explicit setting requires the binding to support that setting at a minimum for the scope used.</span></span> <span data-ttu-id="ef9b1-233">例如，下面的代码示例为 <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> 操作显式指定一个 `GetGuid` 值。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-233">For example, the following code example specifies one <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> value explicitly, for the `GetGuid` operation.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IExplicitProtectionLevelSampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.None)]  
  public int GetInt();
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
  public int GetGuid();
}  
```  
  
 <span data-ttu-id="ef9b1-234">下面是等效的 Visual Basic 代码。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-234">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContract()> _
Public Interface IExplicitProtectionLevelSampleService
    <OperationContract()> _
    Public Function GetString() As String
    End Function
  
    <OperationContract(ProtectionLevel := ProtectionLevel.None)> _
    Public Function GetInt() As Integer
    End Function
  
    <OperationContractAttribute(ProtectionLevel := ProtectionLevel.EncryptAndSign)> _
    Public Function GetGuid() As Integer
    End Function
  
End Interface  
```  
  
 <span data-ttu-id="ef9b1-235">实现此 `IExplicitProtectionLevelSampleService` 协定并且具有使用默认 <xref:System.ServiceModel.WSHttpBinding>（其默认的 <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> 是 <xref:System.ServiceModel.SecurityMode.Message>）的终结点的服务具有以下行为：</span><span class="sxs-lookup"><span data-stu-id="ef9b1-235">A service that implements this `IExplicitProtectionLevelSampleService` contract and has an endpoint that uses the default <xref:System.ServiceModel.WSHttpBinding> (the default <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, which is <xref:System.ServiceModel.SecurityMode.Message>) has the following behavior:</span></span>  
  
- <span data-ttu-id="ef9b1-236">对 `GetString` 操作消息加密并签名。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-236">The `GetString` operation messages are encrypted and signed.</span></span>  
  
- <span data-ttu-id="ef9b1-237">`GetInt` 操作消息以未加密且未签名文本（即纯文本）的形式发送。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-237">The `GetInt` operation messages are sent as unencrypted and unsigned (that is, plain) text.</span></span>  
  
- <span data-ttu-id="ef9b1-238">`GetGuid` 操作 <xref:System.Guid?displayProperty=nameWithType> 将在一条已加密且签名的消息中返回。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-238">The `GetGuid` operation <xref:System.Guid?displayProperty=nameWithType> is returned in a message that is encrypted and signed.</span></span>  
  
 <span data-ttu-id="ef9b1-239">有关保护级别以及如何使用它们的详细信息，请参阅[了解保护级别](understanding-protection-level.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-239">For more information about protection levels and how to use them, see [Understanding Protection Level](understanding-protection-level.md).</span></span> <span data-ttu-id="ef9b1-240">有关安全性的详细信息，请参阅[保护服务](securing-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-240">For more information about security, see [Securing Services](securing-services.md).</span></span>  
  
##### <a name="other-operation-signature-requirements"></a><span data-ttu-id="ef9b1-241">其他操作签名要求</span><span class="sxs-lookup"><span data-stu-id="ef9b1-241">Other Operation Signature Requirements</span></span>  
 <span data-ttu-id="ef9b1-242">某些应用程序功能要求特定种类的操作签名。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-242">Some application features require a particular kind of operation signature.</span></span> <span data-ttu-id="ef9b1-243">例如，<xref:System.ServiceModel.NetMsmqBinding> 绑定支持持久性服务和客户端，即应用程序可以在通信期间重新启动，并在其停止的位置处拾取，不会遗漏任何消息。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-243">For example, the <xref:System.ServiceModel.NetMsmqBinding> binding supports durable services and clients, in which an application can restart in the middle of communication and pick up where it left off without missing any messages.</span></span> <span data-ttu-id="ef9b1-244">（有关详细信息，请参阅[WCF 中的队列](./feature-details/queues-in-wcf.md)。）但是，持久性操作只能接受一个 `in` 参数，并且没有返回值。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-244">(For more information, see [Queues in WCF](./feature-details/queues-in-wcf.md).) However, durable operations must take only one `in` parameter and have no return value.</span></span>  
  
 <span data-ttu-id="ef9b1-245">另一个示例是在操作中使用 <xref:System.IO.Stream> 类型。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-245">Another example is the use of <xref:System.IO.Stream> types in operations.</span></span> <span data-ttu-id="ef9b1-246">由于 <xref:System.IO.Stream> 参数包括整个消息正文，如果输入或输出（也就是 `ref` 参数、`out` 参数或返回值）的类型为 <xref:System.IO.Stream>，则它必须是在操作中指定的唯一输入或输出。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-246">Because the <xref:System.IO.Stream> parameter includes the entire message body, if an input or an output (that is, `ref` parameter, `out` parameter, or return value) is of type <xref:System.IO.Stream>, then it must be the only input or output specified in your operation.</span></span> <span data-ttu-id="ef9b1-247">此外，参数或返回类型必须是 <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> 或 <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-247">In addition, the parameter or return type must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, or <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ef9b1-248">有关流的详细信息，请参阅[大数据和流式处理](./feature-details/large-data-and-streaming.md)。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-248">For more information about streams, see [Large Data and Streaming](./feature-details/large-data-and-streaming.md).</span></span>  
  
##### <a name="names-namespaces-and-obfuscation"></a><span data-ttu-id="ef9b1-249">名称、命名空间和模糊处理</span><span class="sxs-lookup"><span data-stu-id="ef9b1-249">Names, Namespaces, and Obfuscation</span></span>  
 <span data-ttu-id="ef9b1-250">在将协定转换为 WSDL 以及创建和发送协定消息时，协定与操作的定义中的 .NET 类型的名称和命名空间意义重大。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-250">The names and namespaces of the .NET types in the definition of contracts and operations are significant when contracts are converted into WSDL and when contract messages are created and sent.</span></span> <span data-ttu-id="ef9b1-251">因此，强烈建议使用所有支持协定属性 (Attribute)（如 `Name`、`Namespace`、<xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.OperationContractAttribute> 和其他协定属性 (Attribute)）的 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性 (Property) 显式设置服务协定名称和命名空间。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-251">Therefore, it is strongly recommended that service contract names and namespaces are explicitly set using the `Name` and `Namespace` properties of all supporting contract attributes such as the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>, and other contract attributes.</span></span>  
  
 <span data-ttu-id="ef9b1-252">这样做的一个原因在于，如果未显式设置名称和命名空间，则在程序集上使用 IL 混淆处理时会改变协定类型名称和命名空间，并产生已修改的 WSDL 以及通常会失败的网络交换。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-252">One result of this is that if the names and namespaces are not explicitly set, the use of IL obfuscation on the assembly alters the contract type names and namespaces and results in modified WSDL and wire exchanges that typically fail.</span></span> <span data-ttu-id="ef9b1-253">如果未显式设置协定名称和命名空间，但确实想使用混淆处理，请使用 <xref:System.Reflection.ObfuscationAttribute> 和 <xref:System.Reflection.ObfuscateAssemblyAttribute> 属性，以防止修改协定类型名称和命名空间。</span><span class="sxs-lookup"><span data-stu-id="ef9b1-253">If you do not set the contract names and namespaces explicitly but do intend to use obfuscation, use the <xref:System.Reflection.ObfuscationAttribute> and <xref:System.Reflection.ObfuscateAssemblyAttribute> attributes to prevent the modification of the contract type names and namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef9b1-254">请参阅</span><span class="sxs-lookup"><span data-stu-id="ef9b1-254">See also</span></span>

- [<span data-ttu-id="ef9b1-255">如何：创建请求-答复协定</span><span class="sxs-lookup"><span data-stu-id="ef9b1-255">How to: Create a Request-Reply Contract</span></span>](./feature-details/how-to-create-a-request-reply-contract.md)
- [<span data-ttu-id="ef9b1-256">如何：创建单向协定</span><span class="sxs-lookup"><span data-stu-id="ef9b1-256">How to: Create a One-Way Contract</span></span>](./feature-details/how-to-create-a-one-way-contract.md)
- [<span data-ttu-id="ef9b1-257">如何：创建双工协定</span><span class="sxs-lookup"><span data-stu-id="ef9b1-257">How to: Create a Duplex Contract</span></span>](./feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="ef9b1-258">在服务协定中指定数据传输</span><span class="sxs-lookup"><span data-stu-id="ef9b1-258">Specifying Data Transfer in Service Contracts</span></span>](./feature-details/specifying-data-transfer-in-service-contracts.md)
- [<span data-ttu-id="ef9b1-259">在协定和服务中指定和处理错误</span><span class="sxs-lookup"><span data-stu-id="ef9b1-259">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
- [<span data-ttu-id="ef9b1-260">使用会话</span><span class="sxs-lookup"><span data-stu-id="ef9b1-260">Using Sessions</span></span>](using-sessions.md)
- [<span data-ttu-id="ef9b1-261">同步和异步操作</span><span class="sxs-lookup"><span data-stu-id="ef9b1-261">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
- [<span data-ttu-id="ef9b1-262">Reliable Services</span><span class="sxs-lookup"><span data-stu-id="ef9b1-262">Reliable Services</span></span>](reliable-services.md)
- [<span data-ttu-id="ef9b1-263">服务和事务</span><span class="sxs-lookup"><span data-stu-id="ef9b1-263">Services and Transactions</span></span>](services-and-transactions.md)
