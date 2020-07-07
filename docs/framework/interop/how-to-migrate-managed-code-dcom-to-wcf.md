---
title: 如何：将托管代码 DCOM 迁移到 WCF
description: 将服务器和客户端之间的分布式组件对象模型 (DCOM) 托管代码调用迁移到 Windows Communication Foundation (WCF)。
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
ms.openlocfilehash: cc6ac1dd01e17bb184d1f1faca372134d6130d33
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619086"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="11630-103">如何：将托管代码 DCOM 迁移到 WCF</span><span class="sxs-lookup"><span data-stu-id="11630-103">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="11630-104">Windows Communication Foundation (WCF) 是针对分布式组件对象模型 (DCOM) 建议的安全选择，可用于处理分布式环境中服务器和客户端间的托管代码调用。</span><span class="sxs-lookup"><span data-stu-id="11630-104">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="11630-105">本文介绍在以下情景中，如何将代码从 DCOM 迁移到 WCF。</span><span class="sxs-lookup"><span data-stu-id="11630-105">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="11630-106">远程服务将对象按值返回到客户端</span><span class="sxs-lookup"><span data-stu-id="11630-106">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="11630-107">客户端将对象按值返回到远程服务</span><span class="sxs-lookup"><span data-stu-id="11630-107">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="11630-108">远程服务将对象按引用返回到客户端</span><span class="sxs-lookup"><span data-stu-id="11630-108">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="11630-109">出于安全原因，WCF 中不允许将对象按引用从客户端发送到服务。</span><span class="sxs-lookup"><span data-stu-id="11630-109">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="11630-110">在 WCF 中使用双工服务可实现需要在客户端和服务器间来回会话的方案。</span><span class="sxs-lookup"><span data-stu-id="11630-110">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="11630-111">有关双工服务的详细信息，请参阅[双工服务](../wcf/feature-details/duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="11630-111">For more information about duplex services, see [Duplex Services](../wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="11630-112">有关创建 WCF 服务和这些服务的客户端的详细信息，请参阅[基本 WCF 编程](../wcf/basic-wcf-programming.md)、[设计和实现服务](../wcf/designing-and-implementing-services.md)以及[生成客户端](../wcf/building-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="11630-112">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../wcf/basic-wcf-programming.md), [Designing and Implementing Services](../wcf/designing-and-implementing-services.md), and [Building Clients](../wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="11630-113">DCOM 代码示例</span><span class="sxs-lookup"><span data-stu-id="11630-113">DCOM example code</span></span>  
 <span data-ttu-id="11630-114">对于这些方案，使用 WCF 所示的 DCOM 接口具有以下结构：</span><span class="sxs-lookup"><span data-stu-id="11630-114">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
```csharp  
[ComVisible(true)]  
[Guid("AA9C4CDB-55EA-4413-90D2-843F1A49E6E6")]  
public interface IRemoteService  
{  
   Customer GetObjectByValue();  
   IRemoteObject GetObjectByReference();  
   void SendObjectByValue(Customer customer);  
}  
  
[ComVisible(true)]  
[Guid("A12C98DE-B6A1-463D-8C24-81E4BBC4351B")]  
public interface IRemoteObject  
{  
}  
  
public class Customer  
{  
}  
```  
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="11630-115">此服务返回对象按值</span><span class="sxs-lookup"><span data-stu-id="11630-115">The service returns an object by-value</span></span>  
 <span data-ttu-id="11630-116">对于此方案，可调用服务并且此服务的方法将返回对象，此对象按值从服务器传递到客户端对象。</span><span class="sxs-lookup"><span data-stu-id="11630-116">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="11630-117">这种方案表示以下 COM 调用：</span><span class="sxs-lookup"><span data-stu-id="11630-117">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="11630-118">在此方案中，客户端从远程服务接收对象的反序列化副本。</span><span class="sxs-lookup"><span data-stu-id="11630-118">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="11630-119">客户端与此本地副本可进行交互，而无需调用返回到服务。</span><span class="sxs-lookup"><span data-stu-id="11630-119">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="11630-120">换言之，客户端会得到保证，在调用本地副本的方法时，无论如何都不会涉及到该服务。</span><span class="sxs-lookup"><span data-stu-id="11630-120">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="11630-121">WCF 始终按值从服务返回对象，因此以下步骤描述了创建常规 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="11630-121">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="11630-122">步骤 1：定义 WCF 服务接口</span><span class="sxs-lookup"><span data-stu-id="11630-122">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="11630-123">定义 WCF 服务的公共接口并标记 [<xref:System.ServiceModel.ServiceContractAttribute>] 属性。</span><span class="sxs-lookup"><span data-stu-id="11630-123">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="11630-124">为需要对客户端公开的方法标记 [<xref:System.ServiceModel.OperationContractAttribute>] 属性。</span><span class="sxs-lookup"><span data-stu-id="11630-124">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="11630-125">以下示例演示了如何使用这些属性标识客户端可以调用的服务器端接口和接口方法。</span><span class="sxs-lookup"><span data-stu-id="11630-125">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="11630-126">此方案中使用的方法用粗体显示。</span><span class="sxs-lookup"><span data-stu-id="11630-126">The method used for this scenario is shown in bold.</span></span>  
  
