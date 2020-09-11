---
ms.openlocfilehash: 6bb3b11ef4e4cb6f6a039c97911b0acca862fe6f
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465559"
---
### <a name="ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a><span data-ttu-id="95405-101">CA2247:TaskCompletionSource 构造函数的参数应为 TaskCreationOptions 值</span><span class="sxs-lookup"><span data-stu-id="95405-101">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>

<span data-ttu-id="95405-102">从 .NET 5.0 开始，默认启用 .NET 代码分析器规则 [CA2247](/visualstudio/code-quality/ca2247)。</span><span class="sxs-lookup"><span data-stu-id="95405-102">.NET code analyzer rule [CA2247](/visualstudio/code-quality/ca2247) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="95405-103">关于对 <xref:System.Threading.Tasks.TaskCompletionSource%601> 构造函数的调用（该函数传递类型为 <xref:System.Threading.Tasks.TaskContinuationOptions> 的参数），它会生成一个生成警告。</span><span class="sxs-lookup"><span data-stu-id="95405-103">It produces a build warning for calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="95405-104">更改说明</span><span class="sxs-lookup"><span data-stu-id="95405-104">Change description</span></span>

<span data-ttu-id="95405-105">从 .NET 5.0 开始，.NET SDK 包括 [.NET 源代码分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="95405-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="95405-106">其中一些规则会默认启用，包括 [CA2247](/visualstudio/code-quality/ca2247)。</span><span class="sxs-lookup"><span data-stu-id="95405-106">Several of these rules are enabled, by default, including [CA2247](/visualstudio/code-quality/ca2247).</span></span> <span data-ttu-id="95405-107">如果项目包含违反此规则的代码，并已被配置为将警告视为错误，则此更改可能会中断生成。</span><span class="sxs-lookup"><span data-stu-id="95405-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="95405-108">规则 CA2247 会查找对 <xref:System.Threading.Tasks.TaskCompletionSource%601> 构造函数的调用，这些调用传递类型为 <xref:System.Threading.Tasks.TaskContinuationOptions> 的参数。</span><span class="sxs-lookup"><span data-stu-id="95405-108">Rule CA2247 finds calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span> <span data-ttu-id="95405-109"><xref:System.Threading.Tasks.TaskCompletionSource%601> 类型具有一个接受 <xref:System.Threading.Tasks.TaskCreationOptions> 值的构造函数和一个接受 <xref:System.Object> 的构造函数。</span><span class="sxs-lookup"><span data-stu-id="95405-109">The <xref:System.Threading.Tasks.TaskCompletionSource%601> type has a constructor that accepts a <xref:System.Threading.Tasks.TaskCreationOptions> value, and another constructor that accepts an <xref:System.Object>.</span></span> <span data-ttu-id="95405-110">如果意外传递了 <xref:System.Threading.Tasks.TaskContinuationOptions> 值（而不是 <xref:System.Threading.Tasks.TaskCreationOptions> 值），则在运行时调用带有 <xref:System.Object> 参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="95405-110">If you accidentally pass a <xref:System.Threading.Tasks.TaskContinuationOptions> value instead of a <xref:System.Threading.Tasks.TaskCreationOptions> value, the constructor with the <xref:System.Object> parameter is called at run time.</span></span> <span data-ttu-id="95405-111">代码将编译并运行，但没有预期行为。</span><span class="sxs-lookup"><span data-stu-id="95405-111">Your code will compile and run but won't have the intended behavior.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="95405-112">引入的版本</span><span class="sxs-lookup"><span data-stu-id="95405-112">Version introduced</span></span>

<span data-ttu-id="95405-113">5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="95405-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="95405-114">建议操作</span><span class="sxs-lookup"><span data-stu-id="95405-114">Recommended action</span></span>

- <span data-ttu-id="95405-115">将 <xref:System.Threading.Tasks.TaskContinuationOptions> 参数替换为相应的 <xref:System.Threading.Tasks.TaskCreationOptions> 值。</span><span class="sxs-lookup"><span data-stu-id="95405-115">Replace the <xref:System.Threading.Tasks.TaskContinuationOptions> argument with the corresponding <xref:System.Threading.Tasks.TaskCreationOptions> value.</span></span> <span data-ttu-id="95405-116">请勿禁止显示此警告，因为它几乎总是突出显示代码中的 bug。</span><span class="sxs-lookup"><span data-stu-id="95405-116">Do not suppress this warning, since it almost always highlights a bug in your code.</span></span> <span data-ttu-id="95405-117">有关详细信息，请参阅 [CA2247](/visualstudio/code-quality/ca2247)。</span><span class="sxs-lookup"><span data-stu-id="95405-117">For more information, see [CA2247](/visualstudio/code-quality/ca2247).</span></span>

- <span data-ttu-id="95405-118">若要完全禁用代码分析，请在项目文件中将 `EnableNETAnalyzers` 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="95405-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="95405-119">有关详细信息，请参阅 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="95405-119">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="95405-120">类别</span><span class="sxs-lookup"><span data-stu-id="95405-120">Category</span></span>

<span data-ttu-id="95405-121">代码分析</span><span class="sxs-lookup"><span data-stu-id="95405-121">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="95405-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="95405-122">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

#### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

-->
