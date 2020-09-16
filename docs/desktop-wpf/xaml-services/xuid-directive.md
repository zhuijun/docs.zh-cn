---
title: x:Uid 指令
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 3de02702e6fd2be63bc2d099dad11f896b281ad1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543493"
---
# <a name="xuid-directive"></a>x:Uid 指令

为标记元素提供一个唯一标识符。 在许多情况下，XAML 本地化流程和工具使用此唯一标识符。

## <a name="xaml-attribute-usage"></a>XAML 属性用法

```xaml
<object x:Uid="identifier"... />
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`identifier`|手动创建或自动生成的字符串，当使用者解释该字符串时，该字符串应在文件中是唯一的 `x:Uid` 。|

## <a name="remarks"></a>备注

在 [MS-CHAP] 中， `x:Uid` 定义为指令。 有关详细信息，请参阅[ \[ \] 5.3.6 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。

`x:Uid``x:Name`由于有规定的 XAML 本地化方案，并且用于本地化的标识符不依赖于的编程模型，因此与两者分开 `x:Name` 。 此外，由 `x:Name` xaml 名称范围控制; 但是， `x:Uid` 不受任何 xaml 语言定义的唯一性强制概念的约束。 不是本地化流程的一部分的 (处理器) 的 XAML 处理器不应强制实施值的唯一性 `x:Uid` 。 从概念上讲，这种责任在值的发起方。 `x:Uid`单个 XAML 源中值的唯一性假定对于值的使用者（如专用的全球化过程或工具）是合理的。 典型的唯一性模型是， `x:Uid` 值在表示 XAML 的 XML 编码文件中是唯一的。

对特定 XAML 架构有重要了解的工具可以选择仅应用于 `x:Uid` 真正可本地化的字符串，而不是在标记中遇到文本字符串值的所有情况。

框架可以 `x:Uid` 通过将特性应用 <xref:System.Windows.Markup.UidPropertyAttribute> 于定义类型，将其对象模型中的特定属性指定为别名。 如果框架指定了特定属性，则对 `x:Uid` 同一对象同时指定和化名成员是无效的。 如果同时 `x:Uid` 指定了和别名成员，则在这种情况下，.NET XAML 服务 API 通常会引发 <xref:System.Xaml.XamlDuplicateMemberException> 。

## <a name="wpf-usage-notes"></a>WPF 用法说明

有关中的角色的详细信息， `x:Uid` 请参阅 [适用于 Wpf 的全球化](/dotnet/desktop/wpf/advanced/globalization-for-wpf) 和 XAML 的 BAML 形式。 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [WPF 的全球化](/dotnet/desktop/wpf/advanced/globalization-for-wpf)
