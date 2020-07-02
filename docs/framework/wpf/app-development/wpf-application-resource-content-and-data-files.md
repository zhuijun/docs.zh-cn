---
title: 应用程序资源、内容和数据文件
description: 了解有关在 Windows Presentation Foundation （WPF）中配置、识别和使用应用程序数据文件的特殊支持。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
ms.openlocfilehash: 324b3eb922f0fd1d1d9ad00105a06a7fbdb8effd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622856"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="23b70-103">WPF 应用程序资源、内容和数据文件</span><span class="sxs-lookup"><span data-stu-id="23b70-103">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="23b70-104">Microsoft Windows 应用程序通常依赖于包含不可执行的数据的文件，例如 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 图像、视频和音频。</span><span class="sxs-lookup"><span data-stu-id="23b70-104">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="23b70-105">Windows Presentation Foundation （WPF）为配置、标识和使用这些类型的数据文件（称为应用程序数据文件）提供特殊支持。</span><span class="sxs-lookup"><span data-stu-id="23b70-105">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="23b70-106">这种支持主要针对一组特定的应用程序数据文件类型，包括：</span><span class="sxs-lookup"><span data-stu-id="23b70-106">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="23b70-107">**资源文件**：编译为可执行文件或库 WPF 程序集的数据文件。</span><span class="sxs-lookup"><span data-stu-id="23b70-107">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="23b70-108">**内容文件**：独立的数据文件，与可执行的 WPF 程序集具有显式关联。</span><span class="sxs-lookup"><span data-stu-id="23b70-108">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="23b70-109">**源站点文件**：与可执行 WPF 程序集没有关联的独立数据文件。</span><span class="sxs-lookup"><span data-stu-id="23b70-109">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="23b70-110">这三种类型的文件之间的一个重要区别是：资源文件和内容文件在生成时即为程序集所知；程序集明确知道它们的存在。</span><span class="sxs-lookup"><span data-stu-id="23b70-110">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="23b70-111">但对于源站点文件，程序集可能根本不知道它们，或者通过包统一资源标识符（URI）引用隐式了解;对于后一种情况，不能保证引用的源站点文件确实存在。</span><span class="sxs-lookup"><span data-stu-id="23b70-111">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="23b70-112">若要引用应用程序数据文件，Windows Presentation Foundation （WPF）使用包统一资源标识符（URI）方案，详见 WPF 中的[Pack uri](pack-uris-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="23b70-112">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="23b70-113">本主题介绍如何配置和使用应用程序数据文件。</span><span class="sxs-lookup"><span data-stu-id="23b70-113">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="23b70-114">资源文件</span><span class="sxs-lookup"><span data-stu-id="23b70-114">Resource Files</span></span>  
 <span data-ttu-id="23b70-115">如果应用程序数据文件必须始终可供某个应用程序使用，那么保证可用性的唯一方法是将其编译到应用程序的主可执行程序集内，或者它所引用的程序集内。</span><span class="sxs-lookup"><span data-stu-id="23b70-115">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="23b70-116">这种类型的应用程序数据文件称为*资源文件*。</span><span class="sxs-lookup"><span data-stu-id="23b70-116">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="23b70-117">应在以下情况下使用资源文件：</span><span class="sxs-lookup"><span data-stu-id="23b70-117">You should use resource files when:</span></span>  
  
