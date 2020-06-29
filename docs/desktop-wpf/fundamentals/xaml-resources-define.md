---
title: 定义 XAML 资源
description: 了解适用于 .NET Core 的 WPF 中的 XAML 资源。 了解 XAML 资源的类型，并学习如何定义 XAML 资源。
author: adegeo
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: f8eaf3fd931aa6804b0b9a9c19c6bcc042678ebf
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325719"
---
# <a name="overview-of-xaml-resources"></a>XAML 资源概述

资源是可以在应用中的不同位置重复使用的对象。 资源的示例包括画笔和样式。 本概述介绍如何使用 Extensible Application Markup Language (XAML) 中的资源。 你还可以使用代码创建和访问资源。

> [!NOTE]
> 本文所述的 XAML 资源与*应用资源*不同，后者通常指添加到应用中的文件，例如内容、数据或嵌入式文件。

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>使用 XAML 中的资源

下面的示例将 <xref:System.Windows.Media.SolidColorBrush> 定义为页面根元素上的资源。 该示例随后引用资源，并使用它来设置多个子元素的属性，其中包括 <xref:System.Windows.Shapes.Ellipse>、<xref:System.Windows.Controls.TextBlock> 和 <xref:System.Windows.Controls.Button>。

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

每个框架级元素（<xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>）都具有 <xref:System.Windows.FrameworkElement.Resources%2A> 属性，该属性是包含已定义资源的 <xref:System.Windows.ResourceDictionary> 类型。 你可以在任何元素上定义资源，例如 <xref:System.Windows.Controls.Button>。 但是，最常在根元素上定义资源，本示例中的根元素为 <xref:System.Windows.Controls.Page>。

资源字典中的每个资源都必须具有唯一键。 在标记中定义资源时，可通过 [x:Key 指令](../xaml-services/xkey-directive.md)来分配唯一键。 通常情况下，这个键是一个字符串；但是，也可使用相应的标记扩展将其设置为其他对象类型。 资源的非字符串键用于 WPF 中的某些功能区，尤其是样式、组件资源和数据样式。

你可以使用具有资源标记扩展语法（指定资源的键名）的已定义资源。 例如，将资源用作另一个元素上的属性的值。

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

在前面的示例中，如果 XAML 加载程序处理 <xref:System.Windows.Controls.Button> 上 <xref:System.Windows.Controls.Control.Background%2A> 属性的值 `{StaticResource MyBrush}`，则资源查找逻辑会首先检查 <xref:System.Windows.Controls.Button> 元素的资源字典。 如果 <xref:System.Windows.Controls.Button> 没有资源键 `MyBrush` 的定义（在该示例中没有；其资源集合为空），则查找逻辑接下来会检查 <xref:System.Windows.Controls.Button> 的父元素，即 <xref:System.Windows.Controls.Page>。 如果在 <xref:System.Windows.Controls.Page> 根元素上定义资源，则 <xref:System.Windows.Controls.Page> 的逻辑树中的所有元素都可以访问它。 而且，你可以重复使用相同的资源来设置接受与该资源所表示类型相同的类型的所有属性的值。 在前面的示例中，同一 `MyBrush` 资源设置两个不同的属性：<xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A> 和 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>。

## <a name="static-and-dynamic-resources"></a>静态和动态资源

