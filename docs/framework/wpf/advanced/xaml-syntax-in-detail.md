---
title: XAML 语法详述
description: 了解用于描述 Windows Presentation Foundation 和其他使用 XAML 的框架的 XAML 语法元素的术语。
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- XAML [WPF], parsing of attributes
- parsing of attributes [WPF]
- XAML [WPF], markup extensions
- attached properties [WPF]
- tag syntax [XAML]
- markup extensions [WPF]
- XAML [WPF], object element syntax
- XAML [WPF], syntax terminology
- attached events [WPF]
- lookup semantics [WPF]
- XAML [WPF], attached events
- XAML [WPF], content syntax
- XAML [WPF], lookup semantics
- content syntax [WPF]
- object element syntax [WPF]
- syntax terminology [XAML]
- XAML [WPF], attached properties
- attributes [XAML], parsing
- XAML [WPF], tag syntax
- XAML [WPF], attribute syntax
- property element syntax [WPF]
- terminology [XAML]
- namespaces [WPF], XML
- attribute syntax [XAML]
- XAML [WPF], property element syntax
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
ms.openlocfilehash: 6ef217a646b14f02c0b812f6316ec84f26d4b660
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168349"
---
# <a name="xaml-syntax-in-detail"></a>XAML 语法详述
本主题定义用于描述 XAML 语法元素的术语。 在本文档的其余部分中经常使用这些术语，这两个术语分别适用于 WPF 文档，适用于使用 XAML 的其他框架或由 system.exception 级别的 XAML 语言支持启用的基本 XAML 概念。 本主题概述了在主题[XAML 概述（WPF）](../../../desktop-wpf/fundamentals/xaml.md)中引入的基本术语。  

<a name="the_xaml_language_specification"></a>
## <a name="the-xaml-language-specification"></a>XAML 语言规范  
 此处定义的 XAML 语法术语也是在 XAML 语言规范中定义或引用的。 XAML 是一种基于 XML 的语言，并在 XML 结构规则后跟随或展开。 其中一些术语是从或中共享的，它基于在描述 XML 语言或 XML 文档对象模型时常用的术语。  
  
 有关 XAML 语言规范的详细信息，请从 Microsoft 下载中心下载[ \[ MS XAML \] ](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf) 。  
  
<a name="xaml_and_clr"></a>
## <a name="xaml-and-clr"></a>XAML 和 CLR  
 XAML 是一种标记语言。 公共语言运行时（CLR）根据其名称的隐含，启用运行时执行。 XAML 本身不是 CLR 运行时直接使用的公共语言之一。 相反，可以将 XAML 视为支持其自己的类型系统。 WPF 使用的特定 XAML 分析系统是在 CLR 和 CLR 类型系统上构建的。 在分析用于 WPF 的 XAML 时，XAML 类型会映射到 CLR 类型以实例化运行时表示形式。 出于此原因，本文档中的语法讨论的其余部分将包括对 CLR 类型系统的引用，尽管 XAML 语言规范中的等效语法讨论不包括在内。 （根据 XAML 语言规范级别，XAML 类型可以映射到任何其他类型系统，而无需是 CLR，但这需要创建和使用不同的 XAML 分析器。）  
  
#### <a name="members-of-types-and-class-inheritance"></a>类型和类继承的成员  
 作为类型的 XAML 成员出现的属性和事件 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 通常继承自基类型。 例如，请看下面的示例： `<Button Background="Blue" .../>` 。 <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> 如果要查看类定义、反射结果或文档，属性不是类的直接声明属性。 相反， <xref:System.Windows.Controls.Control.Background%2A> 继承自基类 <xref:System.Windows.Controls.Control> 。  
  
 XAML 元素的类继承行为 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是对 XML 标记的架构强制解释的一项重大影响。 类继承可能会变得复杂，尤其是在中间基类是抽象类或涉及接口时。 这是一种原因，这是一组 XAML 元素及其允许的特性很难准确准确地使用通常用于 XML 编程（如 DTD 或 XSD 格式）的架构类型来表示。 另一个原因是 XAML 语言自身的可扩展性和类型映射功能排除了允许的类型和成员的任何固定表示形式的完整性。  
  
