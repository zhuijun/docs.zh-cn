---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 0718f789ff4d99fb4e2651a9a704da4248cd5f49
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158430"
---
# \<claimsAuthorizationManager>

<span data-ttu-id="1a3fb-101">为传入声明注册声明授权管理器。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-101">Registers a claims authorization manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="1a3fb-102">语法</span><span class="sxs-lookup"><span data-stu-id="1a3fb-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a3fb-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1a3fb-103">Attributes and Elements</span></span>  

 <span data-ttu-id="1a3fb-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a3fb-105">特性</span><span class="sxs-lookup"><span data-stu-id="1a3fb-105">Attributes</span></span>  
  
|<span data-ttu-id="1a3fb-106">属性</span><span class="sxs-lookup"><span data-stu-id="1a3fb-106">Attribute</span></span>|<span data-ttu-id="1a3fb-107">说明</span><span class="sxs-lookup"><span data-stu-id="1a3fb-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a3fb-108">type</span><span class="sxs-lookup"><span data-stu-id="1a3fb-108">type</span></span>|<span data-ttu-id="1a3fb-109">派生自类的自定义类型 <xref:System.Security.Claims.ClaimsAuthorizationManager> 。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-109">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="1a3fb-110">有关如何指定属性的详细信息 `type` ，请参阅 [自定义类型引用](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-110">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a3fb-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1a3fb-111">Child Elements</span></span>  

 <span data-ttu-id="1a3fb-112">如果没有 `type` 属性，或者如果 `type` 特性引用 <xref:System.Security.Claims.ClaimsAuthenticationManager> 类，则 `<claimsAuthorizationManager>` 元素不采用子元素; 但是，从派生的类 <xref:System.Security.Claims.ClaimsAuthorizationManager> 可以定义子配置元素。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a3fb-113">父元素</span><span class="sxs-lookup"><span data-stu-id="1a3fb-113">Parent Elements</span></span>  
  
|<span data-ttu-id="1a3fb-114">元素</span><span class="sxs-lookup"><span data-stu-id="1a3fb-114">Element</span></span>|<span data-ttu-id="1a3fb-115">描述</span><span class="sxs-lookup"><span data-stu-id="1a3fb-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="1a3fb-116">指定服务级别标识设置。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a3fb-117">备注</span><span class="sxs-lookup"><span data-stu-id="1a3fb-117">Remarks</span></span>  

 <span data-ttu-id="1a3fb-118">通过类提供的默认行为 <xref:System.Security.Claims.ClaimsAuthorizationManager> 始终授权传入声明。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="1a3fb-119">如果未 `type` 指定任何特性或 `type` 特性指定了 <xref:System.Security.Claims.ClaimsAuthorizationManager> 类，则元素不 `<claimsAuthorizationManager>` 采用子元素。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="1a3fb-120">可以指定 `type` 用于注册派生自类的类型的属性， <xref:System.Security.Claims.ClaimsAuthorizationManager> 以实现自定义行为。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="1a3fb-121">派生类可以 `<claimsAuthorizationManager>` 通过重写 <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> 方法来处理这些元素，从而支持通过元素的子元素进行的配置。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-121">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="1a3fb-122">为子元素定义的架构位于类的设计器中。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1a3fb-123">当使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 类在代码中提供基于声明的访问控制时，元素引用的标识配置将 `<federationConfiguration>` 配置用于做出授权决定的声明授权管理器和策略。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-123">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="1a3fb-124">即使在非被动 Web 应用场景的情况下（例如 Windows Communication Foundation (WCF) 应用程序或不是基于 Web 的应用程序），也是如此。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-124">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="1a3fb-125">如果应用程序不是被动 Web 应用程序，则 `<claimsAuthorizationManager>` 元素 (及其子策略元素，如果只应用了引用的标识配置) 。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-125">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="1a3fb-126">忽略所有其他设置。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-126">All other settings are ignored.</span></span> <span data-ttu-id="1a3fb-127">有关详细信息，请参阅 [\<federationConfiguration>](federationconfiguration.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-127">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="1a3fb-128">此元素设置 <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-128">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a3fb-129">示例</span><span class="sxs-lookup"><span data-stu-id="1a3fb-129">Example</span></span>  

 <span data-ttu-id="1a3fb-130">下面的 XML 显示了一个声明授权管理器的配置，该管理器实现由资源操作对组成的策略，其中每个规则都指定请求者为对资源执行操作而必须拥有的声明的布尔组合。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-130">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="1a3fb-131">示例中可找到实现声明授权管理器的代码，该代码可使用此策略 `ClaimsBasedAuthorization` 。</span><span class="sxs-lookup"><span data-stu-id="1a3fb-131">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
