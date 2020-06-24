---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602716"
---

<span data-ttu-id="0d908-101">[dotnet-install 脚本](../../tools/dotnet-install-script.md)用于 SDK 的自动化和非管理员安装。</span><span class="sxs-lookup"><span data-stu-id="0d908-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK**.</span></span> <span data-ttu-id="0d908-102">可通过 <https://dot.net/v1/dotnet-install.sh> 下载脚本。</span><span class="sxs-lookup"><span data-stu-id="0d908-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="0d908-103">此脚本默认安装最新的[长期支持 (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，即 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="0d908-103">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="0d908-104">若要安装当前版本（可能不是 (LTS) 版本），请使用 `-c Current` 参数。</span><span class="sxs-lookup"><span data-stu-id="0d908-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="0d908-105">若要安装 .NET Core 运行时而非 SDK，请使用 `--runtime` 参数。</span><span class="sxs-lookup"><span data-stu-id="0d908-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime
```

<span data-ttu-id="0d908-106">可以通过更改 `-c` 参数以指示特定版本来安装特定版本。</span><span class="sxs-lookup"><span data-stu-id="0d908-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="0d908-107">以下命令将安装 .NET Core SDK 3.1。</span><span class="sxs-lookup"><span data-stu-id="0d908-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="0d908-108">有关详细信息，请参阅 [dotnet-install 脚本参考](../../tools/dotnet-install-script.md)。</span><span class="sxs-lookup"><span data-stu-id="0d908-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
