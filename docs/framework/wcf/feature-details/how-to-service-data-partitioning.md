---
title: 如何：服务数据分区
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 3b2f86ee6a4dea25fb5c972d4cecb1b9ed411b29
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601187"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="26d62-102">如何：服务数据分区</span><span class="sxs-lookup"><span data-stu-id="26d62-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="26d62-103">本主题概述了在同一目标服务的多个实例之间划分消息时所需采取的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="26d62-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="26d62-104">如果需要缩放服务以提供更好的服务质量，或者需要以特定方式处理来自不同客户的请求，此时通常采用服务数据划分。</span><span class="sxs-lookup"><span data-stu-id="26d62-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="26d62-105">例如，来自高价值或 "黄金" 客户的消息可能需要比标准客户的消息处理更高的优先级。</span><span class="sxs-lookup"><span data-stu-id="26d62-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="26d62-106">在本示例中，将消息路由到 regularCalc 服务的两个实例之一。</span><span class="sxs-lookup"><span data-stu-id="26d62-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="26d62-107">服务的两个实例相同；但是，calculator1 终结点表示的服务负责处理从高价值客户收到的消息，而 calculator 2 终结点负责处理来自其他客户的消息。</span><span class="sxs-lookup"><span data-stu-id="26d62-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="26d62-108">客户端发送的消息不含任何独特数据可用于标识应将消息路由到哪个服务实例。</span><span class="sxs-lookup"><span data-stu-id="26d62-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="26d62-109">为了使每个客户端都将数据路由到特定目标服务，系统中将实现两个用于接收消息的服务终结点。</span><span class="sxs-lookup"><span data-stu-id="26d62-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26d62-110">虽然此示例中使用特定终结点来划分数据，不过，也可使用消息本身中包含的信息（如标头或正文数据）来实现此操作。</span><span class="sxs-lookup"><span data-stu-id="26d62-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="26d62-111">实现服务数据划分</span><span class="sxs-lookup"><span data-stu-id="26d62-111">Implement Service Data Partitioning</span></span>  
  
1. <span data-ttu-id="26d62-112">通过指定由服务公开的服务终结点，创建基本路由服务配置。</span><span class="sxs-lookup"><span data-stu-id="26d62-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="26d62-113">下面的示例定义了两个用于接收消息的终结点，</span><span class="sxs-lookup"><span data-stu-id="26d62-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="26d62-114">还定义了客户端终结点，这些客户端终结点用于将消息发送到 regularCalc 服务实例。</span><span class="sxs-lookup"><span data-stu-id="26d62-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
       </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
        <endpoint name="CalcEndpoint1"  
                  address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
  
        <endpoint name="CalcEndpoint2"  
                  address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
     </client>  
    ```  
  
2. <span data-ttu-id="26d62-115">定义用于将消息路由到目标终结点的筛选器。</span><span class="sxs-lookup"><span data-stu-id="26d62-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="26d62-116">对于本示例，EndpointName 筛选器用于确定哪个服务终结点接收消息。</span><span class="sxs-lookup"><span data-stu-id="26d62-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="26d62-117">下面的示例定义所需的路由节和筛选器。</span><span class="sxs-lookup"><span data-stu-id="26d62-117">The following example defines the necessary routing section and filters.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the different message filters-->  
      <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
      <filter name="HighPriority" filterType="EndpointName"  
              filterData="calculator1Endpoint"/>  
      <filter name="NormalPriority" filterType="EndpointName"  
              filterData="calculator2Endpoint"/>  
    </filters>  
    ```  
  
3. <span data-ttu-id="26d62-118">定义筛选器表，该表将各个筛选器与客户端终结点相关联。</span><span class="sxs-lookup"><span data-stu-id="26d62-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="26d62-119">在本示例中，将根据通过其接收消息的特定终结点路由消息。</span><span class="sxs-lookup"><span data-stu-id="26d62-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="26d62-120">由于消息只能与两个可能的过滤器之一匹配，因此无需使用筛选器优先级控制筛选器的求值顺序。</span><span class="sxs-lookup"><span data-stu-id="26d62-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="26d62-121">以下代码定义筛选器表并添加前面定义的筛选器。</span><span class="sxs-lookup"><span data-stu-id="26d62-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="26d62-122">若要根据表中包含的筛选器对传入消息求值，必须使用路由行为将筛选器表与服务终结点关联。</span><span class="sxs-lookup"><span data-stu-id="26d62-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="26d62-123">下面的示例演示如何将 "filterTable1" 与服务终结点相关联：</span><span class="sxs-lookup"><span data-stu-id="26d62-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="26d62-124">示例</span><span class="sxs-lookup"><span data-stu-id="26d62-124">Example</span></span>  
 <span data-ttu-id="26d62-125">下面是配置文件的完整代码清单。</span><span class="sxs-lookup"><span data-stu-id="26d62-125">The following is a complete listing of the configuration file.</span></span>  
  
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
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
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
      <endpoint name="CalcEndpoint1"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="CalcEndpoint2"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
  
      <filters>  
        <!--define the different message filters-->  
        <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
        <filter name="HighPriority" filterType="EndpointName"  
                filterData="calculator1Endpoint"/>  
        <filter name="NormalPriority" filterType="EndpointName"  
                filterData="calculator2Endpoint"/>  
      </filters>  
  
      <filterTables>  
        <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
          <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
        </filterTable>  
      </filterTables>  
  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26d62-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26d62-126">See also</span></span>

- [<span data-ttu-id="26d62-127">路由服务</span><span class="sxs-lookup"><span data-stu-id="26d62-127">Routing Services</span></span>](../samples/routing-services.md)
