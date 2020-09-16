---
title: 自定义类型和库的 XAML 相关 CLR 特性
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: a4b8a58ea2c7d9de2b59ed78dc37e4ce1c434b79
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535392"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>自定义类型和库的 XAML 相关 CLR 特性

本主题介绍了公共语言运行时 (CLR) 由 .NET XAML 服务定义的属性。 它还介绍了在 .NET 中定义的、具有应用程序程序集或类型的 XAML 相关方案的其他 CLR 特性。 将程序集、类型或成员与这些 CLR 特性相关联可提供与类型相关的 XAML 类型系统信息。 向使用 .NET XAML 服务的任何 XAML 使用者提供信息，以便直接或通过专用的 XAML 读取器和 XAML 编写器处理 XAML 节点流。

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>自定义类型和自定义成员的 XAML 相关 CLR 特性

使用 CLR 特性时，需要使用整个 CLR 来定义类型，否则此类属性将不可用。 如果你使用 CLR 定义类型支持，则 .NET XAML 服务 XAML 编写器使用的默认 XAML 架构上下文可以通过反射针对支持程序集读取 CLR 特性。

以下各节介绍可应用于自定义类型或自定义成员的与 XAML 相关的属性。 每个 CLR 特性都传达与 XAML 类型系统相关的信息。 在加载路径中，特性化信息要么有助于 XAML 读取器构成有效的 XAML 节点流，要么有助于 XAML 编写器生成有效的对象图。 在保存路径中，特性化信息可以帮助 XAML 读取器形成重构 XAML 类型系统信息的有效 XAML 节点流;或声明 XAML 编写器或其他 XAML 使用者的序列化提示或要求。

### <a name="ambientattribute"></a>AmbientAttribute

**参考文档：**<xref:System.Windows.Markup.AmbientAttribute>

**适用于：**`get`支持可附加属性的类、属性或访问器成员。

**参数：** 内容

<xref:System.Windows.Markup.AmbientAttribute> 指示应在 XAML 中的环境属性概念下解释属性或采用特性化类型的所有属性。 环境概念涉及 XAML 处理器如何确定成员的类型所有者。 环境属性是一个属性，其中的值应在创建对象图时在分析器上下文中可用，但在此情况下，将为正在创建的即时 XAML 节点挂起典型类型成员查找。

环境概念可以应用于可附加成员，这些成员不会以 CLR 特性定义的方式表示为属性 <xref:System.AttributeTargets> 。 方法归属用法仅适用于 `get` 支持 XAML 的可附加用法的访问器。

### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute

**参考文档：**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>

**适用于：** 班级

**参数：** 一个字符串，指定与单个构造函数参数匹配的属性的名称。

<xref:System.Windows.Markup.ConstructorArgumentAttribute> 指定可以通过使用非参数构造函数语法来初始化对象，指定名称的属性提供构造信息。 此信息主要用于 XAML 序列化。 有关详细信息，请参阅 <xref:System.Windows.Markup.ConstructorArgumentAttribute>。

### <a name="contentpropertyattribute"></a>ContentPropertyAttribute

**参考文档：**  <xref:System.Windows.Markup.ContentPropertyAttribute>

**适用于：** 班级

**参数：** 一个字符串，指定特性化类型的成员的名称。

<xref:System.Windows.Markup.ContentPropertyAttribute> 指示由参数命名的属性应作为该类型的 XAML 内容属性。 XAML 内容属性定义继承到可分配给定义类型的所有派生类型。 您可以通过 <xref:System.Windows.Markup.ContentPropertyAttribute> 对特定派生类型应用，来重写特定派生类型的定义。

对于用作 XAML 内容属性的属性，可在 XAML 用法中省略属性的属性元素标记。 通常，可以指定 XAML 内容属性，这些属性可为内容和包含模型升级简化的 XAML 标记。 由于只能将一个成员指定为 XAML 内容属性，因此，有时需要对类型的多个容器属性中的哪个容器属性指定为 XAML 内容属性。 其他容器属性必须与显式属性元素一起使用。

在 XAML 节点流中，XAML 内容属性仍生成， `StartMember` 并 `EndMember` 使用属性的名称作为节点 <xref:System.Xaml.XamlMember> 。 若要确定成员是否为 XAML 内容属性，请检查 <xref:System.Xaml.XamlType> 位置的值 `StartObject` 并获取的值 <xref:System.Xaml.XamlType.ContentProperty%2A> 。

### <a name="contentwrapperattribute"></a>ContentWrapperAttribute

**参考文档：**  <xref:System.Windows.Markup.ContentWrapperAttribute>

