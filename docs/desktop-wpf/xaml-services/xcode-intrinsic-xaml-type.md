---
title: x:Code 内部 XAML 类型
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: ea7bc17cba19137b4e4ca2d8cddb32e6630887c9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544838"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code 内部 XAML 类型
允许在 XAML 生产中放置代码。 此类代码可由编译 XAML 的任何 XAML 处理器实现进行编译，或在 XAML 生产环境中保留，以供以后使用（如运行时的解释）使用。

## <a name="xaml-object-element-usage"></a>XAML 对象元素用法

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a>备注

`x:Code`Xaml 指令元素中的代码仍会在提供的常规 XML 命名空间和 xaml 命名空间中进行解释。 因此，通常需要将用于段内的代码括起来 `x:Code` `CDATA` 。

`x:Code` 对于 XAML 生产的所有可能的部署机制，都不允许这样做。 在特定框架中 (例如 WPF) 必须编译代码。 在其他框架中， `x:Code` 可能通常不允许使用。

对于允许托管内容的框架 `x:Code` ，用于内容的正确语言编译器由 `x:Code` 用于编译应用程序的包含项目的设置和目标决定。

## <a name="wpf-usage-notes"></a>WPF 用法说明

在 `x:Code` FOR WPF 内声明的代码有几个值得注意的限制：

- `x:Code`指令元素必须是 XAML 生成的根元素的直接子元素。

- 必须在父根元素上提供[X：Class 指令](xclass-directive.md)。

- 放置在中的代码 `x:Code` 将被编译为位于已为该 XAML 页创建的分部类的范围内。 因此，您定义的所有代码必须是此分部类的成员或变量。

- 除了在分部类中嵌套类之外，不能定义其他类 (允许嵌套，但这并不典型，因为在 XAML) 中无法引用嵌套类。 不能定义用于现有分部类的命名空间，也不能将其添加到中。

- 对分部类之外的代码实体的引用必须完全限定。 如果被声明的成员被替代为分部类可重写成员，则必须用特定语言的 override 关键字指定此项。 如果在作用域中声明的成员 `x:Code` 与在 XAML 中创建的分部类的成员冲突，则编译器将报告冲突，但 XAML 文件无法编译或加载。

## <a name="see-also"></a>请参阅

- [x:Class 指令](xclass-directive.md)
- [WPF 中的代码隐藏和 XAML](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [XAML 概述 (WPF)](../fundamentals/xaml.md)
