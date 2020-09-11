---
title: dotnet publish 命令
description: dotnet publish 命令可将 .NET Core 项目或解决方案发布到目录。
ms.date: 02/24/2020
ms.openlocfilehash: f171baaa0dbc070b6389ec0fa9895b2c5dcfafff
ms.sourcegitcommit: f279a4488c48236793c04bf825ae6f9128790849
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2020
ms.locfileid: "89501904"
---
# <a name="dotnet-publish"></a><span data-ttu-id="f74aa-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="f74aa-103">dotnet publish</span></span>

<span data-ttu-id="f74aa-104">本文适用于： ✔️ .NET Core 2.1 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="f74aa-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f74aa-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="f74aa-105">Name</span></span>

<span data-ttu-id="f74aa-106">`dotnet publish` - 将应用程序及其依赖项发布到文件夹以部署到托管系统。</span><span class="sxs-lookup"><span data-stu-id="f74aa-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f74aa-107">摘要</span><span class="sxs-lookup"><span data-stu-id="f74aa-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a><span data-ttu-id="f74aa-108">描述</span><span class="sxs-lookup"><span data-stu-id="f74aa-108">Description</span></span>

<span data-ttu-id="f74aa-109">`dotnet publish` 编译应用程序、读取 project 文件中指定的所有依赖项并将生成的文件集发布到目录。</span><span class="sxs-lookup"><span data-stu-id="f74aa-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="f74aa-110">输出包括以下资产：</span><span class="sxs-lookup"><span data-stu-id="f74aa-110">The output includes the following assets:</span></span>

- <span data-ttu-id="f74aa-111">扩展名为 dll 的程序集中的中间语言 (IL) 代码。</span><span class="sxs-lookup"><span data-stu-id="f74aa-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="f74aa-112">包含项目所有依赖项的 .deps.json 文件。</span><span class="sxs-lookup"><span data-stu-id="f74aa-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="f74aa-113">.runtimeconfig.json 文件，其中指定了应用程序所需的共享运行时，以及运行时的其他配置选项（例如垃圾回收类型）。</span><span class="sxs-lookup"><span data-stu-id="f74aa-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="f74aa-114">应用程序的依赖项，将这些依赖项从 NuGet 缓存复制到输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="f74aa-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="f74aa-115">`dotnet publish` 命令的输出可供部署至托管系统（例如服务器、电脑、Mac、笔记本电脑）以便执行。</span><span class="sxs-lookup"><span data-stu-id="f74aa-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="f74aa-116">若要准备用于部署的应用程序，这是唯一正式受支持的方法。</span><span class="sxs-lookup"><span data-stu-id="f74aa-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="f74aa-117">根据项目指定的部署的类型，托管系统不一定已在其上安装 .NET Core 共享运行时。</span><span class="sxs-lookup"><span data-stu-id="f74aa-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="f74aa-118">有关详细信息，请参阅[使用 .NET Core CLI 发布 .NET Core 应用](../deploying/deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="f74aa-119">隐式还原</span><span class="sxs-lookup"><span data-stu-id="f74aa-119">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a><span data-ttu-id="f74aa-120">MSBuild</span><span class="sxs-lookup"><span data-stu-id="f74aa-120">MSBuild</span></span>

<span data-ttu-id="f74aa-121">`dotnet publish` 命令调用 MSBuild，后者会调用 `Publish` 目标。</span><span class="sxs-lookup"><span data-stu-id="f74aa-121">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="f74aa-122">任何传递给 `dotnet publish` 的参数都将传递给 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="f74aa-122">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="f74aa-123">`-c` 和 `-o` 参数分别映射到 MSBuild 的 `Configuration` 和 `PublishDir` 属性。</span><span class="sxs-lookup"><span data-stu-id="f74aa-123">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `PublishDir` properties, respectively.</span></span>

<span data-ttu-id="f74aa-124">`dotnet publish` 命令接受 MSBuild 选项，如用来设置属性的 `-p` 和用来定义记录器的 `-l`。</span><span class="sxs-lookup"><span data-stu-id="f74aa-124">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="f74aa-125">例如，可以使用以下格式设置 MSBuild 属性：`-p:<NAME>=<VALUE>`。</span><span class="sxs-lookup"><span data-stu-id="f74aa-125">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span>

