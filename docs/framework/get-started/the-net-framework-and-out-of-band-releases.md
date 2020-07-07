---
title: .NET Framework 和带外版本
description: 了解 .NET 和带外版本。 发布了一些带外 (OOB) 的新功能，可改进跨平台开发或引入新的功能。
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 9653696f46279e0c23418f92030d64839cc20518
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618761"
---
# <a name="net-framework-and-out-of-band-releases"></a><span data-ttu-id="5cfec-104">.NET Framework 和带外版本</span><span class="sxs-lookup"><span data-stu-id="5cfec-104">.NET Framework and out-of-band releases</span></span>

<span data-ttu-id="5cfec-105">.NET Framework 不断发展，可适应不同的平台（例如 UWP 应用、传统桌面和 Web 应用）并最大限度地实现代码重用。</span><span class="sxs-lookup"><span data-stu-id="5cfec-105">.NET Framework has evolved to accommodate different platforms, such as UWP apps and traditional desktop and web apps, and to maximize code reuse.</span></span> <span data-ttu-id="5cfec-106">除了定期的 .NET Framework 发布之外，还会发布一些带外 (OOB) 的新功能，改进跨平台开发或引入新的功能。</span><span class="sxs-lookup"><span data-stu-id="5cfec-106">In addition to regular .NET Framework releases, new features are released out of band (OOB) to improve cross-platform development or to introduce new functionality.</span></span>

## <a name="advantages-of-oob-releases"></a><span data-ttu-id="5cfec-107">OOB 版本的优点</span><span class="sxs-lookup"><span data-stu-id="5cfec-107">Advantages of OOB releases</span></span>

<span data-ttu-id="5cfec-108">通过将新组件或更新发送给带外组件，使 Microsoft 能够更频繁地提供 .NET Framework 的更新。</span><span class="sxs-lookup"><span data-stu-id="5cfec-108">Shipping new components or updates to components out of band enables Microsoft to provide more frequent updates to .NET Framework.</span></span> <span data-ttu-id="5cfec-109">此外，我们可以更快地收集和回应客户反馈。</span><span class="sxs-lookup"><span data-stu-id="5cfec-109">In addition, we can gather and respond to customer feedback more quickly.</span></span>

<span data-ttu-id="5cfec-110">如果你在应用中使用了 OOB 功能，你的用户不必安装最新版 .NET Framework 即可运行你的应用，因为 OOB 程序集是与你的应用包一起部署的。</span><span class="sxs-lookup"><span data-stu-id="5cfec-110">When you use an OOB feature in your app, your users do not have to install the latest version of .NET Framework to run your app, because the OOB assemblies deploy with your app package.</span></span>

## <a name="how-oob-packages-are-distributed"></a><span data-ttu-id="5cfec-111">OOB 包是如何存储的</span><span class="sxs-lookup"><span data-stu-id="5cfec-111">How OOB packages are distributed</span></span>

