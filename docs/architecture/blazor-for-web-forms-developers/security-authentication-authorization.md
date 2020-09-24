---
title: 安全性： ASP.NET Web 窗体和中的身份验证和授权 Blazor
description: 了解如何在 ASP.NET Web 窗体和中处理身份验证和授权 Blazor 。
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/11/2019
ms.openlocfilehash: 690e559617e4961c3cf3262a6d2d48a6bfac67cd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161290"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-no-locblazor"></a><span data-ttu-id="a9b85-103">安全性：ASP.NET Web Forms 和 Blazor  中的身份验证和授权</span><span class="sxs-lookup"><span data-stu-id="a9b85-103">Security: Authentication and Authorization in ASP.NET Web Forms and Blazor</span></span>

<span data-ttu-id="a9b85-104">从 ASP.NET Web 窗体应用程序迁移到 Blazor 几乎肯定需要更新身份验证和授权的执行方式，假设应用程序已配置身份验证。</span><span class="sxs-lookup"><span data-stu-id="a9b85-104">Migrating from an ASP.NET Web Forms application to Blazor will almost certainly require updating how authentication and authorization is performed, assuming the application had authentication configured.</span></span> <span data-ttu-id="a9b85-105">本章介绍如何从 ASP.NET Web 窗体通用提供程序模型（ () 成员资格、角色和用户配置文件）迁移，以及如何使用应用 ASP.NET Core 标识 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-105">This chapter will cover how to migrate from the ASP.NET Web Forms universal provider model (for membership, roles, and user profiles) and how to work with ASP.NET Core Identity from Blazor apps.</span></span> <span data-ttu-id="a9b85-106">尽管本章将介绍高级步骤和注意事项，但在引用的文档中可以找到详细步骤和脚本。</span><span class="sxs-lookup"><span data-stu-id="a9b85-106">While this chapter will cover the high level steps and considerations, the detailed steps and scripts may be found in the referenced documentation.</span></span>

## <a name="aspnet-universal-providers"></a><span data-ttu-id="a9b85-107">ASP.NET 通用提供程序</span><span class="sxs-lookup"><span data-stu-id="a9b85-107">ASP.NET universal providers</span></span>