```csharp  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Web;
. . .  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]  
    void StoreCustomer(Customer customer);  
  
    [OperationContract]     Customer GetCustomer(string firstName, string lastName);
  
}  
```  
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="11630-127">步骤 2：定义数据协定</span><span class="sxs-lookup"><span data-stu-id="11630-127">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="11630-128">下一步，你应该创建服务的数据协定，此协定将描述服务及其客户端间将如何交换数据。</span><span class="sxs-lookup"><span data-stu-id="11630-128">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="11630-129">应为数据协定中描述的类标记 [<xref:System.Runtime.Serialization.DataContractAttribute>] 属性。</span><span class="sxs-lookup"><span data-stu-id="11630-129">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="11630-130">希望对客户端和服务器可见的单独属性或字段标记为 [<xref:System.Runtime.Serialization.DataMemberAttribute>] 属性。</span><span class="sxs-lookup"><span data-stu-id="11630-130">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="11630-131">要允许从数据协定的类派生的类型，必须使用 [<xref:System.Runtime.Serialization.KnownTypeAttribute>] 属性标识它们。</span><span class="sxs-lookup"><span data-stu-id="11630-131">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="11630-132">WCF 将仅序列化或反序列化服务接口中的类型和标识为已知类型的类型。</span><span class="sxs-lookup"><span data-stu-id="11630-132">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="11630-133">如果尝试使用不是已知类型的类型，则将发生异常。</span><span class="sxs-lookup"><span data-stu-id="11630-133">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="11630-134">有关数据协定的详细信息，请参阅[数据协定](../wcf/samples/data-contracts.md)</span><span class="sxs-lookup"><span data-stu-id="11630-134">For more information about data contracts, see [Data Contracts](../wcf/samples/data-contracts.md).</span></span>  
  
