---
title: 如何：服务版本控制
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: beb7de63d300ad7986bfc59093006b074b9456ba
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586931"
---
# <a name="how-to-service-versioning"></a><span data-ttu-id="d49da-102">如何：服务版本控制</span><span class="sxs-lookup"><span data-stu-id="d49da-102">How To: Service Versioning</span></span>
<span data-ttu-id="d49da-103">本主题概述了创建路由配置以将消息路由到同一服务的不同版本所需采取的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="d49da-103">This topic outlines the basic steps required to create a routing configuration that routes messages to different versions of the same service.</span></span> <span data-ttu-id="d49da-104">在本示例中，消息将路由到计算器服务的两个不同版本：`roundingCalc` (v1) 和 `regularCalc` (v2)。</span><span class="sxs-lookup"><span data-stu-id="d49da-104">In this example, messages are routed to two different versions of a calculator service, `roundingCalc` (v1) and `regularCalc` (v2).</span></span> <span data-ttu-id="d49da-105">这两个实现都支持相同的操作，但较早的服务 `roundingCalc` 在返回计算结果前会将所有计算结果舍入到最接近的整数值。</span><span class="sxs-lookup"><span data-stu-id="d49da-105">Both implementations support the same operations; however the older service, `roundingCalc`, rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="d49da-106">客户端应用程序必须能够指示是否使用较新的 `regularCalc` 服务。</span><span class="sxs-lookup"><span data-stu-id="d49da-106">A client application must be able to indicate whether to use the newer `regularCalc` service.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d49da-107">为了将消息路由到特定服务版本，路由服务必须能够根据消息内容确定消息目标。</span><span class="sxs-lookup"><span data-stu-id="d49da-107">In order to route a message to a specific service version, the Routing Service must be able to determine the message destination based on the message content.</span></span> <span data-ttu-id="d49da-108">在下面演示的方法中，客户端将信息插入消息头中来指定版本。</span><span class="sxs-lookup"><span data-stu-id="d49da-108">In the method demonstrated below, the client will specify the version by inserting information into a message header.</span></span> <span data-ttu-id="d49da-109">存在几种无需客户端传递额外数据的服务版本控制方法。</span><span class="sxs-lookup"><span data-stu-id="d49da-109">There are methods of service versioning that do not require clients to pass additional data.</span></span> <span data-ttu-id="d49da-110">例如，可以将消息路由到服务的最新版本或最兼容的版本，或者路由器可以使用标准 SOAP 信封的一部分。</span><span class="sxs-lookup"><span data-stu-id="d49da-110">For example, a message could be routed to the most recent or most compatible version of a service or the router could use a part of the standard SOAP envelope.</span></span>  
  
 <span data-ttu-id="d49da-111">这两个服务公开的运算包括：</span><span class="sxs-lookup"><span data-stu-id="d49da-111">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="d49da-112">添加</span><span class="sxs-lookup"><span data-stu-id="d49da-112">Add</span></span>  
  
- <span data-ttu-id="d49da-113">减</span><span class="sxs-lookup"><span data-stu-id="d49da-113">Subtract</span></span>  
  
- <span data-ttu-id="d49da-114">乘</span><span class="sxs-lookup"><span data-stu-id="d49da-114">Multiply</span></span>  
  
