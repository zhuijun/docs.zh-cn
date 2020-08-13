---
ms.openlocfilehash: 3d29848e12d496d2d53c204e00ef8604831495e1
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024689"
---
### <a name="intptr-and-uintptr-implement-iformattable"></a><span data-ttu-id="b5717-101">IntPtr 和 UIntPtr 实现 IFormattable</span><span class="sxs-lookup"><span data-stu-id="b5717-101">IntPtr and UIntPtr implement IFormattable</span></span>

<span data-ttu-id="b5717-102"><xref:System.IntPtr> 和 <xref:System.UIntPtr> 现在实现 <xref:System.IFormattable>。</span><span class="sxs-lookup"><span data-stu-id="b5717-102"><xref:System.IntPtr> and <xref:System.UIntPtr> now implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="b5717-103">检查 <xref:System.IFormattable> 支持的功能现在可能返回这些类型的不同结果，因为它们可能以格式说明符和区域性的形式传递。</span><span class="sxs-lookup"><span data-stu-id="b5717-103">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b5717-104">更改描述</span><span class="sxs-lookup"><span data-stu-id="b5717-104">Change description</span></span>

<span data-ttu-id="b5717-105">在早期版本的 .NET 中，<xref:System.IntPtr> 和 <xref:System.UIntPtr> 不实现 <xref:System.IFormattable>。</span><span class="sxs-lookup"><span data-stu-id="b5717-105">In previous versions of .NET, <xref:System.IntPtr> and <xref:System.UIntPtr> do not implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="b5717-106">检查 <xref:System.IFormattable> 的函数可回退到仅调用 <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> 或 <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>，这意味着不会遵循格式说明符和区域性。</span><span class="sxs-lookup"><span data-stu-id="b5717-106">Functions that check for <xref:System.IFormattable> may fall back to just calling <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> or <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, which means that format specifiers and cultures are not respected.</span></span>

<span data-ttu-id="b5717-107">在 .NET 5.0 和更高版本中，<xref:System.IntPtr> 和 <xref:System.UIntPtr> 实现 <xref:System.IFormattable>。</span><span class="sxs-lookup"><span data-stu-id="b5717-107">In .NET 5.0 and later versions, <xref:System.IntPtr> and <xref:System.UIntPtr> implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="b5717-108">检查 <xref:System.IFormattable> 支持的功能现在可能返回这些类型的不同结果，因为它们可能以格式说明符和区域性的形式传递。</span><span class="sxs-lookup"><span data-stu-id="b5717-108">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

<span data-ttu-id="b5717-109">此更改会影响内插字符串和 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 等方案。</span><span class="sxs-lookup"><span data-stu-id="b5717-109">This change impacts scenarios like interpolated strings and <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, among others.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b5717-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="b5717-110">Reason for change</span></span>

<span data-ttu-id="b5717-111"><xref:System.IntPtr> 和 <xref:System.UIntPtr> 现在通过 `nint` 和 `nuint` 关键字获得 C# 语言支持。</span><span class="sxs-lookup"><span data-stu-id="b5717-111"><xref:System.IntPtr> and <xref:System.UIntPtr> now have language support in C# through the `nint` and `nuint` keywords.</span></span> <span data-ttu-id="b5717-112">更新了后备类型，以通过其他基元类型（例如 <xref:System.Int32?displayProperty=nameWithType>）公开的功能提供接近奇偶校验（如果可能）。</span><span class="sxs-lookup"><span data-stu-id="b5717-112">The backing types were updated to provide near parity (where possible) with functionality exposed by other primitive types, such as <xref:System.Int32?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b5717-113">引入的版本</span><span class="sxs-lookup"><span data-stu-id="b5717-113">Version introduced</span></span>

<span data-ttu-id="b5717-114">5.0 预览版 4</span><span class="sxs-lookup"><span data-stu-id="b5717-114">5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b5717-115">建议操作</span><span class="sxs-lookup"><span data-stu-id="b5717-115">Recommended action</span></span>

<span data-ttu-id="b5717-116">如果不希望在显示这些类型的值时使用格式说明符或自定义区域性，则可以调用 `ToString()` 的 <xref:System.IntPtr.ToString?displayProperty=nameWithType> 和 <xref:System.UIntPtr.ToString?displayProperty=nameWithType> 重载。</span><span class="sxs-lookup"><span data-stu-id="b5717-116">If you don't want a format specifier or custom culture to be used when displaying values of these types, you can call the <xref:System.IntPtr.ToString?displayProperty=nameWithType> and <xref:System.UIntPtr.ToString?displayProperty=nameWithType> overloads of `ToString()`.</span></span>

#### <a name="category"></a><span data-ttu-id="b5717-117">类别</span><span class="sxs-lookup"><span data-stu-id="b5717-117">Category</span></span>

<span data-ttu-id="b5717-118">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="b5717-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b5717-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="b5717-119">Affected APIs</span></span>

<span data-ttu-id="b5717-120">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="b5717-120">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
