---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 165dbed1b78d00f8d4dd3e482b9fee8a23db60da
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399618"
---
# \<serviceHostingEnvironment>
<span data-ttu-id="79443-101">此元素定义服务主机环境要为特定传输实例化的类型。</span><span class="sxs-lookup"><span data-stu-id="79443-101">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="79443-102">如果此元素为空，则使用默认类型。</span><span class="sxs-lookup"><span data-stu-id="79443-102">If this element is empty, the default type is used.</span></span> <span data-ttu-id="79443-103">此元素只能在应用程序或计算机级别的配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="79443-103">This element can only be used at the application or machine level configuration files.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceHostingEnvironment>**  
  
## <a name="syntax"></a><span data-ttu-id="79443-104">语法</span><span class="sxs-lookup"><span data-stu-id="79443-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79443-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="79443-105">Attributes and Elements</span></span>  
 <span data-ttu-id="79443-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="79443-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79443-107">特性</span><span class="sxs-lookup"><span data-stu-id="79443-107">Attributes</span></span>  
  
|<span data-ttu-id="79443-108">属性</span><span class="sxs-lookup"><span data-stu-id="79443-108">Attribute</span></span>|<span data-ttu-id="79443-109">说明</span><span class="sxs-lookup"><span data-stu-id="79443-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79443-110">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="79443-110">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="79443-111">一个布尔值，指示是否已为当前应用程序启用了 ASP.NET 兼容模式。</span><span class="sxs-lookup"><span data-stu-id="79443-111">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="79443-112">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="79443-112">The default is `false`.</span></span><br /><br /> <span data-ttu-id="79443-113">如果此特性设置为 `true` ，则对 Windows Communication Foundation （WCF）服务的请求将流经 ASP.NET HTTP 管道，并且禁止通过非 HTTP 协议进行通信。</span><span class="sxs-lookup"><span data-stu-id="79443-113">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="79443-114">有关详细信息，请参阅[WCF 服务和 ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md)。</span><span class="sxs-lookup"><span data-stu-id="79443-114">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="79443-115">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="79443-115">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="79443-116">一个整数，指定在可以激活 WCF 服务之前，系统应提供的最小可用内存量。</span><span class="sxs-lookup"><span data-stu-id="79443-116">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="79443-117">**警告：** 如果在 WCF 服务的 web.config 文件中将此属性和部分信任一起指定，则会在 <xref:System.Security.SecurityException> 运行服务时生成。</span><span class="sxs-lookup"><span data-stu-id="79443-117">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="79443-118">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="79443-118">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="79443-119">一个布尔值，指定是否对每个站点启用多个 IIS 绑定。</span><span class="sxs-lookup"><span data-stu-id="79443-119">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="79443-120">IIS 由网站组成，这些网站是包含虚拟目录的虚拟应用程序的容器。</span><span class="sxs-lookup"><span data-stu-id="79443-120">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="79443-121">可通过一个或多个 IIS 绑定访问站点上的应用程序。</span><span class="sxs-lookup"><span data-stu-id="79443-121">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="79443-122">一个 IIS 绑定提供两条信息：绑定协议和绑定信息。</span><span class="sxs-lookup"><span data-stu-id="79443-122">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="79443-123">绑定协议定义进行通信所依据的方案，而绑定信息是用于访问站点的信息。</span><span class="sxs-lookup"><span data-stu-id="79443-123">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="79443-124">绑定协议的一个示例可以是 HTTP，而绑定信息可包含 IP 地址、端口、主机标头等。</span><span class="sxs-lookup"><span data-stu-id="79443-124">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="79443-125">IIS 支持一个站点指定多个 IIS 绑定，这会导致一个方案有多个基址。</span><span class="sxs-lookup"><span data-stu-id="79443-125">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="79443-126">但是，在站点下承载的 Windows Communication Foundation （WCF）服务只允许绑定到每个方案的一个 baseAddress。</span><span class="sxs-lookup"><span data-stu-id="79443-126">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="79443-127">若要为一个 Windows Communication Foundation （WCF）服务的每个站点启用多个 IIS 绑定，请将此特性设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="79443-127">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="79443-128">请注意，仅对 HTTP 协议支持多个站点绑定。</span><span class="sxs-lookup"><span data-stu-id="79443-128">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="79443-129">配置文件中的终结点地址需要是一个完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="79443-129">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79443-130">子元素</span><span class="sxs-lookup"><span data-stu-id="79443-130">Child Elements</span></span>  
  
|<span data-ttu-id="79443-131">元素</span><span class="sxs-lookup"><span data-stu-id="79443-131">Element</span></span>|<span data-ttu-id="79443-132">描述</span><span class="sxs-lookup"><span data-stu-id="79443-132">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="79443-133">一个配置元素的集合，这些元素指定服务主机所使用的基址的前缀筛选器。</span><span class="sxs-lookup"><span data-stu-id="79443-133">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[\<serviceActivations>](serviceactivations.md)|<span data-ttu-id="79443-134">一个描述激活设置的配置节。</span><span class="sxs-lookup"><span data-stu-id="79443-134">A configuration section that describes activation settings.</span></span>|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="79443-135">一个配置元素的集合，这些元素标识特定传输的类型。</span><span class="sxs-lookup"><span data-stu-id="79443-135">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79443-136">父元素</span><span class="sxs-lookup"><span data-stu-id="79443-136">Parent Elements</span></span>  
  
