---
title: .NET Framework 对 Windows 应用商店应用程序和 Windows 运行时的支持情况
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Windows Store apps, .NET Framework support for
- Windows Runtime, .NET Framework support for
- .NET for Windows Store apps
- .NET Framework, and Windows Store apps
- .NET Framework, and Windows Runtime
ms.assetid: 6fa7d044-ae12-4c54-b8ee-50915607a565
ms.openlocfilehash: 2d1b35181f508a616ab264c859119da7512e5f23
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547566"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>.NET Framework 对 Windows 应用商店应用程序和 Windows 运行时的支持情况

.NET Framework 4.5 使用 Windows 运行时支持许多软件开发方案。 这些方案分为三类：

- 使用 XAML 控件开发 Windows 8.x 应用商店应用，如 [使用 c # 或 Visual Basic 的 Windows 应用商店应用的路线图](/previous-versions/windows/apps/br229583(v=win.10))中所述， [如何 (XAML) ](/previous-versions/windows/apps/br229566(v=win.10))，以及 [适用于 windows 应用商店应用的 .net 概述](/previous-versions/windows/apps/br230302(v=vs.140))。

- 开发要在使用 .NET Framework 创建的 Windows 8.x 应用商店应用程序中使用的类库。

- 开发 Windows 运行时组件，打包在中。WinMD 文件，可由支持 Windows 运行时的任何编程语言使用。 有关示例，请参阅 [在 c # 中创建 Windows 运行时组件和 Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)。

本主题概述 .NET Framework 为所有三个类别提供的支持，并介绍 Windows 运行时组件的方案。 第一部分包含有关 .NET Framework 与 Windows 运行时之间的关系的基本信息，并说明了在帮助系统和 IDE 中可能会遇到的一些问题。 [第二部分](#WindowsRuntimeComponents)讨论用于开发 Windows 运行时组件的方案。

## <a name="the-basics"></a>基础知识

.NET Framework 通过提供适用于 Windows 8.x 应用商店应用的 .NET，并支持 Windows 运行时本身，来支持前面列出的三种开发方案。

- [.NET Framework 和 Windows 运行时命名空间](/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) 提供了 .NET Framework 类库的简化视图，并只包含可用于创建 Windows 8.X 应用商店应用和 Windows 运行时组件的类型和成员。

  - 使用 Visual Studio (Visual Studio 2012 或更高版本) 开发 Windows 8.x 应用商店应用或 Windows 运行时组件时，一组引用程序集可确保只显示相关类型和成员。

  - 此简化的 API 集通过删除在 .NET Framework 中重复的功能或复制 Windows 运行时功能来进一步简化。 例如，它仅包含集合类型的泛型版本，并消除 XML 文档对象模型，以支持 Windows 运行时 XML API 集。

  - 还会删除简单包装操作系统 API 的功能，因为 Windows 运行时可以从托管代码调用。

  若要了解有关适用于 Windows 8.x 应用商店应用的 .NET 的详细信息，请参阅 [适用于 Windows 应用商店应用的 .net 概述](/previous-versions/windows/apps/br230302(v=vs.140))。 若要阅读有关 API 选择过程的信息，请参阅 .NET 博客中的 [用于 Metro 风格的应用程序](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) 条目。

- [Windows 运行时](/uwp/api/)提供用于生成 Windows 8.X 应用商店应用的用户界面元素，并提供对操作系统功能的访问权限。 与 .NET Framework 一样，Windows 运行时具有元数据，使 c # 和 Visual Basic 编译器可以使用 Windows 运行时使用 .NET Framework 类库的方式。 通过隐藏一些差异，.NET Framework 可以更轻松地使用 Windows 运行时：

  - .NET Framework 和 Windows 运行时之间编程模式的某些差异（如添加和移除事件处理程序的模式）是隐藏的。 只需使用 .NET Framework 模式即可。

  - 隐藏在常用类型上存在一些差异（例如，基元类型和集合）。 你只需使用 .NET Framework 类型，如本文后面的 [IDE 中显示的差异](#DifferencesVisibleInIDE)中所述。

大多数情况下，对 Windows 运行时 .NET Framework 支持是透明的。 下一节将讨论托管代码与 Windows 运行时之间的一些明显差异。

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework 和 Windows 运行时参考文档

Windows 运行时和 .NET Framework 文档集是独立的。 如果按 F1 显示关于类型或成员的帮助，将显示相应集合中的参考文档。 但是，如果浏览 [Windows 运行时引用](/uwp/api/) ，则可能会遇到似乎令困惑的示例：

- 接口等主题 <xref:Windows.Foundation.Collections.IIterable%601> 没有 Visual Basic 或 c # 的声明语法。 相反，在这种情况下，".NET：此接口" ) ，".NET：此接口" 将显示在语法部分上方 (\<T> 。 这是因为 .NET Framework 和 Windows 运行时提供与不同接口相同的功能。 此外，它们还有下列行为差异：`IIterable` 有一个 `First` 方法，而没有返回枚举器的 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法。 Windows 运行时 .NET Framework 通过使托管代码显示为使用熟悉的类型，而不是强制您了解执行常见任务的其他方式。 你不会 `IIterable` 在 IDE 中看到该接口，因此，在 Windows 运行时参考 "文档中遇到此接口的唯一方法是直接浏览该文档。

- <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)>文档说明了一个紧密相关的问题：不同语言的参数类型似乎不同。 对于 C# 和 Visual Basic，参数类型为 <xref:System.String?displayProperty=nameWithType> 和 <xref:System.Uri?displayProperty=nameWithType>。 同样，这是因为 .NET Framework 具有自己的 `String` 和 `Uri` 类型，并且，对于这种常用的类型，不宜强制 .NET Framework 用户了解执行操作的不同方式。 在 IDE 中，.NET Framework 隐藏相应的 Windows 运行时类型。

- 在少数情况下（如 <xref:Windows.UI.Xaml.GridLength> 结构），.NET Framework 提供名称相同但功能更多的类型。 例如，有些构造函数和属性主题与 `GridLength` 相关，但是其语法部分仅适用于 Visual Basic 和 C#，因为成员仅在托管代码时是可用的。 在 Windows 运行时中，结构只有字段。 Windows 运行时结构需要 helper 类， <xref:Windows.UI.Xaml.GridLengthHelper> 以提供等效功能。 当你在编写托管代码时，不会在 IDE 中看到该帮助器类。

- 在 IDE 中，Windows 运行时类型看起来是从派生的 <xref:System.Object?displayProperty=nameWithType> 。 它们看上去拥有从 <xref:System.Object> 继承的成员，例如 <xref:System.Object.ToString%2A?displayProperty=nameWithType>。 如果实际从继承的类型 <xref:System.Object> ，并且 Windows 运行时类型可以强制转换为，则这些成员的操作方式与此相同 <xref:System.Object> 。 此功能是 .NET Framework 为 Windows 运行时提供的支持的一部分。 但是，如果您查看 Windows 运行时参考文档中的类型，则不会显示此类成员。 <xref:System.Object?displayProperty=nameWithType> 参考文档为这些明显继承的成员提供了文档。

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>可在 IDE 中看到的差异

在更高级的编程方案中，例如，使用以 c # 编写的 Windows 运行时组件为使用 JavaScript 为 Windows 构建的 Windows 8.x 应用商店应用程序提供应用程序逻辑，这些差异在 IDE 和文档中都很明显。 当组件 `IDictionary<int, string>` 向 javascript 返回并在 javascript 调试器中查看该组件时，你将看到方法， `IMap<int, string>` 因为 JavaScript 使用 Windows 运行时类型。 下表显示了这两种语言中以不同方式显示的一些常用的集合类型：

|Windows 运行时类型|对应的 .NET Framework 类型|
|--------------------------------------------------------------|---------------------------------------|
|`IIterable<T>`|`IEnumerable<T>`|
|`IIterator<T>`|`IEnumerator<T>`|
|`IVector<T>`|`IList<T>`|
|`IVectorView<T>`|`IReadOnlyList<T>`|
|`IMap<K, V>`|`IDictionary<TKey, TValue>`|
|`IMapView<K, V>`|`IReadOnlyDictionary<TKey, TValue>`|
|`IBindableIterable`|`IEnumerable`|
|`IBindableVector`|`IList`|
|`Windows.UI.Xaml.Data.INotifyPropertyChanged`|`System.ComponentModel.INotifyPropertyChanged`|
|`Windows.UI.Xaml.Data.PropertyChangedEventHandler`|`System.ComponentModel.PropertyChangedEventHandler`|
|`Windows.UI.Xaml.Data.PropertyChangedEventArgs`|`System.ComponentModel.PropertyChangedEventArgs`|

在 Windows 运行时中， `IMap<K, V>` `IMapView<K, V>` 使用来循环访问和 `IKeyValuePair` 。 在将它们传递给托管代码时，它们显示为 `IDictionary<TKey, TValue>` 和 `IReadOnlyDictionary<TKey, TValue>`，因此自然要使用 `System.Collections.Generic.KeyValuePair<TKey, TValue>` 来枚举它们。

接口在托管代码中的显示方式将影响实现这些接口的类型的显示方式。 例如， `PropertySet` 类实现 `IMap<K, V>`，后者在托管代码中显示为 `IDictionary<TKey, TValue>`。 `PropertySet` 显示为已实现 `IDictionary<TKey, TValue>` 而不是 `IMap<K, V>`，因此在托管代码中，它显示为具有 `Add` 方法，其行为类似于 .NET Framework 字典中的 `Add` 方法。 它不会显示为具有 `Insert` 方法。

有关使用 .NET Framework 创建 Windows 运行时组件的详细信息，以及演示如何将此类组件与 JavaScript 一起使用的演练，请参阅使用 [c # 和 Visual Basic 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)。

### <a name="primitive-types"></a>基元类型

为了能够在托管代码中自然地使用 Windows 运行时，.NET Framework 基元类型在代码中显示，而不是 Windows 运行时基元类型。 在 .NET Framework 中，基元类型（如 `Int32` 结构）具有许多有用的属性和方法，如 `Int32.TryParse` 方法。 相比之下，Windows 运行时中的基元类型和结构只有字段。 在托管代码中使用基元时，它们将显示为 .NET Framework 类型，您可以如往常一样使用 .NET Framework 类型的属性和方法。 以下列表提供了一个摘要：

- 对于 Windows 运行时基元，，，，， `Int32` `Int64` `Single` `Double` `Boolean` `String` () 、、、和的 Unicode 字符的不可变集合，请 `Enum` `UInt32` `UInt64` `Guid` 使用命名空间中具有相同名称的类型 `System` 。

- 对于 `UInt8`，请使用 `System.Byte`。

- 对于 `Char16`，请使用 `System.Char`。

- 对于 `IInspectable` 接口，使用 `System.Object`。

- 对于 `HRESULT`，使用包含一个 `System.Int32` 成员的结构。

与接口类型一样，仅当 .NET Framework 项目是使用 JavaScript 生成的 Windows 8.x 应用商店应用使用的 Windows 运行时组件时，才会看到此表示形式的证据。

在托管代码中显示为其 .NET Framework 等效项的其他基本的常用 Windows 运行时类型包括 `Windows.Foundation.DateTime` 结构，结构在托管代码中显示为 <xref:System.DateTimeOffset?displayProperty=nameWithType> 结构，结构显示 `Windows.Foundation.TimeSpan` 为 <xref:System.TimeSpan?displayProperty=nameWithType> 结构。

### <a name="other-differences"></a>其他差异

在少数情况下，.NET Framework 类型会显示在代码中，而不是 Windows 运行时类型需要对你的操作。 例如， <xref:Windows.Foundation.Uri?displayProperty=nameWithType> 类 <xref:System.Uri?displayProperty=nameWithType> 在 .NET Framework 代码中显示为。 <xref:System.Uri?displayProperty=nameWithType> 允许使用相对 URI，但 <xref:Windows.Foundation.Uri?displayProperty=nameWithType> 需要绝对 uri。 因此，当您将 URI 传递到 Windows 运行时方法时，必须确保它是绝对的。 请参阅 [将 URI 传递给 Windows 运行时](passing-a-uri-to-the-windows-runtime.md)。

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>开发的 Windows 运行时组件的方案

托管 Windows 运行时组件支持的方案取决于以下一般原则：

- Windows 运行时使用 .NET Framework 生成的组件与其他 Windows Runtimelibraries 没有明显的区别。 例如，如果使用托管代码重新实现本机 Windows 运行时组件，则这两个组件表面不区分。 在托管代码中编写的组件对使用它的代码来说是不可见的，即使该代码本身是托管代码。 但是，在内部，组件是真正的托管代码并运行在公共语言运行时 (CLR) 上。

- 组件可以包含实现应用程序逻辑、Windows 8.x 存储 UI 控件或二者的类型。

  > [!NOTE]
  > 最好将 UI 元素与应用程序逻辑分离开来。 此外，在使用 JavaScript 和 HTML 为 Windows 构建的 Windows 8.x 应用商店应用中，不能使用 Windows 8.x 应用商店 UI 控件。

- 组件可以是适用于 Windows 8.x 应用商店应用程序的 Visual Studio 解决方案中的项目，也可以是可添加到多个解决方案中的可重用组件。

  > [!NOTE]
  > 如果你的组件将仅与 c # 或 Visual Basic 一起使用，则没有理由使其成为 Windows 运行时组件。 如果改为使用普通 .NET Framework 类库，则无需将其公共 API 图面限制为 Windows 运行时类型。

- 您可以通过使用 Windows 运行时特性来释放可重用组件的版本 <xref:Windows.Foundation.Metadata.VersionAttribute> ，以确定 (哪些类型以及将类型) 中的哪些成员添加到不同版本。

- 组件中的类型可以派生自 Windows 运行时类型。 控件可从命名空间中的基元控件类型 <xref:Windows.UI.Xaml.Controls.Primitives> 或更多已完成的控件（如）派生 <xref:Windows.UI.Xaml.Controls.Button> 。

  > [!IMPORTANT]
  > 从 Windows 8 和 .NET Framework 4.5 开始，托管 Windows 运行时组件中的所有公共类型都必须是密封的。 其他 Windows 运行时组件中的类型不能从它们派生。 如果要在组件中提供多态行为，可以创建一个接口并在多态类型中实现它。

- 组件中所有公共类型的参数和返回类型都必须是 Windows 运行时类型 (包括组件定义) Windows 运行时类型。

以下部分提供常见方案的示例。

### <a name="application-logic-for-a-windows-8x-store-app-with-javascript"></a>使用 JavaScript 的 Windows 8.x 应用商店应用的应用程序逻辑

当你使用 JavaScript 开发适用于 Windows 的 Windows 8.x 应用商店应用时，你可能会发现应用程序逻辑的某些部分在托管代码中性能更佳或更易于开发。 JavaScript 不能直接使用 .NET Framework 类库，但是，您可以使将类库包装为 .WinMD 文件。 在此方案中，Windows 运行时组件是应用程序不可或缺的一部分，因此提供版本特性并无意义。

### <a name="reusable-windows-8x-store-ui-controls"></a>可重用的 Windows 8.x 应用商店 UI 控件

可以在可重用的 Windows 运行时组件中打包一组相关的 UI 控件。 该组件可以独立销售，或作为您创建的应用元素使用。 在此方案中，有必要使用 Windows 运行时 <xref:Windows.Foundation.Metadata.VersionAttribute> 特性来改善兼容性。

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>来自现有 .NET Framework 应用的可重用的应用程序逻辑

可以将现有的桌面应用程序中的托管代码作为独立的 Windows 运行时组件进行打包。 这使你可以使用 Windows 8.x 应用商店应用中使用 c + + 或 JavaScript 生成的组件，以及使用 c # 或 Visual Basic 生成的 Windows 8.x 应用商店应用。 如果代码有多个可重用的方案，可选择进行版本控制。

## <a name="related-topics"></a>相关主题

|Title|说明|
|-----------|-----------------|
|[适用于 Microsoft Store 应用的 .NET 概述](/previous-versions/windows/apps/br230302(v=vs.140))|描述可用于创建 Windows 8.x 应用商店应用和 Windows RuntimeComponents 的 .NET Framework 类型和成员。 （位于 Windows 开发中心。）|
|[使用 C# 或 Visual Basic 的 Windows 运行时应用的路线图](/previous-versions/windows/apps/br229583(v=win.10))|提供了一些关键资源来帮助你开始使用 c # 或 Visual Basic 开发 Windows 8.x 应用商店应用，包括许多快速入门主题、指导原则和最佳实践。 （位于 Windows 开发中心。）|
|[如何 (XAML) ](/previous-versions/windows/apps/br229566(v=win.10))|提供了一些关键资源来帮助你开始使用 c # 或 Visual Basic 开发 Windows 8.x 应用商店应用，包括许多快速入门主题、指导原则和最佳实践。 （位于 Windows 开发中心。）|
|[用 C# 和 Visual Basic 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|描述如何使用 .NET Framework 创建 Windows 运行时组件，并说明如何使用它作为使用 JavaScript 为 Windows 构建的 Windows 8.x 应用商店应用的一部分，并介绍如何使用 Visual Studio 调试此组合。 （位于 Windows 开发中心。）|
|[Windows 运行时参考](/uwp/api/)|Windows 运行时的参考文档。 （位于 Windows 开发中心。）|
|[向 Windows 运行时传递 URI](passing-a-uri-to-the-windows-runtime.md)|描述将 URI 从托管代码传递到 Windows 运行时时可能出现的问题，以及如何避免此问题。|
