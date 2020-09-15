---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615612"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a><span data-ttu-id="b7918-101">调用具有 null 自变量的 CreateDefaultAuthorizationContext 的方式已更改</span><span class="sxs-lookup"><span data-stu-id="b7918-101">Calling CreateDefaultAuthorizationContext with a null argument has changed</span></span>

#### <a name="details"></a><span data-ttu-id="b7918-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b7918-102">Details</span></span>

<span data-ttu-id="b7918-103">调用具有 null authorizationPolicies 自变量的 <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> 所返回的 <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> 实现更改了其在 .NET Framework 4.6 中的实现。</span><span class="sxs-lookup"><span data-stu-id="b7918-103">The implementation of the <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> returned by a call to the <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> with a null authorizationPolicies argument has changed its implementation in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b7918-104">建议</span><span class="sxs-lookup"><span data-stu-id="b7918-104">Suggestion</span></span>

<span data-ttu-id="b7918-105">在极少数情况下，使用自定义身份验证的 WCF 应用可能会看到行为差异。</span><span class="sxs-lookup"><span data-stu-id="b7918-105">In rare cases, WCF apps that use custom authentication may see behavioral differences.</span></span> <span data-ttu-id="b7918-106">在这类情况下，可使用以下两种方式之一还原以前的行为：</span><span class="sxs-lookup"><span data-stu-id="b7918-106">In such cases, the previous behavior can be restored in either of two ways:</span></span>

- <span data-ttu-id="b7918-107">重新编译你的应用以面向早于 4.6 的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="b7918-107">Recompile your app to target an earlier version of the .NET Framework than 4.6.</span></span> <span data-ttu-id="b7918-108">对于 IIS 承载的服务，请使用 `<httpRuntime targetFramework="x.x">` 元素以面向早期版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="b7918-108">For IIS-hosted services, use the `<httpRuntime targetFramework="x.x">` element to target an earlier version of the .NET Framework.</span></span>
- <span data-ttu-id="b7918-109">将下面的行添加到 app.config 文件的 `<appSettings>` 部分：</span><span class="sxs-lookup"><span data-stu-id="b7918-109">Add the following line to the `<appSettings>` section of your app.config file:</span></span>

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| <span data-ttu-id="b7918-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="b7918-110">Name</span></span>    | <span data-ttu-id="b7918-111">“值”</span><span class="sxs-lookup"><span data-stu-id="b7918-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b7918-112">范围</span><span class="sxs-lookup"><span data-stu-id="b7918-112">Scope</span></span>   | <span data-ttu-id="b7918-113">次要</span><span class="sxs-lookup"><span data-stu-id="b7918-113">Minor</span></span>       |
| <span data-ttu-id="b7918-114">Version</span><span class="sxs-lookup"><span data-stu-id="b7918-114">Version</span></span> | <span data-ttu-id="b7918-115">4.6</span><span class="sxs-lookup"><span data-stu-id="b7918-115">4.6</span></span>         |
| <span data-ttu-id="b7918-116">类型</span><span class="sxs-lookup"><span data-stu-id="b7918-116">Type</span></span>    | <span data-ttu-id="b7918-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="b7918-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b7918-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="b7918-118">Affected APIs</span></span>

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>
