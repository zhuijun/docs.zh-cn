---
title: 检查 Windows、Linux 和 macOS 上安装的 .NET Core 版本 - .NET Core
description: 了解如何列出计算机上安装的 .NET Core 版本。 这包括 .NET Core 运行时和 SDK。
author: adegeo
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: cc4d9c6a366cd0e5da4c3446536c93efdc9f5503
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324814"
---
# <a name="how-to-check-that-net-core-is-already-installed"></a><span data-ttu-id="46bf9-104">如何检查是否已安装 .NET Core</span><span class="sxs-lookup"><span data-stu-id="46bf9-104">How to check that .NET Core is already installed</span></span>

<span data-ttu-id="46bf9-105">本文介绍如何检查计算机上安装的 .NET Core 运行时和 SDK 的版本。</span><span class="sxs-lookup"><span data-stu-id="46bf9-105">This article teaches you how to check which versions of the .NET Core runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="46bf9-106">如果你拥有一个集成开发环境（如 Visual Studio 或 Visual Studio for Mac），则可能已安装 .NET core。</span><span class="sxs-lookup"><span data-stu-id="46bf9-106">.NET core may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="46bf9-107">安装 SDK 便会安装相应的运行时。</span><span class="sxs-lookup"><span data-stu-id="46bf9-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="46bf9-108">如果本文中的任何命令失败，则未安装运行时或 SDK。</span><span class="sxs-lookup"><span data-stu-id="46bf9-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="46bf9-109">有关详细信息，请参阅[下载并安装 .NET Core](index.md)。</span><span class="sxs-lookup"><span data-stu-id="46bf9-109">For more information, see [Download and install .NET Core](index.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="46bf9-110">检查 SDK 版本</span><span class="sxs-lookup"><span data-stu-id="46bf9-110">Check SDK versions</span></span>

<span data-ttu-id="46bf9-111">可使用终端查看当前安装的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="46bf9-111">You can see which versions of the .NET Core SDK are currently installed with a terminal.</span></span> <span data-ttu-id="46bf9-112">打开终端并运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="46bf9-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="46bf9-113">将获得类似于下面的输出。</span><span class="sxs-lookup"><span data-stu-id="46bf9-113">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
2.2.101 [C:\program files\dotnet\sdk]
3.0.100 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
2.2.101 [/home/user/dotnet/sdk]
3.0.100 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
2.2.101 [/usr/local/share/dotnet/sdk]
3.0.100 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a><span data-ttu-id="46bf9-114">检查运行时版本</span><span class="sxs-lookup"><span data-stu-id="46bf9-114">Check runtime versions</span></span>

<span data-ttu-id="46bf9-115">可使用以下命令查看当前安装的 .NET Core 运行时版本。</span><span class="sxs-lookup"><span data-stu-id="46bf9-115">You can see which versions of the .NET Core runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="46bf9-116">将获得类似于下面的输出。</span><span class="sxs-lookup"><span data-stu-id="46bf9-116">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a><span data-ttu-id="46bf9-117">检查安装文件夹</span><span class="sxs-lookup"><span data-stu-id="46bf9-117">Check for install folders</span></span>

<span data-ttu-id="46bf9-118">可以安装 .NET Core，但不能将其添加到操作系统或用户配置文件的 `PATH` 变量。</span><span class="sxs-lookup"><span data-stu-id="46bf9-118">It's possible that .NET Core is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="46bf9-119">运行前面几节中的命令可能不起作用。</span><span class="sxs-lookup"><span data-stu-id="46bf9-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="46bf9-120">作为替代方法，可以检查 .NET Core 安装文件夹是否存在。</span><span class="sxs-lookup"><span data-stu-id="46bf9-120">As an alternative, you can check that the .NET Core install folders exist.</span></span>

<span data-ttu-id="46bf9-121">从安装程序或脚本安装 .NET Core 时，会将其安装到标准文件夹中。</span><span class="sxs-lookup"><span data-stu-id="46bf9-121">When you install .NET Core from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="46bf9-122">大多数时候，安装 .NET Core 时使用的安装程序或脚本会让你选择安装到另一个文件夹。</span><span class="sxs-lookup"><span data-stu-id="46bf9-122">Much of the time the installer or script you're using to install .NET Core gives you an option to install to a different folder.</span></span> <span data-ttu-id="46bf9-123">如果选择安装到其他文件夹，请调整文件夹路径的开头。</span><span class="sxs-lookup"><span data-stu-id="46bf9-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="46bf9-124">dotnet executable  </span><span class="sxs-lookup"><span data-stu-id="46bf9-124">**dotnet executable**</span></span>\
<span data-ttu-id="46bf9-125">C:\\program files\\dotnet\\dotnet.exe </span><span class="sxs-lookup"><span data-stu-id="46bf9-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="46bf9-126">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="46bf9-126">**.NET SDK**</span></span>\
<span data-ttu-id="46bf9-127">C:\\program files\\dotnet\\sdk\\{version}\\ </span><span class="sxs-lookup"><span data-stu-id="46bf9-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="46bf9-128">.NET Runtime  </span><span class="sxs-lookup"><span data-stu-id="46bf9-128">**.NET Runtime**</span></span>\
<span data-ttu-id="46bf9-129">C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\ </span><span class="sxs-lookup"><span data-stu-id="46bf9-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="46bf9-130">dotnet executable  </span><span class="sxs-lookup"><span data-stu-id="46bf9-130">**dotnet executable**</span></span>\
<span data-ttu-id="46bf9-131">/home/user/share/dotnet/dotnet </span><span class="sxs-lookup"><span data-stu-id="46bf9-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="46bf9-132">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="46bf9-132">**.NET SDK**</span></span>\
<span data-ttu-id="46bf9-133">/home/user/share/dotnet/sdk/{version}/ </span><span class="sxs-lookup"><span data-stu-id="46bf9-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="46bf9-134">.NET Runtime  </span><span class="sxs-lookup"><span data-stu-id="46bf9-134">**.NET Runtime**</span></span>\
<span data-ttu-id="46bf9-135">/home/user/share/dotnet/shared/{runtime-type}/{version}/ </span><span class="sxs-lookup"><span data-stu-id="46bf9-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="46bf9-136">dotnet executable  </span><span class="sxs-lookup"><span data-stu-id="46bf9-136">**dotnet executable**</span></span>\
<span data-ttu-id="46bf9-137">/usr/local/share/dotnet/dotnet </span><span class="sxs-lookup"><span data-stu-id="46bf9-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="46bf9-138">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="46bf9-138">**.NET SDK**</span></span>\
<span data-ttu-id="46bf9-139">/usr/local/share/dotnet/sdk/{version}/ </span><span class="sxs-lookup"><span data-stu-id="46bf9-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="46bf9-140">.NET Runtime  </span><span class="sxs-lookup"><span data-stu-id="46bf9-140">**.NET Runtime**</span></span>\
<span data-ttu-id="46bf9-141">/usr/local/share/dotnet/shared/{runtime-type}/{version}/ </span><span class="sxs-lookup"><span data-stu-id="46bf9-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="46bf9-142">详细信息</span><span class="sxs-lookup"><span data-stu-id="46bf9-142">More information</span></span>

<span data-ttu-id="46bf9-143">可通过命令 `dotnet --info` 查看 SDK 版本和运行时版本。</span><span class="sxs-lookup"><span data-stu-id="46bf9-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="46bf9-144">你还将获得其他环境相关信息，如操作系统版本和运行时标识符 (RID)。</span><span class="sxs-lookup"><span data-stu-id="46bf9-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="46bf9-145">后续步骤</span><span class="sxs-lookup"><span data-stu-id="46bf9-145">Next steps</span></span>

- <span data-ttu-id="46bf9-146">[安装 .NET Core 运行时](runtime.md)。</span><span class="sxs-lookup"><span data-stu-id="46bf9-146">[Install the .NET Core Runtime](runtime.md).</span></span>
- <span data-ttu-id="46bf9-147">[安装 .NET Core SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="46bf9-147">[Install the .NET Core SDK](sdk.md).</span></span>