<a name="object_element_syntax"></a>
## <a name="object-element-syntax"></a>对象元素语法  
 *对象元素语法*是通过声明 XML 元素来实例化 CLR 类或结构的 XAML 标记语法。 此语法类似于其他标记语言（如 HTML）的元素语法。 对象元素语法以左尖括号（ \< ）开头，后跟要实例化的类或结构的类型名称。 零个或多个空格可以跟在类型名称之后，还可以在 object 元素上声明零个或多个属性，并在每个属性名称 = "value" 对之间用一个或多个空格分隔。 最后，必须满足以下条件之一：  
  
- 元素和标记必须以正斜杠（/）结束，后面紧跟右尖括号（>）。  
  
- 开始标记必须由右尖括号（>）完成。 其他对象元素、属性元素或内部文本可以跟随开始标记。 此处可以确切包含的内容通常受元素的对象模型的约束。 还必须存在对象元素的等效结束标记，并将其与其他开始和结束标记对进行适当的嵌套和平衡。  
  
 .NET 实现的 XAML 包含一组规则，这些规则将对象元素映射到类型、属性或事件中的属性，以及 XAML 命名空间到 CLR 命名空间和程序集。 对于 WPF 和 .NET，XAML 对象元素映射到在引用的程序集中定义的 .NET 类型，属性映射到这些类型的成员。 在 XAML 中引用 CLR 类型时，还可以访问该类型的继承成员。  
  
 例如，下面的示例是实例化类的新实例的对象元素语法 <xref:System.Windows.Controls.Button> ，还为该属性指定了一个 <xref:System.Windows.FrameworkElement.Name%2A> 属性和一个值：  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 下面的示例是包含 XAML 内容属性语法的对象元素语法。 中包含的内部文本将用于设置 <xref:System.Windows.Controls.TextBox> XAML 内容属性 <xref:System.Windows.Controls.TextBox.Text%2A> 。  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>内容模型  
 类在语法方面可能支持使用作为 XAML 对象元素，但当该元素置于整体内容模型或元素树的预期位置时，它将仅在应用程序或页中正常运行。 例如， <xref:System.Windows.Controls.MenuItem> 通常只应将作为 <xref:System.Windows.Controls.Primitives.MenuBase> 派生类（如）的子级 <xref:System.Windows.Controls.Menu> 。 特定元素的内容模型记录为控件的类页和可用作 XAML 元素的其他类的 "备注" 的一部分 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。  
  
<a name="properties_of_object_elements"></a>
## <a name="properties-of-object-elements"></a>对象元素的属性  
 XAML 中的属性由各种可能的语法设置。 根据要设置的属性的基础类型系统特征，可用于特定属性的语法将有所不同。  
  
 通过设置属性的值，您可以将功能或特征添加到对象中，因为它们存在于运行时对象关系图中。 对象元素中创建的对象的初始状态基于无参数构造函数的行为。 通常，应用程序将使用任何给定对象的完全默认实例以外的内容。  
  
<a name="attribute_syntax_properties"></a>
## <a name="attribute-syntax-properties"></a>特性语法（属性）  
 特性语法是 XAML 标记语法，它通过在现有对象元素上声明特性来设置属性的值。 特性名称必须与支持相关对象元素的类的属性的 CLR 成员名称匹配。 特性名称后跟赋值运算符（=）。 属性值必须是括在引号内的字符串。  
  
> [!NOTE]
> 可以使用交替引号将文本引号置于特性中。 例如，可以将单引号用作一种声明其中包含双引号字符的字符串。 无论使用单引号还是双引号，都应使用匹配对来打开和关闭属性值字符串。 还提供了一些转义序列或其他技术，可用于解决任何特定 XAML 语法施加的字符限制。 请参阅[XML 字符实体和 XAML](../../../desktop-wpf/xaml-services/xml-character-entities.md)。  
  
 为了通过属性语法进行设置，属性必须是公共的，并且必须是可写的。 后备类型系统中的属性的值必须是值类型，或者必须是 XAML 处理器在访问相关支持类型时可以实例化或引用的引用类型。  
  
 对于 WPF XAML 事件，作为特性名称引用的事件必须是公共的，并且必须具有公共委托。  
  
 属性或事件必须是由包含对象元素实例化的类或结构的成员。  
  
