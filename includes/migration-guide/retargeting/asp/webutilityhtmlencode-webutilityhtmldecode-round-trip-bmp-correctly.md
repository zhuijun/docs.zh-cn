---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617118"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a><span data-ttu-id="1966c-101">WebUtility.HtmlEncode 和 WebUtility.HtmlDecode 正确往返 BMP</span><span class="sxs-lookup"><span data-stu-id="1966c-101">WebUtility.HtmlEncode and WebUtility.HtmlDecode round-trip BMP correctly</span></span>

#### <a name="details"></a><span data-ttu-id="1966c-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1966c-102">Details</span></span>

<span data-ttu-id="1966c-103">对于面向 .NET Framework 4.5 的应用程序，当基本多语言平面 (BMP) 外的字符传递给 <xref:System.Net.WebUtility.HtmlDecode(System.String)> 方法时，这些字符可正确往返。</span><span class="sxs-lookup"><span data-stu-id="1966c-103">For applications that target the .NET Framework 4.5, characters that are outside the Basic Multilingual Plane (BMP) round-trip correctly when they are passed to the <xref:System.Net.WebUtility.HtmlDecode(System.String)> methods.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1966c-104">建议</span><span class="sxs-lookup"><span data-stu-id="1966c-104">Suggestion</span></span>

<span data-ttu-id="1966c-105">此更改不应影响当前应用程序，但要还原原始行为，请将 `<httpRuntime>` 元素的 `targetFramework` 属性设置为“4.5”以外的字符串。</span><span class="sxs-lookup"><span data-stu-id="1966c-105">This change should have no effect on current applications, but to restore the original behavior, set the `targetFramework` attribute of the `<httpRuntime>` element to a string other than "4.5".</span></span> <span data-ttu-id="1966c-106">还可以设置 `unicodeEncodingConformance` 配置元素的 `unicodeDecodingConformance` 和 `<webUtility>` 特性以单独控制 .NET Framework 的目标版本的行为。</span><span class="sxs-lookup"><span data-stu-id="1966c-106">You can also set the `unicodeEncodingConformance` and `unicodeDecodingConformance` attributes of the `<webUtility>` configuration element to control this behavior independently of the targeted version of the .NET Framework.</span></span>

| <span data-ttu-id="1966c-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="1966c-107">Name</span></span>    | <span data-ttu-id="1966c-108">“值”</span><span class="sxs-lookup"><span data-stu-id="1966c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1966c-109">范围</span><span class="sxs-lookup"><span data-stu-id="1966c-109">Scope</span></span>   | <span data-ttu-id="1966c-110">边缘</span><span class="sxs-lookup"><span data-stu-id="1966c-110">Edge</span></span>        |
| <span data-ttu-id="1966c-111">Version</span><span class="sxs-lookup"><span data-stu-id="1966c-111">Version</span></span> | <span data-ttu-id="1966c-112">4.5</span><span class="sxs-lookup"><span data-stu-id="1966c-112">4.5</span></span>         |
| <span data-ttu-id="1966c-113">类型</span><span class="sxs-lookup"><span data-stu-id="1966c-113">Type</span></span>    | <span data-ttu-id="1966c-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="1966c-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="1966c-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1966c-115">Affected APIs</span></span>

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
