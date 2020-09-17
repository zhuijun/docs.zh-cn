---
ms.openlocfilehash: ada458ffeeba95d4989507f90c789b159f359797
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065125"
---
### <a name="ca1417-outattribute-on-string-parameter-for-pinvoke"></a><span data-ttu-id="7b674-101">CA1417:P/Invoke 的字符串参数上的 OutAttribute</span><span class="sxs-lookup"><span data-stu-id="7b674-101">CA1417: OutAttribute on string parameter for P/Invoke</span></span>

<span data-ttu-id="7b674-102">从 .NET 5.0 开始，默认启用 .NET 代码分析器规则 [CA1417](/visualstudio/code-quality/ca1417)。</span><span class="sxs-lookup"><span data-stu-id="7b674-102">.NET code analyzer rule [CA1417](/visualstudio/code-quality/ca1417) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="7b674-103">它会为任何[平台调用 (P/Invoke)](../../../../docs/standard/native-interop/pinvoke.md) 方法定义生成一个生成警告，该定义中 <xref:System.String> 参数按值传递并使用 <xref:System.Runtime.InteropServices.OutAttribute> 进行标记。</span><span class="sxs-lookup"><span data-stu-id="7b674-103">It produces a build warning for any [Platform Invoke (P/Invoke)](../../../../docs/standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is passed by value and marked with <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7b674-104">更改说明</span><span class="sxs-lookup"><span data-stu-id="7b674-104">Change description</span></span>

<span data-ttu-id="7b674-105">从 .NET 5.0 开始，.NET SDK 包括 [.NET 源代码分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="7b674-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="7b674-106">其中一些规则会默认启用，包括 [CA1417](/visualstudio/code-quality/ca1417)。</span><span class="sxs-lookup"><span data-stu-id="7b674-106">Several of these rules are enabled, by default, including [CA1417](/visualstudio/code-quality/ca1417).</span></span> <span data-ttu-id="7b674-107">如果项目包含违反此规则的代码，并已被配置为将警告视为错误，则此更改可能会中断生成。</span><span class="sxs-lookup"><span data-stu-id="7b674-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="7b674-108">规则 CA1417 标记 [P/Invoke](../../../../docs/standard/native-interop/pinvoke.md) 方法定义，其中 <xref:System.String> 参数用 <xref:System.Runtime.InteropServices.OutAttribute> 属性进行标记并按值传递。</span><span class="sxs-lookup"><span data-stu-id="7b674-108">Rule CA1417 flags [P/Invoke](../../../../docs/standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is marked with the <xref:System.Runtime.InteropServices.OutAttribute> attribute and is passed by value.</span></span> <span data-ttu-id="7b674-109">例如：</span><span class="sxs-lookup"><span data-stu-id="7b674-109">For example:</span></span>

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

<span data-ttu-id="7b674-110">.NET 运行时维护称为内部池的表，该表包含对程序中每个唯一文本字符串的单一引用。</span><span class="sxs-lookup"><span data-stu-id="7b674-110">The .NET runtime maintains a table, called the intern pool, that contains a single reference to each unique literal string in a program.</span></span> <span data-ttu-id="7b674-111">如果将使用 <xref:System.Runtime.InteropServices.OutAttribute> 标记的限定字符串按值传递给 P/Invoke 方法，则运行时可能会不稳定。</span><span class="sxs-lookup"><span data-stu-id="7b674-111">If an interned string marked with <xref:System.Runtime.InteropServices.OutAttribute> is passed by value to a P/Invoke method, the runtime can be destabilized.</span></span> <span data-ttu-id="7b674-112">有关字符串限定的详细信息，请参阅 <xref:System.String.Intern(System.String)?displayProperty=nameWithType> 的备注。</span><span class="sxs-lookup"><span data-stu-id="7b674-112">For more information about string interning, see the remarks for <xref:System.String.Intern(System.String)?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7b674-113">引入的版本</span><span class="sxs-lookup"><span data-stu-id="7b674-113">Version introduced</span></span>

<span data-ttu-id="7b674-114">5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="7b674-114">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7b674-115">建议操作</span><span class="sxs-lookup"><span data-stu-id="7b674-115">Recommended action</span></span>

- <span data-ttu-id="7b674-116">如果需要将修改后的字符串数据封送回调用方，请改为按引用传递字符串。</span><span class="sxs-lookup"><span data-stu-id="7b674-116">If you need to marshal modified string data back to the caller, pass the string by reference instead.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- <span data-ttu-id="7b674-117">如果不需要将修改后的字符串数据封送回调用方，只需删除 <xref:System.Runtime.InteropServices.OutAttribute>。</span><span class="sxs-lookup"><span data-stu-id="7b674-117">If you don't need to marshal modified string data back to the caller, simply remove the <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  <span data-ttu-id="7b674-118">有关详细信息，请参阅 [CA1417](/visualstudio/code-quality/ca1417)。</span><span class="sxs-lookup"><span data-stu-id="7b674-118">For more information, see [CA1417](/visualstudio/code-quality/ca1417).</span></span>

- <span data-ttu-id="7b674-119">若要完全禁用代码分析，请在项目文件中将 `EnableNETAnalyzers` 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="7b674-119">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="7b674-120">有关详细信息，请参阅 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="7b674-120">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="7b674-121">类别</span><span class="sxs-lookup"><span data-stu-id="7b674-121">Category</span></span>

<span data-ttu-id="7b674-122">代码分析</span><span class="sxs-lookup"><span data-stu-id="7b674-122">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7b674-123">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="7b674-123">Affected APIs</span></span>

<span data-ttu-id="7b674-124">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="7b674-124">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
