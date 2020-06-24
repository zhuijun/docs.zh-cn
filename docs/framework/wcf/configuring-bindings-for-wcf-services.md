---
title: 为 Windows Communication Foundation 服务配置绑定
description: 了解如何通过编辑系统下的项在部署时为 WCF 应用程序配置绑定。System.servicemodel 元素。
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: a2bb396e65722726e54cd315e931eea933386659
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247623"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="3eda3-103">为 Windows Communication Foundation 服务配置绑定</span><span class="sxs-lookup"><span data-stu-id="3eda3-103">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="3eda3-104">创建应用程序时，您经常需要将一些决策交给管理员在部署应用程序后制定。</span><span class="sxs-lookup"><span data-stu-id="3eda3-104">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="3eda3-105">例如，通常没有办法提前知道服务地址或统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="3eda3-105">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="3eda3-106">最好允许管理员在创建服务后指定地址，而不是对地址进行硬编码。</span><span class="sxs-lookup"><span data-stu-id="3eda3-106">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="3eda3-107">这种灵活性是通过配置实现的。</span><span class="sxs-lookup"><span data-stu-id="3eda3-107">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3eda3-108">[Svcutil.exe](servicemodel-metadata-utility-tool-svcutil-exe.md)将配置文件与交换机一起使用， `/config` 以快速创建配置文件。</span><span class="sxs-lookup"><span data-stu-id="3eda3-108">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="3eda3-109">主要部分</span><span class="sxs-lookup"><span data-stu-id="3eda3-109">Major Sections</span></span>  
 <span data-ttu-id="3eda3-110">Windows Communication Foundation （WCF）配置方案包含以下三个主要部分（ `serviceModel` 、 `bindings` 和 `services` ）：</span><span class="sxs-lookup"><span data-stu-id="3eda3-110">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a><span data-ttu-id="3eda3-111">ServiceModel 元素</span><span class="sxs-lookup"><span data-stu-id="3eda3-111">ServiceModel Elements</span></span>  
 <span data-ttu-id="3eda3-112">你可以使用由元素限定的部分 `system.ServiceModel` 来配置具有一个或多个终结点的服务类型以及服务的设置。</span><span class="sxs-lookup"><span data-stu-id="3eda3-112">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="3eda3-113">然后，可以为每个终结点配置地址、协定以及绑定。</span><span class="sxs-lookup"><span data-stu-id="3eda3-113">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="3eda3-114">有关终结点的详细信息，请参阅[创建终结点概述](endpoint-creation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3eda3-114">For more information about endpoints, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="3eda3-115">如果未指定任何终结点，则运行时添加默认终结点。</span><span class="sxs-lookup"><span data-stu-id="3eda3-115">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="3eda3-116">有关默认终结点、绑定和行为的详细信息，请参阅[简化配置](simplified-configuration.md)和 [WCF 服务的简化配置](./samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3eda3-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="3eda3-117">绑定指定传输（HTTP、TCP、管道、消息队列）和协议（安全性、可靠性、事务流）。绑定由绑定元素组成，其中的每个元素都指定终结点与世界的通信方式的一个方面。</span><span class="sxs-lookup"><span data-stu-id="3eda3-117">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="3eda3-118">例如，指定 [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) 元素指示使用 HTTP 作为终结点的传输。</span><span class="sxs-lookup"><span data-stu-id="3eda3-118">For example, specifying the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="3eda3-119">这用于在使用此终结点的服务打开时在运行时连接终结点。</span><span class="sxs-lookup"><span data-stu-id="3eda3-119">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="3eda3-120">有两种绑定：预定义绑定和自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="3eda3-120">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="3eda3-121">预定义绑定包含在常见方案中使用的元素的有用组合。</span><span class="sxs-lookup"><span data-stu-id="3eda3-121">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="3eda3-122">有关 WCF 提供的预定义绑定类型的列表，请参阅[系统提供的绑定](system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="3eda3-122">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="3eda3-123">如果没有任何预定义绑定集合具有服务应用程序所需的功能的正确组合，那么你可以构造自定义绑定来满足应用程序的需求。</span><span class="sxs-lookup"><span data-stu-id="3eda3-123">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="3eda3-124">有关自定义绑定的详细信息，请参阅 [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3eda3-124">For more information about custom bindings, see [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="3eda3-125">以下四个示例演示了用于设置 WCF 服务的最常见的绑定配置。</span><span class="sxs-lookup"><span data-stu-id="3eda3-125">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="3eda3-126">指定终结点以使用绑定类型</span><span class="sxs-lookup"><span data-stu-id="3eda3-126">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="3eda3-127">第一个示例说明如何指定一个配置了地址、协定和绑定的终结点。</span><span class="sxs-lookup"><span data-stu-id="3eda3-127">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 <span data-ttu-id="3eda3-128">在本示例中，`name` 属性表示使用该配置的服务类型。</span><span class="sxs-lookup"><span data-stu-id="3eda3-128">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="3eda3-129">当您用 `HelloWorld` 协定通过代码中创建服务时，它将以示例配置中定义的所有终结点进行初始化。</span><span class="sxs-lookup"><span data-stu-id="3eda3-129">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="3eda3-130">如果程序集仅实现一个服务协定，则 `name` 可以省略属性，因为该服务使用唯一可用的类型。</span><span class="sxs-lookup"><span data-stu-id="3eda3-130">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="3eda3-131">该属性采用字符串，该字符串必须遵循以下格式：`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="3eda3-131">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="3eda3-132">`address` 属性指定其他终结点用于与该服务通信的 URI。</span><span class="sxs-lookup"><span data-stu-id="3eda3-132">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="3eda3-133">该 URI 可以是绝对路径，也可以是相对路径。</span><span class="sxs-lookup"><span data-stu-id="3eda3-133">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="3eda3-134">如果提供的是相对地址，则需要主机提供适合于绑定中所使用的传输方案的基址。</span><span class="sxs-lookup"><span data-stu-id="3eda3-134">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="3eda3-135">如果未配置地址，则假定基址为该终结点的地址。</span><span class="sxs-lookup"><span data-stu-id="3eda3-135">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="3eda3-136">`contract` 属性指定该终结点所公开的协定。</span><span class="sxs-lookup"><span data-stu-id="3eda3-136">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="3eda3-137">服务实现类型必须实现该协定类型。</span><span class="sxs-lookup"><span data-stu-id="3eda3-137">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="3eda3-138">如果服务实现所实现的是单个协定类型，则可以省略此属性。</span><span class="sxs-lookup"><span data-stu-id="3eda3-138">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="3eda3-139">`binding` 属性选择要用于此特定终结点的预定义或自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="3eda3-139">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="3eda3-140">不显式选择绑定的终结点使用默认绑定选择，即 `BasicHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="3eda3-140">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="3eda3-141">修改预定义绑定</span><span class="sxs-lookup"><span data-stu-id="3eda3-141">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="3eda3-142">在下面的示例中，修改了预定义绑定。</span><span class="sxs-lookup"><span data-stu-id="3eda3-142">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="3eda3-143">然后可以将该绑定用于配置服务中的任意终结点。</span><span class="sxs-lookup"><span data-stu-id="3eda3-143">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="3eda3-144">可通过将 <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> 值设置为 1 秒的方式来修改绑定。</span><span class="sxs-lookup"><span data-stu-id="3eda3-144">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="3eda3-145">请注意，该属性返回一个 <xref:System.TimeSpan> 对象。</span><span class="sxs-lookup"><span data-stu-id="3eda3-145">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="3eda3-146">在绑定部分中可以找到该更改的绑定。</span><span class="sxs-lookup"><span data-stu-id="3eda3-146">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="3eda3-147">现在，通过在 `binding` 元素中设置 `endpoint` 特性，可以在创建任何终结点时使用该更改的绑定。</span><span class="sxs-lookup"><span data-stu-id="3eda3-147">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3eda3-148">如果为该绑定指定了特定名称，则服务终结点中指定的 `bindingConfiguration` 必须与其相匹配。</span><span class="sxs-lookup"><span data-stu-id="3eda3-148">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="3eda3-149">配置要应用于服务的行为</span><span class="sxs-lookup"><span data-stu-id="3eda3-149">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="3eda3-150">在下面的示例中，为该服务类型配置了一个特定的行为。</span><span class="sxs-lookup"><span data-stu-id="3eda3-150">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="3eda3-151">`ServiceMetadataBehavior`元素用于启用 "使用的[元数据实用工具（Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md) " 来查询服务，并从元数据生成 Web 服务描述语言（WSDL）文档。</span><span class="sxs-lookup"><span data-stu-id="3eda3-151">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3eda3-152">如果为该行为指定了特定名称，则服务或终结点部分中指定的 `behaviorConfiguration` 必须与其相匹配。</span><span class="sxs-lookup"><span data-stu-id="3eda3-152">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />
    </behavior>  
</behaviors>  
<services>  
    <service
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 <span data-ttu-id="3eda3-153">上面的配置使客户端可以调用并获取“HelloWorld”类型的服务的元数据。</span><span class="sxs-lookup"><span data-stu-id="3eda3-153">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="3eda3-154">使用不同的绑定值指定具有两个终结点的服务</span><span class="sxs-lookup"><span data-stu-id="3eda3-154">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="3eda3-155">这是最后一个示例，在本示例中，为 `HelloWorld` 服务类型配置了两个终结点。</span><span class="sxs-lookup"><span data-stu-id="3eda3-155">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="3eda3-156">每个终结点使用同一绑定类型的不同自定义 `bindingConfiguration` 属性（每个都修改 `basicHttpBinding` ）。</span><span class="sxs-lookup"><span data-stu-id="3eda3-156">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding
        name="shortTimeout"  
        timeout="00:00:00:01"
     />  
     <basicHttpBinding
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="3eda3-157">通过添加 `protocolMapping` 部分并按下面的示例所示配置绑定，可以使用默认配置获得相同的行为。</span><span class="sxs-lookup"><span data-stu-id="3eda3-157">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding
        name="shortTimeout"  
        timeout="00:00:00:01"
     />  
     <basicHttpBinding
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3eda3-158">请参阅</span><span class="sxs-lookup"><span data-stu-id="3eda3-158">See also</span></span>

- [<span data-ttu-id="3eda3-159">简化配置</span><span class="sxs-lookup"><span data-stu-id="3eda3-159">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="3eda3-160">系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="3eda3-160">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="3eda3-161">终结点创建概述</span><span class="sxs-lookup"><span data-stu-id="3eda3-161">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)
- [<span data-ttu-id="3eda3-162">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="3eda3-162">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
