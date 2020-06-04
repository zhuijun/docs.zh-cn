---
title: dotnet restore 命令
description: 了解如何使用 dotnet-restore 命令还原依赖项和特定于项目的工具。
ms.date: 02/27/2020
ms.openlocfilehash: 276fad896a6a8a647ed05a9de8c582d463d9ab8f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005307"
---
# <a name="dotnet-restore"></a><span data-ttu-id="b21bc-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b21bc-103">dotnet restore</span></span>

<span data-ttu-id="b21bc-104">本文适用于： ✔️ .NET Core 2.1 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="b21bc-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b21bc-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="b21bc-105">Name</span></span>

<span data-ttu-id="b21bc-106">`dotnet restore` - 恢复项目的依赖项和工具。</span><span class="sxs-lookup"><span data-stu-id="b21bc-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b21bc-107">摘要</span><span class="sxs-lookup"><span data-stu-id="b21bc-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lock-file] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="b21bc-108">描述</span><span class="sxs-lookup"><span data-stu-id="b21bc-108">Description</span></span>

<span data-ttu-id="b21bc-109">`dotnet restore` 命令使用 NuGet 还原依赖项以及在 project 文件中指定的特定于项目的工具。</span><span class="sxs-lookup"><span data-stu-id="b21bc-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span>  <span data-ttu-id="b21bc-110">在大多数情况下，不需要显式使用 `dotnet restore` 命令，因为在运行以下命令时，将会在必要时隐式运行 NuGet 还原：</span><span class="sxs-lookup"><span data-stu-id="b21bc-110">In most cases, you don't need to explicitly use the `dotnet restore` command, since a NuGet restore is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="b21bc-111">有时，通过这些命令运行隐式 NuGet 还原可能不方便。</span><span class="sxs-lookup"><span data-stu-id="b21bc-111">Sometimes, it might be inconvenient to run the implicit NuGet restore with these commands.</span></span> <span data-ttu-id="b21bc-112">例如，某些自动化系统（如生成系统）需要显式调用 `dotnet restore`，以控制还原发生的时间，以便可以控制网络使用量。</span><span class="sxs-lookup"><span data-stu-id="b21bc-112">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="b21bc-113">为了防止运行隐式 NuGet 还原，可以通过上述任意命令使用 `--no-restore` 标记禁用隐式还原。</span><span class="sxs-lookup"><span data-stu-id="b21bc-113">To prevent the implicit NuGet restore, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="b21bc-114">指定源</span><span class="sxs-lookup"><span data-stu-id="b21bc-114">Specify feeds</span></span>

