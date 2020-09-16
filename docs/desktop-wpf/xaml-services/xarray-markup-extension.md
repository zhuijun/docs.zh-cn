---
title: x:Array 标记扩展
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: b812939cbaa74576361de534c0d39ba45536cbcf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555167"
---
# <a name="xarray-markup-extension"></a>x:Array 标记扩展

通过标记扩展为 XAML 中的对象数组提供常规支持。 这对应于 `x:ArrayExtension` [ms-chap] 中的 XAML 类型。

## <a name="xaml-object-element-usage"></a>XAML 对象元素用法

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`typeName`|你将包含的类型的名称 `x:Array` 。 `typeName` 可以 (，并且通常) 包含 XAML 类型定义的 XAML 命名空间的前缀。|
|`arrayContents`|分配给内部属性的项内容 `ArrayExtension.Items` 。 通常，这些项被指定为一个或多个包含在 `x:Array` 开始和结束标记中的对象元素。 此处指定的对象应可分配给在中指定的 XAML 类型 `typeName` 。|

## <a name="remarks"></a>备注

`Type` 是所有对象元素的必需属性 `x:Array` 。 `Type`参数值无需使用 `x:Type` 标记扩展; 类型的短名称为 XAML 类型，可以将其指定为字符串。

在 .NET XAML 服务实现中，所创建数组的输入 XAML 类型和输出 CLR 之间的关系受 <xref:System.Type> 标记扩展的服务上下文影响。 输出 <xref:System.Type> 是 <xref:System.Xaml.XamlType.UnderlyingType%2A> 输入 xaml 类型的，在 <xref:System.Xaml.XamlType> 根据 XAML 架构上下文和上下文提供的服务查找必要后 <xref:System.Windows.Markup.IXamlTypeResolver> 。

处理后，数组内容将分配给 `ArrayExtension.Items` 内部属性。 在 <xref:System.Windows.Markup.ArrayExtension> 实现中，这由表示 <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType> 。

在 .NET XAML 服务实现中，对此标记扩展的处理由类定义 <xref:System.Windows.Markup.ArrayExtension> 。 <xref:System.Windows.Markup.ArrayExtension> 不是密封的，并且可用作自定义数组类型的标记扩展实现的基础。

`x:Array` 更适用于 XAML 中的常规语言扩展性。 但 `x:Array` 也可用于指定某些属性的 xaml 值，这些属性采用支持 XAML 的集合作为其结构化属性内容。 例如，可以指定具有用法的属性的内容 <xref:System.Collections.IEnumerable> `x:Array` 。

`x:Array` 是标记扩展。 当要求转义特性值应为非文本值或非处理程序名称时，通常会实现标记扩展，相对于只在某些类型或属性上放置类型转换器而言，此需求更具有全局性。 `x:Array` 部分是该规则的例外情况，因为它不提供备用属性值处理，而是 `x:Array` 提供其内部文本内容的替代处理。 此行为使现有内容模型可能不支持的类型可以分组到数组中，稍后通过访问命名数组在代码隐藏中进行引用;可以调用 <xref:System.Array> 方法来获取单个数组项。

XAML 中的所有标记扩展在其特性语法中使用大括号 ({,} `)` ，这是 xaml 处理器识别标记扩展必须处理特性值的约定。 有关常规标记扩展的详细信息，请参阅 [XAML 的类型转换器和标记扩展](type-converters-and-markup-extensions.md)。

在 XAML 2009 中， `x:Array` 定义为语言基元，而不是标记扩展。 有关详细信息，请参阅 [常见 XAML 语言基元的内置类型](types-for-primitives.md)。

## <a name="wpf-usage-notes"></a>WPF 用法说明

通常，填充的对象元素 `x:Array` 不是 XAML 命名空间中存在的元素 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ，需要映射到非默认的 xaml 命名空间。

例如，下面是一个包含两个字符串的简单数组，其中 `sys` 前缀 (，还 `x` 在数组级别定义) 。

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

对于用作数组元素的自定义类型，该类还必须支持在 XAML 中实例化为对象元素的要求。 有关详细信息，请参阅 [WPF 的 XAML 和自定义类](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)。

## <a name="see-also"></a>请参阅

- [标记扩展和 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [从 WPF 迁移到 System.Xaml 的类型](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
