---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614323"
---
### <a name="calls-to-claimsidentity-constructors"></a><span data-ttu-id="a6dd0-101">调用 ClaimsIdentity 构造函数</span><span class="sxs-lookup"><span data-stu-id="a6dd0-101">Calls to ClaimsIdentity constructors</span></span>

#### <a name="details"></a><span data-ttu-id="a6dd0-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="a6dd0-102">Details</span></span>

<span data-ttu-id="a6dd0-103">从 .NET Framework 4.6.2 开始，具有 <xref:System.Security.Principal.IIdentity?displayProperty=fullName> 参数的 <xref:System.Security.Claims.ClaimsIdentity> 构造函数设置 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 属性的方式发生了变化。</span><span class="sxs-lookup"><span data-stu-id="a6dd0-103">Starting with the .NET Framework 4.6.2, there is a change in how <xref:System.Security.Claims.ClaimsIdentity> constructors with an <xref:System.Security.Principal.IIdentity?displayProperty=fullName> parameter set the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property.</span></span> <span data-ttu-id="a6dd0-104">如果 <xref:System.Security.Principal.IIdentity?displayProperty=fullName> 参数是 <xref:System.Security.Claims.ClaimsIdentity> 对象，且该 <xref:System.Security.Claims.ClaimsIdentity> 对象的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 属性不为 `null`，则 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 属性是使用 <xref:System.Security.Claims.ClaimsIdentity.Clone> 方法附加的。</span><span class="sxs-lookup"><span data-stu-id="a6dd0-104">If the <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument is a <xref:System.Security.Claims.ClaimsIdentity> object, and the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of that <xref:System.Security.Claims.ClaimsIdentity> object is not `null`, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached by using the <xref:System.Security.Claims.ClaimsIdentity.Clone> method.</span></span> <span data-ttu-id="a6dd0-105">在 Framework 4.6.1 及早期版本中，<xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 属性作为现有引用进行附加。由于此更改，从 .NET Framework 4.6.2 开始，新 <xref:System.Security.Claims.ClaimsIdentity> 对象的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 属性不等于构造函数的 <xref:System.Security.Principal.IIdentity?displayProperty=fullName> 参数的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 属性。</span><span class="sxs-lookup"><span data-stu-id="a6dd0-105">In the Framework 4.6.1 and earlier versions, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached as an existing reference.Because of this change, starting with the .NET Framework 4.6.2, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the new <xref:System.Security.Claims.ClaimsIdentity> object is not equal to the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the constructor's <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument.</span></span> <span data-ttu-id="a6dd0-106">在 .NET Framework 4.6.1 及更早版本中，它们是相等的。</span><span class="sxs-lookup"><span data-stu-id="a6dd0-106">In the .NET Framework 4.6.1 and earlier versions, it is equal.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a6dd0-107">建议</span><span class="sxs-lookup"><span data-stu-id="a6dd0-107">Suggestion</span></span>

<span data-ttu-id="a6dd0-108">如果不需要此行为，可以在应用程序配置文件中将 `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` 开关设置为 `true`，从而还原旧行为。</span><span class="sxs-lookup"><span data-stu-id="a6dd0-108">If this behavior is undesirable, you can restore the previous behavior by setting the `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` switch in your application configuration file to `true`.</span></span> <span data-ttu-id="a6dd0-109">为此，必须在 web.config 文件的 `<runtime>` 部分中添加以下内容：</span><span class="sxs-lookup"><span data-stu-id="a6dd0-109">This requires that you add the following to the `<runtime>` section of your web.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="a6dd0-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="a6dd0-110">Name</span></span>    | <span data-ttu-id="a6dd0-111">“值”</span><span class="sxs-lookup"><span data-stu-id="a6dd0-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a6dd0-112">范围</span><span class="sxs-lookup"><span data-stu-id="a6dd0-112">Scope</span></span>   | <span data-ttu-id="a6dd0-113">边缘</span><span class="sxs-lookup"><span data-stu-id="a6dd0-113">Edge</span></span>        |
| <span data-ttu-id="a6dd0-114">Version</span><span class="sxs-lookup"><span data-stu-id="a6dd0-114">Version</span></span> | <span data-ttu-id="a6dd0-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="a6dd0-115">4.6.2</span></span>       |
| <span data-ttu-id="a6dd0-116">类型</span><span class="sxs-lookup"><span data-stu-id="a6dd0-116">Type</span></span>    | <span data-ttu-id="a6dd0-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="a6dd0-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="a6dd0-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="a6dd0-118">Affected APIs</span></span>

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>