- <span data-ttu-id="d49da-115">除</span><span class="sxs-lookup"><span data-stu-id="d49da-115">Divide</span></span>  
  
 <span data-ttu-id="d49da-116">由于两个服务实现处理相同的运算，并且除了返回的数据之外基本相同，因此从客户端应用程序发送的消息中包含的基本数据不具备足够的独特性，无法确定如何路由请求。</span><span class="sxs-lookup"><span data-stu-id="d49da-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="d49da-117">例如，由于两个服务的默认操作相同，因此不能使用操作筛选器。</span><span class="sxs-lookup"><span data-stu-id="d49da-117">For example, Action filters cannot be used because the default actions for both services are the same.</span></span>  
  
 <span data-ttu-id="d49da-118">可以通过多种方式解决这个问题，例如针对服务的各个版本在路由器上公开特定终结点，或者将自定义标头元素添加到消息中以指示服务版本。</span><span class="sxs-lookup"><span data-stu-id="d49da-118">This can be resolved in several ways, such as exposing a specific endpoint on the router for each version of the service or adding a custom header element to the message to indicate service version.</span></span>  <span data-ttu-id="d49da-119">这些方法均可以将传入消息唯一地路由到服务的特定版本，但利用唯一的消息内容是区分不同服务版本的请求的首选方法。</span><span class="sxs-lookup"><span data-stu-id="d49da-119">Each of these approaches allows you to uniquely route incoming messages to a specific version of the service, but utilizing unique message content is the preferred method of differentiating between requests for different service versions.</span></span>  
  
 <span data-ttu-id="d49da-120">在本示例中，客户端应用程序将“CalcVer”自定义标头添加到请求消息中。</span><span class="sxs-lookup"><span data-stu-id="d49da-120">In this example, the client application adds the ‘CalcVer’ custom header to the request message.</span></span> <span data-ttu-id="d49da-121">此标头将包含一个值，指示应将消息路由到的服务版本。</span><span class="sxs-lookup"><span data-stu-id="d49da-121">This header will contain a value that indicates the version of the service that the message should be routed to.</span></span> <span data-ttu-id="d49da-122">值“1”指示该消息必须由 roundingCalc 服务处理，而值“2”指示必须由 regularCalc 服务处理。</span><span class="sxs-lookup"><span data-stu-id="d49da-122">A value of ‘1’ indicates that the message must be processed by the roundingCalc service, while a value of ‘2’ indicates the regularCalc service.</span></span> <span data-ttu-id="d49da-123">这样，客户端应用程序就可以直接控制将由服务的哪个版本来处理消息。</span><span class="sxs-lookup"><span data-stu-id="d49da-123">This allows the client application to directly control which version of the service will process the message.</span></span>  <span data-ttu-id="d49da-124">由于自定义标头是消息中包含的值，因此您可以使用一个终结点来接收将两个服务版本作为目标的消息。</span><span class="sxs-lookup"><span data-stu-id="d49da-124">Since the custom header is a value contained within the message, you can use one endpoint to receive messages destined for both versions of the service.</span></span> <span data-ttu-id="d49da-125">可以在客户端应用程序中使用下面的代码，将此自定义标头添加到消息中：</span><span class="sxs-lookup"><span data-stu-id="d49da-125">The following code can be used in the client application to add this custom header to the message:</span></span>  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a><span data-ttu-id="d49da-126">实现服务版本控制</span><span class="sxs-lookup"><span data-stu-id="d49da-126">Implement Service Versioning</span></span>  
  
1. <span data-ttu-id="d49da-127">通过指定由服务公开的服务终结点，创建基本的路由服务配置。</span><span class="sxs-lookup"><span data-stu-id="d49da-127">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="d49da-128">下面的示例定义了一个用于接收消息的服务终结点，</span><span class="sxs-lookup"><span data-stu-id="d49da-128">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="d49da-129">还定义用于将消息发送到 `roundingCalc` (v1) 和 `regularCalc` (v2) 服务的客户端终结点。</span><span class="sxs-lookup"><span data-stu-id="d49da-129">It also defines the client endpoints which will be used to send messages to the `roundingCalc` (v1) and the `regularCalc` (v2) services.</span></span>  
  
    ```xml  
    <services>  
        <service behaviorConfiguration="routingConfiguration"  
                 name="System.ServiceModel.Routing.RoutingService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost/routingservice/router" />  
            </baseAddresses>  
          </host>  
          <!--Set up the inbound endpoint for the Routing Service-->  
          <endpoint address="calculator"  
                    binding="wsHttpBinding"  
                    name="routerEndpoint"  
                    contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="http://localhost:8080/servicemodelsamples/service/"  
                    binding="wsHttpBinding"  
                    contract="*" />  
        </client>  
    ```  
  
