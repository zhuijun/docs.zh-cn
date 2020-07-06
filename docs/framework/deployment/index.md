---
title: 部署 .NET Framework 和应用程序
description: 开始随应用程序部署 .NET。 .NET 提供不受影响的应用程序、默认情况下的专用组件和可控的代码共享等功能。
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
ms.openlocfilehash: cce888c962c9ab83c13cce4040eb9ba50270972d
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803491"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="45714-104">部署 .NET Framework 和应用程序</span><span class="sxs-lookup"><span data-stu-id="45714-104">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="45714-105">本文有助于你开始部署应用程序的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="45714-105">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="45714-106">大部分信息都是供开发人员、OEM 和企业管理人员使用的。</span><span class="sxs-lookup"><span data-stu-id="45714-106">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="45714-107">想在其自己的计算机上安装 .NET Framework 的用户应阅读[安装 .NET Framework](../install/index.md)。</span><span class="sxs-lookup"><span data-stu-id="45714-107">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="45714-108">关键部署资源</span><span class="sxs-lookup"><span data-stu-id="45714-108">Key Deployment Resources</span></span>

<span data-ttu-id="45714-109">使用以下指向启用 MSDN 主题的链接了解关于部署和维护 .NET Framework 的特定信息。</span><span class="sxs-lookup"><span data-stu-id="45714-109">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="45714-110">**安装和部署**</span><span class="sxs-lookup"><span data-stu-id="45714-110">**Setup and deployment**</span></span>

