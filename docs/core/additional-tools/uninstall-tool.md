---
title: 卸载工具
description: .NET Core 卸载工具概述，它是一种可实现 .NET Core SDK 和运行时的受控清理的引导式工具。
author: sfoslund
ms.date: 05/27/2020
ms.openlocfilehash: 4e70fd3438b582bd5a0d6a52d7e58ed5e07f8811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446901"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="f4bff-103">.NET Core 卸载工具</span><span class="sxs-lookup"><span data-stu-id="f4bff-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="f4bff-104">[.NET Core 卸载工具](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) 使你可以从系统中删除 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="f4bff-105">可使用选项集合来指定要卸载的版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="f4bff-106">该工具支持 Windows 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="f4bff-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="f4bff-107">目前不支持 Linux。</span><span class="sxs-lookup"><span data-stu-id="f4bff-107">Linux is currently not supported.</span></span>

<span data-ttu-id="f4bff-108">在 Windows 上，该工具只能卸载使用以下安装程序之一安装的 SDK 和运行时：</span><span class="sxs-lookup"><span data-stu-id="f4bff-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="f4bff-109">.NET Core SDK 和运行时安装程序。</span><span class="sxs-lookup"><span data-stu-id="f4bff-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="f4bff-110">Visual studio 安装程序的版本早于 Visual Studio 2019 版本 16.3。</span><span class="sxs-lookup"><span data-stu-id="f4bff-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="f4bff-111">在 macOS 上，该工具只能卸载位于 /usr/local/share/dotnet 文件夹中的 SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="f4bff-112">由于这些限制，该工具可能无法卸载计算机上的所有 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="f4bff-113">可以使用 `dotnet --info` 命令来查找所有安装的 .NET Core SDK 和运行时，包括此工具无法删除的 SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="f4bff-114">`dotnet-core-uninstall list` 命令显示可以通过该工具卸载的 SDK。</span><span class="sxs-lookup"><span data-stu-id="f4bff-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="f4bff-115">安装工具</span><span class="sxs-lookup"><span data-stu-id="f4bff-115">Install the tool</span></span>

