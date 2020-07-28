---
title: 自定义依赖项属性
description: 了解在 Windows Presentation Foundation 中实现属性的步骤，以及用于提高属性的性能、可用性或通用性的选项。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- implementing [WPF], wrappers
- registering properties [WPF]
- properties [WPF], metadata
- metadata [WPF], for properties
- custom dependency properties [WPF]
- properties [WPF], registering
- wrappers [WPF], implementing
- dependency properties [WPF], custom
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
ms.openlocfilehash: b082340afb8b1a814fc5923126aa58183d43bc01
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168150"
---
# <a name="custom-dependency-properties"></a>自定义依赖项属性

本主题介绍了 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 应用程序开发者和组件作者想要创建自定义依赖属性的原因，并介绍了一些可以提高属性的性能、可用性或通用性的实现步骤以及实现选项。

<a name="prerequisites"></a>

## <a name="prerequisites"></a>先决条件

本主题假设你作为 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 类的现有依赖属性的使用者已经对依赖属性有所了解，并且已经阅读了[依赖属性概述](dependency-properties-overview.md)主题。 若要理解本主题中的示例，还应当了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 并知道如何编写 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序。

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>什么是依赖属性？

您可以通过将其实现为依赖属性，使其成为公共语言运行时（CLR）属性，以支持样式设置、数据绑定、继承、动画和默认值。 依赖属性是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 通过调用 <xref:System.Windows.DependencyProperty.Register%2A> 方法（或 <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> ），并由 <xref:System.Windows.DependencyProperty> 标识符字段支持的属性，注册到属性系统。 依赖项属性只能由类型使用 <xref:System.Windows.DependencyObject> ，但 <xref:System.Windows.DependencyObject> 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 类层次结构中非常高，因此中可用的大多数类 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 都可以支持依赖项属性。 有关依赖属性以及在此 SDK 中描述它们的一些术语和约定的详细信息，请参阅[依赖属性概述](dependency-properties-overview.md)。

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>依赖属性示例

在类上实现的依赖属性的示例 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包括 <xref:System.Windows.Controls.Control.Background%2A> 属性、 <xref:System.Windows.FrameworkElement.Width%2A> 属性和 <xref:System.Windows.Controls.TextBox.Text%2A> 属性，等等。 类公开的每个依赖项属性都具有一个对应的公共静态字段 <xref:System.Windows.DependencyProperty> ，该类型在同一类上公开。 这是依赖属性的标识符。 此标识符的命名约定为：依赖属性名称后面加上字符串 `Property`。 例如，属性对应的 <xref:System.Windows.DependencyProperty> 标识符字段 <xref:System.Windows.Controls.Control.Background%2A> 是 <xref:System.Windows.Controls.Control.BackgroundProperty> 。 该标识符存储有关已注册的依赖属性的信息，以后会将该标识符用于涉及依赖属性的其他操作，如调用 <xref:System.Windows.DependencyObject.SetValue%2A> 。

如[依赖属性概述](dependency-properties-overview.md)中所述，中的所有依赖属性 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] （大多数附加属性除外）也是 CLR 属性，因为 "包装器" 实现。 因此，可以从代码中获取或设置依赖属性，方法是调用定义包装的 CLR 访问器，方法与使用其他 CLR 属性的方式相同。 作为已建立的依赖项属性的使用者，通常不使用 <xref:System.Windows.DependencyObject> 方法 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> ，这是基础属性系统的连接点。 相反，CLR 属性的现有实现已 <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> 在属性的和包装实现中调用了，并 `get` `set` 适当地使用了标识符字段。 若要自己实现自定义依赖属性，则需要使用类似的方法定义包装器。

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>应该何时实现依赖属性？

在类上实现属性时，只要类派生自 <xref:System.Windows.DependencyObject> ，就可以选择使用标识符来备份属性， <xref:System.Windows.DependencyProperty> 从而使其成为依赖属性。 不必总是将属性实现为依赖属性，这不一定合适，具体取决于方案需要。 有时，使用私有字段支持属性的通常方法已足够满足需求。 但是，如果要使属性支持以下一个或多个 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能，则应该将属性实现为依赖属性：

