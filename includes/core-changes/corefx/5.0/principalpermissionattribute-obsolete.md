---
ms.openlocfilehash: 2c8a5c1ec87918a91600a3557c679a42cae74896
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556318"
---
### <a name="principalpermissionattribute-is-obsolete-as-error"></a><span data-ttu-id="d93dd-101">PrincipalPermissionAttribute 已过时，报告为错误</span><span class="sxs-lookup"><span data-stu-id="d93dd-101">PrincipalPermissionAttribute is obsolete as error</span></span>

<span data-ttu-id="d93dd-102"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 构造函数已过时，会产生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="d93dd-102">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="d93dd-103">不能实例化此属性或将其应用于方法。</span><span class="sxs-lookup"><span data-stu-id="d93dd-103">You cannot instantiate this attribute or apply it to a method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d93dd-104">更改描述</span><span class="sxs-lookup"><span data-stu-id="d93dd-104">Change description</span></span>

<span data-ttu-id="d93dd-105">在 .NET Framework 和 .NET Core 上，可以用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性批注方法。</span><span class="sxs-lookup"><span data-stu-id="d93dd-105">On .NET Framework and .NET Core, you can annotate methods with the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute.</span></span> <span data-ttu-id="d93dd-106">例如：</span><span class="sxs-lookup"><span data-stu-id="d93dd-106">For example:</span></span>

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

<span data-ttu-id="d93dd-107">从 .NET 5.0 开始，不能将 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性应用于方法。</span><span class="sxs-lookup"><span data-stu-id="d93dd-107">Starting in .NET 5.0, you cannot apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a method.</span></span> <span data-ttu-id="d93dd-108">该属性的构造函数已过时，会产生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="d93dd-108">The constructor for the attribute is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="d93dd-109">与其他过时警告不同，无法禁止显示此错误。</span><span class="sxs-lookup"><span data-stu-id="d93dd-109">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d93dd-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="d93dd-110">Reason for change</span></span>

<span data-ttu-id="d93dd-111"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 类型与子类 <xref:System.Security.Permissions.SecurityAttribute> 等其他类型一样，是 .NET 的代码访问安全性 (CAS) 基础结构的一部分。</span><span class="sxs-lookup"><span data-stu-id="d93dd-111">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, like other types that subclass <xref:System.Security.Permissions.SecurityAttribute>, is part of .NET's Code Access Security (CAS) infrastructure.</span></span> <span data-ttu-id="d93dd-112">在 .NET Framework 2.x - 4.x 中，即使应用程序在完全信任的情况下运行，运行时也会在方法条目上强制使用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 批注。</span><span class="sxs-lookup"><span data-stu-id="d93dd-112">In .NET Framework 2.x - 4.x, the runtime enforces <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations on method entry, even if the application is running under a full-trust scenario.</span></span> <span data-ttu-id="d93dd-113">.NET Core 和 .NET 5.0 及更高版本不支持 CAS 属性，并且运行时将忽略这些属性。</span><span class="sxs-lookup"><span data-stu-id="d93dd-113">.NET Core and .NET 5.0 and later don't support CAS attributes, and the runtime ignores them.</span></span>

<span data-ttu-id="d93dd-114">从 .NET Framework 到 .NET Core 和 .NET 5.0 的行为差异可能导致“无法打开”的情况，在这种情况下，本应阻止但却允许了访问。</span><span class="sxs-lookup"><span data-stu-id="d93dd-114">This difference in behavior from .NET Framework to .NET Core and .NET 5.0 can result in a "fail open" scenario, where access should have been blocked but instead has been allowed.</span></span> <span data-ttu-id="d93dd-115">为防止出现“无法打开”的情况，你不能再在面向 .NET 5.0 或更高版本的代码中应用该属性。</span><span class="sxs-lookup"><span data-stu-id="d93dd-115">To prevent the "fail open" scenario, you can no longer apply the attribute in code that targets .NET 5.0 or later.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d93dd-116">引入的版本</span><span class="sxs-lookup"><span data-stu-id="d93dd-116">Version introduced</span></span>

<span data-ttu-id="d93dd-117">5.0 预览版 7</span><span class="sxs-lookup"><span data-stu-id="d93dd-117">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d93dd-118">建议操作</span><span class="sxs-lookup"><span data-stu-id="d93dd-118">Recommended action</span></span>

<span data-ttu-id="d93dd-119">如果遇到过时错误，则必须采取措施。</span><span class="sxs-lookup"><span data-stu-id="d93dd-119">If you encounter the obsoletion error, you must take action.</span></span>

- <span data-ttu-id="d93dd-120">**如果要将属性应用于 ASP.NET MVC 操作方法，请执行以下操作：**</span><span class="sxs-lookup"><span data-stu-id="d93dd-120">**If you're applying the attribute to an ASP.NET MVC action method:**</span></span>

  <span data-ttu-id="d93dd-121">考虑使用 ASP.NET 的内置授权基础结构。</span><span class="sxs-lookup"><span data-stu-id="d93dd-121">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="d93dd-122">以下代码演示如何使用 <xref:System.Web.Mvc.AuthorizeAttribute> 属性来为控制器添加批注。</span><span class="sxs-lookup"><span data-stu-id="d93dd-122">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="d93dd-123">ASP.NET 运行时将在执行操作之前向用户授权。</span><span class="sxs-lookup"><span data-stu-id="d93dd-123">The ASP.NET runtime will authorize the user before performing the action.</span></span>

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  <span data-ttu-id="d93dd-124">有关详细信息，请参阅 [ASP.NET Core 中基于角色的授权](/aspnet/core/security/authorization/roles)和 [ASP.NET Core 中的授权简介](/aspnet/core/security/authorization/introduction)。</span><span class="sxs-lookup"><span data-stu-id="d93dd-124">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="d93dd-125">**如果要将属性应用到 Web 应用上下文之外的库代码，请执行以下操作：**</span><span class="sxs-lookup"><span data-stu-id="d93dd-125">**If you're applying the attribute to library code outside the context of a web app:**</span></span>

  <span data-ttu-id="d93dd-126">在方法开始时手动执行检查。</span><span class="sxs-lookup"><span data-stu-id="d93dd-126">Perform the checks manually at the beginning of your method.</span></span> <span data-ttu-id="d93dd-127">这可以通过使用 <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> 方法来完成。</span><span class="sxs-lookup"><span data-stu-id="d93dd-127">This can be done by using the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

#### <a name="category"></a><span data-ttu-id="d93dd-128">类别</span><span class="sxs-lookup"><span data-stu-id="d93dd-128">Category</span></span>

- <span data-ttu-id="d93dd-129">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="d93dd-129">Core .NET libraries</span></span>
- <span data-ttu-id="d93dd-130">安全性</span><span class="sxs-lookup"><span data-stu-id="d93dd-130">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d93dd-131">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="d93dd-131">Affected APIs</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
