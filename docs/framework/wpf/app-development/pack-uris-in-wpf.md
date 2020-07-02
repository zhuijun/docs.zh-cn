---
title: 包 Uri
description: 了解使用统一资源标识符（Uri）来标识和加载 Windows Presentation Foundation （WPF）中的文件的多种方法。
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 1d19dec0d846659f8de6ed518a7f98d224354a82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621686"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="b31d5-103">WPF 中的 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-103">Pack URIs in WPF</span></span>

<span data-ttu-id="b31d5-104">在 Windows Presentation Foundation （WPF）中，统一资源标识符（Uri）用于通过多种方式标识和加载文件，其中包括：</span><span class="sxs-lookup"><span data-stu-id="b31d5-104">In Windows Presentation Foundation (WPF), uniform resource identifiers (URIs) are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="b31d5-105">指定 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 以显示应用程序第一次启动的时间。</span><span class="sxs-lookup"><span data-stu-id="b31d5-105">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="b31d5-106">加载图像。</span><span class="sxs-lookup"><span data-stu-id="b31d5-106">Loading images.</span></span>

- <span data-ttu-id="b31d5-107">导航到页。</span><span class="sxs-lookup"><span data-stu-id="b31d5-107">Navigating to pages.</span></span>

- <span data-ttu-id="b31d5-108">加载不可执行的数据文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-108">Loading non-executable data files.</span></span>

<span data-ttu-id="b31d5-109">此外，可以使用 Uri 来标识和加载来自各种位置的文件，包括以下各项：</span><span class="sxs-lookup"><span data-stu-id="b31d5-109">Furthermore, URIs can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="b31d5-110">当前程序集。</span><span class="sxs-lookup"><span data-stu-id="b31d5-110">The current assembly.</span></span>

- <span data-ttu-id="b31d5-111">引用的程序集。</span><span class="sxs-lookup"><span data-stu-id="b31d5-111">A referenced assembly.</span></span>

- <span data-ttu-id="b31d5-112">相对于程序集的某个位置。</span><span class="sxs-lookup"><span data-stu-id="b31d5-112">A location relative to an assembly.</span></span>

- <span data-ttu-id="b31d5-113">应用程序的源站点。</span><span class="sxs-lookup"><span data-stu-id="b31d5-113">The application's site of origin.</span></span>

<span data-ttu-id="b31d5-114">为了提供用于从这些位置标识和加载这些类型的文件的一致机制，WPF 利用了*PACK URI 方案*的扩展性。</span><span class="sxs-lookup"><span data-stu-id="b31d5-114">To provide a consistent mechanism for identifying and loading these types of files from these locations, WPF leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="b31d5-115">本主题概述了方案，并介绍了如何为各种方案构造包 Uri，以及如何在显示如何使用标记和代码中的 pack Uri 之前介绍绝对和相对 Uri 以及 URI 解析。</span><span class="sxs-lookup"><span data-stu-id="b31d5-115">This topic provides an overview of the scheme, covers how to construct pack URIs for a variety of scenarios, discusses absolute and relative URIs and URI resolution, before showing how to use pack URIs from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="b31d5-116">Pack URI 方案</span><span class="sxs-lookup"><span data-stu-id="b31d5-116">The Pack URI Scheme</span></span>

