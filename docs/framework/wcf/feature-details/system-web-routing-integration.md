---
title: System.Web.Routing 集成
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 6e67aa4a790edeb367b099d4a94f465f1e7b9bcc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554770"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="210f6-102">System.Web.Routing 集成</span><span class="sxs-lookup"><span data-stu-id="210f6-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="210f6-103">在 Internet 信息服务 () IIS 中承载 Windows Communication Foundation (WCF) 服务时，会将 .svc 文件放在虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="210f6-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="210f6-104">此 .svc 文件指定所用的服务主机工厂以及实现服务的类。</span><span class="sxs-lookup"><span data-stu-id="210f6-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="210f6-105">向服务发出请求时，请在 URI 中指定 .svc 文件，例如： `http://contoso.com/EmployeeServce.svc` 。</span><span class="sxs-lookup"><span data-stu-id="210f6-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="210f6-106">对于编写 REST 服务的程序员，此类型的 URI 并非最佳选择。</span><span class="sxs-lookup"><span data-stu-id="210f6-106">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="210f6-107">REST 服务的 URI 指定了特定资源，通常没有任何扩展。</span><span class="sxs-lookup"><span data-stu-id="210f6-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="210f6-108"><xref:System.Web.Routing>集成功能允许托管 WCF REST 服务，该服务在没有扩展的情况下响应 uri。</span><span class="sxs-lookup"><span data-stu-id="210f6-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="210f6-109">有关路由的详细信息，请参阅 [ASP.NET 路由](/previous-versions/aspnet/cc668201(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="210f6-109">For more information about routing see [ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="210f6-110">使用 System.Web.Routing 集成</span><span class="sxs-lookup"><span data-stu-id="210f6-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="210f6-111">若要使用 <xref:System.Web.Routing> 集成功能，请使用 <xref:System.ServiceModel.Activation.ServiceRoute> 类创建一个或多个路由，然后将这些路由添加到 Global.asax 文件中的 <xref:System.Web.Routing.RouteTable>。</span><span class="sxs-lookup"><span data-stu-id="210f6-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="210f6-112">这些路由可指定服务所响应的相对 URI。</span><span class="sxs-lookup"><span data-stu-id="210f6-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="210f6-113">以下示例演示如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="210f6-113">The following example shows how to do this.</span></span>  
  
```aspx-csharp  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));
   }  
</script>  
```  
  
 <span data-ttu-id="210f6-114">这示例将具有以 Customers 开头的相对 URI 的所有请求路由到 `Service` 服务。</span><span class="sxs-lookup"><span data-stu-id="210f6-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="210f6-115">在 Web.config 文件中，必须添加 `System.Web.Routing.UrlRoutingModule` 模块，将 `runAllManagedModulesForAllRequests` 特性设置为 `true`，以及将 `UrlRoutingHandler` 处理程序添加到 `<system.webServer>` 元素，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="210f6-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 <span data-ttu-id="210f6-116">此示例将加载路由所需的模块和处理程序。</span><span class="sxs-lookup"><span data-stu-id="210f6-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="210f6-117">有关详细信息，请参阅[路由](routing.md)。</span><span class="sxs-lookup"><span data-stu-id="210f6-117">For more information, see [Routing](routing.md).</span></span> <span data-ttu-id="210f6-118">另外，还必须在 `aspNetCompatibilityEnabled` 元素中将 `true` 特性设置为 `<serviceHostingEnvironment>`，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="210f6-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="210f6-119">实现该服务的类必须启用 ASP.NET 兼容性需求，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="210f6-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="210f6-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="210f6-120">See also</span></span>

- [<span data-ttu-id="210f6-121">WCF Web HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="210f6-121">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- <span data-ttu-id="210f6-122">[ASP.NET 路由](/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="210f6-122">[ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