<span data-ttu-id="5cfec-112">核心公共语言运行时 (CLR) 组件的 OOB 版本通过 [NuGet](https://www.nuget.org/)（.NET 的包管理器）提供。</span><span class="sxs-lookup"><span data-stu-id="5cfec-112">OOB releases for core common language runtime (CLR) components are delivered through [NuGet](https://www.nuget.org/), which is the package manager for .NET.</span></span> <span data-ttu-id="5cfec-113">通过 NuGet，你可轻松地从 Visual Studio 内浏览库并将其添加至你的 .NET Framework 项目。</span><span class="sxs-lookup"><span data-stu-id="5cfec-113">NuGet enables you to browse and add libraries to your .NET Framework projects easily from within Visual Studio.</span></span> <span data-ttu-id="5cfec-114">从 Visual Studio 2012 开始，NuGet 包管理器随附于 Visual Studio 的所有版本。</span><span class="sxs-lookup"><span data-stu-id="5cfec-114">NuGet Package Manager is included with all editions of Visual Studio starting with Visual Studio 2012.</span></span> <span data-ttu-id="5cfec-115">在 Visual Studio 的“工具菜单”中，找到“NuGet 包管理器” 。</span><span class="sxs-lookup"><span data-stu-id="5cfec-115">Look for **NuGet Package Manager** on the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="5cfec-116">如果未安装，请按照[安装 NuGet](/nuget/install-nuget-client-tools) 上的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="5cfec-116">If it's not installed, follow the instructions on [Installing NuGet](/nuget/install-nuget-client-tools).</span></span> <span data-ttu-id="5cfec-117">有关 NuGet 的详细信息，请参阅 [NuGet 文档](/nuget)。</span><span class="sxs-lookup"><span data-stu-id="5cfec-117">For more information about NuGet, see the [NuGet docs](/nuget).</span></span>

## <a name="use-a-nuget-oob-package"></a><span data-ttu-id="5cfec-118">使用 NuGet OOB 包</span><span class="sxs-lookup"><span data-stu-id="5cfec-118">Use a NuGet OOB package</span></span>

<span data-ttu-id="5cfec-119">如果 NuGet 包管理器已安装，你可使用 Visual Studio 中的解决方案资源管理器浏览并添加对 NuGet 包的引用：</span><span class="sxs-lookup"><span data-stu-id="5cfec-119">If NuGet Package Manager is installed, you can browse and add references to NuGet packages by using Solution Explorer in Visual Studio:</span></span>

1. <span data-ttu-id="5cfec-120">在 Visual Studio 中打开项目的快捷菜单，然后选择“管理 NuGet 包”。</span><span class="sxs-lookup"><span data-stu-id="5cfec-120">Open the shortcut menu for your project in Visual Studio, and then choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="5cfec-121">（也可以在“项目”菜单中选择此选项。）</span><span class="sxs-lookup"><span data-stu-id="5cfec-121">(This option is also available from the **Project** menu.)</span></span>

2. <span data-ttu-id="5cfec-122">在左侧窗格中，选择“联机”。</span><span class="sxs-lookup"><span data-stu-id="5cfec-122">In the left pane, choose **Online**.</span></span>

3. <span data-ttu-id="5cfec-123">如果要使用预发行包，请选择中间窗格内下拉列表框中的“包括预发行版”（而不选择“仅限稳定版”）。</span><span class="sxs-lookup"><span data-stu-id="5cfec-123">If you want to use prerelease packages, in the drop-down list box in the middle pane, choose **Include Prerelease** instead of **Stable Only**.</span></span>

4. <span data-ttu-id="5cfec-124">在右侧窗格中，使用“搜索”框来查找要使用的包。</span><span class="sxs-lookup"><span data-stu-id="5cfec-124">In the right pane, use the **Search** box to locate the package you would like to use.</span></span> <span data-ttu-id="5cfec-125">某些 Microsoft 程序包通过 Microsoft .NET Framework 徽标进行识别，发布者均为 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="5cfec-125">Some Microsoft packages are identified by the Microsoft .NET Framework logo, and all identify Microsoft as the publisher.</span></span>

![NuGet 包管理器。](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

<span data-ttu-id="5cfec-127">如前所述，当你部署使用了 OOB 包的应用程序，OOB 程序集将随附你的应用程序包。</span><span class="sxs-lookup"><span data-stu-id="5cfec-127">As mentioned previously, when you deploy an app that uses an OOB package, the OOB assemblies will ship with your app package.</span></span>

## <a name="types-of-oob-releases"></a><span data-ttu-id="5cfec-128">OOB 版本的类型</span><span class="sxs-lookup"><span data-stu-id="5cfec-128">Types of OOB releases</span></span>

<span data-ttu-id="5cfec-129">通常情况下，OOB 程序包具有一个或多个预发行版本和一个稳定的版本。</span><span class="sxs-lookup"><span data-stu-id="5cfec-129">Typically, an OOB package has one or more prerelease versions and a stable version.</span></span> <span data-ttu-id="5cfec-130">预发行附带的许可证通常不允许再发行，但可让你试用程序包并提供反馈。</span><span class="sxs-lookup"><span data-stu-id="5cfec-130">The license that accompanies a prerelease doesn't typically allow redistribution, but enables you to try out a package and provide feedback.</span></span> <span data-ttu-id="5cfec-131">任何对包的更新中都包含反馈。</span><span class="sxs-lookup"><span data-stu-id="5cfec-131">Feedback is incorporated in any updates made to the package.</span></span> <span data-ttu-id="5cfec-132">最终发布版本作为稳定的包随 NuGet 分发并包含允许随应用程序重新分发 NuGet 程序包的许可证。</span><span class="sxs-lookup"><span data-stu-id="5cfec-132">A final release is distributed as a stable package with NuGet and includes a license that lets you redistribute the NuGet package with your app.</span></span> <span data-ttu-id="5cfec-133">稳定程序包受 Microsoft 支持。</span><span class="sxs-lookup"><span data-stu-id="5cfec-133">Stable packages are supported by Microsoft.</span></span> <span data-ttu-id="5cfec-134">Microsoft 还提供 IntelliSense 支持以及其他文档类型（如所有程序包的博客文章和论坛答案）。</span><span class="sxs-lookup"><span data-stu-id="5cfec-134">Microsoft provides IntelliSense support as well as other types of documentation such as blog posts and forum answers for all packages.</span></span> <span data-ttu-id="5cfec-135">此外，只有一些程序包可使用源代码，并非所有程序包都可使用。</span><span class="sxs-lookup"><span data-stu-id="5cfec-135">In addition, source code may be available with some, but not all, packages.</span></span> <span data-ttu-id="5cfec-136">有关新增和更新后的包的公告，可订阅 [.NET Framework 博客](https://devblogs.microsoft.com/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="5cfec-136">For announcements regarding new and updated packages, you can subscribe to [the .NET Framework Blog](https://devblogs.microsoft.com/dotnet/).</span></span>

<span data-ttu-id="5cfec-137">若要查找预发行版包和稳定版包，请在 NuGet 包管理器中选择“包括预发行版”。</span><span class="sxs-lookup"><span data-stu-id="5cfec-137">To find both prerelease and stable packages, choose **Include Prerelease** in NuGet Package Manager.</span></span>

## <a name="see-also"></a><span data-ttu-id="5cfec-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="5cfec-138">See also</span></span>

- [<span data-ttu-id="5cfec-139">入门</span><span class="sxs-lookup"><span data-stu-id="5cfec-139">Getting started</span></span>](index.md)