### <a name="processing-of-attribute-values"></a>属性值的处理  
 由 XAML 处理器处理的左引号和右引号内包含的字符串值。 对于属性，默认处理行为由基础 CLR 属性的类型确定。  
  
 使用此处理顺序通过以下方式之一填充属性值：  
  
1. 如果 XAML 处理器遇到大括号或从派生的对象元素 <xref:System.Windows.Markup.MarkupExtension> ，则首先计算引用的标记扩展，而不是将值作为字符串进行处理，并且由标记扩展返回的对象将用作值。 在许多情况下，由标记扩展返回的对象将是对现有对象的引用，或将计算延迟到运行时的表达式，而不是新实例化的对象。  
  
2. 如果该属性是使用特性化声明的 <xref:System.ComponentModel.TypeConverter> ，或者该属性的值类型是使用属性声明的，则该属性的 <xref:System.ComponentModel.TypeConverter> 字符串值将作为转换输入提交给类型转换器，并且转换器将返回新的对象实例。  
  
3. 如果没有 <xref:System.ComponentModel.TypeConverter> ，则尝试直接转换为属性类型。 此最终级别是 XAML 语言基元类型之间的分析器本机值的直接转换，或者是对枚举中的命名常量名称的检查（分析器然后访问匹配的值）。  
  
#### <a name="enumeration-attribute-values"></a>枚举属性值  
 XAML 中的枚举在本质上由 XAML 分析器进行处理，并且应通过指定枚举命名常量之一的字符串名称来指定枚举的成员。  
  
 对于 nonflag 枚举值，本机行为是处理属性值的字符串，并将其解析为枚举值之一。 不在格式*枚举*中指定枚举。*值*，这与在代码中执行的操作相同。 相反，您只需指定*值*，*枚举*将由您设置的属性的类型推断。 如果在*枚举*中指定属性，则为。*值*格式，它将无法正确解析。  
  
 对于 flagwise 枚举，行为基于 <xref:System.Enum.Parse%2A?displayProperty=nameWithType> 方法。 可以通过用逗号分隔每个值来指定 flagwise 枚举的多个值。 但是，不能合并不 flagwise 的枚举值。 例如，你不能使用逗号语法来尝试创建一个 <xref:System.Windows.Trigger> ，它对 nonflag 枚举的多个条件执行操作：  
  
