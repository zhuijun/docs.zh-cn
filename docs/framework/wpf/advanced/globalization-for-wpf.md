---
title: 全球化
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 2d7cf73e37fe8c4bbdbef3d356f1dbb8903815f3
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812323"
---
# <a name="globalization-for-wpf"></a>WPF 的全球化
本主题介绍编写 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 全球市场应用程序时应注意的问题。 全球化编程元素是在命名空间中的 .NET 中定义的 <xref:System.Globalization> 。

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>XAML 全球化
 Extensible Application Markup Language (XAML) 基于 XML，并利用 XML 规范中定义的全球化支持。 以下各节介绍 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 你应注意的一些功能。

<a name="char_reference"></a>
### <a name="character-references"></a>字符引用
字符引用以十进制或十六进制形式为其表示的特定 Unicode 字符提供 UTF16 代码单元。 下面的示例显示了一个用于哥普特大写字母 HORI 或 "Ϩ" 的十进制字符引用：

```xaml
&#1000;
```

下面的示例演示十六进制字符引用。 请注意，它在十六进制数字前面有一个 **x** 。

```xaml
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>编码
 支持的编码 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 为 ASCII、UNICODE utf-16 和 utf-8。 编码语句位于文档的开头 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。 如果不存在编码特性，并且没有任何字节顺序，则分析器默认为 UTF-8。 UTF-8 和 UTF-16 都是首选编码。 不支持 UTF-7。 下面的示例演示如何在文件中指定 UTF-8 编码 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。

```xaml
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>语言特性
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 使用 [xml： lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) 表示元素的 language 特性。  若要利用 <xref:System.Globalization.CultureInfo> 类，language 特性值需要是预定义的区域性名称之一 <xref:System.Globalization.CultureInfo> 。 [xml:lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) 在元素树中可继承（可按 XML 规则继承，但并不一定这样继承，因为存在依赖属性继承）；在未明确赋值的情况下，其默认值为空字符串。

 语言特性对指定方言非常有用。 例如，法语在法国、魁北克、比利时和瑞士的拼写、词汇和发音各不相同。 同时，中文、日语和朝鲜语使用 Unicode 共享码位，但表意形状不同，它们使用完全不同的字体。

 下面的 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 示例使用 `fr-CA` language 特性指定加拿大法语。