**适用于：** 类，特别是集合类型。

**参数：** 一个 <xref:System.Type> ，指定要用作外部内容的内容包装类型的类型。

<xref:System.Windows.Markup.ContentWrapperAttribute> 指定将用于包装外部内容的关联集合类型上的一个或多个类型。 "外部内容" 指的是对内容属性类型的类型系统约束不会捕获所属类型的 XAML 使用情况支持的所有可能的内容事例。 例如，XAML 支持特定类型的内容可能支持强类型化泛型中的字符串 <xref:System.Collections.ObjectModel.Collection%601> 。 内容包装适用于将预先存在的标记约定迁移到用于集合的可赋值值的 XAML 概念，如迁移与文本相关的内容模型。

若要指定多个内容包装类型，请多次应用该属性。

### <a name="dependsonattribute"></a>DependsOnAttribute

**参考文档：**  <xref:System.Windows.Markup.DependsOnAttribute>

**适用于：** 知识产权

**参数：** 一个字符串，指定特性化类型的另一个成员的名称。

<xref:System.Windows.Markup.DependsOnAttribute> 指示特性化属性依赖于另一个属性的值。 将此特性应用于属性定义可确保先在 XAML 对象写入中处理依赖属性。 使用 <xref:System.Windows.Markup.DependsOnAttribute> 情况：指定类型的异常事例，必须遵循特定的分析顺序才能实现有效的对象创建。

可以将多个 <xref:System.Windows.Markup.DependsOnAttribute> 事例应用于一个属性定义。

### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute

**参考文档：**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

**适用于：** 类，它应为 <xref:System.Windows.Markup.MarkupExtension> 派生类型。

**参数：** 一个 <xref:System.Type> ，指定要作为 `ProvideValue` 特性化结果的最精确类型 <xref:System.Windows.Markup.MarkupExtension> 。

有关详细信息，请参阅 [XAML 的标记扩展概述](markup-extensions-overview.md)。

### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute

**参考文档：**  <xref:System.Windows.Markup.NameScopePropertyAttribute>

**适用于：** 班级

**参数：** 支持两种形式的归属：

- 一个字符串，指定特性化类型上属性的名称。

- 一个字符串，指定属性的名称，并指定一个 <xref:System.Type> 用于定义命名属性的类型的。 此窗体用于将可附加成员指定为 XAML 名称范围属性。

<xref:System.Windows.Markup.NameScopePropertyAttribute> 指定为特性化类提供 XAML 名称范围值的属性。 XAML 名称范围属性应引用实现 <xref:System.Windows.Markup.INameScope> 并保存实际 XAML 名称范围、其存储和行为的对象。

### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute

**参考文档：**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

**适用于：** 班级

**参数：** 一个字符串，指定特性化类型上的运行时名称属性的名称。

<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 报告映射到 XAML [X：Name 指令](xname-directive.md)的特性化类型的属性。 属性必须为类型 <xref:System.String> ，并且必须是可读/写的。

定义继承到可分配给定义类型的所有派生类型。 您可以通过 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 对特定派生类型应用，来重写特定派生类型的定义。

### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute

**参考文档：**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

**适用于：** 各种

**参数：** 内容.

<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 应用于特定的类型，这些特定类型可能在空白内容中显示为子元素 (具有) 的集合保存的内容 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 。 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 主要与 save 路径相关，但通过检查，在加载路径的 XAML 类型系统中提供 <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType> 。 有关详细信息，请参阅 [XAML 中的空白处理](white-space-processing.md)。

### <a name="typeconverterattribute"></a>TypeConverterAttribute

**参考文档：**  <xref:System.ComponentModel.TypeConverterAttribute>

**适用于：** 仅 XAML 有效方法 (的类、属性和方法是 `get` 支持可附加成员) 的访问器。

**参数：** 的 <xref:System.Type> <xref:System.ComponentModel.TypeConverter> 。

<xref:System.ComponentModel.TypeConverterAttribute> 在 XAML 上下文中引用自定义 <xref:System.ComponentModel.TypeConverter> 。 这 <xref:System.ComponentModel.TypeConverter> 为自定义类型或该类型的成员提供类型转换行为。

将 <xref:System.ComponentModel.TypeConverterAttribute> 特性应用到类型，并引用类型转换器实现。 可以在类、结构或接口上定义 XAML 的类型转换器。 不需要为枚举提供类型转换，而是在本机启用该转换。

类型转换器应该能够从用于标记中的属性或初始化文本的字符串转换为所需的目标类型。 有关详细信息，请参阅 [TypeConverters 和 XAML](/dotnet/desktop/wpf/advanced/typeconverters-and-xaml)。