```xaml  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 在 WPF 中，支持在 XAML 中设置的属性的 Flagwise 枚举非常罕见。 但是，其中一个枚举为 <xref:System.Windows.Media.StyleSimulations> 。 例如，可以使用逗号分隔的 flagwise 特性语法来修改在类的 "备注" 中提供的示例 <xref:System.Windows.Documents.Glyphs> ; `StyleSimulations = "BoldSimulation"` 可能会成为 `StyleSimulations = "BoldSimulation,ItalicSimulation"` 。 <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>可以指定多个枚举值的另一个属性。 但是，此属性恰好是一种特殊情况，因为 <xref:System.Windows.Input.ModifierKeys> 枚举支持其自己的类型转换器。 修饰符的类型转换器使用加号（+）作为分隔符，而不是逗号（，）。 此转换支持更传统的语法来表示 Microsoft Windows 编程中的组合键，如 "Ctrl + Alt"。  
  
### <a name="properties-and-event-member-name-references"></a>属性和事件成员名称引用  
 指定特性时，可以引用作为为包含对象元素实例化的 CLR 类型的成员存在的任何属性或事件。  
  
 或者，可以引用附加的属性或附加事件，而不依赖于包含对象元素。 （后面的部分将讨论附加属性。）  
  
 你还可以使用*typeName*来命名可通过默认命名空间访问的任何对象中的任何事件。*事件*部分限定名称;此语法支持为路由事件附加处理程序，其中处理程序旨在处理来自子元素的事件路由，但父元素的成员表中也不包含该事件。 此语法与附加事件语法类似，但此处的事件不是真正的附加事件。 而是引用具有限定名称的事件。 有关详细信息，请参阅[路由事件概述](routed-events-overview.md)。  
  
 在某些情况下，属性名称有时提供为属性的值，而不是属性名称。 该属性名称还可以包括限定符，如以 "*所有者*" 格式指定的属性。*dependencyPropertyName*。 在 XAML 中编写样式或模板时，这种情况很常见。 作为属性值提供的属性名称的处理规则是不同的，由所设置的属性类型或特定 WPF 子系统的行为来控制。 有关详细信息，请参阅[样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。  
  
 属性名称的另一个用法是在属性值描述属性关系时使用。 此功能用于数据绑定和情节提要目标，并由 <xref:System.Windows.PropertyPath> 类及其类型转换器启用。 有关查找语义的更完整说明，请参阅[PROPERTYPATH XAML 语法](propertypath-xaml-syntax.md)。  
  
<a name="property_element_syntax"></a>
## <a name="property-element-syntax"></a>属性元素语法  
 *Property 元素语法*是一种语法，它与元素的基本 XML 语法规则有点与其分离。 在 XML 中，属性的值是一个事实字符串，唯一可能的变体是使用哪种字符串编码格式。 在 XAML 中，可以将其他对象元素分配为属性的值。 此功能由属性元素语法启用。 使用*elementTypeName*中的开始元素标记，而不是在元素标记中指定为特性的属性。*propertyName*窗体，在中指定属性的值，然后关闭 property 元素。  
  
 具体而言，语法以左尖括号（ \<), followed immediately by the type name of the class or structure that the property element syntax is contained within. This is followed immediately by a single dot (.), then by the name of a property, then by a right angle bracket (> ）开头。 与特性语法一样，该属性必须存在于指定类型的已声明公共成员中。 要分配给属性的值包含在 property 元素中。 通常，值作为一个或多个对象元素提供，因为将对象指定为值是属性元素语法旨在解决的方案。 最后，指定相同*elementTypeName*的等效结束标记。必须提供*属性名称*组合，正确地进行嵌套并与其他元素标记平衡。  
  
 例如，下面是的属性的属性元素语法 <xref:System.Windows.FrameworkElement.ContextMenu%2A> <xref:System.Windows.Controls.Button> 。  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 如果指定的属性类型是基元值类型（例如 <xref:System.String> ）或枚举（其中指定了名称），则属性元素内的值还可以作为内部文本提供。 这两种用法有点罕见，因为这两种情况下也可以使用更简单的特性语法。 用字符串填充属性元素的一个方案是：对于不是 XAML 内容属性但仍用于表示 UI 文本的属性，并且需要在该 UI 文本中显示换行符等特定空白元素。 特性语法不能保留换行符，但只要有效的空白保留处于活动状态（有关详细信息，请参阅[XAML 中的空白处理](../../../desktop-wpf/xaml-services/white-space-processing.md)），属性元素语法就可以。 另一种情况是，可以将[X：Uid 指令](../../../desktop-wpf/xaml-services/xuid-directive.md)应用于属性元素，从而将中的值标记为应在 WPF 输出 BAML 或其他技术中本地化的值。  
  
 属性元素不在 WPF 逻辑树中表示。 Property 元素只是用于设置属性的特殊语法，而不是具有支持它的实例或对象的元素。 （有关逻辑树概念的详细信息，请参阅[WPF 中的树](trees-in-wpf.md)。）  
  
 对于支持属性和属性元素语法的属性，这两个语法通常具有相同的结果，尽管微妙之处（如空格处理）在语法上略有不同。  
  
<a name="collection_syntax"></a>
## <a name="collection-syntax"></a>集合语法  
 XAML 规范要求 XAML 处理器实现来标识值类型为集合的属性。 .NET 中的常规 XAML 处理器实现基于托管代码和 CLR，并通过以下方法之一标识集合类型：  
  
- 类型实现 <xref:System.Collections.IList> 。  
  
- 类型实现 <xref:System.Collections.IDictionary> 。  
  
- 类型派生自 <xref:System.Array> （有关 XAML 中数组的详细信息，请参阅[X:Array 标记扩展](../../../desktop-wpf/xaml-services/xarray-markup-extension.md)。）  
  
 如果属性的类型是集合，则不需要在标记中将推断的集合类型指定为对象元素。 相反，旨在成为集合中的项的元素被指定为属性元素的一个或多个子元素。 在加载过程中，将每个此类项计算为一个对象，并通过调用隐含集合的方法将其添加到集合中 `Add` 。 例如，的 <xref:System.Windows.Style.Triggers%2A> 属性 <xref:System.Windows.Style> 采用专用的集合类型 <xref:System.Windows.TriggerCollection> ，该类型实现 <xref:System.Collections.IList> 。 不需要实例化 <xref:System.Windows.TriggerCollection> 标记中的对象元素。 相反，您可以将一个或多个 <xref:System.Windows.Trigger> 项指定为 `Style.Triggers` property 元素中的元素，其中 <xref:System.Windows.Trigger> （或派生类）是应作为强类型和隐式的项类型的类型 <xref:System.Windows.TriggerCollection> 。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 属性可以同时为该类型和派生类型的集合类型和 XAML 内容属性，本主题的下一部分将对此进行讨论。  
  
 隐式集合元素在逻辑树表示形式中创建成员，即使它不在标记中显示为元素也是如此。 通常，父类型的构造函数对作为其属性之一的集合执行实例化，初始空集合将成为对象树的一部分。  
  
> [!NOTE]
> 集合检测不支持泛型列表和字典接口（ <xref:System.Collections.Generic.IList%601> 和 <xref:System.Collections.Generic.IDictionary%602> ）。 但是，可以将 <xref:System.Collections.Generic.List%601> 类用作基类，因为它 <xref:System.Collections.IList> 直接实现或 <xref:System.Collections.Generic.Dictionary%602> 作为基类，因为它 <xref:System.Collections.IDictionary> 直接实现。  
  
 在集合类型的 .NET 参考页中，在 XAML 语法节中，有意省略集合的 object 元素的这一语法被标记为隐式集合语法。  
  
 除了根元素，XAML 文件中作为另一个元素的子元素嵌套的每个对象元素确实是以下两种情况之一或全部的元素：其父元素的隐式集合属性的成员，或指定父元素的 XAML 内容属性值的元素（将在即将发布的部分中讨论 XAML 内容属性）。 换句话说，"标记" 页中的父元素和子元素的关系实际上是根中的单个对象，根下的每个对象元素都是一个提供父级属性值的实例，或者是一个集合中的项的一个实例，该实例也是父级的集合类型属性值。 这种单一根概念是 XML 所共有的，并经常加强加载 XAML 的 Api （例如）的行为 <xref:System.Windows.Markup.XamlReader.Load%2A> 。  
  
 下面的示例是显式指定集合（）的对象元素的语法 <xref:System.Windows.Media.GradientStopCollection> 。  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <GradientStopCollection>  
      <GradientStop Offset="0.0" Color="Red" />  
      <GradientStop Offset="1.0" Color="Blue" />  
    </GradientStopCollection>  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
 请注意，并非始终可以显式声明集合。 例如，尝试 <xref:System.Windows.TriggerCollection> 在前面所示的示例中显式声明 <xref:System.Windows.Style.Triggers%2A> 会失败。 显式声明集合需要集合类必须支持无参数的构造函数，并且没有 <xref:System.Windows.TriggerCollection> 无参数的构造函数。  
  
<a name="xaml_content_properties"></a>
## <a name="xaml-content-properties"></a>XAML 内容属性  
 XAML 内容语法是一种语法，只在指定 <xref:System.Windows.Markup.ContentPropertyAttribute> 为其类声明的一部分的类上启用。 <xref:System.Windows.Markup.ContentPropertyAttribute>引用作为该类型元素（包括派生类）的内容属性的属性名称。 当由 XAML 处理器处理时，在对象元素的开始标记和结束标记之间找到的任何子元素或内部文本都将被指定为该对象的 XAML 内容属性的值。 允许你为 content 属性指定显式属性元素，但此用法通常不会显示在 .NET 参考的 "XAML 语法" 部分中。 显式/详细方法为标记清晰度或标记样式提供了偶尔的值，但内容属性的目的通常是简化标记，以便可以直接嵌套直观相关的元素。 元素的其他属性的属性元素标记未按严格 XAML 语言定义指定为 "content";它们先前在 XAML 分析器的处理顺序中进行处理，并且不被视为 "内容"。  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML 内容属性值必须是连续的  
 XAML 内容属性的值必须完全在该对象元素上的任何其他属性元素之前或之后指定。 无论 XAML 内容属性的值是指定为字符串，还是指定为一个或多个对象，都是如此。 例如，以下标记不会进行分析：  
  
```xaml  
<Button>I am a
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 这对于本质而言是非法的，因为如果通过使用 content 属性的属性元素语法使此语法变为显式，则内容属性将设置两次：  
  
