---
title: 如何：使用筛选器
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 434171138e75a0f4c336cd80cc2beb574b10001e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598887"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="84ca0-102">如何：使用筛选器</span><span class="sxs-lookup"><span data-stu-id="84ca0-102">How To: Use Filters</span></span>
<span data-ttu-id="84ca0-103">本主题概述创建使用多个筛选器的路由配置所需执行的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="84ca0-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="84ca0-104">在本示例中，消息将路由到两个计算器服务实现，即 regularCalc 和 roundingCalc。</span><span class="sxs-lookup"><span data-stu-id="84ca0-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="84ca0-105">这两个实现都支持相同的运算；但其中一个服务在返回计算结果前会将所有计算结果舍入到最接近的整数值。</span><span class="sxs-lookup"><span data-stu-id="84ca0-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="84ca0-106">客户端应用程序必须能够指示是否使用服务的舍入版本；如果未表示任何服务首选项，则消息将在这两个服务间执行负载平衡。</span><span class="sxs-lookup"><span data-stu-id="84ca0-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="84ca0-107">这两个服务公开的运算包括：</span><span class="sxs-lookup"><span data-stu-id="84ca0-107">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="84ca0-108">添加</span><span class="sxs-lookup"><span data-stu-id="84ca0-108">Add</span></span>  
  
- <span data-ttu-id="84ca0-109">减</span><span class="sxs-lookup"><span data-stu-id="84ca0-109">Subtract</span></span>  
  
- <span data-ttu-id="84ca0-110">乘</span><span class="sxs-lookup"><span data-stu-id="84ca0-110">Multiply</span></span>  
  
- <span data-ttu-id="84ca0-111">除</span><span class="sxs-lookup"><span data-stu-id="84ca0-111">Divide</span></span>  
  
 <span data-ttu-id="84ca0-112">鉴于这两个服务实现相同的运算，您无法使用 Action 筛选器，这是因为在消息中指定的操作将并非唯一。</span><span class="sxs-lookup"><span data-stu-id="84ca0-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="84ca0-113">您必须执行其他工作来确保将消息路由到适当的终结点。</span><span class="sxs-lookup"><span data-stu-id="84ca0-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="84ca0-114">确定唯一数据</span><span class="sxs-lookup"><span data-stu-id="84ca0-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="84ca0-115">由于两个服务实现处理相同的运算，并且除了返回的数据之外基本相同，因此从客户端应用程序发送的消息中包含的基本数据不具备足够的独特性，无法确定如何路由请求。</span><span class="sxs-lookup"><span data-stu-id="84ca0-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="84ca0-116">但是，如果客户端应用程序向消息添加了唯一的标头值，则您可以使用此值确定应如何路由消息。</span><span class="sxs-lookup"><span data-stu-id="84ca0-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="84ca0-117">在本示例中，如果客户端应用程序需要由舍入计算器处理消息，它将使用下面的代码添加自定义标头：</span><span class="sxs-lookup"><span data-stu-id="84ca0-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="84ca0-118">现在，您可以使用 XPath 筛选器检查消息中是否含有此标头，并将包含该标头的消息路由到 roundCalc 服务。</span><span class="sxs-lookup"><span data-stu-id="84ca0-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="84ca0-119">此外，路由服务还公开两个虚拟服务终结点，可将这两个终结点与 EndpointName、EndpointAddress 或 PrefixEndpointAddress 筛选器配合使用，以基于客户端应用程序提交请求的目标终结点将传入消息唯一路由到特定计算器实现。</span><span class="sxs-lookup"><span data-stu-id="84ca0-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="84ca0-120">定义终结点</span><span class="sxs-lookup"><span data-stu-id="84ca0-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="84ca0-121">定义路由服务使用的终结点时，首先应确定客户端和服务使用的通道的形状。</span><span class="sxs-lookup"><span data-stu-id="84ca0-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="84ca0-122">在此方案中，两个目标服务都使用请求-答复模式，因此使用 <xref:System.ServiceModel.Routing.IRequestReplyRouter>。</span><span class="sxs-lookup"><span data-stu-id="84ca0-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="84ca0-123">下面的示例定义路由服务公开的服务终结点。</span><span class="sxs-lookup"><span data-stu-id="84ca0-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
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
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     <span data-ttu-id="84ca0-124">通过此配置，路由服务公开三个单独的终结点。</span><span class="sxs-lookup"><span data-stu-id="84ca0-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="84ca0-125">客户端应用程序根据运行时选项将消息发送到其中一个地址。</span><span class="sxs-lookup"><span data-stu-id="84ca0-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="84ca0-126">到达某个 "虚拟" 服务终结点（"舍入/计算器" 或 "常规/计算器"）的消息将转发给相应的计算器实现。</span><span class="sxs-lookup"><span data-stu-id="84ca0-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="84ca0-127">如果客户端应用程序未将请求发送到特定终结点，则将消息发送到常规终结点。</span><span class="sxs-lookup"><span data-stu-id="84ca0-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="84ca0-128">不论选择哪个终结点，客户端应用程序还可以选择包括自定义标头，以指示应将消息转发到舍入计算器实现。</span><span class="sxs-lookup"><span data-stu-id="84ca0-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="84ca0-129">下面的示例定义路由服务将消息路由到的客户端（目标）终结点。</span><span class="sxs-lookup"><span data-stu-id="84ca0-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     <span data-ttu-id="84ca0-130">这些终结点用于在筛选器表中指示当匹配特定筛选器时将消息发送到的目标终结点。</span><span class="sxs-lookup"><span data-stu-id="84ca0-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="84ca0-131">定义筛选器</span><span class="sxs-lookup"><span data-stu-id="84ca0-131">Define Filters</span></span>  
  