- <span data-ttu-id="45714-111">安装程序和部署的一般信息：</span><span class="sxs-lookup"><span data-stu-id="45714-111">General installer and deployment information:</span></span>

  - <span data-ttu-id="45714-112">安装程序选项：</span><span class="sxs-lookup"><span data-stu-id="45714-112">Installer options:</span></span>

    - [<span data-ttu-id="45714-113">Web 安装程序</span><span class="sxs-lookup"><span data-stu-id="45714-113">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="45714-114">脱机安装程序</span><span class="sxs-lookup"><span data-stu-id="45714-114">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="45714-115">安装模式：</span><span class="sxs-lookup"><span data-stu-id="45714-115">Installation modes:</span></span>

    - [<span data-ttu-id="45714-116">无提示安装</span><span class="sxs-lookup"><span data-stu-id="45714-116">Silent installation</span></span>](deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="45714-117">显示 UI</span><span class="sxs-lookup"><span data-stu-id="45714-117">Displaying a UI</span></span>](deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="45714-118">在 .NET Framework 4.5 安装期间减少系统重新启动次数</span><span class="sxs-lookup"><span data-stu-id="45714-118">Reducing system restarts during .NET Framework 4.5 installations</span></span>](reducing-system-restarts.md)

  - [<span data-ttu-id="45714-119">安装和卸载 .NET Framework 受阻疑难解答</span><span class="sxs-lookup"><span data-stu-id="45714-119">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="45714-120">部署客户端应用程序中的 .NET Framework（适用于开发人员）：</span><span class="sxs-lookup"><span data-stu-id="45714-120">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="45714-121">在安装和部署项目中[使用 InstallShield](deployment-guide-for-developers.md#installshield-deployment)</span><span class="sxs-lookup"><span data-stu-id="45714-121">[Using InstallShield](deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="45714-122">使用 Visual Studio ClickOnce 应用程序</span><span class="sxs-lookup"><span data-stu-id="45714-122">Using a Visual Studio ClickOnce application</span></span>](deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="45714-123">创建 WiX 安装包</span><span class="sxs-lookup"><span data-stu-id="45714-123">Creating a WiX installation package</span></span>](deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="45714-124">使用自定义安装程序</span><span class="sxs-lookup"><span data-stu-id="45714-124">Using a custom installer</span></span>](deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="45714-125">适用于开发人员的[其他信息](deployment-guide-for-developers.md)</span><span class="sxs-lookup"><span data-stu-id="45714-125">[Additional information](deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="45714-126">部署.NET Framework（适用于 OEM 和管理人员）：</span><span class="sxs-lookup"><span data-stu-id="45714-126">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="45714-127">Windows 评估和部署工具包 (ADK)</span><span class="sxs-lookup"><span data-stu-id="45714-127">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [<span data-ttu-id="45714-128">管理员指南</span><span class="sxs-lookup"><span data-stu-id="45714-128">Administrator's guide</span></span>](guide-for-administrators.md)

<span data-ttu-id="45714-129">**服务**</span><span class="sxs-lookup"><span data-stu-id="45714-129">**Servicing**</span></span>

- <span data-ttu-id="45714-130">有关一般信息，请参阅 [.NET Framework 博客](https://devblogs.microsoft.com/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="45714-130">For general information, see the [.NET Framework blog](https://devblogs.microsoft.com/dotnet/).</span></span>

- [<span data-ttu-id="45714-131">检测版本</span><span class="sxs-lookup"><span data-stu-id="45714-131">Detecting versions</span></span>](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="45714-132">检测服务包和更新</span><span class="sxs-lookup"><span data-stu-id="45714-132">Detecting service packs and updates</span></span>](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="45714-133">简化部署的功能</span><span class="sxs-lookup"><span data-stu-id="45714-133">Features That Simplify Deployment</span></span>

<span data-ttu-id="45714-134">.NET Framework 提供了大量基本功能，让部署应用程序变得更加容易：</span><span class="sxs-lookup"><span data-stu-id="45714-134">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="45714-135">不产生影响的应用程序。</span><span class="sxs-lookup"><span data-stu-id="45714-135">No-impact applications.</span></span>

     <span data-ttu-id="45714-136">此功能提供应用程序隔离功能并消除 DLL 冲突。</span><span class="sxs-lookup"><span data-stu-id="45714-136">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="45714-137">默认情况下，组件不会影响其他应用程序。</span><span class="sxs-lookup"><span data-stu-id="45714-137">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="45714-138">默认情况下的私有组件。</span><span class="sxs-lookup"><span data-stu-id="45714-138">Private components by default.</span></span>

     <span data-ttu-id="45714-139">默认情况下，组件部署到应用程序目录，并且仅对包含的应用程序可见。</span><span class="sxs-lookup"><span data-stu-id="45714-139">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="45714-140">可控的代码共享。</span><span class="sxs-lookup"><span data-stu-id="45714-140">Controlled code sharing.</span></span>

     <span data-ttu-id="45714-141">代码共享要求你显式提供代码以便进行共享而不是执行默认行为。</span><span class="sxs-lookup"><span data-stu-id="45714-141">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="45714-142">并行版本。</span><span class="sxs-lookup"><span data-stu-id="45714-142">Side-by-side versioning.</span></span>

     <span data-ttu-id="45714-143">组件或应用程序的多个版本可以共存，你可以选择要使用的版本类型，公共语言运行时可以增强版本策略。</span><span class="sxs-lookup"><span data-stu-id="45714-143">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="45714-144">XCOPY 部署和复制。</span><span class="sxs-lookup"><span data-stu-id="45714-144">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="45714-145">在没有注册表项或依赖项的情况下就可以部署自描述和自持有的组件和应用程序。</span><span class="sxs-lookup"><span data-stu-id="45714-145">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="45714-146">动态更新。</span><span class="sxs-lookup"><span data-stu-id="45714-146">On-the-fly updates.</span></span>

     <span data-ttu-id="45714-147">管理员可以使用宿主（例如，ASP.NET）更新程序 Dll，即使在远程计算机也可以。</span><span class="sxs-lookup"><span data-stu-id="45714-147">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="45714-148">与 Windows 安装程序相集成。</span><span class="sxs-lookup"><span data-stu-id="45714-148">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="45714-149">部署应用程序时，播发、发布、修复和按需安装都可用。</span><span class="sxs-lookup"><span data-stu-id="45714-149">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="45714-150">企业部署。</span><span class="sxs-lookup"><span data-stu-id="45714-150">Enterprise deployment.</span></span>

     <span data-ttu-id="45714-151">此功能提供了简单的软件分发，包括使用 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="45714-151">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="45714-152">下载和缓存。</span><span class="sxs-lookup"><span data-stu-id="45714-152">Downloading and caching.</span></span>

     <span data-ttu-id="45714-153">增量下载可使下载大小变得更小，并且组件可以相互隔离，使其只供部署影响较低的应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="45714-153">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="45714-154">部分受信任代码。</span><span class="sxs-lookup"><span data-stu-id="45714-154">Partially trusted code.</span></span>

     <span data-ttu-id="45714-155">标识是基于代码而不是基于用户，并且不会出现任何证书对话框。</span><span class="sxs-lookup"><span data-stu-id="45714-155">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="45714-156">打包和分发 .NET Framework 应用程序</span><span class="sxs-lookup"><span data-stu-id="45714-156">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="45714-157">文档中的其他章节介绍了打包和部署 .NET Framework 的部分信息。</span><span class="sxs-lookup"><span data-stu-id="45714-157">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="45714-158">这些章节介绍了以下关于自描述单元的信息：[程序集](../../standard/assembly/index.md)（不需要注册表项）、[强名称程序集](../../standard/assembly/strong-named.md)（确保名称的唯一性和避免名称欺骗）和[程序集版本控制](../../standard/assembly/versioning.md)（可解决很多与 DLL 冲突相关的问题）。</span><span class="sxs-lookup"><span data-stu-id="45714-158">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="45714-159">以下各节提供有关打包和分发.NET Framework 应用程序的信息。</span><span class="sxs-lookup"><span data-stu-id="45714-159">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="45714-160">打包</span><span class="sxs-lookup"><span data-stu-id="45714-160">Packaging</span></span>

<span data-ttu-id="45714-161">.NET Framework 提供了用于打包应用程序的以下选项：</span><span class="sxs-lookup"><span data-stu-id="45714-161">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="45714-162">作为单个程序集或作为程序集的集合。</span><span class="sxs-lookup"><span data-stu-id="45714-162">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="45714-163">使用此选项，你只需使用创建的 .dll 或 .exe 文件即可。</span><span class="sxs-lookup"><span data-stu-id="45714-163">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="45714-164">作为 cabinet (CAB) 文件。</span><span class="sxs-lookup"><span data-stu-id="45714-164">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="45714-165">使用此选项，将文件压缩成 .cab 文件可使分发或下载耗时更少。</span><span class="sxs-lookup"><span data-stu-id="45714-165">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="45714-166">为 Windows Installer 程序包或其他安装程序格式。</span><span class="sxs-lookup"><span data-stu-id="45714-166">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="45714-167">使用此选项，你可以创建用于 Windows Installer 的 .msi 文件或打包用于其他安装程序的应用程序。</span><span class="sxs-lookup"><span data-stu-id="45714-167">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="45714-168">分布</span><span class="sxs-lookup"><span data-stu-id="45714-168">Distribution</span></span>

<span data-ttu-id="45714-169">.NET Framework 提供了用于分发应用程序的以下选项：</span><span class="sxs-lookup"><span data-stu-id="45714-169">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="45714-170">使用 XCOPY 或 FTP。</span><span class="sxs-lookup"><span data-stu-id="45714-170">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="45714-171">由于公共语言运行时应用程序是自描述的并且不需要注册表项，因此，你可以使用 XCOPY 或 FTP 只将应用程序复制到相应的目录。</span><span class="sxs-lookup"><span data-stu-id="45714-171">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="45714-172">然后即可从该目录运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="45714-172">The application can then be run from that directory.</span></span>

- <span data-ttu-id="45714-173">使用代码下载。</span><span class="sxs-lookup"><span data-stu-id="45714-173">Use code download.</span></span>

     <span data-ttu-id="45714-174">如果你要通过 Internet 或公司的 Intranet 分发应用程序，只需将代码下载到计算机并在下载位置运行应用程序即可。</span><span class="sxs-lookup"><span data-stu-id="45714-174">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="45714-175">使用安装程序（例如 Windows Installer 2.0）。</span><span class="sxs-lookup"><span data-stu-id="45714-175">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="45714-176">Windows Installer 2.0 可以安装、修复或删除全局程序集缓存和专用目录中的 .NET Framework 程序集。</span><span class="sxs-lookup"><span data-stu-id="45714-176">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="45714-177">安装位置</span><span class="sxs-lookup"><span data-stu-id="45714-177">Installation Location</span></span>

<span data-ttu-id="45714-178">要确定部署应用程序的程序集的位置，以便通过运行时找到它们，请参阅[运行时如何定位程序集](how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="45714-178">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="45714-179">安全注意事项也可能会影响你部署应用程序的方式。</span><span class="sxs-lookup"><span data-stu-id="45714-179">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="45714-180">根据代码所在的位置授予托管代码安全权限。</span><span class="sxs-lookup"><span data-stu-id="45714-180">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="45714-181">将应用程序或组件部署到得不到信任的位置（例如 Internet），可限制应用程序或组件可以执行的操作。</span><span class="sxs-lookup"><span data-stu-id="45714-181">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="45714-182">有关部署和安全注意事项的详细信息，请参阅[代码访问安全性基础知识](../misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="45714-182">For more information about deployment and security considerations, see [Code Access Security Basics](../misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="45714-183">相关主题</span><span class="sxs-lookup"><span data-stu-id="45714-183">Related Topics</span></span>

|<span data-ttu-id="45714-184">Title</span><span class="sxs-lookup"><span data-stu-id="45714-184">Title</span></span>|<span data-ttu-id="45714-185">描述</span><span class="sxs-lookup"><span data-stu-id="45714-185">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="45714-186">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="45714-186">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)|<span data-ttu-id="45714-187">描述公共语言运行时如何确定将用于满足绑定请求的程序集类型。</span><span class="sxs-lookup"><span data-stu-id="45714-187">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="45714-188">适用于程序集加载的最佳做法</span><span class="sxs-lookup"><span data-stu-id="45714-188">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)|<span data-ttu-id="45714-189">讨论避免类型标识问题的方法，从而避免发生 <xref:System.InvalidCastException><xref:System.MissingMethodException> 和其他错误。</span><span class="sxs-lookup"><span data-stu-id="45714-189">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="45714-190">在 .NET Framework 4.5 安装期间减少系统重新启动次数</span><span class="sxs-lookup"><span data-stu-id="45714-190">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)|<span data-ttu-id="45714-191">描述在任何可能的情况下可以阻止重启的 Restart Manager，并说明安装 .NET Framework 的应用程序如何利用它。</span><span class="sxs-lookup"><span data-stu-id="45714-191">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="45714-192">面向管理员的部署指南</span><span class="sxs-lookup"><span data-stu-id="45714-192">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)|<span data-ttu-id="45714-193">说明系统管理员如何通过 Microsoft Endpoint Configuration Manager 跨网络部署 .NET Framework 及其系统依赖项。</span><span class="sxs-lookup"><span data-stu-id="45714-193">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>|
|[<span data-ttu-id="45714-194">面向开发人员的部署指南</span><span class="sxs-lookup"><span data-stu-id="45714-194">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)|<span data-ttu-id="45714-195">说明开发人员如何在其计算机的应用程序中安装 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="45714-195">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="45714-196">部署应用程序、服务和组件</span><span class="sxs-lookup"><span data-stu-id="45714-196">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="45714-197">讨论 Visual Studio 中的部署选项，包括使用 ClickOnce 和 Windows Installer 技术发布应用程序的说明。</span><span class="sxs-lookup"><span data-stu-id="45714-197">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="45714-198">发布 ClickOnce 应用程序</span><span class="sxs-lookup"><span data-stu-id="45714-198">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="45714-199">描述打包 Windows 窗体应用程序以及使用 ClickOnce 将其部署到连网的客户端计算机上的方法。</span><span class="sxs-lookup"><span data-stu-id="45714-199">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="45714-200">打包和部署资源</span><span class="sxs-lookup"><span data-stu-id="45714-200">Packaging and Deploying Resources</span></span>](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="45714-201">描述 .NET Framework 用于打包和部署资源的中心辐射模型，包括资源命名约定、后备进程和打包替代项。</span><span class="sxs-lookup"><span data-stu-id="45714-201">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="45714-202">部署互操作应用程序</span><span class="sxs-lookup"><span data-stu-id="45714-202">Deploying an Interop Application</span></span>](../interop/deploying-an-interop-application.md)|<span data-ttu-id="45714-203">说明如何传送和安装互操作应用程序，通常包括 .NET Framework 客户端程序集、表示区分 COM 类型库的一个或多个互操作程序集以及一个或多个已注册的 COM 组件。</span><span class="sxs-lookup"><span data-stu-id="45714-203">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="45714-204">如何：获取 .NET Framework 4.5 安装程序的进度</span><span class="sxs-lookup"><span data-stu-id="45714-204">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="45714-205">描述如何在没有提示的情况下启动和跟踪 .NET Framework 安装进度，同时显示你自己的安装进度视图。</span><span class="sxs-lookup"><span data-stu-id="45714-205">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="45714-206">请参阅</span><span class="sxs-lookup"><span data-stu-id="45714-206">See also</span></span>

- [<span data-ttu-id="45714-207">开发指南</span><span class="sxs-lookup"><span data-stu-id="45714-207">Development Guide</span></span>](../development-guide.md)
