---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: c421273d1d08db047a51f1f1e4f9d6c908f12986
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "84201786"
---
# \<serviceMetadata>
<span data-ttu-id="467b5-101">指定服务元数据的发布和相关信息。</span><span class="sxs-lookup"><span data-stu-id="467b5-101">Specifies the publication of service metadata and associated information.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="467b5-102">语法</span><span class="sxs-lookup"><span data-stu-id="467b5-102">Syntax</span></span>  
  
```xml  
<serviceMetadata externalMetadataLocation="String"
                 httpGetBinding="String"
                 httpGetBindingConfiguration="String"
                 httpGetEnabled="Boolean"
                 httpGetUrl="String"
                 httpsGetBinding="String"
                 httpsGetBindingConfiguration="String"
                 httpsGetEnabled="Boolean"
                 httpsGetUrl="String"
                 policyVersion="Policy12/Policy15" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="467b5-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="467b5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="467b5-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="467b5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="467b5-105">特性</span><span class="sxs-lookup"><span data-stu-id="467b5-105">Attributes</span></span>  
  
|<span data-ttu-id="467b5-106">属性</span><span class="sxs-lookup"><span data-stu-id="467b5-106">Attribute</span></span>|<span data-ttu-id="467b5-107">说明</span><span class="sxs-lookup"><span data-stu-id="467b5-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="467b5-108">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="467b5-108">externalMetadataLocation</span></span>|<span data-ttu-id="467b5-109">一个包含 WSDL 文件的位置的 URI，该文件将返回到用户以响应 WSDL 和 MEX 请求而非自动生成的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="467b5-109">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="467b5-110">当未设置此属性时，将返回默认的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="467b5-110">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="467b5-111">默认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="467b5-111">The default is an empty string.</span></span>|  
|<span data-ttu-id="467b5-112">httpGetBinding</span><span class="sxs-lookup"><span data-stu-id="467b5-112">httpGetBinding</span></span>|<span data-ttu-id="467b5-113">一个字符串，指定将用于通过 HTTP GET 进行元数据检索的绑定类型。</span><span class="sxs-lookup"><span data-stu-id="467b5-113">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="467b5-114">此设置是可选的。</span><span class="sxs-lookup"><span data-stu-id="467b5-114">This setting is optional.</span></span> <span data-ttu-id="467b5-115">如果未指定此设置，则将使用默认绑定。</span><span class="sxs-lookup"><span data-stu-id="467b5-115">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="467b5-116">仅支持具有支持 <xref:System.ServiceModel.Channels.IReplyChannel> 的内部绑定元素的绑定。</span><span class="sxs-lookup"><span data-stu-id="467b5-116">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="467b5-117">此外，绑定的 <xref:System.ServiceModel.Channels.MessageVersion> 属性必须为 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。</span><span class="sxs-lookup"><span data-stu-id="467b5-117">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="467b5-118">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="467b5-118">httpGetBindingConfiguration</span></span>|<span data-ttu-id="467b5-119">一个字符串，用于设置在 `httpGetBinding` 特性中指定的绑定的名称，此名称引用此绑定的其他配置信息。</span><span class="sxs-lookup"><span data-stu-id="467b5-119">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="467b5-120">必须在 `<bindings>` 节中定义相同的名称。</span><span class="sxs-lookup"><span data-stu-id="467b5-120">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="467b5-121">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="467b5-121">httpGetEnabled</span></span>|<span data-ttu-id="467b5-122">一个布尔值，指定是否发布服务元数据以便使用 HTTP/Get 请求进行检索。</span><span class="sxs-lookup"><span data-stu-id="467b5-122">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="467b5-123">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="467b5-123">The default is `false`.</span></span><br /><br /> <span data-ttu-id="467b5-124">如果未指定 httpGetUrl 属性，则发布元数据的地址为服务地址加上“?wsdl”。</span><span class="sxs-lookup"><span data-stu-id="467b5-124">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="467b5-125">例如，如果服务地址为，则 `http://localhost:8080/CalculatorService` HTTP/Get 元数据地址为 `http://localhost:8080/CalculatorService?wsdl` 。</span><span class="sxs-lookup"><span data-stu-id="467b5-125">For example, if the service address is `http://localhost:8080/CalculatorService`, the HTTP/Get metadata address is `http://localhost:8080/CalculatorService?wsdl`.</span></span><br /><br /> <span data-ttu-id="467b5-126">如果此属性为 `false` ，或服务的地址不基于 HTTP 或 HTTPS，则忽略 "？ wsdl"。</span><span class="sxs-lookup"><span data-stu-id="467b5-126">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="467b5-127">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="467b5-127">httpGetUrl</span></span>|<span data-ttu-id="467b5-128">一个 URI，指定发布元数据的地址以便使用 HTTP/Get 请求进行检索。</span><span class="sxs-lookup"><span data-stu-id="467b5-128">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="467b5-129">如果指定了相对 Uri，则它将被视为相对于服务的基址。</span><span class="sxs-lookup"><span data-stu-id="467b5-129">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="467b5-130">httpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="467b5-130">httpsGetBinding</span></span>|<span data-ttu-id="467b5-131">一个字符串，指定将用于通过 HTTPS GET 进行元数据检索的绑定类型。</span><span class="sxs-lookup"><span data-stu-id="467b5-131">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="467b5-132">此设置是可选的。</span><span class="sxs-lookup"><span data-stu-id="467b5-132">This setting is optional.</span></span> <span data-ttu-id="467b5-133">如果未指定此设置，则将使用默认绑定。</span><span class="sxs-lookup"><span data-stu-id="467b5-133">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="467b5-134">仅支持具有支持 <xref:System.ServiceModel.Channels.IReplyChannel> 的内部绑定元素的绑定。</span><span class="sxs-lookup"><span data-stu-id="467b5-134">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="467b5-135">此外，绑定的 <xref:System.ServiceModel.Channels.MessageVersion> 属性必须为 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。</span><span class="sxs-lookup"><span data-stu-id="467b5-135">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="467b5-136">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="467b5-136">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="467b5-137">一个字符串，用于设置在 `httpsGetBinding` 特性中指定的绑定的名称，此名称引用此绑定的其他配置信息。</span><span class="sxs-lookup"><span data-stu-id="467b5-137">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="467b5-138">必须在 `<bindings>` 节中定义相同的名称。</span><span class="sxs-lookup"><span data-stu-id="467b5-138">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="467b5-139">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="467b5-139">httpsGetEnabled</span></span>|<span data-ttu-id="467b5-140">一个布尔值，指定是否发布服务元数据以便使用 HTTPS/Get 请求进行检索。</span><span class="sxs-lookup"><span data-stu-id="467b5-140">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="467b5-141">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="467b5-141">The default is `false`.</span></span><br /><br /> <span data-ttu-id="467b5-142">如果未指定 httpsGetUrl 属性，则发布元数据的地址为服务地址加上“?wsdl”。</span><span class="sxs-lookup"><span data-stu-id="467b5-142">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="467b5-143">例如，如果服务地址为 " https://localhost:8080/CalculatorService "，则 HTTP/Get 元数据地址为 " https://localhost:8080/CalculatorService?wsdl "。</span><span class="sxs-lookup"><span data-stu-id="467b5-143">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="467b5-144">如果此属性为 `false` ，或服务的地址不基于 HTTP 或 HTTPS，则忽略 "？ wsdl"。</span><span class="sxs-lookup"><span data-stu-id="467b5-144">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="467b5-145">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="467b5-145">httpsGetUrl</span></span>|<span data-ttu-id="467b5-146">一个 URI，指定发布元数据的地址以便使用 HTTPS/Get 请求进行检索。</span><span class="sxs-lookup"><span data-stu-id="467b5-146">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="467b5-147">policyVersion</span><span class="sxs-lookup"><span data-stu-id="467b5-147">policyVersion</span></span>|<span data-ttu-id="467b5-148">一个字符串，指定所使用的 WS-Policy 规范的版本。</span><span class="sxs-lookup"><span data-stu-id="467b5-148">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="467b5-149">此属性的类型为 <xref:System.ServiceModel.Description.PolicyVersion>。</span><span class="sxs-lookup"><span data-stu-id="467b5-149">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="467b5-150">子元素</span><span class="sxs-lookup"><span data-stu-id="467b5-150">Child Elements</span></span>  
 <span data-ttu-id="467b5-151">无</span><span class="sxs-lookup"><span data-stu-id="467b5-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="467b5-152">父元素</span><span class="sxs-lookup"><span data-stu-id="467b5-152">Parent Elements</span></span>  
  
