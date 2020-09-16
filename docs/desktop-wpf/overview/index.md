---
title: Windows Presentation Foundation 简介
description: 本文概述了与 .NET Core 相关的 Windows Presentation Foundation (WPF) 是什么以及它提供了哪些功能。
ms.date: 07/18/2019
ms.topic: overview
ms.openlocfilehash: 37443b692ba840da847b2a21c3220f2c36025c12
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551862"
---
# <a name="what-is-windows-presentation-foundation"></a><span data-ttu-id="d784b-103">Windows Presentation Foundation 简介</span><span class="sxs-lookup"><span data-stu-id="d784b-103">What is Windows Presentation Foundation</span></span>

<span data-ttu-id="d784b-104">欢迎使用 Windows Presentation Foundation (WPF) 桌面指南，WPF 是一个可创建适用于 Windows 的桌面客户端应用程序的 UI 框架。</span><span class="sxs-lookup"><span data-stu-id="d784b-104">Welcome to the Desktop Guide for Windows Presentation Foundation (WPF), a UI framework that creates desktop client applications for Windows.</span></span> <span data-ttu-id="d784b-105">WPF 开发平台支持广泛的应用程序开发功能，包括应用程序模型、控件、图形和数据绑定。</span><span class="sxs-lookup"><span data-stu-id="d784b-105">The WPF development platform supports a broad set of application development features, including an application model, controls, graphics, and data binding.</span></span> <span data-ttu-id="d784b-106">WPF 使用 Extensible Application Markup Language (XAML) 为应用程序编程提供声明性模型。</span><span class="sxs-lookup"><span data-stu-id="d784b-106">WPF uses Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="d784b-107">WPF 有两种实现：</span><span class="sxs-lookup"><span data-stu-id="d784b-107">There are two implementations of WPF:</span></span>

