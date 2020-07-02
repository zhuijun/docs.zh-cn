---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621047"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="eaa87-101">现在支持 Unicode 标准版本 8.0 类别</span><span class="sxs-lookup"><span data-stu-id="eaa87-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="eaa87-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="eaa87-102">Details</span></span>

<span data-ttu-id="eaa87-103">在 .NET Framework 4.6.2 中，Unicode 数据已从 Unicode 标准版本 6.3 升级到版本 8.0。</span><span class="sxs-lookup"><span data-stu-id="eaa87-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="eaa87-104">在 .NET Framework 4.6.2 中请求 Unicode 字符类别时，某些结果可能与以前的 .NET Framework 版本中的结果不匹配。</span><span class="sxs-lookup"><span data-stu-id="eaa87-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="eaa87-105">此更改主要影响切罗基语音节和西双版纳新傣文元音标记和音调标记。</span><span class="sxs-lookup"><span data-stu-id="eaa87-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="eaa87-106">建议</span><span class="sxs-lookup"><span data-stu-id="eaa87-106">Suggestion</span></span>

<span data-ttu-id="eaa87-107">检查代码并删除/更改依赖硬编码 Unicode 字符类别的逻辑。</span><span class="sxs-lookup"><span data-stu-id="eaa87-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="eaa87-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="eaa87-108">Name</span></span>    | <span data-ttu-id="eaa87-109">值</span><span class="sxs-lookup"><span data-stu-id="eaa87-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="eaa87-110">范围</span><span class="sxs-lookup"><span data-stu-id="eaa87-110">Scope</span></span>   |<span data-ttu-id="eaa87-111">次要</span><span class="sxs-lookup"><span data-stu-id="eaa87-111">Minor</span></span>|
|<span data-ttu-id="eaa87-112">Version</span><span class="sxs-lookup"><span data-stu-id="eaa87-112">Version</span></span>|<span data-ttu-id="eaa87-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="eaa87-113">4.6.2</span></span>|
|<span data-ttu-id="eaa87-114">类型</span><span class="sxs-lookup"><span data-stu-id="eaa87-114">Type</span></span>|<span data-ttu-id="eaa87-115">运行时</span><span class="sxs-lookup"><span data-stu-id="eaa87-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eaa87-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="eaa87-116">Affected APIs</span></span>

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
