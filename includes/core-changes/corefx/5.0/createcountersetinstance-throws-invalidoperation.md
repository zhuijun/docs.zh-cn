---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144471"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="593ea-101">如果实例已存在，CounterSet.CreateCounterSetInstance 现在将引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="593ea-101">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="593ea-102">从 .NET 5.0 开始，如果计数器集已存在，<xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> 将引发 <xref:System.InvalidOperationException> 而不是 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="593ea-102">Starting in .NET 5.0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

#### <a name="change-description"></a><span data-ttu-id="593ea-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="593ea-103">Change description</span></span>

<span data-ttu-id="593ea-104">在 .NET Framework 和 .NET Core 1.0 到 3.1 中，可以通过调用 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> 创建计数器集的实例。</span><span class="sxs-lookup"><span data-stu-id="593ea-104">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="593ea-105">但是，如果计数器集已存在，则该方法将引发 <xref:System.ArgumentException> 异常。</span><span class="sxs-lookup"><span data-stu-id="593ea-105">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="593ea-106">在 .NET 5.0 和更高版本中，当调用 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> 且计数器集存在时，将引发 <xref:System.InvalidOperationException> 异常。</span><span class="sxs-lookup"><span data-stu-id="593ea-106">In .NET 5.0 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="593ea-107">引入的版本</span><span class="sxs-lookup"><span data-stu-id="593ea-107">Version introduced</span></span>

<span data-ttu-id="593ea-108">5.0 预览版 5</span><span class="sxs-lookup"><span data-stu-id="593ea-108">5.0 Preview 5</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="593ea-109">建议操作</span><span class="sxs-lookup"><span data-stu-id="593ea-109">Recommended action</span></span>

<span data-ttu-id="593ea-110">如果在调用 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> 时捕获应用中的 <xref:System.ArgumentException> 异常，还应考虑捕获 <xref:System.InvalidOperationException> 异常。</span><span class="sxs-lookup"><span data-stu-id="593ea-110">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="593ea-111">不建议捕获 <xref:System.ArgumentException> 异常。</span><span class="sxs-lookup"><span data-stu-id="593ea-111">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

#### <a name="category"></a><span data-ttu-id="593ea-112">类别</span><span class="sxs-lookup"><span data-stu-id="593ea-112">Category</span></span>

<span data-ttu-id="593ea-113">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="593ea-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="593ea-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="593ea-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
