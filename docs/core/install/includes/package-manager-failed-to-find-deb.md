---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602746"
---

<span data-ttu-id="c1827-101">如果收到类似于“找不到包 {netcore-package}”的错误消息，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="c1827-101">If you receive an error message similar to **Unable to locate package {netcore-package}**, run the following commands.</span></span>

<span data-ttu-id="c1827-102">以下命令组中有两个占位符。</span><span class="sxs-lookup"><span data-stu-id="c1827-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="c1827-103">此项表示要安装的 .NET Core 包，如 `aspnetcore-runtime-3.1`。</span><span class="sxs-lookup"><span data-stu-id="c1827-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="c1827-104">此项在以下 `sudo apt-get install` 命令中使用。</span><span class="sxs-lookup"><span data-stu-id="c1827-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="c1827-105">此项表示你所使用的 Linux 版本。</span><span class="sxs-lookup"><span data-stu-id="c1827-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="c1827-106">此项在以下 `wget` 命令中使用。</span><span class="sxs-lookup"><span data-stu-id="c1827-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="c1827-107">尝试清除包列表：</span><span class="sxs-lookup"><span data-stu-id="c1827-107">Try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

<span data-ttu-id="c1827-108">如果这不起作用，可使用以下命令运行手动安装：</span><span class="sxs-lookup"><span data-stu-id="c1827-108">If that doesn't work, you can run a manual install with the following commands:</span></span>