```csharp  
[DataContract]  
[KnownType(typeof(PremiumCustomer))]  
public class Customer  
{  
    [DataMember]  
    public string Firstname;  
    [DataMember]  
    public string Lastname;  
    [DataMember]  
    public Address DefaultDeliveryAddress;  
    [DataMember]  
    public Address DefaultBillingAddress;  
}  
 [DataContract]  
public class PremiumCustomer : Customer  
{  
    [DataMember]  
    public int AccountID;  
}  
  
 [DataContract]  
public class Address  
{  
    [DataMember]  
    public string Street;  
    [DataMember]  
    public string Zipcode;  
    [DataMember]  
    public string City;  
    [DataMember]  
    public string State;  
    [DataMember]  
    public string Country;  
}  
```  
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="11630-135">步骤 3：实现 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="11630-135">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="11630-136">下一步，你应该实现 WCF 服务类，此服务类将实现你在上一步中所定义的接口。</span><span class="sxs-lookup"><span data-stu-id="11630-136">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
```csharp  
public class CustomerService: ICustomerManager
{  
    public void StoreCustomer(Customer customer)  
    {  
        // write to a database  
    }  
    public Customer GetCustomer(string firstName, string lastName)  
    {  
        // read from a database  
    }  
}  
```  
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="11630-137">步骤 4：配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="11630-137">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="11630-138">若要运行 WCF 服务，则需要声明公开特定 URL 中使用特定 WCF 绑定的服务接口的终结点。</span><span class="sxs-lookup"><span data-stu-id="11630-138">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="11630-139">绑定指定传输、编码和协议的详细信息，以便客户端和服务器进行通信。</span><span class="sxs-lookup"><span data-stu-id="11630-139">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="11630-140">通常将绑定添加到服务项目的配置文件 (web.config) 中。</span><span class="sxs-lookup"><span data-stu-id="11630-140">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="11630-141">下面内容显示了服务示例的绑定项：</span><span class="sxs-lookup"><span data-stu-id="11630-141">The following shows a binding entry for the example service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Server.CustomerService">  
        <endpoint address="http://localhost:8083/CustomerManager"
                  binding="basicHttpBinding"  
                  contract="Shared.ICustomerManager" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="11630-142">下一步，需要配置客户端，以匹配由服务所指定的绑定信息。</span><span class="sxs-lookup"><span data-stu-id="11630-142">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="11630-143">为此，请将以下代码添加到客户端的应用程序配置 (app.config) 文件中。</span><span class="sxs-lookup"><span data-stu-id="11630-143">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"
                address="http://localhost:8083/CustomerManager"
                binding="basicHttpBinding"
                contract="Shared.ICustomerManager"/>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="11630-144">步骤 5：运行服务</span><span class="sxs-lookup"><span data-stu-id="11630-144">Step 5: Run the service</span></span>  
 <span data-ttu-id="11630-145">最后，通过向服务应用程序添加以下行并启动此应用程序，你可以在控制台应用程序中自承载服务。</span><span class="sxs-lookup"><span data-stu-id="11630-145">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="11630-146">有关托管 WCF 服务应用程序的其他方式的详细信息，请参阅[托管服务](../wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="11630-146">For more information about other ways to host a WCF service application, [Hosting Services](../wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="11630-147">步骤 6：从客户端调用服务</span><span class="sxs-lookup"><span data-stu-id="11630-147">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="11630-148">若要从客户端调用服务，则需要创建服务的通道工厂，并请求一个通道，这将使你能够直接从客户端调用 `GetCustomer` 方法。</span><span class="sxs-lookup"><span data-stu-id="11630-148">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="11630-149">通道可实现服务接口，并为你处理基础的请求/答复逻辑。</span><span class="sxs-lookup"><span data-stu-id="11630-149">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="11630-150">此方法调用的返回值是服务响应的反序列化的副本。</span><span class="sxs-lookup"><span data-stu-id="11630-150">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="11630-151">客户端按值向服务器发送对象</span><span class="sxs-lookup"><span data-stu-id="11630-151">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="11630-152">在此方案中，客户端将对象按值发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="11630-152">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="11630-153">这意味着服务器将接收对象的反序列化副本。</span><span class="sxs-lookup"><span data-stu-id="11630-153">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="11630-154">服务器可对此副本调用方法，并确保客户端代码中没有回调。</span><span class="sxs-lookup"><span data-stu-id="11630-154">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="11630-155">如前所述，正常的 WCF 数据交换是按值进行的。</span><span class="sxs-lookup"><span data-stu-id="11630-155">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="11630-156">这可确保对其中一个对象的调用方法仅在本地执行 – 它将不会调用客户端上的代码。</span><span class="sxs-lookup"><span data-stu-id="11630-156">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="11630-157">这种方案表示以下 COM 方法调用：</span><span class="sxs-lookup"><span data-stu-id="11630-157">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="11630-158">此方案使用与第一个示例中所示相同的服务接口和数据协定。</span><span class="sxs-lookup"><span data-stu-id="11630-158">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="11630-159">此外，客户端和服务将按相同的方法进行配置。</span><span class="sxs-lookup"><span data-stu-id="11630-159">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="11630-160">在此示例中，建立了一个信道，以发送对象并按相同的方式运行。</span><span class="sxs-lookup"><span data-stu-id="11630-160">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="11630-161">但是，对于此示例，将创建一个客户端，此客户端可调用服务，并按值传递对象。</span><span class="sxs-lookup"><span data-stu-id="11630-161">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="11630-162">客户端将在服务协定中调用的服务方法用粗体显示：</span><span class="sxs-lookup"><span data-stu-id="11630-162">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="11630-163">将代码添加到发送按值对象的客户端</span><span class="sxs-lookup"><span data-stu-id="11630-163">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="11630-164">以下代码演示了客户端如何创建一个新的按值客户对象、如何创建与 `ICustomerManager` 服务进行通信的通道以及如何其发送客户对象。</span><span class="sxs-lookup"><span data-stu-id="11630-164">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="11630-165">将序列化客户对象，并将其发送到服务，由服务将其反序列化为对象的新副本。</span><span class="sxs-lookup"><span data-stu-id="11630-165">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="11630-166">服务对此对象调用的任何方法将仅对服务器本地执行。</span><span class="sxs-lookup"><span data-stu-id="11630-166">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="11630-167">请注意，此代码说明发送派生的类型 (`PremiumCustomer`)。</span><span class="sxs-lookup"><span data-stu-id="11630-167">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="11630-168">服务协定期望 `Customer` 对象，但服务数据协定使用 [<xref:System.Runtime.Serialization.KnownTypeAttribute>] 属性以表示同样允许 `PremiumCustomer`。</span><span class="sxs-lookup"><span data-stu-id="11630-168">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="11630-169">WCF 通过此服务接口序列化或反序列化任何其他类型的尝试将失败。</span><span class="sxs-lookup"><span data-stu-id="11630-169">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
```csharp  
PremiumCustomer customer = new PremiumCustomer();  
customer.Firstname = "John";  
customer.Lastname = "Doe";  
customer.DefaultBillingAddress = new Address();  
customer.DefaultBillingAddress.Street = "One Microsoft Way";  
customer.DefaultDeliveryAddress = customer.DefaultBillingAddress;  
customer.AccountID = 42;  
  
ChannelFactory<ICustomerManager> factory =  
   new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager customerManager = factory.CreateChannel();  
customerManager.StoreCustomer(customer);  
```  
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="11630-170">服务按引用返回对象</span><span class="sxs-lookup"><span data-stu-id="11630-170">The service returns an object by reference</span></span>  
 <span data-ttu-id="11630-171">对于此方案，客户端应用调用远程服务，此方法将返回一个对象，此对象由引用从服务到传递到客户端。</span><span class="sxs-lookup"><span data-stu-id="11630-171">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="11630-172">如前所述，WCF 服务将始终按值返回对象。</span><span class="sxs-lookup"><span data-stu-id="11630-172">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="11630-173">但是，可以通过使用 <xref:System.ServiceModel.EndpointAddress10> 类，实现类似的效果。</span><span class="sxs-lookup"><span data-stu-id="11630-173">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="11630-174"><xref:System.ServiceModel.EndpointAddress10> 是客户端可用于获取服务器上会话按引用对象的可序列化的按值对象。</span><span class="sxs-lookup"><span data-stu-id="11630-174">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="11630-175">此方案所示的 WCF 中按引用对象的行为不同于 DCOM。</span><span class="sxs-lookup"><span data-stu-id="11630-175">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="11630-176">在 DCOM 中，服务器可直接返回按引用对象到客户端，而客户端可调用此对象的方法，并在服务器上执行。</span><span class="sxs-lookup"><span data-stu-id="11630-176">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="11630-177">但是在 WCF 中，始终按值返回对象。</span><span class="sxs-lookup"><span data-stu-id="11630-177">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="11630-178">客户端必须取得由 <xref:System.ServiceModel.EndpointAddress10> 表示的按值对象，并用将其用于创建自己的会话按引用对象。</span><span class="sxs-lookup"><span data-stu-id="11630-178">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="11630-179">客户端方法对服务器上的会话对象执行进行调用。换言之，WCF 中的按引用对象是配置为会话的普通 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="11630-179">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="11630-180">在 WCF 中，会话是使两个终结点之间发送的多个消息关联的一种方法。</span><span class="sxs-lookup"><span data-stu-id="11630-180">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="11630-181">这意味着一旦客户端获取与此服务的连接，将会建立客户端和服务器之间的会话。</span><span class="sxs-lookup"><span data-stu-id="11630-181">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="11630-182">对于此单个会话中的所有交互，客户端都将使用服务器端对象的单个唯一实例。</span><span class="sxs-lookup"><span data-stu-id="11630-182">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="11630-183">会话 WCF 协定与面向连接的网络请求/响应模式类似。</span><span class="sxs-lookup"><span data-stu-id="11630-183">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="11630-184">此方案由以下的 DCOM 方法表示。</span><span class="sxs-lookup"><span data-stu-id="11630-184">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="11630-185">步骤 1：定义会话 WCF 服务接口与实现</span><span class="sxs-lookup"><span data-stu-id="11630-185">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="11630-186">首先，定义包含会话对象的 WCF 服务接口。</span><span class="sxs-lookup"><span data-stu-id="11630-186">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="11630-187">在此代码中，为会话对象标记 `ServiceContract` 属性，从而将其识别为常规的 WCF 服务接口。</span><span class="sxs-lookup"><span data-stu-id="11630-187">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="11630-188">此外，设置 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> 属性，以指示它将成为会话服务。</span><span class="sxs-lookup"><span data-stu-id="11630-188">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
```csharp  
[ServiceContract(SessionMode = SessionMode.Allowed)]  
public interface ISessionBoundObject  
{  
    [OperationContract]  
    string GetCurrentValue();  
  
    [OperationContract]  
    void SetCurrentValue(string value);  
}  
```  
  
 <span data-ttu-id="11630-189">以下代码演示服务实现。</span><span class="sxs-lookup"><span data-stu-id="11630-189">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="11630-190">为此服务标记 [ServiceBehavior] 属性，并且将其 InstanceContextMode 属性设置为 InstanceContextMode.PerSessions，以指示应为每个会话创建这种类型的唯一实例。</span><span class="sxs-lookup"><span data-stu-id="11630-190">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
```csharp  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
    public class MySessionBoundObject : ISessionBoundObject  
    {  
        private string _value;  
  
        public string GetCurrentValue()  
        {  
            return _value;  
        }  
  
        public void SetCurrentValue(string val)  
        {  
            _value = val;  
        }  
  
    }  
```  
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="11630-191">步骤 2：定义会话对象的 WCF 工厂服务</span><span class="sxs-lookup"><span data-stu-id="11630-191">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="11630-192">必须定义并实现创建会话对象的服务。</span><span class="sxs-lookup"><span data-stu-id="11630-192">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="11630-193">下面的代码演示如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="11630-193">The following code shows how to do this.</span></span> <span data-ttu-id="11630-194">此代码将创建另一种返回 <xref:System.ServiceModel.EndpointAddress10> 对象的 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="11630-194">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="11630-195">这是一种可用于创建会话对象的终结点的可序列化形式。</span><span class="sxs-lookup"><span data-stu-id="11630-195">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="11630-196">以下是此服务的实现。</span><span class="sxs-lookup"><span data-stu-id="11630-196">The following is the implementation of this service.</span></span> <span data-ttu-id="11630-197">此实现维护单一实例通道工厂以创建会话对象。</span><span class="sxs-lookup"><span data-stu-id="11630-197">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="11630-198">当调用 `GetInstanceAddress` 时，它会创建一个通道，并创建一个指向与此通道关联的远程地址的 <xref:System.ServiceModel.EndpointAddress10> 对象。</span><span class="sxs-lookup"><span data-stu-id="11630-198">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="11630-199"><xref:System.ServiceModel.EndpointAddress10> 是一种可按值返回到客户端的数据类型。</span><span class="sxs-lookup"><span data-stu-id="11630-199"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>
  
```csharp  
public class SessionBoundFactory : ISessionBoundFactory  
    {  
        public static ChannelFactory<ISessionBoundObject> _factory =
            new ChannelFactory<ISessionBoundObject>("sessionbound");  
  
        public SessionBoundFactory()  
        {  
        }  
  
        public EndpointAddress10 GetInstanceAddress()  
        {  
            IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
            return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
        }  
    }  
```  
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="11630-200">步骤 3：配置并启动 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="11630-200">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="11630-201">若要承载这些服务，将需要添加以下内容到服务器的配置文件 (web.config) 中。</span><span class="sxs-lookup"><span data-stu-id="11630-201">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="11630-202">添加描述会话对象终结点的 `<client>` 节。</span><span class="sxs-lookup"><span data-stu-id="11630-202">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="11630-203">在此方案中，服务器还充当客户端，并必须配置为启用此功能。</span><span class="sxs-lookup"><span data-stu-id="11630-203">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="11630-204">在 `<services>` 节中，声明工厂和会话对象的服务终结点。</span><span class="sxs-lookup"><span data-stu-id="11630-204">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="11630-205">这使客户端可与服务终结点通信，可获取 <xref:System.ServiceModel.EndpointAddress10> 并可创建会话通道。</span><span class="sxs-lookup"><span data-stu-id="11630-205">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="11630-206">以下是使用这些设置的配置文件示例：</span><span class="sxs-lookup"><span data-stu-id="11630-206">The following is an example configuration file with these settings:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"  
                address="net.tcp://localhost:8081/SessionBoundObject"  
                binding="netTcpBinding"  
                contract="Shared.ISessionBoundObject"/>  
    </client>  
  
    <services>  
      <service name="Server.MySessionBoundObject">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                  binding="netTcpBinding"
                  contract="Shared.ISessionBoundObject" />  
      </service>  
      <service name="Server.SessionBoundFactory">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                  binding="netTcpBinding"
                  contract="Shared.ISessionBoundFactory" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="11630-207">将以下行添加到控制台应用程序中，从而自承载服务并启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="11630-207">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="11630-208">步骤 4：配置客户端并调用服务</span><span class="sxs-lookup"><span data-stu-id="11630-208">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="11630-209">通过在项目的应用程序配置文件 (app.config) 中进行以下项，配置客户端与 WCF 服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="11630-209">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"
                address="net.tcp://localhost:8081/SessionBoundObject"
                binding="netTcpBinding"
                contract="Shared.ISessionBoundObject"/>  
      <endpoint name="factory"
                address="net.tcp://localhost:8081/SessionBoundFactory"
                binding="netTcpBinding"
                contract="Shared.ISessionBoundFactory"/>  
    </client>
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="11630-210">若要调用此服务，请将代码添加到客户端，以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="11630-210">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="11630-211">创建 `ISessionBoundFactory` 服务通道。</span><span class="sxs-lookup"><span data-stu-id="11630-211">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="11630-212">使用此通道调用 `ISessionBoundFactory` 服务并获取 <xref:System.ServiceModel.EndpointAddress10> 对象。</span><span class="sxs-lookup"><span data-stu-id="11630-212">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="11630-213">使用 <xref:System.ServiceModel.EndpointAddress10> 创建通道，以获取会话对象。</span><span class="sxs-lookup"><span data-stu-id="11630-213">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="11630-214">调用 `SetCurrentValue` 和 `GetCurrentValue` 方法，演示它与跨多个调用的对象实例相同。</span><span class="sxs-lookup"><span data-stu-id="11630-214">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
```csharp  
ChannelFactory<ISessionBoundFactory> factory =  
        new ChannelFactory<ISessionBoundFactory>("factory");  
  
ISessionBoundFactory sessionBoundFactory = factory.CreateChannel();  
  
EndpointAddress10 address = sessionBoundFactory.GetInstanceAddress();  
  
ChannelFactory<ISessionBoundObject> sessionBoundObjectFactory =  
    new ChannelFactory<ISessionBoundObject>(  
        new NetTcpBinding(),  
        address.ToEndpointAddress());  
  
ISessionBoundObject sessionBoundObject =  
        sessionBoundObjectFactory.CreateChannel();  
  
sessionBoundObject.SetCurrentValue("Hello");  
if (sessionBoundObject.GetCurrentValue() == "Hello")  
{  
    Console.WriteLine("Session-full instance management works as expected");  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="11630-215">请参阅</span><span class="sxs-lookup"><span data-stu-id="11630-215">See also</span></span>

- [<span data-ttu-id="11630-216">基本 WCF 编程</span><span class="sxs-lookup"><span data-stu-id="11630-216">Basic WCF Programming</span></span>](../wcf/basic-wcf-programming.md)
- [<span data-ttu-id="11630-217">设计和实现服务</span><span class="sxs-lookup"><span data-stu-id="11630-217">Designing and Implementing Services</span></span>](../wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="11630-218">生成客户端</span><span class="sxs-lookup"><span data-stu-id="11630-218">Building Clients</span></span>](../wcf/building-clients.md)
- [<span data-ttu-id="11630-219">双工服务</span><span class="sxs-lookup"><span data-stu-id="11630-219">Duplex Services</span></span>](../wcf/feature-details/duplex-services.md)