<span data-ttu-id="b21bc-115">为了还原依赖项，NuGet 需要包所在的源。</span><span class="sxs-lookup"><span data-stu-id="b21bc-115">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="b21bc-116">通常通过“nuGet.config”配置文件提供源。</span><span class="sxs-lookup"><span data-stu-id="b21bc-116">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="b21bc-117">安装 .NET Core SDK 时提供一个默认的配置文件。</span><span class="sxs-lookup"><span data-stu-id="b21bc-117">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="b21bc-118">若要指定其他源，请执行以下任一项操作：</span><span class="sxs-lookup"><span data-stu-id="b21bc-118">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="b21bc-119">在项目目录中创建自己的 nuget.config 文件。</span><span class="sxs-lookup"><span data-stu-id="b21bc-119">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="b21bc-120">有关详细信息，请参阅本文后面介绍的[常见 NuGet 配置](/nuget/consume-packages/configuring-nuget-behavior)和 [nuget.config 差异](#nugetconfig-differences)。</span><span class="sxs-lookup"><span data-stu-id="b21bc-120">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="b21bc-121">使用诸如 [`dotnet nuget add source`](dotnet-nuget-add-source.md) 等 `dotnet nuget` 命令。</span><span class="sxs-lookup"><span data-stu-id="b21bc-121">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="b21bc-122">可以使用 `-s` 选项替代 nuget.config 源。</span><span class="sxs-lookup"><span data-stu-id="b21bc-122">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="b21bc-123">有关如何使用经过身份验证的源的信息，请参阅[使用经过身份验证的源中的包](/nuget/consume-packages/consuming-packages-authenticated-feeds)。</span><span class="sxs-lookup"><span data-stu-id="b21bc-123">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="global-packages-folder"></a><span data-ttu-id="b21bc-124">全局包文件夹</span><span class="sxs-lookup"><span data-stu-id="b21bc-124">Global packages folder</span></span>

<span data-ttu-id="b21bc-125">对于依赖项，可以使用 `--packages` 参数指定还原操作期间放置还原包的位置。</span><span class="sxs-lookup"><span data-stu-id="b21bc-125">For dependencies, you can specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="b21bc-126">如未指定，将使用默认的 NuGet 包缓存，可在所有操作系统上的用户主目录中的 `.nuget/packages` 目录找到它。</span><span class="sxs-lookup"><span data-stu-id="b21bc-126">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="b21bc-127">例如 Linux 上的 /home/user1 或 Windows 上的 C:\Users\user1 。</span><span class="sxs-lookup"><span data-stu-id="b21bc-127">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="b21bc-128">特定于项目的工具</span><span class="sxs-lookup"><span data-stu-id="b21bc-128">Project-specific tooling</span></span>

<span data-ttu-id="b21bc-129">对于特定于项目的工具，`dotnet restore` 首先还原打包工具所在的包，然后继续还原 project 文件中指定的工具依赖项。</span><span class="sxs-lookup"><span data-stu-id="b21bc-129">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="b21bc-130">nuget.config 差异</span><span class="sxs-lookup"><span data-stu-id="b21bc-130">nuget.config differences</span></span>

<span data-ttu-id="b21bc-131">`dotnet restore` 命令的行为会受 Nuget.Config 文件（如果有）中某些设置的影响。</span><span class="sxs-lookup"><span data-stu-id="b21bc-131">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="b21bc-132">例如，在 NuGet.Config 中设置 `globalPackagesFolder` 会将还原的 NuGet 包置于指定的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b21bc-132">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="b21bc-133">这是在 `dotnet restore` 命令中指定 `--packages` 选项的替代方法。</span><span class="sxs-lookup"><span data-stu-id="b21bc-133">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="b21bc-134">有关详细信息，请参阅 [nuget.config 参考](/nuget/schema/nuget-config-file)。</span><span class="sxs-lookup"><span data-stu-id="b21bc-134">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="b21bc-135">有三个 `dotnet restore` 可忽略的特定设置：</span><span class="sxs-lookup"><span data-stu-id="b21bc-135">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="b21bc-136">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="b21bc-136">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="b21bc-137">绑定重定向不适用于 `<PackageReference>` 元素，并且 .NET Core 仅支持 NuGet 包的 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="b21bc-137">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="b21bc-138">解决方案</span><span class="sxs-lookup"><span data-stu-id="b21bc-138">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="b21bc-139">此设置特定于 Visual Studio，不适用于 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="b21bc-139">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="b21bc-140">.Net Core 不使用 `packages.config` 文件，而是使用 NuGet 包的 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="b21bc-140">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="b21bc-141">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="b21bc-141">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="b21bc-142">此设置不适用，如 [NuGet 尚不支持跨平台验证](https://github.com/NuGet/Home/issues/7939)受信任包所述。</span><span class="sxs-lookup"><span data-stu-id="b21bc-142">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="arguments"></a><span data-ttu-id="b21bc-143">自变量</span><span class="sxs-lookup"><span data-stu-id="b21bc-143">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="b21bc-144">要还原的项目文件的可选路径。</span><span class="sxs-lookup"><span data-stu-id="b21bc-144">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="b21bc-145">选项</span><span class="sxs-lookup"><span data-stu-id="b21bc-145">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="b21bc-146">供还原操作使用的 NuGet 配置文件 (nuget.config)。</span><span class="sxs-lookup"><span data-stu-id="b21bc-146">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="b21bc-147">禁用并行还原多个项目。</span><span class="sxs-lookup"><span data-stu-id="b21bc-147">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="b21bc-148">强制解析所有依赖项，即使上次还原已成功，也不例外。</span><span class="sxs-lookup"><span data-stu-id="b21bc-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="b21bc-149">指定此标记等同于删除 project.assets.json 文件。</span><span class="sxs-lookup"><span data-stu-id="b21bc-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="b21bc-150">即使锁定文件已存在，也会强制还原以重新评估所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="b21bc-150">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b21bc-151">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="b21bc-151">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="b21bc-152">如果存在符合版本要求的包，则源失败时警告。</span><span class="sxs-lookup"><span data-stu-id="b21bc-152">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="b21bc-153">允许命令停止并等待用户输入或操作（例如，完成身份验证）。</span><span class="sxs-lookup"><span data-stu-id="b21bc-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="b21bc-154">从 .NET Core 2.1.400 开始。</span><span class="sxs-lookup"><span data-stu-id="b21bc-154">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="b21bc-155">写入项目锁定文件的输出位置。</span><span class="sxs-lookup"><span data-stu-id="b21bc-155">Output location where project lock file is written.</span></span> <span data-ttu-id="b21bc-156">默认情况下，此位置为 PROJECT_ROOT \packages.lock.json。</span><span class="sxs-lookup"><span data-stu-id="b21bc-156">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="b21bc-157">不允许更新项目锁定文件。</span><span class="sxs-lookup"><span data-stu-id="b21bc-157">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="b21bc-158">指定不缓存 HTTP 请求。</span><span class="sxs-lookup"><span data-stu-id="b21bc-158">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="b21bc-159">当使用项目到项目 (P2P) 引用还原项目时，还原根项目，不还原引用。</span><span class="sxs-lookup"><span data-stu-id="b21bc-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="b21bc-160">指定还原包的目录。</span><span class="sxs-lookup"><span data-stu-id="b21bc-160">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="b21bc-161">指定程序包还原的运行时。</span><span class="sxs-lookup"><span data-stu-id="b21bc-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="b21bc-162">这用于还原 *.csproj* 文件中的 `<RuntimeIdentifiers>` 标记中未显式列出的运行时的程序包。</span><span class="sxs-lookup"><span data-stu-id="b21bc-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="b21bc-163">有关运行时标识符 (RID) 的列表，请参阅 [RID 目录](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="b21bc-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="b21bc-164">通过多次指定此选项提供多个 RID。</span><span class="sxs-lookup"><span data-stu-id="b21bc-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="b21bc-165">指定要在还原操作期间使用的 NuGet 包源的 URI。</span><span class="sxs-lookup"><span data-stu-id="b21bc-165">Specifies the URI of the NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="b21bc-166">此设置会替代 nuget.config 文件中指定的所有源。</span><span class="sxs-lookup"><span data-stu-id="b21bc-166">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="b21bc-167">多次指定此选项可以提供多个源。</span><span class="sxs-lookup"><span data-stu-id="b21bc-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lock-file`**

  <span data-ttu-id="b21bc-168">允许生成项目锁定文件并与还原一起使用。</span><span class="sxs-lookup"><span data-stu-id="b21bc-168">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="b21bc-169">设置命令的详细级别。</span><span class="sxs-lookup"><span data-stu-id="b21bc-169">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b21bc-170">允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="b21bc-170">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b21bc-171">默认值是 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="b21bc-171">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="b21bc-172">示例</span><span class="sxs-lookup"><span data-stu-id="b21bc-172">Examples</span></span>

- <span data-ttu-id="b21bc-173">还原当前目录中项目的依赖项和工具：</span><span class="sxs-lookup"><span data-stu-id="b21bc-173">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="b21bc-174">还原在给定路径中找到的 `app1` 项目的依赖项和工具：</span><span class="sxs-lookup"><span data-stu-id="b21bc-174">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="b21bc-175">通过将提供的文件路径用作源，在当前目录中还原项目的依赖项和工具：</span><span class="sxs-lookup"><span data-stu-id="b21bc-175">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="b21bc-176">通过将提供的两个文件路径用作源，在当前目录中还原项目的依赖项和工具：</span><span class="sxs-lookup"><span data-stu-id="b21bc-176">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="b21bc-177">还原当前目录中项目的依赖项和工具，并显示详细的输出：</span><span class="sxs-lookup"><span data-stu-id="b21bc-177">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
