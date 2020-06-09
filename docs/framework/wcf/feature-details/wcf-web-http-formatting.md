---
title: WCF Web HTTP 格式设置
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: 011ff4f2e667268fac1aa2d82c0a2c4ffefc8dde
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585553"
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="43b43-102">WCF Web HTTP 格式设置</span><span class="sxs-lookup"><span data-stu-id="43b43-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="43b43-103">通过 WCF Web HTTP 编程模型，你可以动态确定服务操作返回其响应所采用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="43b43-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="43b43-104">支持使用以下两种方法来确定相应格式：即自动和显式。</span><span class="sxs-lookup"><span data-stu-id="43b43-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="43b43-105">自动格式设置</span><span class="sxs-lookup"><span data-stu-id="43b43-105">Automatic formatting</span></span>  
 <span data-ttu-id="43b43-106">启用后，自动格式设置将选择返回响应所采用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="43b43-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="43b43-107">该功能按以下顺序检查下列各项，以此来确定最佳格式：</span><span class="sxs-lookup"><span data-stu-id="43b43-107">It determines the best format by checking the following, in order:</span></span>  
  
1. <span data-ttu-id="43b43-108">请求消息的 Accept 标头中的媒体类型。</span><span class="sxs-lookup"><span data-stu-id="43b43-108">The media types in the request message’s Accept header.</span></span>  
  
2. <span data-ttu-id="43b43-109">请求消息的内容类型。</span><span class="sxs-lookup"><span data-stu-id="43b43-109">The content-type of the request message.</span></span>  
  
3. <span data-ttu-id="43b43-110">操作中的默认格式设置。</span><span class="sxs-lookup"><span data-stu-id="43b43-110">The default format setting in the operation.</span></span>  
  
4. <span data-ttu-id="43b43-111">WebHttpBehavior 中的默认格式设置。</span><span class="sxs-lookup"><span data-stu-id="43b43-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="43b43-112">如果请求消息包含 Accept 标头，则 Windows Communication Foundation （WCF）基础结构将搜索它所支持的类型。</span><span class="sxs-lookup"><span data-stu-id="43b43-112">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="43b43-113">如果 `Accept` 标头指定了其媒体类型的优先级，则会遵循这些优先级。</span><span class="sxs-lookup"><span data-stu-id="43b43-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="43b43-114">如果未在 `Accept` 标头中找到适当的格式，则使用请求消息的内容类型。</span><span class="sxs-lookup"><span data-stu-id="43b43-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="43b43-115">如果未指定适当的内容类型，则使用操作的默认格式设置。</span><span class="sxs-lookup"><span data-stu-id="43b43-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="43b43-116">默认格式使用 `ResponseFormat` 和 <xref:System.ServiceModel.Web.WebGetAttribute> 特性的 <xref:System.ServiceModel.Web.WebInvokeAttribute> 参数设置。</span><span class="sxs-lookup"><span data-stu-id="43b43-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="43b43-117">如果未对操作指定默认格式，则使用 <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="43b43-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="43b43-118">自动格式设置依赖于 <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="43b43-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="43b43-119">如果此属性设置为 `true`，WCF 基础结构将确定要使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="43b43-119">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="43b43-120">默认情况下，禁用自动格式选择，以保证向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="43b43-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="43b43-121">可以通过编程方式或配置启用自动格式选择。</span><span class="sxs-lookup"><span data-stu-id="43b43-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="43b43-122">下面的示例演示如何在代码中启用自动格式选择。</span><span class="sxs-lookup"><span data-stu-id="43b43-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 <span data-ttu-id="43b43-123">还可通过配置启用自动格式设置。</span><span class="sxs-lookup"><span data-stu-id="43b43-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="43b43-124">您可以直接在 <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> 上设置 <xref:System.ServiceModel.Description.WebHttpBehavior> 属性，也可以使用 <xref:System.ServiceModel.Description.WebHttpEndpoint> 进行设置。</span><span class="sxs-lookup"><span data-stu-id="43b43-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="43b43-125">下面的示例演示如何在 <xref:System.ServiceModel.Description.WebHttpBehavior> 上启用自动格式选择。</span><span class="sxs-lookup"><span data-stu-id="43b43-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="43b43-126">下面的示例演示如何使用 <xref:System.ServiceModel.Description.WebHttpEndpoint> 启用自动格式选择。</span><span class="sxs-lookup"><span data-stu-id="43b43-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a><span data-ttu-id="43b43-127">显式格式设置</span><span class="sxs-lookup"><span data-stu-id="43b43-127">Explicit formatting</span></span>  
 <span data-ttu-id="43b43-128">顾名思义，在显式格式设置过程中，开发人员在操作代码中确定要使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="43b43-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="43b43-129">如果最佳格式为 XML 或 JSON，开发人员会将 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> 设置为 <xref:System.ServiceModel.Web.WebMessageFormat.Xml> 或 <xref:System.ServiceModel.Web.WebMessageFormat.Json>。</span><span class="sxs-lookup"><span data-stu-id="43b43-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="43b43-130">如果未显式设置 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> 属性，则使用操作的默认格式。</span><span class="sxs-lookup"><span data-stu-id="43b43-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="43b43-131">下面的示例检查格式查询字符串参数，以获取要采用的格式。</span><span class="sxs-lookup"><span data-stu-id="43b43-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="43b43-132">如果已指定该参数，则使用 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> 设置操作的格式。</span><span class="sxs-lookup"><span data-stu-id="43b43-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
        // if a format query string parameter has been specified, set the response format to that. If no such
        // query string parameter exists the Accept header will be used
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
            if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
            {
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;
            }
            else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                throw new WebFaultException<string>($"Unsupported format '{formatQueryStringValue}'",   HttpStatusCode.BadRequest);
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 <span data-ttu-id="43b43-133">如果您需要支持除 XML 或 JSON 以外的其他格式，请定义您的操作，并将返回类型设置为 <xref:System.ServiceModel.Channels.Message>。</span><span class="sxs-lookup"><span data-stu-id="43b43-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="43b43-134">在操作代码中，确定要使用的相应格式，然后使用下列方法之一创建 <xref:System.ServiceModel.Channels.Message> 对象：</span><span class="sxs-lookup"><span data-stu-id="43b43-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="43b43-135">上述每种方法都会采取相应内容，并创建具有相应格式的消息。</span><span class="sxs-lookup"><span data-stu-id="43b43-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="43b43-136">`WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` 方法可用于获取客户端首选格式的列表（按首选项的降序顺序）。</span><span class="sxs-lookup"><span data-stu-id="43b43-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="43b43-137">下面的示例演示如何使用 `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` 确定要使用的格式，然后使用相应的响应创建方法创建响应消息。</span><span class="sxs-lookup"><span data-stu-id="43b43-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="43b43-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43b43-138">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="43b43-139">WCF Web HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="43b43-139">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="43b43-140">UriTemplate 和 UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="43b43-140">UriTemplate and UriTemplateTable</span></span>](uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="43b43-141">WCF Web HTTP 编程模型概述</span><span class="sxs-lookup"><span data-stu-id="43b43-141">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="43b43-142">WCF Web HTTP 编程对象模型</span><span class="sxs-lookup"><span data-stu-id="43b43-142">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