01. <span data-ttu-id="d784b-108">托管于 [GitHub](https://github.com/dotnet/wpf) 上的开放源代码实现。</span><span class="sxs-lookup"><span data-stu-id="d784b-108">The open-source implementation hosted on [GitHub](https://github.com/dotnet/wpf).</span></span> <span data-ttu-id="d784b-109">此版本在 .NET Core 3.0 上运行。</span><span class="sxs-lookup"><span data-stu-id="d784b-109">This version runs on .NET Core 3.0.</span></span> <span data-ttu-id="d784b-110">适用于 XAML 的 WPF 视觉对象设计器最低要求 [Visual Studio 2019 版本 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+desktopguide)。</span><span class="sxs-lookup"><span data-stu-id="d784b-110">The WPF Visual Designer for XAML requires, at a minimum, [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+desktopguide).</span></span>

01. <span data-ttu-id="d784b-111">受 Visual Studio 2019 和 Visual Studio 2017 支持的 .NET Framework 实现。</span><span class="sxs-lookup"><span data-stu-id="d784b-111">The .NET Framework implementation that's supported by Visual Studio 2019 and Visual Studio 2017.</span></span>

<span data-ttu-id="d784b-112">本桌面指南适用于 .NET Core 3.0 和 WPF。</span><span class="sxs-lookup"><span data-stu-id="d784b-112">This Desktop Guide is written for .NET Core 3.0 and WPF.</span></span> <span data-ttu-id="d784b-113">如需详细了解使用 .NET Framework 的 WPF 的现有文档，请参阅 [Framework Windows Presentation Foundation](/dotnet/desktop/wpf/)。</span><span class="sxs-lookup"><span data-stu-id="d784b-113">For more information about the existing documentation for WPF with the .NET Framework, see [Framework Windows Presentation Foundation](/dotnet/desktop/wpf/).</span></span>

## <a name="xaml"></a><span data-ttu-id="d784b-114">XAML</span><span class="sxs-lookup"><span data-stu-id="d784b-114">XAML</span></span>

<span data-ttu-id="d784b-115">XAML 是一种基于 XML 的声明语言，WPF 使用它来定义资源或 UI 元素等内容。</span><span class="sxs-lookup"><span data-stu-id="d784b-115">XAML is a declarative XML-based language that WPF uses for things such as defining resources or UI elements.</span></span> <span data-ttu-id="d784b-116">XAML 中定义的元素表示程序集中对象的实例化。</span><span class="sxs-lookup"><span data-stu-id="d784b-116">Elements defined in XAML represent the instantiation of objects from an assembly.</span></span> <span data-ttu-id="d784b-117">XAML 与大多数其他标记语言不同，后者在运行时进行解释，且与后备类型系统无直接关系。</span><span class="sxs-lookup"><span data-stu-id="d784b-117">XAML is unlike most other markup languages, which are interpreted at runtime without a direct tie to a backing type system.</span></span>

<span data-ttu-id="d784b-118">以下示例演示如何创建 UI 中的按钮。</span><span class="sxs-lookup"><span data-stu-id="d784b-118">The following example shows how you would create a button as part of a UI.</span></span> <span data-ttu-id="d784b-119">此示例旨在让你了解 XAML 如何表示对象，其中 `Button` 是类型，`Content` 是属性。</span><span class="sxs-lookup"><span data-stu-id="d784b-119">This example is intended to give you an idea of how XAML represents an object, where `Button` is the type and `Content` is a property.</span></span>

```xaml
<StackPanel>
    <Button Content="Click Me!" />
</StackPanel>
```

<!--For more information, see [XAML overview (WPF)](../../../framework/wpf/advanced/xaml-overview-wpf.md).-->

### <a name="xaml-extensions"></a><span data-ttu-id="d784b-120">XAML 扩展</span><span class="sxs-lookup"><span data-stu-id="d784b-120">XAML extensions</span></span>

<span data-ttu-id="d784b-121">XAML 为标记扩展提供了语法。</span><span class="sxs-lookup"><span data-stu-id="d784b-121">XAML provides syntax for markup extensions.</span></span> <span data-ttu-id="d784b-122">标记扩展可用于以特性形式、属性元素形式或同时采用这两种形式来提供属性的值。</span><span class="sxs-lookup"><span data-stu-id="d784b-122">Markup extensions can be used to provide values for properties in attribute form, property-element form, or both.</span></span>

<span data-ttu-id="d784b-123">例如，上述 XAML 代码定义了一个按钮，其中可见内容设置为文本字符串 `"Click Me!"`，但该内容可以改由受支持的标记扩展进行设置。</span><span class="sxs-lookup"><span data-stu-id="d784b-123">For example, the previous XAML code defined a button with the visible content set to the literal string `"Click Me!"`, but the content can be instead set by a supported markup extension.</span></span> <span data-ttu-id="d784b-124">标记扩展是通过一对大括号 (`{ }`) 来定义的。</span><span class="sxs-lookup"><span data-stu-id="d784b-124">A markup extension is defined with opening and closing curly braces `{ }`.</span></span> <span data-ttu-id="d784b-125">然后，由紧跟在左大括号后面的字符串标记来标识标记扩展的类型。</span><span class="sxs-lookup"><span data-stu-id="d784b-125">The type of markup extension is then identified by the string token immediately following the opening curly brace.</span></span>

```xaml
<StackPanel>
    <Button Content="{MarkupType}" />
</StackPanel>
```

<span data-ttu-id="d784b-126">WPF 为 XAML 提供了不同的标记扩展，例如用于数据绑定的 `{Binding}`。</span><span class="sxs-lookup"><span data-stu-id="d784b-126">WPF provides different markup extensions for XAML such as `{Binding}` for data binding.</span></span>

<span data-ttu-id="d784b-127">有关详细信息，请参阅[标记扩展和 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)。</span><span class="sxs-lookup"><span data-stu-id="d784b-127">For more information, see [Markup Extensions and WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml).</span></span>

## <a name="property-system"></a><span data-ttu-id="d784b-128">属性系统</span><span class="sxs-lookup"><span data-stu-id="d784b-128">Property system</span></span>

<span data-ttu-id="d784b-129">WPF 提供一组服务，这些服务可用于扩展类型的[属性](../../standard/base-types/common-type-system.md#properties)的功能。</span><span class="sxs-lookup"><span data-stu-id="d784b-129">WPF provides a set of services that can be used to extend the functionality of a type's [property](../../standard/base-types/common-type-system.md#properties).</span></span> <span data-ttu-id="d784b-130">这些服务统称为 WPF 属性系统。</span><span class="sxs-lookup"><span data-stu-id="d784b-130">Collectively, these services are referred to as the *WPF property system*.</span></span> <span data-ttu-id="d784b-131">由 WPF 属性系统支持的属性称为依赖属性。</span><span class="sxs-lookup"><span data-stu-id="d784b-131">A property that is backed by the WPF property system is known as a dependency property.</span></span>

<span data-ttu-id="d784b-132">依赖属性通过提供支持属性的 <xref:System.Windows.DependencyProperty> 类型来扩展属性功能。</span><span class="sxs-lookup"><span data-stu-id="d784b-132">Dependency properties extend property functionality by providing the <xref:System.Windows.DependencyProperty> type that backs a property.</span></span> <span data-ttu-id="d784b-133">依赖项属性类型是使用专用字段支持属性的标准模式的替代实现。</span><span class="sxs-lookup"><span data-stu-id="d784b-133">The dependency property type is an alternative implementation of the standard pattern of backing the property with a private field.</span></span>

### <a name="dependency-property"></a><span data-ttu-id="d784b-134">依赖属性</span><span class="sxs-lookup"><span data-stu-id="d784b-134">Dependency property</span></span>

<span data-ttu-id="d784b-135">在 WPF 中，依赖属性通常公开为标准 .NET [属性](../../standard/base-types/common-type-system.md#properties)。</span><span class="sxs-lookup"><span data-stu-id="d784b-135">In WPF, dependency properties are typically exposed as standard .NET [properties](../../standard/base-types/common-type-system.md#properties).</span></span> <span data-ttu-id="d784b-136">在基本级别，可以直接与这些属性交互，而不必了解它们是以依赖属性的形式实现的。</span><span class="sxs-lookup"><span data-stu-id="d784b-136">At a basic level, you could interact with these properties directly and never know that they're implemented as a dependency property.</span></span>

<span data-ttu-id="d784b-137">依赖属性的用途在于提供一种方法来基于其他输入的值计算属性值。</span><span class="sxs-lookup"><span data-stu-id="d784b-137">The purpose of dependency properties is to provide a way to compute the value of a property based on the value of other inputs.</span></span> <span data-ttu-id="d784b-138">这些其他输入可能包括系统属性（如主题和用户首选项）或者来自数据绑定和动画的实时属性。</span><span class="sxs-lookup"><span data-stu-id="d784b-138">These other inputs might include system properties such as themes and user preferences, or just-in-time property from data binding and animations.</span></span>

<span data-ttu-id="d784b-139">可以实现依赖属性来提供验证、默认值以及监视对其他属性的更改的回调。</span><span class="sxs-lookup"><span data-stu-id="d784b-139">A dependency property can be implemented to provide validation, default values, and callbacks that monitor changes to other properties.</span></span> <span data-ttu-id="d784b-140">派生类还可以通过重写依赖属性元数据（而不是新建属性或重写现有属性）来更改现有属性的某些具体特征。</span><span class="sxs-lookup"><span data-stu-id="d784b-140">Derived classes can also change some specific characteristics of an existing property by overriding dependency property metadata, rather than creating a new property or overriding an existing property.</span></span>

### <a name="dependency-object"></a><span data-ttu-id="d784b-141">依赖对象</span><span class="sxs-lookup"><span data-stu-id="d784b-141">Dependency object</span></span>

<span data-ttu-id="d784b-142">WPF 属性系统的另一个重要类型是 <xref:System.Windows.DependencyObject>。</span><span class="sxs-lookup"><span data-stu-id="d784b-142">Another type that is key to the WPF property system is the <xref:System.Windows.DependencyObject>.</span></span> <span data-ttu-id="d784b-143">此类型定义可以注册和拥有依赖属性的基类。</span><span class="sxs-lookup"><span data-stu-id="d784b-143">This type defines the base class that can register and own a dependency property.</span></span> <span data-ttu-id="d784b-144"><xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> 方法为依赖对象实例提供了依赖属性的支持实现。</span><span class="sxs-lookup"><span data-stu-id="d784b-144">The <xref:System.Windows.DependencyObject.GetValue%2A> and <xref:System.Windows.DependencyObject.SetValue%2A> methods provide the backing implementation of the dependency property for the dependency object instance.</span></span>

<span data-ttu-id="d784b-145">以下示例演示的依赖对象定义一个名为 `ValueProperty` 的单一依赖属性标识符。</span><span class="sxs-lookup"><span data-stu-id="d784b-145">The following example shows a dependency object that defines a single dependency property identifier named `ValueProperty`.</span></span> <span data-ttu-id="d784b-146">此依赖属性通过使用 `Value` .NET 属性创建而成。</span><span class="sxs-lookup"><span data-stu-id="d784b-146">The dependency property is created with the `Value` .NET property.</span></span>

```csharp
public class TextField: DependencyObject
{
    public static readonly DependencyProperty ValueProperty =
        DependencyProperty.Register("Value", typeof(string), typeof(TextField), new PropertyMetadata(""));

    public string Value
    {
        get { return (string)GetValue(ValueProperty); }
        set { SetValue(ValueProperty, value); }
    }
}
```

<span data-ttu-id="d784b-147">此依赖属性被定义为依赖对象类型的静态成员，例如上例中的 `TextField`。</span><span class="sxs-lookup"><span data-stu-id="d784b-147">The dependency property is defined as a static member of a dependency object type, such as `TextField` in example above.</span></span> <span data-ttu-id="d784b-148">此依赖属性必须通过依赖对象注册。</span><span class="sxs-lookup"><span data-stu-id="d784b-148">The dependency property must be registered with the dependency object.</span></span>

<span data-ttu-id="d784b-149">上例中的 `Value` 属性包装此依赖属性，从而提供了你可能较为熟悉的标准 .NET 属性模式。</span><span class="sxs-lookup"><span data-stu-id="d784b-149">The `Value` property in the example above wraps the dependency property, providing the standard .NET property pattern you're probably used to.</span></span>

<!--For more information, see [Dependency properties overview](../../../framework/wpf/advanced/dependency-properties-overview.md).-->

## <a name="events"></a><span data-ttu-id="d784b-150">事件</span><span class="sxs-lookup"><span data-stu-id="d784b-150">Events</span></span>

<span data-ttu-id="d784b-151">WPF 提供了一个位于熟悉的 .NET 公共语言运行时 (CLR) 事件之上的事件系统。</span><span class="sxs-lookup"><span data-stu-id="d784b-151">WPF provides an eventing system that is layered on top of the .NET common language runtime (CLR) events you're familiar with.</span></span> <span data-ttu-id="d784b-152">这些 WPF 事件称为路由事件。</span><span class="sxs-lookup"><span data-stu-id="d784b-152">These WPF events are called routed events.</span></span>

<span data-ttu-id="d784b-153">路由事件是一个 CLR 事件，它由 `RoutedEvent` 类的实例提供支持并向 WPF 事件系统注册。</span><span class="sxs-lookup"><span data-stu-id="d784b-153">A routed event is a CLR event that is backed by an instance of the `RoutedEvent` class and registered with the WPF event system.</span></span> <span data-ttu-id="d784b-154">从事件注册中获取的 `RoutedEvent` 实例通常保留为特定类的 `public static readonly` 字段成员，该类注册路由事件并因此“拥有”路由事件。</span><span class="sxs-lookup"><span data-stu-id="d784b-154">The `RoutedEvent` instance obtained from event registration is typically retained as a `public static readonly` field member of the class that registers, and thus *owns* the routed event.</span></span> <span data-ttu-id="d784b-155">与同名 CLR 事件（有时称为“包装器”事件）的连接是通过替代 CLR 事件的 `add` 和 `remove` 实现来完成的。</span><span class="sxs-lookup"><span data-stu-id="d784b-155">The connection to the identically named CLR event (which is sometimes termed the *wrapper* event) is accomplished by overriding the `add` and `remove` implementations for the CLR event.</span></span> <span data-ttu-id="d784b-156">路由事件的支持和连接机制在概念上与以下机制相似：[依赖属性](#dependency-property)是一个 CLR 属性，该属性由 `DependencyProperty` 类提供支持并向 WPF 属性系统注册。</span><span class="sxs-lookup"><span data-stu-id="d784b-156">The routed event backing and connection mechanism is conceptually similar to how a [dependency property](#dependency-property) is a CLR property that is backed by the `DependencyProperty` class and registered with the WPF property system.</span></span>

<span data-ttu-id="d784b-157">路由事件系统的主要优点是，这类事件会上升到控制元素树上来查找处理程序。</span><span class="sxs-lookup"><span data-stu-id="d784b-157">The main advantage of the routed event system is that events are *bubbled up* the control element tree looking for a handler.</span></span> <span data-ttu-id="d784b-158">例如，由于 WPF 具有丰富的内容模型，你可以将图像控件设置为按钮控件的内容。</span><span class="sxs-lookup"><span data-stu-id="d784b-158">For example, because WPF has a rich content model, you set an image control as the content of a button control.</span></span> <span data-ttu-id="d784b-159">在图像控件上单击鼠标时，你可能期望它使用鼠标事件，从而中断导致按钮调用 `Click` 事件的命中测试。</span><span class="sxs-lookup"><span data-stu-id="d784b-159">When the mouse is clicked on the image control, you would expect it to consume the mouse events, and thus break the hit-tests that cause a button to invoke the `Click` event.</span></span> <span data-ttu-id="d784b-160">在传统 CLR 事件模型中，你需要通过向图像和按钮附加相同的处理程序来规避此限制。</span><span class="sxs-lookup"><span data-stu-id="d784b-160">In a traditional CLR eventing model, you would work around this limitation by attaching the same handler to both the image and the button.</span></span> <span data-ttu-id="d784b-161">但是，通过路由事件，在图像控件上调用的鼠标事件（例如选择它）会上升到父级按钮控件。</span><span class="sxs-lookup"><span data-stu-id="d784b-161">But with the routed event system, the mouse events invoked on the image control (such as selecting it) bubble up to the parent button control.</span></span>

<!--For more information, including other types of event models, see [Events overview](../../../framework/wpf/advanced/routed-events-overview.md).-->

## <a name="data-binding"></a><span data-ttu-id="d784b-162">数据绑定</span><span class="sxs-lookup"><span data-stu-id="d784b-162">Data binding</span></span>

<span data-ttu-id="d784b-163">WPF 数据绑定为应用程序呈现数据并与数据交互提供了一种简单且一致的方式。</span><span class="sxs-lookup"><span data-stu-id="d784b-163">WPF data binding provides a simple and consistent way for applications to present and interact with data.</span></span> <span data-ttu-id="d784b-164">元素能够以公共语言运行时 (CLR) 对象和 XML 的形式，绑定到不同类型数据源中的数据。</span><span class="sxs-lookup"><span data-stu-id="d784b-164">Elements can be bound to data from different types of data sources in the form of common language runtime (CLR) objects and XML.</span></span> <span data-ttu-id="d784b-165">WPF 还提供了通过拖放操作传输数据的机制。</span><span class="sxs-lookup"><span data-stu-id="d784b-165">WPF also provides a mechanism for the transfer of data through drag-and-drop operations.</span></span>

<span data-ttu-id="d784b-166">数据绑定是在应用程序 UI 和业务逻辑之间建立连接的过程。</span><span class="sxs-lookup"><span data-stu-id="d784b-166">Data binding is the process that establishes a connection between the application UI and business logic.</span></span> <span data-ttu-id="d784b-167">如果绑定具有正确的设置，并且数据提供适当的通知，则在数据更改其值时，绑定到该数据的元素会自动反映更改。</span><span class="sxs-lookup"><span data-stu-id="d784b-167">If the binding has the correct settings and the data provides the proper notifications, then, when the data changes its value, the elements that bound to the data reflect changes automatically.</span></span> <span data-ttu-id="d784b-168">数据绑定还意味着，如果元素中数据的外部表示形式发生更改，则基础数据会自动进行更新以反映更改。</span><span class="sxs-lookup"><span data-stu-id="d784b-168">Data binding can also mean that if an outer representation of the data in an element changes, then the underlying data is automatically updated to reflect the change.</span></span> <span data-ttu-id="d784b-169">例如，如果用户编辑 TextBox 元素中的值，则基础数据值会自动更新以反映该更改。</span><span class="sxs-lookup"><span data-stu-id="d784b-169">For example, if the user edits the value in a TextBox element, the underlying data value is automatically updated to reflect that change.</span></span>

<span data-ttu-id="d784b-170">数据绑定可以通过 `{Binding}` 标记扩展以 XAML 配置。</span><span class="sxs-lookup"><span data-stu-id="d784b-170">Data binding can be configured in XAML through the `{Binding}` markup extension.</span></span> <span data-ttu-id="d784b-171">以下示例演示绑定到数据对象的 `ButtonText` 属性。</span><span class="sxs-lookup"><span data-stu-id="d784b-171">The following example demonstrates binding to a data object's `ButtonText` property.</span></span> <span data-ttu-id="d784b-172">如果绑定失败，则会使用 `Click Me!` 的值。</span><span class="sxs-lookup"><span data-stu-id="d784b-172">If that binding fails, the value of `Click Me!` is used.</span></span>

```xaml
<StackPanel>
    <Button Content="{Binding ButtonText, FallbackValue='Click Me!'}" />
</StackPanel>
```

<span data-ttu-id="d784b-173">有关详细信息，请参阅[数据绑定概述](../data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d784b-173">For more information, see [Data binding overview](../data/data-binding-overview.md).</span></span>

## <a name="ui-components"></a><span data-ttu-id="d784b-174">UI 组件</span><span class="sxs-lookup"><span data-stu-id="d784b-174">UI components</span></span>

<span data-ttu-id="d784b-175">WPF 提供许多几乎在所有 Windows 应用程序中都会使用的常见 UI 组件，如`Button`、`Label`、`TextBox`、`Menu` 和 `ListBox`。</span><span class="sxs-lookup"><span data-stu-id="d784b-175">WPF provides many of the common UI components that are used in almost every Windows application, such as `Button`, `Label`, `TextBox`, `Menu`, and `ListBox`.</span></span> <span data-ttu-id="d784b-176">以前，这些对象称为控件。</span><span class="sxs-lookup"><span data-stu-id="d784b-176">Historically, these objects have been referred to as controls.</span></span> <span data-ttu-id="d784b-177">虽然 WPF SDK 继续使用术语“控件”泛指任何代表应用程序中可见对象的类，但请务必注意，类不必从 `Control` 类继承即可具有可见外观。</span><span class="sxs-lookup"><span data-stu-id="d784b-177">While the WPF SDK continues to use the term control to loosely mean any class that represents a visible object in an application, it's important to note that a class doesn't need to inherit from the `Control` class to have a visible presence.</span></span> <span data-ttu-id="d784b-178">从 `Control` 类继承的类包含一个 `ControlTemplate`，它允许控件的使用方在无需创建新子类的情况下从根本上改变控件的外观。</span><span class="sxs-lookup"><span data-stu-id="d784b-178">Classes that inherit from the `Control` class contain a `ControlTemplate`, which allows the consumer of a control to radically change the control's appearance without having to create a new subclass.</span></span>

## <a name="styles-and-templates"></a><span data-ttu-id="d784b-179">样式和模板</span><span class="sxs-lookup"><span data-stu-id="d784b-179">Styles and templates</span></span>

<span data-ttu-id="d784b-180">WPF 样式设置和模板化是指一套功能（样式、模板、触发器和情节提要），可使应用程序、文档和 UI 设计者创建极具视觉表现力的应用程序，并为其产品创建标准化的特定外观。</span><span class="sxs-lookup"><span data-stu-id="d784b-180">WPF styling and templating refer to a suite of features (styles, templates, triggers, and storyboards) that allow an application, document, or UI designer to create visually compelling applications and to standardize on a particular look for their product.</span></span>

<span data-ttu-id="d784b-181">WPF 样式模型的另一个功能是呈现内容和逻辑的分离，这意味着，设计人员可以使用 XAML 来处理应用程序的外观，而开发人员可以在其他位置处理编程逻辑。</span><span class="sxs-lookup"><span data-stu-id="d784b-181">Another feature of the WPF styling model is the separation of presentation and logic, which means designers can work on the appearance of an application with XAML while developers work on the programming logic elsewhere.</span></span>

<span data-ttu-id="d784b-182">此外，了解资源很重要，正是这些资源使样式和模板能够重复使用。</span><span class="sxs-lookup"><span data-stu-id="d784b-182">In addition, it's important to understand resources, which are what enable styles and templates to be reused.</span></span>

<span data-ttu-id="d784b-183">有关详细信息，请参阅[样式和模板](../fundamentals/styles-templates-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d784b-183">For more information, see [Styles and templates](../fundamentals/styles-templates-overview.md).</span></span>

## <a name="resources"></a><span data-ttu-id="d784b-184">资源</span><span class="sxs-lookup"><span data-stu-id="d784b-184">Resources</span></span>

<span data-ttu-id="d784b-185">WPF 资源是可以在应用程序中的不同位置重复使用的对象。</span><span class="sxs-lookup"><span data-stu-id="d784b-185">WPF resources are objects that can be reused in different places in your application.</span></span> <span data-ttu-id="d784b-186">资源示例包括样式、模板和颜色画笔。</span><span class="sxs-lookup"><span data-stu-id="d784b-186">Examples of resources include styles, templates, and color brushes.</span></span> <span data-ttu-id="d784b-187">可以采用代码和 XAML 格式定义和引用资源。</span><span class="sxs-lookup"><span data-stu-id="d784b-187">Resources can be both defined and referenced in code and in XAML format.</span></span>

<span data-ttu-id="d784b-188">每个框架级别元素（<xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>）都具有 `Resources` 属性，该属性是包含已定义资源的 <xref:System.Windows.ResourceDictionary> 类型。</span><span class="sxs-lookup"><span data-stu-id="d784b-188">Every framework-level element (<xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>) has a `Resources` property (which is a <xref:System.Windows.ResourceDictionary> type) that contains defined resources.</span></span> <span data-ttu-id="d784b-189">由于所有元素都继承自框架级别元素，因此所有元素都可以定义资源。</span><span class="sxs-lookup"><span data-stu-id="d784b-189">Since all elements inherit from a framework-level element, all elements can define resources.</span></span> <span data-ttu-id="d784b-190">但是，最常见的做法是在 XAML 文档的根元素上定义资源。</span><span class="sxs-lookup"><span data-stu-id="d784b-190">It's most common, however, to define resources on a root element of a XAML document.</span></span>

<!--For more information, see [XAML Resources](../../../framework/wpf/advanced/xaml-resources.md).-->

## <a name="next-steps"></a><span data-ttu-id="d784b-191">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d784b-191">Next steps</span></span>

- <span data-ttu-id="d784b-192">[创建 WPF 应用程序](/visualstudio/get-started/csharp/tutorial-wpf?bc=%252fdotnet%252fbreadcrumb%252ftoc.json&toc=%252fdotnet%252fdesktop-wpf%252ftoc.json)。</span><span class="sxs-lookup"><span data-stu-id="d784b-192">[Create a WPF application.](/visualstudio/get-started/csharp/tutorial-wpf?bc=%252fdotnet%252fbreadcrumb%252ftoc.json&toc=%252fdotnet%252fdesktop-wpf%252ftoc.json)</span></span>
- <span data-ttu-id="d784b-193">[探索与 .NET Framework 的差异](../migration/differences-from-net-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="d784b-193">[Explore the differences from .NET Framework.](../migration/differences-from-net-framework.md)</span></span>
- <span data-ttu-id="d784b-194">[了解 XAML](../fundamentals/xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="d784b-194">[Learn about XAML.](../fundamentals/xaml.md)</span></span>
