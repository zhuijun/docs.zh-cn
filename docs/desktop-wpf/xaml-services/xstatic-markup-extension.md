---
title: x:Static 标记扩展
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: 634a480b4d7446ed09708f6c91276d1c2f61d4a9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551606"
---
# <a name="xstatic-markup-extension"></a>x:Static 标记扩展

引用在公共语言规范中定义的任何静态的按值代码实体 (符合 CLS) 的方式。 引用的静态属性可用于在 XAML 中提供属性的值。

## <a name="xaml-attribute-usage"></a>XAML 属性用法

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a>XAML 值

| | |
|-|-|
|`prefix`|可选。 引用映射的非默认 XAML 命名空间的前缀。 `prefix` 用法中显式显示，因为很少引用默认 XAML 命名空间中的静态属性。 请参阅“备注”。|
|`typeName`|必需。 定义所需静态成员的类型的名称。|
|`staticMemberName`|必需。 ) 的常量、静态属性、字段或枚举值 (所需的静态值成员的名称。|

## <a name="remarks"></a>备注

引用的代码实体必须是以下项之一：

- 常量
- 静态属性
- 一个字段
- 枚举值

如果指定任何其他代码实体（如非静态属性），则会导致编译时错误，如果已编译了 XAML 或 XAML 加载时分析异常，则会引发编译时错误。

可以 `x:Static` 引用当前 xaml 文档的默认 xaml 命名空间中不是的静态字段或属性; 但是，这需要前缀映射。 XAML 命名空间几乎始终在 XAML 文档的根元素上定义。

当 .NET XAML 服务及其 XAML 读取器和 XAML 编写器与默认的 XAML 架构上下文一起运行时，它们可以执行静态属性的查找操作。 此 XAML 架构上下文可以使用 CLR 反射为对象图构造提供必要的静态值。 `typeName`指定的实际上是 XAML 类型名称，而不是 CLR 类型名称，不过，在使用默认 XAML 架构上下文或使用所有基于 CLR 的现有 XAML 实现框架时，这些名称本质上是相同的名称。

当你进行 `x:Static` 不直接是属性值的类型的引用时，请小心。 在 XAML 处理序列中，从标记扩展提供的值不会调用其他值转换。 即使您的 `x:Static` 引用创建一个文本字符串，并且基于文本字符串的属性值的值转换通常出现在该特定成员或返回类型的任何成员值中，也是如此。

特性语法是最常用于该标记扩展的语法。 在 `x:Static` 标识符字符串之后提供的字符串标记被指定为基础 <xref:System.Windows.Markup.StaticExtension.Member%2A> 扩展类的 <xref:System.Windows.Markup.StaticExtension> 值。

还有其他两个在技术上可能的 XAML 用法。 不过，这些用法不太常见，因为它们不太必要：

01. 对象元素语法。

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. 带有用于初始化字符串的显式成员属性的特性语法。

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

在 .NET XAML 服务实现中，对此标记扩展的处理由类定义 <xref:System.Windows.Markup.StaticExtension> 。

`x:Static` 是标记扩展。 XAML 中的所有标记扩展在 `{` `}` 其特性语法中使用和字符，这是 xaml 处理器识别标记扩展必须提供值的约定。 有关标记扩展的详细信息，请参阅 [Markup Extensions for XAML Overview](markup-extensions-overview.md)。

## <a name="wpf-usage-notes"></a>WPF 用法说明

用于 WPF 编程的默认 XAML 命名空间不包含很多有用的静态属性，并且大多数有用的静态属性都具有支持，如可以方便使用的类型转换器 `{x:Static}` 。 对于静态属性，如果满足以下条件之一，则必须映射 XAML 命名空间的前缀：

- 引用的类型存在于 WPF 中，但它不是 WPF () 的默认 XAML 命名空间的一部分 `http://schemas.microsoft.com/winfx/2006/xaml/presentation` 。 这是使用的一种非常常见的方案 `x:Static` 。 例如，你可以将 `x:Static` 具有 XAML 命名空间映射的引用用于 <xref:System> CLR 命名空间和 mscorlib 程序集，以便引用类的静态属性 <xref:System.Environment> 。

- 正在从自定义程序集引用类型。

- 正在引用 WPF 程序集中存在的类型，但该类型位于未映射到 WPF 默认 XAML 命名空间的一部分的 CLR 命名空间中。 CLR 命名空间到 WPF 的默认 XAML 命名空间的映射由各种 WPF 程序集中的定义执行 (有关此概念的详细信息，请参阅 [WPF xaml 的 Xaml 命名空间和命名空间映射](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)) 。 如果 CLR 命名空间主要由通常不适用于 XAML 的类定义组成，则不映射的 CLR 命名空间可能会存在，例如 <xref:System.Windows.Threading> 。

有关如何对 WPF 使用前缀和 XAML 命名空间的详细信息，请参阅 [WPF xaml 的 XAML 命名空间和命名空间映射](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)。

## <a name="see-also"></a>请参阅

- [x:Type 标记扩展](xtype-markup-extension.md)
- [从 WPF 迁移到 System.Xaml 的类型](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