不是应用于类型的所有值，也可以针对特定属性建立 XAML 的类型转换器行为。 在这种情况下，您将应用于 <xref:System.ComponentModel.TypeConverterAttribute> 外部定义 (属性定义，而不是特定 `get` 和 `set` 定义) 。

可通过将应用 <xref:System.ComponentModel.TypeConverterAttribute> 到 `get` 支持 xaml 使用的方法访问器来分配自定义可附加成员的 XAML 用法的类型转换器行为。

与类似 <xref:System.ComponentModel.TypeConverter> ， <xref:System.ComponentModel.TypeConverterAttribute> 在存在 XAML 之前存在于 .net 中，类型转换器模型用于其他目的。 若要引用和使用 <xref:System.ComponentModel.TypeConverterAttribute> ，你必须完全限定它或提供的 `using` 语句 <xref:System.ComponentModel> 。 还包括项目中的系统程序集。

### <a name="uidpropertyattribute"></a>UidPropertyAttribute

**参考文档：**  <xref:System.Windows.Markup.UidPropertyAttribute>

**适用于：** 班级

**参数：** 按名称引用相关属性的字符串。

指示为 [X：Uid 指令](xuid-directive.md)指定别名的类的 CLR 属性。

### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute

**参考文档：**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>

**适用于：** 班级

**参数：** 布尔值。 如果用于属性的预期目的，则该值应设置为 `true` 。

指示在 XAML 对象图创建期间是否自上而下生成此类型。 这是一个高级概念，可能与编程模型的定义密切相关。 有关详细信息，请参阅 <xref:System.Windows.Markup.UsableDuringInitializationAttribute>。

### <a name="valueserializerattribute"></a>ValueSerializerAttribute

**参考文档：**  <xref:System.Windows.Markup.ValueSerializerAttribute>

**适用于：** 仅 XAML 有效方法 (的类、属性和方法是 `get` 支持可附加成员) 的访问器。

**参数：** 一个 <xref:System.Type> ，指定序列化程序支持类，以便在序列化特性化类型的所有属性或特定的特性化属性时使用。

<xref:System.Windows.Markup.ValueSerializer> 指定一个值序列化类，该类需要更多的状态和上下文，而 <xref:System.ComponentModel.TypeConverter> 不是。 <xref:System.Windows.Markup.ValueSerializer> 可以通过对可 <xref:System.Windows.Markup.ValueSerializerAttribute> `get` 附加成员的静态访问器方法应用属性，与可附加成员关联。 值序列化还适用于枚举、接口和结构，但不适用于委托。

### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute

**参考文档：**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

**适用于：** 类，特别是应承载混合内容的集合类型，在这种情况下，对象元素周围的空白可能对 UI 表示形式非常重要。

**参数：** 内容.

<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 指示应由 XAML 处理器以空白形式处理集合类型，这将影响集合中的 XAML 节点流的值节点的构造。 有关详细信息，请参阅 [XAML 中的空白处理](white-space-processing.md)。

### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute

**参考文档：**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>

**适用于：** 类，属性。

**参数：** 支持将两个特性窗体类型作为字符串或类型为 <xref:System.Type> 。 请参阅 <xref:System.Windows.Markup.XamlDeferLoadAttribute>。

指示类或属性具有 XAML 的延迟加载用途（如模板行为），并报告启用延迟行为及其目标/内容类型的类。

### <a name="xamlsetmarkupextensionattribute"></a>System.windows.markup.xamlsetmarkupextensionattribute

**参考文档：**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>

**适用于：** 班级

**参数：** 命名回调。

指示类可以使用标记扩展为其一个或多个属性提供值，并引用 XAML 编写器在对类的任何属性执行标记扩展设置操作之前应调用的处理程序。

### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute

**参考文档：**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>

**适用于：** 班级

**参数：** 命名回调。

指示类可以使用类型转换器为其一个或多个属性提供值，并引用 XAML 编写器在对类的任何属性执行类型转换器设置操作之前应调用的处理程序。

### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute

**参考文档：**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>

**适用于：** 班级

**参数：** 一个字符串，指定属性类型的别名属性的名称 `xml:lang` 。

<xref:System.Windows.Markup.XmlLangPropertyAttribute> 报告映射到 XML 指令的特性化类型的属性 `lang` 。 属性的类型不一定为， <xref:System.String> 但必须可从字符串中赋值 (可以通过将类型转换器与属性的类型或特定属性) 关联来实现。 属性必须是读/写属性。