资源可引用为静态资源或动态资源。 可通过使用 [StaticResource 标记扩展](../../framework/wpf/advanced/staticresource-markup-extension.md)或 [DynamicResource 标记扩展](../../framework/wpf/advanced/dynamicresource-markup-extension.md)创建引用。 标记扩展是 XAML 的一项功能，可以通过使用标记扩展来处理属性字符串并将对象返回到 XAML 加载程序，从而指定对象引用。 有关标记扩展行为的详细信息，请参阅 [标记扩展和 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。

使用标记扩展时，通常会以字符串的形式提供一个或多个由该特定标记扩展处理的参数。 [StaticResource 标记扩展](../../framework/wpf/advanced/staticresource-markup-extension.md)通过在所有可用的资源字典中查找键值来处理键。 处理在加载期间进行，即加载过程需要分配属性值时。 [DynamicResource 标记扩展](../../framework/wpf/advanced/dynamicresource-markup-extension.md)则通过创建表达式来处理键，而且表达式会保持未计算状态，直至应用运行为止。当应用实际运行时，表达式会进行计算并提供一个值。

在引用某个资源时，下列注意事项可能会对于使用静态资源引用还是使用动态资源引用产生影响：

- 确定如何为应用创建资源的整体设计（在每页上、在应用程序中、在宽松的 XAML 中或在仅包含资源的程序集中）时，请考虑以下事项：

- 应用的功能。 实时更新资源是否为应用要求的一部分？
- 该资源引用类型的相应查找行为。
- 特定的属性或资源类型，以及这些类型的本机行为。

## <a name="static-resources"></a>静态资源

在以下情况下，最适合使用静态资源引用：

- 应用设计将其大多数资源集中到页面或应用程序级资源字典中。 静态资源引用不基于运行时行为（例如重载页面）重新计算。 因此，根据资源和应用设计，如果避免不必要地使用大量动态资源引用，可能会一定程度地提高性能。

- 要设置不在 <xref:System.Windows.DependencyObject> 或 <xref:System.Windows.Freezable> 上的属性的值。

- 要创建的资源字典将编译成 DLL，并将打包为应用的一部分或在应用间共享。

- 要为自定义控件创建主题，并要定义在主题中使用的资源。 在这种情况下，通常不希望执行动态资源引用查找行为，而是希望执行静态资源引用行为，以确保查找可预测并自包含到主题中。 使用动态资源引用时，即使主题中的引用也会在运行时前保持未计算状态。 而且，主题可能会得到应用，但某个本地元素仍会重新定义主题正尝试引用的键，并且该本地元素在查找期间会排在主题之前。 如果发生这种情况，主题的行为将偏离预期方式。

- 要使用资源设置大量依赖属性。 依赖属性会通过属性系统启用有效值缓存功能；因此，如果为可在加载时进行计算的依赖属性提供了值，则该依赖属性不必检查是否存在重新计算的表达式并可返回最后一个有效值。 此项技术可以提高性能。

- 想为所有使用者更改基础资源，或想通过使用 [x:Shared 属性](../xaml-services/xshared-attribute.md)为每个使用者维护单独的可写实例。

### <a name="static-resource-lookup-behavior"></a>静态资源查找行为

下面介绍属性或元素引用静态资源时自动发生的查找过程：

01. 查找进程在用于设置属性的元素所定义的资源字典中查找请求的键。

01. 查找过程随后会向上遍历逻辑树，以查找父元素及其资源字典。 此过程到达根元素后才会停止。

01. 检查应用资源。 应用资源就是 <xref:System.Windows.Application> 对象为 WPF 应用定义的资源字典中的资源。

从资源字典中进行的静态资源引用必须引用已在资源引用前进行过词法定义的资源。 静态资源引用无法解析前向引用。 因此，请设计资源字典的结构，以便在每个相应资源字典的开头或邻近开头的位置定义资源。

静态资源查找可以扩展到主题或系统资源中，但此查找受支持只是因为 XAML 加载程序推迟了请求。 为了让页面加载时的运行时主题正确地应用到应用，这种延迟是必需的。 但是，不建议使用对已知仅在主题中存在或作为系统资源存在的键的静态资源引用，因为如果用户实时更改主题，不会重新计算此类引用。 请求主题或系统资源时，动态资源引用更为可靠。 例外情况是当主题元素自身请求另一个资源。 出于上述原因，这些引用应该是静态资源引用。

因找不到静态资源引用而引发的异常行为各不相同。 如果资源被延迟，则异常会在运行时发生。 如果资源未延迟，则异常会在加载时发生。

## <a name="dynamic-resources"></a>动态资源

在以下情况下，最适合使用动态资源：

- 资源（包括系统资源或用户可设置的资源）的值取决于直到运行时才知道的条件。 例如，你可以创建 setter 值（引用由 <xref:System.Windows.SystemColors>、<xref:System.Windows.SystemFonts> 或 <xref:System.Windows.SystemParameters> 公开的系统属性）。 这些值是真正的动态值，因为它们最终来自用户和操作系统的运行时环境。 或许还拥有可能会发生变化的应用程序级主题，而页面级资源访问也必须捕获其中的变化。

- 要为自定义控件创建或引用主题样式。

- 打算在应用生存期内调整 <xref:System.Windows.ResourceDictionary> 的内容。

- 拥有存在相互依赖关系且可能需要进行前向引用的复杂资源结构。 静态资源引用不支持前向引用，但动态资源引用支持，因为资源在运行时之前不需要计算，所以前向引用是一个不相关的概念。

- 要引用从编译或工作集的角度来看很大的资源，而且该资源在页面加载时可能不会立即使用。 页面加载时，始终会从 XAML 加载静态资源引用。 但是，动态资源引用在使用前不会加载。

- 要创建的样式的 setter 值可能来自受主题或其他用户设置影响的其他值。

- 要将资源应用于可能会在应用生存期内在逻辑树中重定父级的元素。 父级更改后，资源查找范围也可能会随之更改；因此，如果希望重定父级的元素的资源基于新范围重新进行计算，请始终使用动态资源引用。

### <a name="dynamic-resource-lookup-behavior"></a>动态资源查找行为

如果调用 <xref:System.Windows.FrameworkElement.FindResource%2A> 或 <xref:System.Windows.FrameworkElement.SetResourceReference%2A>，则动态资源引用的资源查找行为会与代码中的查找行为并行执行：

01. 查找在用于设置属性的元素所定义的资源字典中查找请求的键：

    - 如果元素定义 <xref:System.Windows.FrameworkElement.Style%2A> 属性，则该元素的 <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName> 将检查其 <xref:System.Windows.Style.Resources> 字典。

    - 如果元素定义 <xref:System.Windows.Controls.Control.Template%2A> 属性，则检查该元素的 <xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName> 字典。

01. 查找会向上遍历逻辑树，以查找父元素及其资源字典。 此过程到达根元素后才会停止。

01. 检查应用资源。 应用资源就是 <xref:System.Windows.Application> 对象为 WPF 应用定义的资源字典中的资源。

01. 检查主题资源字典中当前处于活动状态的主题。 如果主题在运行时发生更改，则会重新计算值。

01. 检查系统资源。

异常行为（如果有）各不相同：

- 如果 <xref:System.Windows.FrameworkElement.FindResource%2A> 调用请求了某个资源但未找到该资源，则会引发异常。

- 如果 <xref:System.Windows.FrameworkElement.TryFindResource%2A> 调用请求了某个资源但未找到该资源，不会引发任何异常，并且返回的值为 `null`。 如果要设置的属性不接受 `null`，则仍有可能引发更深的异常（取决于要设置的单独属性）。

- 如果 XAML 中的动态资源引用请求了某个资源但未找到该资源，则行为取决于常规属性系统。 常规行为即存在资源的级别上没有发生属性设置操作时执行的行为。 例如，如果尝试使用无法计算的资源来设置个别按钮元素上的背景，则值设置操作不会产生任何结果，但有效值可能仍来自属性系统和值优先级中的其他参与者。 例如，背景值可能仍来自在本地定义的某个按钮样式，或来自主题样式。 对于并非由主题样式定义的属性，资源计算失败后的有效值可能来自属性元数据中的默认值。

### <a name="restrictions"></a>限制

动态资源引用存在一些重要限制。 必须至少满足以下条件之一：

- 要设置的属性必须是 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 上的属性。 该属性必须由 <xref:System.Windows.DependencyProperty> 支持。

- 该引用用于 `StyleSetter` 内的值。

- 要设置的属性必须是 <xref:System.Windows.Freezable>（以 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 属性的值或 <xref:System.Windows.Setter> 值的形式提供）上的属性。

由于要设置的属性必须是 <xref:System.Windows.DependencyProperty> 或 <xref:System.Windows.Freezable> 属性，大多数属性更改都可以传播到 UI，这是因为属性更改（更改的动态资源值）会经由属性系统确认。 大多数控件都包含相应的逻辑；当 <xref:System.Windows.DependencyProperty> 有所更改且该属性可能会影响布局时，该逻辑将强制使用控件的其他布局。 但是，并不保证所有使用 [DynamicResource 标记扩展](../../framework/wpf/advanced/dynamicresource-markup-extension.md)作为其值的属性都能在 UI 中提供实时更新。 此功能可能仍会因属性、属性所属的类型，甚至应用的逻辑结构而异。

## <a name="styles-datatemplates-and-implicit-keys"></a>样式、DataTemplate 和隐式键

尽管 <xref:System.Windows.ResourceDictionary> 中的所有项都必须具有键，但这并不意味着所有资源都必须具有显式 `x:Key`。 多种对象类型在定义为资源时都支持隐式键，其键值会与另一属性的值绑定。 这类键被称为隐式键，而 `x:Key` 属性为显式键。 任何隐式键都可通过指定显式键来覆盖。

关于资源，一个重要的方案就是用于定义 <xref:System.Windows.Style>。 事实上，<xref:System.Windows.Style> 几乎总会作为资源字典中的条目进行定义，因为样式在本质上可供重复使用。 有关样式的详细信息，请参阅[样式设置和模板化](styles-templates-overview.md)。

控件样式可通过隐式键来创建和引用。 用于定义控件默认外观的主题样式依赖于该隐式键。 从请求的角度来看，隐式键是控件本身的 <xref:System.Type>。 从定义资源的角度来看，隐式键是样式的 <xref:System.Windows.Style.TargetType%2A>。 因此，如果要创建自定义控件的主题或要创建会与现有主题样式交互的样式，则无需为该 <xref:System.Windows.Style> 指定 [x:Key 指令](../xaml-services/xkey-directive.md)。 另外，如果想要使用主题样式，则根本无需指定任何样式。 例如，即使 <xref:System.Windows.Style> 资源似乎没有键，以下样式定义仍起作用：

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

该样式确实具有一个键：隐式键 `typeof(System.Windows.Controls.Button)`。 在标记中，可以直接将 <xref:System.Windows.Style.TargetType%2A> 指定为类型名称（或者，可以选择使用 [{x:Type...}](../xaml-services/xtype-markup-extension.md) 返回 <xref:System.Type>）。

通过 WPF 使用的默认主题样式机制，即使 <xref:System.Windows.Controls.Button> 本身不尝试指定其 <xref:System.Windows.FrameworkElement.Style%2A> 属性或对样式的特定资源引用，该样式也将作为页面上 <xref:System.Windows.Controls.Button> 的运行时样式应用。 在页面中定义的样式位于查找序列中的靠前位置（在主题字典样式之前），其所用的键与主题字典样式的键相同。 可以在页面上的任意位置指定 `<Button>Hello</Button>`，使用 `Button` 的 <xref:System.Windows.Style.TargetType%2A> 定义的样式将应用于该按钮。 如果需要，仍可为此样式显式指定与 <xref:System.Windows.Style.TargetType%2A> 的类型值相同的键，以求在标记中清楚明示，但这是可选的。

如果 <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> 为 `true`，则样式的隐式键不会应用于控件。 （另请注意，<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> 可能被设置为控件类的本机行为的一部分，而不是在控件的实例上显式设置。）此外，为了支持在派生类方案中使用隐式键，控件必须替代 <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>（作为 WPF 的一部分提供的所有现有控件都包括此替代）。 有关样式、主题和控件设计的详细信息，请参阅[可样式化控件的设计指南](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md)。

<xref:System.Windows.DataTemplate> 也有一个隐式键。 <xref:System.Windows.DataTemplate> 的隐式键是 <xref:System.Windows.DataTemplate.DataType%2A> 属性值。 <xref:System.Windows.DataTemplate.DataType%2A> 也可以作为类型的名称来指定，而不是使用 [{x:Type...}](../xaml-services/xtype-markup-extension.md) 来显式指定。 有关详细信息，请参阅[数据模板化概述](../../framework/wpf/data/data-templating-overview.md)。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.ResourceDictionary>
- [应用程序资源](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [资源和代码](../../framework/wpf/advanced/resources-and-code.md)
- [定义和引用资源](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [应用程序管理概述](../../framework/wpf/app-development/application-management-overview.md)
- [x:Type 标记扩展](../xaml-services/xtype-markup-extension.md)
- [StaticResource 标记扩展](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [DynamicResource 标记扩展](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
