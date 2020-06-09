---
title: 在配置文件中配置发现
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 59eaecb7e34b9105bc694f444d98c13c036d552f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597548"
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="9ec4f-102">在配置文件中配置发现</span><span class="sxs-lookup"><span data-stu-id="9ec4f-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="9ec4f-103">发现功能主要采用四组配置设置。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="9ec4f-104">本主题将简要介绍其中的每组设置，并用示例演示如何配置这些设置。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="9ec4f-105">本主题每一部分后面都将提供一个链接，以便于您获取有关各个方面的更详尽的文档。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="9ec4f-106">行为配置</span><span class="sxs-lookup"><span data-stu-id="9ec4f-106">Behavior Configuration</span></span>  
 <span data-ttu-id="9ec4f-107">发现功能采用服务行为和终结点行为。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="9ec4f-108"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 行为能够发现服务的所有终结点，并允许您指定公告终结点。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="9ec4f-109">下面的示例演示如何添加 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 以及指定公告终结点。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="9ec4f-110">指定行为后，请从 <的> 元素进行引用， `service` 如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
         <!-- Application Endpoint -->  
         <endpoint address="endpoint0"  
                   binding="basicHttpBinding"  
                   contract="IHelloWorldService" />  
         <!-- Discovery Endpoints -->  
         <endpoint kind="udpDiscoveryEndpoint" />  
        </service>  
    </services>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9ec4f-111">为使服务可供检测，还必须添加发现终结点，上面的示例添加了一个 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 标准终结点。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="9ec4f-112">添加公告终结点时，还必须向 <> 元素添加公告侦听器服务， `services` 如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
      <!-- Application Endpoint -->  
      <endpoint address="endpoint0"  
                binding="basicHttpBinding"  
                contract="IHelloWorldService" />  
      <!-- Discovery Endpoints -->  
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <!-- Announcement Listener Configuration -->  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>
```  
  
 <span data-ttu-id="9ec4f-113"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 行为用于允许或禁止发现特定终结点。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="9ec4f-114">下面的示例配置一个具有两个应用程序终结点的服务，其中一个终结点允许发现，另一个终结点禁止发现。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="9ec4f-115">为每个终结点添加一个 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 行为。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService"  
               behaviorConfiguration="helloWorldServiceBehavior">  
  
        <!-- Application Endpoints -->  
        <endpoint address="endpoint0"  
                 binding="basicHttpBinding"  
                 contract="IHelloWorldService"
                 behaviorConfiguration="ep0Behavior" />  
  
        <endpoint address="endpoint1"  
                  binding="basicHttpBinding"  
                  contract="IHelloWorldService"  
                  behaviorConfiguration="ep1Behavior" />  
  
        <!-- Discovery Endpoints -->  
        <endpoint kind="udpDiscoveryEndpoint" />  
      </service>  
   </services>  
   <behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery />  
        </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="ep0Behavior">  
          <endpointDiscovery enabled="true"/>  
        </behavior>  
        <behavior name="ep1Behavior">  
          <endpointDiscovery enabled="false"/>  
        </behavior>  
     </endpointBehaviors>  
   </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9ec4f-116"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 行为还可用于向服务返回的终结点元数据添加自定义元数据。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="9ec4f-117">以下示例演示如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-117">The following example shows how to do this.</span></span>  
  
```xml  
<behavior name="ep4Behavior">  
   <endpointDiscovery enabled="true">  
      <extensions>  
         <CustomMetadata>This is custom metadata.</CustomMetadata>  
         <d:Types xmlns:d="http://schemas.xmlsoap.org/ws/2005/04/discovery" xmlns:i="http://printer.example.org/2003/imaging">i:PrintBasic</d:Types>  
         <CustomMetadata netsted="true">  
            <NestedMetadata>This is a nested custom metadata.</NestedMetadata>  
         </CustomMetadata>  
      </extensions>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="9ec4f-118"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 行为还可用于添加客户端搜索服务时采用的范围和类型。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="9ec4f-119">下面的示例演示如何在客户端配置文件中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
```xml  
<behavior name="ep2Behavior">  
   <endpointDiscovery enabled="true">  
      <scopes>  
         <add scope="http://www.microsoft.com/building42/floor1"/>  
         <add scope="ldap:///ou=engineeringo=examplecomc=us"/>  
      </scopes>  
      <types>  
         <add name="test" namespace="http://example.microsoft.com/" />  
         <add name="additionalContract" namespace="http://example.microsoft.com/" />  
      </types>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="9ec4f-120">有关的详细信息 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ， <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 请参阅[WCF 发现概述](wcf-discovery-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="9ec4f-121">绑定元素配置</span><span class="sxs-lookup"><span data-stu-id="9ec4f-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="9ec4f-122">绑定元素配置在客户端最有意义。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="9ec4f-123">您可以使用配置指定从 WCF 客户端应用程序发现服务时采用的查找条件。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="9ec4f-124">下面的示例使用 <xref:System.ServiceModel.Discovery.DiscoveryClient> 通道创建自定义绑定，并指定包含类型和范围的查找条件。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="9ec4f-125">此外，本示例还指定了 <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 和 <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
```xml  
<bindings>  
   <customBinding>  
      <!-- Binding Configuration for the Application Endpoint -->  
      <binding name="discoBindingConfiguration">  
         <discoveryClient>  
            <endpoint kind="discoveryEndpoint"  
                      address="http://localhost:8000/ConfigTest/Discovery"  
                      binding="customBinding"  
                      bindingConfiguration="httpSoap12WSAddressing10"/>  
            <findCriteria duration="00:00:10" maxResults="2">  
              <types>  
                <add name="IHelloWorldService"/>  
              </types>  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>
            </findCriteria>  
          </discoveryClient>  
          <textMessageEncoding messageVersion="Soap11"/>  
          <httpTransport />  
      </binding>
   </customBinding>
