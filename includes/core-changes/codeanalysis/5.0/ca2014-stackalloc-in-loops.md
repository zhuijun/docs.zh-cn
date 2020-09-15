---
ms.openlocfilehash: a51160a8ab5a4b437e51db31def577f8d8f50182
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065127"
---
### <a name="ca2014-do-not-use-stackalloc-in-loops"></a><span data-ttu-id="3a5da-101">CA2014:请勿在循环中使用 stackalloc</span><span class="sxs-lookup"><span data-stu-id="3a5da-101">CA2014: Do not use stackalloc in loops</span></span>

<span data-ttu-id="3a5da-102">从 .NET 5.0 开始，默认启用 .NET 代码分析器规则 [CA2014](/visualstudio/code-quality/ca2014)。</span><span class="sxs-lookup"><span data-stu-id="3a5da-102">.NET code analyzer rule [CA2014](/visualstudio/code-quality/ca2014) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="3a5da-103">对于在循环内使用 [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) 表达式的任何 C# 代码，它都会生成一个生成警告。</span><span class="sxs-lookup"><span data-stu-id="3a5da-103">It produces a build warning for any C# code where a [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) expression is used inside a loop.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a5da-104">更改说明</span><span class="sxs-lookup"><span data-stu-id="3a5da-104">Change description</span></span>

<span data-ttu-id="3a5da-105">从 .NET 5.0 开始，.NET SDK 包括 [.NET 源代码分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="3a5da-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="3a5da-106">其中一些规则会默认启用，包括 [CA2014](/visualstudio/code-quality/ca2014)。</span><span class="sxs-lookup"><span data-stu-id="3a5da-106">Several of these rules are enabled, by default, including [CA2014](/visualstudio/code-quality/ca2014).</span></span> <span data-ttu-id="3a5da-107">如果项目包含违反此规则的代码，并已被配置为将警告视为错误，则此更改可能会中断生成。</span><span class="sxs-lookup"><span data-stu-id="3a5da-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="3a5da-108">规则 CA2014 会查找在循环中使用 [stackalloc 表达式](../../../../docs/csharp/language-reference/operators/stackalloc.md)的 C# 代码。</span><span class="sxs-lookup"><span data-stu-id="3a5da-108">Rule CA2014 looks for C# code where a [stackalloc expression](../../../../docs/csharp/language-reference/operators/stackalloc.md) is used inside a loop.</span></span> <span data-ttu-id="3a5da-109">[stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) 从当前堆栈帧中分配内存。</span><span class="sxs-lookup"><span data-stu-id="3a5da-109">[stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) allocates memory from the current stack frame.</span></span> <span data-ttu-id="3a5da-110">在当前方法调用返回之前，不会释放内存，这可能导致堆栈溢出。</span><span class="sxs-lookup"><span data-stu-id="3a5da-110">The memory isn't released until the current method call returns, which can lead to stack overflows.</span></span> <span data-ttu-id="3a5da-111">因为无法捕获堆栈溢出异常，应用将在发生堆栈溢出时终止。</span><span class="sxs-lookup"><span data-stu-id="3a5da-111">Because you can't catch stack overflow exceptions, the app will terminate in case of stack overflow.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a5da-112">引入的版本</span><span class="sxs-lookup"><span data-stu-id="3a5da-112">Version introduced</span></span>

<span data-ttu-id="3a5da-113">5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="3a5da-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a5da-114">建议操作</span><span class="sxs-lookup"><span data-stu-id="3a5da-114">Recommended action</span></span>

- <span data-ttu-id="3a5da-115">不要在循环内使用 [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md)。</span><span class="sxs-lookup"><span data-stu-id="3a5da-115">Avoid using [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) inside loops.</span></span> <span data-ttu-id="3a5da-116">在循环外分配内存块，然后在循环内重用它。</span><span class="sxs-lookup"><span data-stu-id="3a5da-116">Allocate the memory block outside the loop and reuse it inside the loop.</span></span> <span data-ttu-id="3a5da-117">有关详细信息，请参阅 [CA2014](/visualstudio/code-quality/ca2014)。</span><span class="sxs-lookup"><span data-stu-id="3a5da-117">For more information, see [CA2014](/visualstudio/code-quality/ca2014).</span></span>

- <span data-ttu-id="3a5da-118">若要完全禁用代码分析，请在项目文件中将 `EnableNETAnalyzers` 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="3a5da-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="3a5da-119">有关详细信息，请参阅 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="3a5da-119">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="3a5da-120">类别</span><span class="sxs-lookup"><span data-stu-id="3a5da-120">Category</span></span>

<span data-ttu-id="3a5da-121">代码分析</span><span class="sxs-lookup"><span data-stu-id="3a5da-121">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a5da-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3a5da-122">Affected APIs</span></span>

<span data-ttu-id="3a5da-123">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="3a5da-123">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