1. <span data-ttu-id="84ca0-132">若要根据客户端应用程序添加到消息的 "RoundingCalculator" 自定义标头路由消息，请定义一个筛选器，该筛选器使用 XPath 查询来检查是否存在此标头。</span><span class="sxs-lookup"><span data-stu-id="84ca0-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="84ca0-133">由于此标头是使用自定义命名空间定义的，因此还添加了一个命名空间项，用于定义在 XPath 查询中使用的自定义命名空间前缀 "custom"。</span><span class="sxs-lookup"><span data-stu-id="84ca0-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="84ca0-134">下面的示例定义所需的路由节、命名空间表和 XPath 筛选器。</span><span class="sxs-lookup"><span data-stu-id="84ca0-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     <span data-ttu-id="84ca0-135">此**MessageFilter**在包含值 "舍入" 的消息中查找 RoundingCalculator 标头。</span><span class="sxs-lookup"><span data-stu-id="84ca0-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="84ca0-136">此标头由客户端设置，用于指示应将消息路由到 roundingCalc 服务。</span><span class="sxs-lookup"><span data-stu-id="84ca0-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="84ca0-137">默认情况下，在命名空间表中定义 s12 命名空间前缀，表示命名空间 `http://www.w3.org/2003/05/soap-envelope` 。</span><span class="sxs-lookup"><span data-stu-id="84ca0-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="84ca0-138">您还必须定义用于查找在两个虚拟终结点上接收到的消息的筛选器。</span><span class="sxs-lookup"><span data-stu-id="84ca0-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="84ca0-139">第一个虚拟终结点是 "常规/计算器" 终结点。</span><span class="sxs-lookup"><span data-stu-id="84ca0-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="84ca0-140">客户端可以将请求发送到此终结点，以指示应将消息路由到 regularCalc 服务。</span><span class="sxs-lookup"><span data-stu-id="84ca0-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="84ca0-141">下面的配置定义一个筛选器，该筛选器使用 <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> 确定消息是否通过具有 filterData 中指定的名称的终结点到达。</span><span class="sxs-lookup"><span data-stu-id="84ca0-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="84ca0-142">如果名为 "calculatorEndpoint" 的服务终结点收到消息，此筛选器的计算结果为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="84ca0-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="84ca0-143">接着，定义一个筛选器，该筛选器查找发送到 roundingEndpoint 地址的消息。</span><span class="sxs-lookup"><span data-stu-id="84ca0-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="84ca0-144">客户端可以将请求发送到此终结点，以指示应将消息路由到 roundingCalc 服务。</span><span class="sxs-lookup"><span data-stu-id="84ca0-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="84ca0-145">下面的配置定义一个筛选器，该筛选器使用 <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> 来确定消息是否到达 "舍入/计算器" 终结点。</span><span class="sxs-lookup"><span data-stu-id="84ca0-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="84ca0-146">如果在以开头的地址收到消息， `http://localhost/routingservice/router/rounding/` 则此筛选器的计算结果为**true**。</span><span class="sxs-lookup"><span data-stu-id="84ca0-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="84ca0-147">由于此配置使用的基址为，为 `http://localhost/routingservice/router` roundingEndpoint 指定的地址为 "舍入/计算器"，用于与此终结点通信的完整地址为 `http://localhost/routingservice/router/rounding/calculator` ，与此筛选器匹配。</span><span class="sxs-lookup"><span data-stu-id="84ca0-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="84ca0-148">PrefixEndpointAddress 筛选器在执行匹配时不会计算主机名，因为可以使用多种主机名形式引用单个主机，而所有这些主机名可能都是从客户端应用程序引用主机的有效方式。</span><span class="sxs-lookup"><span data-stu-id="84ca0-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="84ca0-149">例如，下面的所有主机名可能引用同一主机：</span><span class="sxs-lookup"><span data-stu-id="84ca0-149">For example, all of the following may refer to the same host:</span></span>  
    >
    > - <span data-ttu-id="84ca0-150">localhost</span><span class="sxs-lookup"><span data-stu-id="84ca0-150">localhost</span></span>  
    > - <span data-ttu-id="84ca0-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="84ca0-151">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="84ca0-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="84ca0-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="84ca0-153">最后一个筛选器必须支持路由到达常规终结点但没有自定义标头的消息。</span><span class="sxs-lookup"><span data-stu-id="84ca0-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="84ca0-154">对于此种情况，消息应在 regularCalc 和 roundingCalc 服务之间交替。</span><span class="sxs-lookup"><span data-stu-id="84ca0-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="84ca0-155">若要支持这些消息的 "轮循机制" 路由，请使用自定义筛选器，以允许一个筛选器实例与每个已处理消息匹配。</span><span class="sxs-lookup"><span data-stu-id="84ca0-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="84ca0-156">下面定义了 RoundRobinMessageFilter 的两个实例，这两个实例组合在一起以指示它们应彼此交替。</span><span class="sxs-lookup"><span data-stu-id="84ca0-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     <span data-ttu-id="84ca0-157">在运行期间，此筛选器类型在定义的此类型的所有筛选器实例（这些实例在一个集合中配置为同一组）之间交替。</span><span class="sxs-lookup"><span data-stu-id="84ca0-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="84ca0-158">这会导致此自定义筛选器处理的消息在 `true` 和的返回之间交替 `RoundRobinFilter1` `RoundRobinFilter2` 。</span><span class="sxs-lookup"><span data-stu-id="84ca0-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="84ca0-159">定义筛选器表</span><span class="sxs-lookup"><span data-stu-id="84ca0-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="84ca0-160">若要将筛选器与特定客户端终结点关联，必须将筛选器放置到筛选器表中。</span><span class="sxs-lookup"><span data-stu-id="84ca0-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="84ca0-161">此示例方案还采用筛选器优先级设置，该可选设置用于指示筛选器的处理顺序。</span><span class="sxs-lookup"><span data-stu-id="84ca0-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="84ca0-162">如果未指定筛选器优先级，则将同时计算所有筛选器。</span><span class="sxs-lookup"><span data-stu-id="84ca0-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="84ca0-163">虽然指定筛选器优先级可以控制筛选器的处理顺序，但可能会对路由服务的性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="84ca0-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="84ca0-164">如有可能，请构造筛选器逻辑，以免使用筛选器优先级。</span><span class="sxs-lookup"><span data-stu-id="84ca0-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="84ca0-165">下面定义了筛选器表，并将之前定义的 "XPathFilter" 添加到优先级为2的表中。</span><span class="sxs-lookup"><span data-stu-id="84ca0-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="84ca0-166">此项还指定，如果与 `XPathFilter` 消息匹配，消息将路由到 `roundingCalcEndpoint` 。</span><span class="sxs-lookup"><span data-stu-id="84ca0-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          </filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="84ca0-167">如果指定了筛选器优先级，将首先计算优先级最高的筛选器。</span><span class="sxs-lookup"><span data-stu-id="84ca0-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="84ca0-168">如果处于特定优先级级别的一个或多个筛选器匹配，将不会计算较低优先级级别的筛选器。</span><span class="sxs-lookup"><span data-stu-id="84ca0-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="84ca0-169">对于此方案，指定的最高优先级是 2，这是此级别的唯一筛选器条目。</span><span class="sxs-lookup"><span data-stu-id="84ca0-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="84ca0-170">定义了筛选器条目，以通过检查终结点名称或地址前缀来检查是否在特定终结点上收到了消息。</span><span class="sxs-lookup"><span data-stu-id="84ca0-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="84ca0-171">下面的条目将这两个筛选器条目添加到筛选器表，并将这两个条目与消息将路由到的目标终结点相关联。</span><span class="sxs-lookup"><span data-stu-id="84ca0-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="84ca0-172">这些筛选器的优先级设置为 1，指示近当前面的 XPath 筛选器与消息不匹配时才应运行这些筛选器。</span><span class="sxs-lookup"><span data-stu-id="84ca0-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="84ca0-173">由于这些筛选器的筛选器优先级为 1，因此，仅当优先级级别为 2 的筛选器与消息不匹配时，才会计算这些筛选器。</span><span class="sxs-lookup"><span data-stu-id="84ca0-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="84ca0-174">此外，由于这两个筛选器具有相同的优先级级别，因此将同时计算它们。</span><span class="sxs-lookup"><span data-stu-id="84ca0-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="84ca0-175">由于两个筛选器是互斥的，因此其中只能有一个筛选器与消息相匹配。</span><span class="sxs-lookup"><span data-stu-id="84ca0-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="84ca0-176">如果消息与前面的所有筛选器均不匹配，则将通过泛型服务终结点接收该消息，并且该消息未包含指示其路由到的目标位置的标头信息。</span><span class="sxs-lookup"><span data-stu-id="84ca0-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="84ca0-177">这些消息将由自定义筛选器处理，该筛选器在两个计算器服务之间对这些消息实现负载平衡。</span><span class="sxs-lookup"><span data-stu-id="84ca0-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="84ca0-178">下面的示例演示如何将筛选器条目添加到筛选器表；每个筛选器均与两个目标终结点之一相关联。</span><span class="sxs-lookup"><span data-stu-id="84ca0-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="84ca0-179">由于这些条目指定了优先级 0，因此，仅当较高优先级的筛选器与消息均不匹配时，才会计算这些筛选器。</span><span class="sxs-lookup"><span data-stu-id="84ca0-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="84ca0-180">此外，由于这两个筛选器具有相同的优先级级别，因此将同时计算它们。</span><span class="sxs-lookup"><span data-stu-id="84ca0-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="84ca0-181">如前所述，对于接收到的每条消息，在这些筛选器定义使用的自定义筛选器中，只有其中一个筛选器的计算结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="84ca0-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="84ca0-182">由于仅使用此筛选器定义了两个筛选器，并且两个筛选器具有指定的相同组设置，因此其结果是：路由服务在将消息发送到 regularCalcEndpoint 和 RoundingCalcEndpoint 之间交替。</span><span class="sxs-lookup"><span data-stu-id="84ca0-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="84ca0-183">若要根据筛选器计算消息，筛选器表必须首先与将用来接收消息的服务终结点相关联。</span><span class="sxs-lookup"><span data-stu-id="84ca0-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="84ca0-184">下面的示例演示如何使用路由行为将路由表与服务终结点相关联：</span><span class="sxs-lookup"><span data-stu-id="84ca0-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="84ca0-185">示例</span><span class="sxs-lookup"><span data-stu-id="84ca0-185">Example</span></span>  
 <span data-ttu-id="84ca0-186">下面是配置文件的完整代码清单。</span><span class="sxs-lookup"><span data-stu-id="84ca0-186">The following is a complete listing of the configuration file.</span></span>  
  
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
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
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
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="84ca0-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84ca0-187">See also</span></span>

- [<span data-ttu-id="84ca0-188">路由服务</span><span class="sxs-lookup"><span data-stu-id="84ca0-188">Routing Services</span></span>](../samples/routing-services.md)