</bindings>  
```  
  
 <span data-ttu-id="9ec4f-126">客户端终结点必须引用此自定义绑定配置：</span><span class="sxs-lookup"><span data-stu-id="9ec4f-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 <span data-ttu-id="9ec4f-127">有关查找条件的详细信息，请参阅[发现查找和 s](discovery-find-and-findcriteria.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-127">For more information about find criteria see [Discovery Find and FindCriteria](discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="9ec4f-128">有关发现和绑定元素的详细信息，请参阅[WCF 发现概述](wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="9ec4f-128">For more information about discovery and binding elements see, [WCF Discovery Overview](wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="9ec4f-129">标准终结点配置</span><span class="sxs-lookup"><span data-stu-id="9ec4f-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="9ec4f-130">标准终结点是预定义的终结点，这样的终结点的一个或多个属性（地址、绑定或协定）采用默认值，或者具有一个或多个无法更改的属性值。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="9ec4f-131">.NET 4 随附了 3 个与发现相关的标准终结点：<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>、<xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> 和 <xref:System.ServiceModel.Discovery.DynamicEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="9ec4f-132"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 是通过 UDP 多播绑定为发现操作预先配置的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="9ec4f-133"><xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> 是预先配置的通过 UDP 绑定发送公告消息的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="9ec4f-134"><xref:System.ServiceModel.Discovery.DynamicEndpoint> 是使用发现功能在运行时动态查找已发现服务的终结点地址的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="9ec4f-135">标准绑定是使用一个包含 kind 特性的 <> 元素指定的，该 `endpoint` 元素包含指定要添加的标准终结点的类型。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="9ec4f-136">下面的示例演示如何添加 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 和 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>  
```  
  
 <span data-ttu-id="9ec4f-137">标准终结点在 <> 元素中进行配置 `standardEndpoints` 。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="9ec4f-138">下面的示例演示如何配置 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 和 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<standardEndpoints>  
      <udpAnnouncementEndpoint>  
        <standardEndpoint
            name="udpAnnouncementEndpointSettings"
            multicastAddress="soap.udp://239.255.255.250:3703"
            maxAnnouncementDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="1028"  
            maxPendingMessageCount="10"  
            maxMulticastRetransmitCount="3"  
            maxUnicastRetransmitCount="2"  
            socketReceiveBufferSize="131072"  
            timeToLive="2" />  
        </standardEndpoint>  
      </udpAnnouncementEndpoint>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
            name="udpDiscoveryEndpointSettings"  
            multicastAddress="soap.udp://239.255.255.252:3704"  
            maxResponseDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="2048"  
            maxPendingMessageCount="5"  
            maxReceivedMessageSize="8192"  
            maxBufferPoolSize="262144"/>  
        </standardEndpoint>  
      </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="9ec4f-139">添加标准终结点配置后，请在每个终结点的 <> 元素中引用该配置， `endpoint` 如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->
      <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="udpDiscoveryEndpointSettings"/>  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" endpointConfiguration="udpAnnouncementEndpointSettings" >  
   </service>  
</services>  
```  
  
 <span data-ttu-id="9ec4f-140">与发现功能使用的其他标准终结点不同，您可以为 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 指定绑定和协定。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="9ec4f-141">下面的示例演示如何添加和配置 <xref:System.ServiceModel.Discovery.DynamicEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint kind="dynamicEndpoint" binding="basicHttpBinding" contract="IHelloWorldService" endpointConfiguration="dynamicEndpointConfiguration" />  
    </client>
   <standardEndpoints>  
      <dynamicEndpoint>  
         <standardEndpoint name="dynamicEndpointConfiguration">  
             <discoveryClientSettings>  
              <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="2">  
                 <types>  
                   <add name="IHelloWorldService"/>  
                 </types>  
                 <scopes>  
                   <add scope="http://www.microsoft.com/building42/floor1"/>  
                 </scopes>  
                 <extensions>  
                   <CustomMetadata>This is custom metadata.</CustomMetadata>
                 </extensions>  
               </findCriteria>  
             </discoveryClientSettings>  
           </standardEndpoint>  
         </dynamicEndpoint>  
   </standardEndpoints>  
</system.ServiceModel>  
```  
  
 <span data-ttu-id="9ec4f-142">有关标准终结点的详细信息，请参阅[标准终结点](standard-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec4f-142">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
