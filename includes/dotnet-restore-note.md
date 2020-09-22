---
ms.openlocfilehash: f22ee4accf9ff00814fa540adce4b9ecc6686da4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537726"
---
<span data-ttu-id="a0d23-101">无需运行 [`dotnet restore`](~/docs/core/tools/dotnet-restore.md)，因为它由所有需要还原的命令隐式运行，如 `dotnet new`、`dotnet build`、`dotnet run`、`dotnet test`、`dotnet publish` 和 `dotnet pack`。</span><span class="sxs-lookup"><span data-stu-id="a0d23-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="a0d23-102">若要禁用隐式还原，请使用 `--no-restore` 选项。</span><span class="sxs-lookup"><span data-stu-id="a0d23-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="a0d23-103">在执行显式还原有意义的某些情况下，例如 [Azure DevOps Services 中的持续集成生成](/azure/devops/build-release/apps/aspnet/build-aspnet-core)中，或在需要显式控制还原发生时间的生成系统中，`dotnet restore` 命令仍然有用。</span><span class="sxs-lookup"><span data-stu-id="a0d23-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="a0d23-104">有关如何使用 NuGet 源的信息，请参阅 [`dotnet restore` 文档](../docs/core/tools/dotnet-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d23-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
