---
ms.openlocfilehash: b371525c9f4e57c6a09e5bb9232884e5c5e707e0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602764"
---

<span data-ttu-id="3b1c0-101">使用包管理器进行安装时，将为你安装这些库。</span><span class="sxs-lookup"><span data-stu-id="3b1c0-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="3b1c0-102">但是，如果手动安装 .NET Core 或发布自包含的应用，则需要确保已安装以下库：</span><span class="sxs-lookup"><span data-stu-id="3b1c0-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="3b1c0-103">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="3b1c0-103">lttng-ust</span></span>
- <span data-ttu-id="3b1c0-104">libcurl</span><span class="sxs-lookup"><span data-stu-id="3b1c0-104">libcurl</span></span>
- <span data-ttu-id="3b1c0-105">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="3b1c0-105">openssl-libs</span></span>
- <span data-ttu-id="3b1c0-106">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="3b1c0-106">krb5-libs</span></span>
- <span data-ttu-id="3b1c0-107">libicu</span><span class="sxs-lookup"><span data-stu-id="3b1c0-107">libicu</span></span>
- <span data-ttu-id="3b1c0-108">zlib</span><span class="sxs-lookup"><span data-stu-id="3b1c0-108">zlib</span></span>
- <span data-ttu-id="3b1c0-109">libunwind</span><span class="sxs-lookup"><span data-stu-id="3b1c0-109">libunwind</span></span>
- <span data-ttu-id="3b1c0-110">libuuid</span><span class="sxs-lookup"><span data-stu-id="3b1c0-110">libuuid</span></span>

<span data-ttu-id="3b1c0-111">如果目标运行时环境的 OpenSSL 版本为1.1 或更高版本，则需要安装 compat-openssl10。</span><span class="sxs-lookup"><span data-stu-id="3b1c0-111">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="3b1c0-112">有关依赖项的详细信息，请参阅[独立式 Linux 应用](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="3b1c0-112">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="3b1c0-113">对于使用 System.Drawing.Common 程序集的 .NET Core 应用，还需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="3b1c0-113">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="3b1c0-114">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="3b1c0-114">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="3b1c0-115">可以通过将 Mono 存储库添加到系统来安装最新版 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="3b1c0-115">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="3b1c0-116">有关详细信息，请参阅 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="3b1c0-116">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
