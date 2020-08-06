---
title: NuGet 和 .NET 库
description: 使用 .NET 库的 NuGet 打包的最佳实践建议。
ms.date: 01/15/2019
ms.openlocfilehash: d9f8d7cc4402a87e1429791b57a0306b318dfbe4
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382108"
---
# <a name="nuget"></a><span data-ttu-id="70616-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="70616-103">NuGet</span></span>

<span data-ttu-id="70616-104">NuGet 是 .NET 生态系统的包管理器，并且是开发人员用来发现并获取 .NET 开放源代码库的主要方法。</span><span class="sxs-lookup"><span data-stu-id="70616-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="70616-105">[NuGet.org](https://www.nuget.org/)（由托管 NuGet 包的 Microsoft 提供的免费服务）是公共 NuGet 包的主要主机，但可以发布到自定义 NuGet 服务，如 [MyGet](https://www.myget.org/) 和 [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/)。</span><span class="sxs-lookup"><span data-stu-id="70616-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="70616-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="70616-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="70616-107">创建 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="70616-107">Create a NuGet package</span></span>

<span data-ttu-id="70616-108">NuGet 包 (`*.nupkg`) 是一个 zip 文件，其中包含 .NET 程序集和关联的元数据。</span><span class="sxs-lookup"><span data-stu-id="70616-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="70616-109">创建 NuGet 包有两种主要方式。</span><span class="sxs-lookup"><span data-stu-id="70616-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="70616-110">较新的推荐方式是从 SDK 样式项目（其内容以 `<Project Sdk="Microsoft.NET.Sdk">` 开头的项目文件）创建包。</span><span class="sxs-lookup"><span data-stu-id="70616-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="70616-111">程序集和目标会自动添加到包，剩余元数据会添加到 MSBuild 文件，如包名称和版本号。</span><span class="sxs-lookup"><span data-stu-id="70616-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="70616-112">使用 [`dotnet pack`](../../core/tools/dotnet-pack.md) 命令编译会输出 `*.nupkg` 文件，而不是程序集。</span><span class="sxs-lookup"><span data-stu-id="70616-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="70616-113">创建 NuGet 包的较旧方式是使用 `*.nuspec` 文件和 `nuget.exe` 命令行工具。</span><span class="sxs-lookup"><span data-stu-id="70616-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="70616-114">nuspec 文件为你提供更好的控制，但必须仔细指定要包含在最终 NuGet 包中的程序集和目标。</span><span class="sxs-lookup"><span data-stu-id="70616-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="70616-115">很容易犯错或很容易忘记在发生更改时更新 nuspec。</span><span class="sxs-lookup"><span data-stu-id="70616-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="70616-116">nuspec 的优点是可以将其用于创建尚不支持 SDK 样式项目文件的框架的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="70616-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="70616-117">✔️ 请考虑使用 SDK 样式项目文件创建 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="70616-117">✔️ CONSIDER using an SDK-style project file to create the NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="70616-118">包依赖项</span><span class="sxs-lookup"><span data-stu-id="70616-118">Package dependencies</span></span>

<span data-ttu-id="70616-119">[依赖项](./dependencies.md)一文详细介绍了 NuGet 包依赖项。</span><span class="sxs-lookup"><span data-stu-id="70616-119">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="70616-120">重要的 NuGet 包元数据</span><span class="sxs-lookup"><span data-stu-id="70616-120">Important NuGet package metadata</span></span>

<span data-ttu-id="70616-121">NuGet 包支持多个[元数据属性](/nuget/reference/nuspec)。</span><span class="sxs-lookup"><span data-stu-id="70616-121">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="70616-122">下表包含 NuGet.org 上的每个包应提供的核心元数据：</span><span class="sxs-lookup"><span data-stu-id="70616-122">The following table contains the core metadata that every package on NuGet.org should provide:</span></span>