2. <span data-ttu-id="d49da-130">定义用于将消息路由到目标终结点的筛选器。</span><span class="sxs-lookup"><span data-stu-id="d49da-130">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="d49da-131">对于本示例，使用 XPath 筛选器检测 "CalcVer" 自定义标头的值，以确定应将消息路由到哪个版本。</span><span class="sxs-lookup"><span data-stu-id="d49da-131">For this example, the XPath filter is used to detect the value of the "CalcVer" custom header to determine which version the message should be routed to.</span></span> <span data-ttu-id="d49da-132">XPath 筛选器还用于检测不包含 "CalcVer" 标头的消息。</span><span class="sxs-lookup"><span data-stu-id="d49da-132">An XPath filter is also used to detect messages that do not contain the "CalcVer" header.</span></span> <span data-ttu-id="d49da-133">下面的示例定义所需的筛选器和命名空间表。</span><span class="sxs-lookup"><span data-stu-id="d49da-133">The following example defines the required filters and namespace table.</span></span>  
  
    ```xml  
    <!-- use the namespace table element to define a prefix for our custom namespace-->  
    <namespaceTable>  
      <add prefix="custom" namespace="http://my.custom.namespace/"/>  
    </namespaceTable>  
    <filters>  
      <!--define the different message filters-->  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 2-->  
      <filter name="XPathFilterRegular" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '2'"/>  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 1-->  
      <filter name="XPathFilterRounding" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '1'"/>  
       <!--define an xpath message filter to look for  
           messages that do not contain the custom header-->  
       <filter name="XPathFilterNoHeader" filterType="XPath"  
               filterData="count(sm:header()/custom:CalcVer)=0"/>  
    </filters>
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="d49da-134">默认情况下，在命名空间表中定义 s12 命名空间前缀，表示命名空间 `http://www.w3.org/2003/05/soap-envelope` 。</span><span class="sxs-lookup"><span data-stu-id="d49da-134">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
3. <span data-ttu-id="d49da-135">定义筛选器表，该表将各个筛选器与客户端终结点相关联。</span><span class="sxs-lookup"><span data-stu-id="d49da-135">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="d49da-136">如果消息包含值为1的 "CalcVer" 标头，则会将其发送到 regularCalc 服务。</span><span class="sxs-lookup"><span data-stu-id="d49da-136">If the message contains the "CalcVer" header with a value of 1, it will be sent to the regularCalc service.</span></span> <span data-ttu-id="d49da-137">如果标头包含值 2，则系统将该消息发送到 roundingCalc 服务。</span><span class="sxs-lookup"><span data-stu-id="d49da-137">If the header contains a value of 2, it will be sent to the roundingCalc service.</span></span> <span data-ttu-id="d49da-138">如果没有标头，则系统将该消息路由到 regularCalc。</span><span class="sxs-lookup"><span data-stu-id="d49da-138">If no header is present, the message will be routed to the regularCalc.</span></span>  
  
     <span data-ttu-id="d49da-139">以下代码定义筛选器表并添加前面定义的筛选器。</span><span class="sxs-lookup"><span data-stu-id="d49da-139">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <!--look for the custom header = 1, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
          <!--look for the custom header = 2, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
          <!--look for the absence of the custom header, and if  
              it is not present, assume the v1 endpoint-->  
          <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="d49da-140">若要根据筛选器表中包含的筛选器评估传入消息，必须使用路由行为将筛选器表与服务终结点关联。</span><span class="sxs-lookup"><span data-stu-id="d49da-140">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="d49da-141">下面的示例演示如何 `filterTable1` 将与服务终结点相关联：</span><span class="sxs-lookup"><span data-stu-id="d49da-141">The following example demonstrates associating `filterTable1` with the service endpoints:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="d49da-142">示例</span><span class="sxs-lookup"><span data-stu-id="d49da-142">Example</span></span>  
 <span data-ttu-id="d49da-143">下面是配置文件的完整代码清单。</span><span class="sxs-lookup"><span data-stu-id="d49da-143">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="http://localhost:8080/servicemodelsamples/service/"  
                binding="wsHttpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 2-->  
        <filter name="XPathFilterRegular" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '2'"/>  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 1-->  
        <filter name="XPathFilterRounding" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '1'"/>  
        <!--define an xpath message filter to look for  
            messages that do not contain the custom header-->  
        <filter name="XPathFilterNoHeader" filterType="XPath"  
                filterData="count(sm:header()/custom:CalcVer)=0"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filters to the message filter table-->  
            <!--look for the custom header = 1, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
            <!--look for the custom header = 2, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
            <!--look for the absence of the custom header, and if  
                it is not present, assume the v1 endpoint-->  
            <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="d49da-144">示例</span><span class="sxs-lookup"><span data-stu-id="d49da-144">Example</span></span>  
 <span data-ttu-id="d49da-145">下面是客户端应用程序的完整代码清单。</span><span class="sxs-lookup"><span data-stu-id="d49da-145">The following is a complete listing of the client application.</span></span>  
  
