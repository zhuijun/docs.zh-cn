---
title: 源链接和 .NET 库
description: 有关使用源链接改进 .NET 库调试的最佳做法建议。
ms.date: 01/15/2019
ms.openlocfilehash: 5dee2a6b1f77daa641351e02c1dd3e0a38f66550
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201982"
---
# <a name="source-link"></a><span data-ttu-id="fe5cd-103">源链接</span><span class="sxs-lookup"><span data-stu-id="fe5cd-103">Source Link</span></span>

<span data-ttu-id="fe5cd-104">源链接是一种使开发人员可以从 NuGet 对 .NET 程序集进行源代码调试的技术。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="fe5cd-105">源链接在创建 NuGet 包时执行，然后将源代码管理元数据嵌入在程序集和包中。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="fe5cd-106">下载包并且在 Visual Studio 中启用了源链接的开发人员可以单步执行其源代码。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="fe5cd-107">源链接提供源代码管理元数据来创造出色的调试体验。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="fe5cd-108">源链接演示</span><span class="sxs-lookup"><span data-stu-id="fe5cd-108">Source Link demo</span></span>

<!--markdownlint-disable MD034 -->
> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="fe5cd-109">使用源链接</span><span class="sxs-lookup"><span data-stu-id="fe5cd-109">Using Source Link</span></span>

<span data-ttu-id="fe5cd-110">可以在 [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub 存储库上找到有关使用源链接的说明。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="fe5cd-111">可以使用 [NuGet 包资源管理器](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)以确认源链接元数据是否已成功嵌入在包中。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="fe5cd-112">检查 `Repository` 元数据是否存在并具有注释标识符，以及 .pdb 文件是否与每个目标的 .dll 放置在一起。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-112">Check the `Repository` metadata is present with a commit identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="fe5cd-113">![NuGet 包资源管理器中的源链接](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet 包资源管理器中的源链接")</span><span class="sxs-lookup"><span data-stu-id="fe5cd-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="fe5cd-114">✔️ 请考虑使用源链接将源代码管理元数据添加到程序集和 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-114">✔️ CONSIDER using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="fe5cd-115">可以通过将调试器特性添加到类型来进一步增强开发人员的调试体验。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="fe5cd-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> 可以自定义类或字段在调试器变量窗口中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="fe5cd-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> 指示调试器逐行执行代码，而不是单步执行代码。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="fe5cd-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> 控制成员是否会显示在调试器变量窗口中以及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="fe5cd-119">✔️ 请考虑发布符号文件 (`*.pdb`)。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-119">✔️ CONSIDER publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="fe5cd-120">为获得最佳调试体验，库应发布符号文件并使用源链接。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="fe5cd-121">有关符号文件和符号包的详细信息，请参阅[符号包](./nuget.md#symbol-packages)。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

<span data-ttu-id="fe5cd-122">✔️ 考虑启用确定性版本。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-122">✔️ CONSIDER enabling deterministic builds.</span></span>

> <span data-ttu-id="fe5cd-123">确定性版本可用于验证生成的二进制文件是否是从指定的源生成的，并提供可跟踪性。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-123">Deterministic builds enable verification that the resulting binary was built from the specified source and provide traceability.</span></span> <span data-ttu-id="fe5cd-124">有关确定性版本的详细信息和启用它们的说明，请参阅[确定性版本](https://github.com/clairernovotny/DeterministicBuilds)。</span><span class="sxs-lookup"><span data-stu-id="fe5cd-124">For more information about deterministic builds and instructions for enabling them, see [Deterministic Builds](https://github.com/clairernovotny/DeterministicBuilds).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fe5cd-125">[上一页](dependencies.md)
>[下一页](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="fe5cd-125">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
