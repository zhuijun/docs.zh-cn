---
ms.openlocfilehash: db89539982c1afe0df374027d54826f3265f0fee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602770"
---

### <a name="install-the-sdk"></a><span data-ttu-id="daf87-101">安装 SDK</span><span class="sxs-lookup"><span data-stu-id="daf87-101">Install the SDK</span></span>

<span data-ttu-id="daf87-102">.NET Core SDK 使你可以通过 .NET Core 开发应用。</span><span class="sxs-lookup"><span data-stu-id="daf87-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="daf87-103">若要安装 .NET Core SDK，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="daf87-103">To install the .NET Core SDK, run the following commands.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="daf87-104">安装运行时</span><span class="sxs-lookup"><span data-stu-id="daf87-104">Install the runtime</span></span>

<span data-ttu-id="daf87-105">.NET Core 运行时允许运行使用不随附运行时的 .NET Core 所开发的应用。</span><span class="sxs-lookup"><span data-stu-id="daf87-105">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="daf87-106">以下命令安装 ASP.NET Core 运行时，这是与 .NET Core 最兼容的运行时。</span><span class="sxs-lookup"><span data-stu-id="daf87-106">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="daf87-107">在终端中，运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="daf87-107">In your terminal, run the following commands.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

<span data-ttu-id="daf87-108">作为 ASP.NET Core 运行时的一种替代方法，你可以安装不包含 ASP.NET Core 支持的 .NET Core 运行时：将上述命令中的 `aspnetcore-runtime-2.1` 替换为 `dotnet-runtime-3.1`。</span><span class="sxs-lookup"><span data-stu-id="daf87-108">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```
