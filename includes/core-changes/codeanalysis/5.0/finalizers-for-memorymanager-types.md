---
ms.openlocfilehash: 4fc31f75e8f8cdd50abebd399d9749688e6faa5a
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465560"
---
### <a name="ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a><span data-ttu-id="52aee-101">CA2015:请勿为派生自 MemoryManager\<T> 的类型定义终结器</span><span class="sxs-lookup"><span data-stu-id="52aee-101">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>

<span data-ttu-id="52aee-102">从 .NET 5.0 开始，默认启用 .NET 代码分析器规则 [CA2015](/visualstudio/code-quality/ca2015)。</span><span class="sxs-lookup"><span data-stu-id="52aee-102">.NET code analyzer rule [CA2015](/visualstudio/code-quality/ca2015) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="52aee-103">对于派生自定义终结器的 <xref:System.Buffers.MemoryManager%601> 的任何类型，它都会生成一个生成警告。</span><span class="sxs-lookup"><span data-stu-id="52aee-103">It produces a build warning for any types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span>

#### <a name="change-description"></a><span data-ttu-id="52aee-104">更改说明</span><span class="sxs-lookup"><span data-stu-id="52aee-104">Change description</span></span>

<span data-ttu-id="52aee-105">从 .NET 5.0 开始，.NET SDK 包括 [.NET 源代码分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="52aee-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="52aee-106">其中一些规则会默认启用，包括 [CA2015](/visualstudio/code-quality/ca2015)。</span><span class="sxs-lookup"><span data-stu-id="52aee-106">Several of these rules are enabled, by default, including [CA2015](/visualstudio/code-quality/ca2015).</span></span> <span data-ttu-id="52aee-107">如果项目包含违反此规则的代码，并已被配置为将警告视为错误，则此更改可能会中断生成。</span><span class="sxs-lookup"><span data-stu-id="52aee-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="52aee-108">派生自定义终结器的 <xref:System.Buffers.MemoryManager%601> 的规则 CA2015 标记类型。</span><span class="sxs-lookup"><span data-stu-id="52aee-108">Rule CA2015 flags types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span> <span data-ttu-id="52aee-109">将终结器添加到派生自 <xref:System.Buffers.MemoryManager%601> 的类型可能表明存在 bug。</span><span class="sxs-lookup"><span data-stu-id="52aee-109">Adding a finalizer to a type that derives from <xref:System.Buffers.MemoryManager%601> is likely an indication of a bug.</span></span> <span data-ttu-id="52aee-110">这表明在 <xref:System.Span%601> 中获得的本机资源正在被清除，同时 <xref:System.Span%601> 可能仍在使用该资源。</span><span class="sxs-lookup"><span data-stu-id="52aee-110">It suggests that a native resource that could have been obtained in a <xref:System.Span%601> is getting cleaned up, potentially while it's still in use by the <xref:System.Span%601>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="52aee-111">引入的版本</span><span class="sxs-lookup"><span data-stu-id="52aee-111">Version introduced</span></span>

<span data-ttu-id="52aee-112">5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="52aee-112">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="52aee-113">建议操作</span><span class="sxs-lookup"><span data-stu-id="52aee-113">Recommended action</span></span>

- <span data-ttu-id="52aee-114">删除终结器定义。</span><span class="sxs-lookup"><span data-stu-id="52aee-114">Remove the finalizer definition.</span></span> <span data-ttu-id="52aee-115">有关详细信息，请参阅 [CA2015](/visualstudio/code-quality/ca2015)。</span><span class="sxs-lookup"><span data-stu-id="52aee-115">For more information, see [CA2015](/visualstudio/code-quality/ca2015).</span></span>

- <span data-ttu-id="52aee-116">若要完全禁用代码分析，请在项目文件中将 `EnableNETAnalyzers` 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="52aee-116">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="52aee-117">有关详细信息，请参阅 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="52aee-117">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="52aee-118">类别</span><span class="sxs-lookup"><span data-stu-id="52aee-118">Category</span></span>

<span data-ttu-id="52aee-119">代码分析</span><span class="sxs-lookup"><span data-stu-id="52aee-119">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="52aee-120">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="52aee-120">Affected APIs</span></span>

<span data-ttu-id="52aee-121">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="52aee-121">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
