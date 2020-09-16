---
title: x:ClassModifier 指令
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 73732a06029cca3a4c6c6d82762d5263c5b8c955
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544812"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier 指令
如果 `x:Class` 还提供了，则修改 XAML 编译行为。 具体而言，不是创建具有访问级别 (默认) 的部分，而是 `class` `Public` `x:Class` 使用访问级别创建提供的 `NotPublic` 。 此行为会影响生成的程序集中类的访问级别。

## <a name="xaml-attribute-usage"></a>XAML 属性用法

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|*NotPublic*|要传递给指定的确切字符串 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 与 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 不同，具体取决于所使用的代码隐藏编程语言。 请参阅“备注”。|

## <a name="dependencies"></a>依赖项

还必须在同一元素上提供[x：Class](xclass-directive.md) ，并且该元素必须是页面中的根元素。 有关详细信息，请参阅[ \[ \] 4.3.1.8 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。

## <a name="remarks"></a>备注

`x:ClassModifier`.NET XAML 服务用法中的值因编程语言而异。 要使用的字符串取决于每种语言如何实现其 <xref:System.CodeDom.Compiler.CodeDomProvider> 和返回的类型转换器，以定义和的 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 含义 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ，以及该语言是否区分大小写。

- 对于 c #，要传递的要传递的字符串 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 为 `internal` 。

- 对于 Microsoft Visual Basic .NET，要传递的字符串为 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend` 。

- 对于 c + +/CLI，不存在支持编译 XAML 的目标;因此，传递的值未指定。

你还可以在 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> `public` Visual Basic) 中指定 c # (`Public` ; 但是， <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 由于 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 已是默认行为，因此不常指定。

具有等效用户代码访问级别限制的其他值（如 `private` c # 中的）与不相关， `x:ClassModifier` 因为 XAML 中不支持嵌套类引用，因此， <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 修饰符具有相同的效果。

## <a name="security-notes"></a>安全说明

中声明的访问级别 `x:ClassModifier` 仍受特定框架及其功能的解释。 WPF 包含加载和实例化类型的功能 `x:ClassModifier` `internal` ，其中，如果通过包 URI 引用从 WPF 资源引用此类，则为。 这种情况与其他框架所实现的情况类似，但并不依赖 `x:ClassModifier` 于阻止所有可能的实例化尝试。

## <a name="see-also"></a>请参阅

- [x:Class 指令](xclass-directive.md)
- [WPF 中的代码隐藏和 XAML](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [x:FieldModifier 指令](xfieldmodifier-directive.md)
- [安全性 (WPF)](/dotnet/desktop/wpf/security-wpf)
- [从 WPF 迁移到 System.Xaml 的类型](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