```xaml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 支持所有 Unicode 功能，包括代理项。 只要字符集可以映射到 Unicode，就支持该字符集。 例如，GB18030 中引入了某些可映射到中文、日语和朝鲜语 (CFK) 扩展 A 和 B 以及代理项对的字符，因此完全受支持。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序可以使用 <xref:System.Globalization.StringInfo> 来操作字符串，而无需了解它们是否具有代理项对或组合字符。

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>使用 XAML 设计国际用户界面
 本部分介绍 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 编写应用程序时应考虑的一些功能。

<a name="intl_text"></a>
### <a name="international-text"></a>国际化文本
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包括针对所有 Microsoft .NET Framework 支持的书写系统的内置处理。

 目前支持以下脚本：

- 阿拉伯语

- 孟加拉语

- 梵语

- 西里尔语

- 希腊语

- 古吉拉特语

- 果鲁穆奇语

- 希伯来语

- 表意文字脚本

- 卡纳达语

- 老挝语

- 拉丁语

- 马拉雅拉姆语

- 蒙古语

- 奥里亚语

- 叙利亚语

- 泰米尔语

- 泰卢固语

- 塔安那文

- 泰语*

- 藏语

 *此版本支持显示和编辑泰语文本，但不支持断词。

 目前不支持以下脚本：

- 高棉语

- 古朝鲜语

- 缅甸

- 僧伽罗语

 所有书写系统引擎都支持 OpenType 字体。 OpenType 字体可以包含 OpenType 布局表，它们使字体创建者能够设计更好的国际化和高端版式字体。 OpenType 字体布局表包含有关符号替换、标志符号定位、对齐和基线定位的信息，使文本处理应用程序能够改进文本布局。

 OpenType 字体允许使用 Unicode 编码处理大字形集。 这种编码享有广泛的国际支持，并支持版式字形变体。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文本呈现由支持分辨率独立性的 Microsoft ClearType 子像素技术提供支持。 这极大地提高了可读性，并为所有脚本提供了支持高质量杂志样式文档的功能。

<a name="intl_layout"></a>
### <a name="international-layout"></a>国际化布局
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一种支持水平、双向和垂直布局的简便方式。 在演示框架中， <xref:System.Windows.FrameworkElement.FlowDirection%2A> 属性可用于定义布局。 流方向模式包括：

- *LeftToRight* - 适用于拉丁语和东亚语等语言的水平布局。

- *RightToLeft* - 适用于阿拉伯语和希伯来语等语言的双向布局。

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>开发可本地化的应用程序
 编写供全球使用的应用程序时，应牢记应用程序必须可本地化。 以下主题指出了若干注意事项。

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>多语言用户界面
  (MUI) 的多语言用户界面是 Microsoft 支持，可将 Ui 从一种语言切换到另一种语言。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序使用程序集模型来支持 MUI。 一个应用程序包含非特定语言程序集和与语言相关的附属资源程序集。 入口点是主程序集中的托管 .EXE。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 资源加载器利用框架的资源管理器来支持资源查找和回退。 多个语言附属程序集使用同一个主程序集。 加载的资源程序集取决于 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> 当前线程的。

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>可本地化的用户界面
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 来定义它们 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的。 通过 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，开发人员可使用一组属性和逻辑指定对象的层次结构。 的主要用途 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 是开发 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序，但它可用于指定 (CLR) 对象的任何公共语言运行时的层次结构。 大多数开发人员都使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 来指定其应用程序 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ，并使用编程语言（例如 c #）来响应用户交互。

 从资源的角度来看， [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 旨在描述依赖于语言的文件 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 是一个资源元素，因此，其最终分发格式必须可本地化以支持国际语言。 由于 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 无法处理事件，因此许多 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 应用程序都包含用于执行此操作的代码块。 有关详细信息，请参阅 [XAML 概述 (WPF) ](../../../desktop-wpf/fundamentals/xaml.md)。 当 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件被标记化为 XAML 的 BAML 形式时，代码将被去除并编译到不同的二进制文件中。 BAML 形式的 XAML 文件、图像以及其他类型的托管资源对象将嵌入附属资源程序集中，该程序集可本地化为其他语言，如果不需要进行本地化，以上各项就会嵌入主程序集中。

> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序支持所有 FrameworkCLR 资源，包括字符串表、图像等。

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>生成可本地化的应用程序
 本地化是指适应 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 不同的文化。 若要使 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序可本地化，开发人员需要将所有可本地化的资源生成到一个资源程序集中。 资源程序集本地化为不同的语言，代码隐藏使用资源管理 API 进行加载。 应用程序所需的文件之一 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是项目文件 () 。 应用程序中使用的所有资源都应包括在项目文件中。 以下 .csproj 文件示例演示如何执行此操作。

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 若要在应用程序中使用资源，请实例化 <xref:System.Resources.ResourceManager> 并加载要使用的资源。 下面的示例演示如何执行此操作。

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>在本地化的应用程序中使用 ClickOnce
 ClickOnce 是 Visual Studio 2005 附带的一种新的 Windows 窗体部署技术。 通过该技术可安装应用程序和升级 Web 应用程序。 对使用 ClickOnce 部署的应用程序进行本地化后，只能在本地化的区域性中查看该应用程序。 例如，如果已部署的应用程序本地化为日语，则只能在日语版 Microsoft Windows 上查看该应用程序。 这会带来一个问题，因为它是日语用户运行英语版本的 Windows 的常见方案。

 此问题的解决方案是设置非特定语言回退特性。 应用程序开发人员可选择从主程序集中删除资源，并指定可在特定区域性对应的附属程序集中找到该资源。 若要控制此过程，请使用 <xref:System.Resources.NeutralResourcesLanguageAttribute> 。 类的构造函数 <xref:System.Resources.NeutralResourcesLanguageAttribute> 具有两个签名，一个签名使用 <xref:System.Resources.UltimateResourceFallbackLocation> 参数来指定 <xref:System.Resources.ResourceManager> 应提取回退资源的位置：主程序集或附属程序集。 下面的示例演示如何使用此特性。 对于最终回退位置，代码会导致在 <xref:System.Resources.ResourceManager> 当前正在执行的程序集的目录的 "正在执行" 子目录中查找资源。

```csharp
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>另请参阅

- [WPF 全球化和本地化概述](wpf-globalization-and-localization-overview.md)
