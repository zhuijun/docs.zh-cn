---
title: x:TypeArguments 指令
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 430ab65af52282ccb1d429cd2523efe213f13609
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543546"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments 指令

将泛型的约束类型参数传递到泛型类型的构造函数。

## <a name="xaml-attribute-usage"></a>XAML 属性用法

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`object`|XAML 类型的对象元素声明，由 CLR 泛型类型支持。 如果 `object` 引用的 xaml 类型不是来自默认 xaml 命名空间，则 `object` 需要一个前缀以指示 xaml 命名空间，其中 `object` 存在。|
|`typeString`|一个字符串，它将一个或多个 XAML 类型名称声明为字符串，这些名称提供 CLR 泛型类型的类型参数。 有关其他语法说明，请参阅备注。|

## <a name="remarks"></a>备注

在大多数情况下，作为字符串中的信息项使用的 XAML 类型作为 `typeString` 前缀。 CLR 泛型约束的典型类型 (例如， <xref:System.Int32> <xref:System.String>) 来自 clr 基类库。 这些库不会映射到典型的特定于框架的默认 XAML 命名空间，因此需要 XAML 使用的前缀映射。

可以使用逗号分隔符指定多个 XAML 类型名称。

如果泛型约束本身使用泛型类型，则嵌套约束类型参数可由括号括起来 ( # A1。

请注意，的这一定义 `x:TypeArguments` 特定于 .NET XAML 服务并使用 CLR 支持。 可在[ \[ \] 5.3.11 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))中找到语言级定义。

## <a name="usage-examples"></a>用法示例

对于这些示例，假定声明以下 XAML 命名空间定义：

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a>List\<String>

`<scg:List x:TypeArguments="sys:String" ...>`<xref:System.Collections.Generic.List%601>使用类型参数实例化新的 <xref:System.String> 。

### <a name="dictionarystringstring"></a>Dictionary\<String,String>

`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`<xref:System.Collections.Generic.Dictionary%602>使用两个类型参数实例化一个新的 <xref:System.String> 。

### <a name="queuekeyvaluepairstringstring"></a>队列<KeyValuePair\<String,String>>

`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` 实例化一个新 <xref:System.Collections.Generic.Queue%601> 的，它的约束具有 <xref:System.Collections.Generic.KeyValuePair%602> 内部约束类型参数 <xref:System.String> 和 <xref:System.String> 。

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 和 WPF 泛型 XAML 用法

对于 XAML 2006 用法以及用于 WPF 应用程序的 XAML， `x:TypeArguments` 一般情况下，xaml 中的和泛型类型用法存在以下限制：

- 只有 XAML 文件的根元素可以支持引用泛型类型的泛型 XAML 用法。

- 根元素必须映射到至少具有一个类型参数的泛型类型。 例如 <xref:System.Windows.Navigation.PageFunction%601>。 页函数是 WPF 中 XAML 泛型用法支持的主要方案。

- 泛型的根元素 XAML 对象元素还必须使用声明分部类 `x:Class` 。 即使定义 WPF 生成操作也是如此。

- `x:TypeArguments` 无法引用嵌套的泛型约束。

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>不带 WPF 3.0 或 WPF 3.5 依赖项的 XAML 2009 或 XAML 2006

在 .NET XAML 服务中，对于 XAML 2006 或 XAML 2009，对泛型 XAML 用法的 WPF 相关限制是宽松的。 可以在支持类型系统和对象模型可以支持的 XAML 标记中的任意位置实例化泛型对象元素。

如果使用 XAML 2009，而不是映射 CLR 基类型以获取公共语言基元的 XAML 类型，则可以将 [常见 XAML 语言基元的内置类型](types-for-primitives.md) 用作中的信息项 `typeString` 。 例如，可以声明以下 (前缀映射，但 x 是 xaml 2009) 的 XAML 语言 XAML 命名空间：

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

在 WPF 中，当面向 .NET Framework 4 或 .NET Core 3.0 (或更高版本的) 时，可以将 XAML 2009 功能与一起使用， `x:TypeArguments` 但仅适用于未进行标记) 编译的稀疏 xaml (xaml。 WPF 的已编译标记的 XAML 以及 XAML 的 BAML 形式当前不支持 XAML 2009 关键字和功能。 如果需要对 XAML 进行标记编译，则必须在 [xaml 2006 和 WPF 一般 XAML 使用](#xaml-2006-and-wpf-generic-xaml-usages) 部分中所述的限制下运行。 仅 .NET Framework 支持 BAML。

## <a name="see-also"></a>请参阅

- [x:Class 指令](xclass-directive.md)
- [x:Type 标记扩展](xtype-markup-extension.md)
- [常见 XAML 语言基元的内置类型](types-for-primitives.md)
- [XAML 中的泛型](generics.md)
