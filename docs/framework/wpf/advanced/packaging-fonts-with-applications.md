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
# <a name="packaging-fonts-with-applications"></a>将字体与应用程序一起打包
本主题概述了如何将字体打包到 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 应用程序。  
  
> [!NOTE]
> 与大多数软件类型一样，字体文件也采用许可模式，而不是出售。 控制字体使用的许可证因供应商而异，但在一般情况下，大多数许可证（包括 Microsoft 使用应用程序和 Windows 提供的字体）都不允许在应用程序中嵌入字体或以其他方式重新分布。 因此，开发人员有责任确保自己具备必要的许可权，可以在应用程序中嵌入相应的字体或者以其他方式重新分布。  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a>字体打包简介  
 你可以轻松地将字体打包为 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序中的资源，以显示用户界面文本和其他类型的基于文本的内容。 字体可以与应用程序的程序集文件分开，也可以嵌入到这些程序集文件中。 还可以创建纯资源字体库，以供应用程序引用。  
  
 OpenType 和 TrueType®字体包含一个类型标志 fsType，指示字体嵌入字体的许可权限。 但是，这个类型标志仅引用存储在文档中的嵌入字体，而不引用嵌入到应用程序中的字体。 可以通过创建 <xref:System.Windows.Media.GlyphTypeface> 对象并引用其属性来检索字体的字体嵌入权限 <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> 。 有关 fsType 标志的详细信息，请参阅[OpenType 规范](https://www.microsoft.com/typography/otspec/os2.htm)的 "OS/2 和 Windows 指标" 部分。  
  
 [Microsoft 版式](https://docs.microsoft.com/typography/)网站包含联系信息，可帮助你查找特定字体供应商或查找自定义工作的字体供应商。  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a>将字体作为内容项添加  
 可以将字体作为项目内容项添加到应用程序中，这些项目内容项与应用程序的程序集文件是分开的。 这意味着内容项不会作为程序集中的资源嵌入。 以下项目文件示例演示如何定义内容项。  
  
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
  
 为了确保应用程序可以在运行时使用字体，这些字体必须能够从应用程序的部署目录中访问。 `<CopyToOutputDirectory>`应用程序项目文件中的元素可让你在生成过程中自动将字体复制到应用程序部署目录。 以下项目文件示例演示如何将字体复制到部署目录中。  
  
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
  
 以下代码示例演示如何将应用程序的字体作为内容项来引用，所引用的内容项必须与应用程序的程序集文件位于同一个目录中。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a>将字体作为资源项添加  
 可以将字体作为项目资源项添加到应用程序中，这些项目资源项会嵌入到应用程序的程序集文件中。 对资源使用单独的子目录有助于对应用程序的项目文件进行整理。 以下项目文件示例演示如何在单独的子目录中将字体定义为资源项。  
  
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
> 将字体作为资源添加到应用程序时，请确保设置的是 `<Resource>` 元素，而不是 `<EmbeddedResource>` 应用程序的项目文件中的元素。 `<EmbeddedResource>`不支持生成操作的元素。  
  
 以下标记示例演示如何引用应用程序的字体资源。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>在代码中引用字体资源项  
 若要从代码中引用字体资源项，必须提供由两部分组成的字体资源引用：基统一资源标识符（URI）;和字体位置参考。 这些值用作方法的参数 <xref:System.Windows.Media.FontFamily.%23ctor%2A> 。 下面的代码示例演示如何在名为的项目子目录中引用应用程序的字体资源 `resources` 。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 基统一资源标识符（URI）可以包含字体资源所在的应用程序子目录。 在这种情况下，字体位置引用不需要指定目录，而是必须包含前导 " `./` "，这表示该字体资源位于由基统一资源标识符（URI）指定的同一目录中。 以下代码示例演示另一种引用字体资源项的方法，该示例与上面的代码示例等效。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>在同一应用程序子目录中引用字体  
 可以将应用程序内容和资源文件放在应用程序项目中由用户定义的同一子目录中。 以下项目文件示例显示在同一子目录中定义的内容页和字体资源。  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 由于应用程序内容和字体位于同一子目录中，因此字体引用是相对于应用程序内容的。 以下示例演示当字体与应用程序位于同一目录中时，如何引用应用程序的字体资源。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>在应用程序中枚举字体  
 若要在应用程序中将字体作为资源项枚举，请使用 <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> 或 <xref:System.Windows.Media.Fonts.GetTypefaces%2A> 方法。 下面的示例演示如何使用 <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> 方法 <xref:System.Windows.Media.FontFamily> 从应用程序字体位置返回对象的集合。 在本示例中，应用程序包含一个名为“resources”的子目录。  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 下面的示例演示如何使用 <xref:System.Windows.Media.Fonts.GetTypefaces%2A> 方法 <xref:System.Windows.Media.Typeface> 从应用程序字体位置返回对象的集合。 在本示例中，应用程序包含一个名为“resources”的子目录。  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a>创建字体资源库  
 可以创建仅包含字体的纯资源库，这种类型的库项目中没有任何代码。 创建纯资源库是将资源与使用它们的应用程序代码分开的一种常用方法。 这还使得库程序集可以包括在多个应用程序项目中。 以下项目文件示例演示纯资源库项目的关键部分。  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a>引用资源库中的字体  
 若要在应用程序中引用资源库中的字体，必须将库程序集的名称作为字体引用的前缀。 在本例中，字体资源程序集是“FontLibrary”。 若要将程序集名称与程序集内的引用分开，请使用“;”字符。 添加后跟字体名引用的“Component”关键字即完成字体库资源的完整引用。 以下代码示例演示如何引用资源库程序集内的字体。  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> 此 SDK 包含一组可用于应用程序的示例 OpenType 字体 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 这些字体是在纯资源库中定义的。 有关详细信息，请参阅[示例 OpenType 字体包](sample-opentype-font-pack.md)。  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a>字体的使用限制  
 下面的列表介绍了在应用程序中打包和使用字体的几个限制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ：  
  
- **字体嵌入权限位：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序不检查或实施任何字体嵌入权限位。 有关详细信息，请参阅[Introduction_to_Packing Fonts](#introduction_to_packaging_fonts)部分。  
  
- **源字体：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序不允许对 http 或 ftp 统一资源标识符（URI）进行字体引用。  
  
- **使用 pack： notation 的绝对 URI：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序不允许 <xref:System.Windows.Media.FontFamily> 使用 "pack：" 以编程方式创建对象，作为对字体的绝对统一资源标识符（URI）引用的一部分。 例如， `"pack://application:,,,/resources/#Pericles Light"` 是无效的字体引用。  
  
- **自动嵌入字体：** 在设计时，不支持搜索应用程序对字体的使用情况，而且不支持自动在应用程序的资源中嵌入字体。  
  
- **字体子集：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序不支持为非固定文档创建字体子集。  
  
- 如果存在不正确的引用，应用程序将回退到使用可用字体。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Microsoft Typography: Links, News, and Contacts](https://docs.microsoft.com/typography/)（Microsoft 版式：链接、新闻和联系人）
- [OpenType 规范](https://www.microsoft.com/typography/otspec/)
- [OpenType 字体功能](opentype-font-features.md)
- [示例 OpenType 字体包](sample-opentype-font-pack.md)
