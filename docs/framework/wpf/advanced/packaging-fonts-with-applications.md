---
title: 将字体与应用程序一起打包
description: 了解如何使用 Windows Presentation Foundation 应用程序打包字体，包括添加字体作为内容和资源项以及字体使用限制。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: 725f05c22eda199d86e5ec5dbb6bdd899ee66a5d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166358"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="cff3a-103">将字体与应用程序一起打包</span><span class="sxs-lookup"><span data-stu-id="cff3a-103">Packaging Fonts with Applications</span></span>
<span data-ttu-id="cff3a-104">本主题概述了如何将字体打包到 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 应用程序。</span><span class="sxs-lookup"><span data-stu-id="cff3a-104">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cff3a-105">与大多数软件类型一样，字体文件也采用许可模式，而不是出售。</span><span class="sxs-lookup"><span data-stu-id="cff3a-105">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="cff3a-106">控制字体使用的许可证因供应商而异，但在一般情况下，大多数许可证（包括 Microsoft 使用应用程序和 Windows 提供的字体）都不允许在应用程序中嵌入字体或以其他方式重新分布。</span><span class="sxs-lookup"><span data-stu-id="cff3a-106">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts Microsoft supplies with applications and Windows, do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="cff3a-107">因此，开发人员有责任确保自己具备必要的许可权，可以在应用程序中嵌入相应的字体或者以其他方式重新分布。</span><span class="sxs-lookup"><span data-stu-id="cff3a-107">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="cff3a-108">字体打包简介</span><span class="sxs-lookup"><span data-stu-id="cff3a-108">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="cff3a-109">你可以轻松地将字体打包为 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序中的资源，以显示用户界面文本和其他类型的基于文本的内容。</span><span class="sxs-lookup"><span data-stu-id="cff3a-109">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="cff3a-110">字体可以与应用程序的程序集文件分开，也可以嵌入到这些程序集文件中。</span><span class="sxs-lookup"><span data-stu-id="cff3a-110">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="cff3a-111">还可以创建纯资源字体库，以供应用程序引用。</span><span class="sxs-lookup"><span data-stu-id="cff3a-111">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 <span data-ttu-id="cff3a-112">OpenType 和 TrueType®字体包含一个类型标志 fsType，指示字体嵌入字体的许可权限。</span><span class="sxs-lookup"><span data-stu-id="cff3a-112">OpenType and TrueType® fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="cff3a-113">但是，这个类型标志仅引用存储在文档中的嵌入字体，而不引用嵌入到应用程序中的字体。</span><span class="sxs-lookup"><span data-stu-id="cff3a-113">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="cff3a-114">可以通过创建 <xref:System.Windows.Media.GlyphTypeface> 对象并引用其属性来检索字体的字体嵌入权限 <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> 。</span><span class="sxs-lookup"><span data-stu-id="cff3a-114">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="cff3a-115">有关 fsType 标志的详细信息，请参阅[OpenType 规范](https://www.microsoft.com/typography/otspec/os2.htm)的 "OS/2 和 Windows 指标" 部分。</span><span class="sxs-lookup"><span data-stu-id="cff3a-115">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="cff3a-116">[Microsoft 版式](https://docs.microsoft.com/typography/)网站包含联系信息，可帮助你查找特定字体供应商或查找自定义工作的字体供应商。</span><span class="sxs-lookup"><span data-stu-id="cff3a-116">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="cff3a-117">将字体作为内容项添加</span><span class="sxs-lookup"><span data-stu-id="cff3a-117">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="cff3a-118">可以将字体作为项目内容项添加到应用程序中，这些项目内容项与应用程序的程序集文件是分开的。</span><span class="sxs-lookup"><span data-stu-id="cff3a-118">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="cff3a-119">这意味着内容项不会作为程序集中的资源嵌入。</span><span class="sxs-lookup"><span data-stu-id="cff3a-119">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="cff3a-120">以下项目文件示例演示如何定义内容项。</span><span class="sxs-lookup"><span data-stu-id="cff3a-120">The following project file example shows how to define content items.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 <span data-ttu-id="cff3a-121">为了确保应用程序可以在运行时使用字体，这些字体必须能够从应用程序的部署目录中访问。</span><span class="sxs-lookup"><span data-stu-id="cff3a-121">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="cff3a-122">`<CopyToOutputDirectory>`应用程序项目文件中的元素可让你在生成过程中自动将字体复制到应用程序部署目录。</span><span class="sxs-lookup"><span data-stu-id="cff3a-122">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="cff3a-123">以下项目文件示例演示如何将字体复制到部署目录中。</span><span class="sxs-lookup"><span data-stu-id="cff3a-123">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
```xml  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 <span data-ttu-id="cff3a-124">以下代码示例演示如何将应用程序的字体作为内容项来引用，所引用的内容项必须与应用程序的程序集文件位于同一个目录中。</span><span class="sxs-lookup"><span data-stu-id="cff3a-124">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="cff3a-125">将字体作为资源项添加</span><span class="sxs-lookup"><span data-stu-id="cff3a-125">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="cff3a-126">可以将字体作为项目资源项添加到应用程序中，这些项目资源项会嵌入到应用程序的程序集文件中。</span><span class="sxs-lookup"><span data-stu-id="cff3a-126">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="cff3a-127">对资源使用单独的子目录有助于对应用程序的项目文件进行整理。</span><span class="sxs-lookup"><span data-stu-id="cff3a-127">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="cff3a-128">以下项目文件示例演示如何在单独的子目录中将字体定义为资源项。</span><span class="sxs-lookup"><span data-stu-id="cff3a-128">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="cff3a-129">将字体作为资源添加到应用程序时，请确保设置的是 `<Resource>` 元素，而不是 `<EmbeddedResource>` 应用程序的项目文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="cff3a-129">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="cff3a-130">`<EmbeddedResource>`不支持生成操作的元素。</span><span class="sxs-lookup"><span data-stu-id="cff3a-130">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="cff3a-131">以下标记示例演示如何引用应用程序的字体资源。</span><span class="sxs-lookup"><span data-stu-id="cff3a-131">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="cff3a-132">在代码中引用字体资源项</span><span class="sxs-lookup"><span data-stu-id="cff3a-132">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="cff3a-133">若要从代码中引用字体资源项，必须提供由两部分组成的字体资源引用：基统一资源标识符（URI）;和字体位置参考。</span><span class="sxs-lookup"><span data-stu-id="cff3a-133">In order to reference font resource items from code, you must supply a two-part font resource reference: the base uniform resource identifier (URI); and the font location reference.</span></span> <span data-ttu-id="cff3a-134">这些值用作方法的参数 <xref:System.Windows.Media.FontFamily.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="cff3a-134">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="cff3a-135">下面的代码示例演示如何在名为的项目子目录中引用应用程序的字体资源 `resources` 。</span><span class="sxs-lookup"><span data-stu-id="cff3a-135">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="cff3a-136">基统一资源标识符（URI）可以包含字体资源所在的应用程序子目录。</span><span class="sxs-lookup"><span data-stu-id="cff3a-136">The base uniform resource identifier (URI) can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="cff3a-137">在这种情况下，字体位置引用不需要指定目录，而是必须包含前导 " `./` "，这表示该字体资源位于由基统一资源标识符（URI）指定的同一目录中。</span><span class="sxs-lookup"><span data-stu-id="cff3a-137">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base uniform resource identifier (URI).</span></span> <span data-ttu-id="cff3a-138">以下代码示例演示另一种引用字体资源项的方法，该示例与上面的代码示例等效。</span><span class="sxs-lookup"><span data-stu-id="cff3a-138">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="cff3a-139">在同一应用程序子目录中引用字体</span><span class="sxs-lookup"><span data-stu-id="cff3a-139">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="cff3a-140">可以将应用程序内容和资源文件放在应用程序项目中由用户定义的同一子目录中。</span><span class="sxs-lookup"><span data-stu-id="cff3a-140">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="cff3a-141">以下项目文件示例显示在同一子目录中定义的内容页和字体资源。</span><span class="sxs-lookup"><span data-stu-id="cff3a-141">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="cff3a-142">由于应用程序内容和字体位于同一子目录中，因此字体引用是相对于应用程序内容的。</span><span class="sxs-lookup"><span data-stu-id="cff3a-142">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="cff3a-143">以下示例演示当字体与应用程序位于同一目录中时，如何引用应用程序的字体资源。</span><span class="sxs-lookup"><span data-stu-id="cff3a-143">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="cff3a-144">在应用程序中枚举字体</span><span class="sxs-lookup"><span data-stu-id="cff3a-144">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="cff3a-145">若要在应用程序中将字体作为资源项枚举，请使用 <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> 或 <xref:System.Windows.Media.Fonts.GetTypefaces%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="cff3a-145">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="cff3a-146">下面的示例演示如何使用 <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> 方法 <xref:System.Windows.Media.FontFamily> 从应用程序字体位置返回对象的集合。</span><span class="sxs-lookup"><span data-stu-id="cff3a-146">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="cff3a-147">在本示例中，应用程序包含一个名为“resources”的子目录。</span><span class="sxs-lookup"><span data-stu-id="cff3a-147">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="cff3a-148">下面的示例演示如何使用 <xref:System.Windows.Media.Fonts.GetTypefaces%2A> 方法 <xref:System.Windows.Media.Typeface> 从应用程序字体位置返回对象的集合。</span><span class="sxs-lookup"><span data-stu-id="cff3a-148">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="cff3a-149">在本示例中，应用程序包含一个名为“resources”的子目录。</span><span class="sxs-lookup"><span data-stu-id="cff3a-149">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="cff3a-150">创建字体资源库</span><span class="sxs-lookup"><span data-stu-id="cff3a-150">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="cff3a-151">可以创建仅包含字体的纯资源库，这种类型的库项目中没有任何代码。</span><span class="sxs-lookup"><span data-stu-id="cff3a-151">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="cff3a-152">创建纯资源库是将资源与使用它们的应用程序代码分开的一种常用方法。</span><span class="sxs-lookup"><span data-stu-id="cff3a-152">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="cff3a-153">这还使得库程序集可以包括在多个应用程序项目中。</span><span class="sxs-lookup"><span data-stu-id="cff3a-153">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="cff3a-154">以下项目文件示例演示纯资源库项目的关键部分。</span><span class="sxs-lookup"><span data-stu-id="cff3a-154">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
```xml  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="cff3a-155">引用资源库中的字体</span><span class="sxs-lookup"><span data-stu-id="cff3a-155">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="cff3a-156">若要在应用程序中引用资源库中的字体，必须将库程序集的名称作为字体引用的前缀。</span><span class="sxs-lookup"><span data-stu-id="cff3a-156">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="cff3a-157">在本例中，字体资源程序集是“FontLibrary”。</span><span class="sxs-lookup"><span data-stu-id="cff3a-157">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="cff3a-158">若要将程序集名称与程序集内的引用分开，请使用“;”字符。</span><span class="sxs-lookup"><span data-stu-id="cff3a-158">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="cff3a-159">添加后跟字体名引用的“Component”关键字即完成字体库资源的完整引用。</span><span class="sxs-lookup"><span data-stu-id="cff3a-159">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="cff3a-160">以下代码示例演示如何引用资源库程序集内的字体。</span><span class="sxs-lookup"><span data-stu-id="cff3a-160">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> <span data-ttu-id="cff3a-161">此 SDK 包含一组可用于应用程序的示例 OpenType 字体 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cff3a-161">This SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="cff3a-162">这些字体是在纯资源库中定义的。</span><span class="sxs-lookup"><span data-stu-id="cff3a-162">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="cff3a-163">有关详细信息，请参阅[示例 OpenType 字体包](sample-opentype-font-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="cff3a-163">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a><span data-ttu-id="cff3a-164">字体的使用限制</span><span class="sxs-lookup"><span data-stu-id="cff3a-164">Limitations on Font Usage</span></span>  
 <span data-ttu-id="cff3a-165">下面的列表介绍了在应用程序中打包和使用字体的几个限制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="cff3a-165">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="cff3a-166">**字体嵌入权限位：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序不检查或实施任何字体嵌入权限位。</span><span class="sxs-lookup"><span data-stu-id="cff3a-166">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="cff3a-167">有关详细信息，请参阅[Introduction_to_Packing Fonts](#introduction_to_packaging_fonts)部分。</span><span class="sxs-lookup"><span data-stu-id="cff3a-167">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="cff3a-168">**源字体：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序不允许对 http 或 ftp 统一资源标识符（URI）进行字体引用。</span><span class="sxs-lookup"><span data-stu-id="cff3a-168">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp uniform resource identifier (URI).</span></span>  
  
- <span data-ttu-id="cff3a-169">**使用 pack： notation 的绝对 URI：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序不允许 <xref:System.Windows.Media.FontFamily> 使用 "pack：" 以编程方式创建对象，作为对字体的绝对统一资源标识符（URI）引用的一部分。</span><span class="sxs-lookup"><span data-stu-id="cff3a-169">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute uniform resource identifier (URI) reference to a font.</span></span> <span data-ttu-id="cff3a-170">例如， `"pack://application:,,,/resources/#Pericles Light"` 是无效的字体引用。</span><span class="sxs-lookup"><span data-stu-id="cff3a-170">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="cff3a-171">**自动嵌入字体：** 在设计时，不支持搜索应用程序对字体的使用情况，而且不支持自动在应用程序的资源中嵌入字体。</span><span class="sxs-lookup"><span data-stu-id="cff3a-171">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="cff3a-172">**字体子集：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序不支持为非固定文档创建字体子集。</span><span class="sxs-lookup"><span data-stu-id="cff3a-172">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="cff3a-173">如果存在不正确的引用，应用程序将回退到使用可用字体。</span><span class="sxs-lookup"><span data-stu-id="cff3a-173">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff3a-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cff3a-174">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- <span data-ttu-id="cff3a-175">[Microsoft Typography: Links, News, and Contacts](https://docs.microsoft.com/typography/)（Microsoft 版式：链接、新闻和联系人）</span><span class="sxs-lookup"><span data-stu-id="cff3a-175">[Microsoft Typography: Links, News, and Contacts](https://docs.microsoft.com/typography/)</span></span>
- [<span data-ttu-id="cff3a-176">OpenType 规范</span><span class="sxs-lookup"><span data-stu-id="cff3a-176">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="cff3a-177">OpenType 字体功能</span><span class="sxs-lookup"><span data-stu-id="cff3a-177">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="cff3a-178">示例 OpenType 字体包</span><span class="sxs-lookup"><span data-stu-id="cff3a-178">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