| <span data-ttu-id="70616-123">MSBuild 属性名称</span><span class="sxs-lookup"><span data-stu-id="70616-123">MSBuild Property name</span></span>              | <span data-ttu-id="70616-124">Nuspec 名称</span><span class="sxs-lookup"><span data-stu-id="70616-124">Nuspec name</span></span>              | <span data-ttu-id="70616-125">描述</span><span class="sxs-lookup"><span data-stu-id="70616-125">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="70616-126">包标识符。</span><span class="sxs-lookup"><span data-stu-id="70616-126">The package identifier.</span></span> <span data-ttu-id="70616-127">如果标识符的前缀满足[条件](/nuget/reference/id-prefix-reservation)，则可以保留该前缀。</span><span class="sxs-lookup"><span data-stu-id="70616-127">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="70616-128">NuGet 包版本。</span><span class="sxs-lookup"><span data-stu-id="70616-128">NuGet package version.</span></span> <span data-ttu-id="70616-129">有关详细信息，请参阅 [NuGet 包版本](./versioning.md#nuget-package-version)。</span><span class="sxs-lookup"><span data-stu-id="70616-129">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="70616-130">明了易用的包标题。</span><span class="sxs-lookup"><span data-stu-id="70616-130">A human-friendly title of the package.</span></span> <span data-ttu-id="70616-131">默认为 `PackageId`。</span><span class="sxs-lookup"><span data-stu-id="70616-131">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="70616-132">UI 中显示的包的详细说明。</span><span class="sxs-lookup"><span data-stu-id="70616-132">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="70616-133">包创建者的逗号分隔列表，与 nuget.org 上的配置文件名称一致。</span><span class="sxs-lookup"><span data-stu-id="70616-133">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="70616-134">描述包的标记和关键字的空格分隔列表。</span><span class="sxs-lookup"><span data-stu-id="70616-134">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="70616-135">搜索包时使用标记。</span><span class="sxs-lookup"><span data-stu-id="70616-135">Tags are used when searching for packages.</span></span>             |
| `PackageIcon`                   | `icon`                  | <span data-ttu-id="70616-136">包中要用作包图标的图像的路径。</span><span class="sxs-lookup"><span data-stu-id="70616-136">A path to an image in the package to use as a package icon.</span></span> <span data-ttu-id="70616-137">详细了解 [`icon` 元数据](/nuget/reference/nuspec#icon)。</span><span class="sxs-lookup"><span data-stu-id="70616-137">Read more about [`icon` metadata](/nuget/reference/nuspec#icon).</span></span> |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="70616-138">项目主页或源存储库的 URL。</span><span class="sxs-lookup"><span data-stu-id="70616-138">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseExpression`         | `license`                  | <span data-ttu-id="70616-139">项目许可证的 [SPDX 标识符](https://spdx.org/licenses/)。</span><span class="sxs-lookup"><span data-stu-id="70616-139">The project license's [SPDX identifier](https://spdx.org/licenses/).</span></span> <span data-ttu-id="70616-140">只有获得 OSI 和 FSF 批准的许可证才能使用标识符。</span><span class="sxs-lookup"><span data-stu-id="70616-140">Only OSI and FSF approved licenses can use an identifier.</span></span> <span data-ttu-id="70616-141">其他许可证应使用 `PackageLicenseFile`。</span><span class="sxs-lookup"><span data-stu-id="70616-141">Other licenses should use `PackageLicenseFile`.</span></span> <span data-ttu-id="70616-142">详细了解 [`license` 元数据](/nuget/reference/nuspec#license)。</span><span class="sxs-lookup"><span data-stu-id="70616-142">Read more about [`license` metadata](/nuget/reference/nuspec#license).</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="70616-143">无许可证的项目默认为 [exclusive copyright](https://choosealicense.com/no-permission/)（独占版权所有），从而无法供其他人使用。</span><span class="sxs-lookup"><span data-stu-id="70616-143">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it legally impossible for other people to use.</span></span>

<span data-ttu-id="70616-144">✔️ 请考虑选择带有满足 NuGet 前缀预留[条件](/nuget/reference/id-prefix-reservation)的前缀的 NuGet 包名称。</span><span class="sxs-lookup"><span data-stu-id="70616-144">✔️ CONSIDER choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="70616-145">✔️ 请使用指向包图标的 HTTPS href。</span><span class="sxs-lookup"><span data-stu-id="70616-145">✔️ DO use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="70616-146">启用 HTTPS 运行并显示非 HTTPS 图像的 NuGet.org 等网站将创建混合内容警告。</span><span class="sxs-lookup"><span data-stu-id="70616-146">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="70616-147">✔️ 请使用属于 64x64 并具有透明背景的包图标图像以获得最佳查看结果。</span><span class="sxs-lookup"><span data-stu-id="70616-147">✔️ DO use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

<span data-ttu-id="70616-148">✔️ 请考虑设置[源链接](./sourcelink.md)以将源代码管理元数据添加到程序集和 NuGet 包中。</span><span class="sxs-lookup"><span data-stu-id="70616-148">✔️ CONSIDER setting up [Source Link](./sourcelink.md) to add source control metadata to your assemblies and NuGet package.</span></span>

> <span data-ttu-id="70616-149">源链接会自动将 `RepositoryUrl` 和 `RepositoryType` 元数据添加到 NuGet 包中。</span><span class="sxs-lookup"><span data-stu-id="70616-149">Source Link automatically adds `RepositoryUrl` and `RepositoryType` metadata to the NuGet package.</span></span> <span data-ttu-id="70616-150">源链接还会添加用于构建包的确切源代码的相关信息。</span><span class="sxs-lookup"><span data-stu-id="70616-150">Source Link also adds information about the exact source code the package was built from.</span></span> <span data-ttu-id="70616-151">例如，从 Git 存储库创建的包将添加提交哈希作为元数据。</span><span class="sxs-lookup"><span data-stu-id="70616-151">For example, a package created from a Git repository will have the commit hash added as metadata.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="70616-152">预发行包</span><span class="sxs-lookup"><span data-stu-id="70616-152">Pre-release packages</span></span>

<span data-ttu-id="70616-153">具有版本后缀的 NuGet 包被视为[预发行版](/nuget/create-packages/prerelease-packages)。</span><span class="sxs-lookup"><span data-stu-id="70616-153">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="70616-154">默认情况下，NuGet 包管理器 UI 显示稳定版本，除非用户选择预发行包，使预发行包适用于受限的用户测试。</span><span class="sxs-lookup"><span data-stu-id="70616-154">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="70616-155">稳定版包不能依赖于预发行包。</span><span class="sxs-lookup"><span data-stu-id="70616-155">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="70616-156">必须创建自己的预发行包或依赖于较旧的稳定版本。</span><span class="sxs-lookup"><span data-stu-id="70616-156">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="70616-157">![NuGet 预发布版本包依赖项](./media/nuget/nuget-prerelease-package.png "NuGet 预发布版本包依赖项")</span><span class="sxs-lookup"><span data-stu-id="70616-157">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="70616-158">✔️ 请在测试、预览或试用预发行包后进行发布。</span><span class="sxs-lookup"><span data-stu-id="70616-158">✔️ DO publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="70616-159">✔️ 请在稳定版包就绪后进行发布，以便其他稳定版包可以引用它。</span><span class="sxs-lookup"><span data-stu-id="70616-159">✔️ DO publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="70616-160">符号包</span><span class="sxs-lookup"><span data-stu-id="70616-160">Symbol packages</span></span>

<span data-ttu-id="70616-161">符号文件 (`*.pdb`) 由 .NET 编译器与程序集一起生成。</span><span class="sxs-lookup"><span data-stu-id="70616-161">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="70616-162">符号文件将执行位置映射到原始源代码，以便可以逐行执行源代码（因为它使用调试程序运行）。</span><span class="sxs-lookup"><span data-stu-id="70616-162">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="70616-163">NuGet 支持[生成单独的符号包 (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg)（包含符号文件）以及主包（包含 .NET 程序集）。</span><span class="sxs-lookup"><span data-stu-id="70616-163">NuGet supports [generating a separate symbol package (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="70616-164">符号包的理念是它们托管在符号服务器上并仅由 Visual Studio 等工具按需下载。</span><span class="sxs-lookup"><span data-stu-id="70616-164">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="70616-165">NuGet.org 托管了自己的[符号服务器存储库](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server)。</span><span class="sxs-lookup"><span data-stu-id="70616-165">NuGet.org hosts its own [symbols server repository](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span></span> <span data-ttu-id="70616-166">开发人员可以通过向其在 [Visual Studio 中的符号源](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)添加 `https://symbols.nuget.org/download/symbols`，来使用发布到 NuGet.org 符号服务器的符号。</span><span class="sxs-lookup"><span data-stu-id="70616-166">Developers can use the symbols published to the NuGet.org symbol server by adding `https://symbols.nuget.org/download/symbols` to their [symbol sources in Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70616-167">NuGet.org 符号服务器仅支持由 SDK 样式项目创建的新的[可移植符号文件](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`)。</span><span class="sxs-lookup"><span data-stu-id="70616-167">The NuGet.org symbol server only supports the new [portable symbol files](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects.</span></span>
>
> <span data-ttu-id="70616-168">若要在调试 .NET 库时使用 NuGet.org 符号服务器，开发人员必须安装有 Visual Studio 2017 版本 15.9 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="70616-168">To use the NuGet.org symbol server when debugging a .NET library, developers must have Visual Studio 2017 version 15.9 or later.</span></span>

<span data-ttu-id="70616-169">创建符号包的另一种方法是在主 NuGet 包中嵌入符号文件。</span><span class="sxs-lookup"><span data-stu-id="70616-169">An alternative to creating a symbol package is embedding symbol files in the main NuGet package.</span></span> <span data-ttu-id="70616-170">主 NuGet 包将变大，但嵌入的符号文件意味着开发人员不需要配置 NuGet.org 符号服务器。</span><span class="sxs-lookup"><span data-stu-id="70616-170">The main NuGet package will be larger, but the embedded symbol files means developers don't need to configure the NuGet.org symbol server.</span></span> <span data-ttu-id="70616-171">如果使用 SDK 样式项目生成 NuGet 包，则可以通过设置 `AllowedOutputExtensionsInPackageBuildOutputFolder` 属性来嵌入符号文件：</span><span class="sxs-lookup"><span data-stu-id="70616-171">If you're building your NuGet package using an SDK-style project, then you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="70616-172">嵌入式符号文件的缺点是，对于使用 SDK 样式项目编译的 .NET 库，它们会将包的大小增加约 30%。</span><span class="sxs-lookup"><span data-stu-id="70616-172">The downside of embedding symbol files is that they increase the package size by about 30% for .NET libraries compiled using SDK-style projects.</span></span> <span data-ttu-id="70616-173">如果要考虑包大小，应改成在符号包中发布符号。</span><span class="sxs-lookup"><span data-stu-id="70616-173">If package size is a concern, you should publish symbols in a symbol package instead.</span></span>

<span data-ttu-id="70616-174">✔️ 请考虑将符号作为符号包 (`*.snupkg`) 发布到 NuGet.org</span><span class="sxs-lookup"><span data-stu-id="70616-174">✔️ CONSIDER publishing symbols as a symbol package (`*.snupkg`) to NuGet.org</span></span>

> <span data-ttu-id="70616-175">符号包 (`*.snupkg`) 为开发人员提供了良好的按需调试体验，而不会使主程序包大小膨胀，也不会影响那些不打算调试 NuGet 包的用户的还原性能。</span><span class="sxs-lookup"><span data-stu-id="70616-175">Symbol packages (`*.snupkg`) provide developers a good on-demand debugging experience without bloating the main package size and impacting restore performance for those who don't intend to debug the NuGet package.</span></span>
>
> <span data-ttu-id="70616-176">需要注意的是，用户可能需要在其 IDE 中查找和配置 NuGet 符号服务器（作为一次性设置）来获取符号文件。</span><span class="sxs-lookup"><span data-stu-id="70616-176">The caveat is that users may need to find and configure the NuGet symbol server in their IDE (as a one-time setup) to get symbol files.</span></span> <span data-ttu-id="70616-177">Visual Studio 2019 版本 16.1 将 NuGet.org 的符号服务器添加到了默认符号服务器列表中。</span><span class="sxs-lookup"><span data-stu-id="70616-177">Visual Studio 2019 version 16.1 added NuGet.org's symbol server to the list of default symbol servers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="70616-178">[上一页](strong-naming.md)
>[下一页](dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="70616-178">[Previous](strong-naming.md)
[Next](dependencies.md)</span></span>
