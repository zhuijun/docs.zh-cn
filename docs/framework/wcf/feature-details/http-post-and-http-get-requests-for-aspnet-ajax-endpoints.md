---
title: 如何：在 ASP.NET AJAX 终结点的 HTTP POST 和 HTTP GET 请求之间进行选择
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: c74b1acdf3802ab680123cd9d676919fe47236e8
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051579"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="1605c-102">如何：在 ASP.NET AJAX 终结点的 HTTP POST 和 HTTP GET 请求之间进行选择</span><span class="sxs-lookup"><span data-stu-id="1605c-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="1605c-103">Windows Communication Foundation （WCF）允许您创建一个服务，用于公开可从客户端网站上的 JavaScript 中调用的 ASP.NET 支持 AJAX 的终结点。</span><span class="sxs-lookup"><span data-stu-id="1605c-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="1605c-104">有关生成此类服务的基本过程，[请参见如何：使用配置添加 ASP.NET Ajax 终结点](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)和[如何：在不使用配置的情况下添加 ASP.NET ajax 终结点](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="1605c-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="1605c-105">ASP.NET AJAX 支持使用 HTTP POST 和 HTTP GET 谓词（HTTP POST 为默认谓词）的操作。</span><span class="sxs-lookup"><span data-stu-id="1605c-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="1605c-106">创建没有任何副作用并返回很少或从不进行更改的数据的操作时，应改用 HTTP GET。</span><span class="sxs-lookup"><span data-stu-id="1605c-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="1605c-107">GET 操作的结果可以缓存，这意味着对相同操作的多次调用可能导致只请求一次服务。</span><span class="sxs-lookup"><span data-stu-id="1605c-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="1605c-108">缓存不是由 WCF 完成，但可以在任何级别（在用户的浏览器中、代理服务器上以及其他级别）进行。如果你想要提高服务性能，但如果经常更改数据或操作执行某些操作，则缓存将非常有利。</span><span class="sxs-lookup"><span data-stu-id="1605c-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="1605c-109">例如，如果设计服务来管理用户的音乐库，则基于唱片集的标题查找艺术家的操作可以从使用 GET 中获益，但是将唱片集添加到用户的个人收藏集的操作必须使用 POST。</span><span class="sxs-lookup"><span data-stu-id="1605c-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="1605c-110">若要控制缓存的生存期，请使用 <xref:System.ServiceModel.Web.OutgoingWebResponseContext> 类型。</span><span class="sxs-lookup"><span data-stu-id="1605c-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="1605c-111">例如，在设计返回每小时更新的天气预报时会使用 GET，但应将缓存持续时间限制在一小时以内，以防止服务的用户访问过时的数据。</span><span class="sxs-lookup"><span data-stu-id="1605c-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="1605c-112">在使用来自使用脚本管理器控件的 ASP.NET AJAX 页上的服务时，操作是使用 GET 还是 POST 并没有区别，脚本管理器机制会确保发出正确的请求类型。</span><span class="sxs-lookup"><span data-stu-id="1605c-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="1605c-113">HTTP GET 操作使用由 POST 操作支持的任何输入参数，其中包括复杂的数据协定类型。</span><span class="sxs-lookup"><span data-stu-id="1605c-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="1605c-114">但是，大多数情况下建议避免在 GET 操作中使用太多的参数或太复杂的参数，原因是这样会降低缓存的效率。</span><span class="sxs-lookup"><span data-stu-id="1605c-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="1605c-115">本主题演示了如何通过在服务协定中将 <xref:System.ServiceModel.Web.WebGetAttribute> 或 <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性添加到相关的操作以在 GET 和 POST 之间选择。</span><span class="sxs-lookup"><span data-stu-id="1605c-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="1605c-116">运行服务所需的其他步骤（若要实现、配置和托管服务）与 WCF 中任何 ASP.NET AJAX 服务使用的步骤类似。</span><span class="sxs-lookup"><span data-stu-id="1605c-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="1605c-117">以 <xref:System.ServiceModel.Web.WebGetAttribute> 标记的操作始终使用 GET 请求。</span><span class="sxs-lookup"><span data-stu-id="1605c-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="1605c-118">以 <xref:System.ServiceModel.Web.WebInvokeAttribute> 标记或未以这两个属性中的任何一个进行标记的操作将使用 POST 请求。</span><span class="sxs-lookup"><span data-stu-id="1605c-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="1605c-119">通过 <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性，<xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> 允许使用 GET 和 POST 之外的其他 HTTP 谓词（如 PUT 和 DELETE 等）。</span><span class="sxs-lookup"><span data-stu-id="1605c-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="1605c-120">但是，ASP.NET AJAX 不支持这些谓词。</span><span class="sxs-lookup"><span data-stu-id="1605c-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="1605c-121">如果打算使用脚本管理器控件来使用来自 ASP.NET 页上的服务，请不要使用 <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="1605c-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="1605c-122">有关切换到 GET 的工作示例，请参阅[基本 AJAX 服务](../samples/basic-ajax-service.md)示例。</span><span class="sxs-lookup"><span data-stu-id="1605c-122">For a working example of switching to GET, see the [Basic AJAX Service](../samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="1605c-123">有关使用 POST 的示例，请参阅[使用 HTTP post 的 AJAX 服务](../samples/ajax-service-using-http-post.md)示例。</span><span class="sxs-lookup"><span data-stu-id="1605c-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="1605c-124">创建响应 HTTP GET 或 HTTP POST 请求的 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="1605c-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="1605c-125">使用以特性标记的接口定义基本 WCF 服务协定 <xref:System.ServiceModel.ServiceContractAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="1605c-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="1605c-126">用 <xref:System.ServiceModel.OperationContractAttribute> 标记每个操作。</span><span class="sxs-lookup"><span data-stu-id="1605c-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="1605c-127">添加 <xref:System.ServiceModel.Web.WebGetAttribute> 属性以规定操作应响应 HTTP GET 请求。</span><span class="sxs-lookup"><span data-stu-id="1605c-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="1605c-128">也可以添加 <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性来显式指定 HTTP POST，或不指定属性（默认设置为 HTTP POST）。</span><span class="sxs-lookup"><span data-stu-id="1605c-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
    ```csharp
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="1605c-129">使用 `IMusicService` 实现 `MusicService` 服务协定。</span><span class="sxs-lookup"><span data-stu-id="1605c-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
    ```csharp
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3. <span data-ttu-id="1605c-130">在应用程序中创建一个名为 service 的新文件（扩展名为 .svc）。</span><span class="sxs-lookup"><span data-stu-id="1605c-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="1605c-131">通过为服务添加适当的[ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md)指令信息来编辑此文件。</span><span class="sxs-lookup"><span data-stu-id="1605c-131">Edit this file by adding the appropriate [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="1605c-132">指定 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 要在[ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md)指令中使用以便自动配置 ASP.NET AJAX 终结点。</span><span class="sxs-lookup"><span data-stu-id="1605c-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```aspx-csharp
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="1605c-133">调用服务</span><span class="sxs-lookup"><span data-stu-id="1605c-133">To call the service</span></span>  
  
1. <span data-ttu-id="1605c-134">可以通过使用浏览器来测试服务的 GET 操作，而无需使用任何客户端代码。</span><span class="sxs-lookup"><span data-stu-id="1605c-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="1605c-135">例如，如果你的服务是在地址配置的 `http://example.com/service.svc` ，则在 `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` 浏览器地址栏中键入会调用服务，并使响应被下载或显示。</span><span class="sxs-lookup"><span data-stu-id="1605c-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="1605c-136">可以像使用任何其他 ASP.NET AJAX 服务一样将服务与 GET 操作一起使用，即，在 ASP.NET AJAX 脚本管理器控件的“脚本”集合中输入相应的服务 URL。</span><span class="sxs-lookup"><span data-stu-id="1605c-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="1605c-137">有关示例，请参阅[基本 AJAX 服务](../samples/basic-ajax-service.md)。</span><span class="sxs-lookup"><span data-stu-id="1605c-137">For an example, see the [Basic AJAX Service](../samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1605c-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="1605c-138">See also</span></span>

- [<span data-ttu-id="1605c-139">为 ASP.NET AJAX 创建 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="1605c-139">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="1605c-140">如何：将支持 AJAX 的 ASP.NET Web 服务迁移到 WCF</span><span class="sxs-lookup"><span data-stu-id="1605c-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
