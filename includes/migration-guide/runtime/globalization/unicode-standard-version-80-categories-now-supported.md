---
ms.openlocfilehash: f389a9e9bcf4ac1777db66731a085d74889c4a98
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496740"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="d6a94-101">现在支持 Unicode 标准版本 8.0 类别</span><span class="sxs-lookup"><span data-stu-id="d6a94-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="d6a94-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="d6a94-102">Details</span></span>

<span data-ttu-id="d6a94-103">在 .NET Framework 4.6.2 中，Unicode 数据已从 Unicode 标准版本 6.3 升级到版本 8.0。</span><span class="sxs-lookup"><span data-stu-id="d6a94-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="d6a94-104">在 .NET Framework 4.6.2 中请求 Unicode 字符类别时，某些结果可能与以前的 .NET Framework 版本中的结果不匹配。</span><span class="sxs-lookup"><span data-stu-id="d6a94-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="d6a94-105">此更改主要影响切罗基语音节和西双版纳新傣文元音标记和音调标记。</span><span class="sxs-lookup"><span data-stu-id="d6a94-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d6a94-106">建议</span><span class="sxs-lookup"><span data-stu-id="d6a94-106">Suggestion</span></span>

<span data-ttu-id="d6a94-107">检查代码并删除/更改依赖硬编码 Unicode 字符类别的逻辑。</span><span class="sxs-lookup"><span data-stu-id="d6a94-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="d6a94-108">名称</span><span class="sxs-lookup"><span data-stu-id="d6a94-108">Name</span></span>    | <span data-ttu-id="d6a94-109">值</span><span class="sxs-lookup"><span data-stu-id="d6a94-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d6a94-110">范围</span><span class="sxs-lookup"><span data-stu-id="d6a94-110">Scope</span></span>   |<span data-ttu-id="d6a94-111">次要</span><span class="sxs-lookup"><span data-stu-id="d6a94-111">Minor</span></span>|
|<span data-ttu-id="d6a94-112">Version</span><span class="sxs-lookup"><span data-stu-id="d6a94-112">Version</span></span>|<span data-ttu-id="d6a94-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="d6a94-113">4.6.2</span></span>|
|<span data-ttu-id="d6a94-114">类型</span><span class="sxs-lookup"><span data-stu-id="d6a94-114">Type</span></span>|<span data-ttu-id="d6a94-115">运行时</span><span class="sxs-lookup"><span data-stu-id="d6a94-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="d6a94-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="d6a94-116">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Char.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)`

-->