<span data-ttu-id="f74aa-126">还可通过引用 .pubxml 文件（自 .NET Core 3.1 SDK 起可用）设置与发布相关的属性。</span><span class="sxs-lookup"><span data-stu-id="f74aa-126">You can also set publish-related properties by referring to a *.pubxml* file (available since .NET Core 3.1 SDK).</span></span> <span data-ttu-id="f74aa-127">例如：</span><span class="sxs-lookup"><span data-stu-id="f74aa-127">For example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=FolderProfile
```

<span data-ttu-id="f74aa-128">前面的示例使用 \<project_folder>/Properties/PublishProfiles 文件夹中的 FolderProfile.pubxml 文件。</span><span class="sxs-lookup"><span data-stu-id="f74aa-128">The preceding example uses the *FolderProfile.pubxml* file that is found in the *\<project_folder>/Properties/PublishProfiles* folder.</span></span> <span data-ttu-id="f74aa-129">如果在设置 `PublishProfile` 属性时指定路径和文件扩展名，则它们会被忽略。</span><span class="sxs-lookup"><span data-stu-id="f74aa-129">If you specify a path and file extension when setting the `PublishProfile` property, they are ignored.</span></span> <span data-ttu-id="f74aa-130">默认情况下，MSBuild 会在 Properties/PublishProfiles 文件夹中查找，并假定 .pubxml 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="f74aa-130">MSBuild by default looks in the *Properties/PublishProfiles* folder and assumes the *pubxml* file extension.</span></span> <span data-ttu-id="f74aa-131">若要指定包含扩展名的路径和文件名，请设置 `PublishProfileFullPath` 属性，而不是 `PublishProfile` 属性。</span><span class="sxs-lookup"><span data-stu-id="f74aa-131">To specify the path and filename including extension, set the `PublishProfileFullPath` property instead of the `PublishProfile` property.</span></span>

<span data-ttu-id="f74aa-132">有关更多信息，请参见以下资源：</span><span class="sxs-lookup"><span data-stu-id="f74aa-132">For more information, see the following resources:</span></span>

- [<span data-ttu-id="f74aa-133">MSBuild 命令行参考</span><span class="sxs-lookup"><span data-stu-id="f74aa-133">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="f74aa-134">用于 ASP.NET Core 应用部署的 Visual Studio 发布配置文件 (.pubxml)</span><span class="sxs-lookup"><span data-stu-id="f74aa-134">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="f74aa-135">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="f74aa-135">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="f74aa-136">自变量</span><span class="sxs-lookup"><span data-stu-id="f74aa-136">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="f74aa-137">要发布的项目或解决方案。</span><span class="sxs-lookup"><span data-stu-id="f74aa-137">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="f74aa-138">`PROJECT` 是 [C#](csproj.md)、F# 或 Visual Basic 项目文件的路径和文件名，或包含 C#、F# 或 Visual Basic 项目文件的目录的路径。</span><span class="sxs-lookup"><span data-stu-id="f74aa-138">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="f74aa-139">如果未指定目录，则默认为当前目录。</span><span class="sxs-lookup"><span data-stu-id="f74aa-139">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="f74aa-140">`SOLUTION` 是解决方案文件（扩展名为 .sln）的路径和文件名，或包含解决方案文件的目录的路径。</span><span class="sxs-lookup"><span data-stu-id="f74aa-140">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="f74aa-141">如果未指定目录，则默认为当前目录。</span><span class="sxs-lookup"><span data-stu-id="f74aa-141">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="f74aa-142">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="f74aa-142">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="f74aa-143">选项</span><span class="sxs-lookup"><span data-stu-id="f74aa-143">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="f74aa-144">定义生成配置。</span><span class="sxs-lookup"><span data-stu-id="f74aa-144">Defines the build configuration.</span></span> <span data-ttu-id="f74aa-145">大多数项目的默认配置为 `Debug`，但你可以覆盖项目中的生成配置设置。</span><span class="sxs-lookup"><span data-stu-id="f74aa-145">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f74aa-146">为指定的[目标框架](../../standard/frameworks.md)发布应用程序。</span><span class="sxs-lookup"><span data-stu-id="f74aa-146">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="f74aa-147">必须在项目文件中指定目标框架。</span><span class="sxs-lookup"><span data-stu-id="f74aa-147">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="f74aa-148">强制解析所有依赖项，即使上次还原已成功，也不例外。</span><span class="sxs-lookup"><span data-stu-id="f74aa-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="f74aa-149">指定此标记等同于删除 project.assets.json 文件。</span><span class="sxs-lookup"><span data-stu-id="f74aa-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f74aa-150">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="f74aa-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="f74aa-151">允许命令停止并等待用户输入或操作。</span><span class="sxs-lookup"><span data-stu-id="f74aa-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="f74aa-152">例如，完成身份验证。</span><span class="sxs-lookup"><span data-stu-id="f74aa-152">For example, to complete authentication.</span></span> <span data-ttu-id="f74aa-153">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="f74aa-153">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="f74aa-154">指定一个或多个[目标清单](../deploying/runtime-store.md)，用于剪裁与应用程序一同发布的一组包。</span><span class="sxs-lookup"><span data-stu-id="f74aa-154">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="f74aa-155">清单文件是 [`dotnet store` 命令](dotnet-store.md)输出的一部分。</span><span class="sxs-lookup"><span data-stu-id="f74aa-155">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="f74aa-156">若要指定多个清单，请为每个清单添加一个 `--manifest` 选项。</span><span class="sxs-lookup"><span data-stu-id="f74aa-156">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="f74aa-157">发布前不生成项目。</span><span class="sxs-lookup"><span data-stu-id="f74aa-157">Doesn't build the project before publishing.</span></span> <span data-ttu-id="f74aa-158">还将隐式设置 `--no-restore` 标记。</span><span class="sxs-lookup"><span data-stu-id="f74aa-158">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="f74aa-159">忽略项目间引用，仅还原根项目。</span><span class="sxs-lookup"><span data-stu-id="f74aa-159">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="f74aa-160">不显示启动版权标志或版权消息。</span><span class="sxs-lookup"><span data-stu-id="f74aa-160">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="f74aa-161">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="f74aa-161">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f74aa-162">运行此命令时不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="f74aa-162">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f74aa-163">指定输出目录的路径。</span><span class="sxs-lookup"><span data-stu-id="f74aa-163">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="f74aa-164">如果未指定，则默认为依赖框架的可执行文件和跨平台二进制文件的路径 [project_file_folder]/bin/[configuration]/[framework]/publish/。</span><span class="sxs-lookup"><span data-stu-id="f74aa-164">If not specified, it defaults to *[project_file_folder]/bin/[configuration]/[framework]/publish/* for a framework-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="f74aa-165">默认为独立的可执行文件路径 [project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/。</span><span class="sxs-lookup"><span data-stu-id="f74aa-165">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="f74aa-166">在 Web 项目中，如果输出文件夹位于项目文件夹，则连续的 `dotnet publish` 命令将产生嵌套的输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="f74aa-166">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="f74aa-167">例如，如果项目文件夹是“myproject”，发布输出文件夹是“myproject/publish”，并且运行 `dotnet publish` 两次，则第二次运行会将“.config”和“.json”等内容文件放入“myproject/publish/publish”    。</span><span class="sxs-lookup"><span data-stu-id="f74aa-167">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="f74aa-168">若要避免嵌套发布文件夹，请指定一个不在项目文件夹正下方的发布文件夹，或从项目中排除发布文件夹。</span><span class="sxs-lookup"><span data-stu-id="f74aa-168">To avoid nesting publish folders, specify a publish folder that is not **directly** under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="f74aa-169">若要排除名为“publishoutput”的发布文件夹，请将以下元素添加到“.csproj”文件中的 `PropertyGroup` 元素中 ：</span><span class="sxs-lookup"><span data-stu-id="f74aa-169">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="f74aa-170">.NET Core 3.x SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="f74aa-170">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="f74aa-171">如果在发布项目时指定了相对路径，则生成的输出目录相对于当前工作目录，而不是项目文件位置。</span><span class="sxs-lookup"><span data-stu-id="f74aa-171">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="f74aa-172">如果在发布解决方案时指定了相对路径，则所有项目的所有输出都会进入相对于当前工作目录的指定文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f74aa-172">If a relative path is specified when publishing a solution, all output for all projects goes into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="f74aa-173">若要使发布输出进入每个项目的单独文件夹，请使用 msbuild `PublishDir` 属性（而不是 `--output` 选项）指定相对路径。</span><span class="sxs-lookup"><span data-stu-id="f74aa-173">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="f74aa-174">例如，`dotnet publish -p:PublishDir=.\publish` 将每个项目的发布输出发送到包含项目文件的文件夹下的 `publish` 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f74aa-174">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="f74aa-175">.NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="f74aa-175">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="f74aa-176">如果在发布项目时指定了相对路径，则生成的输出目录相对于项目文件位置，而不是当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="f74aa-176">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="f74aa-177">如果在发布解决方案时指定了相对路径，则每个项目的输出会进入相对于项目文件位置的单独文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f74aa-177">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="f74aa-178">如果在发布解决方案时指定了绝对路径，则所有项目的所有发布输出都会进入指定文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f74aa-178">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun=true`**

  <span data-ttu-id="f74aa-179">以 ReadyToRun (R2R) 格式编译应用程序集。</span><span class="sxs-lookup"><span data-stu-id="f74aa-179">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="f74aa-180">R2R 是一种预先 (AOT) 编译形式。</span><span class="sxs-lookup"><span data-stu-id="f74aa-180">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="f74aa-181">有关详细信息，请参阅 [ReadyToRun 图像](../whats-new/dotnet-core-3-0.md#readytorun-images)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-181">For more information, see [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span> <span data-ttu-id="f74aa-182">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="f74aa-182">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f74aa-183">建议在发布配置文件中而不是在命令行中指定此选项。</span><span class="sxs-lookup"><span data-stu-id="f74aa-183">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="f74aa-184">有关详细信息，请参阅 [MSBuild](#msbuild)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-184">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile=true`**

  <span data-ttu-id="f74aa-185">将应用打包到特定于平台的单个文件可执行文件中。</span><span class="sxs-lookup"><span data-stu-id="f74aa-185">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="f74aa-186">该可执行文件是自解压缩文件，包含运行应用所需的所有依赖项（包括本机依赖项）。</span><span class="sxs-lookup"><span data-stu-id="f74aa-186">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="f74aa-187">首次运行应用时，应用程序将根据应用名称和生成标识符自解压缩到一个目录中。</span><span class="sxs-lookup"><span data-stu-id="f74aa-187">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="f74aa-188">再次运行应用程序时，启动速度将变快。</span><span class="sxs-lookup"><span data-stu-id="f74aa-188">Startup is faster when the application is run again.</span></span> <span data-ttu-id="f74aa-189">除非使用了新版本，否则应用程序无需再次进行自解压缩。</span><span class="sxs-lookup"><span data-stu-id="f74aa-189">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="f74aa-190">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="f74aa-190">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="f74aa-191">有关单文件发布的详细信息，请参阅[单文件捆绑程序设计文档](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-191">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="f74aa-192">建议在发布配置文件中而不是在命令行中指定此选项。</span><span class="sxs-lookup"><span data-stu-id="f74aa-192">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="f74aa-193">有关详细信息，请参阅 [MSBuild](#msbuild)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-193">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed=true`**

  <span data-ttu-id="f74aa-194">在发布自包含的可执行文件时，剪裁未使用的库以减小应用的部署大小。</span><span class="sxs-lookup"><span data-stu-id="f74aa-194">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="f74aa-195">有关详细信息，请参阅[剪裁自包含部署和可执行文件](../deploying/trim-self-contained.md)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-195">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="f74aa-196">从 .NET Core 3.0 开始，SDK 作为预览功能提供。</span><span class="sxs-lookup"><span data-stu-id="f74aa-196">Available since .NET Core 3.0 SDK as a preview feature.</span></span>

  <span data-ttu-id="f74aa-197">建议在发布配置文件中而不是在命令行中指定此选项。</span><span class="sxs-lookup"><span data-stu-id="f74aa-197">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="f74aa-198">有关详细信息，请参阅 [MSBuild](#msbuild)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-198">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="f74aa-199">与应用程序一同发布 .NET Core 运行时，因此无需在目标计算机上安装运行时。</span><span class="sxs-lookup"><span data-stu-id="f74aa-199">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="f74aa-200">如果指定了运行时标识符，并且项目是可执行项目（而不是库项目），则默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="f74aa-200">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="f74aa-201">有关详细信息，请参阅 [.NET Core 应用程序发布](../deploying/index.md)和[使用 .NET Core CLI 发布 .NET Core 应用](../deploying/deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-201">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="f74aa-202">如果在未指定 `true` 或 `false` 的情况下使用此选项，则默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="f74aa-202">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="f74aa-203">在这种情况下，请不要紧接在 `--self-contained` 后放置解决方案或项目参数，因为该位置需要 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="f74aa-203">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="f74aa-204">等效于 `--self-contained false`。</span><span class="sxs-lookup"><span data-stu-id="f74aa-204">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="f74aa-205">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="f74aa-205">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f74aa-206">发布针对给定运行时的应用程序。</span><span class="sxs-lookup"><span data-stu-id="f74aa-206">Publishes the application for a given runtime.</span></span> <span data-ttu-id="f74aa-207">有关运行时标识符 (RID) 的列表，请参阅 [RID 目录](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-207">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="f74aa-208">有关详细信息，请参阅 [.NET Core 应用程序发布](../deploying/index.md)和[使用 .NET Core CLI 发布 .NET Core 应用](../deploying/deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-208">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f74aa-209">设置命令的详细级别。</span><span class="sxs-lookup"><span data-stu-id="f74aa-209">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f74aa-210">允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f74aa-210">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f74aa-211">默认值是 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="f74aa-211">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="f74aa-212">定义版本后缀来替换项目文件的版本字段中的星号 (`*`)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-212">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="f74aa-213">示例</span><span class="sxs-lookup"><span data-stu-id="f74aa-213">Examples</span></span>

- <span data-ttu-id="f74aa-214">为当前目录中的项目创建一个[依赖框架的跨平台二进制文件](../deploying/index.md#produce-a-cross-platform-binary)：</span><span class="sxs-lookup"><span data-stu-id="f74aa-214">Create a [framework-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="f74aa-215">自 .NET Core 3.0 SDK 起，此示例还为当前平台创建[依赖框架的可执行文件](../deploying/index.md#publish-framework-dependent)。</span><span class="sxs-lookup"><span data-stu-id="f74aa-215">Starting with .NET Core 3.0 SDK, this example also creates a [framework-dependent executable](../deploying/index.md#publish-framework-dependent) for the current platform.</span></span>

- <span data-ttu-id="f74aa-216">针对特定运行时，为当前目录中的项目创建[独立可执行文件](../deploying/index.md#publish-self-contained)：</span><span class="sxs-lookup"><span data-stu-id="f74aa-216">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="f74aa-217">项目文件中必须包含 RID。</span><span class="sxs-lookup"><span data-stu-id="f74aa-217">The RID must be in the project file.</span></span>

- <span data-ttu-id="f74aa-218">针对特定平台，为当前目录中的项目创建[依赖框架的可执行文件](../deploying/index.md#publish-framework-dependent)：</span><span class="sxs-lookup"><span data-stu-id="f74aa-218">Create a [framework-dependent executable](../deploying/index.md#publish-framework-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="f74aa-219">项目文件中必须包含 RID。</span><span class="sxs-lookup"><span data-stu-id="f74aa-219">The RID must be in the project file.</span></span> <span data-ttu-id="f74aa-220">此示例适用于 .NET Core 3.0 SDK 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="f74aa-220">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="f74aa-221">针对特定运行时和目标框架，在当前目录中发布项目：</span><span class="sxs-lookup"><span data-stu-id="f74aa-221">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="f74aa-222">发布指定的项目文件：</span><span class="sxs-lookup"><span data-stu-id="f74aa-222">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="f74aa-223">发布当前应用程序，但在还原操作期间不还原项目到项目 (P2P) 引用，只还原根项目：</span><span class="sxs-lookup"><span data-stu-id="f74aa-223">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="f74aa-224">请参阅</span><span class="sxs-lookup"><span data-stu-id="f74aa-224">See also</span></span>

- [<span data-ttu-id="f74aa-225">.NET Core 应用程序发布概述</span><span class="sxs-lookup"><span data-stu-id="f74aa-225">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="f74aa-226">使用 .NET Core CLI 发布 .NET Core 应用</span><span class="sxs-lookup"><span data-stu-id="f74aa-226">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="f74aa-227">目标框架</span><span class="sxs-lookup"><span data-stu-id="f74aa-227">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="f74aa-228">运行时标识符 (RID) 目录</span><span class="sxs-lookup"><span data-stu-id="f74aa-228">Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="f74aa-229">处理 macOS Catalina 公证</span><span class="sxs-lookup"><span data-stu-id="f74aa-229">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="f74aa-230">已发布应用程序的目录结构</span><span class="sxs-lookup"><span data-stu-id="f74aa-230">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="f74aa-231">MSBuild 命令行参考</span><span class="sxs-lookup"><span data-stu-id="f74aa-231">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="f74aa-232">用于 ASP.NET Core 应用部署的 Visual Studio 发布配置文件 (.pubxml)</span><span class="sxs-lookup"><span data-stu-id="f74aa-232">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="f74aa-233">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="f74aa-233">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="f74aa-234">ILLInk.Tasks</span><span class="sxs-lookup"><span data-stu-id="f74aa-234">ILLInk.Tasks</span></span>](https://aka.ms/dotnet-illink)
