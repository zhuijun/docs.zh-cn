---
ms.openlocfilehash: a806107456a65a4919592da9535a2617f677cfe0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496651"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a><span data-ttu-id="ce3c5-101">WPF DispatcherSynchronizationContext.CreateCopy 现在返回新副本，而非当前实例</span><span class="sxs-lookup"><span data-stu-id="ce3c5-101">WPF DispatcherSynchronizationContext.CreateCopy now returns a new copy instead of the current instance</span></span>

#### <a name="details"></a><span data-ttu-id="ce3c5-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ce3c5-102">Details</span></span>

<span data-ttu-id="ce3c5-103">在 .NET Framework 4 中，<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> 返回当前实例的引用，这主要作为一项性能优化。</span><span class="sxs-lookup"><span data-stu-id="ce3c5-103">In the .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> returned a reference to the current instance, primarily as a performance optimization.</span></span> <span data-ttu-id="ce3c5-104">在 .NET Framework 4.5 中，它返回新实例，这可以首次得出结论：相同的引用指示执行线程位于正确的同步上下文中。</span><span class="sxs-lookup"><span data-stu-id="ce3c5-104">In the .NET Framework 4.5, it returns a new instance which makes it possible for the first time to conclude that equal references indicate the executing thread is in the correct synchronization context.</span></span>  <span data-ttu-id="ce3c5-105">检查这些引用标识的代码可能不受影响，但由于此更改，作为迁移到 .NET Framework 4.5 或更高版本的一部分，应测试调用 <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> 的代码。</span><span class="sxs-lookup"><span data-stu-id="ce3c5-105">It is unlikely that code that checks the identity of these references will be affected, but because of the change, code that calls <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> should be tested as part of migration to the .NET Framework 4.5 or newer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ce3c5-106">建议</span><span class="sxs-lookup"><span data-stu-id="ce3c5-106">Suggestion</span></span>

<span data-ttu-id="ce3c5-107">请注意，<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> 现在将返回新的 <xref:System.Threading.SynchronizationContext?displayProperty=fullName> 对象。</span><span class="sxs-lookup"><span data-stu-id="ce3c5-107">Be aware that <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> will now return a new <xref:System.Threading.SynchronizationContext?displayProperty=fullName> object.</span></span> <span data-ttu-id="ce3c5-108">以前，使用按此方法所生成引用的等效项的代码实际上不会检查它是否在正确的上下文中，但针对 .NET Framework 4.5 或更高版本生成时则会检查。</span><span class="sxs-lookup"><span data-stu-id="ce3c5-108">Previously, code that used equivalence of references generated this way was not actually checking whether it was in the proper context, but does when built against .NET Framework 4.5 or later.</span></span>  <span data-ttu-id="ce3c5-109">虽然不太可能产生问题，但执行受影响的代码路径应足以确定这是否会带来任何问题。</span><span class="sxs-lookup"><span data-stu-id="ce3c5-109">While unlikely to cause issues, exercising the affected code paths should be enough to determine if this poses any problem.</span></span>

| <span data-ttu-id="ce3c5-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="ce3c5-110">Name</span></span>    | <span data-ttu-id="ce3c5-111">“值”</span><span class="sxs-lookup"><span data-stu-id="ce3c5-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ce3c5-112">范围</span><span class="sxs-lookup"><span data-stu-id="ce3c5-112">Scope</span></span>   |<span data-ttu-id="ce3c5-113">次要</span><span class="sxs-lookup"><span data-stu-id="ce3c5-113">Minor</span></span>|
|<span data-ttu-id="ce3c5-114">Version</span><span class="sxs-lookup"><span data-stu-id="ce3c5-114">Version</span></span>|<span data-ttu-id="ce3c5-115">4.5</span><span class="sxs-lookup"><span data-stu-id="ce3c5-115">4.5</span></span>|
|<span data-ttu-id="ce3c5-116">类型</span><span class="sxs-lookup"><span data-stu-id="ce3c5-116">Type</span></span>|<span data-ttu-id="ce3c5-117">运行时</span><span class="sxs-lookup"><span data-stu-id="ce3c5-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ce3c5-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="ce3c5-118">Affected APIs</span></span>

- <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy`

-->
