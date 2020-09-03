---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957676"
---
### <a name="razor-razortemplateengine-api-removed"></a><span data-ttu-id="545c7-101">Razor：已删除 RazorTemplateEngine API</span><span class="sxs-lookup"><span data-stu-id="545c7-101">Razor: RazorTemplateEngine API removed</span></span>

<span data-ttu-id="545c7-102">已删除 [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API，该内容已替换为 <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>。</span><span class="sxs-lookup"><span data-stu-id="545c7-102">The [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API was removed and replaced with <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>.</span></span>

<span data-ttu-id="545c7-103">有关讨论，请参阅 GitHub 问题 [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215)。</span><span class="sxs-lookup"><span data-stu-id="545c7-103">For discussion, see GitHub issue [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="545c7-104">引入的版本</span><span class="sxs-lookup"><span data-stu-id="545c7-104">Version introduced</span></span>

<span data-ttu-id="545c7-105">3.0</span><span class="sxs-lookup"><span data-stu-id="545c7-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="545c7-106">旧行为</span><span class="sxs-lookup"><span data-stu-id="545c7-106">Old behavior</span></span>

<span data-ttu-id="545c7-107">可创建模板引擎并将其用于分析和生成 Razor 文件的代码。</span><span class="sxs-lookup"><span data-stu-id="545c7-107">A template engine can be created and used to parse and generate code for Razor files.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="545c7-108">新行为</span><span class="sxs-lookup"><span data-stu-id="545c7-108">New behavior</span></span>

<span data-ttu-id="545c7-109">可创建 `RazorProjectEngine`，使其提供与 `RazorTemplateEngine` 相同类型的信息，以分析和生成 Razor 文件的代码。</span><span class="sxs-lookup"><span data-stu-id="545c7-109">`RazorProjectEngine` can be created and provided the same type of information as `RazorTemplateEngine` to parse and generate code for Razor files.</span></span> <span data-ttu-id="545c7-110">`RazorProjectEngine` 也可提供额外的配置级别。</span><span class="sxs-lookup"><span data-stu-id="545c7-110">`RazorProjectEngine` also provides extra levels of configuration.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="545c7-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="545c7-111">Reason for change</span></span>

<span data-ttu-id="545c7-112">`RazorTemplateEngine` 与现有实现过于紧密耦合。</span><span class="sxs-lookup"><span data-stu-id="545c7-112">`RazorTemplateEngine` was too tightly coupled to the existing implementations.</span></span> <span data-ttu-id="545c7-113">在尝试正确配置 Razor 分析/生成管道时，这种紧密耦合会导致更多问题。</span><span class="sxs-lookup"><span data-stu-id="545c7-113">This tight coupling led to more questions when trying to properly configure a Razor parsing/generation pipeline.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="545c7-114">建议操作</span><span class="sxs-lookup"><span data-stu-id="545c7-114">Recommended action</span></span>

<span data-ttu-id="545c7-115">请使用 `RazorProjectEngine`，而不是 `RazorTemplateEngine`。</span><span class="sxs-lookup"><span data-stu-id="545c7-115">Use `RazorProjectEngine` instead of `RazorTemplateEngine`.</span></span> <span data-ttu-id="545c7-116">请考虑以下示例。</span><span class="sxs-lookup"><span data-stu-id="545c7-116">Consider the following examples.</span></span>

##### <a name="create-and-configure-the-razorprojectengine"></a><span data-ttu-id="545c7-117">创建和配置 RazorProjectEngine</span><span class="sxs-lookup"><span data-stu-id="545c7-117">Create and configure the RazorProjectEngine</span></span>

```csharp
RazorProjectEngine projectEngine =
    RazorProjectEngine.Create(RazorConfiguration.Default,
        RazorProjectFileSystem.Create(@"C:\source\repos\ConsoleApp4\ConsoleApp4"),
        builder =>
        {
            builder.ConfigureClass((document, classNode) =>
            {
                classNode.ClassName = "MyClassName";

                // Can also configure other aspects of the class here.
            });

            // More configuration can go here
        });
```

##### <a name="generate-code-for-a-razor-file"></a><span data-ttu-id="545c7-118">生成 Razor 文件的代码</span><span class="sxs-lookup"><span data-stu-id="545c7-118">Generate code for a Razor file</span></span>

```csharp
RazorProjectItem item = projectEngine.FileSystem.GetItem(
    @"C:\source\repos\ConsoleApp4\ConsoleApp4\Example.cshtml",
    FileKinds.Legacy);
RazorCodeDocument output = projectEngine.Process(item);

// Things available
RazorSyntaxTree syntaxTree = output.GetSyntaxTree();
DocumentIntermediateNode intermediateDocument =
    output.GetDocumentIntermediateNode();
RazorCSharpDocument csharpDocument = output.GetCSharpDocument();
```

#### <a name="category"></a><span data-ttu-id="545c7-119">类别</span><span class="sxs-lookup"><span data-stu-id="545c7-119">Category</span></span>

<span data-ttu-id="545c7-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="545c7-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="545c7-121">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="545c7-121">Affected APIs</span></span>

- [<span data-ttu-id="545c7-122">RazorTemplateEngine</span><span class="sxs-lookup"><span data-stu-id="545c7-122">RazorTemplateEngine</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [<span data-ttu-id="545c7-123">RazorTemplateEngineOptions</span><span class="sxs-lookup"><span data-stu-id="545c7-123">RazorTemplateEngineOptions</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->
