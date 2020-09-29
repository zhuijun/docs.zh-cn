---
title: dotnet-install 脚本
description: 了解用于安装 .NET Core SDK 和共享运行时的 dotnet-install 脚本。
ms.date: 09/22/2020
ms.openlocfilehash: 35161edd2a4862e064373d75f1e19396983f3a64
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078198"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="81de5-103">dotnet-install 脚本引用</span><span class="sxs-lookup"><span data-stu-id="81de5-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="81de5-104">“属性”</span><span class="sxs-lookup"><span data-stu-id="81de5-104">Name</span></span>

<span data-ttu-id="81de5-105">`dotnet-install.ps1` | `dotnet-install.sh` - 用于安装 .NET Core SDK 和共享运行时的脚本。</span><span class="sxs-lookup"><span data-stu-id="81de5-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="81de5-106">摘要</span><span class="sxs-lookup"><span data-stu-id="81de5-106">Synopsis</span></span>

<span data-ttu-id="81de5-107">Windows：</span><span class="sxs-lookup"><span data-stu-id="81de5-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress] [-ProxyBypassList <LIST_OF_URLS>]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

Get-Help ./dotnet-install.ps1
```

<span data-ttu-id="81de5-108">Linux/macOS：</span><span class="sxs-lookup"><span data-stu-id="81de5-108">Linux/macOS:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

<span data-ttu-id="81de5-109">bash 脚本也读取 PowerShell 开关。因此，可以在 Linux/macOS 系统上将 PowerShell 开关与脚本结合使用。</span><span class="sxs-lookup"><span data-stu-id="81de5-109">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

## <a name="description"></a><span data-ttu-id="81de5-110">描述</span><span class="sxs-lookup"><span data-stu-id="81de5-110">Description</span></span>

<span data-ttu-id="81de5-111">`dotnet-install` 脚本执行 .NET Core SDK 的非管理员安装，其中包含 .NET Core CLI 和共享运行时。</span><span class="sxs-lookup"><span data-stu-id="81de5-111">The `dotnet-install` scripts perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span> <span data-ttu-id="81de5-112">有两个脚本：</span><span class="sxs-lookup"><span data-stu-id="81de5-112">There are two scripts:</span></span>

* <span data-ttu-id="81de5-113">在 Windows 上运行的 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="81de5-113">A PowerShell script that works on Windows.</span></span>
* <span data-ttu-id="81de5-114">在 Linux/macOS 上运行的 bash 脚本。</span><span class="sxs-lookup"><span data-stu-id="81de5-114">A bash script that works on Linux/macOS.</span></span>

### <a name="purpose"></a><span data-ttu-id="81de5-115">目标</span><span class="sxs-lookup"><span data-stu-id="81de5-115">Purpose</span></span>

 <span data-ttu-id="81de5-116">脚本的预期用途是用于持续集成 (CI) 方案，其中：</span><span class="sxs-lookup"><span data-stu-id="81de5-116">The intended use of the scripts is for Continuous Integration (CI) scenarios, where:</span></span>

* <span data-ttu-id="81de5-117">需要在无需用户交互和管理员权限的情况下安装 SDK。</span><span class="sxs-lookup"><span data-stu-id="81de5-117">The SDK needs to be installed without user interaction and without admin rights.</span></span>
* <span data-ttu-id="81de5-118">无需在多个 CI 运行中保留 SDK 安装。</span><span class="sxs-lookup"><span data-stu-id="81de5-118">The SDK installation doesn't need to persist across multiple CI runs.</span></span>

  <span data-ttu-id="81de5-119">典型的事件序列：</span><span class="sxs-lookup"><span data-stu-id="81de5-119">The typical sequence of events:</span></span>
  * <span data-ttu-id="81de5-120">触发 CI。</span><span class="sxs-lookup"><span data-stu-id="81de5-120">CI is triggered.</span></span>
  * <span data-ttu-id="81de5-121">CI 使用其中一个脚本安装 SDK。</span><span class="sxs-lookup"><span data-stu-id="81de5-121">CI installs the SDK using one of these scripts.</span></span>
  * <span data-ttu-id="81de5-122">CI 完成其工作并清除临时数据（包括 SDK 安装）。</span><span class="sxs-lookup"><span data-stu-id="81de5-122">CI finishes its work and clears temporary data including the SDK installation.</span></span>

<span data-ttu-id="81de5-123">要设置开发环境或运行应用，请使用安装程序而不是这些脚本。</span><span class="sxs-lookup"><span data-stu-id="81de5-123">To set up a development environment or to run apps, use the installers rather than these scripts.</span></span>

### <a name="recommended-version"></a><span data-ttu-id="81de5-124">建议的版本</span><span class="sxs-lookup"><span data-stu-id="81de5-124">Recommended version</span></span>

<span data-ttu-id="81de5-125">建议使用脚本的稳定版本：</span><span class="sxs-lookup"><span data-stu-id="81de5-125">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="81de5-126">Bash (Linux/macOS)：<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="81de5-126">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="81de5-127">PowerShell (Windows)：<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="81de5-127">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

### <a name="script-behavior"></a><span data-ttu-id="81de5-128">脚本行为</span><span class="sxs-lookup"><span data-stu-id="81de5-128">Script behavior</span></span>

<span data-ttu-id="81de5-129">这两个脚本的行为相同。</span><span class="sxs-lookup"><span data-stu-id="81de5-129">Both scripts have the same behavior.</span></span> <span data-ttu-id="81de5-130">它们从 CLI 生成放置下载 ZIP/tarball 文件，并将其安装在默认位置或 `-InstallDir|--install-dir` 所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="81de5-130">They download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span>

<span data-ttu-id="81de5-131">默认情况下，安装脚本下载 SDK 并安装它。</span><span class="sxs-lookup"><span data-stu-id="81de5-131">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="81de5-132">如果只想获取共享的运行时，请指定 `-Runtime|--runtime` 参数。</span><span class="sxs-lookup"><span data-stu-id="81de5-132">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="81de5-133">默认情况下，该脚本会将安装位置添加到当前会话的 $PATH。</span><span class="sxs-lookup"><span data-stu-id="81de5-133">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="81de5-134">通过指定 `-NoPath|--no-path` 参数覆盖此默认行为。</span><span class="sxs-lookup"><span data-stu-id="81de5-134">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span> <span data-ttu-id="81de5-135">脚本未设置 `DOTNET_ROOT` 环境变量。</span><span class="sxs-lookup"><span data-stu-id="81de5-135">The script doesn't set the `DOTNET_ROOT` environment variable.</span></span>

<span data-ttu-id="81de5-136">运行脚本前，请安装所需的[依赖项](../install/windows.md#dependencies)。</span><span class="sxs-lookup"><span data-stu-id="81de5-136">Before running the script, install the required [dependencies](../install/windows.md#dependencies).</span></span>

<span data-ttu-id="81de5-137">可以使用 `-Version|--version` 参数安装特定版本。</span><span class="sxs-lookup"><span data-stu-id="81de5-137">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="81de5-138">必须将版本指定为由 3 部分构成的版本号，例如 `2.1.0`。</span><span class="sxs-lookup"><span data-stu-id="81de5-138">The version must be specified as a three-part version number, such as `2.1.0`.</span></span> <span data-ttu-id="81de5-139">如果未指定版本，则脚本将安装 `latest` 版本。</span><span class="sxs-lookup"><span data-stu-id="81de5-139">If the version isn't specified, the script installs the `latest` version.</span></span>

<span data-ttu-id="81de5-140">安装脚本不会更新 Windows 上的注册表。</span><span class="sxs-lookup"><span data-stu-id="81de5-140">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="81de5-141">它们只是下载压缩的二进制文件并将其复制到文件夹。</span><span class="sxs-lookup"><span data-stu-id="81de5-141">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="81de5-142">如果要更新注册表项值，请使用 .NET Core 安装程序。</span><span class="sxs-lookup"><span data-stu-id="81de5-142">If you want registry key values to be updated, use the .NET Core installers.</span></span>

## <a name="options"></a><span data-ttu-id="81de5-143">选项</span><span class="sxs-lookup"><span data-stu-id="81de5-143">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="81de5-144">要安装的 .NET Core 二进制文件的体系结构。</span><span class="sxs-lookup"><span data-stu-id="81de5-144">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="81de5-145">可能值为 `<auto>`、`amd64`、`x64`、`x86`、`arm64` 以及 `arm`。</span><span class="sxs-lookup"><span data-stu-id="81de5-145">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="81de5-146">默认值为 `<auto>`，它表示当前正在运行的操作系统体系结构。</span><span class="sxs-lookup"><span data-stu-id="81de5-146">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="81de5-147">指定此安装程序的 Azure 源的 URL。</span><span class="sxs-lookup"><span data-stu-id="81de5-147">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="81de5-148">建议不要更改该值。</span><span class="sxs-lookup"><span data-stu-id="81de5-148">We recommended that you don't change this value.</span></span> <span data-ttu-id="81de5-149">默认值为 `https://dotnetcli.azureedge.net/dotnet`。</span><span class="sxs-lookup"><span data-stu-id="81de5-149">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="81de5-150">指定安装的源通道。</span><span class="sxs-lookup"><span data-stu-id="81de5-150">Specifies the source channel for the installation.</span></span> <span data-ttu-id="81de5-151">可能的值为：</span><span class="sxs-lookup"><span data-stu-id="81de5-151">The possible values are:</span></span>

  - <span data-ttu-id="81de5-152">`Current` - 最新版本。</span><span class="sxs-lookup"><span data-stu-id="81de5-152">`Current` - Most current release.</span></span>
  - <span data-ttu-id="81de5-153">`LTS` - 长期支持频道（最新受支持版本）。</span><span class="sxs-lookup"><span data-stu-id="81de5-153">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="81de5-154">表示特定版本的由两部分构成的 X.Y 格式的版本（例如 `2.1` 或 `3.0`）。</span><span class="sxs-lookup"><span data-stu-id="81de5-154">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="81de5-155">分支名称：例如 `release/3.1.1xx` 或 `master`（适用于每日测试版本）。</span><span class="sxs-lookup"><span data-stu-id="81de5-155">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="81de5-156">使用此选项可以从预览通道安装版本。</span><span class="sxs-lookup"><span data-stu-id="81de5-156">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="81de5-157">使用[安装程序和二进制文件](https://github.com/dotnet/core-sdk#installers-and-binaries)中列出的通道名称。</span><span class="sxs-lookup"><span data-stu-id="81de5-157">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="81de5-158">默认值为 `LTS`。</span><span class="sxs-lookup"><span data-stu-id="81de5-158">The default value is `LTS`.</span></span> <span data-ttu-id="81de5-159">有关 .NET 支持频道的详细信息，请参阅 [.NET 支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)页。</span><span class="sxs-lookup"><span data-stu-id="81de5-159">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="81de5-160">如果设置，脚本将不会执行安装。</span><span class="sxs-lookup"><span data-stu-id="81de5-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="81de5-161">而会显示要使用哪个命令行来持续安装当前请求的 .NET Core CLI 版本。</span><span class="sxs-lookup"><span data-stu-id="81de5-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="81de5-162">例如，如果指定版本 `latest`，它将显示特定版本的链接，以便可在生成脚本中明确地使用此命令。</span><span class="sxs-lookup"><span data-stu-id="81de5-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="81de5-163">如果想要自行安装或下载，它还会显示二进制文件位置。</span><span class="sxs-lookup"><span data-stu-id="81de5-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="81de5-164">用作追加到 Azure 源的查询字符串。</span><span class="sxs-lookup"><span data-stu-id="81de5-164">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="81de5-165">这允许更改 URL 以使用非公共 blob 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="81de5-165">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--help`**

  <span data-ttu-id="81de5-166">打印脚本帮助。</span><span class="sxs-lookup"><span data-stu-id="81de5-166">Prints out help for the script.</span></span> <span data-ttu-id="81de5-167">仅适用于 bash 脚本。</span><span class="sxs-lookup"><span data-stu-id="81de5-167">Applies only to bash script.</span></span> <span data-ttu-id="81de5-168">对于 PowerShell，请使用 `Get-Help ./dotnet-install.ps1`。</span><span class="sxs-lookup"><span data-stu-id="81de5-168">For PowerShell, use `Get-Help ./dotnet-install.ps1`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="81de5-169">指定安装路径。</span><span class="sxs-lookup"><span data-stu-id="81de5-169">Specifies the installation path.</span></span> <span data-ttu-id="81de5-170">如果不存在，则会创建该目录。</span><span class="sxs-lookup"><span data-stu-id="81de5-170">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="81de5-171">默认值为“%LocalAppData%\Microsoft\dotnet”（在 Windows 上）和“/usr/share/dotnet”（在 Linux/macOS 上）。</span><span class="sxs-lookup"><span data-stu-id="81de5-171">The default value is *%LocalAppData%\Microsoft\dotnet* on Windows and */usr/share/dotnet* on Linux/macOS.</span></span> <span data-ttu-id="81de5-172">会将二进制文件直接放入目录中。</span><span class="sxs-lookup"><span data-stu-id="81de5-172">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="81de5-173">指定将用于确定 SDK 版本的 [global.json](global-json.md) 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="81de5-173">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="81de5-174">global.json 文件必须具有 `sdk:version` 的值。</span><span class="sxs-lookup"><span data-stu-id="81de5-174">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="81de5-175">禁止从 [Azure 内容分发网络 (CDN)](/azure/cdn/cdn-overview) 进行下载，并直接使用未缓存源。</span><span class="sxs-lookup"><span data-stu-id="81de5-175">Disables downloading from the [Azure Content Delivery Network (CDN)](/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="81de5-176">如果设定，不会将安装文件夹导出到当前会话的路径。</span><span class="sxs-lookup"><span data-stu-id="81de5-176">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="81de5-177">默认情况下，该脚本会修改 PATH，这会使 .NET Core CLI 在安装后立即可用。</span><span class="sxs-lookup"><span data-stu-id="81de5-177">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="81de5-178">如果设置，安装程序发出 Web 请求时将使用该代理。</span><span class="sxs-lookup"><span data-stu-id="81de5-178">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="81de5-179">（仅适用于 Windows。）</span><span class="sxs-lookup"><span data-stu-id="81de5-179">(Only valid for Windows.)</span></span>

- **`-ProxyBypassList <LIST_OF_URLS>`**

  <span data-ttu-id="81de5-180">如果设置了 `ProxyAddress`，它会提供一个以逗号分隔的 URL 列表，表中的 URL 将绕过代理。</span><span class="sxs-lookup"><span data-stu-id="81de5-180">If set with `ProxyAddress`, provides a list of comma-separated urls that will bypass the proxy.</span></span> <span data-ttu-id="81de5-181">（仅适用于 Windows。）</span><span class="sxs-lookup"><span data-stu-id="81de5-181">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="81de5-182">如果设置，在使用代理地址时，安装程序会使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="81de5-182">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="81de5-183">（仅适用于 Windows。）</span><span class="sxs-lookup"><span data-stu-id="81de5-183">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="81de5-184">仅安装共享运行时，而非整个 SDK。</span><span class="sxs-lookup"><span data-stu-id="81de5-184">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="81de5-185">可能的值为：</span><span class="sxs-lookup"><span data-stu-id="81de5-185">The possible values are:</span></span>

  - <span data-ttu-id="81de5-186">`dotnet` - `Microsoft.NETCore.App` 共享运行时。</span><span class="sxs-lookup"><span data-stu-id="81de5-186">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="81de5-187">`aspnetcore` - `Microsoft.AspNetCore.App` 共享运行时。</span><span class="sxs-lookup"><span data-stu-id="81de5-187">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="81de5-188">`windowsdesktop` - `Microsoft.WindowsDesktop.App` 共享运行时。</span><span class="sxs-lookup"><span data-stu-id="81de5-188">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="81de5-189">指定要为其安装工具的[运行时标识符](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="81de5-189">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="81de5-190">使用适用于可移植 Linux 的 `linux-x64`。</span><span class="sxs-lookup"><span data-stu-id="81de5-190">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="81de5-191">（仅适用于 Linux/macOS。）</span><span class="sxs-lookup"><span data-stu-id="81de5-191">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="81de5-192">此参数已过时，可能会在将来版本的脚本中删除。</span><span class="sxs-lookup"><span data-stu-id="81de5-192">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="81de5-193">建议的替代项为 `-Runtime|--runtime` 选项。</span><span class="sxs-lookup"><span data-stu-id="81de5-193">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="81de5-194">仅安装共享运行时位，而非整个 SDK。</span><span class="sxs-lookup"><span data-stu-id="81de5-194">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="81de5-195">此选项等效于指定 `-Runtime|--runtime dotnet`。</span><span class="sxs-lookup"><span data-stu-id="81de5-195">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="81de5-196">跳过安装未添加版本的文件，例如 dotnet.exe（如果它们已经存在）。</span><span class="sxs-lookup"><span data-stu-id="81de5-196">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="81de5-197">允许更改此安装程序使用的未缓存源的 URL。</span><span class="sxs-lookup"><span data-stu-id="81de5-197">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="81de5-198">建议不要更改该值。</span><span class="sxs-lookup"><span data-stu-id="81de5-198">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="81de5-199">显示诊断信息。</span><span class="sxs-lookup"><span data-stu-id="81de5-199">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="81de5-200">表示特定的内部版本。</span><span class="sxs-lookup"><span data-stu-id="81de5-200">Represents a specific build version.</span></span> <span data-ttu-id="81de5-201">可能的值为：</span><span class="sxs-lookup"><span data-stu-id="81de5-201">The possible values are:</span></span>

  - <span data-ttu-id="81de5-202">`latest` - 频道上的最新内部版本（与 `-Channel` 选项结合使用）。</span><span class="sxs-lookup"><span data-stu-id="81de5-202">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="81de5-203">由三部分组成的版本，采用 X.Y.Z 格式，表示特定的内部版本；取代 `-Channel` 选项。</span><span class="sxs-lookup"><span data-stu-id="81de5-203">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="81de5-204">例如：`2.0.0-preview2-006120`。</span><span class="sxs-lookup"><span data-stu-id="81de5-204">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="81de5-205">如果没有指定，`-Version` 默认值为 `latest`。</span><span class="sxs-lookup"><span data-stu-id="81de5-205">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="81de5-206">示例</span><span class="sxs-lookup"><span data-stu-id="81de5-206">Examples</span></span>

- <span data-ttu-id="81de5-207">将最新的长期支持 (LTS) 版本安装到默认位置：</span><span class="sxs-lookup"><span data-stu-id="81de5-207">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="81de5-208">Windows：</span><span class="sxs-lookup"><span data-stu-id="81de5-208">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="81de5-209">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="81de5-209">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="81de5-210">将 3.1 通道中的最新版本安装到指定位置：</span><span class="sxs-lookup"><span data-stu-id="81de5-210">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="81de5-211">Windows：</span><span class="sxs-lookup"><span data-stu-id="81de5-211">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="81de5-212">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="81de5-212">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="81de5-213">安装 3.0.0 版共享运行时：</span><span class="sxs-lookup"><span data-stu-id="81de5-213">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="81de5-214">Windows：</span><span class="sxs-lookup"><span data-stu-id="81de5-214">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="81de5-215">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="81de5-215">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="81de5-216">获取脚本并在公司代理后面安装 2.1.2 版本（仅限 Windows）：</span><span class="sxs-lookup"><span data-stu-id="81de5-216">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="81de5-217">获取脚本并安装 .NET Core CLI 单行式命令示例：</span><span class="sxs-lookup"><span data-stu-id="81de5-217">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="81de5-218">Windows：</span><span class="sxs-lookup"><span data-stu-id="81de5-218">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="81de5-219">macOS/Linux：</span><span class="sxs-lookup"><span data-stu-id="81de5-219">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="81de5-220">请参阅</span><span class="sxs-lookup"><span data-stu-id="81de5-220">See also</span></span>

- [<span data-ttu-id="81de5-221">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="81de5-221">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="81de5-222">.NET Core 运行时和 SDK 下载存档</span><span class="sxs-lookup"><span data-stu-id="81de5-222">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
