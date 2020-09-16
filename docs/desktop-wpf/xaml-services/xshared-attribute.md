---
title: x:Shared 特性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: d5000b51d83066ec2d529db2033d8ac54f7ad329
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557783"
---
# <a name="xshared-attribute"></a>x:Shared 特性

当设置为时 `false` ，将修改 WPF 资源检索行为，以便对特性化资源的请求为每个请求创建一个新的实例，而不是为所有请求共享同一个实例。

## <a name="xaml-attribute-usage"></a>XAML 属性用法

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a>备注

`x:Shared` 映射到 XAML 语言 XAML 命名空间，并由 .NET XAML 服务及其 XAML 读取器识别为有效的 XAML 语言元素。 但是，的指定功能 `x:Shared` 仅与 wpf 应用程序和 WPF XAML 分析器相关。 在 WPF 中， `x:Shared` 仅当应用于 wpf 内存在的对象时，它才可用作特性 <xref:System.Windows.ResourceDictionary> 。 其他用法不会引发分析异常或其他错误，但它们不起作用。

`x:Shared`XAML 语言规范中未指定的含义。 其他 XAML 实现（如在 .NET XAML 服务上构建的实现）不一定提供资源共享支持。 此类 XAML 实现可以在也使用值的支持框架中提供类似的行为 `x:Shared` 。

在 WPF 中，资源的默认 `x:Shared` 条件是 `true` 。 这种情况意味着，任何给定的资源请求始终返回相同的实例。

如果修改通过资源 API 返回的对象（如 <xref:System.Windows.FrameworkElement.FindResource%2A> ），或直接在中修改对象，则会 <xref:System.Windows.ResourceDictionary> 更改原始资源。 如果对该资源的引用是动态资源引用，则该资源的使用者将获取更改的资源。

如果对资源的引用是静态资源引用，则在处理时间之后对资源所做的更改 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 是不相关的。 有关静态和动态资源引用的详细信息，请参阅 [XAML 资源](../fundamentals/xaml-resources-define.md)。

显式指定的 `x:Shared="true"` 操作很少完成，因为它已是默认值。 WPF 对象模型中没有等效的直接代码 `x:Shared` ; 它只能在 XAML 用法中指定，并且必须通过默认的 WPF 行为进行处理，或者，如果使用 .NET Xaml 服务及其 XAML 读取器进行处理，则必须使用加载路径上的中间 XAML 节点流进行处理。

的一种情况 `x:Shared="false"` 是，如果将 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 派生类定义为资源，然后将元素资源引入到内容模型中。 `x:Shared="false"` 允许在同一集合中多次引入元素资源 (如 <xref:System.Windows.Controls.UIElementCollection>) 。 如果 `x:Shared="false"` 此集合强制执行其内容的唯一性，则不会出现这种情况。 但是，该 `x:Shared="false"` 行为会创建资源的另一个相同实例，而不是返回同一个实例。

的另一种情况 `x:Shared="false"` 是，如果为 <xref:System.Windows.Freezable> 动画值使用资源，但想要基于每个动画修改资源。

的字符串处理 `false` 不区分大小写。

在 WPF 中， `x:Shared` 仅在以下情况下有效：

- <xref:System.Windows.ResourceDictionary>包含必须编译的项的 `x:Shared` 。 <xref:System.Windows.ResourceDictionary>不能位于松散 XAML 内或用于主题。

- <xref:System.Windows.ResourceDictionary>包含项的不能嵌套在另一个中 <xref:System.Windows.ResourceDictionary> 。 例如，你不能使用 `x:Shared` 中已有项的中的项 <xref:System.Windows.ResourceDictionary> <xref:System.Windows.Style> <xref:System.Windows.ResourceDictionary> 。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.ResourceDictionary>
- [XAML 资源](../fundamentals/xaml-resources-define.md)
- [基元素](/dotnet/desktop/wpf/advanced/base-elements)
