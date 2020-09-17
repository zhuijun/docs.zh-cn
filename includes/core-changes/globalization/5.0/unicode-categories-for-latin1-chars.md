---
ms.openlocfilehash: 48d2f1b5fa2eced30d3c9fb65804268904f11ab8
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065054"
---
### <a name="unicode-category-changed-for-some-latin-1-characters"></a><span data-ttu-id="52c05-101">某些 Latin-1 字符的 Unicode 类别已更改</span><span class="sxs-lookup"><span data-stu-id="52c05-101">Unicode category changed for some Latin-1 characters</span></span>

<span data-ttu-id="52c05-102">现在，<xref:System.Char> 方法为 Latin-1 范围内的字符返回正确的 Unicode 类别。</span><span class="sxs-lookup"><span data-stu-id="52c05-102"><xref:System.Char> methods now return the correct Unicode category for characters in the Latin-1 range.</span></span> <span data-ttu-id="52c05-103">类别与 Unicode 标准的类别匹配。</span><span class="sxs-lookup"><span data-stu-id="52c05-103">The category matches that of the Unicode standard.</span></span>

#### <a name="change-description"></a><span data-ttu-id="52c05-104">更改说明</span><span class="sxs-lookup"><span data-stu-id="52c05-104">Change description</span></span>

<span data-ttu-id="52c05-105">在以前的 .NET 版本中，<xref:System.Char> 方法对 Latin-1 范围内的字符使用 Unicode 类别的固定列表。</span><span class="sxs-lookup"><span data-stu-id="52c05-105">In previous .NET versions, <xref:System.Char> methods used a fixed list of Unicode categories for characters in the Latin-1 range.</span></span> <span data-ttu-id="52c05-106">但是，自从实现这些 API 以来，Unicode 标准已更改其中某些字符的类别，从而造成了不一致。</span><span class="sxs-lookup"><span data-stu-id="52c05-106">However, the Unicode standard has changed the categories of some of these characters since those APIs were implemented, creating a discrepancy.</span></span> <span data-ttu-id="52c05-107">此外，遵循 Unicode 标准的 <xref:System.Char> 和 <xref:System.Globalization.CharUnicodeInfo> API 之间也存在不一致。</span><span class="sxs-lookup"><span data-stu-id="52c05-107">In addition, there was also a discrepancy between <xref:System.Char> and <xref:System.Globalization.CharUnicodeInfo> APIs, which follow the Unicode standard.</span></span> <span data-ttu-id="52c05-108">在 .NET 5.0 及更高版本中，<xref:System.Char> 方法使用并返回与所有字符的 Unicode 标准匹配的 Unicode 类别。</span><span class="sxs-lookup"><span data-stu-id="52c05-108">In .NET 5.0 and later versions, <xref:System.Char> methods use and return the Unicode category that matches the Unicode standard for all characters.</span></span>

<span data-ttu-id="52c05-109">下表显示了 .NET 5.0 中 Unicode 类别已更改的字符：</span><span class="sxs-lookup"><span data-stu-id="52c05-109">The following table shows the characters whose Unicode categories have changed in .NET 5.0:</span></span>

| <span data-ttu-id="52c05-110">字符</span><span class="sxs-lookup"><span data-stu-id="52c05-110">Character</span></span>    | <span data-ttu-id="52c05-111">Unicode 类别</span><span class="sxs-lookup"><span data-stu-id="52c05-111">Unicode category</span></span><br><span data-ttu-id="52c05-112">在以前的 .NET 版本中</span><span class="sxs-lookup"><span data-stu-id="52c05-112">in previous .NET versions</span></span> | <span data-ttu-id="52c05-113">Unicode 类别</span><span class="sxs-lookup"><span data-stu-id="52c05-113">Unicode category</span></span><br><span data-ttu-id="52c05-114">在 .NET 5.0 及更高版本中</span><span class="sxs-lookup"><span data-stu-id="52c05-114">in .NET 5.0 and later versions</span></span> |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| <span data-ttu-id="52c05-115">§ (\u00a7)</span><span class="sxs-lookup"><span data-stu-id="52c05-115">§ (\u00a7)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="52c05-116">ª (\u00aa)</span><span class="sxs-lookup"><span data-stu-id="52c05-116">ª (\u00aa)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |
| <span data-ttu-id="52c05-117">SHY (\u00ad)</span><span class="sxs-lookup"><span data-stu-id="52c05-117">SHY (\u00ad)</span></span> | `DashPunctuation`                             | `Format`                                           |
| <span data-ttu-id="52c05-118">¶ (\u00b6)</span><span class="sxs-lookup"><span data-stu-id="52c05-118">¶ (\u00b6)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="52c05-119">º (\u00ba)</span><span class="sxs-lookup"><span data-stu-id="52c05-119">º (\u00ba)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |

#### <a name="version-introduced"></a><span data-ttu-id="52c05-120">引入的版本</span><span class="sxs-lookup"><span data-stu-id="52c05-120">Version introduced</span></span>

<span data-ttu-id="52c05-121">.NET 5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="52c05-121">.NET 5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="52c05-122">建议操作</span><span class="sxs-lookup"><span data-stu-id="52c05-122">Recommended action</span></span>

<span data-ttu-id="52c05-123">如果你有任何使用 <xref:System.Char> 类获取 Unicode 字符类别的代码，并且假定该类别永远不会改变，则可能需要对其进行更新。</span><span class="sxs-lookup"><span data-stu-id="52c05-123">If you have any code that gets the Unicode character category by using the <xref:System.Char> class and assumes the category will never change, you may need to update it.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="52c05-124">更改原因</span><span class="sxs-lookup"><span data-stu-id="52c05-124">Reason for change</span></span>

<span data-ttu-id="52c05-125">进行此更改是为了使 <xref:System.Char> 类型返回的类别与 Unicode 标准和 <xref:System.Globalization.CharUnicodeInfo> 类型保持一致。</span><span class="sxs-lookup"><span data-stu-id="52c05-125">This change was made so that the categories returned by the <xref:System.Char> type are consistent with both the Unicode standard and the <xref:System.Globalization.CharUnicodeInfo> type.</span></span>

#### <a name="category"></a><span data-ttu-id="52c05-126">类别</span><span class="sxs-lookup"><span data-stu-id="52c05-126">Category</span></span>

- <span data-ttu-id="52c05-127">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="52c05-127">Core .NET libraries</span></span>
- <span data-ttu-id="52c05-128">全球化</span><span class="sxs-lookup"><span data-stu-id="52c05-128">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="52c05-129">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="52c05-129">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

<span data-ttu-id="52c05-130">此外，此更改会影响依赖于 <xref:System.Char> 来获取 Unicode 字符类别的任何类，例如 <xref:System.Text.RegularExpressions.Regex>。</span><span class="sxs-lookup"><span data-stu-id="52c05-130">Additionally, any class that depends on <xref:System.Char> to obtain the Unicode character category, for example, <xref:System.Text.RegularExpressions.Regex>, is affected by this change.</span></span>

<!--

#### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

-->
