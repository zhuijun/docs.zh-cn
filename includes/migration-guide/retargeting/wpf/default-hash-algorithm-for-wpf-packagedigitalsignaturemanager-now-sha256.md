---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614407"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a><span data-ttu-id="312cf-101">WPF PackageDigitalSignatureManager 现在的默认哈希算法是 SHA256</span><span class="sxs-lookup"><span data-stu-id="312cf-101">The default hash algorithm for WPF PackageDigitalSignatureManager is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="312cf-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="312cf-102">Details</span></span>

<span data-ttu-id="312cf-103">`System.IO.Packaging.PackageDigitalSignatureManager` 提供与 WPF 包相关的数字签名功能。</span><span class="sxs-lookup"><span data-stu-id="312cf-103">The `System.IO.Packaging.PackageDigitalSignatureManager` provides functionality for digital signatures in relation to WPF packages.</span></span>  <span data-ttu-id="312cf-104">在 .NET Framework 4.7 和更早版本中，包的签名部分使用的默认算法 (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) 是 SHA1。</span><span class="sxs-lookup"><span data-stu-id="312cf-104">In the .NET Framework 4.7 and earlier versions, the default algorithm (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) used for signing parts of a package was SHA1.</span></span>  <span data-ttu-id="312cf-105">由于 SHA1 最近的安全问题，从 .NET Framework 4.7.1 起，此默认算法已更改为 SHA256。</span><span class="sxs-lookup"><span data-stu-id="312cf-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.1.</span></span>  <span data-ttu-id="312cf-106">此更改会影响所有包签名，包括 XPS 文档。</span><span class="sxs-lookup"><span data-stu-id="312cf-106">This change affects all package signing, including XPS documents.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="312cf-107">建议</span><span class="sxs-lookup"><span data-stu-id="312cf-107">Suggestion</span></span>

<span data-ttu-id="312cf-108">面向 .NET Framework 4.7.1 以下框架版本并需要利用此更改的开发人员或者面向 .NET Framework 4.7.1 或更高版本并需要之前功能的开发人员可以正确设置以下 AppContext 标记。</span><span class="sxs-lookup"><span data-stu-id="312cf-108">A developer who wants to utilize this change while targeting a framework version below .NET Framework 4.7.1 or a developer who requires the previous functionality while targeting .NET Framework 4.7.1 or greater can set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="312cf-109">值为 true 将导致 SHA1 作为默认算法使用；而 false 则导致 SHA256 作为默认算法使用。</span><span class="sxs-lookup"><span data-stu-id="312cf-109">A value of true will result in SHA1 being used as the default algorithm; false results in SHA256.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="312cf-110">名称</span><span class="sxs-lookup"><span data-stu-id="312cf-110">Name</span></span>    | <span data-ttu-id="312cf-111">“值”</span><span class="sxs-lookup"><span data-stu-id="312cf-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="312cf-112">范围</span><span class="sxs-lookup"><span data-stu-id="312cf-112">Scope</span></span>   | <span data-ttu-id="312cf-113">边缘</span><span class="sxs-lookup"><span data-stu-id="312cf-113">Edge</span></span>        |
| <span data-ttu-id="312cf-114">Version</span><span class="sxs-lookup"><span data-stu-id="312cf-114">Version</span></span> | <span data-ttu-id="312cf-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="312cf-115">4.7.1</span></span>       |
| <span data-ttu-id="312cf-116">类型</span><span class="sxs-lookup"><span data-stu-id="312cf-116">Type</span></span>    | <span data-ttu-id="312cf-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="312cf-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="312cf-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="312cf-118">Affected APIs</span></span>

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>