|<span data-ttu-id="79443-137">元素</span><span class="sxs-lookup"><span data-stu-id="79443-137">Element</span></span>|<span data-ttu-id="79443-138">描述</span><span class="sxs-lookup"><span data-stu-id="79443-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79443-139">serviceModel</span><span class="sxs-lookup"><span data-stu-id="79443-139">serviceModel</span></span>|<span data-ttu-id="79443-140">所有 Windows Communication Foundation (WCF) 配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="79443-140">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79443-141">注解</span><span class="sxs-lookup"><span data-stu-id="79443-141">Remarks</span></span>  
 <span data-ttu-id="79443-142">默认情况下，WCF 服务和 ASP.NET 一起在寄宿应用程序域 (AppDomain) 中并行运行。</span><span class="sxs-lookup"><span data-stu-id="79443-142">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="79443-143">即使 WCF 和 ASP.NET 可以在同一 AppDomain 中共存，但在默认情况下，ASP.NET HTTP 管道不会处理 WCF 请求。</span><span class="sxs-lookup"><span data-stu-id="79443-143">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="79443-144">因此，WCF 服务不能使用 ASP.NET 应用程序平台的一些元素，</span><span class="sxs-lookup"><span data-stu-id="79443-144">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="79443-145">其中包括：</span><span class="sxs-lookup"><span data-stu-id="79443-145">These include</span></span>  
  
- <span data-ttu-id="79443-146">ASP.NET File/URL 授权</span><span class="sxs-lookup"><span data-stu-id="79443-146">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="79443-147">ASP.NET 模拟</span><span class="sxs-lookup"><span data-stu-id="79443-147">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="79443-148">基于 Cookie 的会话状态</span><span class="sxs-lookup"><span data-stu-id="79443-148">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="79443-149">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="79443-149">HttpContext.Current</span></span>  
  
- <span data-ttu-id="79443-150">通过自定义 HttpModule 获得的管道扩展性</span><span class="sxs-lookup"><span data-stu-id="79443-150">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="79443-151">如果要使 WCF 服务在 ASP.NET 上下文中正常工作并仅通过 HTTP 进行通信，则可以使用 WCF 的 ASP.NET 兼容模式。</span><span class="sxs-lookup"><span data-stu-id="79443-151">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="79443-152">当 `aspNetCompatibilityEnabled` 属性在应用程序级别中设置为 `true` 时，此模式将启用。</span><span class="sxs-lookup"><span data-stu-id="79443-152">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="79443-153">服务实现必须使用 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 类来声明其可以在兼容模式中运行。</span><span class="sxs-lookup"><span data-stu-id="79443-153">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="79443-154">当启用此兼容模式时，</span><span class="sxs-lookup"><span data-stu-id="79443-154">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="79443-155">ASP.NET File/URL 授权将在 WCF 授权之前强制执行。</span><span class="sxs-lookup"><span data-stu-id="79443-155">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="79443-156">授权决定是基于请求的传输级标识的。</span><span class="sxs-lookup"><span data-stu-id="79443-156">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="79443-157">消息级别的标识将被忽略。</span><span class="sxs-lookup"><span data-stu-id="79443-157">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="79443-158">WCF 服务操作开始是在 ASP.NET 模拟上下文中执行的。</span><span class="sxs-lookup"><span data-stu-id="79443-158">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="79443-159">如果为某个特定服务同时启用了 ASP.NET 模拟和 WCF 模拟，则将应用 WCF 模拟上下文。</span><span class="sxs-lookup"><span data-stu-id="79443-159">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="79443-160">可以通过 WCF 服务代码使用 HttpContext.Current，并且阻止服务公开非 HTTP 终结点。</span><span class="sxs-lookup"><span data-stu-id="79443-160">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="79443-161">WCF 请求由 ASP.NET 管道处理。</span><span class="sxs-lookup"><span data-stu-id="79443-161">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="79443-162">已配置为对传入请求执行操作的 HttpModule 也可以处理 WCF 请求。</span><span class="sxs-lookup"><span data-stu-id="79443-162">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="79443-163">这些 HttpModule 可包括 ASP.NET 平台组件（如 <xref:System.Web.SessionState.SessionStateModule>）以及自定义第三方模块。</span><span class="sxs-lookup"><span data-stu-id="79443-163">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79443-164">示例</span><span class="sxs-lookup"><span data-stu-id="79443-164">Example</span></span>  
 <span data-ttu-id="79443-165">下面的代码示例演示如何启用 ASP 兼容模式。</span><span class="sxs-lookup"><span data-stu-id="79443-165">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="79443-166">代码</span><span class="sxs-lookup"><span data-stu-id="79443-166">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="79443-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79443-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="79443-168">承载</span><span class="sxs-lookup"><span data-stu-id="79443-168">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="79443-169">WCF 服务和 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="79443-169">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