<span data-ttu-id="a9b85-108">自 ASP.NET 2.0 起，ASP.NET Web 窗体平台支持多种功能（包括成员身份）的提供程序模型。</span><span class="sxs-lookup"><span data-stu-id="a9b85-108">Since ASP.NET 2.0, the ASP.NET Web Forms platform has supported a provider model for a variety of features, including membership.</span></span> <span data-ttu-id="a9b85-109">通用成员资格提供程序与可选角色提供程序一起，通常与 ASP.NET Web 窗体应用程序一起部署。</span><span class="sxs-lookup"><span data-stu-id="a9b85-109">The universal membership provider, along with the optional role provider, is very commonly deployed with ASP.NET Web Forms applications.</span></span> <span data-ttu-id="a9b85-110">它提供一种强大且安全的方式来管理身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="a9b85-110">It offers a robust and secure way to manage authentication and authorization that continues to work well today.</span></span> <span data-ttu-id="a9b85-111">这些通用 [提供程序的](https://www.nuget.org/packages/Microsoft.AspNet.Providers)最新产品/服务可作为 NuGet 包、</span><span class="sxs-lookup"><span data-stu-id="a9b85-111">The most recent offering of these universal providers is available as a NuGet package, [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span></span>

<span data-ttu-id="a9b85-112">通用提供程序使用包括、、和之类的表的 SQL 数据库 `aspnet_Applications` 架构 `aspnet_Membership` `aspnet_Roles` `aspnet_Users` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-112">The Universal Providers work with a SQL database schema that includes tables like `aspnet_Applications`, `aspnet_Membership`, `aspnet_Roles`, and `aspnet_Users`.</span></span> <span data-ttu-id="a9b85-113">通过运行 [aspnet_regsql.exe 命令](/previous-versions/ms229862(v=vs.140))进行配置时，提供程序将安装表和存储过程，这些表和存储过程提供了处理基础数据所需的所有必要查询和命令。</span><span class="sxs-lookup"><span data-stu-id="a9b85-113">When configured by running the [aspnet_regsql.exe command](/previous-versions/ms229862(v=vs.140)), the providers install tables and stored procedures that provide all of the necessary queries and commands necessary to work with the underlying data.</span></span> <span data-ttu-id="a9b85-114">数据库架构和这些存储过程与较新 ASP.NET Identity 和 ASP.NET Core 标识系统不兼容，因此必须将现有数据迁移到新系统。</span><span class="sxs-lookup"><span data-stu-id="a9b85-114">The database schema and these stored procedures are not compatible with newer ASP.NET Identity and ASP.NET Core Identity systems, so existing data must be migrated into the new system.</span></span> <span data-ttu-id="a9b85-115">图1显示了为通用提供程序配置的示例表架构。</span><span class="sxs-lookup"><span data-stu-id="a9b85-115">Figure 1 shows an example table schema configured for universal providers.</span></span>

![通用提供程序架构](./media/security/membership-tables.png)

<span data-ttu-id="a9b85-117">通用提供程序负责处理用户、成员资格、角色和配置文件。</span><span class="sxs-lookup"><span data-stu-id="a9b85-117">The universal provider handles users, membership, roles, and profiles.</span></span> <span data-ttu-id="a9b85-118">向用户分配全局唯一标识符和非常基本的信息 (userId，用户名) 存储在 `aspnet_Users` 表中。</span><span class="sxs-lookup"><span data-stu-id="a9b85-118">Users are assigned globally unique identifiers and very basic information (userId, userName) is stored in the `aspnet_Users` table.</span></span> <span data-ttu-id="a9b85-119">身份验证信息（如密码、密码格式、密码 salt、锁定计数器和详细信息等）存储在表中 `aspnet_Membership` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-119">Authentication information, such as password, password format, password salt, lockout counters and details, etc. are stored in the `aspnet_Membership` table.</span></span> <span data-ttu-id="a9b85-120">角色只包含名称和唯一标识符，这些标识符通过关联表分配给用户 `aspnet_UsersInRoles` ，提供多对多的关系。</span><span class="sxs-lookup"><span data-stu-id="a9b85-120">Roles consist simply of names and unique identifiers, which are assigned to users via the `aspnet_UsersInRoles` association table, providing a many-to-many relationship.</span></span>

<span data-ttu-id="a9b85-121">如果现有系统除了使用成员身份外，还会使用角色，则需要将用户帐户、关联的密码、角色和角色成员身份迁移到 ASP.NET Core 标识。</span><span class="sxs-lookup"><span data-stu-id="a9b85-121">If your existing system is using roles in addition to membership, you will need to migrate the user accounts, the associated passwords, the roles, and the role membership into ASP.NET Core Identity.</span></span> <span data-ttu-id="a9b85-122">你还可能需要使用 if 语句来更新你当前正在执行角色检查的代码，而不是使用声明性筛选器、特性和/或标记帮助程序。</span><span class="sxs-lookup"><span data-stu-id="a9b85-122">You will also most likely need to update your code where you're currently performing role checks using if statements to instead leverage declarative filters, attributes, and/or tag helpers.</span></span> <span data-ttu-id="a9b85-123">我们将在本章末尾更详细地查看迁移注意事项。</span><span class="sxs-lookup"><span data-stu-id="a9b85-123">We will review migration considerations in greater detail at the end of this chapter.</span></span>

### <a name="authorization-configuration-in-web-forms"></a><span data-ttu-id="a9b85-124">Web 窗体中的授权配置</span><span class="sxs-lookup"><span data-stu-id="a9b85-124">Authorization configuration in Web Forms</span></span>

<span data-ttu-id="a9b85-125">若要在 ASP.NET Web 窗体应用程序中配置对某些页面的授权访问，通常指定匿名用户无法访问某些页面或文件夹。</span><span class="sxs-lookup"><span data-stu-id="a9b85-125">To configure authorized access to certain pages in an ASP.NET Web Forms application, typically you specify that certain pages or folders are inaccessible to anonymous users.</span></span> <span data-ttu-id="a9b85-126">这是在 web.config 文件中完成的：</span><span class="sxs-lookup"><span data-stu-id="a9b85-126">This is done in the web.config file:</span></span>

```xml
<?xml version="1.0"?>
<configuration>
    <system.web>
      <authentication mode="Forms">
        <forms defaultUrl="~/home.aspx" loginUrl="~/login.aspx"
          slidingExpiration="true" timeout="2880"></forms>
      </authentication>

      <authorization>
        <deny users="?" />
      </authorization>
    </system.web>
</configuration>
```

<span data-ttu-id="a9b85-127">" `authentication` 配置" 部分设置应用程序的窗体身份验证。</span><span class="sxs-lookup"><span data-stu-id="a9b85-127">The `authentication` configuration section sets up forms authentication for the application.</span></span> <span data-ttu-id="a9b85-128">此 `authorization` 部分用于禁止对整个应用程序的匿名用户使用。</span><span class="sxs-lookup"><span data-stu-id="a9b85-128">The `authorization` section is used to disallow anonymous users for the entire application.</span></span> <span data-ttu-id="a9b85-129">不过，你可以基于每个位置提供更精细的授权规则，还可以应用基于角色的授权检查。</span><span class="sxs-lookup"><span data-stu-id="a9b85-129">However, you can provide more granular authorization rules on a per-location basis as well as apply role based authorization checks.</span></span>

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="a9b85-130">上述配置（与第一个配置结合使用时）将允许匿名用户访问登录页，并覆盖未经身份验证的用户的站点范围限制。</span><span class="sxs-lookup"><span data-stu-id="a9b85-130">The above configuration, when combined with the first one, would allow anonymous users to access the login page, overriding the site-wide restriction on non-authenticated users.</span></span>

```xml
<location path="/admin">
  <system.web>
    <authorization>
      <allow roles="Administrators" />
      <deny users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="a9b85-131">以上配置在与其他配置结合使用时， `/admin` 会将文件夹及其内的所有资源限制为 "Administrators" 角色的成员。</span><span class="sxs-lookup"><span data-stu-id="a9b85-131">The above configuration, when combined with the others, restricts access to the `/admin` folder and all resources within it to members of the "Administrators" role.</span></span> <span data-ttu-id="a9b85-132">这还可以通过在 `web.config` 文件夹根目录中放置单独的文件来应用 `/admin` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-132">This could also be applied by placing a separate `web.config` file within the `/admin` folder root.</span></span>

### <a name="authorization-code-in-web-forms"></a><span data-ttu-id="a9b85-133">Web 窗体中的授权代码</span><span class="sxs-lookup"><span data-stu-id="a9b85-133">Authorization code in Web Forms</span></span>

<span data-ttu-id="a9b85-134">除了使用配置访问之外 `web.config` ，还可以通过编程方式配置 Web 窗体应用程序中的访问和行为。</span><span class="sxs-lookup"><span data-stu-id="a9b85-134">In addition to configuring access using `web.config`, you can also programmatically configure access and behavior in your Web Forms application.</span></span> <span data-ttu-id="a9b85-135">例如，你可以限制执行特定操作的功能，或根据用户的角色查看特定数据。</span><span class="sxs-lookup"><span data-stu-id="a9b85-135">For instance, you can restrict the ability to perform certain operations or view certain data based on the user's role.</span></span>

<span data-ttu-id="a9b85-136">此代码既可以在代码隐藏逻辑中使用，也可以在页面本身中使用：</span><span class="sxs-lookup"><span data-stu-id="a9b85-136">This code can be used both in codebehind logic as well as in the page itself:</span></span>

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

<span data-ttu-id="a9b85-137">除了检查用户角色成员身份外，还可以确定是否已对其进行身份验证 (不过，这通常是使用以上) 的基于位置的配置来实现的。</span><span class="sxs-lookup"><span data-stu-id="a9b85-137">In addition to checking user role membership, you can also determine if they are authenticated (though often this is better done using the location-based configuration covered above).</span></span> <span data-ttu-id="a9b85-138">下面是此方法的一个示例。</span><span class="sxs-lookup"><span data-stu-id="a9b85-138">Below is an example of this approach.</span></span>

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

<span data-ttu-id="a9b85-139">在上面的代码中，基于角色的访问控制 (RBAC) 用于根据当前用户的角色确定页面的某些元素（如 `SecretPanel` ）是否可见。</span><span class="sxs-lookup"><span data-stu-id="a9b85-139">In the code above, role-based access control (RBAC) is used to determine whether certain elements of the page, such as a `SecretPanel`, are visible based on the current user's role.</span></span>

<span data-ttu-id="a9b85-140">通常，ASP.NET Web 窗体应用程序配置文件中的安全性 `web.config` ，然后在页面中需要的位置 `.aspx` 和相关的代码隐藏文件中添加其他检查 `.aspx.cs` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-140">Typically, ASP.NET Web Forms applications configure security within the `web.config` file and then add additional checks where needed in `.aspx` pages and their related `.aspx.cs` codebehind files.</span></span> <span data-ttu-id="a9b85-141">大多数应用程序都使用通用成员资格提供程序，通常使用其他角色提供程序。</span><span class="sxs-lookup"><span data-stu-id="a9b85-141">Most applications leverage the universal membership provider, frequently with the additional role provider.</span></span>

## <a name="aspnet-core-identity"></a><span data-ttu-id="a9b85-142">ASP.NET Core 标识</span><span class="sxs-lookup"><span data-stu-id="a9b85-142">ASP.NET Core Identity</span></span>

<span data-ttu-id="a9b85-143">尽管仍需要身份验证和授权，但与通用提供程序相比，ASP.NET Core 标识将使用一组不同的抽象和假设。</span><span class="sxs-lookup"><span data-stu-id="a9b85-143">Although still tasked with authentication and authorization, ASP.NET Core Identity uses a different set of abstractions and assumptions when compared to the universal providers.</span></span> <span data-ttu-id="a9b85-144">例如，新的标识模型支持第三方身份验证，允许用户使用社交媒体帐户或其他受信任的身份验证提供程序进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="a9b85-144">For example, the new Identity model supports third party authentication, allowing users to authenticate using a social media account or other trusted authentication provider.</span></span> <span data-ttu-id="a9b85-145">ASP.NET Core 标识支持通常需要的页的 UI，如登录、注销和注册。</span><span class="sxs-lookup"><span data-stu-id="a9b85-145">ASP.NET Core Identity supports UI for commonly needed pages like login, logout, and register.</span></span> <span data-ttu-id="a9b85-146">它利用 EF Core 来访问其数据，并使用 EF Core 迁移来生成支持其数据模型所需的必需架构。</span><span class="sxs-lookup"><span data-stu-id="a9b85-146">It leverages EF Core for its data access, and uses EF Core migrations to generate the necessary schema required to supports its data model.</span></span> <span data-ttu-id="a9b85-147">本 [ASP.NET Core 上的标识简介](/aspnet/core/security/authentication/identity) 提供了 ASP.NET Core 标识中包含的内容以及如何开始使用它。</span><span class="sxs-lookup"><span data-stu-id="a9b85-147">This [introduction to Identity on ASP.NET Core](/aspnet/core/security/authentication/identity) provides a good overview of what is included with ASP.NET Core Identity and how to get started working with it.</span></span> <span data-ttu-id="a9b85-148">如果你尚未在应用程序及其数据库中设置 ASP.NET Core 标识，则会帮助你入门。</span><span class="sxs-lookup"><span data-stu-id="a9b85-148">If you haven't already set up ASP.NET Core Identity in your application and its database, it will help you get started.</span></span>

### <a name="roles-claims-and-policies"></a><span data-ttu-id="a9b85-149">角色、声明和策略</span><span class="sxs-lookup"><span data-stu-id="a9b85-149">Roles, claims, and policies</span></span>

<span data-ttu-id="a9b85-150">通用提供程序和 ASP.NET Core 标识都支持角色的概念。</span><span class="sxs-lookup"><span data-stu-id="a9b85-150">Both the universal providers and ASP.NET Core Identity support the concept of roles.</span></span> <span data-ttu-id="a9b85-151">你可以为用户创建角色并将用户分配到角色。</span><span class="sxs-lookup"><span data-stu-id="a9b85-151">You can create roles for users and assign users to roles.</span></span> <span data-ttu-id="a9b85-152">用户可以属于任意数量的角色，你可以验证角色成员身份作为授权实现的一部分。</span><span class="sxs-lookup"><span data-stu-id="a9b85-152">Users can belong to any number of roles, and you can verify role membership as part of your authorization implementation.</span></span>

<span data-ttu-id="a9b85-153">除了角色外，ASP.NET Core 标识还支持声明和策略的概念。</span><span class="sxs-lookup"><span data-stu-id="a9b85-153">In addition to roles, ASP.NET Core identity supports the concepts of claims and policies.</span></span> <span data-ttu-id="a9b85-154">虽然角色应专门对应于该角色中的用户应能够访问的一组资源，但声明只是用户标识的一部分。</span><span class="sxs-lookup"><span data-stu-id="a9b85-154">While a role should specifically correspond to a set of resources a user in that role should be able to access, a claim is simply part of a user's identity.</span></span> <span data-ttu-id="a9b85-155">声明是表示使用者的名称值对，而不是主题可执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a9b85-155">A claim is a name value pair that represents what the subject is, not what the subject can do.</span></span>

<span data-ttu-id="a9b85-156">可以直接检查用户的声明，并根据其确定是否应向用户授予对资源的访问权限。</span><span class="sxs-lookup"><span data-stu-id="a9b85-156">It is possible to directly inspect a user's claims and determine based on these whether a user should be given access to a resource.</span></span> <span data-ttu-id="a9b85-157">但是，此类检查通常是重复性的，并分散在整个系统中。</span><span class="sxs-lookup"><span data-stu-id="a9b85-157">However, such checks are often repetitive and scattered throughout the system.</span></span> <span data-ttu-id="a9b85-158">更好的方法是定义 *策略*。</span><span class="sxs-lookup"><span data-stu-id="a9b85-158">A better approach is to define a *policy*.</span></span>

<span data-ttu-id="a9b85-159">授权策略包括一个或多个要求。</span><span class="sxs-lookup"><span data-stu-id="a9b85-159">An authorization policy consists of one or more requirements.</span></span> <span data-ttu-id="a9b85-160">在的方法中，将策略注册为授权服务配置的一部分 `ConfigureServices` `Startup.cs` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-160">Policies are registered as part of the authorization service configuration in the `ConfigureServices` method of `Startup.cs`.</span></span> <span data-ttu-id="a9b85-161">例如，以下代码片段将配置名为 "CanadiansOnly" 的策略，该策略要求用户具有值为 "加拿大" 的国家/地区声明。</span><span class="sxs-lookup"><span data-stu-id="a9b85-161">For example, the following code snippet configures a policy called "CanadiansOnly" which has the requirement that the user have the Country claim with the value of "Canada".</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

<span data-ttu-id="a9b85-162">你可以 [在文档中了解有关如何创建自定义策略的详细信息](/aspnet/core/security/authorization/policies)。</span><span class="sxs-lookup"><span data-stu-id="a9b85-162">You can [learn more about how to create custom policies in the documentation](/aspnet/core/security/authorization/policies).</span></span>

<span data-ttu-id="a9b85-163">无论你使用的是策略还是角色，你都可以指定应用程序中的特定页面 Blazor 要求具有属性的角色或策略 `[Authorize]` ，并将其应用于 `@attribute` 指令。</span><span class="sxs-lookup"><span data-stu-id="a9b85-163">Whether you're using policies or roles, you can specify that a particular page in your Blazor application require that role or policy with the `[Authorize]` attribute, applied with the `@attribute` directive.</span></span>

<span data-ttu-id="a9b85-164">需要角色：</span><span class="sxs-lookup"><span data-stu-id="a9b85-164">Requiring a role:</span></span>

```csharp
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="a9b85-165">要求满足策略：</span><span class="sxs-lookup"><span data-stu-id="a9b85-165">Requiring a policy be satisfied:</span></span>

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

<span data-ttu-id="a9b85-166">如果需要在代码中访问用户的身份验证状态、角色或声明，可以通过两种主要方式实现此目的。</span><span class="sxs-lookup"><span data-stu-id="a9b85-166">If you need access to a user's authentication state, roles, or claims in your code, there are two primary ways to achieve this.</span></span> <span data-ttu-id="a9b85-167">第一种方式是接收身份验证状态作为级联参数。</span><span class="sxs-lookup"><span data-stu-id="a9b85-167">The first is to receive the authentication state as a cascading parameter.</span></span> <span data-ttu-id="a9b85-168">第二种是使用注入的来访问状态 `AuthenticationStateProvider` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-168">The second is to access the state using an injected `AuthenticationStateProvider`.</span></span> <span data-ttu-id="a9b85-169">[ Blazor 安全文档](/aspnet/core/blazor/security/)中介绍了上述每种方法的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a9b85-169">The details of each of these approaches are described in the [Blazor Security documentation](/aspnet/core/blazor/security/).</span></span>

<span data-ttu-id="a9b85-170">下面的代码演示如何将 `AuthenticationState` 作为级联参数接收：</span><span class="sxs-lookup"><span data-stu-id="a9b85-170">The following code shows how to receive the `AuthenticationState` as a cascading parameter:</span></span>

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

<span data-ttu-id="a9b85-171">使用此参数时，可以使用以下代码获取用户：</span><span class="sxs-lookup"><span data-stu-id="a9b85-171">With this parameter in place, you can get the user using this code:</span></span>

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

<span data-ttu-id="a9b85-172">下面的代码演示如何注入 `AuthenticationStateProvider` ：</span><span class="sxs-lookup"><span data-stu-id="a9b85-172">The following code shows how to inject the `AuthenticationStateProvider`:</span></span>

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

<span data-ttu-id="a9b85-173">提供程序准备就绪后，可以使用以下代码获取用户的访问权限：</span><span class="sxs-lookup"><span data-stu-id="a9b85-173">With the provider in place, you can gain access to the user with the following code:</span></span>

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

<span data-ttu-id="a9b85-174">**注意：**`AuthorizeView`本章稍后介绍的组件提供了一种声明性方法来控制用户在页面或组件上看到的内容。</span><span class="sxs-lookup"><span data-stu-id="a9b85-174">**Note:** The `AuthorizeView` component, covered later in this chapter, provides a declarative way to control what a user sees on a page or component.</span></span>

<span data-ttu-id="a9b85-175">若要在服务器应用程序中使用用户和声明 (Blazor) 你可能还需要注入 `UserManager<T>` (用于 `IdentityUser` 默认) ，可用于枚举和修改用户的声明。</span><span class="sxs-lookup"><span data-stu-id="a9b85-175">To work with users and claims (in Blazor Server applications) you may also need to inject a `UserManager<T>` (use `IdentityUser` for default) which you can use to enumerate and modify claims for a user.</span></span> <span data-ttu-id="a9b85-176">首先，注入类型并将其分配给属性：</span><span class="sxs-lookup"><span data-stu-id="a9b85-176">First inject the type and assign it to a property:</span></span>

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

<span data-ttu-id="a9b85-177">然后使用它来处理用户的声明。</span><span class="sxs-lookup"><span data-stu-id="a9b85-177">Then use it to work with the user's claims.</span></span> <span data-ttu-id="a9b85-178">下面的示例演示如何在用户上添加和保存声明：</span><span class="sxs-lookup"><span data-stu-id="a9b85-178">The following sample shows how to add and persist a claim on a user:</span></span>

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

<span data-ttu-id="a9b85-179">如果需要使用角色，请遵循相同的方法。</span><span class="sxs-lookup"><span data-stu-id="a9b85-179">If you need to work with roles, follow the same approach.</span></span> <span data-ttu-id="a9b85-180">可能需要注入 `RoleManager<T>` `IdentityRole` 默认类型的 () ，以便列出和管理角色本身。</span><span class="sxs-lookup"><span data-stu-id="a9b85-180">You may need to inject a `RoleManager<T>` (use `IdentityRole` for default type) to list and manage the roles themselves.</span></span>

<span data-ttu-id="a9b85-181">**注意：** 在 Blazor WebAssembly 项目中，您将需要提供服务器 api 来 (执行这些操作，而不是使用 `UserManager<T>` 或 `RoleManager<T>` 直接) 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-181">**Note:** In Blazor WebAssembly projects, you will need to provide server APIs to perform these operations (instead of using `UserManager<T>` or `RoleManager<T>` directly).</span></span> <span data-ttu-id="a9b85-182">BlazorWebAssembly 客户端应用程序可以通过安全地调用为此目的而公开的 API 终结点来管理声明和/或角色。</span><span class="sxs-lookup"><span data-stu-id="a9b85-182">A Blazor WebAssembly client application would manage claims and/or roles by securely calling API endpoints exposed for this purpose.</span></span>

### <a name="migration-guide"></a><span data-ttu-id="a9b85-183">迁移指南</span><span class="sxs-lookup"><span data-stu-id="a9b85-183">Migration guide</span></span>

<span data-ttu-id="a9b85-184">从 ASP.NET Web 窗体和通用提供程序迁移到 ASP.NET Core 标识需要几个步骤：</span><span class="sxs-lookup"><span data-stu-id="a9b85-184">Migrating from ASP.NET Web Forms and universal providers to ASP.NET Core Identity requires several steps:</span></span>

1. <span data-ttu-id="a9b85-185">在目标数据库中创建 ASP.NET Core 标识数据库架构</span><span class="sxs-lookup"><span data-stu-id="a9b85-185">Create ASP.NET Core Identity database schema in destination database</span></span>
2. <span data-ttu-id="a9b85-186">将数据从通用提供程序架构迁移到 ASP.NET Core 标识架构</span><span class="sxs-lookup"><span data-stu-id="a9b85-186">Migrate data from universal provider schema to ASP.NET Core Identity schema</span></span>
3. <span data-ttu-id="a9b85-187">将 web.config 中的配置迁移到中间件和服务，通常为 `Startup.cs`</span><span class="sxs-lookup"><span data-stu-id="a9b85-187">Migrate configuration from web.config to middleware and services, typically in `Startup.cs`</span></span>
4. <span data-ttu-id="a9b85-188">使用控件和条件更新单个页面，使用标记帮助程序和新的标识 Api。</span><span class="sxs-lookup"><span data-stu-id="a9b85-188">Update individual pages using controls and conditionals to use tag helpers and new identity APIs.</span></span>

<span data-ttu-id="a9b85-189">以下部分详细介绍了这些步骤。</span><span class="sxs-lookup"><span data-stu-id="a9b85-189">Each of these steps is described in detail in the following sections.</span></span>

### <a name="creating-the-aspnet-core-identity-schema"></a><span data-ttu-id="a9b85-190">创建 ASP.NET Core 标识架构</span><span class="sxs-lookup"><span data-stu-id="a9b85-190">Creating the ASP.NET Core Identity schema</span></span>

<span data-ttu-id="a9b85-191">有多种方法可以创建用于 ASP.NET Core 标识的必要的表结构。</span><span class="sxs-lookup"><span data-stu-id="a9b85-191">There are several ways to create the necessary table structure used for ASP.NET Core Identity.</span></span> <span data-ttu-id="a9b85-192">最简单的办法就是创建一个新的 ASP.NET Core Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="a9b85-192">The simplest is to create a new ASP.NET Core Web application.</span></span> <span data-ttu-id="a9b85-193">选择 "Web 应用程序"，然后将 "身份验证" 更改为使用单个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="a9b85-193">Choose Web Application and then change Authentication to use Individual User Accounts.</span></span>

![具有单独用户帐户的新项目](./media/security/individual-user-accounts.png)

<span data-ttu-id="a9b85-195">在命令行中，可以通过运行来执行相同的操作 `dotnet new webapp -au Individual` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-195">From the command line, you can do the same thing by running `dotnet new webapp -au Individual`.</span></span> <span data-ttu-id="a9b85-196">应用创建后，运行它并在站点上注册。</span><span class="sxs-lookup"><span data-stu-id="a9b85-196">Once the app has been created, run it and register on the site.</span></span> <span data-ttu-id="a9b85-197">应会触发如下所示的页面：</span><span class="sxs-lookup"><span data-stu-id="a9b85-197">You should trigger a page like the one shown below:</span></span>

![应用迁移页面](./media/security/apply-migrations-page.png)

<span data-ttu-id="a9b85-199">单击 "应用迁移" 按钮，应创建必要的数据库表。</span><span class="sxs-lookup"><span data-stu-id="a9b85-199">Click on the "Apply Migrations" button and the necessary database tables should be created for you.</span></span> <span data-ttu-id="a9b85-200">此外，迁移文件应显示在你的项目中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9b85-200">In addition, the migration files should appear in your project, as shown:</span></span>

![迁移文件](./media/security/migration-files.png)

<span data-ttu-id="a9b85-202">你可以使用此命令行工具自行运行迁移，而无需运行 web 应用程序：</span><span class="sxs-lookup"><span data-stu-id="a9b85-202">You can run the migration yourself, without running the web application, using this command line tool:</span></span>

```powershell
dotnet ef database update
```

<span data-ttu-id="a9b85-203">如果要运行脚本将新架构应用到现有数据库，可以从命令行编写这些迁移的脚本。</span><span class="sxs-lookup"><span data-stu-id="a9b85-203">If you would rather run a script to apply the new schema to an existing database, you can script these migrations from the command line.</span></span> <span data-ttu-id="a9b85-204">运行以下命令以生成脚本：</span><span class="sxs-lookup"><span data-stu-id="a9b85-204">Run this command to generate the script:</span></span>

```powershell
dotnet ef migrations script -o auth.sql
```

<span data-ttu-id="a9b85-205">这会在输出文件中生成一个 SQL 脚本， `auth.sql` 然后可以对所需的任何数据库运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="a9b85-205">This will produce a SQL script in the output file `auth.sql` which can then be run against whatever database you like.</span></span> <span data-ttu-id="a9b85-206">如果运行命令时遇到任何问题 `dotnet ef` ，请 [确保系统上已安装 EF Core 工具](/ef/core/miscellaneous/cli/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="a9b85-206">If you have any trouble running `dotnet ef` commands, [make sure you have the EF Core tools installed on your system](/ef/core/miscellaneous/cli/dotnet).</span></span>

<span data-ttu-id="a9b85-207">如果源表上有其他列，则需要在新架构中确定这些列的最佳位置。</span><span class="sxs-lookup"><span data-stu-id="a9b85-207">In the event you have additional columns on your source tables, you will need to identify the best location for these columns in the new schema.</span></span> <span data-ttu-id="a9b85-208">通常， `aspnet_Membership` 应将表中的列映射到 `AspNetUsers` 表。</span><span class="sxs-lookup"><span data-stu-id="a9b85-208">Generally, columns found on the `aspnet_Membership` table should be mapped to the `AspNetUsers` table.</span></span> <span data-ttu-id="a9b85-209">上的列 `aspnet_Roles` 应映射到 `AspNetRoles` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-209">Columns on `aspnet_Roles` should be mapped to `AspNetRoles`.</span></span> <span data-ttu-id="a9b85-210">表中的任何其他列 `aspnet_UsersInRoles` 都将添加到 `AspNetUserRoles` 表中。</span><span class="sxs-lookup"><span data-stu-id="a9b85-210">Any additional columns on the `aspnet_UsersInRoles` table would be added to the `AspNetUserRoles` table.</span></span>

<span data-ttu-id="a9b85-211">还需要考虑将任何其他列放在单独的表中，以便将来的迁移不需要考虑默认标识架构的自定义。</span><span class="sxs-lookup"><span data-stu-id="a9b85-211">It's also worth considering putting any additional columns on separate tables, so that future migrations won't need to take into account such customizations of the default identity schema.</span></span>

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a><span data-ttu-id="a9b85-212">将数据从通用提供程序迁移到 ASP.NET Core 标识</span><span class="sxs-lookup"><span data-stu-id="a9b85-212">Migrating data from universal providers to ASP.NET Core Identity</span></span>

<span data-ttu-id="a9b85-213">准备好目标表架构后，下一步是将用户和角色记录迁移到新的架构。</span><span class="sxs-lookup"><span data-stu-id="a9b85-213">Once you have the destination table schema in place, the next step is to migrate your user and role records to the new schema.</span></span> <span data-ttu-id="a9b85-214">架构差异的完整列表，包括映射到哪些新列的列，可在 [此处](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)找到。</span><span class="sxs-lookup"><span data-stu-id="a9b85-214">A complete list of the schema differences, including which columns map to which new columns, can be found [here](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span>

<span data-ttu-id="a9b85-215">若要将用户从成员身份迁移到新的标识表，你应 [按照文档中所述的步骤进行操作](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)。</span><span class="sxs-lookup"><span data-stu-id="a9b85-215">To migrate your users from membership to the new identity tables, you should [follow the steps described in the documentation](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="a9b85-216">完成这些步骤和提供的脚本后，用户将需要在下次登录时更改其密码。</span><span class="sxs-lookup"><span data-stu-id="a9b85-216">After following these steps and the script provided, your users will need to change their password the next time they log in.</span></span>

<span data-ttu-id="a9b85-217">可以迁移用户密码，但过程更多。</span><span class="sxs-lookup"><span data-stu-id="a9b85-217">It is possible to migrate user passwords but the process is much more involved.</span></span> <span data-ttu-id="a9b85-218">要求用户在迁移过程中更新其密码，并鼓励他们使用全新的唯一密码，这可能会增强应用程序的整体安全性。</span><span class="sxs-lookup"><span data-stu-id="a9b85-218">Requiring users to update their passwords as part of the migration process, and encouraging them to use new, unique passwords, is likely to enhance the overall security of the application.</span></span>

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a><span data-ttu-id="a9b85-219">将 web.config 的安全设置迁移到 Startup.cs</span><span class="sxs-lookup"><span data-stu-id="a9b85-219">Migrating security settings from web.config to Startup.cs</span></span>

<span data-ttu-id="a9b85-220">如上所述，ASP.NET 成员身份和角色提供程序在应用程序的 web.config 文件中配置。</span><span class="sxs-lookup"><span data-stu-id="a9b85-220">As noted above, ASP.NET membership and role providers are configured in the application's web.config file.</span></span> <span data-ttu-id="a9b85-221">由于 ASP.NET Core 应用未绑定到 IIS 并使用单独的系统进行配置，因此，必须在其他位置配置这些设置。</span><span class="sxs-lookup"><span data-stu-id="a9b85-221">Since ASP.NET Core apps are not tied to IIS and use a separate system for configuration, these settings must be configured elsewhere.</span></span> <span data-ttu-id="a9b85-222">大多数情况下，在文件中配置 ASP.NET Core 标识 `Startup.cs` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-222">For the most part, ASP.NET Core Identity is configured in the `Startup.cs` file.</span></span> <span data-ttu-id="a9b85-223">打开之前创建的 web 项目 (生成标识表架构) 并查看其 `Startup.cs` 文件。</span><span class="sxs-lookup"><span data-stu-id="a9b85-223">Open the web project that was created earlier (to generate the identity table schema) and review its `Startup.cs` file.</span></span>

<span data-ttu-id="a9b85-224">默认的 ConfigureServices 方法添加对 EF Core 和标识的支持：</span><span class="sxs-lookup"><span data-stu-id="a9b85-224">The default ConfigureServices method adds support for EF Core and Identity:</span></span>

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

<span data-ttu-id="a9b85-225">`AddDefaultIdentity`扩展方法用于将标识配置为使用默认值 `ApplicationDbContext` 和框架的 `IdentityUser` 类型。</span><span class="sxs-lookup"><span data-stu-id="a9b85-225">The `AddDefaultIdentity` extension method is used to configure Identity to use the default `ApplicationDbContext` and the framework's `IdentityUser` type.</span></span> <span data-ttu-id="a9b85-226">如果使用的是自定义 `IdentityUser` ，请确保在此处指定其类型。</span><span class="sxs-lookup"><span data-stu-id="a9b85-226">If you're using a custom `IdentityUser`, be sure to specify its type here.</span></span> <span data-ttu-id="a9b85-227">如果这些扩展方法在你的应用程序中不起作用，请检查你是否具有适当的 using 语句，以及你是否具有必要的 NuGet 包引用。</span><span class="sxs-lookup"><span data-stu-id="a9b85-227">If these extension methods aren't working in your application, check that you have the appropriate using statements and that you have the necessary NuGet package references.</span></span> <span data-ttu-id="a9b85-228">例如，你的项目应具有的某些版本 `Microsoft.AspNetCore.Identity.EntityFrameworkCore` 和 `Microsoft.AspNetCore.Identity.UI` 引用的包。</span><span class="sxs-lookup"><span data-stu-id="a9b85-228">For example, your project should have some version of the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` and `Microsoft.AspNetCore.Identity.UI` packages referenced.</span></span>

<span data-ttu-id="a9b85-229">此外，在中 `Startup.cs` ，你应看到为站点配置的必要中间件。</span><span class="sxs-lookup"><span data-stu-id="a9b85-229">Also in `Startup.cs` you should see the necessary middleware configured for the site.</span></span> <span data-ttu-id="a9b85-230">具体来说 `UseAuthentication` ， `UseAuthorization` 应在适当的位置设置和。</span><span class="sxs-lookup"><span data-stu-id="a9b85-230">Specifically, `UseAuthentication` and `UseAuthorization` should be set up, and in the proper location.</span></span>

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

<span data-ttu-id="a9b85-231">ASP.NET Identity 不会从匿名或基于角色的访问中配置位置 `Startup.cs` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-231">ASP.NET Identity does not configure anonymous or role-based access to locations from `Startup.cs`.</span></span> <span data-ttu-id="a9b85-232">需要将任何特定于位置的授权配置数据迁移到 ASP.NET Core 中的筛选器。</span><span class="sxs-lookup"><span data-stu-id="a9b85-232">You will need to migrate any location-specific authorization configuration data to filters in ASP.NET Core.</span></span> <span data-ttu-id="a9b85-233">请注意需要此类更新的文件夹和页面。</span><span class="sxs-lookup"><span data-stu-id="a9b85-233">Make note of which folders and pages will require such updates.</span></span> <span data-ttu-id="a9b85-234">你将在下一节中进行这些更改。</span><span class="sxs-lookup"><span data-stu-id="a9b85-234">You will make these changes in the next section.</span></span>

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a><span data-ttu-id="a9b85-235">更新单个页面以使用 ASP.NET Core 标识抽象化</span><span class="sxs-lookup"><span data-stu-id="a9b85-235">Updating individual pages to use ASP.NET Core Identity abstractions</span></span>

<span data-ttu-id="a9b85-236">在 ASP.NET Web 窗体应用程序中，如果你有 web.config 设置拒绝匿名用户访问某些页面或文件夹，则只需将 `[Authorize]` 属性添加到此类页即可迁移这些内容：</span><span class="sxs-lookup"><span data-stu-id="a9b85-236">In your ASP.NET Web Forms application, if you had web.config settings to deny access to certain pages or folders to anonymous users, you would migrate these by simply adding the `[Authorize]` attribute to such pages:</span></span>

```razor
@attribute [Authorize]
```

<span data-ttu-id="a9b85-237">如果你进一步拒绝了对属于特定角色的用户的访问，则你也可以通过添加指定角色的属性来迁移此操作：</span><span class="sxs-lookup"><span data-stu-id="a9b85-237">If you further had denied access except to those users belonging to a certain role, you would likewise migrate this by adding an attribute specifying a role:</span></span>

```razor
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="a9b85-238">请注意， `[Authorize]` 属性仅适用于 `@page` 通过路由器访问的组件 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-238">Note that the `[Authorize]` attribute only works on `@page` components that are reached via the Blazor Router.</span></span> <span data-ttu-id="a9b85-239">特性不适用于子组件，而子组件应改用 `AuthorizeView` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-239">The attribute does not work with child components, which should instead use `AuthorizeView`.</span></span>

<span data-ttu-id="a9b85-240">如果在页标记中有用于确定是否向特定用户显示某些代码的逻辑，则可以将其替换为 `AuthorizeView` 组件。</span><span class="sxs-lookup"><span data-stu-id="a9b85-240">If you have logic within page markup for determining whether to display some code to a certain user, you can replace this with the `AuthorizeView` component.</span></span> <span data-ttu-id="a9b85-241">[AuthorizeView 组件](/aspnet/core/blazor/security#authorizeview-component)根据用户是否有权查看它来有选择地显示 UI。</span><span class="sxs-lookup"><span data-stu-id="a9b85-241">The [AuthorizeView component](/aspnet/core/blazor/security#authorizeview-component) selectively displays UI depending on whether the user is authorized to see it.</span></span> <span data-ttu-id="a9b85-242">它还公开了 `context` 可用于访问用户信息的变量。</span><span class="sxs-lookup"><span data-stu-id="a9b85-242">It also exposes a `context` variable that can be used to access user information.</span></span>

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

<span data-ttu-id="a9b85-243">可以通过从配置为属性的中访问用户，来访问过程逻辑中的身份验证状态 `Task<AuthenticationState` `[CascadingParameter]` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-243">You can access authentication state within procedural logic by accessing the user from a `Task<AuthenticationState` configured with the `[CascadingParameter]` attribute.</span></span> <span data-ttu-id="a9b85-244">这会使你可以访问用户，这可以让你确定他们是否经过身份验证，以及他们是否属于特定角色。</span><span class="sxs-lookup"><span data-stu-id="a9b85-244">This will get you access to the user, which can let you determine if they are authenticated and if they belong to a particular role.</span></span> <span data-ttu-id="a9b85-245">如果需要评估策略过程，可以注入实例， `IAuthorizationService` 并对 `AuthorizeAsync` 其调用方法。</span><span class="sxs-lookup"><span data-stu-id="a9b85-245">If you need to evaluate a policy procedurally, you can inject an instance of the `IAuthorizationService` and calls the `AuthorizeAsync` method on it.</span></span> <span data-ttu-id="a9b85-246">下面的示例代码演示如何获取用户信息，并允许授权用户执行策略限制的任务 `content-editor` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-246">The following sample code demonstrates how to get user information and allow an authorized user to perform a task restricted by the `content-editor` policy.</span></span>

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

<span data-ttu-id="a9b85-247">`AuthenticationState`首先需要将设置为级联值，然后才能将其绑定到此类级联参数。</span><span class="sxs-lookup"><span data-stu-id="a9b85-247">The `AuthenticationState` does first need to be setup as a cascading value before it can be bound to a cascading parameter like this.</span></span> <span data-ttu-id="a9b85-248">通常使用组件完成此操作 `CascadingAuthenticationState` 。</span><span class="sxs-lookup"><span data-stu-id="a9b85-248">That's typically done using the `CascadingAuthenticationState` component.</span></span> <span data-ttu-id="a9b85-249">这通常在中完成 `App.razor` ：</span><span class="sxs-lookup"><span data-stu-id="a9b85-249">This is typically done in `App.razor`:</span></span>

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a><span data-ttu-id="a9b85-250">总结</span><span class="sxs-lookup"><span data-stu-id="a9b85-250">Summary</span></span>

<span data-ttu-id="a9b85-251">Blazor 使用与 ASP.NET Core 相同的安全模型，ASP.NET Core 标识。</span><span class="sxs-lookup"><span data-stu-id="a9b85-251">Blazor uses the same security model as ASP.NET Core, which is ASP.NET Core Identity.</span></span> <span data-ttu-id="a9b85-252">从通用提供程序迁移到 ASP.NET Core 标识相对简单，假设不太太多自定义应用到了原始数据架构。</span><span class="sxs-lookup"><span data-stu-id="a9b85-252">Migrating from universal providers to ASP.NET Core Identity is relatively straightforward, assuming not too much customization was applied to the original data schema.</span></span> <span data-ttu-id="a9b85-253">数据迁移完成后，在应用中使用身份验证和授权 Blazor ，可配置，同时提供对大多数安全要求的编程支持。</span><span class="sxs-lookup"><span data-stu-id="a9b85-253">Once the data has been migrated, working with authentication and authorization in Blazor apps is well-documented, with configurable as well as programmatic support for most security requirements.</span></span>

## <a name="references"></a><span data-ttu-id="a9b85-254">参考</span><span class="sxs-lookup"><span data-stu-id="a9b85-254">References</span></span>

- [<span data-ttu-id="a9b85-255">ASP.NET Core 上的标识简介</span><span class="sxs-lookup"><span data-stu-id="a9b85-255">Introduction to Identity on ASP.NET Core</span></span>](/aspnet/core/security/authentication/identity)
- [<span data-ttu-id="a9b85-256">从 ASP.NET 成员身份验证迁移到 ASP.NET Core 2.0 标识</span><span class="sxs-lookup"><span data-stu-id="a9b85-256">Migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity</span></span>](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [<span data-ttu-id="a9b85-257">将身份验证和标识迁移到 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a9b85-257">Migrate Authentication and Identity to ASP.NET Core</span></span>](/aspnet/core/migration/identity)
- [<span data-ttu-id="a9b85-258">ASP.NET Core Blazor 身份验证和授权</span><span class="sxs-lookup"><span data-stu-id="a9b85-258">ASP.NET Core Blazor authentication and authorization</span></span>](/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
><span data-ttu-id="a9b85-259">[上一页](config.md)
>[下一页](migration.md)</span><span class="sxs-lookup"><span data-stu-id="a9b85-259">[Previous](config.md)
[Next](migration.md)</span></span>
