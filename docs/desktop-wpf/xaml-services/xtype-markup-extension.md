---
title: x:Type 标记扩展
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: 00e6684f6ad1eb8d96f72f49bd5e0d211c8166c3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559065"
---
# <a name="xtype-markup-extension"></a>x:Type 标记扩展

提供作为 <xref:System.Type> 指定 XAML 类型的基础类型的 CLR 对象。

## <a name="xaml-attribute-usage"></a>XAML 属性用法

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a>XAML 对象元素用法

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`prefix`|可选。 映射非默认 XAML 命名空间的前缀。 通常不需要指定前缀。 请参阅“备注”。|
|`typeNameValue`|必需。 可解析为当前默认 XAML 命名空间的类型名称;如果提供，则为指定的映射前缀 `prefix` 。|

## <a name="remarks"></a>备注

`x:Type`标记扩展的函数与 `typeof()` c # 中的运算符或 `GetType` Microsoft Visual Basic 中的运算符类似。

`x:Type`标记扩展为采用该类型的属性提供 from 字符串转换行为 <xref:System.Type> 。 输入为 XAML 类型。 输入 XAML 类型和输出 CLR 之间的关系 <xref:System.Type> 是 <xref:System.Type> <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType> ， <xref:System.Xaml.XamlType> 在根据 XAML 架构上下文和上下文提供的服务查找必需的后，输出为输入的 <xref:System.Windows.Markup.IXamlTypeResolver> 。

在 .NET XAML 服务中，对此标记扩展的处理由类定义 <xref:System.Windows.Markup.TypeExtension> 。

在特定的框架实现中，一些 <xref:System.Type> 作为值使用的属性可以直接接受 (类型) 的字符串值的类型名称 `Name` 。 但是，实现此行为是一种复杂的方案。 有关示例，请参阅后面的 "WPF 用法说明" 部分。

特性语法是最常用于该标记扩展的语法。 在 `x:Type` 标识符字符串之后提供的字符串标记被指定为基础 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 扩展类的 <xref:System.Windows.Markup.TypeExtension> 值。 在基于 CLR 类型的 .NET XAML 服务的默认 XAML 架构上下文下，此特性的值是 <xref:System.Reflection.MemberInfo.Name%2A> 所需类型的，或者包含 <xref:System.Reflection.MemberInfo.Name%2A> 前面带有非默认 XAML 命名空间映射前缀的。

`x:Type`标记扩展可用于对象元素语法。 在这种情况下，需要指定属性的值 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 才能正确地初始化扩展。

`x:Type`标记扩展还可用作详细特性; 但这种用法并不典型：`<object property="{x:Type TypeName=typeNameValue}" .../>`

## <a name="wpf-usage-notes"></a>WPF 用法说明

### <a name="default-xaml-namespace-and-type-mapping"></a>默认 XAML 命名空间和类型映射

WPF 编程的默认 XAML 命名空间包含典型 XAML 方案所需的大多数 XAML 类型;因此，在引用 XAML 类型值时，通常可以避免前缀。 如果引用的是自定义程序集的类型或存在于 WPF 程序集中的类型，但却来自未映射到默认 XAML 命名空间的 CLR 命名空间，则可能需要映射前缀。 有关前缀、XAML 命名空间和映射 CLR 命名空间的详细信息，请参阅 [WPF xaml 的 XAML 命名空间和命名空间映射](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)。

### <a name="type-properties-that-support-typename-as-string"></a>支持类型为字符串的类型属性

WPF 支持用于指定类型的某些属性的值的方法， <xref:System.Type> 无需 `x:Type` 使用标记扩展用法。 相反，你可以将值指定为命名类型的字符串。 这是和的 <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> 示例 <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType> 。 不通过类型转换器或标记扩展提供对此行为的支持。 相反，这是通过实现的延迟行为 <xref:System.Windows.FrameworkElementFactory> 。

Silverlight 支持类似的约定。 事实上，Silverlight 目前并不支持 `{x:Type}` 其 XAML 语言支持，并且不接受 `{x:Type}` 用于支持 WPF Silverlight XAML 迁移的少数几种情况。 因此，类型即字符串行为内置于所有 Silverlight 本机属性评估中，其中 a <xref:System.Type> 是值。

## <a name="xaml-2009"></a>XAML 2009

XAML 2009 提供对泛型类型的其他支持，并修改和的功能行为 `x:TypeArguments` `x:Type` 以提供此支持。

- `x:TypeArguments` 与泛型对象实例化关联的对象元素可以位于根以外的元素上。 有关详细信息，请参阅 [X:TypeArguments 指令](xtypearguments-directive.md)的 "XAML 2009" 一节。

- XAML 2009 支持用于在标记中指定泛型类型的约束的语法。 这可以由 `x:TypeArguments` 、通过 `x:Type` 或两个功能组合使用。

- 当处理 XAML 2009 for load 时，WPF XAML 实现还会将此功能添加到使用类型的某些框架属性的隐式类型转换行为 <xref:System.Type> 。

在 WPF 中，可以使用 XAML 2009 功能，但仅针对未进行标记编译) 的松散 XAML (XAML。 WPF 的已编译标记的 XAML 以及 XAML 的 BAML 形式当前不支持 XAML 2009 关键字和功能。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Style>
- [样式设置和模板化](../fundamentals/styles-templates-overview.md)
- [XAML 概述 (WPF)](../fundamentals/xaml.md)
- [标记扩展和 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
