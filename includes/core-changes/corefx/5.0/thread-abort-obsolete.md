---
ms.openlocfilehash: 85488de561a2298f2ff4009ec78b9a6e294053f3
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598169"
---
### <a name="threadabort-is-obsolete"></a><span data-ttu-id="bac16-101">Thread.Abort 已过时</span><span class="sxs-lookup"><span data-stu-id="bac16-101">Thread.Abort is obsolete</span></span>

<span data-ttu-id="bac16-102"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> API 已过时。</span><span class="sxs-lookup"><span data-stu-id="bac16-102">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="bac16-103">如果调用这些方法，则面向 .NET 5.0 或更高版本的项目将遇到编译时警告。</span><span class="sxs-lookup"><span data-stu-id="bac16-103">Projects that target .NET 5.0 or a later version will encounter compile-time warnings if these methods are called.</span></span> <span data-ttu-id="bac16-104">如果禁止显示警告，则将在运行时引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="bac16-104">If you suppress the warnings, a <xref:System.PlatformNotSupportedException> will be thrown at run time.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bac16-105">更改说明</span><span class="sxs-lookup"><span data-stu-id="bac16-105">Change description</span></span>

<span data-ttu-id="bac16-106">以前，对 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 的调用不会生成编译时警告，但该方法确实会在运行时引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="bac16-106">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="bac16-107">从 .NET 5.0 开始，<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 以警告的形式标记为已过时。</span><span class="sxs-lookup"><span data-stu-id="bac16-107">Starting in .NET 5.0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="bac16-108">调用此方法将生成编译器警告 `SYSLIB0006`。</span><span class="sxs-lookup"><span data-stu-id="bac16-108">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="bac16-109">该方法的实现保持不变，并且继续引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="bac16-109">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bac16-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="bac16-110">Reason for change</span></span>

<span data-ttu-id="bac16-111">假定 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 在除 .NET Framework 以外的所有 .NET 实现中始终引发 <xref:System.PlatformNotSupportedException>，则向该方法添加 <xref:System.ObsoleteAttribute>，以引起人们对其调用位置的注意。</span><span class="sxs-lookup"><span data-stu-id="bac16-111">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bac16-112">引入的版本</span><span class="sxs-lookup"><span data-stu-id="bac16-112">Version introduced</span></span>

<span data-ttu-id="bac16-113">5.0 RC 1</span><span class="sxs-lookup"><span data-stu-id="bac16-113">5.0 RC 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bac16-114">建议操作</span><span class="sxs-lookup"><span data-stu-id="bac16-114">Recommended action</span></span>

- <span data-ttu-id="bac16-115">使用 <xref:System.Threading.CancellationToken> 中止对工作单元的处理，而不是调用 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="bac16-115">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bac16-116">以下示例说明了 <xref:System.Threading.CancellationToken> 的用法。</span><span class="sxs-lookup"><span data-stu-id="bac16-116">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

  ```csharp
  void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
  {
      if (QueryIsMoreWorkPending())
      {
          // If the CancellationToken is marked as "needs to cancel",
          // this will throw the appropriate exception.
          cancellationToken.ThrowIfCancellationRequested();

          WorkItem work = DequeueWorkItem();
          ProcessWorkItem(work);
      }
  }
  ```

  <span data-ttu-id="bac16-117">有关详细信息，请参阅[托管线程中的取消](../../../../docs/standard/threading/cancellation-in-managed-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="bac16-117">For more information, see [Cancellation in managed threads](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="bac16-118">若要禁止显示编译时警告，请禁止显示警告代码 `SYSLIB0006`。</span><span class="sxs-lookup"><span data-stu-id="bac16-118">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="bac16-119">警告代码特定于 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>，并且禁止显示该代码不会禁止显示代码中的其他过时警告。</span><span class="sxs-lookup"><span data-stu-id="bac16-119">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="bac16-120">但是，建议删除对 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 的调用，而不是禁止显示该警告。</span><span class="sxs-lookup"><span data-stu-id="bac16-120">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="bac16-121">另外，还可以在项目文件中取消警告。</span><span class="sxs-lookup"><span data-stu-id="bac16-121">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="bac16-122">类别</span><span class="sxs-lookup"><span data-stu-id="bac16-122">Category</span></span>

- <span data-ttu-id="bac16-123">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="bac16-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bac16-124">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="bac16-124">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
