---
title: WCF Web HTTP 编程模型概述
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: 34d7945b8a7898955794e2ad5813bc66f52b60c7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594928"
---
# <a name="wcf-web-http-programming-model-overview"></a><span data-ttu-id="05926-102">WCF Web HTTP 编程模型概述</span><span class="sxs-lookup"><span data-stu-id="05926-102">WCF Web HTTP Programming Model Overview</span></span>
<span data-ttu-id="05926-103">Windows Communication Foundation （WCF） WEB HTTP 编程模型提供了用 WCF 生成 WEB HTTP 服务所需的基本元素。</span><span class="sxs-lookup"><span data-stu-id="05926-103">The Windows Communication Foundation (WCF) WEB HTTP programming model provides the basic elements required to build WEB HTTP services with WCF.</span></span> <span data-ttu-id="05926-104">WCF WEB HTTP 服务旨在由最大范围的可能客户端（包括 Web 浏览器）访问，并且具有以下独特要求：</span><span class="sxs-lookup"><span data-stu-id="05926-104">WCF WEB HTTP services are designed to be accessed by the widest range of possible clients, including Web browsers and have the following unique requirements:</span></span>  
  
- <span data-ttu-id="05926-105">**Uri 和 Uri 处理**Uri 在 WEB HTTP 服务的设计中扮演着一个中心角色。</span><span class="sxs-lookup"><span data-stu-id="05926-105">**URIs and URI Processing** URIs play a central role in the design of WEB HTTP services.</span></span> <span data-ttu-id="05926-106">WCF WEB HTTP 编程模型使用 <xref:System.UriTemplate> 和 <xref:System.UriTemplateTable> 类来提供 URI 处理功能。</span><span class="sxs-lookup"><span data-stu-id="05926-106">The WCF WEB HTTP programming model uses the <xref:System.UriTemplate> and <xref:System.UriTemplateTable> classes to provide URI processing capabilities.</span></span>  
  
- <span data-ttu-id="05926-107">**支持 GET 和 POST 操作**WEB HTTP 服务除了使用各种调用谓词来进行数据修改和远程调用以外，还使用 GET 谓词进行数据检索。</span><span class="sxs-lookup"><span data-stu-id="05926-107">**Support for GET and POST operations** WEB HTTP services make use of the GET verb for data retrieval, in addition to various invoke verbs for data modification and remote invocation.</span></span> <span data-ttu-id="05926-108">WCF WEB HTTP 编程模型使用 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 将服务操作与 GET 和其他 HTTP 谓词（如 PUT、POST 和 DELETE）相关联。</span><span class="sxs-lookup"><span data-stu-id="05926-108">The WCF WEB HTTP programming model uses the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> to associate service operations with both GET and other HTTP verbs like PUT, POST, and DELETE.</span></span>  
  
