---
ms.openlocfilehash: 43ebb37124b8efe077b9f81fe5351bd7db2c72f7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302697"
---
### <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a><span data-ttu-id="3ac23-101">对于不支持的类型，Vector\<T> 始终引发 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="3ac23-101">Vector\<T> always throws NotSupportedException for unsupported types</span></span>

<span data-ttu-id="3ac23-102">现在，对于不支持的类型参数，<xref:System.Numerics.Vector%601?displayProperty=nameWithType> 始终引发 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="3ac23-102"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> now always throws a <xref:System.NotSupportedException> for unsupported type parameters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3ac23-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="3ac23-103">Change description</span></span>

<span data-ttu-id="3ac23-104">以前，如果 `T` 是[不支持的类型](#unsupported-types)，<xref:System.Numerics.Vector%601> 的成员将不会始终引发 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="3ac23-104">Previously, members of <xref:System.Numerics.Vector%601> would not always throw a <xref:System.NotSupportedException> when `T` was an [unsupported type](#unsupported-types).</span></span> <span data-ttu-id="3ac23-105">并非总是因支持硬件加速的代码路径而引发异常。</span><span class="sxs-lookup"><span data-stu-id="3ac23-105">The exception wasn't always thrown because of code paths that supported hardware acceleration.</span></span> <span data-ttu-id="3ac23-106">例如，`Vector<bool> + Vector<bool>` 返回了 `default`，而不是在没有硬件加速的平台（如 ARM32）上引发异常。</span><span class="sxs-lookup"><span data-stu-id="3ac23-106">For example, `Vector<bool> + Vector<bool>` returned `default` instead of throwing an exception on platforms that have no hardware acceleration, such as ARM32.</span></span> <span data-ttu-id="3ac23-107">对于不支持的类型，<xref:System.Numerics.Vector%601> 成员在不同的平台和硬件配置中表现出不一致的行为。</span><span class="sxs-lookup"><span data-stu-id="3ac23-107">For unsupported types, <xref:System.Numerics.Vector%601> members exhibited inconsistent behavior across different platforms and hardware configurations.</span></span>

<span data-ttu-id="3ac23-108">从 .NET 5.0 开始，如果 `T` 不是受支持的类型，则 <xref:System.Numerics.Vector%601> 成员始终对所有硬件配置引发 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="3ac23-108">Starting in .NET 5.0, <xref:System.Numerics.Vector%601> members always throw a <xref:System.NotSupportedException> on all hardware configurations when `T` is not a supported type.</span></span>

##### <a name="unsupported-types"></a><span data-ttu-id="3ac23-109">不支持的类型</span><span class="sxs-lookup"><span data-stu-id="3ac23-109">Unsupported types</span></span>

<span data-ttu-id="3ac23-110"><xref:System.Numerics.Vector%601> 的类型参数支持的类型如下：</span><span class="sxs-lookup"><span data-stu-id="3ac23-110">The supported types for the type parameter of <xref:System.Numerics.Vector%601> are:</span></span>

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

<span data-ttu-id="3ac23-111">支持的类型并无变化，但将来可能会更改。</span><span class="sxs-lookup"><span data-stu-id="3ac23-111">The supported types have not changed, however, they may change in the future.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3ac23-112">引入的版本</span><span class="sxs-lookup"><span data-stu-id="3ac23-112">Version introduced</span></span>

<span data-ttu-id="3ac23-113">5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="3ac23-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3ac23-114">建议操作</span><span class="sxs-lookup"><span data-stu-id="3ac23-114">Recommended action</span></span>

<span data-ttu-id="3ac23-115">不要对 <xref:System.Numerics.Vector%601> 的类型参数使用不受支持的类型。</span><span class="sxs-lookup"><span data-stu-id="3ac23-115">Don't use an unsupported type for the type parameter of <xref:System.Numerics.Vector%601>.</span></span>

#### <a name="category"></a><span data-ttu-id="3ac23-116">类别</span><span class="sxs-lookup"><span data-stu-id="3ac23-116">Category</span></span>

<span data-ttu-id="3ac23-117">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="3ac23-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3ac23-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3ac23-118">Affected APIs</span></span>

- <span data-ttu-id="3ac23-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> 及其所有成员</span><span class="sxs-lookup"><span data-stu-id="3ac23-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> and all its members</span></span>

<!--

#### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