- <span data-ttu-id="23b70-118">将资源文件编译到程序集内之后，无需更新资源文件的内容。</span><span class="sxs-lookup"><span data-stu-id="23b70-118">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="23b70-119">希望通过减少文件依赖项的数量来简化应用程序分发的复杂性。</span><span class="sxs-lookup"><span data-stu-id="23b70-119">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="23b70-120">应用程序数据文件需要可本地化（请参阅[WPF 全球化和本地化概述](../advanced/wpf-globalization-and-localization-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="23b70-120">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23b70-121">本节中所述的资源文件不同于[XAML 资源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)中所述的资源文件，与[管理应用程序资源（.net）](/visualstudio/ide/managing-application-resources-dotnet)中所述的嵌入或链接的资源不同。</span><span class="sxs-lookup"><span data-stu-id="23b70-121">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="23b70-122">配置资源文件</span><span class="sxs-lookup"><span data-stu-id="23b70-122">Configuring Resource Files</span></span>  
 <span data-ttu-id="23b70-123">在 WPF 中，资源文件是作为项包含在 Microsoft 生成引擎（MSBuild）项目中的文件 `Resource` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-123">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="23b70-124">在 Visual Studio 中，你可以通过将文件添加到项目并将其设置为来创建资源文件 `Build Action` `Resource` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-124">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="23b70-125">生成项目时，MSBuild 会将资源编译到程序集中。</span><span class="sxs-lookup"><span data-stu-id="23b70-125">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="23b70-126">使用资源文件</span><span class="sxs-lookup"><span data-stu-id="23b70-126">Using Resource Files</span></span>  
 <span data-ttu-id="23b70-127">若要加载资源文件，可以调用类的 <xref:System.Windows.Application.GetResourceStream%2A> 方法 <xref:System.Windows.Application> ，并传递标识所需的资源文件的包 URI。</span><span class="sxs-lookup"><span data-stu-id="23b70-127">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="23b70-128"><xref:System.Windows.Application.GetResourceStream%2A>返回一个 <xref:System.Windows.Resources.StreamResourceInfo> 对象，该对象将资源文件作为公开 <xref:System.IO.Stream> ，并描述其内容类型。</span><span class="sxs-lookup"><span data-stu-id="23b70-128"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="23b70-129">例如，下面的代码演示如何使用 <xref:System.Windows.Application.GetResourceStream%2A> 加载 <xref:System.Windows.Controls.Page> 资源文件并将其设置为 <xref:System.Windows.Controls.Frame> （）的内容 `pageFrame` ：</span><span class="sxs-lookup"><span data-stu-id="23b70-129">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="23b70-130">虽然调用会 <xref:System.Windows.Application.GetResourceStream%2A> 使你能够访问 <xref:System.IO.Stream> ，但你需要执行其他工作，将其转换为你要将其设置为的属性类型。</span><span class="sxs-lookup"><span data-stu-id="23b70-130">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="23b70-131">相反，你可以让 WPF <xref:System.IO.Stream> 通过使用代码将资源文件直接加载到类型的属性中来处理打开和转换。</span><span class="sxs-lookup"><span data-stu-id="23b70-131">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="23b70-132">下面的示例演示如何 <xref:System.Windows.Controls.Page> 使用代码将直接加载到 <xref:System.Windows.Controls.Frame> （ `pageFrame` ）。</span><span class="sxs-lookup"><span data-stu-id="23b70-132">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="23b70-133">下面的示例是与上例等效的标记。</span><span class="sxs-lookup"><span data-stu-id="23b70-133">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="23b70-134">作为资源文件的应用程序代码文件</span><span class="sxs-lookup"><span data-stu-id="23b70-134">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="23b70-135">使用包 Uri 可以引用一组特殊的 WPF 应用程序代码文件，包括 windows、页面、流文档和资源字典。</span><span class="sxs-lookup"><span data-stu-id="23b70-135">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="23b70-136">例如，你可以 <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> 使用一个包 URI 来设置属性，该属性引用在应用程序启动时要加载的窗口或页面。</span><span class="sxs-lookup"><span data-stu-id="23b70-136">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="23b70-137">当将 XAML 文件作为项包含在 MSBuild 项目中时，可以执行此操作 `Page` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-137">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="23b70-138">在 Visual Studio 中，将新的 <xref:System.Windows.Window> 、、、 <xref:System.Windows.Navigation.NavigationWindow> 或添加 <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.ResourceDictionary> 到项目， `Build Action` 标记文件的将默认为 `Page` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-138">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="23b70-139">在编译具有项的项目时 `Page` ， [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 项将转换为二进制格式，并编译到关联的程序集中。</span><span class="sxs-lookup"><span data-stu-id="23b70-139">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="23b70-140">因此，可以像使用典型的资源文件一样使用这些文件。</span><span class="sxs-lookup"><span data-stu-id="23b70-140">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23b70-141">如果将 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件配置为 `Resource` 项，但没有代码隐藏文件，则会将原始文件 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 编译为程序集而不是原始的二进制版本 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="23b70-141">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="23b70-142">内容文件</span><span class="sxs-lookup"><span data-stu-id="23b70-142">Content Files</span></span>  
 <span data-ttu-id="23b70-143">*内容文件*与可执行程序集一起分发为松散文件。</span><span class="sxs-lookup"><span data-stu-id="23b70-143">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="23b70-144">虽然它们不编译到程序集内，但编译程序集时所使用的元数据建立了与每个内容文件的关联。</span><span class="sxs-lookup"><span data-stu-id="23b70-144">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="23b70-145">如果应用程序需要一组特定的应用程序数据文件，并且你希望能够更新这些文件，而无需重新编译使用它们的程序集，应使用内容文件。</span><span class="sxs-lookup"><span data-stu-id="23b70-145">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="23b70-146">配置内容文件</span><span class="sxs-lookup"><span data-stu-id="23b70-146">Configuring Content Files</span></span>  
 <span data-ttu-id="23b70-147">若要将内容文件添加到项目中，必须将应用程序数据文件作为项包括在内 `Content` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-147">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="23b70-148">此外，由于不会将内容文件直接编译到程序集中，因此需要设置 MSBuild `CopyToOutputDirectory` metadata 元素，以指定将内容文件复制到相对于生成的程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="23b70-148">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="23b70-149">如果希望在每次生成项目时将资源复制到生成输出文件夹，请 `CopyToOutputDirectory` 使用值设置元数据元素 `Always` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-149">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="23b70-150">否则，你可以通过使用值来确保只将最新版本的资源复制到生成输出文件夹 `PreserveNewest` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-150">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="23b70-151">下面演示的是一个配置为内容文件的文件，此内容文件只有在将新版本的资源添加到项目时才会复制到生成输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="23b70-151">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="23b70-152">在 Visual Studio 中，你可以通过将文件添加到项目并将其设置为来创建内容文件 `Build Action` `Content` ，并将其设置为（与相同 `Copy to Output Directory` `Copy always` `Always` ）和 `Copy if newer` （与相同 `PreserveNewest` ）。</span><span class="sxs-lookup"><span data-stu-id="23b70-152">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="23b70-153">生成项目时， <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 会将属性编译到每个内容文件的程序集的元数据中。</span><span class="sxs-lookup"><span data-stu-id="23b70-153">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="23b70-154">的值 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 表示内容文件相对于其在项目中的位置的路径。</span><span class="sxs-lookup"><span data-stu-id="23b70-154">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="23b70-155">例如，如果内容文件位于项目子文件夹中，则其他路径信息将合并到 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 值中。</span><span class="sxs-lookup"><span data-stu-id="23b70-155">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="23b70-156"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>该值也是内容文件在生成输出文件夹中的路径的值。</span><span class="sxs-lookup"><span data-stu-id="23b70-156">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="23b70-157">使用内容文件</span><span class="sxs-lookup"><span data-stu-id="23b70-157">Using Content Files</span></span>  
 <span data-ttu-id="23b70-158">若要加载内容文件，可以调用类的 <xref:System.Windows.Application.GetContentStream%2A> 方法 <xref:System.Windows.Application> ，并传递标识所需内容文件的包 URI。</span><span class="sxs-lookup"><span data-stu-id="23b70-158">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="23b70-159"><xref:System.Windows.Application.GetContentStream%2A>返回一个 <xref:System.Windows.Resources.StreamResourceInfo> 对象，该对象将内容文件作为公开 <xref:System.IO.Stream> ，并描述其内容类型。</span><span class="sxs-lookup"><span data-stu-id="23b70-159"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="23b70-160">例如，下面的代码演示如何使用 <xref:System.Windows.Application.GetContentStream%2A> 加载 <xref:System.Windows.Controls.Page> 内容文件，并将其设置为 <xref:System.Windows.Controls.Frame> （）的内容 `pageFrame` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-160">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="23b70-161">虽然调用会 <xref:System.Windows.Application.GetContentStream%2A> 使你能够访问 <xref:System.IO.Stream> ，但你需要执行其他工作，将其转换为你要将其设置为的属性类型。</span><span class="sxs-lookup"><span data-stu-id="23b70-161">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="23b70-162">相反，你可以让 WPF <xref:System.IO.Stream> 通过使用代码将资源文件直接加载到类型的属性中来处理打开和转换。</span><span class="sxs-lookup"><span data-stu-id="23b70-162">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="23b70-163">下面的示例演示如何 <xref:System.Windows.Controls.Page> 使用代码将直接加载到 <xref:System.Windows.Controls.Frame> （ `pageFrame` ）。</span><span class="sxs-lookup"><span data-stu-id="23b70-163">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="23b70-164">下面的示例是与上例等效的标记。</span><span class="sxs-lookup"><span data-stu-id="23b70-164">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="23b70-165">源站点文件</span><span class="sxs-lookup"><span data-stu-id="23b70-165">Site of Origin Files</span></span>  
 <span data-ttu-id="23b70-166">资源文件与一起分发的程序集具有显式关系，如定义 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="23b70-166">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="23b70-167">但是，有些情况下可能需要在程序集和应用程序数据文件之间建立隐式关系或不存在的关系，这些情况包括：</span><span class="sxs-lookup"><span data-stu-id="23b70-167">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="23b70-168">文件在编译时不存在。</span><span class="sxs-lookup"><span data-stu-id="23b70-168">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="23b70-169">在运行之前不知道程序集将需要哪些文件。</span><span class="sxs-lookup"><span data-stu-id="23b70-169">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="23b70-170">希望能够更新文件，无需重新编译与这些文件关联的程序集。</span><span class="sxs-lookup"><span data-stu-id="23b70-170">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="23b70-171">应用程序使用大型数据文件（如音频和视频），并且你希望仅在用户选择下载时才下载这些文件。</span><span class="sxs-lookup"><span data-stu-id="23b70-171">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="23b70-172">可以通过使用传统的 URI 方案（如和方案）加载这些类型的文件 `file:///` `http://` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-172">It is possible to load these types of files by using traditional URI schemes, such as the `file:///` and `http://` schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="23b70-173">但是， `file:///` 和 `http://` 方案要求你的应用程序具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="23b70-173">However, the `file:///` and `http://` schemes require your application to have full trust.</span></span> <span data-ttu-id="23b70-174">如果你的应用程序是从 Internet 或 intranet 启动的 XAML 浏览器应用程序（XBAP），并且它只请求从这些位置启动的应用程序允许的权限集，则只能从应用程序的源站点（启动位置）加载松散文件。</span><span class="sxs-lookup"><span data-stu-id="23b70-174">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="23b70-175">此类文件称为*源站点*文件。</span><span class="sxs-lookup"><span data-stu-id="23b70-175">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="23b70-176">虽然源站点文件并不仅限于部分信任应用程序，但这些文件是部分信任应用程序的唯一选择。</span><span class="sxs-lookup"><span data-stu-id="23b70-176">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="23b70-177">完全信任应用程序可能仍然需要加载它们在生成时所不知道的应用程序数据文件；但是完全信任应用程序可以使用 file:///，应用程序数据文件很可能将安装在该应用程序程序集所在的文件夹或其子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="23b70-177">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="23b70-178">在此情况下，使用源站点引用比使用 file:/// 更加容易，因为使用 file:/// 需要找出文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="23b70-178">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23b70-179">源站点文件不与客户端计算机上的 XAML 浏览器应用程序（XBAP）缓存，而内容文件为。</span><span class="sxs-lookup"><span data-stu-id="23b70-179">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="23b70-180">因此，只有在专门请求下载源站点文件时，才会下载它们。</span><span class="sxs-lookup"><span data-stu-id="23b70-180">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="23b70-181">如果 XAML 浏览器应用程序（XBAP）应用程序包含大型媒体文件，则将其配置为源站点文件意味着初始应用程序的启动速度要快得多，并且仅按需下载这些文件。</span><span class="sxs-lookup"><span data-stu-id="23b70-181">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="23b70-182">配置源站点文件</span><span class="sxs-lookup"><span data-stu-id="23b70-182">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="23b70-183">如果源站点文件在编译时不存在或未知，则需要使用传统的部署机制来确保在运行时可以使用所需的文件，包括使用 `XCopy` 命令行程序或 Microsoft Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="23b70-183">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="23b70-184">如果你在编译时知道想要位于源站点的文件，但仍希望避免显式依赖项，则可以将这些文件作为项添加到 MSBuild 项目 `None` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-184">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="23b70-185">与内容文件一样，需要设置 MSBuild `CopyToOutputDirectory` 属性以指定将源站点文件复制到相对于生成的程序集的位置，方法是指定 `Always` 值或 `PreserveNewest` 值。</span><span class="sxs-lookup"><span data-stu-id="23b70-185">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="23b70-186">在 Visual Studio 中，你可以通过将文件添加到项目并将其设置为来创建源站点文件 `Build Action` `None` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-186">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="23b70-187">生成项目时，MSBuild 会将指定的文件复制到生成输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="23b70-187">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="23b70-188">使用源站点文件</span><span class="sxs-lookup"><span data-stu-id="23b70-188">Using Site of Origin Files</span></span>  
 <span data-ttu-id="23b70-189">若要加载源站点文件，可以调用 <xref:System.Windows.Application.GetRemoteStream%2A> 类的方法 <xref:System.Windows.Application> ，同时传递标识所需的源站点文件的包 URI。</span><span class="sxs-lookup"><span data-stu-id="23b70-189">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="23b70-190"><xref:System.Windows.Application.GetRemoteStream%2A>返回一个 <xref:System.Windows.Resources.StreamResourceInfo> 对象，该对象将源站点文件作为公开 <xref:System.IO.Stream> ，并描述其内容类型。</span><span class="sxs-lookup"><span data-stu-id="23b70-190"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="23b70-191">例如，下面的代码演示如何使用 <xref:System.Windows.Application.GetRemoteStream%2A> 加载 <xref:System.Windows.Controls.Page> 源站点文件并将其设置为 <xref:System.Windows.Controls.Frame> （）的内容 `pageFrame` 。</span><span class="sxs-lookup"><span data-stu-id="23b70-191">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="23b70-192">虽然调用会 <xref:System.Windows.Application.GetRemoteStream%2A> 使你能够访问 <xref:System.IO.Stream> ，但你需要执行其他工作，将其转换为你要将其设置为的属性类型。</span><span class="sxs-lookup"><span data-stu-id="23b70-192">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="23b70-193">相反，你可以让 WPF <xref:System.IO.Stream> 通过使用代码将资源文件直接加载到类型的属性中来处理打开和转换。</span><span class="sxs-lookup"><span data-stu-id="23b70-193">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="23b70-194">下面的示例演示如何 <xref:System.Windows.Controls.Page> 使用代码将直接加载到 <xref:System.Windows.Controls.Frame> （ `pageFrame` ）。</span><span class="sxs-lookup"><span data-stu-id="23b70-194">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="23b70-195">下面的示例是与上例等效的标记。</span><span class="sxs-lookup"><span data-stu-id="23b70-195">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="23b70-196">更改生成类型后重新生成</span><span class="sxs-lookup"><span data-stu-id="23b70-196">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="23b70-197">在更改应用程序数据文件的生成类型后，需要重新生成整个应用程序以确保应用这些更改。</span><span class="sxs-lookup"><span data-stu-id="23b70-197">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="23b70-198">如果只生成应用程序，则不会应用更改。</span><span class="sxs-lookup"><span data-stu-id="23b70-198">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b70-199">请参阅</span><span class="sxs-lookup"><span data-stu-id="23b70-199">See also</span></span>

- [<span data-ttu-id="23b70-200">WPF 中的 Pack URI</span><span class="sxs-lookup"><span data-stu-id="23b70-200">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