|<span data-ttu-id="467b5-153">元素</span><span class="sxs-lookup"><span data-stu-id="467b5-153">Element</span></span>|<span data-ttu-id="467b5-154">描述</span><span class="sxs-lookup"><span data-stu-id="467b5-154">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="467b5-155">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="467b5-155">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="467b5-156">注解</span><span class="sxs-lookup"><span data-stu-id="467b5-156">Remarks</span></span>  
 <span data-ttu-id="467b5-157">此配置元素允许您控制服务的元数据发布功能。</span><span class="sxs-lookup"><span data-stu-id="467b5-157">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="467b5-158">为了避免无意中泄漏可能敏感的服务元数据，Windows Communication Foundation （WCF）服务的默认配置将禁用元数据发布。</span><span class="sxs-lookup"><span data-stu-id="467b5-158">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="467b5-159">默认情况下此行为是安全的，但也意味着你无法使用元数据导入工具（例如 Svcutil.exe）生成调用服务所需的客户端代码，除非在配置中显式启用服务的元数据发布行为。</span><span class="sxs-lookup"><span data-stu-id="467b5-159">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="467b5-160">使用此配置元素，可以为服务启用此发布行为。</span><span class="sxs-lookup"><span data-stu-id="467b5-160">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="467b5-161">有关配置此行为的详细示例，请参阅[元数据发布行为](../../../wcf/samples/metadata-publishing-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="467b5-161">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="467b5-162">利用可选的 `httpGetBinding` 和 `httpsGetBinding`属性，你可以配置用于通过 HTTP GET（或 HTTPS GET）检索元数据的绑定。</span><span class="sxs-lookup"><span data-stu-id="467b5-162">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="467b5-163">如果未指定这两个属性，则根据情况使用相应的默认绑定（采用 HTTP 时为 `HttpTransportBindingElement`，采用 HTTPS 时为 `HttpsTransportBindingElement`）进行元数据检索。</span><span class="sxs-lookup"><span data-stu-id="467b5-163">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="467b5-164">请注意：不能将这些属性用于内置 WCF 绑定。</span><span class="sxs-lookup"><span data-stu-id="467b5-164">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="467b5-165">仅支持具有支持 <xref:System.ServiceModel.Channels.IReplyChannel> 的内部绑定元素的绑定。</span><span class="sxs-lookup"><span data-stu-id="467b5-165">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="467b5-166">此外，绑定的 <xref:System.ServiceModel.Channels.MessageVersion> 属性必须为 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。</span><span class="sxs-lookup"><span data-stu-id="467b5-166">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="467b5-167">为了降低服务被恶意使用者滥用的可能性，可以使用 SSL over HTTP (HTTPS) 机制来确保传输的安全。</span><span class="sxs-lookup"><span data-stu-id="467b5-167">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="467b5-168">为此，必须首先将一个适合的 X.509 证书绑定到承载该服务的计算机上的特定端口。</span><span class="sxs-lookup"><span data-stu-id="467b5-168">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="467b5-169">（有关详细信息，请参阅使用[证书](../../../wcf/feature-details/working-with-certificates.md)。）其次，将此元素添加到服务配置，并将 `httpsGetEnabled` 特性设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="467b5-169">(For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="467b5-170">最后，将 `httpsGetUrl` 属性设置为服务元数据终结点的 URL，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="467b5-170">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="NewBehavior">
      <serviceMetadata httpsGetEnabled="true"
                       httpsGetUrl="https://myComputerName/myEndpoint" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="example"></a><span data-ttu-id="467b5-171">示例</span><span class="sxs-lookup"><span data-stu-id="467b5-171">Example</span></span>  
 <span data-ttu-id="467b5-172">下面的示例使用元素将服务配置为公开元数据 \<serviceMetadata> 。</span><span class="sxs-lookup"><span data-stu-id="467b5-172">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="467b5-173">它还配置终结点以便将 `IMetadataExchange` 协定作为 WS-MetadataExchange (MEX) 协议的实现公开。</span><span class="sxs-lookup"><span data-stu-id="467b5-173">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="467b5-174">此示例使用的是 `mexHttpBinding`，这是一种便于使用的标准绑定，与安全模式设置为 `wsHttpBinding` 的 `None` 等效。</span><span class="sxs-lookup"><span data-stu-id="467b5-174">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="467b5-175">在终结点中使用相对地址 "mex"，该地址在针对服务基址进行解析时将导致终结点地址 `http://localhost/servicemodelsamples/service.svc/mex` 。</span><span class="sxs-lookup"><span data-stu-id="467b5-175">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="467b5-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="467b5-176">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="467b5-177">安全行为</span><span class="sxs-lookup"><span data-stu-id="467b5-177">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="467b5-178">元数据发布行为</span><span class="sxs-lookup"><span data-stu-id="467b5-178">Metadata Publishing Behavior</span></span>](../../../wcf/samples/metadata-publishing-behavior.md)
