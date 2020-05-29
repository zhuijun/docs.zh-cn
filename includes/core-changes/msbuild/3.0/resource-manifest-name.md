---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206215"
---
### <a name="resource-manifest-file-name-change"></a><span data-ttu-id="44296-101">资源清单文件名更改</span><span class="sxs-lookup"><span data-stu-id="44296-101">Resource manifest file name change</span></span>

<span data-ttu-id="44296-102">从 .NET Core 3.0 开始，默认情况下，MSBuild 会为资源文件生成不同的清单文件名。</span><span class="sxs-lookup"><span data-stu-id="44296-102">Starting in .NET Core 3.0, in the default case, MSBuild generates a different manifest file name for resource files.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="44296-103">引入的版本</span><span class="sxs-lookup"><span data-stu-id="44296-103">Version introduced</span></span>

<span data-ttu-id="44296-104">3.0</span><span class="sxs-lookup"><span data-stu-id="44296-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="44296-105">更改描述</span><span class="sxs-lookup"><span data-stu-id="44296-105">Change description</span></span>

<span data-ttu-id="44296-106">在 .NET Core 3.0 之前，如果没有为项目文件中的 `EmbeddedResource` 项指定 `LogicalName`、`ManifestResourceName` 或 `DependentUpon` 元数据，则 MSBuild 会在 `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` 模式中生成清单文件名。</span><span class="sxs-lookup"><span data-stu-id="44296-106">Prior to .NET Core 3.0, if no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata was specified for an `EmbeddedResource` item in the project file, MSBuild generated a manifest file name in the pattern `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources`.</span></span> <span data-ttu-id="44296-107">如果未在项目文件中定义 `RootNamespace`，则其默认为项目名称。</span><span class="sxs-lookup"><span data-stu-id="44296-107">If `RootNamespace` is not defined in the project file, it defaults to the project name.</span></span> <span data-ttu-id="44296-108">例如，根项目目录中名为“Form1.resx”的资源文件的生成清单名称是“MyProject.Form1.resources”。</span><span class="sxs-lookup"><span data-stu-id="44296-108">For example, the generated manifest name for a resource file named *Form1.resx* in the root project directory was *MyProject.Form1.resources*.</span></span>

<span data-ttu-id="44296-109">从 .NET Core 3.0 开始，如果资源文件与同名的源文件（例如 Form1.resx 和 Form1.cs）并置，则 MSBuild 将使用源文件中的类型信息在 `<Namespace>.<ClassName>.resources` 模式中生成清单文件名。</span><span class="sxs-lookup"><span data-stu-id="44296-109">Starting in .NET Core 3.0, if a resource file is colocated with a source file of the same name (for example, *Form1.resx* and *Form1.cs*), MSBuild uses type information from the source file to generate the manifest file name in the pattern `<Namespace>.<ClassName>.resources`.</span></span> <span data-ttu-id="44296-110">命名空间和类名称是从并置源文件的第一个类型中提取的。</span><span class="sxs-lookup"><span data-stu-id="44296-110">The namespace and class name are extracted from the first type in the colocated source file.</span></span> <span data-ttu-id="44296-111">例如，与名为“Form1.cs”的源文件并置的、名为“Form1.resx”的资源文件的生成清单名称是“MyNamespace.Form1.resources”。</span><span class="sxs-lookup"><span data-stu-id="44296-111">For example, the generated manifest name for a resource file named *Form1.resx* that's colocated with a source file named *Form1.cs* is *MyNamespace.Form1.resources*.</span></span> <span data-ttu-id="44296-112">需要注意的一点是，文件名的第一部分不同于早期版本的 .NET Core（是 MyNamespace，而不是 MyProject）。</span><span class="sxs-lookup"><span data-stu-id="44296-112">The key thing to note is that the first part of the file name is different to prior versions of .NET Core (*MyNamespace* instead of *MyProject*).</span></span>

> [!NOTE]
> <span data-ttu-id="44296-113">如果已在项目文件中的 `EmbeddedResource` 项上指定 `LogicalName`、`ManifestResourceName` 或 `DependentUpon` 元数据，则此更改不会影响该资源文件。</span><span class="sxs-lookup"><span data-stu-id="44296-113">If you have `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata specified on an `EmbeddedResource` item in the project file, then this change does not affect that resource file.</span></span>

<span data-ttu-id="44296-114">此重大更改是在 .NET Core 项目中添加 `EmbeddedResourceUseDependentUponConvention` 属性时引入的。</span><span class="sxs-lookup"><span data-stu-id="44296-114">This breaking change was introduced with the addition of the `EmbeddedResourceUseDependentUponConvention` property to .NET Core projects.</span></span> <span data-ttu-id="44296-115">默认情况下，不会在 .NET Core 项目文件中显式列出资源文件，因此它们没有 `DependentUpon` 元数据来指定如何命名生成的 .resources 文件。</span><span class="sxs-lookup"><span data-stu-id="44296-115">By default, resource files aren't explicitly listed in a .NET Core project file, so they have no `DependentUpon` metadata to specify how to name the generated *.resources* file.</span></span> <span data-ttu-id="44296-116">如果 `EmbeddedResourceUseDependentUponConvention` 设置为 `true`（默认值），则 MSBuild 将查找并置的源文件，并从该文件中提取命名空间和类名。</span><span class="sxs-lookup"><span data-stu-id="44296-116">When `EmbeddedResourceUseDependentUponConvention` is set to `true`, which is the default, MSBuild looks for a colocated source file and extracts a namespace and class name from that file.</span></span> <span data-ttu-id="44296-117">如果将 `EmbeddedResourceUseDependentUponConvention` 设置为 `false`，则 MSBuild 将根据之前的行为生成清单名称，将 `RootNamespace` 和相对文件路径组合在一起。</span><span class="sxs-lookup"><span data-stu-id="44296-117">If you set `EmbeddedResourceUseDependentUponConvention` to `false`, MSBuild generates the manifest name according to the previous behavior, which combines `RootNamespace` and the relative file path.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="44296-118">建议操作</span><span class="sxs-lookup"><span data-stu-id="44296-118">Recommended action</span></span>

<span data-ttu-id="44296-119">在大多数情况下，开发人员不需要执行任何操作，应用应可以继续工作。</span><span class="sxs-lookup"><span data-stu-id="44296-119">In most cases, no action is required on the part of the developer, and your app should continue to work.</span></span> <span data-ttu-id="44296-120">但是，如果此更改造成应用中断运行，你可以：</span><span class="sxs-lookup"><span data-stu-id="44296-120">However, if this change breaks your app, you can either:</span></span>

- <span data-ttu-id="44296-121">将代码更改为需要新的清单名称。</span><span class="sxs-lookup"><span data-stu-id="44296-121">Change your code to expect the new manifest name.</span></span>

- <span data-ttu-id="44296-122">在项目文件中将 `EmbeddedResourceUseDependentUponConvention` 设置为 `false`，以选择退出新命名约定。</span><span class="sxs-lookup"><span data-stu-id="44296-122">Opt out of the new naming convention by setting `EmbeddedResourceUseDependentUponConvention` to `false` in your project file.</span></span>

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="44296-123">类别</span><span class="sxs-lookup"><span data-stu-id="44296-123">Category</span></span>

<span data-ttu-id="44296-124">MSBuild</span><span class="sxs-lookup"><span data-stu-id="44296-124">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="44296-125">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="44296-125">Affected APIs</span></span>

<span data-ttu-id="44296-126">不可用</span><span class="sxs-lookup"><span data-stu-id="44296-126">N/A</span></span>
