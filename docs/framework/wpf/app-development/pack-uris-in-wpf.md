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
# <a name="pack-uris-in-wpf"></a>WPF 中的 Pack URI

在 Windows Presentation Foundation （WPF）中，统一资源标识符（Uri）用于通过多种方式标识和加载文件，其中包括：

- 指定 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 以显示应用程序第一次启动的时间。

- 加载图像。

- 导航到页。

- 加载不可执行的数据文件。

此外，可以使用 Uri 来标识和加载来自各种位置的文件，包括以下各项：

- 当前程序集。

- 引用的程序集。

- 相对于程序集的某个位置。

- 应用程序的源站点。

为了提供用于从这些位置标识和加载这些类型的文件的一致机制，WPF 利用了*PACK URI 方案*的扩展性。 本主题概述了方案，并介绍了如何为各种方案构造包 Uri，以及如何在显示如何使用标记和代码中的 pack Uri 之前介绍绝对和相对 Uri 以及 URI 解析。

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>Pack URI 方案

Pack URI 方案由[开放式打包约定](https://www.ecma-international.org/publications/standards/Ecma-376.htm)（OPC）规范使用，此规范描述了用于组织和标识内容的模型。 此模型的关键元素是包和部件，其中，*包*是一个或多个逻辑*部分*的逻辑容器。 下图阐释了此概念。

![包和部件示意图](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

为了识别部件，OPC 规范利用了 RFC 2396 （统一资源标识符（URI）：通用语法）的扩展性来定义 pack URI 方案。

由 URI 指定的方案由其前缀定义;http、ftp 和 file 是众所周知的示例。 Pack URI 方案使用 "pack" 作为其方案，并且包含两个组件：颁发机构和路径。 下面是 pack URI 的格式。

pack://*机构* / *路径*

*颁发机构*指定包含部件的包类型，而*路径*指定部件在包中的位置。

下图阐释了此概念：

![包、颁发机构与路径之间的关系](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

包和部件之间的关系类似于应用程序和文件之间的关系，其中应用程序（包）可以包含一个或多个文件（部件），包括：

- 编译到本地程序集内的资源文件。

- 编译到所引用的程序集内的资源文件。

- 编译到引用程序集内的资源文件。

- 内容文件。

- 源站点文件。

为了访问这些类型的文件，WPF 支持两个权限： application:///和 siteoforigin:///。 application:/// 授权标识在编译时已知的应用程序数据文件，包括资源文件和内容文件。 siteoforigin:/// 授权标识源站点文件。 下图显示了每种授权的范围。

![Pack URI 示意图](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> 包 URI 的颁发机构组件是一个指向包并必须符合 RFC 2396 的嵌入 URI。 另外，必须用字符“,”替换字符“/”，并且必须对保留字符（如“%”和“?”）进行转义。 有关详细信息，请参阅 OPC。

以下各节说明如何使用这两个颁发机构构造包 Uri 以及用于标识资源、内容和源站点文件的相应路径。

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>资源文件 Pack URI

资源文件配置为 MSBuild `Resource` 项并编译为程序集。 WPF 支持构造包 Uri，这些 Uri 可用于标识编译到本地程序集中或编译到从本地程序集引用的程序集中的资源文件。

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>本地程序集资源文件

编译到本地程序集的资源文件的 pack URI 使用以下授权和路径：

- **授权**：application:///。

- **路径**：资源文件的名称，包括其相对于本地程序集项目文件夹根目录的路径。

下面的示例演示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 位于本地程序集的项目文件夹的根目录中的资源文件的 PACK URI。

`pack://application:,,,/ResourceFile.xaml`

下面的示例演示一个资源文件的 pack URI [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，该资源文件位于本地程序集的项目文件夹的子文件夹中。

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>引用的程序集资源文件

编译到引用的程序集中的资源文件的 pack URI 使用以下授权和路径：

- **授权**：application:///。

- **路径**：编译到所引用程序集内的资源文件的名称。 路径必须符合以下格式：

  *AssemblyShortName*{*;版本*] {*;PublicKey*]; 组件/*路径*

  - **程序集短名称**：所引用的程序集的短名称。

  - **;版本** [可选]：所引用的包含资源文件的程序集的版本。 此部分在加载两个或多个具有相同短名称的引用程序集时使用。

  - **;公钥** [可选]：用于对引用程序集进行签名的公钥。 此部分在加载两个或多个具有相同短名称的引用程序集时使用。

  - **;组件**：指定所引用的程序集是从本地程序集引用的。

  - **/路径**：资源文件的名称，包括其相对于所引用程序集的项目文件夹根目录的路径。

下面的示例演示一个资源文件的 pack URI [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，该资源文件位于所引用程序集的项目文件夹的根目录中。

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

下面的示例演示一个资源文件的 pack URI [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，该资源文件位于所引用程序集的项目文件夹的子文件夹中。

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

下面的示例演示一个资源文件的 pack URI，该 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 资源文件位于所引用的特定于版本的程序集的项目文件夹的根文件夹中。

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

请注意，所引用的程序集资源文件的 pack URI 语法只能与 application:///机构一起使用。 例如，WPF 不支持以下。

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>内容文件 Pack URI

内容文件的 pack URI 使用以下授权和路径：

- **授权**：application:///。

- **路径**：内容文件的名称，包括其相对于应用程序的主可执行程序集的文件系统位置的路径。

下面的示例演示一个内容文件的 pack URI [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，该内容文件与可执行程序集位于同一文件夹中。

`pack://application:,,,/ContentFile.xaml`

下面的示例演示一个内容文件的 pack URI [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，该内容文件位于相对于应用程序的可执行程序集的子文件夹中。

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> 不能导航到 HTML 内容文件。 URI 方案仅支持导航到位于源站点的 HTML 文件。

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>源站点 Pack URI

源站点文件的 pack URI 使用以下授权和路径：

- **授权**：siteoforigin:///。

- **路径**：源站点文件的名称，包括其相对于可执行程序集启动位置的路径。

下面的示例演示了 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 源站点文件的 PACK URI，该站点存储在可执行程序集所在的位置。

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

下面的示例演示了 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 源站点文件的 PACK URI，该站点存储在相对于从中启动应用程序的可执行程序集的位置的子文件夹中。

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>页面文件

配置为 MSBuild 项的 XAML 文件 `Page` 将以与资源文件相同的方式编译到程序集中。 因此， `Page` 可以使用资源文件的 Pack uri 来标识 MSBuild 项。

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]通常配置为 MSBuild 项的文件类型 `Page` 具有以下项之一作为其根元素：

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>绝对和相对 Pack Uri

完全限定的 pack URI 包含方案、颁发机构和路径，并被视为绝对包 URI。 作为开发人员的简化， [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 元素通常允许使用相对 PACK URI 设置相应的属性，其中只包含路径。

例如，请考虑本地程序集中某个资源文件的以下绝对包 URI。

`pack://application:,,,/ResourceFile.xaml`

引用此资源文件的相对 pack URI 如下所示。

`/ResourceFile.xaml`

> [!NOTE]
> 由于源站点文件不与程序集相关联，因此只能用绝对包 Uri 来引用它们。

默认情况下，相对 pack URI 被视为相对于包含引用的标记或代码的位置。 但是，如果使用前导反斜杠，则相对 pack URI 引用将被视为相对于应用程序的根。 例如，假设具有以下项目结构。

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

如果 Page1 包含引用*根*\SUBFOLDER\PAGE2.XAML 的 URI，则引用可以使用以下相对 pack URI。

`Page2.xaml`

如果 Page1 包含引用*根*\PAGE2.XAML 的 URI，则引用可以使用以下相对 pack URI。

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>Pack URI 解析

Pack Uri 的格式使得不同类型的文件的包 Uri 能够看起来相同。 例如，请考虑下面的绝对包 URI。

`pack://application:,,,/ResourceOrContentFile.xaml`

此绝对包 URI 可以引用本地程序集或内容文件中的资源文件。 对于以下相对 URI 也是如此。

`/ResourceOrContentFile.xaml`

为了确定 pack URI 引用的文件类型，WPF 使用以下试探法解析本地程序集中的资源文件和内容文件的 Uri：

1. 探测与 pack URI 匹配的属性的程序集元数据 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 。

2. 如果 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 找到该属性，则包 URI 的路径引用一个内容文件。

3. 如果 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 找不到该属性，则探测编译到本地程序集的资源文件。

4. 如果找到与包 URI 的路径匹配的资源文件，则包 URI 的路径引用资源文件。

5. 如果找不到该资源，则内部创建的 <xref:System.Uri> 无效。

URI 解析不适用于引用以下各项的 Uri：

- 引用的程序集中的内容文件： WPF 不支持这些文件类型。

- 引用的程序集中的嵌入文件：标识这些文件的 Uri 是唯一的，因为它们包括引用的程序集的名称和 `;component` 后缀。

- 源站点文件：标识它们的 Uri 是唯一的，因为它们是可以由包含 siteoforigin:///机构的 pack Uri 标识的唯一文件。

Pack URI 解析可以通过一种简化来使代码在一定程度上独立于资源和内容文件的位置。 例如，如果本地程序集中有一个资源文件，该文件已重新配置为内容文件，则该资源的 pack URI 将保持不变，这与使用包 URI 的代码一样。

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>使用 Pack URI 编程

许多 WPF 类实现可通过 pack Uri 进行设置的属性，包括：

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

可以从标记和代码中设置这些属性。 本节演示这两种设置方式的基本构造，然后演示通用方案示例。

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>在标记中使用 Pack URI

通过使用 pack URI 设置特性的元素，在标记中指定包 URI。 例如：

`<element attribute="pack://application:,,,/File.xaml" />`

表1说明了可在标记中指定的各种绝对包 Uri。

表 1：标记中的绝对 Pack URI

|文件|绝对包 URI|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|资源文件 - 本地程序集|`"pack://application:,,,/ResourceFile.xaml"`|
|子文件夹中的资源文件 - 本地程序集|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|资源文件 - 引用的程序集|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|所引用程序集的子文件夹中的资源文件|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|所引用版本化程序集中的资源文件|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|内容文件|`"pack://application:,,,/ContentFile.xaml"`|
|子文件夹中的内容文件|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|源站点文件|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|子文件夹中的源站点文件|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

表2说明了可以在标记中指定的各种相对包 Uri。

表 2：标记中的相对 Pack URI

|文件|相对 pack URI|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|本地程序集内的资源文件|`"/ResourceFile.xaml"`|
|本地程序集的子文件夹中的资源文件|`"/Subfolder/ResourceFile.xaml"`|
|所引用程序集内的资源文件|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|所引用程序集的子文件夹中的资源文件|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|内容文件|`"/ContentFile.xaml"`|
|子文件夹中的内容文件|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>在代码中使用 Pack URI

通过实例化 <xref:System.Uri> 类并将包 uri 作为参数传递给构造函数，可以在代码中指定包 uri。 以下示例就将此进行演示。

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

默认情况下， <xref:System.Uri> 类将 Pack uri 视为绝对 uri。 因此，当 <xref:System.Uri> 使用相对 PACK URI 创建类的实例时，将引发异常。

```csharp
Uri uri = new Uri("/File.xaml");
```

幸运的是， <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> <xref:System.Uri> 类构造函数的重载接受类型的参数， <xref:System.UriKind> 以允许您指定包 URI 是绝对的还是相对的。

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

你应仅指定 <xref:System.UriKind.Absolute> 或 <xref:System.UriKind.Relative> 在你确定所提供的 pack URI 是另一个。 如果你不知道所使用的 pack URI 的类型，例如当用户在运行时输入包 URI 时，请 <xref:System.UriKind.RelativeOrAbsolute> 改用。

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

表3说明了可以使用在代码中指定的各种相对包 Uri <xref:System.Uri?displayProperty=nameWithType> 。

表 3：代码中的绝对 Pack URI

|文件|绝对包 URI|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|资源文件 - 本地程序集|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|子文件夹中的资源文件 - 本地程序集|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|资源文件 - 引用的程序集|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|所引用程序集的子文件夹中的资源文件|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|所引用版本化程序集中的资源文件|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|内容文件|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|子文件夹中的内容文件|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|源站点文件|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|子文件夹中的源站点文件|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

表4说明了可以使用在代码中指定的各种相对包 Uri <xref:System.Uri?displayProperty=nameWithType> 。

表 4：代码中的相对 Pack URI

|文件|相对 pack URI|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|资源文件 - 本地程序集|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|子文件夹中的资源文件 - 本地程序集|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|资源文件 - 引用的程序集|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|子文件夹中的资源文件 - 引用的程序集|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|内容文件|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|子文件夹中的内容文件|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>常见 Pack URI 方案

前面几节讨论了如何构造包 Uri 来标识资源、内容和源站点文件。 在 WPF 中，可以通过多种方式使用这些构造，以下部分介绍了几种常见的用法。

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>指定当应用程序启动时显示的 UI

<xref:System.Windows.Application.StartupUri%2A>指定在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 启动 WPF 应用程序时要显示的第一个。 对于独立应用程序， [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 可以是一个窗口，如下面的示例中所示。

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

独立应用程序和 XAML 浏览器应用程序（Xbap）还可以将页指定为初始 UI，如下面的示例中所示。

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

如果应用程序是独立的应用程序，并且使用指定了页面 <xref:System.Windows.Application.StartupUri%2A> ，则 WPF 会打开 <xref:System.Windows.Navigation.NavigationWindow> 以承载页面。 对于 Xbap，将在主机浏览器中显示页面。

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>导航到页面

下面的示例演示如何导航到页面。

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

有关在 WPF 中导航的各种方式的详细信息，请参阅[导航概述](navigation-overview.md)。

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>指定窗口图标

下面的示例演示如何使用 URI 指定窗口的图标。

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

有关详细信息，请参阅 <xref:System.Windows.Window.Icon%2A>。

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>加载图像、音频和视频文件

WPF 允许应用程序使用各种媒体类型，所有这些类型都可以使用 pack Uri 进行标识和加载，如下面的示例中所示。

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

有关使用媒体内容的详细信息，请参阅[图形和多媒体](../graphics-multimedia/index.md)。

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>从源站点加载资源字典

资源字典（ <xref:System.Windows.ResourceDictionary> ）可用于支持应用程序主题。 创建和管理主题的一种方式是将多个主题创建为位于应用程序源站点的资源字典。 这样，在添加和更新主题时将无需重新编译和重新部署应用程序。 可以使用 pack Uri 来标识和加载这些资源字典，如以下示例中所示。

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

有关 WPF 中的主题的概述，请参阅[样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。

## <a name="see-also"></a>请参阅

- [WPF 应用程序资源、内容和数据文件](wpf-application-resource-content-and-data-files.md)