```xaml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 例如，如果 content 属性是一个集合，并且子元素与属性元素交错在一起，则这是一个类似的非法示例：  
  
```xaml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>
## <a name="content-properties-and-collection-syntax-combined"></a>内容属性和集合语法组合  
 为了接受多个对象元素作为内容，内容属性的类型必须特别是集合类型。 类似于集合类型的属性元素语法，XAML 处理器必须标识作为集合类型的类型。 如果元素具有 XAML 内容属性，且 XAML 内容属性的类型是集合，则不需要在标记中将隐含的集合类型指定为对象元素，并且不需要将 XAML 内容属性指定为 property 元素。 因此，标记中的外观内容模型现在可以将多个子元素作为内容进行分配。 下面是派生类的内容语法 <xref:System.Windows.Controls.Panel> 。 所有 <xref:System.Windows.Controls.Panel> 派生类都将 XAML 内容属性建立为 <xref:System.Windows.Controls.Panel.Children%2A> ，这需要类型的值 <xref:System.Windows.Controls.UIElementCollection> 。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 请注意，标记中不需要的属性元素 <xref:System.Windows.Controls.Panel.Children%2A> 和的元素 <xref:System.Windows.Controls.UIElementCollection> 。 这是 XAML 的一项设计功能，使定义为的递归包含元素 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 更直观地表示为具有直接父子元素关系的嵌套元素树，而不会干扰属性元素标记或集合对象。 事实上，在 <xref:System.Windows.Controls.UIElementCollection> 设计上不能在标记中显式指定为对象元素。 由于其唯一用途是作为隐式集合，因此不会 <xref:System.Windows.Controls.UIElementCollection> 公开公共的无参数构造函数，因此不能将其实例化为对象元素。  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>使用 Content 属性混合对象中的属性元素和对象元素  
 XAML 规范声明 XAML 处理器可以强制在对象元素中用于填充 XAML 内容属性的对象元素必须是连续的，且不能混合使用。 对混合属性元素和内容的这一限制由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 处理器强制执行。  
  
 您可以将一个子对象元素作为对象元素中的第一个直接标记。 然后，可以引入属性元素。 或者，您可以指定一个或多个属性元素，然后指定 content，再指定更多属性元素。 但一旦属性元素跟随内容，就不能再引入任何内容，只能添加属性元素。  
  
 此内容/属性元素顺序要求不适用于用作内容的内部文本。 但是，它仍是一个很好的标记样式来保持内部文本连续，因为如果属性元素与内部文本交错，则很难在标记中直观地检测到有效的空白。  
  
