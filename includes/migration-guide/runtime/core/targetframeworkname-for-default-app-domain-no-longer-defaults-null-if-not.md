---
ms.openlocfilehash: 4e685722271a8079e727ea9c2e0e501f68b30fc9
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496340"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a><span data-ttu-id="1185d-101">默认应用域的 TargetFrameworkName 不再默认为 null（如果未设置）</span><span class="sxs-lookup"><span data-stu-id="1185d-101">TargetFrameworkName for default app domain no longer defaults to null if not set</span></span>

#### <a name="details"></a><span data-ttu-id="1185d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1185d-102">Details</span></span>

<span data-ttu-id="1185d-103">以前，除非显式设置，否则默认应用域中的 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> 为 null。</span><span class="sxs-lookup"><span data-stu-id="1185d-103">The <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> was previously null in the default app domain, unless it was explicitly set.</span></span> <span data-ttu-id="1185d-104">从 4.6 开始，默认应用域的 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> 属性将具有派生自 TargetFrameworkAttribute 的默认值（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="1185d-104">Beginning in 4.6, the <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> property for the default app domain will have a default value derived from the TargetFrameworkAttribute (if one is present).</span></span> <span data-ttu-id="1185d-105">除非显式重写，否则非默认应用域将继续从默认应用域继承 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>（在 4.6 中不会默认为 null）。</span><span class="sxs-lookup"><span data-stu-id="1185d-105">Non-default app domains will continue to inherit their <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> from the default app domain (which will not default to null in 4.6) unless it is explicitly overridden.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1185d-106">建议</span><span class="sxs-lookup"><span data-stu-id="1185d-106">Suggestion</span></span>

<span data-ttu-id="1185d-107">应更新代码，以独立于默认为 null 的 <xref:System.AppDomainSetup.TargetFrameworkName>。</span><span class="sxs-lookup"><span data-stu-id="1185d-107">Code should be updated to not depend on <xref:System.AppDomainSetup.TargetFrameworkName> defaulting to null.</span></span> <span data-ttu-id="1185d-108">如果需要此属性继续评估为 null，它可显式设为该值。</span><span class="sxs-lookup"><span data-stu-id="1185d-108">If it is required that this property continue to evaluate to null, it can be explicitly set to that value.</span></span>

| <span data-ttu-id="1185d-109">名称</span><span class="sxs-lookup"><span data-stu-id="1185d-109">Name</span></span>    | <span data-ttu-id="1185d-110">值</span><span class="sxs-lookup"><span data-stu-id="1185d-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1185d-111">范围</span><span class="sxs-lookup"><span data-stu-id="1185d-111">Scope</span></span>   |<span data-ttu-id="1185d-112">边缘</span><span class="sxs-lookup"><span data-stu-id="1185d-112">Edge</span></span>|
|<span data-ttu-id="1185d-113">Version</span><span class="sxs-lookup"><span data-stu-id="1185d-113">Version</span></span>|<span data-ttu-id="1185d-114">4.6</span><span class="sxs-lookup"><span data-stu-id="1185d-114">4.6</span></span>|
|<span data-ttu-id="1185d-115">类型</span><span class="sxs-lookup"><span data-stu-id="1185d-115">Type</span></span>|<span data-ttu-id="1185d-116">运行时</span><span class="sxs-lookup"><span data-stu-id="1185d-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1185d-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1185d-117">Affected APIs</span></span>

- <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.AppDomainSetup.TargetFrameworkName`

-->
