---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602686"
---

[<span data-ttu-id="e0e36-101">.NET Core 可以从 Snap Store 中获取。</span><span class="sxs-lookup"><span data-stu-id="e0e36-101">.NET Core is available from the Snap Store.</span></span>](https://snapcraft.io/dotnet-sdk)

<span data-ttu-id="e0e36-102">Snap 是应用及其依赖项的捆绑包，无需修改即可在多个不同的 Linux 发行版中正常运行。</span><span class="sxs-lookup"><span data-stu-id="e0e36-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="e0e36-103">可以从 Snap Store 中发现和安装 Snap。</span><span class="sxs-lookup"><span data-stu-id="e0e36-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="e0e36-104">若要详细了解 Snap，请参阅[开始使用 Snap](https://snapcraft.io/docs/getting-started)。</span><span class="sxs-lookup"><span data-stu-id="e0e36-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="e0e36-105">只有受支持的 .NET Core 版本，才能通过 Snap 获取。</span><span class="sxs-lookup"><span data-stu-id="e0e36-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="e0e36-106">安装 SDK</span><span class="sxs-lookup"><span data-stu-id="e0e36-106">Install the SDK</span></span>

<span data-ttu-id="e0e36-107">适用于 .NET Core SDK 的 Snap 包都是在同一标识符（即 `dotnet-sdk`）下发布的。</span><span class="sxs-lookup"><span data-stu-id="e0e36-107">Snap packages for .NET Core SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="e0e36-108">可以通过指定通道来安装特定版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="e0e36-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="e0e36-109">SDK 包括相应的运行时。</span><span class="sxs-lookup"><span data-stu-id="e0e36-109">The SDK includes the coresponding runtime.</span></span> <span data-ttu-id="e0e36-110">下表列出了通道：</span><span class="sxs-lookup"><span data-stu-id="e0e36-110">The following table list the channels:</span></span>

| <span data-ttu-id="e0e36-111">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="e0e36-111">.NET Core version</span></span> | <span data-ttu-id="e0e36-112">Snap 包</span><span class="sxs-lookup"><span data-stu-id="e0e36-112">Snap package</span></span>             |
|-------------------|--------------------------|
| <span data-ttu-id="e0e36-113">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="e0e36-113">3.1 (LTS)</span></span>         | <span data-ttu-id="e0e36-114">`3.1` 或 `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="e0e36-114">`3.1` or `latest/stable`</span></span> |
| <span data-ttu-id="e0e36-115">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="e0e36-115">2.1 (LTS)</span></span>         | `2.1`                    |
| <span data-ttu-id="e0e36-116">.NET 5.0（预览）</span><span class="sxs-lookup"><span data-stu-id="e0e36-116">.NET 5.0 preview</span></span>  | `5.0/beta`               |

<span data-ttu-id="e0e36-117">若要安装适用于 .NET Core SDK 的 Snap 包，请运行 `snap install` 命令。</span><span class="sxs-lookup"><span data-stu-id="e0e36-117">Use the `snap install` command to install a .NET Core SDK snap package.</span></span> <span data-ttu-id="e0e36-118">使用 `--channel` 参数来指明要安装哪个版本。</span><span class="sxs-lookup"><span data-stu-id="e0e36-118">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="e0e36-119">如果省略此参数，则使用 `latest/stable`。</span><span class="sxs-lookup"><span data-stu-id="e0e36-119">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="e0e36-120">在下面的示例中，指定的是 `3.1`：</span><span class="sxs-lookup"><span data-stu-id="e0e36-120">In this example, `3.1` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

<span data-ttu-id="e0e36-121">接下来，使用 `snap alias` 命令为系统注册 `dotnet` 命令：</span><span class="sxs-lookup"><span data-stu-id="e0e36-121">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="e0e36-122">此命令的格式为 `sudo snap alias {package}.{command} {alias}`。</span><span class="sxs-lookup"><span data-stu-id="e0e36-122">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="e0e36-123">可以选择所需的任何 `{alias}` 名称。</span><span class="sxs-lookup"><span data-stu-id="e0e36-123">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="e0e36-124">例如，可以根据 Snap 安装的特定版本来命名此命令：`sudo snap alias dotnet-sdk.dotnet dotnet31`。</span><span class="sxs-lookup"><span data-stu-id="e0e36-124">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet31`.</span></span> <span data-ttu-id="e0e36-125">运行命令 `dotnet31` 时，将调用这一特定版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="e0e36-125">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="e0e36-126">但这与大多数教程和示例不兼容，因为它们需要使用 `dotnet` 命令。</span><span class="sxs-lookup"><span data-stu-id="e0e36-126">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="e0e36-127">安装运行时</span><span class="sxs-lookup"><span data-stu-id="e0e36-127">Install the runtime</span></span>

<span data-ttu-id="e0e36-128">适用于 .NET Core Runtime 的 Snap 包都是在各自的包标识符下发布的。</span><span class="sxs-lookup"><span data-stu-id="e0e36-128">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="e0e36-129">下表列出了这些包标识符：</span><span class="sxs-lookup"><span data-stu-id="e0e36-129">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="e0e36-130">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="e0e36-130">.NET Core version</span></span> | <span data-ttu-id="e0e36-131">Snap 包</span><span class="sxs-lookup"><span data-stu-id="e0e36-131">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="e0e36-132">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="e0e36-132">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="e0e36-133">3.0</span><span class="sxs-lookup"><span data-stu-id="e0e36-133">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="e0e36-134">2.2</span><span class="sxs-lookup"><span data-stu-id="e0e36-134">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="e0e36-135">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="e0e36-135">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="e0e36-136">若要安装适用于 .NET Core Runtime 的 Snap 包，请运行 `snap install` 命令。</span><span class="sxs-lookup"><span data-stu-id="e0e36-136">Use the `snap install` command to install a .NET Core Runtime snap package.</span></span> <span data-ttu-id="e0e36-137">在下面的示例中，安装的是 .NET Core 3.1：</span><span class="sxs-lookup"><span data-stu-id="e0e36-137">In this example, .NET Core 3.1 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-31 --classic
```

<span data-ttu-id="e0e36-138">接下来，使用 `snap alias` 命令为系统注册 `dotnet` 命令：</span><span class="sxs-lookup"><span data-stu-id="e0e36-138">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

<span data-ttu-id="e0e36-139">此命令的格式为 `sudo snap alias {package}.{command} {alias}`。</span><span class="sxs-lookup"><span data-stu-id="e0e36-139">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="e0e36-140">可以选择所需的任何 `{alias}` 名称。</span><span class="sxs-lookup"><span data-stu-id="e0e36-140">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="e0e36-141">例如，可以根据 Snap 安装的特定版本来命名此命令：`sudo snap alias dotnet-runtime-31.dotnet dotnet31`。</span><span class="sxs-lookup"><span data-stu-id="e0e36-141">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-31.dotnet dotnet31`.</span></span> <span data-ttu-id="e0e36-142">运行命令 `dotnet31` 时，将调用这一特定版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="e0e36-142">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="e0e36-143">但这与大多数教程和示例不兼容，因为它们需要使用 `dotnet` 命令。</span><span class="sxs-lookup"><span data-stu-id="e0e36-143">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="e0e36-144">SSL 证书错误</span><span class="sxs-lookup"><span data-stu-id="e0e36-144">SSL Certificate errors</span></span>

<span data-ttu-id="e0e36-145">通过 Snap 安装 .NET 后，可能会在某些发行版上找不到 .NET SSL 证书，并且可能会在 `restore` 期间看到如下错误：</span><span class="sxs-lookup"><span data-stu-id="e0e36-145">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="e0e36-146">若要解决此问题，请设置一些环境变量：</span><span class="sxs-lookup"><span data-stu-id="e0e36-146">To resolve this issue, set a few enviornment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="e0e36-147">证书位置因发行版而异。</span><span class="sxs-lookup"><span data-stu-id="e0e36-147">The certificate location will vary by distro.</span></span> <span data-ttu-id="e0e36-148">下面是我们在发行版中遇到此问题的位置。</span><span class="sxs-lookup"><span data-stu-id="e0e36-148">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="e0e36-149">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="e0e36-149">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="e0e36-150">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="e0e36-150">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="e0e36-151">Solus - `/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="e0e36-151">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>
