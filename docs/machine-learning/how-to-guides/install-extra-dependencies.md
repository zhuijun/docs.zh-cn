---
title: 安装额外的 ML.NET 依赖项
description: 了解如何安装 ML.NET 包所依赖的但又不与 NuGet 包一起安装的任何本机库
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: c744b42b4b95681de7b0cbeaef338cc890708fd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008425"
---
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="0499a-103">安装额外的 ML.NET 依赖项</span><span class="sxs-lookup"><span data-stu-id="0499a-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="0499a-104">在大多数情况下，在所有操作系统上，安装 ML.NET 就像引用适当的 NuGet 包一样简单。</span><span class="sxs-lookup"><span data-stu-id="0499a-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```dotnetcli
dotnet add package Microsoft.ML
```

<span data-ttu-id="0499a-105">但在某些情况下，还存在其他安装要求，尤其是在需要本机组件时。</span><span class="sxs-lookup"><span data-stu-id="0499a-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="0499a-106">本文档介绍了这些情况的安装要求。</span><span class="sxs-lookup"><span data-stu-id="0499a-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="0499a-107">这些部分根据特定的 `Microsoft.ML.*` NuGet 包进行了细分，此包具有其他依赖项。</span><span class="sxs-lookup"><span data-stu-id="0499a-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="0499a-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span><span class="sxs-lookup"><span data-stu-id="0499a-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="0499a-109">这两个包都依赖于 `Microsoft.ML.MKL.Redist`，而后者又依赖于 `libiomp`。</span><span class="sxs-lookup"><span data-stu-id="0499a-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libiomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="0499a-110">Windows</span><span class="sxs-lookup"><span data-stu-id="0499a-110">Windows</span></span>

<span data-ttu-id="0499a-111">无需执行额外的安装步骤。</span><span class="sxs-lookup"><span data-stu-id="0499a-111">No extra installation steps required.</span></span> <span data-ttu-id="0499a-112">将 NuGet 包添加到项目时，会安装库。</span><span class="sxs-lookup"><span data-stu-id="0499a-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="0499a-113">Linux</span><span class="sxs-lookup"><span data-stu-id="0499a-113">Linux</span></span>

1. <span data-ttu-id="0499a-114">安装存储库的 GPG 键</span><span class="sxs-lookup"><span data-stu-id="0499a-114">Install the GPG key for the repository</span></span>

    ```bash
    sudo bash
    # <type your user password when prompted.  this will put you in a root shell>
    # cd to /tmp where this shell has write permission
    cd /tmp
    # now get the key:
    wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now install that key
    apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now remove the public key file exit the root shell
    rm GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    exit
    ```

2. <span data-ttu-id="0499a-115">为 MKL 添加 APT 存储库</span><span class="sxs-lookup"><span data-stu-id="0499a-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="0499a-116">更新包</span><span class="sxs-lookup"><span data-stu-id="0499a-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="0499a-117">安装 MKL</span><span class="sxs-lookup"><span data-stu-id="0499a-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="0499a-118">例如：</span><span class="sxs-lookup"><span data-stu-id="0499a-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="0499a-119">确定 `libiomp.so` 的位置</span><span class="sxs-lookup"><span data-stu-id="0499a-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="0499a-120">例如：</span><span class="sxs-lookup"><span data-stu-id="0499a-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="0499a-121">将此位置添加到加载库路径：</span><span class="sxs-lookup"><span data-stu-id="0499a-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a><span data-ttu-id="0499a-122">Mac</span><span class="sxs-lookup"><span data-stu-id="0499a-122">Mac</span></span>

1. <span data-ttu-id="0499a-123">使用 `Homebrew` 安装库</span><span class="sxs-lookup"><span data-stu-id="0499a-123">Install the library with `Homebrew`</span></span>

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
