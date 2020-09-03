---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132934"
---

<span data-ttu-id="0b816-101">如果收到类似于“找不到包 {netcore-package}”或“无法安装某些包”的错误消息，请运行以下命令 。</span><span class="sxs-lookup"><span data-stu-id="0b816-101">If you receive an error message similar to **Unable to locate package {netcore-package}** or **Some packages could not be installed**, run the following commands.</span></span>

<span data-ttu-id="0b816-102">以下命令组中有两个占位符。</span><span class="sxs-lookup"><span data-stu-id="0b816-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="0b816-103">此项表示要安装的 .NET Core 包，如 `aspnetcore-runtime-3.1`。</span><span class="sxs-lookup"><span data-stu-id="0b816-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="0b816-104">此项在以下 `sudo apt-get install` 命令中使用。</span><span class="sxs-lookup"><span data-stu-id="0b816-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="0b816-105">此项表示你所使用的 Linux 版本。</span><span class="sxs-lookup"><span data-stu-id="0b816-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="0b816-106">此项在以下 `wget` 命令中使用。</span><span class="sxs-lookup"><span data-stu-id="0b816-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="0b816-107">首先，尝试清除包列表：</span><span class="sxs-lookup"><span data-stu-id="0b816-107">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="0b816-108">然后，再次尝试安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="0b816-108">Then, try to install .NET Core again.</span></span> <span data-ttu-id="0b816-109">如果这不起作用，可使用以下命令运行手动安装：</span><span class="sxs-lookup"><span data-stu-id="0b816-109">If that doesn't work, you can run a manual install with the following commands:</span></span>
