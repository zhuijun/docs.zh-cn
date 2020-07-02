---
title: 如何对 .NET Core 运行时和 SDK 进行版本控制
description: 本文介绍了 .NET Core SDK 和运行时的版本控制方式（类似于语义版本控制）。
ms.date: 06/24/2020
ms.openlocfilehash: 5e315f49227f3c2ea40652a30fabbf566bdfe495
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619749"
---
# <a name="overview-of-how-net-core-is-versioned"></a><span data-ttu-id="a8a84-103">.NET Core 的版本控制方式概述</span><span class="sxs-lookup"><span data-stu-id="a8a84-103">Overview of how .NET Core is versioned</span></span>

<span data-ttu-id="a8a84-104">.NET Core 是指 .NET Core 运行时和 .NET Core SDK，它包含开发应用程序所需的工具。</span><span class="sxs-lookup"><span data-stu-id="a8a84-104">.NET Core refers to the .NET Core Runtime and the .NET Core SDK, which contains the tools you need to develop applications.</span></span> <span data-ttu-id="a8a84-105">.NET Core SDK 可与任何以前版本的 .NET Core 运行时一起使用。</span><span class="sxs-lookup"><span data-stu-id="a8a84-105">.NET Core SDKs are designed to work with any previous version of the .NET Core Runtime.</span></span> <span data-ttu-id="a8a84-106">本文介绍运行时和 SDK 版本策略。</span><span class="sxs-lookup"><span data-stu-id="a8a84-106">This article explains the runtime and the SDK version strategy.</span></span> <span data-ttu-id="a8a84-107">有关 .NET Standard 版本号的说明，请参阅介绍 [.NET Standar](../../standard/net-standard.md#net-implementation-support) 的文章。</span><span class="sxs-lookup"><span data-stu-id="a8a84-107">An explanation of version numbers for .NET Standard can be found in the article introducing [.NET Standard](../../standard/net-standard.md#net-implementation-support).</span></span>

<span data-ttu-id="a8a84-108">.NET Core 运行时和 .NET Core SDK 以不同的速率添加新功能，通常情况下，.NET Core SDK 提供更新工具的速度比 .NET Core 运行时更改生产中所用运行时的速度快。</span><span class="sxs-lookup"><span data-stu-id="a8a84-108">The .NET Core Runtime and .NET Core SDK add new features at a different rate - in general the .NET Core SDK provides updated tools more quickly than the .NET Core Runtime changes the runtime you use in production.</span></span>

## <a name="versioning-details"></a><span data-ttu-id="a8a84-109">版本控制详细信息</span><span class="sxs-lookup"><span data-stu-id="a8a84-109">Versioning details</span></span>

<span data-ttu-id="a8a84-110">“.NET Core 2.1”是指 .NET Core 运行时版本号。</span><span class="sxs-lookup"><span data-stu-id="a8a84-110">".NET Core 2.1" refers to the .NET Core Runtime version number.</span></span> <span data-ttu-id="a8a84-111">.NET Core 运行时用于版本控制的主要/次要/补丁方法需遵循[语义版本控制](#semantic-versioning)。</span><span class="sxs-lookup"><span data-stu-id="a8a84-111">The .NET Core Runtime has a major/minor/patch approach to versioning that follows [semantic versioning](#semantic-versioning).</span></span>

<span data-ttu-id="a8a84-112">.NET Core SDK 不遵循语义版本控制。</span><span class="sxs-lookup"><span data-stu-id="a8a84-112">The .NET Core SDK doesn't follow semantic versioning.</span></span> <span data-ttu-id="a8a84-113">.NET Core SDK 发布速度更快，其版本必须传达相应的运行时和 SDK 自己的次要版本和修补程序版本。</span><span class="sxs-lookup"><span data-stu-id="a8a84-113">The .NET Core SDK releases faster and its versions must communicate both the aligned runtime and the SDK's own minor and patch releases.</span></span> <span data-ttu-id="a8a84-114">.NET Core SDK 版本的前两个位置被锁定到与之一起发布的 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="a8a84-114">The first two positions of the .NET Core SDK version are locked to the .NET Core Runtime it released with.</span></span> <span data-ttu-id="a8a84-115">每个版本的 SDK 都可以为此版本或任何更低版本的运行时创建应用程序。</span><span class="sxs-lookup"><span data-stu-id="a8a84-115">Each version of the SDK can create applications for this runtime or any lower version.</span></span>

<span data-ttu-id="a8a84-116">SDK 版本号的第三个位置同时传达次要编号和修补程序编号。</span><span class="sxs-lookup"><span data-stu-id="a8a84-116">The third position of the SDK version number communicates both the minor and patch number.</span></span> <span data-ttu-id="a8a84-117">次要版本乘以 100。</span><span class="sxs-lookup"><span data-stu-id="a8a84-117">The minor version is multiplied by 100.</span></span> <span data-ttu-id="a8a84-118">次要版本 1，修补程序版本 2 将表示为 102。</span><span class="sxs-lookup"><span data-stu-id="a8a84-118">Minor version 1, patch version 2 would be represented as 102.</span></span> <span data-ttu-id="a8a84-119">最后两位数代表修补程序号。</span><span class="sxs-lookup"><span data-stu-id="a8a84-119">The final two digits represent the patch number.</span></span> <span data-ttu-id="a8a84-120">例如，.NET Core 2.2 可能会创建如下表所示的版本：</span><span class="sxs-lookup"><span data-stu-id="a8a84-120">For example, the release of .NET Core 2.2 may create releases like the following table:</span></span>

| <span data-ttu-id="a8a84-121">更改</span><span class="sxs-lookup"><span data-stu-id="a8a84-121">Change</span></span>                | <span data-ttu-id="a8a84-122">.NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="a8a84-122">.NET Core Runtime</span></span> | <span data-ttu-id="a8a84-123">.NET Core SDK (\*)</span><span class="sxs-lookup"><span data-stu-id="a8a84-123">.NET Core SDK (\*)</span></span> |
|-----------------------|-------------------|-------------------|
| <span data-ttu-id="a8a84-124">初始版本</span><span class="sxs-lookup"><span data-stu-id="a8a84-124">Initial release</span></span>       | <span data-ttu-id="a8a84-125">2.2.0</span><span class="sxs-lookup"><span data-stu-id="a8a84-125">2.2.0</span></span>             | <span data-ttu-id="a8a84-126">2.2.100</span><span class="sxs-lookup"><span data-stu-id="a8a84-126">2.2.100</span></span>           |
| <span data-ttu-id="a8a84-127">SDK 修补程序</span><span class="sxs-lookup"><span data-stu-id="a8a84-127">SDK Patch</span></span>             | <span data-ttu-id="a8a84-128">2.2.0</span><span class="sxs-lookup"><span data-stu-id="a8a84-128">2.2.0</span></span>             | <span data-ttu-id="a8a84-129">2.2.101</span><span class="sxs-lookup"><span data-stu-id="a8a84-129">2.2.101</span></span>           |
| <span data-ttu-id="a8a84-130">运行时和 SDK 修补程序</span><span class="sxs-lookup"><span data-stu-id="a8a84-130">Runtime and SDK Patch</span></span> | <span data-ttu-id="a8a84-131">2.2.1</span><span class="sxs-lookup"><span data-stu-id="a8a84-131">2.2.1</span></span>             | <span data-ttu-id="a8a84-132">2.2.102</span><span class="sxs-lookup"><span data-stu-id="a8a84-132">2.2.102</span></span>           |
| <span data-ttu-id="a8a84-133">SDK 功能更改</span><span class="sxs-lookup"><span data-stu-id="a8a84-133">SDK Feature change</span></span>    | <span data-ttu-id="a8a84-134">2.2.1</span><span class="sxs-lookup"><span data-stu-id="a8a84-134">2.2.1</span></span>             | <span data-ttu-id="a8a84-135">2.2.200</span><span class="sxs-lookup"><span data-stu-id="a8a84-135">2.2.200</span></span>           |

<span data-ttu-id="a8a84-136">(\*) 这个图表以 2.2 .NET Core 运行时为例，因为一个历史项目表明 .NET Core 2.1 的第一个 SDK 是 2.1.300。</span><span class="sxs-lookup"><span data-stu-id="a8a84-136">(\*) This chart uses the 2.2 .NET Core Runtime as the example because a historic artifact meant the first SDK for .NET Core 2.1 is 2.1.300.</span></span> <span data-ttu-id="a8a84-137">有关详细信息，请参阅 [.NET Core 版本选择](selection.md)页。</span><span class="sxs-lookup"><span data-stu-id="a8a84-137">For more information, See the [.NET Core version selection](selection.md).</span></span>

<span data-ttu-id="a8a84-138">注意：</span><span class="sxs-lookup"><span data-stu-id="a8a84-138">NOTES:</span></span>

- <span data-ttu-id="a8a84-139">如果在运行时功能更新之前，SDK 有 10 个功能更新，则版本号将滚动到 1000 系列，2.2.1000 等编号为 2.2.900 之后的功能版本。</span><span class="sxs-lookup"><span data-stu-id="a8a84-139">If the SDK has 10 feature updates before a runtime feature update, version numbers roll into the 1000 series with numbers like 2.2.1000 as the feature release following 2.2.900.</span></span> <span data-ttu-id="a8a84-140">应该不会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="a8a84-140">This situation isn't expected to occur.</span></span>
- <span data-ttu-id="a8a84-141">不会出现为发布功能的 99 修补程序版本。</span><span class="sxs-lookup"><span data-stu-id="a8a84-141">99 patch releases without a feature release won't occur.</span></span> <span data-ttu-id="a8a84-142">如果某版本接近此数字，则会强制发布功能。</span><span class="sxs-lookup"><span data-stu-id="a8a84-142">If a release approaches this number, it forces a feature release.</span></span>

<span data-ttu-id="a8a84-143">可在 [dotnet/设计](https://github.com/dotnet/designs/pull/29) 存储库中查看初始建议的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="a8a84-143">You can see more details in the initial proposal at the [dotnet/designs](https://github.com/dotnet/designs/pull/29) repository.</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="a8a84-144">语义化版本控制</span><span class="sxs-lookup"><span data-stu-id="a8a84-144">Semantic versioning</span></span>

<span data-ttu-id="a8a84-145">.NET Core 运行时大致遵循[语义版本控制 (SemVer)](https://semver.org/)，采用 `MAJOR.MINOR.PATCH` 版本控制，通过版本号的各部分来描述更改程度和类型。</span><span class="sxs-lookup"><span data-stu-id="a8a84-145">The .NET Core *Runtime* roughly adheres to [Semantic Versioning (SemVer)](https://semver.org/), adopting the use of `MAJOR.MINOR.PATCH` versioning, using the various parts of the version number to describe the degree and type of change.</span></span>

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

<span data-ttu-id="a8a84-146">可选的 `PRERELEASE` 和 `BUILDNUMBER` 部分永远不会成为受支持版本的一部分，并且将仅存在于夜间版本、来自源目标的本地版本，以及不受支持的预览版本中。</span><span class="sxs-lookup"><span data-stu-id="a8a84-146">The optional `PRERELEASE` and `BUILDNUMBER` parts are never part of supported releases and only exist on nightly builds, local builds from source targets, and unsupported preview releases.</span></span>

### <a name="understand-runtime-version-number-changes"></a><span data-ttu-id="a8a84-147">了解运行时版本号更改</span><span class="sxs-lookup"><span data-stu-id="a8a84-147">Understand runtime version number changes</span></span>

<span data-ttu-id="a8a84-148">`MAJOR` 在下列情况时递增：</span><span class="sxs-lookup"><span data-stu-id="a8a84-148">`MAJOR` is incremented when:</span></span>

- <span data-ttu-id="a8a84-149">产品或新产品方向发生重大更改。</span><span class="sxs-lookup"><span data-stu-id="a8a84-149">Significant changes occur to the product, or a new product direction.</span></span>
- <span data-ttu-id="a8a84-150">发生了中断性变更。</span><span class="sxs-lookup"><span data-stu-id="a8a84-150">Breaking changes were taken.</span></span> <span data-ttu-id="a8a84-151">接受中断性变更存在较大障碍。</span><span class="sxs-lookup"><span data-stu-id="a8a84-151">There's a high bar to accepting breaking changes.</span></span>
- <span data-ttu-id="a8a84-152">旧版本不再受支持。</span><span class="sxs-lookup"><span data-stu-id="a8a84-152">An old version is no longer supported.</span></span>
- <span data-ttu-id="a8a84-153">采用了现有依赖项的较新 `MAJOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="a8a84-153">A newer `MAJOR` version of an existing dependency is adopted.</span></span>

<span data-ttu-id="a8a84-154">`MINOR` 在下列情况时递增：</span><span class="sxs-lookup"><span data-stu-id="a8a84-154">`MINOR` is incremented when:</span></span>

- <span data-ttu-id="a8a84-155">添加了公共 API 外围应用。</span><span class="sxs-lookup"><span data-stu-id="a8a84-155">Public API surface area is added.</span></span>
- <span data-ttu-id="a8a84-156">添加了新行为。</span><span class="sxs-lookup"><span data-stu-id="a8a84-156">A new behavior is added.</span></span>
- <span data-ttu-id="a8a84-157">采用了现有依赖项的较新 `MINOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="a8a84-157">A newer `MINOR` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="a8a84-158">引入了新依赖项。</span><span class="sxs-lookup"><span data-stu-id="a8a84-158">A new dependency is introduced.</span></span>

<span data-ttu-id="a8a84-159">`PATCH` 在下列情况时递增：</span><span class="sxs-lookup"><span data-stu-id="a8a84-159">`PATCH` is incremented when:</span></span>

- <span data-ttu-id="a8a84-160">进行了 Bug 修复。</span><span class="sxs-lookup"><span data-stu-id="a8a84-160">Bug fixes are made.</span></span>
- <span data-ttu-id="a8a84-161">添加了对较新平台的支持。</span><span class="sxs-lookup"><span data-stu-id="a8a84-161">Support for a newer platform is added.</span></span>
- <span data-ttu-id="a8a84-162">采用了现有依赖项的较新 `PATCH` 版本。</span><span class="sxs-lookup"><span data-stu-id="a8a84-162">A newer `PATCH` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="a8a84-163">任何其他不符合上述情况的更改。</span><span class="sxs-lookup"><span data-stu-id="a8a84-163">Any other change doesn't fit one of the previous cases.</span></span>

<span data-ttu-id="a8a84-164">存在多处更改时，单个更改影响的最高级别元素会递增，并将随后的元素重置为零。</span><span class="sxs-lookup"><span data-stu-id="a8a84-164">When there are multiple changes, the highest element affected by individual changes is incremented, and the following ones are reset to zero.</span></span> <span data-ttu-id="a8a84-165">例如，当 `MAJOR` 递增时，`MINOR` 和 `PATCH` 将重置为零。</span><span class="sxs-lookup"><span data-stu-id="a8a84-165">For example, when `MAJOR` is incremented, `MINOR` and `PATCH` are reset to zero.</span></span> <span data-ttu-id="a8a84-166">当 `MINOR` 递增时，`PATCH` 将重置为零，而 `MAJOR` 保持不变。</span><span class="sxs-lookup"><span data-stu-id="a8a84-166">When `MINOR` is incremented, `PATCH` is reset to zero while `MAJOR` is left untouched.</span></span>

## <a name="version-numbers-in-file-names"></a><span data-ttu-id="a8a84-167">文件名中的版本号</span><span class="sxs-lookup"><span data-stu-id="a8a84-167">Version numbers in file names</span></span>

<span data-ttu-id="a8a84-168">为 .NET Core 下载的文件带有版本，例如 `dotnet-sdk-2.1.300-win10-x64.exe`。</span><span class="sxs-lookup"><span data-stu-id="a8a84-168">The files downloaded for .NET Core carry the version, for example, `dotnet-sdk-2.1.300-win10-x64.exe`.</span></span>

### <a name="preview-versions"></a><span data-ttu-id="a8a84-169">预览版</span><span class="sxs-lookup"><span data-stu-id="a8a84-169">Preview versions</span></span>

<span data-ttu-id="a8a84-170">预览版向版本中追加了 `-preview[number]-([build]|"final")`。</span><span class="sxs-lookup"><span data-stu-id="a8a84-170">Preview versions have a `-preview[number]-([build]|"final")` appended to the version.</span></span> <span data-ttu-id="a8a84-171">例如 `2.0.0-preview1-final`。</span><span class="sxs-lookup"><span data-stu-id="a8a84-171">For example, `2.0.0-preview1-final`.</span></span>

### <a name="servicing-versions"></a><span data-ttu-id="a8a84-172">服务版本</span><span class="sxs-lookup"><span data-stu-id="a8a84-172">Servicing versions</span></span>

<span data-ttu-id="a8a84-173">在版本发布后，版本分支通常停止生成日常版本，而开始生成服务版本。</span><span class="sxs-lookup"><span data-stu-id="a8a84-173">After a release goes out, the release branches generally stop producing daily builds and instead start producing servicing builds.</span></span> <span data-ttu-id="a8a84-174">服务版本向版本追加了 `-servicing-[number]`。</span><span class="sxs-lookup"><span data-stu-id="a8a84-174">Servicing versions have a `-servicing-[number]` appended to the version.</span></span> <span data-ttu-id="a8a84-175">例如 `2.0.1-servicing-006924`。</span><span class="sxs-lookup"><span data-stu-id="a8a84-175">For example, `2.0.1-servicing-006924`.</span></span>

## <a name="relationship-to-net-standard-versions"></a><span data-ttu-id="a8a84-176">与 .NET Standard 版本的关系</span><span class="sxs-lookup"><span data-stu-id="a8a84-176">Relationship to .NET Standard versions</span></span>

<span data-ttu-id="a8a84-177">.NET Standard 由 .NET 引用程序集组成。</span><span class="sxs-lookup"><span data-stu-id="a8a84-177">.NET Standard consists of a .NET reference assembly.</span></span> <span data-ttu-id="a8a84-178">每个平台都有多个特定的实现。</span><span class="sxs-lookup"><span data-stu-id="a8a84-178">There are multiple implementations specific to each platform.</span></span> <span data-ttu-id="a8a84-179">引用程序集包含 .NET API 的定义，后者是给定 .NET Standard 版本的一部分。</span><span class="sxs-lookup"><span data-stu-id="a8a84-179">The reference assembly contains the definition of .NET APIs which are part of a given .NET Standard version.</span></span> <span data-ttu-id="a8a84-180">每个实现均满足特定平台上的 .NET Standard 协定。</span><span class="sxs-lookup"><span data-stu-id="a8a84-180">Each implementation fulfills the .NET Standard contract on the specific platform.</span></span> <span data-ttu-id="a8a84-181">可参阅 .NET 指南中有关 [.NET Standard](../../standard/net-standard.md) 的文章，深入了解 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="a8a84-181">You can learn more about .NET Standard in the article on [.NET Standard](../../standard/net-standard.md) in the .NET Guide.</span></span>

<span data-ttu-id="a8a84-182">.NET Standard 引用程序集使用 `MAJOR.MINOR` 版本控制方案。</span><span class="sxs-lookup"><span data-stu-id="a8a84-182">The .NET Standard reference assembly uses a `MAJOR.MINOR` versioning scheme.</span></span> <span data-ttu-id="a8a84-183">`PATCH` 级别对 .NET Standard 并无用处，因为它只公开 API 规范（没有实现），并且根据定义，对 API 的任何更改都将作为功能集的更改，从进而产生新的 `MINOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="a8a84-183">`PATCH` level isn't useful for .NET Standard because it exposes only an API specification (no implementation) and by definition any change to the API would represent a change in the feature set, and thus a new `MINOR` version.</span></span>

<span data-ttu-id="a8a84-184">每个平台上的实现通常可作为平台版本的一部分更新，因此对于在该平台上使用 .NET Standard 的程序员来说并不明显。</span><span class="sxs-lookup"><span data-stu-id="a8a84-184">The implementations on each platform may be updated, typically as part of the platform release, and thus not evident to the programmers using .NET Standard on that platform.</span></span>

<span data-ttu-id="a8a84-185">每个版本的 .NET Core 都实现了某一版本的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="a8a84-185">Each version of .NET Core implements a version of .NET Standard.</span></span> <span data-ttu-id="a8a84-186">实现某一版本的 .NET Standard 意味着支持以前版本的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="a8a84-186">Implementing a version of .NET Standard implies support for previous versions of .NET Standard.</span></span> <span data-ttu-id="a8a84-187">.NET Standard 和 .NET Core 版本独立。</span><span class="sxs-lookup"><span data-stu-id="a8a84-187">.NET Standard and .NET Core version independently.</span></span> <span data-ttu-id="a8a84-188">.NET Core 2.0 实现 .NET Standard 2.0 是巧合。</span><span class="sxs-lookup"><span data-stu-id="a8a84-188">It's a coincidence that .NET Core 2.0 implements .NET Standard 2.0.</span></span> <span data-ttu-id="a8a84-189">.NET Core 2.1 也可实现 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="a8a84-189">.NET Core 2.1 also implements .NET Standard 2.0.</span></span> <span data-ttu-id="a8a84-190">.NET Standard 的未来版本出现后，.NET Core 将支持这些版本。</span><span class="sxs-lookup"><span data-stu-id="a8a84-190">.NET Core will support future versions of .NET Standard as they become available.</span></span>

| <span data-ttu-id="a8a84-191">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a8a84-191">.NET Core</span></span> | <span data-ttu-id="a8a84-192">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="a8a84-192">.NET Standard</span></span> |
|-----------|---------------|
| <span data-ttu-id="a8a84-193">1.0</span><span class="sxs-lookup"><span data-stu-id="a8a84-193">1.0</span></span>       | <span data-ttu-id="a8a84-194">达 1.6</span><span class="sxs-lookup"><span data-stu-id="a8a84-194">up to 1.6</span></span>     |
| <span data-ttu-id="a8a84-195">2.0</span><span class="sxs-lookup"><span data-stu-id="a8a84-195">2.0</span></span>       | <span data-ttu-id="a8a84-196">达 2.0</span><span class="sxs-lookup"><span data-stu-id="a8a84-196">up to 2.0</span></span>     |
| <span data-ttu-id="a8a84-197">2.1</span><span class="sxs-lookup"><span data-stu-id="a8a84-197">2.1</span></span>       | <span data-ttu-id="a8a84-198">达 2.0</span><span class="sxs-lookup"><span data-stu-id="a8a84-198">up to 2.0</span></span>     |
| <span data-ttu-id="a8a84-199">2.2</span><span class="sxs-lookup"><span data-stu-id="a8a84-199">2.2</span></span>       | <span data-ttu-id="a8a84-200">达 2.0</span><span class="sxs-lookup"><span data-stu-id="a8a84-200">up to 2.0</span></span>     |
| <span data-ttu-id="a8a84-201">3.0</span><span class="sxs-lookup"><span data-stu-id="a8a84-201">3.0</span></span>       | <span data-ttu-id="a8a84-202">至 2.1</span><span class="sxs-lookup"><span data-stu-id="a8a84-202">up to 2.1</span></span>     |
| <span data-ttu-id="a8a84-203">3.1</span><span class="sxs-lookup"><span data-stu-id="a8a84-203">3.1</span></span>       | <span data-ttu-id="a8a84-204">至 2.1</span><span class="sxs-lookup"><span data-stu-id="a8a84-204">up to 2.1</span></span>     |

<span data-ttu-id="a8a84-205">有关 .NET Standard 版本的交互表以及它们与 .NET 实现的对应关系，请参阅 [.NET Standard 版本](https://dotnet.microsoft.com/platform/dotnet-standard#versions)。</span><span class="sxs-lookup"><span data-stu-id="a8a84-205">For an interactive table of the .NET Standard versions, and how they correspond to .NET implementations, see [.NET Standard versions](https://dotnet.microsoft.com/platform/dotnet-standard#versions).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8a84-206">请参阅</span><span class="sxs-lookup"><span data-stu-id="a8a84-206">See also</span></span>

- [<span data-ttu-id="a8a84-207">目标框架</span><span class="sxs-lookup"><span data-stu-id="a8a84-207">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="a8a84-208">.NET Core 分发打包</span><span class="sxs-lookup"><span data-stu-id="a8a84-208">.NET Core distribution packaging</span></span>](../distribution-packaging.md)
- [<span data-ttu-id="a8a84-209">.NET Core 支持生命周期简报</span><span class="sxs-lookup"><span data-stu-id="a8a84-209">.NET Core Support Lifecycle Fact Sheet</span></span>](https://dotnet.microsoft.com/platform/support/policy)
- [<span data-ttu-id="a8a84-210">.NET Core 2 和版本绑定</span><span class="sxs-lookup"><span data-stu-id="a8a84-210">.NET Core 2+ Version Binding</span></span>](https://github.com/dotnet/designs/issues/3)
- [<span data-ttu-id="a8a84-211">.NET Core 的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="a8a84-211">Docker images for .NET Core</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
