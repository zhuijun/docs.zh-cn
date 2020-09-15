---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617124"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a><span data-ttu-id="16550-101">System.Uri 分析符合 RFC 3987</span><span class="sxs-lookup"><span data-stu-id="16550-101">System.Uri parsing adheres to RFC 3987</span></span>

#### <a name="details"></a><span data-ttu-id="16550-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="16550-102">Details</span></span>

<span data-ttu-id="16550-103">在 .NET Framework 4.5 中，对 URI 分析做了几方面的更改。</span><span class="sxs-lookup"><span data-stu-id="16550-103">URI parsing has changed in several ways in .NET Framework 4.5.</span></span> <span data-ttu-id="16550-104">但请注意，这些更改仅影响面向 .NET Framework 4.5 的代码。</span><span class="sxs-lookup"><span data-stu-id="16550-104">Note, however, that these changes only affect code targeting .NET Framework 4.5.</span></span> <span data-ttu-id="16550-105">如果二进制文件面向 .NET Framework 4.0，则将遵守旧行为。</span><span class="sxs-lookup"><span data-stu-id="16550-105">If a binary targets .NET Framework 4.0, the old behavior will be observed.</span></span> <span data-ttu-id="16550-106">.NET Framework 4.5 中对 URI 分析所做的更改包括：</span><span class="sxs-lookup"><span data-stu-id="16550-106">Changes to URI parsing in .NET Framework 4.5 include:</span></span>

- <span data-ttu-id="16550-107">URI 分析将根据 RFC 3987 中的最新 IRI 规则执行规范化和字符检查。</span><span class="sxs-lookup"><span data-stu-id="16550-107">URI parsing will perform normalization and character checking according to the latest IRI rules in RFC 3987.</span></span>
- <span data-ttu-id="16550-108">将仅对 URI 的主机部分执行 Unicode 范式 C。</span><span class="sxs-lookup"><span data-stu-id="16550-108">Unicode normalization form C will only be performed on the host portion of the URI.</span></span>
- <span data-ttu-id="16550-109">无效 mailto：URI 现在会抛出异常。</span><span class="sxs-lookup"><span data-stu-id="16550-109">Invalid mailto: URIs will now cause an exception.</span></span>
- <span data-ttu-id="16550-110">现在将保留路径段末尾的尾随点。</span><span class="sxs-lookup"><span data-stu-id="16550-110">Trailing dots at the end of a path segment are now preserved.</span></span>
- <span data-ttu-id="16550-111">`file://` URI 不会转义 `?` 字符。</span><span class="sxs-lookup"><span data-stu-id="16550-111">`file://` URIs do not escape the `?` character.</span></span>
- <span data-ttu-id="16550-112">不支持从 `U+0080` 到 `U+009F` 的 Unicode 控制字符。</span><span class="sxs-lookup"><span data-stu-id="16550-112">Unicode control characters `U+0080` through `U+009F` are not supported.</span></span>
- <span data-ttu-id="16550-113">逗号字符 `,` 或 `%2c` 不会自动取消转义。</span><span class="sxs-lookup"><span data-stu-id="16550-113">Comma characters `,` or `%2c` are not automatically unescaped.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="16550-114">建议</span><span class="sxs-lookup"><span data-stu-id="16550-114">Suggestion</span></span>

<span data-ttu-id="16550-115">如果需要使用旧的 .NET Framework 4.0 URI 分析语义（通常不需要），可通过面向 .NET Framework 4.0 使用它们。</span><span class="sxs-lookup"><span data-stu-id="16550-115">If the old .NET Framework 4.0 URI parsing semantics are necessary (they often aren't), they can be used by targeting .NET Framework 4.0.</span></span> <span data-ttu-id="16550-116">这可通过在程序集上使用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> 来实现，也可以通过“项目属性”页中 Visual Studio 的项目系统 UI 来实现。</span><span class="sxs-lookup"><span data-stu-id="16550-116">This can be accomplished by using a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> on the assembly, or through Visual Studio's project system UI in the 'project properties' page.</span></span>

| <span data-ttu-id="16550-117">“属性”</span><span class="sxs-lookup"><span data-stu-id="16550-117">Name</span></span>    | <span data-ttu-id="16550-118">“值”</span><span class="sxs-lookup"><span data-stu-id="16550-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="16550-119">范围</span><span class="sxs-lookup"><span data-stu-id="16550-119">Scope</span></span>   | <span data-ttu-id="16550-120">主要</span><span class="sxs-lookup"><span data-stu-id="16550-120">Major</span></span>       |
| <span data-ttu-id="16550-121">Version</span><span class="sxs-lookup"><span data-stu-id="16550-121">Version</span></span> | <span data-ttu-id="16550-122">4.5</span><span class="sxs-lookup"><span data-stu-id="16550-122">4.5</span></span>         |
| <span data-ttu-id="16550-123">类型</span><span class="sxs-lookup"><span data-stu-id="16550-123">Type</span></span>    | <span data-ttu-id="16550-124">重定目标</span><span class="sxs-lookup"><span data-stu-id="16550-124">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="16550-125">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="16550-125">Affected APIs</span></span>

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