- 需要可以在样式中设置属性。 有关详细信息，请参阅[样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。

- 需要属性支持数据绑定。 有关数据绑定依赖属性的详细信息，请参阅[绑定两个控件的属性](../data/how-to-bind-the-properties-of-two-controls.md)。

- 需要可以使用动态资源引用设置属性。 有关详细信息，请参阅 [XAML 资源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。

- 需要从元素树中的父元素自动继承属性值。 在这种情况下，请使用方法进行注册 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> ，即使你还创建了用于 CLR 访问的属性包装。 有关详细信息，请参阅[属性值继承](property-value-inheritance.md)。

- 需要属性可以进行动画处理。 有关详细信息，请参阅 [动画概述](../graphics-multimedia/animation-overview.md)。

- 需要属性系统在先前的值因属性系统、环境或用户执行的操作而发生更改，或者因读取和使用样式而发生更改时进行报告。 通过使用属性元素据，属性可以指定回调方法，每次属性系统确定属性值已明确改动时将调用此回调方法。 与此相关的一个概念是属性值强制转换。 有关详细信息，请参阅[依赖属性回调和验证](dependency-property-callbacks-and-validation.md)。

- 需要使用同时也被 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 进程使用的已建立的元数据约定，例如报告更改属性值是否应需要布局系统重新安排元素的可视内容。 或者需要能够使用元素据替代，以便派生类可以更改基于元数据的特性，例如默认值。

- 您希望使用自定义控件的属性来接收 Visual Studio WPF 设计器支持，如 "**属性**" 窗口编辑。 有关详细信息，请参阅[控件创作概述](../controls/control-authoring-overview.md)。

检查这些方案时，还应考虑是否可以通过替代现有依赖属性的元素据而不是通过实现一个全新的属性来实现方案。 元素据替代是否可行取决于方案以及方案与现有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 依赖属性和类中的实现的相似度。 有关替代现有属性上的元素据的详细信息，请参阅[依赖属性元素据](dependency-property-metadata.md)。

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>定义依赖属性的检查清单

定义依赖属性包含 4 个不同的概念。 这些概念并不一定是严格的过程步骤，因为其中一些概念在实现中会被合并为一行代码：

- （可选）创建依赖属性的属性元素据。

- 在属性系统中注册属性名称，并指定所有者类型和属性值类型。 此外，还应指定属性元素据（如果用到）。

- <xref:System.Windows.DependencyProperty>将标识符定义为 `public` `static` `readonly` 所有者类型上的字段。

- 定义一个 CLR "包装器" 属性，该属性的名称与依赖项属性的名称匹配。 实现 CLR "包装器" 属性的 `get` 和 `set` 访问器，以连接到支持它的依赖属性。

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>在属性系统中注册属性

为使属性成为依赖属性，必须在属性系统维护的表中注册该属性，并为属性指定一个唯一标识符。此唯一标识符会用作后续属性系统操作的限定符。 这些操作可能是内部操作，也可能是你自己的代码调用属性系统 Api。 若要注册属性，请在 <xref:System.Windows.DependencyProperty.Register%2A> 类（类中，但在任何成员定义之外）的正文中调用方法。 方法调用还提供标识符字段 <xref:System.Windows.DependencyProperty.Register%2A> 作为返回值。 <xref:System.Windows.DependencyProperty.Register%2A>调用在其他成员定义之外完成的原因是，使用此返回值将 `public` `static` `readonly` 类型为的字段分配 <xref:System.Windows.DependencyProperty> 为类的一部分。 此字段会作为依赖属性的标识符。

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>依赖属性命名约定

必需完全遵循已有的依赖属性命名约定，例外情况除外。

依赖属性本身将有一个基本名称 "AquariumGraphic"，如本示例所示，它作为的第一个参数 <xref:System.Windows.DependencyProperty.Register%2A> 。 此名称在每个注册类型内必须唯一。 通过基类型继承的依赖属性会被视为注册类型的已有部分；无法再次注册已继承属性的名称。 但是，即使不继承依赖属性，也有方法可将类添加为依赖属性的所有者；有关详细信息，请参阅[依赖属性元素据](dependency-property-metadata.md)。

创建标识符字段时，按注册时的属性名称命名此字段，再加上后缀 `Property`。 此字段是依赖项属性的标识符，稍后会将其用作所需的和调用的输入，由您自己的代码通过您自己的代码 <xref:System.Windows.DependencyObject.SetValue%2A> <xref:System.Windows.DependencyObject.GetValue%2A> 访问属性，由您允许的任何外部代码访问，由属性系统提供，并可能由 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 处理器提供。

> [!NOTE]
> 在类的主体中定义依赖属性是典型的实现，但也可以在类静态构造函数中定义依赖属性。 需要多行代码来初始化依赖属性时，此方法会很有用。

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>实现“包装器”

包装实现应 <xref:System.Windows.DependencyObject.GetValue%2A> 在实现中调用 `get` ，而 <xref:System.Windows.DependencyObject.SetValue%2A> 在实现中，将在 `set` 此处显示初始注册调用和字段，以清楚地说明这一点。

除异常情况以外，包装实现只能 <xref:System.Windows.DependencyObject.GetValue%2A> 分别执行和 <xref:System.Windows.DependencyObject.SetValue%2A> 操作。 其原因请参阅 [XAML 加载和依赖属性](xaml-loading-and-dependency-properties.md)主题。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 类上提供的所有现有公共依赖属性都使用这一简单的包装器实现模型；大多数情况下，依赖属性工作原理的复杂性本质上在于它是属性系统的行为，还是通过其他概念（例如强制转换或通过属性元数据进行的属性更改回调）实现的行为。

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

同样，按照约定，包装属性的名称必须与所选名称相同，并指定为注册该属性的调用的第一个参数 <xref:System.Windows.DependencyProperty.Register%2A> 。 如果属性不遵从此约定，尽管不一定会禁用所有可能的用法，但你会遇到几个比较突出的问题：

- 样式和模板的某些方面不起作用。

- 大多数工具和设计器必须依赖命名约定，才能正确序列化 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 或在每个属性级别提供设计器环境帮助。

- 当前的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 加载程序实现完全绕过包装器，并依赖于处理属性值时的命名约定。 有关详细信息，请参阅 [XAML 加载和依赖属性](xaml-loading-and-dependency-properties.md)。

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>新依赖属性的属性元数据

注册依赖属性时，通过属性系统进行注册会创建一个存储属性特征的元素据对象。 如果将属性注册到的简单签名，则其中许多特性都具有默认设置 <xref:System.Windows.DependencyProperty.Register%2A> 。 通过的其他签名， <xref:System.Windows.DependencyProperty.Register%2A> 可以指定注册属性时所需的元数据。 为依赖属性使用的最常见元数据是为其使用默认值。该默认值适用于使用此属性的新实例。

如果要创建在的派生类上存在的依赖项属性 <xref:System.Windows.FrameworkElement> ，则可以使用更专用的元数据类， <xref:System.Windows.FrameworkPropertyMetadata> 而不是基类 <xref:System.Windows.PropertyMetadata> 。 类的构造函数 <xref:System.Windows.FrameworkPropertyMetadata> 有多个签名，你可以在其中组合指定各种元数据特征。 如果只想指定默认值，请使用采用类型为的单个参数的签名 <xref:System.Object> 。 将该对象参数传递为你的属性的特定于类型的默认值（提供的默认值必须是你在调用中提供的参数的类型 `propertyType` <xref:System.Windows.DependencyProperty.Register%2A> ）。

对于 <xref:System.Windows.FrameworkPropertyMetadata> ，你还可以为属性指定元数据选项标志。 注册后这些标记会转换为属性元素据上的不同属性，并用于将某些条件传送给布局引擎等其他进程。

#### <a name="setting-appropriate-metadata-flags"></a>设置合适的元数据标记

- 如果您的属性（或其值的更改）影响 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ，特别是影响布局系统如何调整页面中元素的大小或呈现元素，请设置以下一个或多个标志： <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> 、 <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> 、 <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> 。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>指示对此属性的更改需要更改 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 呈现，其中包含对象在父对象中可能需要更多或更少的空间。 例如，“宽度”属性应该设置此标记。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>指示对此属性的更改需要更改呈现，这 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 通常不需要在专用空间中进行更改，而是指示空间中的位置已更改。 例如，“对齐”属性应该设置此标记。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>指示发生了其他一些更改，这些更改不会影响布局和度量值，但需要其他呈现。 更改现有元素的颜色的属性便是一个示例，例如“背景”。

  - 对属性系统或布局回调进行自己的替代实现时，这些标记通常用作元数据中的协议。 例如， <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> <xref:System.Windows.UIElement.InvalidateArrange%2A> 如果实例的任何属性报告值更改并 <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> `true` 在其元数据中具有相同的值，则可能会调用回调。

- 超出上述所需大小时，某些属性可能会影响所含父元素的呈现特征。 示例是 <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> 在流文档模型中使用的属性，在该模型中，对该属性的更改可以更改包含该段落的流文档的总体呈现。 使用 <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> 或 <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> 标识您自己的属性中的相似事例。

- 默认情况下，依赖属性支持数据绑定。 在无实际的数据绑定方案或大型对象的数据绑定性能构成问题的情况下，可有意禁用数据绑定。

- 默认情况下， <xref:System.Windows.Data.Binding.Mode%2A> 依赖属性的数据绑定默认为 <xref:System.Windows.Data.BindingMode.OneWay> 。 始终可以将绑定更改为 <xref:System.Windows.Data.BindingMode.TwoWay> 每个绑定实例; 有关详细信息，请参阅[指定绑定的方向](../data/how-to-specify-the-direction-of-the-binding.md)。 但作为依赖属性作者，你可以选择在默认情况下将属性设置为使用 <xref:System.Windows.Data.BindingMode.TwoWay> 绑定模式。 现有依赖属性的一个示例是 <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType> ; 此属性的方案是 <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> 设置逻辑和 <xref:System.Windows.Controls.MenuItem> 与默认主题样式交互的组合。 <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>属性逻辑使用数据绑定来根据其他状态属性和方法调用来维护属性的状态。 默认绑定的另一个示例属性 <xref:System.Windows.Data.BindingMode.TwoWay> 是 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 。

- 还可以通过设置标志来启用自定义依赖属性中的属性继承 <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> 。 在父元素和子元素具有相同属性的情况中，属性继承非常有用，它可以使子元素将该特定属性值设置为与父元素设置的值相同。 一个示例可继承属性是 <xref:System.Windows.FrameworkElement.DataContext%2A> ，它用于绑定操作，以便为数据呈现启用重要的主-从方案。 通过使 <xref:System.Windows.FrameworkElement.DataContext%2A> 可继承，任何子元素也会继承该数据上下文。 因为使用了属性值继承，你可以在页面或应用程序根目录上指定数据上下文，而无需对所有可能子元素中的绑定重新指定上下文。 <xref:System.Windows.FrameworkElement.DataContext%2A>也是一个很好的示例，用于说明继承重写默认值，但它始终可以在任何特定子元素上本地设置;有关详细信息，请参阅对[分层数据使用主-从模式](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。 属性值继承确实可能存在性能成本，因此应谨慎使用；有关详细信息，请参阅[属性值继承](property-value-inheritance.md)。

- 设置 <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> 标志以指示是否应通过导航日志服务检测或使用依赖属性。 此属性是一个示例，即， <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> 导航日志记录历史记录时，选择控件中选定的任何项都应持久保存。

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>只读依赖项属性

可以定义只读的依赖属性。 但是，为何将属性定义为只读的情况略有不同，其过程与在属性系统中注册属性并公开标识符相同。 有关详细信息，请参阅[只读依赖属性](read-only-dependency-properties.md)。

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>集合类型依赖项属性

集合类型依赖属性要考虑一些其他实现问题。 有关详细信息，请参阅[集合类型依赖属性](collection-type-dependency-properties.md)。

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>依赖属性安全注意事项

依赖属性应声明为公共属性。 依赖属性标识符字段应声明为公共静态字段。 即使您尝试声明其他访问级别（如受保护），也始终可以通过标识符与属性系统 Api 一起访问依赖属性。 即使是受保护的标识符字段也可能是可访问的，因为元数据报告或值确定 Api 是属性系统的一部分，例如 <xref:System.Windows.LocalValueEnumerator> 。 有关详细信息，请参阅[依赖属性的安全性](dependency-property-security.md)。

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>依赖属性和类构造函数

托管代码编程（通常通过FxCop 等代码分析工具强制执行）的一般原则是：类构造函数不应调用虚方法。 这是因为构造函数可以作为派生的类构造函数的基本初始化来调用，并且可能会在所构造的对象实例不完全初始化状态下通过构造函数输入虚方法。 从派生自的任何类派生时 <xref:System.Windows.DependencyObject> ，应注意到属性系统本身在内部调用并公开了虚方法。 这些虚方法属于 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 属性系统服务。 替代方法会使派生类参与值确定。 为避免运行时初始化出现潜在问题，，不应该在类的构造函数中设置依赖属性值，除非遵循特定的构造函数模式进行操作。 有关详细信息，请参阅 [DependencyObject 的安全构造函数模式](safe-constructor-patterns-for-dependencyobjects.md)。

## <a name="see-also"></a>请参阅

- [依赖项属性概述](dependency-properties-overview.md)
- [依赖项属性元数据](dependency-property-metadata.md)
- [控件创作概述](../controls/control-authoring-overview.md)
- [集合类型依赖项属性](collection-type-dependency-properties.md)
- [依赖项属性的安全性](dependency-property-security.md)
- [XAML 加载和依赖项属性](xaml-loading-and-dependency-properties.md)
- [DependencyObject 的安全构造函数模式](safe-constructor-patterns-for-dependencyobjects.md)
