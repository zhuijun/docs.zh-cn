---
title: 使用包管理器在 Ubuntu 20.04 上安装 .NET Core - .NET Core
description: 使用包管理器在 Ubuntu 20.04 上安装 .NET Core SDK 和运行时。
author: thraka
ms.author: adegeo
ms.date: 05/13/2020
ms.openlocfilehash: 4d7d7ee9117314ef360097fee929f24943c7a7f2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83618869"
---
# <a name="ubuntu-2004-package-manager---install-net-core"></a><span data-ttu-id="97966-103">Ubuntu 20.04 包管理器 - 安装 .NET Core</span><span class="sxs-lookup"><span data-stu-id="97966-103">Ubuntu 20.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="97966-104">本文介绍如何使用包管理器在 Ubuntu 20.04 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="97966-104">This article describes how to use a package manager to install .NET Core on Ubuntu 20.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="97966-105">添加 Microsoft 存储库密钥和源</span><span class="sxs-lookup"><span data-stu-id="97966-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="97966-106">安装 .NET 之前，需要：</span><span class="sxs-lookup"><span data-stu-id="97966-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="97966-107">将 Microsoft 包签名密钥添加到受信任密钥列表。</span><span class="sxs-lookup"><span data-stu-id="97966-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="97966-108">将此存储库添加到包管理器。</span><span class="sxs-lookup"><span data-stu-id="97966-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="97966-109">安装必需的依赖项。</span><span class="sxs-lookup"><span data-stu-id="97966-109">Install required dependencies.</span></span>

<span data-ttu-id="97966-110">每台计算机只需要执行一次此操作。</span><span class="sxs-lookup"><span data-stu-id="97966-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="97966-111">打开终端并运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="97966-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="97966-112">安装 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="97966-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="97966-113">更新可供安装的产品，然后安装 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="97966-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="97966-114">在终端中，运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="97966-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="97966-115">如果收到类似于“找不到包 dotnet-sdk-3.1”的错误消息，请参阅[包管理器疑难解答](#troubleshoot-the-package-manager)部分。</span><span class="sxs-lookup"><span data-stu-id="97966-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="97966-116">安装 ASP.NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="97966-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="97966-117">更新可供安装的产品，然后安装 ASP.NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="97966-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="97966-118">在终端中，运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="97966-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="97966-119">如果收到类似于“找不到包 aspnetcore-runtime-3.1”的错误消息，请参阅[包管理器疑难解答](#troubleshoot-the-package-manager)部分。</span><span class="sxs-lookup"><span data-stu-id="97966-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="97966-120">安装 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="97966-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="97966-121">更新可供安装的产品，然后安装 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="97966-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="97966-122">在终端中，运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="97966-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="97966-123">如果收到类似于“找不到包 dotnet-runtime-3.1”的错误消息，请参阅[包管理器疑难解答](#troubleshoot-the-package-manager)部分。</span><span class="sxs-lookup"><span data-stu-id="97966-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="97966-124">如何安装其他版本</span><span class="sxs-lookup"><span data-stu-id="97966-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="97966-125">包管理器疑难解答</span><span class="sxs-lookup"><span data-stu-id="97966-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="97966-126">本部分提供有关使用程序包管理器安装 .NET Core 时可能会遇到的常见错误的信息。</span><span class="sxs-lookup"><span data-stu-id="97966-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="97966-127">无法定位</span><span class="sxs-lookup"><span data-stu-id="97966-127">Unable to locate</span></span>

<span data-ttu-id="97966-128">如果收到类似于“找不到包 {.NET Core 包}”的错误消息，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="97966-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="97966-129">如果这不起作用，可使用以下命令运行手动安装。</span><span class="sxs-lookup"><span data-stu-id="97966-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/20.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="97966-130">未能提取</span><span class="sxs-lookup"><span data-stu-id="97966-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
