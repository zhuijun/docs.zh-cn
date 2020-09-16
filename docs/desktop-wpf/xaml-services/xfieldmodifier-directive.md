---
title: x:FieldModifier 指令
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 4e67a6dac49b8d6a7d316526f99a1519b08fd68b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554470"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier 指令
修改 XAML 编译行为，以便使用 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> access 而不是默认行为来定义命名对象引用的字段 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 。

## <a name="xaml-attribute-usage"></a>XAML 属性用法

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|*公共*|传递给指定的确切字符串 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 与 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 不同，具体取决于所使用的代码隐藏编程语言。 请参阅“备注”。|

## <a name="dependencies"></a>依赖项

 如果 XAML 生产使用 `x:FieldModifier` 任意位置，则该 xaml 生产的根元素必须声明 [x：Class 指令](xclass-directive.md)。

## <a name="remarks"></a>备注

`x:FieldModifier` 与声明类或其成员的常规访问级别无关。 当处理作为 XAML 生产一部分的特定 XAML 对象时，此方法仅适用于 XAML 处理行为，并成为可在应用程序的对象图中访问的对象。 默认情况下，此类对象的字段引用保持为私有，这会阻止控件使用者直接修改对象图。 相反，控件使用者应该使用由编程模型启用的标准模式（如通过获取布局根、子元素集合、专用公共属性等）来修改对象关系图。

特性的值 `x:FieldModifier` 因编程语言而异，其用途在特定框架中可能有所不同。 要使用的字符串取决于每种语言如何实现其 <xref:System.CodeDom.Compiler.CodeDomProvider> 和返回的类型转换器，以定义和的 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 含义 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ，以及该语言是否区分大小写。

- 对于 c #，要传递的要传递的字符串 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 为 `public` 。

- 对于 Microsoft Visual Basic .NET，要传递的字符串为 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> `Public` 。

- 对于 c + +/CLI，当前不存在 XAML 的目标;因此，传递的字符串未定义。

你还可以在 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> Visual Basic 中指定 (`internal` c # 中 `Friend`) 但指定 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 非常罕见，因为 `NotPublic` 行为已是默认值。

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 是默认行为，因为编译 XAML 的程序集之外的代码很少需要访问 XAML 创建的元素。 WPF 安全体系结构与 XAML 编译行为一起不会声明将元素实例存储为公共的字段，除非您专门将设置 `x:FieldModifier` 为允许公共访问。

`x:FieldModifier` 仅适用于具有 [X：Name 指令](xname-directive.md) 的元素，因为该名称用于在其公开后引用字段。

默认情况下，根元素的分部类是公共的;但是，可以使用 [X:ClassModifier 指令](xclassmodifier-directive.md)使其成为非公共的。 [X:ClassModifier 指令](xclassmodifier-directive.md)还会影响 root 元素类的实例的访问级别。 你可以将 `x:Name` 和置于 `x:FieldModifier` 根元素上，但这只会生成根元素的公共字段副本，其真正的根元素类访问级别仍由 [x:ClassModifier 指令](xclassmodifier-directive.md)控制。

## <a name="see-also"></a>请参阅

- [XAML 及 WPF 的自定义类](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
- [WPF 中的代码隐藏和 XAML](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [x:Name 指令](xname-directive.md)
- [Building a WPF Application (WPF)](/dotnet/desktop/wpf/app-development/building-a-wpf-application-wpf)（生成 WPF 应用程序 (WPF)）
- [x:ClassModifier 指令](xclassmodifier-directive.md)
