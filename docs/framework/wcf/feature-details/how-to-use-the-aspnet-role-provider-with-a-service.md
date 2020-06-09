---
title: 如何：将 ASP.NET 角色提供程序与服务一起使用
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 45eeda046e877b4379d7d0e5edd90fac305f5e44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595292"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="0fb13-102">如何：将 ASP.NET 角色提供程序与服务一起使用</span><span class="sxs-lookup"><span data-stu-id="0fb13-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="0fb13-103">ASP.NET 角色提供程序（与 ASP.NET 成员资格提供程序结合使用）是一项功能，使 ASP.NET 开发人员能够创建允许用户通过网站创建帐户并为其分配角色进行授权的网站。</span><span class="sxs-lookup"><span data-stu-id="0fb13-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="0fb13-104">借助此功能，任何用户都可以通过网站建立帐户，并登录以获取该网站及其服务的独占访问权。</span><span class="sxs-lookup"><span data-stu-id="0fb13-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="0fb13-105">这与要求用户在 Windows 域中具有帐户的 Windows 安全完全不同。</span><span class="sxs-lookup"><span data-stu-id="0fb13-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="0fb13-106">相反，任何提供凭据（用户名/密码组合）的用户都可以使用该网站及其服务。</span><span class="sxs-lookup"><span data-stu-id="0fb13-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="0fb13-107">有关示例应用程序，请参阅[成员身份和角色提供程序](../samples/membership-and-role-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="0fb13-107">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="0fb13-108">有关 ASP.NET 成员资格提供程序功能的详细信息，请参阅[如何：使用 ASP.NET 成员资格提供程序](how-to-use-the-aspnet-membership-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="0fb13-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="0fb13-109">角色提供程序功能使用 SQL Server 数据库存储用户信息。</span><span class="sxs-lookup"><span data-stu-id="0fb13-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="0fb13-110">Windows Communication Foundation （WCF）开发人员可以出于安全目的利用这些功能。</span><span class="sxs-lookup"><span data-stu-id="0fb13-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="0fb13-111">当集成到 WCF 应用程序中时，用户必须为 WCF 客户端应用程序提供用户名/密码组合。</span><span class="sxs-lookup"><span data-stu-id="0fb13-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="0fb13-112">若要使 WCF 能够使用数据库，必须创建类的实例 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ，将其 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 属性设置为 <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> ，并将该实例添加到承载服务的的行为集合 <xref:System.ServiceModel.ServiceHost> 。</span><span class="sxs-lookup"><span data-stu-id="0fb13-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="0fb13-113">配置角色提供程序</span><span class="sxs-lookup"><span data-stu-id="0fb13-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="0fb13-114">在 web.config 文件中的 < > 元素下， `system.web` 添加一个 < `roleManager` > 元素，并将其属性设置 `enabled` 为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="0fb13-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="0fb13-115">将 `defaultProvider` 属性设置为 `SqlRoleProvider`。</span><span class="sxs-lookup"><span data-stu-id="0fb13-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="0fb13-116">作为 <> 元素的子 `roleManager` 元素，请添加 <`providers`> 元素。</span><span class="sxs-lookup"><span data-stu-id="0fb13-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="0fb13-117">作为 <> 元素的子 `providers` 元素，添加一个 <> 元素，并将 `add` 以下属性设置为适当的值： `name` 、 `type` 、 `connectionStringName` 和 `applicationName` ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="0fb13-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="0fb13-118">将服务配置为使用角色提供程序</span><span class="sxs-lookup"><span data-stu-id="0fb13-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="0fb13-119">在 web.config 文件中，添加一个 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0fb13-119">In the Web.config file, add a [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="0fb13-120">将 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 元素添加到 <`system.ServiceModel`> 元素。</span><span class="sxs-lookup"><span data-stu-id="0fb13-120">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="0fb13-121">将添加 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 到 <`behaviors`> 元素。</span><span class="sxs-lookup"><span data-stu-id="0fb13-121">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="0fb13-122">添加 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 元素，并将 `name` 属性设置为合适的值。</span><span class="sxs-lookup"><span data-stu-id="0fb13-122">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="0fb13-123">将添加 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) 到 <`behavior`> 元素。</span><span class="sxs-lookup"><span data-stu-id="0fb13-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="0fb13-124">将 `principalPermissionMode` 属性设置为 `UseAspNetRoles`。</span><span class="sxs-lookup"><span data-stu-id="0fb13-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="0fb13-125">将 `roleProviderName` 属性设置为 `SqlRoleProvider`。</span><span class="sxs-lookup"><span data-stu-id="0fb13-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="0fb13-126">下面的示例演示此配置的一个片段。</span><span class="sxs-lookup"><span data-stu-id="0fb13-126">The following example shows a fragment of the configuration.</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0fb13-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0fb13-127">See also</span></span>

- [<span data-ttu-id="0fb13-128">成员资格和角色提供程序</span><span class="sxs-lookup"><span data-stu-id="0fb13-128">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
- [<span data-ttu-id="0fb13-129">如何：使用 ASP.NET 成员资格提供程序</span><span class="sxs-lookup"><span data-stu-id="0fb13-129">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