映射的应用场景 `xml:lang` 是为了使运行时对象模型可以访问 XML 指定的语言信息，而无需使用 XMLDOM 进行专门处理。

定义继承到可分配给定义类型的所有派生类型。 您可以通过在特定派生类型上应用来重写特定派生类型的定义 <xref:System.Windows.Markup.XmlLangPropertyAttribute> ，但这种情况并不常见。

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>程序集级别的 XAML 相关 CLR 特性

以下各节介绍了与 XAML 相关的特性，这些特性不应用于类型或成员定义，而是应用于程序集。 这些属性与定义包含要在 XAML 中使用的自定义类型的库的整体目标有关。 有些属性不一定会直接影响 XAML 节点流，而是在节点流中传递，供其他使用者使用。 信息的使用者包括需要 XAML 命名空间信息和关联的前缀信息的设计环境或序列化过程。 XAML 架构上下文 (包括 .NET XAML 服务默认值) 还使用此信息。

### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute

**参考文档：**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

**参数：**

- 一个字符串，该字符串指定要归类的 XAML 命名空间的标识符。

- 一个字符串，该字符串指定可从上一个参数归类 XAML 命名空间的 XAML 命名空间的标识符。

  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> 指定 XAML 命名空间可由另一个 XAML 命名空间归入。 通常，先前定义的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 中指示了包含 XAML 命令空间。 此方法可用于对库中的 XAML 词汇进行版本控制，并使其与先前定义的针对早期版本的词汇的标记兼容。

### <a name="xmlnsdefinitionattribute"></a>System.windows.markup.xmlnsdefinitionattribute>

**参考文档：**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

**参数：**

- 一个字符串，指定要定义的 XAML 命名空间的标识符。

- 命名 CLR 命名空间的字符串。 CLR 命名空间应在程序集中定义公共类型，并且必须至少有一个 CLR 命名空间类型适用于 XAML 用法。

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定在 XAML 命名空间和 CLR 命名空间之间按程序集进行的映射，然后 XAML 对象编写器或 XAML 架构上下文使用该命名空间进行类型解析。

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>可以将多个应用程序应用于一个程序集。 这可能是由于以下原因引起的：

- 库设计包含多个 CLR 命名空间，适用于运行时 API 访问的逻辑组织;但是，你希望这些命名空间中的所有类型都可以通过引用相同的 XAML 命名空间来使用 XAML。 在这种情况下，可以 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 使用相同 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 值但不同的值来应用多个属性 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> 。 如果要为 XAML 命名空间定义映射，而框架或应用程序要将其用作默认的 XAML 命名空间，则此方法特别有用。

- 库设计包含多个 CLR 命名空间，并且需要在这些 CLR 命名空间中的类型用法之间进行有意的 XAML 命名空间分隔。

- 在程序集中定义 CLR 命名空间，并希望可通过多个 XAML 命名空间访问该命名空间。 当您支持具有相同基本代码的多个词汇时，会发生这种情况。

- 在一个或多个 CLR 命名空间中定义 XAML 语言支持。 在这种情况下， <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 该值应为 `http://schemas.microsoft.com/winfx/2006/xaml` 。

### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute

**参考文档：**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>

**参数：**

- 一个指定 XAML 命名空间的标识符的字符串。

- 一个字符串，指定建议的前缀。

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定一个建议用于 XAML 命名空间的前缀。 当写入 .NET XAML 服务序列化的 XAML 文件中的元素和属性时 <xref:System.Xaml.XamlXmlWriter> ，或者当 xaml 实现库与具有 XAML 编辑功能的设计环境进行交互时，前缀非常有用。

  <xref:System.Windows.Markup.XmlnsPrefixAttribute>可以将多个应用程序应用于一个程序集。 这可能是由于以下原因引起的：

- 程序集定义多个 XAML 命名空间的类型。 在这种情况下，为每个 XAML 命名空间定义不同的前缀值。

- 支持多个词汇，并为每个词汇和 XAML 命名空间使用不同的前缀。

- 在程序集中定义 XAML 语言支持，并为指定 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> `http://schemas.microsoft.com/winfx/2006/xaml` 。 在这种情况下，通常应升级前缀 `x` 。

> [!NOTE]
> .NET XAML 服务还定义了与 XAML 相关的属性 <xref:System.Windows.Markup.RootNamespaceAttribute> 。 此属性是项目系统支持的程序集级别特性，它与 XAML 自定义类型无关。

## <a name="see-also"></a>请参阅

- <xref:System.Attribute>
- [定义与 .NET XAML 服务一起使用的自定义类型](define-custom-types.md)