<span data-ttu-id="f4bff-116">可以从[此处](https://aka.ms/dotnet-core-uninstall-tool)下载 .NET Core 卸载工具，然后在 [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub 存储库中找到资源代码。</span><span class="sxs-lookup"><span data-stu-id="f4bff-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="f4bff-117">此工具需要提升才能卸载 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="f4bff-118">因此，应将其安装在写入保护的目录中，如 Windows 上的 C:\Program Files 或 macOS 上的 /usr/local/bin。</span><span class="sxs-lookup"><span data-stu-id="f4bff-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="f4bff-119">另请参阅[提升的 Dotnet 命令访问权限](../tools/elevated-access.md)。</span><span class="sxs-lookup"><span data-stu-id="f4bff-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="f4bff-120">有关详细信息，请参阅[详细安装说明](https://aka.ms/dotnet-core-uninstall-tool)。</span><span class="sxs-lookup"><span data-stu-id="f4bff-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="f4bff-121">运行该工具</span><span class="sxs-lookup"><span data-stu-id="f4bff-121">Run the tool</span></span>

<span data-ttu-id="f4bff-122">以下步骤说明了运行卸载工具的建议方法：</span><span class="sxs-lookup"><span data-stu-id="f4bff-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="f4bff-123">步骤 1 - 显示已安装的 .NET Core Sdk 和运行时</span><span class="sxs-lookup"><span data-stu-id="f4bff-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="f4bff-124">步骤 2 - 执行试运行</span><span class="sxs-lookup"><span data-stu-id="f4bff-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="f4bff-125">步骤 3 - 卸载 .NET Core SDK 和运行时</span><span class="sxs-lookup"><span data-stu-id="f4bff-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="f4bff-126">步骤 4 - 删除 NuGet 回退文件夹（可选）</span><span class="sxs-lookup"><span data-stu-id="f4bff-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="f4bff-127">步骤 1 - 显示安装的 .NET Core SDK 和运行时</span><span class="sxs-lookup"><span data-stu-id="f4bff-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="f4bff-128">`dotnet-core-uninstall list` 命令列出了已安装的 .NET Core SDK 和运行时，可以通过此工具将其删除。</span><span class="sxs-lookup"><span data-stu-id="f4bff-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="f4bff-129">Visual Studio 可能需要某些 SDK 和运行时，它们将显示出来，并说明为何不建议将其卸载。</span><span class="sxs-lookup"><span data-stu-id="f4bff-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="f4bff-130">在大多数情况下，`dotnet-core-uninstall list` 命令的输出将与 `dotnet --info` 输出中的已安装版本列表不匹配。</span><span class="sxs-lookup"><span data-stu-id="f4bff-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="f4bff-131">具体而言，此工具将不会显示通过 zip 文件安装的版本，也不会显示由 Visual Studio（Visual Studio 2019 16.3 或更高版本）托管的版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="f4bff-132">检查某个版本是否由 Visual Studio 托管的一种方法是在 `Add or Remove Programs` 中查看该版本，由 Visual Studio 托管的版本在显示名称中会以这种方式标记。</span><span class="sxs-lookup"><span data-stu-id="f4bff-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="f4bff-133">**dotnet-core-uninstall list**</span><span class="sxs-lookup"><span data-stu-id="f4bff-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="f4bff-134">摘要</span><span class="sxs-lookup"><span data-stu-id="f4bff-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="f4bff-135">选项</span><span class="sxs-lookup"><span data-stu-id="f4bff-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="f4bff-136">Windows</span><span class="sxs-lookup"><span data-stu-id="f4bff-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="f4bff-137">列出可通过此工具卸载的所有 ASP.NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="f4bff-138">列出可通过此工具卸载的所有 .NET Core 托管捆绑包。</span><span class="sxs-lookup"><span data-stu-id="f4bff-138">Lists all the .NET Core hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="f4bff-139">列出可通过此工具卸载的所有 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="f4bff-140">列出可通过此工具卸载的所有 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="f4bff-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="f4bff-141">设置详细程度。</span><span class="sxs-lookup"><span data-stu-id="f4bff-141">Sets the verbosity level.</span></span> <span data-ttu-id="f4bff-142">允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f4bff-143">默认值为 `normal`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="f4bff-144">列出可通过此工具卸载的所有 x64 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="f4bff-145">列出可通过此工具卸载的所有 x86 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="f4bff-146">macOS</span><span class="sxs-lookup"><span data-stu-id="f4bff-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="f4bff-147">列出可通过此工具卸载的所有 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="f4bff-148">列出可通过此工具卸载的所有 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="f4bff-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="f4bff-149">设置详细程度。</span><span class="sxs-lookup"><span data-stu-id="f4bff-149">Sets the verbosity level.</span></span> <span data-ttu-id="f4bff-150">允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f4bff-151">默认值为 `normal`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="f4bff-152">示例</span><span class="sxs-lookup"><span data-stu-id="f4bff-152">Examples</span></span>

* <span data-ttu-id="f4bff-153">列出可通过此工具删除的所有 .NET Core SDK 和运行时：</span><span class="sxs-lookup"><span data-stu-id="f4bff-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="f4bff-154">列出所有 x64 .NET Core SDK 和运行时：</span><span class="sxs-lookup"><span data-stu-id="f4bff-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="f4bff-155">列出所有 x86 .NET Core SDK：</span><span class="sxs-lookup"><span data-stu-id="f4bff-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="f4bff-156">步骤 2 - 执行试运行</span><span class="sxs-lookup"><span data-stu-id="f4bff-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="f4bff-157">`dotnet-core-uninstall dry-run` 和 `dotnet-core-uninstall whatif` 命令显示将根据提供的选项删除的 .NET Core SDK 和运行时，而无需执行卸载。</span><span class="sxs-lookup"><span data-stu-id="f4bff-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="f4bff-158">这些命令是同义词。</span><span class="sxs-lookup"><span data-stu-id="f4bff-158">These commands are synonyms.</span></span>

<span data-ttu-id="f4bff-159">**dotnet-core-uninstall dry-run 和 dotnet-core-uninstall whatif**</span><span class="sxs-lookup"><span data-stu-id="f4bff-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="f4bff-160">摘要</span><span class="sxs-lookup"><span data-stu-id="f4bff-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="f4bff-161">自变量</span><span class="sxs-lookup"><span data-stu-id="f4bff-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="f4bff-162">要卸载的指定版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-162">The specified version to uninstall.</span></span> <span data-ttu-id="f4bff-163">可以逐一列出多个版本，用空格分隔。</span><span class="sxs-lookup"><span data-stu-id="f4bff-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="f4bff-164">此外还支持响应文件。</span><span class="sxs-lookup"><span data-stu-id="f4bff-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="f4bff-165">响应文件是在命令行上放置所有版本的替代方法。</span><span class="sxs-lookup"><span data-stu-id="f4bff-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="f4bff-166">它们是文本文件，通常具有 \*.rsp 扩展名，每个版本都在单独的行上列出。</span><span class="sxs-lookup"><span data-stu-id="f4bff-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="f4bff-167">若要为 `VERSION` 参数指定响应文件，请使用后面紧跟响应文件名的 \@ 字符。</span><span class="sxs-lookup"><span data-stu-id="f4bff-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="f4bff-168">选项</span><span class="sxs-lookup"><span data-stu-id="f4bff-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="f4bff-169">Windows</span><span class="sxs-lookup"><span data-stu-id="f4bff-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="f4bff-170">删除所有 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="f4bff-171">仅删除版本小于指定版本的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="f4bff-172">仍安装指定版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="f4bff-173">除了那些指定版本外，删除所有 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="f4bff-174">删除 .NET Core SDK 和运行时（最高版本除外）。</span><span class="sxs-lookup"><span data-stu-id="f4bff-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="f4bff-175">删除由较高版本的修补程序取代的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="f4bff-176">此选项保护 global.json。</span><span class="sxs-lookup"><span data-stu-id="f4bff-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="f4bff-177">删除标记为预览的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="f4bff-178">删除标记为预览的 .NET Core SDK 和运行时（最高预览版除外）。</span><span class="sxs-lookup"><span data-stu-id="f4bff-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="f4bff-179">仅删除 ASP.NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="f4bff-180">仅删除 .NET Core 运行时和托管绑定。</span><span class="sxs-lookup"><span data-stu-id="f4bff-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="f4bff-181">删除与指定 `major.minor` 版本相匹配的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="f4bff-182">仅删除 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="f4bff-183">仅删除 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="f4bff-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="f4bff-184">设置详细程度。</span><span class="sxs-lookup"><span data-stu-id="f4bff-184">Sets the verbosity level.</span></span> <span data-ttu-id="f4bff-185">允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f4bff-186">默认值为 `normal`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="f4bff-187">必须与 `--sdk`、`--runtime` 和 `--aspnet-runtime` 结合使用才能删除 x64 SDK 或运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="f4bff-188">必须与 `--sdk`、`--runtime` 和 `--aspnet-runtime` 结合使用才能删除 x86 SDK 或运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="f4bff-189">`--force` 强制删除可能由 Visual Studio 使用的版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="f4bff-190">注意：</span><span class="sxs-lookup"><span data-stu-id="f4bff-190">Notes:</span></span>

1. <span data-ttu-id="f4bff-191">只需 `--sdk`、`--runtime`、`--aspnet-runtime` 和 `--hosting-bundle` 中的一个。</span><span class="sxs-lookup"><span data-stu-id="f4bff-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="f4bff-192">`--all`、`--all-below`、`--all-but`、`--all-but-latest`、`--all-lower-patches`、`--all-previews`、`--all-previews-but-latest`、`--major-minor` 和 `[<VERSION>...]` 除外。</span><span class="sxs-lookup"><span data-stu-id="f4bff-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="f4bff-193">如果未指定 `--x64` 或 `--x86`，则同时删除 x64 和 x86。</span><span class="sxs-lookup"><span data-stu-id="f4bff-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="f4bff-194">macOS</span><span class="sxs-lookup"><span data-stu-id="f4bff-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="f4bff-195">删除所有 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="f4bff-196">删除低于指定版本的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="f4bff-197">将保留指定的版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="f4bff-198">删除 .NET Core SDK 和运行时（指定版本除外）。</span><span class="sxs-lookup"><span data-stu-id="f4bff-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="f4bff-199">删除 .NET Core SDK 和运行时（最高版本除外）。</span><span class="sxs-lookup"><span data-stu-id="f4bff-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="f4bff-200">删除由较高版本的修补程序取代的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="f4bff-201">此选项保护 global.json。</span><span class="sxs-lookup"><span data-stu-id="f4bff-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="f4bff-202">删除标记为预览的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="f4bff-203">删除标记为预览的 .NET Core SDK 和运行时（最高预览版除外）。</span><span class="sxs-lookup"><span data-stu-id="f4bff-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="f4bff-204">删除与指定 `major.minor` 版本相匹配的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="f4bff-205">仅删除 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="f4bff-206">仅删除 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="f4bff-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="f4bff-207">设置详细程度。</span><span class="sxs-lookup"><span data-stu-id="f4bff-207">Sets the verbosity level.</span></span> <span data-ttu-id="f4bff-208">允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f4bff-209">默认值为 `normal`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="f4bff-210">`--force` 强制删除可能由 Visual Studio 或 SDK 使用的版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="f4bff-211">注意：</span><span class="sxs-lookup"><span data-stu-id="f4bff-211">Notes:</span></span>

1. <span data-ttu-id="f4bff-212">只需 `--sdk` 和 `--runtime` 中的一个。</span><span class="sxs-lookup"><span data-stu-id="f4bff-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="f4bff-213">`--all`、`--all-below`、`--all-but`、`--all-but-latest`、`--all-lower-patches`、`--all-previews`、`--all-previews-but-latest`、`--major-minor` 和 `[<VERSION>...]` 除外。</span><span class="sxs-lookup"><span data-stu-id="f4bff-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="f4bff-214">示例</span><span class="sxs-lookup"><span data-stu-id="f4bff-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="f4bff-215">默认情况下，Visual Studio 或其他 SDK 可能需要的 .NET Core SDK 和运行时不会包含在 `dotnet-core-uninstall dry-run` 输出中。</span><span class="sxs-lookup"><span data-stu-id="f4bff-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="f4bff-216">在下面的示例中，某些指定的 SDK 和运行时可能不会包含在输出中，具体取决于计算机的状态。</span><span class="sxs-lookup"><span data-stu-id="f4bff-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="f4bff-217">若要包括所有 SDK 和运行时，请将它们显式列出为参数或使用 `--force` 选项。</span><span class="sxs-lookup"><span data-stu-id="f4bff-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="f4bff-218">试运行删除已被较高版本的修补程序取代的所有 .NET Core 运行时：</span><span class="sxs-lookup"><span data-stu-id="f4bff-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="f4bff-219">试运行删除低于版本 `2.2.301` 的所有 .NET Core SDK：</span><span class="sxs-lookup"><span data-stu-id="f4bff-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="f4bff-220">步骤 3 - 卸载 .NET Core SDK 和运行时</span><span class="sxs-lookup"><span data-stu-id="f4bff-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="f4bff-221">`dotnet-core-uninstall remove` 卸载由选项集合指定的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="f4bff-222">该工具不能用于卸载版本 5.0 或更高版本的 SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="f4bff-223">由于此工具具有破坏性行为，因此强烈建议在运行 remove 命令之前执行试运行。</span><span class="sxs-lookup"><span data-stu-id="f4bff-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="f4bff-224">使用 `remove` 命令时，试运行将显示要删除的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="f4bff-225">请参阅[是否应删除版本？](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version)了解哪些 SDK 和运行时可以安全删除。</span><span class="sxs-lookup"><span data-stu-id="f4bff-225">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="f4bff-226">请记住以下注意事项：</span><span class="sxs-lookup"><span data-stu-id="f4bff-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="f4bff-227">此工具可以卸载计算机上 `global.json` 文件所需的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="f4bff-228">可以从[下载 .NET Core](https://dotnet.microsoft.com/download/dotnet-core) 页面重新安装 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="f4bff-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="f4bff-229">此工具可以卸载计算机上依赖于框架的应用程序所需的 .NET Core 运行时版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="f4bff-230">可以从[下载 .NET Core](https://dotnet.microsoft.com/download/dotnet-core) 页面重新安装 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="f4bff-231">此工具可以卸载 Visual Studio 所依赖的 .NET Core SDK 和运行时版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="f4bff-232">如果中断 Visual Studio 安装，请在 Visual Studio 安装程序中运行“修复”以返回到工作状态。</span><span class="sxs-lookup"><span data-stu-id="f4bff-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="f4bff-233">默认情况下，所有命令都将保留 Visual Studio 或其他 SDK 可能需要的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="f4bff-234">可以通过将这些 SDK 和运行时显式列出为参数或使用 `--force` 选项来卸载这些 SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="f4bff-235">此工具需要提升才能卸载 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="f4bff-236">在 Windows 上的管理员命令提示符中运行此工具，在 macOS 上则通过 `sudo` 运行。</span><span class="sxs-lookup"><span data-stu-id="f4bff-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="f4bff-237">`dry-run` 和 `whatif` 命令不需要提升。</span><span class="sxs-lookup"><span data-stu-id="f4bff-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="f4bff-238">**dotnet-core-uninstall remove**</span><span class="sxs-lookup"><span data-stu-id="f4bff-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="f4bff-239">摘要</span><span class="sxs-lookup"><span data-stu-id="f4bff-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="f4bff-240">自变量</span><span class="sxs-lookup"><span data-stu-id="f4bff-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="f4bff-241">要卸载的指定版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-241">The specified version to uninstall.</span></span> <span data-ttu-id="f4bff-242">可以逐一列出多个版本，用空格分隔。</span><span class="sxs-lookup"><span data-stu-id="f4bff-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="f4bff-243">此外还支持响应文件。</span><span class="sxs-lookup"><span data-stu-id="f4bff-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="f4bff-244">响应文件是在命令行上放置所有版本的替代方法。</span><span class="sxs-lookup"><span data-stu-id="f4bff-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="f4bff-245">它们是文本文件，通常具有 \*.rsp 扩展名，每个版本都在单独的行上列出。</span><span class="sxs-lookup"><span data-stu-id="f4bff-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="f4bff-246">若要为 `VERSION` 参数指定响应文件，请使用后面紧跟响应文件名的 \@ 字符。</span><span class="sxs-lookup"><span data-stu-id="f4bff-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="f4bff-247">选项</span><span class="sxs-lookup"><span data-stu-id="f4bff-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="f4bff-248">Windows</span><span class="sxs-lookup"><span data-stu-id="f4bff-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="f4bff-249">删除所有 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="f4bff-250">仅删除版本小于指定版本的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="f4bff-251">仍安装指定版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="f4bff-252">除了那些指定版本外，删除所有 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="f4bff-253">删除 .NET Core SDK 和运行时（最高版本除外）。</span><span class="sxs-lookup"><span data-stu-id="f4bff-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="f4bff-254">删除由较高版本的修补程序取代的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="f4bff-255">此选项保护 global.json。</span><span class="sxs-lookup"><span data-stu-id="f4bff-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="f4bff-256">删除标记为预览的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="f4bff-257">删除标记为预览的 .NET Core SDK 和运行时（最高预览版除外）。</span><span class="sxs-lookup"><span data-stu-id="f4bff-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="f4bff-258">仅删除 ASP.NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="f4bff-259">仅删除 .NET Core 托管绑定。</span><span class="sxs-lookup"><span data-stu-id="f4bff-259">Removes .NET Core hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="f4bff-260">删除与指定 `major.minor` 版本相匹配的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="f4bff-261">仅删除 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="f4bff-262">仅删除 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="f4bff-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="f4bff-263">设置详细程度。</span><span class="sxs-lookup"><span data-stu-id="f4bff-263">Sets the verbosity level.</span></span> <span data-ttu-id="f4bff-264">允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f4bff-265">默认值为 `normal`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="f4bff-266">必须与 `--sdk`、`--runtime` 和 `--aspnet-runtime` 结合使用才能删除 x64 SDK 或运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="f4bff-267">必须与 `--sdk`、`--runtime` 和 `--aspnet-runtime` 结合使用才能删除 x86 SDK 或运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="f4bff-268">`-y, --yes` 执行命令而不需要进行是或否确认。</span><span class="sxs-lookup"><span data-stu-id="f4bff-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="f4bff-269">`--force` 强制删除可能由 Visual Studio 使用的版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="f4bff-270">注意：</span><span class="sxs-lookup"><span data-stu-id="f4bff-270">Notes:</span></span>

1. <span data-ttu-id="f4bff-271">只需 `--sdk`、`--runtime`、`--aspnet-runtime` 和 `--hosting-bundle` 中的一个。</span><span class="sxs-lookup"><span data-stu-id="f4bff-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="f4bff-272">`--all`、`--all-below`、`--all-but`、`--all-but-latest`、`--all-lower-patches`、`--all-previews`、`--all-previews-but-latest`、`--major-minor` 和 `[<VERSION>...]` 除外。</span><span class="sxs-lookup"><span data-stu-id="f4bff-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="f4bff-273">如果未指定 `--x64` 或 `--x86`，则同时删除 x64 和 x86。</span><span class="sxs-lookup"><span data-stu-id="f4bff-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="f4bff-274">macOS</span><span class="sxs-lookup"><span data-stu-id="f4bff-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="f4bff-275">删除所有 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="f4bff-276">删除低于指定版本的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="f4bff-277">将保留指定的版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="f4bff-278">删除 .NET Core SDK 和运行时（指定版本除外）。</span><span class="sxs-lookup"><span data-stu-id="f4bff-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="f4bff-279">删除 .NET Core SDK 和运行时（最高版本除外）。</span><span class="sxs-lookup"><span data-stu-id="f4bff-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="f4bff-280">删除由较高版本的修补程序取代的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="f4bff-281">此选项保护 global.json。</span><span class="sxs-lookup"><span data-stu-id="f4bff-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="f4bff-282">删除标记为预览的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="f4bff-283">删除标记为预览的 .NET Core SDK 和运行时（最高预览版除外）。</span><span class="sxs-lookup"><span data-stu-id="f4bff-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="f4bff-284">删除与指定 `major.minor` 版本相匹配的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="f4bff-285">仅删除 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="f4bff-286">仅删除 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="f4bff-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="f4bff-287">设置详细程度。</span><span class="sxs-lookup"><span data-stu-id="f4bff-287">Sets the verbosity level.</span></span> <span data-ttu-id="f4bff-288">允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f4bff-289">默认值为 `normal`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-289">The default value is `normal`.</span></span>

* <span data-ttu-id="f4bff-290">`-y, --yes` 执行命令而不需要进行 Y/N 确认。</span><span class="sxs-lookup"><span data-stu-id="f4bff-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="f4bff-291">`--force` 强制删除可能由 Visual Studio 或 SDK 使用的版本。</span><span class="sxs-lookup"><span data-stu-id="f4bff-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="f4bff-292">注意：</span><span class="sxs-lookup"><span data-stu-id="f4bff-292">Notes:</span></span>

1. <span data-ttu-id="f4bff-293">只需 `--sdk` 和 `--runtime` 中的一个。</span><span class="sxs-lookup"><span data-stu-id="f4bff-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="f4bff-294">`--all`、`--all-below`、`--all-but`、`--all-but-latest`、`--all-lower-patches`、`--all-previews`、`--all-previews-but-latest`、`--major-minor` 和 `[<VERSION>...]` 除外。</span><span class="sxs-lookup"><span data-stu-id="f4bff-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="f4bff-295">示例</span><span class="sxs-lookup"><span data-stu-id="f4bff-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="f4bff-296">默认情况下，将保留 Visual Studio 或其他 SDK 可能需要的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="f4bff-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="f4bff-297">在下面的示例中，可能保留某些指定的 SDK 和运行时，具体取决于计算机的状态。</span><span class="sxs-lookup"><span data-stu-id="f4bff-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="f4bff-298">若要删除所有 SDK 和运行时，请将它们显式列出为参数或使用 `--force` 选项。</span><span class="sxs-lookup"><span data-stu-id="f4bff-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="f4bff-299">删除除版本 `3.0.0-preview6-27804-01` 之外的所有 .NET Core 运行时，无需进行 Y/N 确认：</span><span class="sxs-lookup"><span data-stu-id="f4bff-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="f4bff-300">删除所有 .NET Core 1.1 SDK，无需进行 Y/N 确认：</span><span class="sxs-lookup"><span data-stu-id="f4bff-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="f4bff-301">删除没有控制台输出的 .NET Core 1.1.11 SDK：</span><span class="sxs-lookup"><span data-stu-id="f4bff-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="f4bff-302">删除可由此工具安全删除的所有 .NET Core SDK：</span><span class="sxs-lookup"><span data-stu-id="f4bff-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="f4bff-303">删除此工具可删除的所有 .NET Core SDK，包括 Visual Studio 可能需要的 SDK（不推荐）：</span><span class="sxs-lookup"><span data-stu-id="f4bff-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="f4bff-304">删除响应文件 `versions.rsp` 中指定的所有 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="f4bff-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="f4bff-305">versions.rsp 的内容如下所示：</span><span class="sxs-lookup"><span data-stu-id="f4bff-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="f4bff-306">步骤 4 - 删除 NuGet 回退文件夹（可选）</span><span class="sxs-lookup"><span data-stu-id="f4bff-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="f4bff-307">在某些情况下，你不再需要 `NuGetFallbackFolder`，可能希望将其删除。</span><span class="sxs-lookup"><span data-stu-id="f4bff-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="f4bff-308">有关删除此文件夹的详细信息，请参阅[删除 NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder)。</span><span class="sxs-lookup"><span data-stu-id="f4bff-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="f4bff-309">卸载工具</span><span class="sxs-lookup"><span data-stu-id="f4bff-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="f4bff-310">Windows</span><span class="sxs-lookup"><span data-stu-id="f4bff-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="f4bff-311">打开“添加或删除程序”。</span><span class="sxs-lookup"><span data-stu-id="f4bff-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="f4bff-312">搜索 `Microsoft .NET Core SDK Uninstall Tool`。</span><span class="sxs-lookup"><span data-stu-id="f4bff-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="f4bff-313">选择“卸载”。</span><span class="sxs-lookup"><span data-stu-id="f4bff-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="f4bff-314">macOS</span><span class="sxs-lookup"><span data-stu-id="f4bff-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="f4bff-315">从安装目录中删除已下载的 dotnet-core-uninstall.tar.gz 文件。</span><span class="sxs-lookup"><span data-stu-id="f4bff-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="f4bff-316">如果将此文件的内容解压缩到其他目录中，请务必同时删除该内容。</span><span class="sxs-lookup"><span data-stu-id="f4bff-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
