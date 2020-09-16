---
title: 对 WCF Web HTTP 服务的缓存支持
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 0445f0214f90873dad4241789db270c9b6f4a2f6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559410"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="e5cfe-102">对 WCF Web HTTP 服务的缓存支持</span><span class="sxs-lookup"><span data-stu-id="e5cfe-102">Caching Support for WCF Web HTTP Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="e5cfe-103">使你能够使用 WCF Web HTTP 服务的 ASP.NET 中已有的声明性缓存机制。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-103">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="e5cfe-104">这样，你可以缓存来自 WCF Web HTTP 服务操作的响应。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="e5cfe-105">如果用户向配置为进行缓存的服务发送了 HTTP GET，ASP.NET 将发送回已缓存的响应且不会调用服务方法。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="e5cfe-106">在缓存过期后，下次用户发送 HTTP GET 时，将会调用服务方法且再次缓存响应。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="e5cfe-107">有关 ASP.NET 缓存的详细信息，请参阅 [ASP.NET 缓存概述](/previous-versions/aspnet/ms178597(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](/previous-versions/aspnet/ms178597(v=vs.100)).</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="e5cfe-108">基本 Web HTTP 服务缓存</span><span class="sxs-lookup"><span data-stu-id="e5cfe-108">Basic Web HTTP Service Caching</span></span>  

  <span data-ttu-id="e5cfe-109">若要启用 WEB HTTP 服务缓存，必须首先通过将应用 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 于服务设置为或，启用 ASP.NET 兼容性 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required> 。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-109">To enable WEB HTTP service caching, you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="e5cfe-110">.NET Framework 4 引入了一个名为 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 的新属性，该属性允许你指定缓存配置文件名称。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-110">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="e5cfe-111">此特性适用于服务操作。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="e5cfe-112">下面的示例将 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 应用到服务以启用 ASP.NET 兼容性，并配置 `GetCustomer` 操作以进行缓存。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="e5cfe-113"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 特性指定包含要使用的缓存设置的缓存配置文件。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
```csharp
[ServiceContract]
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
<span data-ttu-id="e5cfe-114">同时在 Web.config 文件中打开 ASP.NET 兼容模式，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-114">Also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="e5cfe-115">如果未启用 ASP.NET 兼容模式且使用了 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="e5cfe-116"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 所指定的缓存配置文件名称标识已添加到 Web.config 配置文件的缓存配置文件。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="e5cfe-117">缓存配置文件在 <> 元素中定义， `outputCacheSetting` 如下面的配置示例所示。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="e5cfe-118">这是可供 ASP.NET 应用程序使用的同一配置元素。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="e5cfe-119">有关 ASP.NET 缓存配置文件的详细信息，请参阅 <xref:System.Web.Configuration.OutputCacheProfile> 。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="e5cfe-120">对于 Web HTTP 服务，缓存配置文件中最重要的特性是 `cacheDuration` 和 `varyByParam`。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="e5cfe-121">这两个特性都是必需的。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-121">Both of these attributes are required.</span></span> <span data-ttu-id="e5cfe-122">`cacheDuration` 以秒为单位设置应缓存响应的时间。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="e5cfe-123">`varyByParam` 允许您指定用于缓存响应的查询字符串参数。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="e5cfe-124">对于使用不同查询字符串参数值发出的所有请求，将单独进行缓存。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="e5cfe-125">例如，在对发出初始请求后 `http://MyServer/MyHttpService/MyOperation?param=10` ，只要缓存持续时间) ，就会将缓存的响应 (返回缓存的响应。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-125">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="e5cfe-126">对于形式相同但具有不同参数查询字符串参数值的类似请求的响应，将单独进行缓存。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="e5cfe-127">如果不需要此单独缓存行为，请将 `varyByParam` 设置为“无”。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="e5cfe-128">SQL 缓存依赖项</span><span class="sxs-lookup"><span data-stu-id="e5cfe-128">SQL Cache Dependency</span></span>  

  <span data-ttu-id="e5cfe-129">还可以跟随 SQL 缓存依赖项来缓存 Web HTTP 服务响应。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="e5cfe-130">如果 WCF Web HTTP 服务依赖于 SQL 数据库中存储的数据，则当 SQL 数据库表中的数据更改时，您可能希望缓存服务的响应并使已缓存的响应无效。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="e5cfe-131">此行为完全在 Web.config 文件中配置。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="e5cfe-132">首先，在 <> 元素中定义一个连接字符串 `connectionStrings` 。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-132">First, define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="e5cfe-133">然后，必须在 <> 元素内的 <> 元素内启用 SQL 缓存依赖关系 `caching` `system.web` ，如以下配置示例所示。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="e5cfe-134">此处启用了 SQL 缓存依赖项，并设置了 1000 毫秒的轮询时间。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="e5cfe-135">每当轮询时间结束时，都会检查数据库表是否有更新。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="e5cfe-136">如果检测到更改，则会删除缓存的内容，并且下次调用服务操作时将缓存新响应。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="e5cfe-137">在 <`sqlCacheDependency`> 元素中添加数据库，并在 <> 元素中引用连接字符串， `databases` 如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="e5cfe-138">接下来，必须在 <> 元素中配置输出缓存设置 `caching` ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="e5cfe-139">此处，"缓存持续时间" 设置为 "60 `varyByParam` "，设置为 "无"，并 `sqlDependency` 设置为以分号分隔的数据库名称/表对列表，以冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none, and `sqlDependency` is set to a semicolon-delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="e5cfe-140">当 `MyTable` 中的数据发生更改时，将删除服务操作的已缓存响应；当调用操作时，将生成新的响应（通过调用服务操作），缓存该响应并将其返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e5cfe-141">要使 ASP.NET 能够访问 SQL 数据库，必须使用 [ASP.NET SQL Server 注册工具](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span></span> <span data-ttu-id="e5cfe-142">此外，还必须允许适当的用户帐户对数据库和表具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="e5cfe-143">有关详细信息，请参阅 [从 Web 应用程序访问 SQL Server](/previous-versions/aspnet/ht43wsex(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-143">For more information, see [Accessing SQL Server from a Web Application](/previous-versions/aspnet/ht43wsex(v=vs.100)).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="e5cfe-144">基于条件 HTTP GET 的缓存</span><span class="sxs-lookup"><span data-stu-id="e5cfe-144">Conditional HTTP GET Based Caching</span></span>  

  <span data-ttu-id="e5cfe-145">在 Web HTTP 方案中，服务通常使用条件 HTTP GET 来实现智能 HTTP 缓存，如 [HTTP 规范](https://www.w3.org/Protocols/rfc2616/rfc2616.html)中所述。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span></span> <span data-ttu-id="e5cfe-146">为此，服务必须在 HTTP 响应中设置 ETag 标头的值。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-146">To do this, the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="e5cfe-147">服务还必须检查 HTTP 请求中的 If-None-Match 标头，查看是否有任何指定的 ETag 与当前 ETag 相匹配。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="e5cfe-148">对于 GET 和 HEAD 请求，<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 接受 ETag 值并根据请求的 If-None-Match 标头检查该值。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="e5cfe-149">如果该标头存在并且存在匹配项，则会 <xref:System.ServiceModel.Web.WebFaultException> 引发一个具有 HTTP 状态代码 304 (未) 修改的，并使用匹配的 etag 将 ETag 标头添加到响应中。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="e5cfe-150"><xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 方法的一个重载接受上次修改的日期并根据请求的 If-Modified-Since 标头检查该日期。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="e5cfe-151">如果该标头存在并且自该日期以来尚未修改资源，将引发 <xref:System.ServiceModel.Web.WebFaultException> 并返回 HTTP 状态代码 304（未修改）。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="e5cfe-152">对于 PUT、POST 和 DELETE 请求，<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> 采用资源的当前 ETag 值。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="e5cfe-153">如果当前 ETag 值为 null，则该方法将检查 If-None-Match 标头的值是否为 "\*"。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="e5cfe-154">如果当前 ETag 值不是默认值，该方法将根据请求的 If-Match 标头检查当前 ETag 值。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="e5cfe-155">在任一情况下，如果请求中不存在预期的标头或该标头的值不满足条件检查，方法将引发 <xref:System.ServiceModel.Web.WebFaultException>，返回 HTTP 状态代码 412（前置条件失败），并将响应的 ETag 标头设置为当前 ETag 值。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="e5cfe-156">`CheckConditional` 方法和 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> 方法都可确保对响应标头设置的 ETag 值是符合 HTTP 规范的有效 ETag。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="e5cfe-157">这包括将 ETag 值用双引号引起来（如果这些值尚不存在）和正确转义任何内部双引号字符。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="e5cfe-158">不支持弱 ETag 比较。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="e5cfe-159">下面的示例显示如何使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-159">The following example shows how to use these methods.</span></span>  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;

        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a><span data-ttu-id="e5cfe-160">安全注意事项</span><span class="sxs-lookup"><span data-stu-id="e5cfe-160">Security Considerations</span></span>  
 <span data-ttu-id="e5cfe-161">对于需要授权的请求，不应缓存其响应，因为从缓存中提供响应时不会执行该授权。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="e5cfe-162">缓存此类响应将会带来严重的安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="e5cfe-163">通常，需要授权的请求会提供用户特定数据，因此服务器端缓存也没有益处。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="e5cfe-164">在这种情况下，客户端缓存或根本不缓存将更合适。</span><span class="sxs-lookup"><span data-stu-id="e5cfe-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
