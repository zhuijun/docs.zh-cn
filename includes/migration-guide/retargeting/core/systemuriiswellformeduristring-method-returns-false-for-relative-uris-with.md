---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617125"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a><span data-ttu-id="c58bf-101">System.Uri.IsWellFormedUriString 方法为第一个段中具有冒号字符型的相对 URI 返回 false</span><span class="sxs-lookup"><span data-stu-id="c58bf-101">System.Uri.IsWellFormedUriString method returns false for relative URIs with a colon char in first segment</span></span>

#### <a name="details"></a><span data-ttu-id="c58bf-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c58bf-102">Details</span></span>

<span data-ttu-id="c58bf-103">从 .NET Framework 4.5 开始，<xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> 会将第一个段中带有 `:` 的相对 URI 视为格式不正确。</span><span class="sxs-lookup"><span data-stu-id="c58bf-103">Beginning with the .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> will treat relative URIs with a `:` in their first segment as not well formed.</span></span> <span data-ttu-id="c58bf-104">这是 .NET Framework 4.0 中 <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> 行为的更改，以符合 RFC3986。</span><span class="sxs-lookup"><span data-stu-id="c58bf-104">This is a change from <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> behavior in the .NET Framework 4.0 that was made to conform to RFC3986.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c58bf-105">建议</span><span class="sxs-lookup"><span data-stu-id="c58bf-105">Suggestion</span></span>

<span data-ttu-id="c58bf-106">此更改（与许多其他 URI 更改一样）仅影响以 .NET Framework 4.5（或更高版本）为目标的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c58bf-106">This change (like many other URI changes) will only affect applications targeting the .NET Framework 4.5 (or later).</span></span> <span data-ttu-id="c58bf-107">要继续使用旧行为，请使应用以 .NET Framework 4.0 为目标。</span><span class="sxs-lookup"><span data-stu-id="c58bf-107">To keep using the old behavior, target the app against the .NET Framework 4.0.</span></span> <span data-ttu-id="c58bf-108">或者，调用 <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> 前扫描 URI，查找出于验证目的想要删除的 `:` 字符（如果旧行为是可取的）。</span><span class="sxs-lookup"><span data-stu-id="c58bf-108">Alternatively, scan URI's prior to calling <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> looking for `:` characters that you may want to remove for validation purposes, if the old behavior is desirable.</span></span>

| <span data-ttu-id="c58bf-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="c58bf-109">Name</span></span>    | <span data-ttu-id="c58bf-110">“值”</span><span class="sxs-lookup"><span data-stu-id="c58bf-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c58bf-111">范围</span><span class="sxs-lookup"><span data-stu-id="c58bf-111">Scope</span></span>   | <span data-ttu-id="c58bf-112">次要</span><span class="sxs-lookup"><span data-stu-id="c58bf-112">Minor</span></span>       |
| <span data-ttu-id="c58bf-113">Version</span><span class="sxs-lookup"><span data-stu-id="c58bf-113">Version</span></span> | <span data-ttu-id="c58bf-114">4.5</span><span class="sxs-lookup"><span data-stu-id="c58bf-114">4.5</span></span>         |
| <span data-ttu-id="c58bf-115">类型</span><span class="sxs-lookup"><span data-stu-id="c58bf-115">Type</span></span>    | <span data-ttu-id="c58bf-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="c58bf-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c58bf-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c58bf-117">Affected APIs</span></span>

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