<a name="xaml_namespaces"></a>
## <a name="xaml-namespaces"></a>XAML 命名空间  
 上述语法示例均未指定默认 XAML 命名空间之外的 XAML 命名空间。 在典型 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的应用程序中，默认的 XAML 命名空间被指定为 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 命名空间。 可以指定除默认 XAML 命名空间之外的 XAML 命名空间，并且仍使用类似的语法。 但然后，在默认 XAML 命名空间内无法访问的类的任何位置，该类名前面必须带有 XAML 命名空间的前缀，才能映射到相应的 CLR 命名空间。 例如， `<custom:Example/>` 是对象元素语法，用于实例化类的实例 `Example` ，其中包含该类的 CLR 命名空间（也可能是包含支持类型的外部程序集信息）以前映射到 `custom` 前缀。  
  
 有关 XAML 命名空间的详细信息，请参阅[WPF xaml 的 Xaml 命名空间和命名空间映射](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="markup_extensions"></a>
## <a name="markup-extensions"></a>标记扩展  
 XAML 定义了一个标记扩展编程实体，该实体启用对字符串属性值或对象元素的一般 XAML 处理器处理的转义，并将处理推迟到后备类中。 使用特性语法时标识 XAML 处理器的标记扩展的字符为左大括号（{），后跟右大括号（}）以外的任何字符。 左大括号后面的第一个字符串必须引用提供特定扩展行为的类，如果子字符串属于真实的类名称，则引用可能会忽略子字符串 "Extension"。 此后，可能会出现一个空格，然后将每个后续字符用作扩展实现的输入，直至遇到右大括号。  
  
 .NET XAML 实现使用 <xref:System.Windows.Markup.MarkupExtension> 抽象类作为支持的所有标记扩展 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 以及其他框架或技术的基础。 专门实现的标记扩展 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 通常用于提供引用其他现有对象的方法，或者用于对将在运行时计算的对象进行延迟引用。 例如，通过指定 `{Binding}` 标记扩展来替换特定属性通常会采用的值来完成简单的 WPF 数据绑定。 很多 WPF 标记扩展为属性启用了属性语法，在这种情况下，不可能出现特性语法。 例如， <xref:System.Windows.Style> 对象是一个相对复杂的类型，它包含一系列嵌套的对象和属性。 WPF 中的样式通常定义为中的资源 <xref:System.Windows.ResourceDictionary> ，然后通过请求资源的两个 WPF 标记扩展之一进行引用。 标记扩展将属性值的计算延迟为资源查找，并 <xref:System.Windows.FrameworkElement.Style%2A> 在特性语法中提供属性的值（采用类型 <xref:System.Windows.Style> ），如以下示例中所示：  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 此处 `StaticResource` 标识 <xref:System.Windows.StaticResourceExtension> 提供标记扩展实现的类。 接下来的字符串用作 `MyStyle` 非默认 <xref:System.Windows.StaticResourceExtension> 构造函数的输入，其中来自扩展字符串的参数声明所请求的 <xref:System.Windows.ResourceKey> 。 `MyStyle`应为定义为资源的的 " [x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md) " 值 <xref:System.Windows.Style> 。 [StaticResource 标记扩展](staticresource-markup-extension.md)用法请求资源用于 <xref:System.Windows.Style> 在加载时通过静态资源查找逻辑提供属性值。  
  
 有关标记扩展的详细信息，请参阅[标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)。 有关在常规 .NET XAML 实现中启用的标记扩展和其他 XAML 编程功能的引用，请参阅[XAML 命名空间（x：）语言功能](../../../desktop-wpf/xaml-services/namespace-language-features.md)。 有关特定于 WPF 的标记扩展，请参阅[WPF XAML 扩展](wpf-xaml-extensions.md)。  
  
<a name="attached_properties"></a>
## <a name="attached-properties"></a>附加属性  
 附加属性是 XAML 中引入的一种编程概念，其中属性可由特定类型拥有和定义，但设置为任意元素上的特性或属性元素。 附加属性的主要方案是允许标记结构中的子元素向父元素报告信息，而无需跨所有元素广泛共享对象模型。 相反，附加属性可由父元素用来向子元素报告信息。 有关附加属性以及如何创建您自己的附加属性的详细信息，请参阅[附加属性概述](attached-properties-overview.md)。  
  
 附加属性使用的语法在表面上类似于属性元素语法，因为你还需要指定*typeName*。*propertyName*组合。 有两个重要的差异：  
  
- 您可以使用*typeName*。*propertyName*组合，即使通过特性语法设置附加属性也是如此。 附加属性是在特性语法中限定属性名称的唯一情况。  
  
- 还可以对附加属性使用属性元素语法。 但对于典型的属性元素语法，指定的*类型名称*是包含 property 元素的对象元素。 如果你引用附加属性，则*typeName*是定义附加属性的类，而不是包含对象元素。  
  
<a name="attached_events"></a>
## <a name="attached-events"></a>附加事件  
 附加事件是 XAML 中引入的另一种编程概念，其中事件可以由特定类型定义，但处理程序可以附加到任何对象元素上。 在 WOF 实现中，定义附加事件的类型通常为定义服务的静态类型，有时这些附加事件由公开服务的类型中的路由事件别名公开。 附加事件的处理程序通过特性语法指定。 与附加事件一样，为附加事件扩展特性语法以允许*typeName*。*事件名称用法，* 其中*typeName*是为 `Add` `Remove` 附加事件基础结构提供和事件处理程序访问器的类*eventName* ，而事件名称是事件名称。  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>
## <a name="anatomy-of-a-xaml-root-element"></a>XAML 根元素的解析  
 下表显示了一个典型的 XAML 根元素，该元素向下分解，其中显示了根元素的特定属性：  
  
|||  
|-|-|  
|`<Page`|根元素的打开对象元素|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|默认（ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ） XAML 命名空间|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML 语言 XAML 命名空间|  
|`x:Class="ExampleNamespace.ExampleCode"`|分部类声明，它将标记连接到为分部类定义的任何代码隐藏|  
|`>`|根的对象元素的结尾。 对象尚未关闭，因为元素包含子元素|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>
## <a name="optional-and-nonrecommended-xaml-usages"></a>可选和推荐 XAML 用法  
 以下各节介绍 XAML 处理器在技术上受支持的 XAML 用法，但产生的详细程度或其他美观问题会影响在开发包含 XAML 源的应用程序时可读取的 XAML 文件。  
  
### <a name="optional-property-element-usages"></a>可选属性元素用法  
 可选属性元素用法包括显式写出 XAML 处理器认为隐式的元素内容属性。 例如，当你声明的内容时 <xref:System.Windows.Controls.Menu> ，你可以选择将的集合显式声明 <xref:System.Windows.Controls.ItemsControl.Items%2A> <xref:System.Windows.Controls.Menu> 为 `<Menu.Items>` 属性元素标记，并将每个元素放 <xref:System.Windows.Controls.MenuItem> 在中 `<Menu.Items>` ，而不是使用隐式 XAML 处理器行为，其中的所有子元素都 <xref:System.Windows.Controls.Menu> 必须是 <xref:System.Windows.Controls.MenuItem> 并放置在集合中 <xref:System.Windows.Controls.ItemsControl.Items%2A> 。 有时，可选用法可帮助以直观方式阐明标记中所表示的对象结构。 或者有时，显式属性元素使用可以避免在技术上正常运行的标记，但在视觉上混乱，如属性值中的嵌套标记扩展。  
  
### <a name="full-typenamemembername-qualified-attributes"></a>完整的 typeName 成员限定属性  
 *TypeName*。属性的*成员名称*格式实际上比路由事件事例更通用。 但在其他情况下，该窗体是多余的，如果仅出于标记样式和可读性的原因，应避免这样做。 在下面的示例中，对特性的三个引用中的每个 <xref:System.Windows.Controls.Control.Background%2A> 都完全等效：  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`有效，因为对的属性的限定查找 <xref:System.Windows.Controls.Button> 成功（ <xref:System.Windows.Controls.Control.Background%2A> 从控件继承），并且 <xref:System.Windows.Controls.Button> 是对象元素或基类的类。 `Control.Background`有效，因为 <xref:System.Windows.Controls.Control> 该类实际定义 <xref:System.Windows.Controls.Control.Background%2A> 并且 <xref:System.Windows.Controls.Control> 是一个 <xref:System.Windows.Controls.Button> 基类。  
  
 但是，以下*类型名称*为。*成员名称*形式的示例不起作用，因此会以注释形式显示：  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>是的另一个派生类 <xref:System.Windows.Controls.Control> ，如果在对象元素中指定了，则 `Label.Background` 这种 <xref:System.Windows.Controls.Label> 用法将起作用。 但是，由于不 <xref:System.Windows.Controls.Label> 是的类或基类，因此 <xref:System.Windows.Controls.Button> 指定的 XAML 处理器行为将 `Label.Background` 作为附加属性进行处理。 `Label.Background`不是可用的附加属性，且此使用失败。  
  
### <a name="basetypenamemembername-property-elements"></a>b 属性元素  
 与*typeName*的方式类似。*成员名称*形式适用于特性语法， *b*。*成员名称*语法适用于属性元素语法。 例如，下面的语法有效：  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 此处， `Control.Background` 虽然属性元素包含在中，但却提供了 property 元素 `Button` 。  
  
 但就像*类型名称*一样。属性的*成员名称*形式*b*。*成员名称*在标记中的样式不佳，你应避免这样做。  
  
## <a name="see-also"></a>请参阅

- [XAML 概述 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [XAML 命名空间 (x:)语言功能](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [WPF XAML 扩展](wpf-xaml-extensions.md)
- [依赖项属性概述](dependency-properties-overview.md)
- [TypeConverters 和 XAML](typeconverters-and-xaml.md)
- [XAML 及 WPF 的自定义类](xaml-and-custom-classes-for-wpf.md)
