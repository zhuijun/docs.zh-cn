---
title: x:Name 指令
ms.date: 03/30/2017
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
ms.openlocfilehash: ddaa35b18d1c632fc49b18dabf0d992dc1c78fcc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549478"
---
# <a name="xname-directive"></a>x:Name 指令

在 XAML 名称范围中唯一标识 XAML 定义的元素。 当框架提供 Api 或实现在运行时访问 XAML 创建的对象图的行为时，可以将 XAML 名称范围及其唯一性模型应用于实例化的对象。

## <a name="xaml-attribute-usage"></a>XAML 属性用法

```xaml
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`XAMLNameValue`|符合 [XamlName 语法](xamlname-grammar.md)限制的字符串。|

## <a name="remarks"></a>备注

`x:Name`将应用于框架的后备编程模型后，该名称等效于保存构造函数返回的对象引用或实例的变量。

指令用法的值在 `x:Name` XAML 名称范围内必须是唯一的。 默认情况下，当由 .NET XAML 服务 API 使用时，主 XAML 名称范围将在单个 XAML 生产的 XAML 根元素上定义，并且包含该 XAML 生产中包含的元素。 可能出现在单个 XAML 生产内的其他离散 XAML 名称范围可以由框架定义，以解决特定方案。 例如，在 WPF 中，新的 XAML 名称范围由也在该 XAML 生产环境中定义的任何模板来定义和创建。 有关 XAML 名称范围 (为 WPF 编写但) 许多 XAML 名称范围概念相关的详细信息，请参阅 [WPF Xaml 名称范围](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes)。

通常， `x:Name` 不应在也使用的情况下应用 `x:Key` 。 由特定现有框架实现的 XAML 实现在和之间引入了替代概念 `x:Key` `x:Name` ，但这不是建议的做法。 在处理名称/键信息（如或）时，.NET XAML 服务不支持这种替换概念 <xref:System.Windows.Markup.INameScope> <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> 。

Permittance 的规则 `x:Name` 和名称唯一性强制可能由特定的实现框架定义。 但是，若要与 .NET XAML 服务一起使用，XAML 名称范围唯一性的框架定义应该与 <xref:System.Windows.Markup.INameScope> 本文档中的信息定义一致，并且应使用与信息应用位置相同的规则。 例如，实现将 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 各种标记元素分成不同的 <xref:System.Windows.NameScope> 范围，如资源字典、页面级别 XAML 创建的逻辑树、模板和其他延迟的内容，然后在每个 xaml 名称范围内强制执行 xaml 名称的唯一性。

对于使用 .NET XAML 服务 XAML 对象编写器的自定义类型， `x:Name` 可以建立或更改映射到类型的的属性。 通过 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 在类型定义代码中引用要映射的属性的名称来定义此行为。  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 是一个类型级特性。

Using.NET XAML 服务，可通过实现接口以非特定于框架的方式定义 XAML 名称范围支持的支持逻辑 <xref:System.Windows.Markup.INameScope> 。

## <a name="wpf-usage-notes"></a>WPF 用法说明

在 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 使用 XAML、分部类和代码隐藏的应用程序的标准生成配置下，指定的 `x:Name` 将成为当由标记编译生成任务处理时在基础代码中创建的字段的名称 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ，并且该字段包含对该对象的引用。 默认情况下，创建的字段为内部字段。 可以通过指定 [x:FieldModifier 属性](xfieldmodifier-directive.md)来更改字段访问权限。 在 WPF 和 Silverlight 中，序列是标记编译定义并命名分部类中的字段，但该值最初为空。 然后， `InitializeComponent` 从类构造函数中调用一个名为的生成方法。 `InitializeComponent` 包含 `FindName` 使用每个 `x:Name` 值的调用，此分部类的 XAML 定义部分中存在这些值作为输入字符串。 然后，将返回值分配给赞命名字段引用，以用通过 XAML 分析创建的对象填充字段值。 执行 `InitializeComponent` 时，可以直接使用/字段名称引用运行时对象关系图 `x:Name` ，而不必 `FindName` 在每次需要引用 XAML 定义的对象时都显式调用。

对于使用 Microsoft Visual Basic 目标的 WPF 应用程序，并包括包含生成操作的 XAML 文件 `Page` ，在编译过程中将创建一个单独的引用属性，该属性将 `WithEvents` 关键字添加到具有的所有元素 `x:Name` ，以支持 `Handles` 事件处理程序委托的语法。 此属性始终是公共的。 有关详细信息，请参阅 [Visual Basic 和 WPF 事件处理](/dotnet/desktop/wpf/advanced/visual-basic-and-wpf-event-handling)。

`x:Name` 在加载时，WPF XAML 处理器使用将名称注册到 XAML 名称范围，即使该页未通过生成操作进行标记编译 (例如，) 的资源字典的松散 XAML。 此行为的一个原因是， `x:Name` 绑定可能需要 <xref:System.Windows.Data.Binding.ElementName%2A> 。 有关详细信息，请参阅 [数据绑定概述](../data/data-binding-overview.md)。

如前所述， `x:Name` `Name` 在也使用的情况下，不应应用 (或) `x:Key` 。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> 具有将自身定义为 XAML 名称范围、返回未实现的或 null 值 <xref:System.Windows.Markup.INameScope> 作为执行此行为的方法的特殊行为。 如果 WPF XAML 分析器在 `Name` xaml 定义中遇到或 `x:Name` <xref:System.Windows.ResourceDictionary> ，则不会将该名称添加到任何 xaml 名称范围。 尝试从任何 XAML 名称范围和方法中查找该名称 `FindName` 将不会返回有效的结果。

### <a name="xname-and-name"></a>X：Name 和名称

很多 WPF 应用程序方案都可以避免使用 `x:Name` 特性，因为在 `Name` 默认 XAML 命名空间中为多个重要基类（如）指定的依赖项属性 <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> 满足此相同目的。 还有一些常见 XAML 和 WPF 方案，在这些方案中，代码访问 `Name` 框架级别上没有属性的元素是非常重要的。 例如，某些动画和情节提要支持类不支持 `Name` 属性，但通常需要在代码中引用这些类才能控制动画。 `x:Name`如果打算稍后从代码中引用它们，则应将指定为在 XAML 中创建的时间线和转换的属性。

如果在 <xref:System.Windows.FrameworkElement.Name%2A> 类上作为属性提供， <xref:System.Windows.FrameworkElement.Name%2A> 并且 `x:Name` 可作为属性互换使用，但如果在同一元素上同时指定了这两个异常，则会导致分析异常。 如果 XAML 是标记编译的，则异常将在标记编译中发生，否则会在加载时发生。

<xref:System.Windows.FrameworkElement.Name%2A> 可以使用 XAML 特性语法和使用中的代码进行设置 <xref:System.Windows.DependencyObject.SetValue%2A> 。请注意，在代码中设置该 <xref:System.Windows.FrameworkElement.Name%2A> 属性不会在已加载 xaml 的大多数情况下在 xaml 名称范围内创建代表字段引用。 不要尝试 <xref:System.Windows.FrameworkElement.Name%2A> 在代码中进行设置，而是 <xref:System.Windows.NameScope> 根据相应的名称范围使用代码中的方法。

<xref:System.Windows.FrameworkElement.Name%2A> 还可以通过对内部文本使用属性元素语法来设置，但这种情况并不常见。 相反， `x:Name` 不能在 XAML 属性元素语法中或使用代码中设置 <xref:System.Windows.DependencyObject.SetValue%2A> ; 它只能使用对象的属性语法进行设置，因为它是一个指令。

## <a name="silverlight-usage-notes"></a>Silverlight 使用说明

`x:Name` 对于 Silverlight，单独记录。 有关详细信息，请参阅 [XAML 命名空间 (x： ) 语言功能 (Silverlight) ](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [WPF 中的树](/dotnet/desktop/wpf/advanced/trees-in-wpf)