- <span data-ttu-id="05926-109">**多种数据格式**除了 SOAP 消息以外，Web 样式服务还处理多种类型的数据。</span><span class="sxs-lookup"><span data-stu-id="05926-109">**Multiple data formats** Web-style services process many kinds of data in addition to SOAP messages.</span></span> <span data-ttu-id="05926-110">WCF WEB HTTP 编程模型使用 <xref:System.ServiceModel.WebHttpBinding> 和 <xref:System.ServiceModel.Description.WebHttpBehavior> 来支持多种不同的数据格式，包括 XML 文档、JSON 数据对象和二进制内容（如图像、视频文件或纯文本）的流。</span><span class="sxs-lookup"><span data-stu-id="05926-110">The WCF WEB HTTP programming model uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> to support many different data formats including XML documents, JSON data object, and streams of binary content such as images, video files, or plain text.</span></span>  
  
 <span data-ttu-id="05926-111">WCF WEB HTTP 编程模型扩展了 WCF 的覆盖范围，以涵盖包括 WEB HTTP 服务、AJAX 和 JSON 服务以及联合（ATOM/RSS）源的 Web 样式方案。</span><span class="sxs-lookup"><span data-stu-id="05926-111">The WCF WEB HTTP programming model extends the reach of WCF to cover Web-style scenarios that include WEB HTTP services, AJAX and JSON services, and Syndication (ATOM/RSS) feeds.</span></span> <span data-ttu-id="05926-112">有关 AJAX 和 JSON 服务的详细信息，请参阅[Ajax 集成和 Json 支持](ajax-integration-and-json-support.md)。</span><span class="sxs-lookup"><span data-stu-id="05926-112">For more information about AJAX and JSON services, see [AJAX Integration and JSON Support](ajax-integration-and-json-support.md).</span></span> <span data-ttu-id="05926-113">有关联合的详细信息，请参阅[WCF 联合概述](wcf-syndication-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="05926-113">For more information about Syndication, see [WCF Syndication Overview](wcf-syndication-overview.md).</span></span>  
  
 <span data-ttu-id="05926-114">对于可从 WEB HTTP 服务返回的数据的类型没有额外的限制。</span><span class="sxs-lookup"><span data-stu-id="05926-114">There are no extra restrictions on the types of data that can be returned from a WEB HTTP service.</span></span> <span data-ttu-id="05926-115">任何可序列化类型都可以从 WEB HTTP 服务操作返回。</span><span class="sxs-lookup"><span data-stu-id="05926-115">Any serializable type can be returned from an WEB HTTP service operation.</span></span> <span data-ttu-id="05926-116">因为 WEB HTTP 服务操作可以通过 Web 浏览器调用，所以对可在 URL 中指定的数据类型有一个限制。</span><span class="sxs-lookup"><span data-stu-id="05926-116">Because WEB HTTP service operations can be invoke by a web browser there is a limitation on what data types can be specified in a URL.</span></span> <span data-ttu-id="05926-117">有关默认情况下支持的类型的详细信息，请参阅下面的**UriTemplate 查询字符串参数和 url**部分。</span><span class="sxs-lookup"><span data-stu-id="05926-117">For more information on what types are supported by default see the **UriTemplate Query String Parameters and URLs** section below.</span></span> <span data-ttu-id="05926-118">通过提供您自己的 T:System.ServiceModel.Dispatcher.QueryStringConverter 实现来指定如何将 URL 中指定的参数转换为实际参数类型，可以更改默认行为。</span><span class="sxs-lookup"><span data-stu-id="05926-118">The default behavior can be changed by providing your own T:System.ServiceModel.Dispatcher.QueryStringConverter implementation which specifies how to convert the parameters specified in a URL to the actual parameter type.</span></span> <span data-ttu-id="05926-119">有关详细信息，请参阅<xref:System.ServiceModel.Dispatcher.QueryStringConverter></span><span class="sxs-lookup"><span data-stu-id="05926-119">For more information, see <xref:System.ServiceModel.Dispatcher.QueryStringConverter></span></span>  
  
> [!CAUTION]
> <span data-ttu-id="05926-120">使用 WCF WEB HTTP 编程模型编写的服务不使用 SOAP 消息。</span><span class="sxs-lookup"><span data-stu-id="05926-120">Services written with the WCF WEB HTTP programming model do not use SOAP messages.</span></span> <span data-ttu-id="05926-121">由于不使用 SOAP，因此不能使用 WCF 提供的安全功能。</span><span class="sxs-lookup"><span data-stu-id="05926-121">Because SOAP is not used, the security features provided by WCF cannot be used.</span></span> <span data-ttu-id="05926-122">然而，您可以通过使用 HTTPS 承载服务来使用基于传输的安全性。</span><span class="sxs-lookup"><span data-stu-id="05926-122">You can, however use transport-based security by hosting your service with HTTPS.</span></span> <span data-ttu-id="05926-123">有关 WCF 安全的详细信息，请参阅[安全性概述](security-overview.md)</span><span class="sxs-lookup"><span data-stu-id="05926-123">For more information about WCF security, see [Security Overview](security-overview.md)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="05926-124">为 IIS 安装 WebDAV 扩展会导致 Web HTTP 服务返回 HTTP 405 错误，因为 WebDAV 扩展试图处理所有 PUT 请求。</span><span class="sxs-lookup"><span data-stu-id="05926-124">Installing the WebDAV extension for IIS can cause Web HTTP services to return an HTTP 405 error as the WebDAV extension attempts to handle all PUT requests.</span></span> <span data-ttu-id="05926-125">若要解决此问题，你可卸载 WebDAV 扩展或为网站禁用 WebDAV 扩展。</span><span class="sxs-lookup"><span data-stu-id="05926-125">To work around this issue you can uninstall the WebDAV extension or disable the WebDAV extension for your web site.</span></span> <span data-ttu-id="05926-126">有关详细信息，请参阅[IIS 和 WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)</span><span class="sxs-lookup"><span data-stu-id="05926-126">For more information, see [IIS and WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)</span></span>  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a><span data-ttu-id="05926-127">使用 UriTemplate 和 UriTemplateTable 进行 URI 处理</span><span class="sxs-lookup"><span data-stu-id="05926-127">URI Processing with UriTemplate and UriTemplateTable</span></span>  
 <span data-ttu-id="05926-128">URI 模板提供了一种可以高效地表示很大的结构相似的 URI 集的语法。</span><span class="sxs-lookup"><span data-stu-id="05926-128">URI templates provide an efficient syntax for expressing large sets of structurally similar URIs.</span></span> <span data-ttu-id="05926-129">例如，下面的模板表示所有以“a”开始并以“c”结束而中间段的值不限的、由三个段组成的 URI：a/{segment}/c</span><span class="sxs-lookup"><span data-stu-id="05926-129">For example, the following template expresses the set of all three-segment URIs that begin with "a" and end with "c" without regard to the value of the intermediate segment: a/{segment}/c</span></span>  
  
 <span data-ttu-id="05926-130">此模板描述如下所示的 URI：</span><span class="sxs-lookup"><span data-stu-id="05926-130">This template describes URIs like the following:</span></span>  
  
- <span data-ttu-id="05926-131">a/x/c</span><span class="sxs-lookup"><span data-stu-id="05926-131">a/x/c</span></span>  
  
- <span data-ttu-id="05926-132">a/y/c</span><span class="sxs-lookup"><span data-stu-id="05926-132">a/y/c</span></span>  
  
- <span data-ttu-id="05926-133">a/z/c</span><span class="sxs-lookup"><span data-stu-id="05926-133">a/z/c</span></span>  
  
- <span data-ttu-id="05926-134">等等。</span><span class="sxs-lookup"><span data-stu-id="05926-134">and so on.</span></span>  
  
 <span data-ttu-id="05926-135">在此模板中，大括号表示法 ("{segment}") 指示变量段而不是文本值。</span><span class="sxs-lookup"><span data-stu-id="05926-135">In this template, the curly brace notation ("{segment}") indicates a variable segment instead of a literal value.</span></span>  
  
 <span data-ttu-id="05926-136">.NET Framework 提供了一个 API 来处理名为 <xref:System.UriTemplate> 的 URI 模板。</span><span class="sxs-lookup"><span data-stu-id="05926-136">.NET Framework provides an API for working with URI templates called <xref:System.UriTemplate>.</span></span> <span data-ttu-id="05926-137">`UriTemplates` 允许执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="05926-137">`UriTemplates` allow you to do the following:</span></span>  
  
- <span data-ttu-id="05926-138">您可以 `Bind` 使用一组参数调用其中一个方法来生成与模板匹配的*完全关闭的 URI* 。</span><span class="sxs-lookup"><span data-stu-id="05926-138">You can call one of the `Bind` methods with a set of parameters to produce a *fully-closed URI* that matches the template.</span></span> <span data-ttu-id="05926-139">这意味着，URI 模板中的所有变量均由实际值替换。</span><span class="sxs-lookup"><span data-stu-id="05926-139">This means all variables within the URI template are replaced with actual values.</span></span>  
  
- <span data-ttu-id="05926-140">可以使用候选 URI 调用 `Match`()，此时会使用模板将候选 URI 的各个组成部分分解开来，并会返回一个字典，其中包含根据模板中的变量标记的 URI 的不同部分。</span><span class="sxs-lookup"><span data-stu-id="05926-140">You can call `Match`() with a candidate URI, which uses a template to break up a candidate URI into its constituent parts and returns a dictionary that contains the different parts of the URI labeled according to the variables in the template.</span></span>  
  
- <span data-ttu-id="05926-141">`Bind`() 和 `Match`() 互为逆方法，因此可以调用 `Match`( `Bind`( x ) ) 并返回到开始时的相同环境。</span><span class="sxs-lookup"><span data-stu-id="05926-141">`Bind`() and `Match`() are inverses so that you can call `Match`( `Bind`( x ) ) and come back with the same environment you started with.</span></span>  
  
 <span data-ttu-id="05926-142">在很多时候（尤其是在服务器需要基于 URI 将请求调度到某个服务操作时），对于那些可以单独对包含的每个模板进行寻址的数据结构，您需要一直跟踪其中的一组 <xref:System.UriTemplate> 对象。</span><span class="sxs-lookup"><span data-stu-id="05926-142">There are many times (especially on the server, where dispatching a request to a service operation based on the URI is necessary) that you want to keep track of a set of <xref:System.UriTemplate> objects in a data structure that can independently address each of the contained templates.</span></span> <span data-ttu-id="05926-143"><xref:System.UriTemplateTable> 表示一组 URI 模板，并在给定的一组模板和候选 URI 中选择最匹配的项。</span><span class="sxs-lookup"><span data-stu-id="05926-143"><xref:System.UriTemplateTable> represents a set of URI templates and selects the best match given a set of templates and a candidate URI.</span></span> <span data-ttu-id="05926-144">这并不隶属于任何特定的网络堆栈（包括 WCF），因此可以在必要时使用。</span><span class="sxs-lookup"><span data-stu-id="05926-144">This is not affiliated with any particular networking stack (WCF included) so you can use it wherever necessary.</span></span>  
  
 <span data-ttu-id="05926-145">WCF 服务模型使用 <xref:System.UriTemplate> 和 <xref:System.UriTemplateTable> 将服务操作与由 <xref:System.UriTemplate> 描述的一组 URI 相关联。</span><span class="sxs-lookup"><span data-stu-id="05926-145">The WCF Service Model makes use of <xref:System.UriTemplate> and <xref:System.UriTemplateTable> to associate service operations with a set of URIs described by a <xref:System.UriTemplate>.</span></span> <span data-ttu-id="05926-146">通过使用 <xref:System.UriTemplate> 或 <xref:System.ServiceModel.Web.WebGetAttribute>，将服务操作与 <xref:System.ServiceModel.Web.WebInvokeAttribute> 相关联。</span><span class="sxs-lookup"><span data-stu-id="05926-146">A service operation is associated with a <xref:System.UriTemplate>, using either the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="05926-147">有关和的详细 <xref:System.UriTemplate> 信息 <xref:System.UriTemplateTable> ，请参阅[UriTemplate 和 UriTemplateTable](uritemplate-and-uritemplatetable.md)</span><span class="sxs-lookup"><span data-stu-id="05926-147">For more information about <xref:System.UriTemplate> and <xref:System.UriTemplateTable>, see [UriTemplate and UriTemplateTable](uritemplate-and-uritemplatetable.md)</span></span>  
  
## <a name="webget-and-webinvoke-attributes"></a><span data-ttu-id="05926-148">WebGet 和 WebInvoke 特性</span><span class="sxs-lookup"><span data-stu-id="05926-148">WebGet and WebInvoke Attributes</span></span>  
 <span data-ttu-id="05926-149">WCF WEB HTTP 服务除了使用各种调用谓词（例如 HTTP POST、PUT 和 DELETE）之外，还使用检索谓词（例如 HTTP GET）。</span><span class="sxs-lookup"><span data-stu-id="05926-149">WCF WEB HTTP services make use of retrieval verbs (for example HTTP GET) in addition to various invoke verbs (for example HTTP POST, PUT, and DELETE).</span></span> <span data-ttu-id="05926-150">WCF WEB HTTP 编程模型允许服务开发人员通过和控制与其服务操作相关联的 URI 模板和谓词 <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="05926-150">The WCF WEB HTTP programming model allows service developers to control the both the URI template and verb associated with their service operations with the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="05926-151">可以使用 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 来控制各个操作如何绑定到 URI 以及与这些 URI 相关联的 HTTP 方法。</span><span class="sxs-lookup"><span data-stu-id="05926-151">The <xref:System.ServiceModel.Web.WebGetAttribute> and the <xref:System.ServiceModel.Web.WebInvokeAttribute> allow you to control how individual operations get bound to URIs and the HTTP methods associated with those URIs.</span></span> <span data-ttu-id="05926-152">例如，在下面的代码中添加 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute>。</span><span class="sxs-lookup"><span data-stu-id="05926-152">For example, adding <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> in the following code.</span></span>  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,
                               string newName );  
}  
```  
  
 <span data-ttu-id="05926-153">可以使用上面的代码生成下面的 HTTP 请求。</span><span class="sxs-lookup"><span data-stu-id="05926-153">The preceding code allows you to make the following HTTP requests.</span></span>  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <span data-ttu-id="05926-154"><xref:System.ServiceModel.Web.WebInvokeAttribute> 的默认值为 POST，但也可以将其用于其他谓词。</span><span class="sxs-lookup"><span data-stu-id="05926-154"><xref:System.ServiceModel.Web.WebInvokeAttribute> defaults to POST but you can use it for other verbs too.</span></span>  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 <span data-ttu-id="05926-155">若要查看使用 WCF WEB HTTP 编程模型的 WCF 服务的完整示例，请参阅[如何：创建基本 WCF WEB Http 服务](how-to-create-a-basic-wcf-web-http-service.md)</span><span class="sxs-lookup"><span data-stu-id="05926-155">To see a complete sample of a WCF service that uses the WCF WEB HTTP programming model, see [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md)</span></span>  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a><span data-ttu-id="05926-156">UriTemplate 查询字符串参数和 URL</span><span class="sxs-lookup"><span data-stu-id="05926-156">UriTemplate Query String Parameters and URLs</span></span>  
 <span data-ttu-id="05926-157">可以通过键入与服务操作相关联的 URL 来从 Web 浏览器调用 Web 样式服务。</span><span class="sxs-lookup"><span data-stu-id="05926-157">Web-style services can be called from a Web browser by typing a URL that is associated with a service operation.</span></span> <span data-ttu-id="05926-158">这些服务操作可以采用查询字符串参数，必须在 URL 内使用字符串格式指定这些参数。</span><span class="sxs-lookup"><span data-stu-id="05926-158">These service operations may take query string parameters that must be specified in a string form within the URL.</span></span> <span data-ttu-id="05926-159">下表演示可以在 URL 内传递的类型和使用的格式。</span><span class="sxs-lookup"><span data-stu-id="05926-159">The following table shows the types that can be passed within a URL and the format used.</span></span>  
  
|<span data-ttu-id="05926-160">类型</span><span class="sxs-lookup"><span data-stu-id="05926-160">Type</span></span>|<span data-ttu-id="05926-161">格式</span><span class="sxs-lookup"><span data-stu-id="05926-161">Format</span></span>|  
|----------|------------|  
|<xref:System.Byte>|<span data-ttu-id="05926-162">0 - 255</span><span class="sxs-lookup"><span data-stu-id="05926-162">0 - 255</span></span>|  
|<xref:System.SByte>|<span data-ttu-id="05926-163">-128 - 127</span><span class="sxs-lookup"><span data-stu-id="05926-163">-128 - 127</span></span>|  
|<xref:System.Int16>|<span data-ttu-id="05926-164">-32768 - 32767</span><span class="sxs-lookup"><span data-stu-id="05926-164">-32768 - 32767</span></span>|  
|<xref:System.Int32>|<span data-ttu-id="05926-165">-2,147,483,648 - 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="05926-165">-2,147,483,648 - 2,147,483,647</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="05926-166">-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="05926-166">-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807</span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="05926-167">0 - 65535</span><span class="sxs-lookup"><span data-stu-id="05926-167">0 - 65535</span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="05926-168">0 - 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="05926-168">0 - 4,294,967,295</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="05926-169">0 - 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="05926-169">0 - 18,446,744,073,709,551,615</span></span>|  
|<xref:System.Single>|<span data-ttu-id="05926-170">-3.402823e38 - 3.402823e38（不需要指数表示法）</span><span class="sxs-lookup"><span data-stu-id="05926-170">-3.402823e38 - 3.402823e38 (exponent notation is not required)</span></span>|  
|<xref:System.Double>|<span data-ttu-id="05926-171">-1.79769313486232e308 - 1.79769313486232e308（不需要指数表示法）</span><span class="sxs-lookup"><span data-stu-id="05926-171">-1.79769313486232e308 - 1.79769313486232e308 (exponent notation is not required)</span></span>|  
|<xref:System.Char>|<span data-ttu-id="05926-172">任何单个字符</span><span class="sxs-lookup"><span data-stu-id="05926-172">Any single character</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="05926-173">使用标准表示法的任何小数（无指数）</span><span class="sxs-lookup"><span data-stu-id="05926-173">Any decimal in standard notation (no exponent)</span></span>|  
|<xref:System.Boolean>|<span data-ttu-id="05926-174">True 或 False（不区分大小写）</span><span class="sxs-lookup"><span data-stu-id="05926-174">True or False (case insensitive)</span></span>|  
|<xref:System.String>|<span data-ttu-id="05926-175">任何字符串（不支持空字符串，且不进行转义）</span><span class="sxs-lookup"><span data-stu-id="05926-175">Any string (null string is not supported and no escaping is done)</span></span>|  
|<xref:System.DateTime>|<span data-ttu-id="05926-176">MM/DD/YYYY</span><span class="sxs-lookup"><span data-stu-id="05926-176">MM/DD/YYYY</span></span><br /><br /> <span data-ttu-id="05926-177">MM/DD/YYYY HH： MM： SS [AM&#124;PM]</span><span class="sxs-lookup"><span data-stu-id="05926-177">MM/DD/YYYY HH:MM:SS [AM&#124;PM]</span></span><br /><br /> <span data-ttu-id="05926-178">月、日、年</span><span class="sxs-lookup"><span data-stu-id="05926-178">Month Day Year</span></span><br /><br /> <span data-ttu-id="05926-179">月份日期年 HH： MM： SS [AM&#124;PM]</span><span class="sxs-lookup"><span data-stu-id="05926-179">Month Day Year HH:MM:SS [AM&#124;PM]</span></span>|  
|<xref:System.TimeSpan>|<span data-ttu-id="05926-180">DD.HH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="05926-180">DD.HH:MM:SS</span></span><br /><br /> <span data-ttu-id="05926-181">此处，DD = 天、HH = 小时、MM = 分钟、SS = 秒钟</span><span class="sxs-lookup"><span data-stu-id="05926-181">Where DD = Days, HH = Hours, MM = minutes, SS = Seconds</span></span>|  
|<xref:System.Guid>|<span data-ttu-id="05926-182">一个 GUID，例如：</span><span class="sxs-lookup"><span data-stu-id="05926-182">A GUID, for example:</span></span><br /><br /> <span data-ttu-id="05926-183">936DA01F-9ABD-4d9d-80C7-02AF85C822A8</span><span class="sxs-lookup"><span data-stu-id="05926-183">936DA01F-9ABD-4d9d-80C7-02AF85C822A8</span></span>|  
|<xref:System.DateTimeOffset>|<span data-ttu-id="05926-184">MM/DD/YYYY HH:MM:SS MM:SS</span><span class="sxs-lookup"><span data-stu-id="05926-184">MM/DD/YYYY HH:MM:SS MM:SS</span></span><br /><br /> <span data-ttu-id="05926-185">此处，DD = 天、HH = 小时、MM = 分钟、SS = 秒钟</span><span class="sxs-lookup"><span data-stu-id="05926-185">Where DD = Days, HH = Hours, MM = minutes, SS = Seconds</span></span>|  
|<span data-ttu-id="05926-186">枚举</span><span class="sxs-lookup"><span data-stu-id="05926-186">Enumerations</span></span>|<span data-ttu-id="05926-187">例如，定义枚举的枚举值，如以下代码中所示。</span><span class="sxs-lookup"><span data-stu-id="05926-187">The enumeration value for example, which defines the enumeration as shown in the following code.</span></span><br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> <span data-ttu-id="05926-188">可以在查询字符串中指定任何单独的枚举值（或其对应的整数值）。</span><span class="sxs-lookup"><span data-stu-id="05926-188">Any of the individual enumeration values (or their corresponding integer values) may be specified in the query string.</span></span>|  
|<span data-ttu-id="05926-189">具有可在类型和字符串表示形式之间来回进行转换的 `TypeConverterAttribute` 的类型。</span><span class="sxs-lookup"><span data-stu-id="05926-189">Types that have a `TypeConverterAttribute` that can convert the type to and from a string representation.</span></span>|<span data-ttu-id="05926-190">取决于类型转换器。</span><span class="sxs-lookup"><span data-stu-id="05926-190">Depends on the Type Converter.</span></span>|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a><span data-ttu-id="05926-191">格式和 WCF WEB HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="05926-191">Formats and the WCF WEB HTTP Programming Model</span></span>  
 <span data-ttu-id="05926-192">WCF WEB HTTP 编程模型具有用于处理多种不同数据格式的新功能。</span><span class="sxs-lookup"><span data-stu-id="05926-192">The WCF WEB HTTP programming model has new features to work with many different data formats.</span></span> <span data-ttu-id="05926-193">在绑定层上，<xref:System.ServiceModel.WebHttpBinding> 可以读取和写入下列不同种类的数据：</span><span class="sxs-lookup"><span data-stu-id="05926-193">At the binding layer, the <xref:System.ServiceModel.WebHttpBinding> can read and write the following different kinds of data:</span></span>  
  
- <span data-ttu-id="05926-194">XML</span><span class="sxs-lookup"><span data-stu-id="05926-194">XML</span></span>  
  
- <span data-ttu-id="05926-195">JSON</span><span class="sxs-lookup"><span data-stu-id="05926-195">JSON</span></span>  
  
- <span data-ttu-id="05926-196">不透明二进制流</span><span class="sxs-lookup"><span data-stu-id="05926-196">Opaque binary streams</span></span>  
  
 <span data-ttu-id="05926-197">这意味着 WCF WEB HTTP 编程模型可以处理任何类型的数据，但您可能会对进行编程 <xref:System.IO.Stream> 。</span><span class="sxs-lookup"><span data-stu-id="05926-197">This means the WCF WEB HTTP programming model can handle any type of data but, you may be programming against <xref:System.IO.Stream>.</span></span>  
  
 <span data-ttu-id="05926-198">.NET Framework 3.5 支持 JSON 数据（AJAX）和联合源（包括 ATOM 和 RSS）。</span><span class="sxs-lookup"><span data-stu-id="05926-198">.NET Framework 3.5 provides support for JSON data (AJAX) as well as Syndication feeds (including ATOM and RSS).</span></span> <span data-ttu-id="05926-199">有关这些功能的详细信息，请参阅[Wcf WEB HTTP 格式设置](wcf-web-http-formatting.md)、 [wcf 联合概述](wcf-syndication-overview.md)以及[AJAX 集成和 JSON 支持](ajax-integration-and-json-support.md)。</span><span class="sxs-lookup"><span data-stu-id="05926-199">For more information about these features, see [WCF Web HTTP Formatting](wcf-web-http-formatting.md), [WCF Syndication Overview](wcf-syndication-overview.md), and [AJAX Integration and JSON Support](ajax-integration-and-json-support.md).</span></span>  
  
## <a name="wcf-web-http-programming-model-and-security"></a><span data-ttu-id="05926-200">WCF WEB HTTP 编程模型和安全</span><span class="sxs-lookup"><span data-stu-id="05926-200">WCF WEB HTTP Programming Model and Security</span></span>  

<span data-ttu-id="05926-201">由于 WCF WEB HTTP 编程模型不支持 WS-\* 协议，因此保证 WCF WEB HTTP 服务安全的唯一方式是使用 SSL 通过 HTTPS 公开服务。</span><span class="sxs-lookup"><span data-stu-id="05926-201">Because the WCF WEB HTTP programming model does not support the WS-\* protocols, the only way to secure a WCF WEB HTTP service is to expose the service over HTTPS using SSL.</span></span> <span data-ttu-id="05926-202">有关设置 SSL 和 IIS 7.0 的详细信息，请参阅[如何在 iis 中实现 ssl](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis)。</span><span class="sxs-lookup"><span data-stu-id="05926-202">For more information about setting up SSL with IIS 7.0, see [How to implement SSL in IIS](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis).</span></span>
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a><span data-ttu-id="05926-203">WCF WEB HTTP 编程模型疑难解答</span><span class="sxs-lookup"><span data-stu-id="05926-203">Troubleshooting the WCF WEB HTTP Programming Model</span></span>  
 <span data-ttu-id="05926-204">当使用 <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> 调用 WCF WEB HTTP 服务以创建通道时，即使将其他 <xref:System.ServiceModel.Description.WebHttpBehavior> 传递给 <xref:System.ServiceModel.EndpointAddress>，<xref:System.ServiceModel.EndpointAddress> 也会使用配置文件中设置的 <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>。</span><span class="sxs-lookup"><span data-stu-id="05926-204">When calling WCF WEB HTTP services using a <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> to create a channel, the <xref:System.ServiceModel.Description.WebHttpBehavior> uses the <xref:System.ServiceModel.EndpointAddress> set in the configuration file even if a different <xref:System.ServiceModel.EndpointAddress> is passed to the <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05926-205">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05926-205">See also</span></span>

- [<span data-ttu-id="05926-206">WCF 联合</span><span class="sxs-lookup"><span data-stu-id="05926-206">WCF Syndication</span></span>](wcf-syndication.md)
- [<span data-ttu-id="05926-207">WCF Web HTTP 编程对象模型</span><span class="sxs-lookup"><span data-stu-id="05926-207">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="05926-208">WCF Web HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="05926-208">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