```csharp  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    //The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
    //Client implementation code.  
    class Client  
    {  
        static void Main()  
        {  
            //Print out the welcome text  
            Console.WriteLine("This sample routes the Calculator Sample through the new WCF RoutingService");  
            Console.WriteLine("Wait for all the services to indicate that they've started, then press");  
            Console.WriteLine("<ENTER> to start the client.");  
  
            while (Console.ReadLine() != "quit")  
            {  
                //Offer the Address configuration for the client  
                Console.WriteLine("");  
                Console.WriteLine("Welcome to the Calculator Client!");  
  
                EndpointAddress epa;  
                //set the default address as the general router endpoint  
                epa = new EndpointAddress("http://localhost/routingservice/router/calculator");  
  
                //set up the CalculatorClient with the EndpointAddress, the WSHttpBinding, and the ICalculator contract  
                //We use the WSHttpBinding so that the outgoing has a message envelope, which we'll manipulate in a minute  
                CalculatorClient client = new CalculatorClient(new WSHttpBinding(), epa);  
                //client.Endpoint.Contract = ContractDescription.GetContract(typeof(ICalculator));  
  
                //Ask the customer if they want to add a custom header to the outgoing message.  
                //The Router will look for this header, and if so ignore the endpoint the message was  
                //received on, and instead direct the message to the RoundingCalcService.  
                Console.WriteLine("");  
                Console.WriteLine("Which calculator service should be used?");  
                Console.WriteLine("Enter 1 for the rounding calculator, 2 for the regular calculator.");  
                Console.WriteLine("[1] or [2]?");  
  
                string header = Console.ReadLine();  
  
                //get the current operationContextScope from the client's inner channel  
                using (OperationContextScope ocs = new OperationContextScope((client.InnerChannel)))  
                {  
                    //get the outgoing message headers element (collection) from the context  
                    MessageHeaders messageHeadersElement = OperationContext.Current.OutgoingMessageHeaders;  
  
                    //if they wanted to create the header, go ahead and add it to the outgoing message  
                    if (header != null && (header=="1" || header=="2"))  
                    {  
                        //create a new header "RoundingCalculator", no specific namespace, and set the value to
                        //the value of header.  
                        //the Routing Service will look for this header in order to determine if the message  
                        //should be routed to the RoundingCalculator  
                        messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", header));  
                    }  
                    else //incorrect choice, no header added  
                    {  
                        Console.WriteLine("Incorrect value entered, not adding a header");  
                    }  
  
                        //call the client operations  
                        CallClient(client);  
                }  
  
                //close the client to clean it up  
                client.Close();  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to run the client again or type 'quit' to quit.");  
            }  
        }  
  
        private static void CallClient(CalculatorClient client)  
        {  
            Console.WriteLine("");  
            Console.WriteLine("Sending!");  
            // Call the Add service operation.  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            value1 = 145.00D;  
            value2 = 76.54D;  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            value1 = 9.00D;  
            value2 = 81.25D;  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            value1 = 22.00D;  
            value2 = 7.00D;  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d49da-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d49da-146">See also</span></span>

- [<span data-ttu-id="d49da-147">路由服务</span><span class="sxs-lookup"><span data-stu-id="d49da-147">Routing Services</span></span>](../samples/routing-services.md)