<span data-ttu-id="b31d5-117">Pack URI 方案由[开放式打包约定](https://www.ecma-international.org/publications/standards/Ecma-376.htm)（OPC）规范使用，此规范描述了用于组织和标识内容的模型。</span><span class="sxs-lookup"><span data-stu-id="b31d5-117">The pack URI scheme is used by the [Open Packaging Conventions](https://www.ecma-international.org/publications/standards/Ecma-376.htm) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="b31d5-118">此模型的关键元素是包和部件，其中，*包*是一个或多个逻辑*部分*的逻辑容器。</span><span class="sxs-lookup"><span data-stu-id="b31d5-118">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="b31d5-119">下图阐释了此概念。</span><span class="sxs-lookup"><span data-stu-id="b31d5-119">The following figure illustrates this concept.</span></span>

![包和部件示意图](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="b31d5-121">为了识别部件，OPC 规范利用了 RFC 2396 （统一资源标识符（URI）：通用语法）的扩展性来定义 pack URI 方案。</span><span class="sxs-lookup"><span data-stu-id="b31d5-121">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack URI scheme.</span></span>

<span data-ttu-id="b31d5-122">由 URI 指定的方案由其前缀定义;http、ftp 和 file 是众所周知的示例。</span><span class="sxs-lookup"><span data-stu-id="b31d5-122">The scheme that is specified by a URI is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="b31d5-123">Pack URI 方案使用 "pack" 作为其方案，并且包含两个组件：颁发机构和路径。</span><span class="sxs-lookup"><span data-stu-id="b31d5-123">The pack URI scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="b31d5-124">下面是 pack URI 的格式。</span><span class="sxs-lookup"><span data-stu-id="b31d5-124">The following is the format for a pack URI.</span></span>

<span data-ttu-id="b31d5-125">pack://*机构* / *路径*</span><span class="sxs-lookup"><span data-stu-id="b31d5-125">pack://*authority*/*path*</span></span>

<span data-ttu-id="b31d5-126">*颁发机构*指定包含部件的包类型，而*路径*指定部件在包中的位置。</span><span class="sxs-lookup"><span data-stu-id="b31d5-126">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="b31d5-127">下图阐释了此概念：</span><span class="sxs-lookup"><span data-stu-id="b31d5-127">This concept is illustrated by the following figure:</span></span>

![包、颁发机构与路径之间的关系](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="b31d5-129">包和部件之间的关系类似于应用程序和文件之间的关系，其中应用程序（包）可以包含一个或多个文件（部件），包括：</span><span class="sxs-lookup"><span data-stu-id="b31d5-129">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="b31d5-130">编译到本地程序集内的资源文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-130">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="b31d5-131">编译到所引用的程序集内的资源文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-131">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="b31d5-132">编译到引用程序集内的资源文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-132">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="b31d5-133">内容文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-133">Content files.</span></span>

- <span data-ttu-id="b31d5-134">源站点文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-134">Site of origin files.</span></span>

<span data-ttu-id="b31d5-135">为了访问这些类型的文件，WPF 支持两个权限： application:///和 siteoforigin:///。</span><span class="sxs-lookup"><span data-stu-id="b31d5-135">To access these types of files, WPF supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="b31d5-136">application:/// 授权标识在编译时已知的应用程序数据文件，包括资源文件和内容文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-136">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="b31d5-137">siteoforigin:/// 授权标识源站点文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-137">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="b31d5-138">下图显示了每种授权的范围。</span><span class="sxs-lookup"><span data-stu-id="b31d5-138">The scope of each authority is shown in the following figure.</span></span>

![Pack URI 示意图](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="b31d5-140">包 URI 的颁发机构组件是一个指向包并必须符合 RFC 2396 的嵌入 URI。</span><span class="sxs-lookup"><span data-stu-id="b31d5-140">The authority component of a pack URI is an embedded URI that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="b31d5-141">另外，必须用字符“,”替换字符“/”，并且必须对保留字符（如“%”和“?”）进行转义。</span><span class="sxs-lookup"><span data-stu-id="b31d5-141">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="b31d5-142">有关详细信息，请参阅 OPC。</span><span class="sxs-lookup"><span data-stu-id="b31d5-142">See the OPC for details.</span></span>

<span data-ttu-id="b31d5-143">以下各节说明如何使用这两个颁发机构构造包 Uri 以及用于标识资源、内容和源站点文件的相应路径。</span><span class="sxs-lookup"><span data-stu-id="b31d5-143">The following sections explain how to construct pack URIs using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="b31d5-144">资源文件 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-144">Resource File Pack URIs</span></span>

<span data-ttu-id="b31d5-145">资源文件配置为 MSBuild `Resource` 项并编译为程序集。</span><span class="sxs-lookup"><span data-stu-id="b31d5-145">Resource files are configured as MSBuild `Resource` items and are compiled into assemblies.</span></span> <span data-ttu-id="b31d5-146">WPF 支持构造包 Uri，这些 Uri 可用于标识编译到本地程序集中或编译到从本地程序集引用的程序集中的资源文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-146">WPF supports the construction of pack URIs that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="b31d5-147">本地程序集资源文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-147">Local Assembly Resource File</span></span>

<span data-ttu-id="b31d5-148">编译到本地程序集的资源文件的 pack URI 使用以下授权和路径：</span><span class="sxs-lookup"><span data-stu-id="b31d5-148">The pack URI for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="b31d5-149">**授权**：application:///。</span><span class="sxs-lookup"><span data-stu-id="b31d5-149">**Authority**: application:///.</span></span>

- <span data-ttu-id="b31d5-150">**路径**：资源文件的名称，包括其相对于本地程序集项目文件夹根目录的路径。</span><span class="sxs-lookup"><span data-stu-id="b31d5-150">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="b31d5-151">下面的示例演示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 位于本地程序集的项目文件夹的根目录中的资源文件的 PACK URI。</span><span class="sxs-lookup"><span data-stu-id="b31d5-151">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="b31d5-152">下面的示例演示一个资源文件的 pack URI [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，该资源文件位于本地程序集的项目文件夹的子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b31d5-152">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="b31d5-153">引用的程序集资源文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-153">Referenced Assembly Resource File</span></span>

<span data-ttu-id="b31d5-154">编译到引用的程序集中的资源文件的 pack URI 使用以下授权和路径：</span><span class="sxs-lookup"><span data-stu-id="b31d5-154">The pack URI for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="b31d5-155">**授权**：application:///。</span><span class="sxs-lookup"><span data-stu-id="b31d5-155">**Authority**: application:///.</span></span>

- <span data-ttu-id="b31d5-156">**路径**：编译到所引用程序集内的资源文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b31d5-156">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="b31d5-157">路径必须符合以下格式：</span><span class="sxs-lookup"><span data-stu-id="b31d5-157">The path must conform to the following format:</span></span>

  <span data-ttu-id="b31d5-158">*AssemblyShortName*{*;版本*] {*;PublicKey*]; 组件/*路径*</span><span class="sxs-lookup"><span data-stu-id="b31d5-158">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="b31d5-159">**程序集短名称**：所引用的程序集的短名称。</span><span class="sxs-lookup"><span data-stu-id="b31d5-159">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="b31d5-160">**;版本** [可选]：所引用的包含资源文件的程序集的版本。</span><span class="sxs-lookup"><span data-stu-id="b31d5-160">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="b31d5-161">此部分在加载两个或多个具有相同短名称的引用程序集时使用。</span><span class="sxs-lookup"><span data-stu-id="b31d5-161">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="b31d5-162">**;公钥** [可选]：用于对引用程序集进行签名的公钥。</span><span class="sxs-lookup"><span data-stu-id="b31d5-162">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="b31d5-163">此部分在加载两个或多个具有相同短名称的引用程序集时使用。</span><span class="sxs-lookup"><span data-stu-id="b31d5-163">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="b31d5-164">**;组件**：指定所引用的程序集是从本地程序集引用的。</span><span class="sxs-lookup"><span data-stu-id="b31d5-164">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="b31d5-165">**/路径**：资源文件的名称，包括其相对于所引用程序集的项目文件夹根目录的路径。</span><span class="sxs-lookup"><span data-stu-id="b31d5-165">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="b31d5-166">下面的示例演示一个资源文件的 pack URI [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，该资源文件位于所引用程序集的项目文件夹的根目录中。</span><span class="sxs-lookup"><span data-stu-id="b31d5-166">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="b31d5-167">下面的示例演示一个资源文件的 pack URI [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，该资源文件位于所引用程序集的项目文件夹的子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b31d5-167">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="b31d5-168">下面的示例演示一个资源文件的 pack URI，该 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 资源文件位于所引用的特定于版本的程序集的项目文件夹的根文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b31d5-168">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="b31d5-169">请注意，所引用的程序集资源文件的 pack URI 语法只能与 application:///机构一起使用。</span><span class="sxs-lookup"><span data-stu-id="b31d5-169">Note that the pack URI syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="b31d5-170">例如，WPF 不支持以下。</span><span class="sxs-lookup"><span data-stu-id="b31d5-170">For example, the following is not supported in WPF.</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="b31d5-171">内容文件 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-171">Content File Pack URIs</span></span>

<span data-ttu-id="b31d5-172">内容文件的 pack URI 使用以下授权和路径：</span><span class="sxs-lookup"><span data-stu-id="b31d5-172">The pack URI for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="b31d5-173">**授权**：application:///。</span><span class="sxs-lookup"><span data-stu-id="b31d5-173">**Authority**: application:///.</span></span>

- <span data-ttu-id="b31d5-174">**路径**：内容文件的名称，包括其相对于应用程序的主可执行程序集的文件系统位置的路径。</span><span class="sxs-lookup"><span data-stu-id="b31d5-174">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="b31d5-175">下面的示例演示一个内容文件的 pack URI [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，该内容文件与可执行程序集位于同一文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b31d5-175">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="b31d5-176">下面的示例演示一个内容文件的 pack URI [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，该内容文件位于相对于应用程序的可执行程序集的子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b31d5-176">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="b31d5-177">不能导航到 HTML 内容文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-177">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="b31d5-178">URI 方案仅支持导航到位于源站点的 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-178">The URI scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="b31d5-179">源站点 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-179">Site of Origin Pack URIs</span></span>

<span data-ttu-id="b31d5-180">源站点文件的 pack URI 使用以下授权和路径：</span><span class="sxs-lookup"><span data-stu-id="b31d5-180">The pack URI for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="b31d5-181">**授权**：siteoforigin:///。</span><span class="sxs-lookup"><span data-stu-id="b31d5-181">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="b31d5-182">**路径**：源站点文件的名称，包括其相对于可执行程序集启动位置的路径。</span><span class="sxs-lookup"><span data-stu-id="b31d5-182">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="b31d5-183">下面的示例演示了 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 源站点文件的 PACK URI，该站点存储在可执行程序集所在的位置。</span><span class="sxs-lookup"><span data-stu-id="b31d5-183">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="b31d5-184">下面的示例演示了 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 源站点文件的 PACK URI，该站点存储在相对于从中启动应用程序的可执行程序集的位置的子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b31d5-184">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="b31d5-185">页面文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-185">Page Files</span></span>

<span data-ttu-id="b31d5-186">配置为 MSBuild 项的 XAML 文件 `Page` 将以与资源文件相同的方式编译到程序集中。</span><span class="sxs-lookup"><span data-stu-id="b31d5-186">XAML files that are configured as MSBuild `Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="b31d5-187">因此， `Page` 可以使用资源文件的 Pack uri 来标识 MSBuild 项。</span><span class="sxs-lookup"><span data-stu-id="b31d5-187">Consequently, MSBuild `Page` items can be identified using pack URIs for resource files.</span></span>

<span data-ttu-id="b31d5-188">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]通常配置为 MSBuild 项的文件类型 `Page` 具有以下项之一作为其根元素：</span><span class="sxs-lookup"><span data-stu-id="b31d5-188">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as MSBuild`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="b31d5-189">绝对和相对 Pack Uri</span><span class="sxs-lookup"><span data-stu-id="b31d5-189">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="b31d5-190">完全限定的 pack URI 包含方案、颁发机构和路径，并被视为绝对包 URI。</span><span class="sxs-lookup"><span data-stu-id="b31d5-190">A fully qualified pack URI includes the scheme, the authority, and the path, and it is considered an absolute pack URI.</span></span> <span data-ttu-id="b31d5-191">作为开发人员的简化， [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 元素通常允许使用相对 PACK URI 设置相应的属性，其中只包含路径。</span><span class="sxs-lookup"><span data-stu-id="b31d5-191">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack URI, which includes only the path.</span></span>

<span data-ttu-id="b31d5-192">例如，请考虑本地程序集中某个资源文件的以下绝对包 URI。</span><span class="sxs-lookup"><span data-stu-id="b31d5-192">For example, consider the following absolute pack URI for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="b31d5-193">引用此资源文件的相对 pack URI 如下所示。</span><span class="sxs-lookup"><span data-stu-id="b31d5-193">The relative pack URI that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="b31d5-194">由于源站点文件不与程序集相关联，因此只能用绝对包 Uri 来引用它们。</span><span class="sxs-lookup"><span data-stu-id="b31d5-194">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack URIs.</span></span>

<span data-ttu-id="b31d5-195">默认情况下，相对 pack URI 被视为相对于包含引用的标记或代码的位置。</span><span class="sxs-lookup"><span data-stu-id="b31d5-195">By default, a relative pack URI is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="b31d5-196">但是，如果使用前导反斜杠，则相对 pack URI 引用将被视为相对于应用程序的根。</span><span class="sxs-lookup"><span data-stu-id="b31d5-196">If a leading backslash is used, however, the relative pack URI reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="b31d5-197">例如，假设具有以下项目结构。</span><span class="sxs-lookup"><span data-stu-id="b31d5-197">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="b31d5-198">如果 Page1 包含引用*根*\SUBFOLDER\PAGE2.XAML 的 URI，则引用可以使用以下相对 pack URI。</span><span class="sxs-lookup"><span data-stu-id="b31d5-198">If Page1.xaml contains a URI that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`Page2.xaml`

<span data-ttu-id="b31d5-199">如果 Page1 包含引用*根*\PAGE2.XAML 的 URI，则引用可以使用以下相对 pack URI。</span><span class="sxs-lookup"><span data-stu-id="b31d5-199">If Page1.xaml contains a URI that references *Root*\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="b31d5-200">Pack URI 解析</span><span class="sxs-lookup"><span data-stu-id="b31d5-200">Pack URI Resolution</span></span>

<span data-ttu-id="b31d5-201">Pack Uri 的格式使得不同类型的文件的包 Uri 能够看起来相同。</span><span class="sxs-lookup"><span data-stu-id="b31d5-201">The format of pack URIs makes it possible for pack URIs for different types of files to look the same.</span></span> <span data-ttu-id="b31d5-202">例如，请考虑下面的绝对包 URI。</span><span class="sxs-lookup"><span data-stu-id="b31d5-202">For example, consider the following absolute pack URI.</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="b31d5-203">此绝对包 URI 可以引用本地程序集或内容文件中的资源文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-203">This absolute pack URI could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="b31d5-204">对于以下相对 URI 也是如此。</span><span class="sxs-lookup"><span data-stu-id="b31d5-204">The same is true for the following relative URI.</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="b31d5-205">为了确定 pack URI 引用的文件类型，WPF 使用以下试探法解析本地程序集中的资源文件和内容文件的 Uri：</span><span class="sxs-lookup"><span data-stu-id="b31d5-205">In order to determine the type of file that a pack URI refers to, WPF resolves URIs for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="b31d5-206">探测与 pack URI 匹配的属性的程序集元数据 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="b31d5-206">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack URI.</span></span>

2. <span data-ttu-id="b31d5-207">如果 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 找到该属性，则包 URI 的路径引用一个内容文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack URI refers to a content file.</span></span>

3. <span data-ttu-id="b31d5-208">如果 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 找不到该属性，则探测编译到本地程序集的资源文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-208">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="b31d5-209">如果找到与包 URI 的路径匹配的资源文件，则包 URI 的路径引用资源文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-209">If a resource file that matches the path of the pack URI is found, the path of the pack URI refers to a resource file.</span></span>

5. <span data-ttu-id="b31d5-210">如果找不到该资源，则内部创建的 <xref:System.Uri> 无效。</span><span class="sxs-lookup"><span data-stu-id="b31d5-210">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

<span data-ttu-id="b31d5-211">URI 解析不适用于引用以下各项的 Uri：</span><span class="sxs-lookup"><span data-stu-id="b31d5-211">URI resolution does not apply for URIs that refer to the following:</span></span>

- <span data-ttu-id="b31d5-212">引用的程序集中的内容文件： WPF 不支持这些文件类型。</span><span class="sxs-lookup"><span data-stu-id="b31d5-212">Content files in referenced assemblies: these file types are not supported by WPF.</span></span>

- <span data-ttu-id="b31d5-213">引用的程序集中的嵌入文件：标识这些文件的 Uri 是唯一的，因为它们包括引用的程序集的名称和 `;component` 后缀。</span><span class="sxs-lookup"><span data-stu-id="b31d5-213">Embedded files in referenced assemblies: URIs that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="b31d5-214">源站点文件：标识它们的 Uri 是唯一的，因为它们是可以由包含 siteoforigin:///机构的 pack Uri 标识的唯一文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-214">Site of origin files: URIs that identify them are unique because they are the only files that can be identified by pack URIs that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="b31d5-215">Pack URI 解析可以通过一种简化来使代码在一定程度上独立于资源和内容文件的位置。</span><span class="sxs-lookup"><span data-stu-id="b31d5-215">One simplification that pack URI resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="b31d5-216">例如，如果本地程序集中有一个资源文件，该文件已重新配置为内容文件，则该资源的 pack URI 将保持不变，这与使用包 URI 的代码一样。</span><span class="sxs-lookup"><span data-stu-id="b31d5-216">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack URI for the resource remains the same, as does the code that uses the pack URI.</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="b31d5-217">使用 Pack URI 编程</span><span class="sxs-lookup"><span data-stu-id="b31d5-217">Programming with Pack URIs</span></span>

<span data-ttu-id="b31d5-218">许多 WPF 类实现可通过 pack Uri 进行设置的属性，包括：</span><span class="sxs-lookup"><span data-stu-id="b31d5-218">Many WPF classes implement properties that can be set with pack URIs, including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="b31d5-219">可以从标记和代码中设置这些属性。</span><span class="sxs-lookup"><span data-stu-id="b31d5-219">These properties can be set from both markup and code.</span></span> <span data-ttu-id="b31d5-220">本节演示这两种设置方式的基本构造，然后演示通用方案示例。</span><span class="sxs-lookup"><span data-stu-id="b31d5-220">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="b31d5-221">在标记中使用 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-221">Using Pack URIs in Markup</span></span>

<span data-ttu-id="b31d5-222">通过使用 pack URI 设置特性的元素，在标记中指定包 URI。</span><span class="sxs-lookup"><span data-stu-id="b31d5-222">A pack URI is specified in markup by setting the element of an attribute with the pack URI.</span></span> <span data-ttu-id="b31d5-223">例如：</span><span class="sxs-lookup"><span data-stu-id="b31d5-223">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="b31d5-224">表1说明了可在标记中指定的各种绝对包 Uri。</span><span class="sxs-lookup"><span data-stu-id="b31d5-224">Table 1 illustrates the various absolute pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="b31d5-225">表 1：标记中的绝对 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-225">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="b31d5-226">文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-226">File</span></span>|<span data-ttu-id="b31d5-227">绝对包 URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-227">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="b31d5-228">资源文件 - 本地程序集</span><span class="sxs-lookup"><span data-stu-id="b31d5-228">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="b31d5-229">子文件夹中的资源文件 - 本地程序集</span><span class="sxs-lookup"><span data-stu-id="b31d5-229">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="b31d5-230">资源文件 - 引用的程序集</span><span class="sxs-lookup"><span data-stu-id="b31d5-230">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="b31d5-231">所引用程序集的子文件夹中的资源文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-231">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="b31d5-232">所引用版本化程序集中的资源文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-232">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="b31d5-233">内容文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-233">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="b31d5-234">子文件夹中的内容文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-234">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="b31d5-235">源站点文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-235">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="b31d5-236">子文件夹中的源站点文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-236">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="b31d5-237">表2说明了可以在标记中指定的各种相对包 Uri。</span><span class="sxs-lookup"><span data-stu-id="b31d5-237">Table 2 illustrates the various relative pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="b31d5-238">表 2：标记中的相对 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-238">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="b31d5-239">文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-239">File</span></span>|<span data-ttu-id="b31d5-240">相对 pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-240">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="b31d5-241">本地程序集内的资源文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-241">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="b31d5-242">本地程序集的子文件夹中的资源文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-242">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="b31d5-243">所引用程序集内的资源文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-243">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="b31d5-244">所引用程序集的子文件夹中的资源文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-244">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="b31d5-245">内容文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-245">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="b31d5-246">子文件夹中的内容文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-246">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="b31d5-247">在代码中使用 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-247">Using Pack URIs in Code</span></span>

<span data-ttu-id="b31d5-248">通过实例化 <xref:System.Uri> 类并将包 uri 作为参数传递给构造函数，可以在代码中指定包 uri。</span><span class="sxs-lookup"><span data-stu-id="b31d5-248">You specify a pack URI in code by instantiating the <xref:System.Uri> class and passing the pack URI as a parameter to the constructor.</span></span> <span data-ttu-id="b31d5-249">以下示例就将此进行演示。</span><span class="sxs-lookup"><span data-stu-id="b31d5-249">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="b31d5-250">默认情况下， <xref:System.Uri> 类将 Pack uri 视为绝对 uri。</span><span class="sxs-lookup"><span data-stu-id="b31d5-250">By default, the <xref:System.Uri> class considers pack URIs to be absolute.</span></span> <span data-ttu-id="b31d5-251">因此，当 <xref:System.Uri> 使用相对 PACK URI 创建类的实例时，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="b31d5-251">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack URI.</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="b31d5-252">幸运的是， <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> <xref:System.Uri> 类构造函数的重载接受类型的参数， <xref:System.UriKind> 以允许您指定包 URI 是绝对的还是相对的。</span><span class="sxs-lookup"><span data-stu-id="b31d5-252">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack URI is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="b31d5-253">你应仅指定 <xref:System.UriKind.Absolute> 或 <xref:System.UriKind.Relative> 在你确定所提供的 pack URI 是另一个。</span><span class="sxs-lookup"><span data-stu-id="b31d5-253">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack URI is one or the other.</span></span> <span data-ttu-id="b31d5-254">如果你不知道所使用的 pack URI 的类型，例如当用户在运行时输入包 URI 时，请 <xref:System.UriKind.RelativeOrAbsolute> 改用。</span><span class="sxs-lookup"><span data-stu-id="b31d5-254">If you don't know the type of pack URI that is used, such as when a user enters a pack URI at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="b31d5-255">表3说明了可以使用在代码中指定的各种相对包 Uri <xref:System.Uri?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b31d5-255">Table 3 illustrates the various relative pack URIs that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b31d5-256">表 3：代码中的绝对 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-256">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="b31d5-257">文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-257">File</span></span>|<span data-ttu-id="b31d5-258">绝对包 URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-258">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="b31d5-259">资源文件 - 本地程序集</span><span class="sxs-lookup"><span data-stu-id="b31d5-259">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="b31d5-260">子文件夹中的资源文件 - 本地程序集</span><span class="sxs-lookup"><span data-stu-id="b31d5-260">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="b31d5-261">资源文件 - 引用的程序集</span><span class="sxs-lookup"><span data-stu-id="b31d5-261">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="b31d5-262">所引用程序集的子文件夹中的资源文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-262">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="b31d5-263">所引用版本化程序集中的资源文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-263">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="b31d5-264">内容文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-264">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="b31d5-265">子文件夹中的内容文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-265">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="b31d5-266">源站点文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-266">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="b31d5-267">子文件夹中的源站点文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-267">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="b31d5-268">表4说明了可以使用在代码中指定的各种相对包 Uri <xref:System.Uri?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b31d5-268">Table 4 illustrates the various relative pack URIs that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b31d5-269">表 4：代码中的相对 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-269">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="b31d5-270">文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-270">File</span></span>|<span data-ttu-id="b31d5-271">相对 pack URI</span><span class="sxs-lookup"><span data-stu-id="b31d5-271">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="b31d5-272">资源文件 - 本地程序集</span><span class="sxs-lookup"><span data-stu-id="b31d5-272">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="b31d5-273">子文件夹中的资源文件 - 本地程序集</span><span class="sxs-lookup"><span data-stu-id="b31d5-273">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="b31d5-274">资源文件 - 引用的程序集</span><span class="sxs-lookup"><span data-stu-id="b31d5-274">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="b31d5-275">子文件夹中的资源文件 - 引用的程序集</span><span class="sxs-lookup"><span data-stu-id="b31d5-275">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="b31d5-276">内容文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-276">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="b31d5-277">子文件夹中的内容文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-277">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="b31d5-278">常见 Pack URI 方案</span><span class="sxs-lookup"><span data-stu-id="b31d5-278">Common Pack URI Scenarios</span></span>

<span data-ttu-id="b31d5-279">前面几节讨论了如何构造包 Uri 来标识资源、内容和源站点文件。</span><span class="sxs-lookup"><span data-stu-id="b31d5-279">The preceding sections have discussed how to construct pack URIs to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="b31d5-280">在 WPF 中，可以通过多种方式使用这些构造，以下部分介绍了几种常见的用法。</span><span class="sxs-lookup"><span data-stu-id="b31d5-280">In WPF, these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="b31d5-281">指定当应用程序启动时显示的 UI</span><span class="sxs-lookup"><span data-stu-id="b31d5-281">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="b31d5-282"><xref:System.Windows.Application.StartupUri%2A>指定在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 启动 WPF 应用程序时要显示的第一个。</span><span class="sxs-lookup"><span data-stu-id="b31d5-282"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a WPF application is launched.</span></span> <span data-ttu-id="b31d5-283">对于独立应用程序， [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 可以是一个窗口，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="b31d5-283">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="b31d5-284">独立应用程序和 XAML 浏览器应用程序（Xbap）还可以将页指定为初始 UI，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="b31d5-284">Standalone applications and XAML browser applications (XBAPs) can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="b31d5-285">如果应用程序是独立的应用程序，并且使用指定了页面 <xref:System.Windows.Application.StartupUri%2A> ，则 WPF 会打开 <xref:System.Windows.Navigation.NavigationWindow> 以承载页面。</span><span class="sxs-lookup"><span data-stu-id="b31d5-285">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, WPF opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="b31d5-286">对于 Xbap，将在主机浏览器中显示页面。</span><span class="sxs-lookup"><span data-stu-id="b31d5-286">For XBAPs, the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="b31d5-287">导航到页面</span><span class="sxs-lookup"><span data-stu-id="b31d5-287">Navigating to a Page</span></span>

<span data-ttu-id="b31d5-288">下面的示例演示如何导航到页面。</span><span class="sxs-lookup"><span data-stu-id="b31d5-288">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="b31d5-289">有关在 WPF 中导航的各种方式的详细信息，请参阅[导航概述](navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b31d5-289">For more information on the various ways to navigate in WPF, see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="b31d5-290">指定窗口图标</span><span class="sxs-lookup"><span data-stu-id="b31d5-290">Specifying a Window Icon</span></span>

<span data-ttu-id="b31d5-291">下面的示例演示如何使用 URI 指定窗口的图标。</span><span class="sxs-lookup"><span data-stu-id="b31d5-291">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="b31d5-292">有关详细信息，请参阅 <xref:System.Windows.Window.Icon%2A>。</span><span class="sxs-lookup"><span data-stu-id="b31d5-292">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="b31d5-293">加载图像、音频和视频文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-293">Loading Image, Audio, and Video Files</span></span>

<span data-ttu-id="b31d5-294">WPF 允许应用程序使用各种媒体类型，所有这些类型都可以使用 pack Uri 进行标识和加载，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="b31d5-294">WPF allows applications to use a wide variety of media types, all of which can be identified and loaded with pack URIs, as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="b31d5-295">有关使用媒体内容的详细信息，请参阅[图形和多媒体](../graphics-multimedia/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b31d5-295">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="b31d5-296">从源站点加载资源字典</span><span class="sxs-lookup"><span data-stu-id="b31d5-296">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="b31d5-297">资源字典（ <xref:System.Windows.ResourceDictionary> ）可用于支持应用程序主题。</span><span class="sxs-lookup"><span data-stu-id="b31d5-297">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="b31d5-298">创建和管理主题的一种方式是将多个主题创建为位于应用程序源站点的资源字典。</span><span class="sxs-lookup"><span data-stu-id="b31d5-298">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="b31d5-299">这样，在添加和更新主题时将无需重新编译和重新部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="b31d5-299">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="b31d5-300">可以使用 pack Uri 来标识和加载这些资源字典，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="b31d5-300">These resource dictionaries can be identified and loaded using pack URIs, which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="b31d5-301">有关 WPF 中的主题的概述，请参阅[样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b31d5-301">For an overview of themes in WPF, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b31d5-302">请参阅</span><span class="sxs-lookup"><span data-stu-id="b31d5-302">See also</span></span>

- [<span data-ttu-id="b31d5-303">WPF 应用程序资源、内容和数据文件</span><span class="sxs-lookup"><span data-stu-id="b31d5-303">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
