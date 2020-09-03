---
ms.openlocfilehash: 87f9cc03f334233ef286abd11e6f5ff82d7988c2
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811337"
---
### <a name="ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer"></a><span data-ttu-id="804b5-101">CA1831 使用 AsSpan 或 AsMemory，而不是基于范围的索引器</span><span class="sxs-lookup"><span data-stu-id="804b5-101">CA1831 Use AsSpan or AsMemory instead of Range-based indexer</span></span>

<span data-ttu-id="804b5-102">默认情况下，从 .NET 5.0 开始启用 .NET 代码分析器规则 [CA1831](/visualstudio/code-quality/ca1831)。</span><span class="sxs-lookup"><span data-stu-id="804b5-102">.NET code analyzer rule [CA1831](/visualstudio/code-quality/ca1831) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="804b5-103">对于在字符串中使用基于 <xref:System.Range> 的索引器，但不打算进行复制的任何代码，都将生成一个生成警告。</span><span class="sxs-lookup"><span data-stu-id="804b5-103">It produces a build warning for any code where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span>

#### <a name="change-description"></a><span data-ttu-id="804b5-104">更改说明</span><span class="sxs-lookup"><span data-stu-id="804b5-104">Change description</span></span>

<span data-ttu-id="804b5-105">从 .NET 5.0 开始，.NET SDK 包括 [.NET 源代码分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="804b5-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="804b5-106">默认情况下会启用其中一些规则，包括 [CA1831](/visualstudio/code-quality/ca1831)。</span><span class="sxs-lookup"><span data-stu-id="804b5-106">Several of these rules are enabled, by default, including [CA1831](/visualstudio/code-quality/ca1831).</span></span> <span data-ttu-id="804b5-107">如果项目包含违反此规则的代码，并已被配置为将警告视为错误，则此更改可能会中断生成。</span><span class="sxs-lookup"><span data-stu-id="804b5-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="804b5-108">规则 CA1831 查找在字符串中使用基于 <xref:System.Range> 的索引器但不打算进行复制的实例。</span><span class="sxs-lookup"><span data-stu-id="804b5-108">Rule CA1831 finds instances where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span> <span data-ttu-id="804b5-109">如果直接在字符串中使用基于 <xref:System.Range> 的索引器来生成隐式强制转换，则会创建字符串请求部分的不必要副本。</span><span class="sxs-lookup"><span data-stu-id="804b5-109">If the <xref:System.Range>-based indexer is used directly on a string to produce an implicit cast, then an unnecessary copy of the requested portion of the string is created.</span></span> <span data-ttu-id="804b5-110">例如：</span><span class="sxs-lookup"><span data-stu-id="804b5-110">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

<span data-ttu-id="804b5-111">相反，CA1831 建议在字符串的“范围”上使用基于 <xref:System.Range> 的索引器。</span><span class="sxs-lookup"><span data-stu-id="804b5-111">CA1831 suggests using the <xref:System.Range>-based indexer on a *span* of the string, instead.</span></span> <span data-ttu-id="804b5-112">例如：</span><span class="sxs-lookup"><span data-stu-id="804b5-112">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

#### <a name="version-introduced"></a><span data-ttu-id="804b5-113">引入的版本</span><span class="sxs-lookup"><span data-stu-id="804b5-113">Version introduced</span></span>

<span data-ttu-id="804b5-114">5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="804b5-114">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="804b5-115">建议操作</span><span class="sxs-lookup"><span data-stu-id="804b5-115">Recommended action</span></span>

- <span data-ttu-id="804b5-116">若要更正代码并避免不必要的分配，请在使用基于 <xref:System.Range> 的索引器之前调用 <xref:System.MemoryExtensions.AsSpan(System.String)> 或 <xref:System.MemoryExtensions.AsMemory(System.String)>。</span><span class="sxs-lookup"><span data-stu-id="804b5-116">To correct your code and avoid unnecessary allocations, call <xref:System.MemoryExtensions.AsSpan(System.String)> or <xref:System.MemoryExtensions.AsMemory(System.String)> before using the <xref:System.Range>-based indexer.</span></span> <span data-ttu-id="804b5-117">例如：</span><span class="sxs-lookup"><span data-stu-id="804b5-117">For example:</span></span>

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- <span data-ttu-id="804b5-118">如果不想更改代码，则可通过将规则的严重性设置为 `suggestion` 或 `none` 来禁用规则。</span><span class="sxs-lookup"><span data-stu-id="804b5-118">If you don't want to change your code, you can disable the rule by setting its severity to `suggestion` or `none`.</span></span> <span data-ttu-id="804b5-119">有关详细信息，请参阅[配置代码分析规则](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="804b5-119">For more information, see [Configure code analysis rules](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).</span></span>

- <span data-ttu-id="804b5-120">若要完全禁用代码分析，请在项目文件中将 `EnableNETAnalyzers` 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="804b5-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="804b5-121">有关详细信息，请参阅 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="804b5-121">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="804b5-122">类别</span><span class="sxs-lookup"><span data-stu-id="804b5-122">Category</span></span>

<span data-ttu-id="804b5-123">代码分析</span><span class="sxs-lookup"><span data-stu-id="804b5-123">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="804b5-124">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="804b5-124">Affected APIs</span></span>

- <xref:System.Range?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Range`

-->
