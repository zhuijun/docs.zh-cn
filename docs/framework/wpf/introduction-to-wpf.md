---
title: WPF 介绍
titleSuffix: ''
description: 在 Windows 中创建视觉效果非凡的用户体验。 了解 Windows Presentation Foundation （WPF）的主要功能和概念。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7a79174f5f3aebe90190db45566b37bd5e9fbe3f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853581"
---
# <a name="wpf-overview"></a><span data-ttu-id="9f4e6-104">WPF 概述</span><span class="sxs-lookup"><span data-stu-id="9f4e6-104">WPF overview</span></span>

<span data-ttu-id="9f4e6-105">使用 Windows Presentation Foundation (WPF)，你可以创建适用于 Windows 且具有非凡视觉效果的桌面客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-105">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Contoso Healthcare UI 示例](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="9f4e6-107">WPF 的核心是一个与分辨率无关且基于矢量的呈现引擎，旨在充分利用现代图形硬件。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-107">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="9f4e6-108">WPF 通过一套完善的应用程序开发功能对该核心进行了扩展，这些功能包括可扩展应用程序标记语言 (XAML)、控件、数据绑定、布局、二维和三维图形、动画、样式、模板、文档、媒体、文本和版式。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-108">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="9f4e6-109">WPF 属于 .NET，因此可以生成整合 .NET API 其他元素的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-109">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="9f4e6-110">本概述适用于新用户，介绍了 WPF 的主要功能和概念。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-110">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="9f4e6-111">使用 WPF 进行编程</span><span class="sxs-lookup"><span data-stu-id="9f4e6-111">Program with WPF</span></span>

<span data-ttu-id="9f4e6-112">WPF 作为大部分位于 <xref:System.Windows> 命名空间中的 .NET 类型的一个子集存在。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-112">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="9f4e6-113">如果你之前使用托管技术（如 ASP.NET 和 Windows 窗体）通过 .NET 生成过应用程序，则不会对基本的 WPF 编程体验感到陌生；你可以使用最喜欢的 .NET 编程语言（如 C# 或 Visual Basic）来完成实例化类、设置属性、调用方法以及处理事件等操作。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-113">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="9f4e6-114">WPF 还包括增强属性和事件的其他编程构造： [依赖项属性](advanced/dependency-properties-overview.md) 和 [路由事件](advanced/routed-events-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-114">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="9f4e6-115">标记和代码隐藏</span><span class="sxs-lookup"><span data-stu-id="9f4e6-115">Markup and code-behind</span></span>

<span data-ttu-id="9f4e6-116">通过 WPF，可以使用标记和代码隐藏开发应用程序，这是 ASP.NET 开发人员已经熟悉的体验\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-116">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="9f4e6-117">通常使用 XAML 标记实现应用程序的外观，同时使用托管编程语言（代码隐藏）来实现其行为。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-117">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="9f4e6-118">这种外观和行为的分离具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-118">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="9f4e6-119">降低了开发和维护成本，因为特定于外观的标记与特定于行为的代码不紧密耦合。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-119">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="9f4e6-120">开发效率更高，因为设计人员在实现应用程序外观的同时，开发人员可以实现应用程序的行为。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-120">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="9f4e6-121">WPF 应用程序的[全球化和本地化](advanced/wpf-globalization-and-localization-overview.md) 得以简化。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-121">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="9f4e6-122">标记</span><span class="sxs-lookup"><span data-stu-id="9f4e6-122">Markup</span></span>

<span data-ttu-id="9f4e6-123">XAML 是一种基于 XML 的标记语言，以声明形式实现应用程序的外观。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-123">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="9f4e6-124">通常用它创建窗口、对话框、页和用户控件，并填充控件、形状和图形。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-124">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="9f4e6-125">下面的示例使用 XAML 来实现包含一个按钮的窗口的外观：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-125">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="9f4e6-126">具体而言，此 XAML 通过分别使用 `Window` 和 `Button` 元素来定义窗口和按钮。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-126">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="9f4e6-127">每个元素均配置了特性（如 `Window` 元素的 `Title` 特性）来指定窗口的标题栏文本。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-127">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="9f4e6-128">在运行时，WPF 会将标记中定义的元素和特性转换为 WPF 类的实例。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-128">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="9f4e6-129">例如， `Window` 元素被转换为 <xref:System.Windows.Window> 类的实例，该类的 <xref:System.Windows.Window.Title%2A> 属性是 `Title` 特性的值。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-129">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="9f4e6-130">下图显示了上一示例中的 XAML 定义的用户界面（UI）：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-130">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![包含按钮的窗口](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="9f4e6-132">由于 XAML 是基于 XML 的，因此使用它编写的 UI 汇集在嵌套元素的层次结构中，称为 [元素树](advanced/trees-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-132">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="9f4e6-133">元素树提供了一种直观的逻辑方式来创建和管理 UI。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-133">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="9f4e6-134">代码隐藏</span><span class="sxs-lookup"><span data-stu-id="9f4e6-134">Code-behind</span></span>

<span data-ttu-id="9f4e6-135">应用程序的主要行为是实现响应用户交互的功能，包括处理事件（例如，单击菜单、工具栏或按钮）以及相应地调用业务逻辑和数据访问逻辑。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-135">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="9f4e6-136">在 WPF 中，在与标记相关联的代码中实现此行为。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-136">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="9f4e6-137">此类代码称为代码隐藏。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-137">This type of code is known as code-behind.</span></span> <span data-ttu-id="9f4e6-138">下面的示例显示了上一示例中的更新标记和代码隐藏：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-138">The following example shows the updated markup from the previous example and the code-behind:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub

    End Class

End Namespace
```

<span data-ttu-id="9f4e6-139">在此示例中，代码隐藏实现派生自 <xref:System.Windows.Window> 类的类。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-139">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="9f4e6-140">`x:Class` 特性用于将标记与代码隐藏类相关联。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-140">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="9f4e6-141">从代码隐藏类的构造函数调用 `InitializeComponent`，以将标记中定义的 UI 与代码隐藏类合并在一起。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-141">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="9f4e6-142">（ `InitializeComponent` 生成应用程序时将为你生成，这就是不需要手动实现它的原因。）和的组合 `x:Class` `InitializeComponent` 可确保你的实现在创建时正确初始化。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-142">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="9f4e6-143">代码隐藏类还可实现按钮的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-143">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="9f4e6-144">单击该按钮后，事件处理程序会通过调用 <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> 方法显示一个消息框。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-144">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="9f4e6-145">下图显示了单击按钮时的结果：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-145">The following figure shows the result when the button is clicked:</span></span>

![消息框](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="9f4e6-147">控制</span><span class="sxs-lookup"><span data-stu-id="9f4e6-147">Controls</span></span>

<span data-ttu-id="9f4e6-148">应用程序模型带来的用户体验是构造的控件。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-148">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="9f4e6-149">在 WPF 中，*控件*是一个涵盖性术语，适用于在窗口或页中承载的 WPF 类的类别、具有用户界面并实现某些行为。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-149">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="9f4e6-150">有关详细信息，请参阅[控件](controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-150">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="9f4e6-151">按功能分类的 WPF 控件</span><span class="sxs-lookup"><span data-stu-id="9f4e6-151">WPF controls by function</span></span>

<span data-ttu-id="9f4e6-152">下面列出了内置的 WPF 控件：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-152">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="9f4e6-153">**按钮**： <xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Controls.Primitives.RepeatButton> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-153">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="9f4e6-154">**数据显示**： <xref:System.Windows.Controls.DataGrid> 、 <xref:System.Windows.Controls.ListView> 和 <xref:System.Windows.Controls.TreeView> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-154">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="9f4e6-155">**日期显示和选择**： <xref:System.Windows.Controls.Calendar> 和 <xref:System.Windows.Controls.DatePicker> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-155">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="9f4e6-156">**对话框**： <xref:Microsoft.Win32.OpenFileDialog> 、 <xref:System.Windows.Controls.PrintDialog> 和 <xref:Microsoft.Win32.SaveFileDialog> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-156">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="9f4e6-157">**数字墨迹**： <xref:System.Windows.Controls.InkCanvas> 和 <xref:System.Windows.Controls.InkPresenter> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-157">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="9f4e6-158">**文档**： <xref:System.Windows.Controls.DocumentViewer> 、 <xref:System.Windows.Controls.FlowDocumentPageViewer> 、 <xref:System.Windows.Controls.FlowDocumentReader> 、 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 和 <xref:System.Windows.Controls.StickyNoteControl> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-158">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="9f4e6-159">**输入**： <xref:System.Windows.Controls.TextBox> 、 <xref:System.Windows.Controls.RichTextBox> 和 <xref:System.Windows.Controls.PasswordBox> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-159">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="9f4e6-160">**布局**： <xref:System.Windows.Controls.Border> 、 <xref:System.Windows.Controls.Primitives.BulletDecorator> 、 <xref:System.Windows.Controls.Canvas> 、 <xref:System.Windows.Controls.DockPanel> 、 <xref:System.Windows.Controls.Expander> 、 <xref:System.Windows.Controls.Grid> 、 <xref:System.Windows.Controls.GridView> 、 <xref:System.Windows.Controls.GridSplitter> <xref:System.Windows.Controls.GroupBox> <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Primitives.ResizeGrip> <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.Primitives.ScrollBar> <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.Primitives.Thumb> <xref:System.Windows.Controls.Viewbox> <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Window> 、、、、 <xref:System.Windows.Controls.WrapPanel> 、、、、、、、和。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-160">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="9f4e6-161">**媒体**： <xref:System.Windows.Controls.Image> 、 <xref:System.Windows.Controls.MediaElement> 和 <xref:System.Windows.Controls.SoundPlayerAction> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-161">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="9f4e6-162">**菜单**： <xref:System.Windows.Controls.ContextMenu> 、 <xref:System.Windows.Controls.Menu> 和 <xref:System.Windows.Controls.ToolBar> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-162">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="9f4e6-163">**导航**： <xref:System.Windows.Controls.Frame> 、 <xref:System.Windows.Documents.Hyperlink> 、 <xref:System.Windows.Controls.Page> 、 <xref:System.Windows.Navigation.NavigationWindow> 和 <xref:System.Windows.Controls.TabControl> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-163">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="9f4e6-164">**选项**： <xref:System.Windows.Controls.CheckBox> 、 <xref:System.Windows.Controls.ComboBox> 、 <xref:System.Windows.Controls.ListBox> 、 <xref:System.Windows.Controls.RadioButton> 和 <xref:System.Windows.Controls.Slider> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-164">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="9f4e6-165">**用户信息**： <xref:System.Windows.Controls.AccessText> 、 <xref:System.Windows.Controls.Label> 、 <xref:System.Windows.Controls.Primitives.Popup> 、 <xref:System.Windows.Controls.ProgressBar> 、 <xref:System.Windows.Controls.Primitives.StatusBar> 、 <xref:System.Windows.Controls.TextBlock> 和 <xref:System.Windows.Controls.ToolTip> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-165">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="9f4e6-166">输入和命令</span><span class="sxs-lookup"><span data-stu-id="9f4e6-166">Input and commands</span></span>

<span data-ttu-id="9f4e6-167">最常检测和响应用户输入的控件。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-167">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="9f4e6-168">[WPF 输入系统](advanced/input-overview.md) 使用直接事件和路由事件来支持文本输入、焦点管理和鼠标定位。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-168">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="9f4e6-169">应用程序通常具有复杂的输入要求。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-169">Applications often have complex input requirements.</span></span> <span data-ttu-id="9f4e6-170">WPF 提供了[命令系统](advanced/commanding-overview.md)，用于将用户输入操作与对这些操作做出响应的代码分隔开来。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-170">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="9f4e6-171">布局</span><span class="sxs-lookup"><span data-stu-id="9f4e6-171">Layout</span></span>

<span data-ttu-id="9f4e6-172">创建用户界面时，按照位置和大小排列控件以形成布局。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-172">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="9f4e6-173">任何布局的一项关键要求都是适应窗口大小和显示设置的变化。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-173">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="9f4e6-174">WPF 为你提供一流的可扩展布局系统，而不强制你编写代码以适应这些情况下的布局。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-174">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="9f4e6-175">布局系统的基础是相对定位，这提高了适应不断变化的窗口和显示条件的能力。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-175">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="9f4e6-176">此外，该布局系统还可管理控件之间的协商以确定布局。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-176">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="9f4e6-177">协商是一个两步过程：首先，控件将需要的位置和大小告知父级；其次，父级将控件可以有的空间告知控件。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-177">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="9f4e6-178">该布局系统通过基 WPF 类公开给子控件。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-178">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="9f4e6-179">对于通用的布局（如网格、堆叠和停靠），WPF 包括若干布局控件：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-179">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="9f4e6-180"><xref:System.Windows.Controls.Canvas>：子控件提供其自己的布局。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-180"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="9f4e6-181"><xref:System.Windows.Controls.DockPanel>：子控件与面板的边缘对齐。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-181"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="9f4e6-182"><xref:System.Windows.Controls.Grid>：子控件由行和列定位。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-182"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="9f4e6-183"><xref:System.Windows.Controls.StackPanel>：子控件垂直或水平堆叠。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-183"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="9f4e6-184"><xref:System.Windows.Controls.VirtualizingStackPanel>：子控件在水平或垂直的行上虚拟化并排列。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-184"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="9f4e6-185"><xref:System.Windows.Controls.WrapPanel>：子控件按从左到右的顺序定位，在当前行上的控件超出允许的空间时，换行到下一行。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-185"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="9f4e6-186">下面的示例使用 <xref:System.Windows.Controls.DockPanel> 来布局几个 <xref:System.Windows.Controls.TextBox> 控件：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-186">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="9f4e6-187"><xref:System.Windows.Controls.DockPanel> 允许子 <xref:System.Windows.Controls.TextBox> 控件，以告诉它如何排列这些控件。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-187">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="9f4e6-188">为了完成此操作，<xref:System.Windows.Controls.DockPanel> 实现 `Dock` 附加了属性，该属性公开给子控件，以允许每个子控件指定停靠样式。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-188">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="9f4e6-189">由父控件实现以便子控件使用的属性是 WPF 构造，称为[附加属性](advanced/attached-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-189">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="9f4e6-190">下图显示了前面示例中的 XAML 标记的结果：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-190">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![DockPanel 页](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="9f4e6-192">数据绑定</span><span class="sxs-lookup"><span data-stu-id="9f4e6-192">Data binding</span></span>

<span data-ttu-id="9f4e6-193">大多数应用程序旨在为用户提供查看和编辑数据的方法。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-193">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="9f4e6-194">对于 WPF 应用程序，已对存储和访问数据的工作提供技术（如 SQL Server 和 ADO.NET）。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-194">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="9f4e6-195">访问数据并将数据加载到应用程序的托管对象后，WPF 应用程序的复杂工作开始。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-195">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="9f4e6-196">从根本上来说，这涉及到两件事：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-196">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="9f4e6-197">将数据从托管对象复制到控件，在控件中可以显示和编辑数据。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-197">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="9f4e6-198">确保使用控件对数据所做的更改将复制回托管对象。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-198">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="9f4e6-199">为了简化应用程序开发，WPF 提供了一个数据绑定引擎来自动执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-199">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="9f4e6-200">数据绑定引擎的核心单元是 <xref:System.Windows.Data.Binding> 类，其工作是将控件（绑定目标）绑定到数据对象（绑定源）。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-200">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="9f4e6-201">下图阐释了这种关系：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-201">This relationship is illustrated by the following figure:</span></span>

![基本数据绑定示意图](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="9f4e6-203">下一示例演示如何将 <xref:System.Windows.Controls.TextBox> 绑定到自定义 `Person` 对象的实例。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-203">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="9f4e6-204">下面的代码演示了 `Person` 实现：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-204">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="9f4e6-205">下面的标记将绑定 <xref:System.Windows.Controls.TextBox> 到自定义对象的实例 `Person` ：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-205">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_6.cs)]

<span data-ttu-id="9f4e6-206">在此示例中， `Person` 类在代码隐藏中实例化并被设置为 `DataBindingWindow`的数据上下文。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-206">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="9f4e6-207">在标记中， <xref:System.Windows.Controls.TextBox.Text%2A> 的 <xref:System.Windows.Controls.TextBox> 属性被绑定至 `Person.Name` 属性（使用“`{Binding ... }`”XAML 语法）。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-207">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="9f4e6-208">此 XAML 告知 WPF 将 <xref:System.Windows.Controls.TextBox> 控件绑定至窗口的 `Person` 属性中存储的 <xref:System.Windows.FrameworkElement.DataContext%2A> 对象。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-208">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="9f4e6-209">WPF 数据绑定引擎提供了额外支持，包括验证、排序、筛选和分组。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-209">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="9f4e6-210">此外，数据绑定支持在标准 WPF 控件显示的用户界面不恰当时，使用数据模板来为数据绑定创建自定义的用户界面。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-210">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="9f4e6-211">有关详细信息，请参阅[数据绑定概述](../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-211">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="9f4e6-212">显卡</span><span class="sxs-lookup"><span data-stu-id="9f4e6-212">Graphics</span></span>

<span data-ttu-id="9f4e6-213">WPF 引入了一组广泛、可伸缩的灵活图形功能，具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-213">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="9f4e6-214">**图形与分辨率和设备均无关**。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-214">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="9f4e6-215">WPF 图形系统中的基本度量单位是与设备无关的像素（即 1/96 英寸），且不考虑实际屏幕分辨率，并为实现与分辨率和设备无关的呈现提供了基础。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-215">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="9f4e6-216">每个与设备无关的像素都会自动缩放，以匹配呈现它的系统的每英寸点数 (dpi) 设置。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-216">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="9f4e6-217">**精度更高**。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-217">**Improved precision**.</span></span> <span data-ttu-id="9f4e6-218">WPF 坐标系统使用双精度浮点数字度量，而不是单精度数字。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-218">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="9f4e6-219">转换和不透明度值也表示为双精度数字。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-219">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="9f4e6-220">WPF 还支持广泛的颜色域 (scRGB)，并集成了对管理来自不同颜色空间的输入的支持。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-220">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="9f4e6-221">**高级图形和动画支持**。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-221">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="9f4e6-222">WPF 通过为你管理动画场景简化了图形编程，你无需担心场景处理、呈现循环和双线性内插。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-222">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="9f4e6-223">此外，WPF 还提供了点击测试支持和全面的 alpha 合成支持。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-223">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="9f4e6-224">**硬件加速**。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-224">**Hardware acceleration**.</span></span> <span data-ttu-id="9f4e6-225">WPF 图形系统充分利用图形硬件来尽量降低 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-225">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="9f4e6-226">二维形状</span><span class="sxs-lookup"><span data-stu-id="9f4e6-226">2D shapes</span></span>

<span data-ttu-id="9f4e6-227">WPF 提供一个常用矢量绘制的二维形状库，如下图中所示的矩形和椭圆：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-227">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![椭圆和矩形](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="9f4e6-229">形状的一个有趣功能是它们不只是用于显示；形状实现许多你期望的控件功能，包括键盘和鼠标输入。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-229">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="9f4e6-230">下面的示例演示 <xref:System.Windows.UIElement.MouseUp> 正在处理的事件 <xref:System.Windows.Shapes.Ellipse> ：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-230">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="9f4e6-231">下图显示了前面的代码生成的内容：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-231">The following figure shows what is produced by the preceding code:</span></span>

![包含文本“单击该椭圆！”的窗口](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="9f4e6-233">有关详细信息，请参阅[WPF 中的形状和基本绘图概述](../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-233">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="9f4e6-234">二维几何图形</span><span class="sxs-lookup"><span data-stu-id="9f4e6-234">2D geometries</span></span>

<span data-ttu-id="9f4e6-235">WPF 提供的二维形状包含基本形状的标准集。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-235">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="9f4e6-236">但是，你可能需要创建自定义形状以帮助改进自定义用户界面的设计。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-236">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="9f4e6-237">为此，WPF 提供了几何图形。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-237">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="9f4e6-238">下图演示了使用几何图形来创建可直接绘制、用作画笔或用于剪辑其他形状和控件的自定义形状。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-238">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="9f4e6-239"><xref:System.Windows.Shapes.Path> 对象可用于绘制封闭式或开放式形状、多个形状，甚至曲线形状。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-239"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="9f4e6-240"><xref:System.Windows.Media.Geometry> 对象可用于剪辑、命中测试以及呈现二维图形数据。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-240"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![Path 的各种用法](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="9f4e6-242">有关详细信息，请参阅[几何概述](graphics-multimedia/geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-242">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="9f4e6-243">二维效果</span><span class="sxs-lookup"><span data-stu-id="9f4e6-243">2D effects</span></span>

<span data-ttu-id="9f4e6-244">WPF 二维功能的子集包括视觉效果，如渐变、位图、绘图、用视频绘画、旋转、缩放和倾斜。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-244">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="9f4e6-245">这些都是通过画笔实现的;下图显示了一些示例：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-245">These are all achieved with brushes; the following figure shows some examples:</span></span>

![不同画笔的图示](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="9f4e6-247">有关详细信息，请参阅[WPF 画笔概述](graphics-multimedia/wpf-brushes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-247">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="9f4e6-248">三维呈现</span><span class="sxs-lookup"><span data-stu-id="9f4e6-248">3D rendering</span></span>

<span data-ttu-id="9f4e6-249">WPF 还包括三维呈现功能，这些功能与二维图形集成，以允许创建更令人兴奋且更有趣的用户界面。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-249">WPF also includes 3D rendering capabilities that integrate with 2D graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="9f4e6-250">例如，下图显示呈现在三维形状上的2D 图像：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-250">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Visual3D 示例屏幕快照](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="9f4e6-252">有关详细信息，请参阅[三维图形概述](graphics-multimedia/3-d-graphics-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-252">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="9f4e6-253">动画</span><span class="sxs-lookup"><span data-stu-id="9f4e6-253">Animation</span></span>

<span data-ttu-id="9f4e6-254">WPF 动画支持可以使控件变大、抖动、旋转和淡出，以形成有趣的页面过渡等。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-254">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="9f4e6-255">你可以对大多数 WPF 类，甚至自定义类进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-255">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="9f4e6-256">下图显示了一个简单的动画操作：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-256">The following figure shows a simple animation in action:</span></span>

![具有动画效果的立方体图](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="9f4e6-258">有关详细信息，请参阅[动画概述](graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-258">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="9f4e6-259">媒体</span><span class="sxs-lookup"><span data-stu-id="9f4e6-259">Media</span></span>

<span data-ttu-id="9f4e6-260">传达丰富内容的一种方法是使用视听媒体。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-260">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="9f4e6-261">WPF 为图像、视频和音频提供特殊支持。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-261">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="9f4e6-262">映像</span><span class="sxs-lookup"><span data-stu-id="9f4e6-262">Images</span></span>

<span data-ttu-id="9f4e6-263">图像对大多数应用程序很常见，WPF 提供多种方式来使用它们。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-263">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="9f4e6-264">下图显示一个用户界面，该用户界面中的列表框中包含缩略图图像。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-264">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="9f4e6-265">选中一个缩略图后，将显示该图像的原尺寸。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-265">When a thumbnail is selected, the image is shown full-size.</span></span>

![缩略图图像和完整尺寸图像](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="9f4e6-267">有关详细信息，请参阅[图像处理概述](graphics-multimedia/imaging-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-267">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="9f4e6-268">视频和音频</span><span class="sxs-lookup"><span data-stu-id="9f4e6-268">Video and audio</span></span>

<span data-ttu-id="9f4e6-269"><xref:System.Windows.Controls.MediaElement> 控件能够播放视频和音频，并且其足够灵活，可以用作其他自定义媒体播放器的基础。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-269">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="9f4e6-270">以下 XAML 标记实现了媒体播放器：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-270">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="9f4e6-271">下图中的窗口显示了 <xref:System.Windows.Controls.MediaElement> 操作中的控件：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-271">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![具有音频和视频的 MediaElement 控件](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="9f4e6-273">有关详细信息，请参阅[图形和多媒体](graphics-multimedia/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-273">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="9f4e6-274">文本和版式</span><span class="sxs-lookup"><span data-stu-id="9f4e6-274">Text and typography</span></span>

<span data-ttu-id="9f4e6-275">为了促进高质量的文本呈现，WPF 提供以下功能：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-275">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="9f4e6-276">OpenType 字体支持。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-276">OpenType font support.</span></span>

- <span data-ttu-id="9f4e6-277">ClearType 增强功能。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-277">ClearType enhancements.</span></span>

- <span data-ttu-id="9f4e6-278">利用硬件加速的高性能。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-278">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="9f4e6-279">文本与媒体、图形和动画的集成。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-279">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="9f4e6-280">国际字体支持和回退机制。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-280">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="9f4e6-281">作为文本与图形集成的演示，下图显示了文本修饰的应用程序：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-281">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![具有各种文本修饰的文本](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="9f4e6-283">有关详细信息，请参阅 [Windows Presentation Foundation 中的版式](advanced/typography-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-283">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="9f4e6-284">自定义 WPF 应用</span><span class="sxs-lookup"><span data-stu-id="9f4e6-284">Customize WPF apps</span></span>

<span data-ttu-id="9f4e6-285">到目前为止，你已经了解用于开发应用程序的核心 WPF 构建块。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-285">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="9f4e6-286">你可以使用该应用程序模型来托管和交付应用程序内容，它主要由控件组成。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-286">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="9f4e6-287">若要简化用户界面中控件的排列，并确保保持该排列能够应对窗口大小和显示设置的更改，你可以使用 WPF 布局系统。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-287">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="9f4e6-288">由于大多数应用程序允许用户与数据交互，因此你可以使用数据绑定来减少将用户界面与数据集成的工作。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-288">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="9f4e6-289">若要增强你应用程序的可视化外观，可以使用 WPF 提供的综合图形、动画和媒体支持。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-289">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="9f4e6-290">不过，在创建和管理真正独特且视觉效果非凡的用户体验时，基础知识通常是不够的。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-290">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="9f4e6-291">标准的 WPF 控件可能无法与你所需的应用程序外观集成。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-291">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="9f4e6-292">数据可能不会以最有效的方式显示。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-292">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="9f4e6-293">你应用程序的整体用户体验可能不适合 Windows 主题的默认外观和感觉。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-293">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="9f4e6-294">在许多方面，演示技术需要视觉扩展性，需要的程度与任何其他类型的扩展性一样。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-294">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="9f4e6-295">为此，WPF 提供了多种机制用于创建独特的用户体验，包括控件、触发器、控件和数据模板、样式、用户界面资源以及主题和皮肤的丰富内容模型。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-295">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="9f4e6-296">内容模型</span><span class="sxs-lookup"><span data-stu-id="9f4e6-296">Content model</span></span>

<span data-ttu-id="9f4e6-297">大多数 WPF 控件的主要用途是显示内容。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-297">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="9f4e6-298">在 WPF 中，可以构成控件内容的项的类型和数目称为控件的 *内容模型*。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-298">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="9f4e6-299">某些控件可以包含一种内容类型的一个项；例如， <xref:System.Windows.Controls.TextBox> 的内容是分配给 <xref:System.Windows.Controls.TextBox.Text%2A> 属性的一个字符串值。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-299">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="9f4e6-300">下面的示例设置的内容 <xref:System.Windows.Controls.TextBox> ：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-300">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="9f4e6-301">下图显示了结果：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-301">The following figure shows the result:</span></span>

![包含文本的 TextBox 控件](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="9f4e6-303">但是，其他控件可以包含不同内容类型的多个项； <xref:System.Windows.Controls.Button>的内容（由 <xref:System.Windows.Controls.ContentControl.Content%2A> 属性指定）可以包含各种项（包括布局控件、文本、图像和形状）。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-303">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="9f4e6-304">下面的示例演示了 <xref:System.Windows.Controls.Button> 包含、、、 <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Border> 和的内容 <xref:System.Windows.Controls.MediaElement> ：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-304">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

<span data-ttu-id="9f4e6-305">下图显示了此按钮的内容：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-305">The following figure shows the content of this button:</span></span>

![包含多种类型的内容的按钮](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="9f4e6-307">有关各种控件支持的内容类型的详细信息，请参阅[WPF 内容模型](controls/wpf-content-model.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-307">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="9f4e6-308">触发器</span><span class="sxs-lookup"><span data-stu-id="9f4e6-308">Triggers</span></span>

<span data-ttu-id="9f4e6-309">尽管 XAML 标记的主要用途是实现应用程序的外观，你也可以使用 XAML 来实现应用程序行为的某些方面。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-309">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="9f4e6-310">其中一个示例是使用触发器来基于用户交互更改应用程序的外观。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-310">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="9f4e6-311">有关详细信息，请参阅[样式和模板](../../desktop-wpf/fundamentals/styles-templates-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-311">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="9f4e6-312">控件模板</span><span class="sxs-lookup"><span data-stu-id="9f4e6-312">Control templates</span></span>

<span data-ttu-id="9f4e6-313">WPF 控件的默认用户界面通常是从其他控件和形状构造的。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-313">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="9f4e6-314">例如， <xref:System.Windows.Controls.Button> 由 <xref:Microsoft.Windows.Themes.ButtonChrome> 和 <xref:System.Windows.Controls.ContentPresenter> 控件组成。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-314">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="9f4e6-315"><xref:Microsoft.Windows.Themes.ButtonChrome> 提供了标准按钮外观，而 <xref:System.Windows.Controls.ContentPresenter> 显示按钮的内容，正如 <xref:System.Windows.Controls.ContentControl.Content%2A> 属性所指定。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-315">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="9f4e6-316">有时，某个控件的默认外观可能与应用程序的整体外观不一致。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-316">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="9f4e6-317">在这种情况下，可以使用 <xref:System.Windows.Controls.ControlTemplate> 更改控件的用户界面的外观，而不更改其内容和行为。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-317">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="9f4e6-318">下面的示例演示如何使用更改的外观 <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> ：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-318">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="9f4e6-319">在此示例中，默认按钮用户界面已被替换为 <xref:System.Windows.Shapes.Ellipse> ，它具有深蓝色边框并使用 <xref:System.Windows.Media.RadialGradientBrush>进行填充。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-319">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="9f4e6-320"><xref:System.Windows.Controls.ContentPresenter> 控件显示 <xref:System.Windows.Controls.Button>的内容，“单击我!”</span><span class="sxs-lookup"><span data-stu-id="9f4e6-320">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="9f4e6-321">单击 <xref:System.Windows.Controls.Button> 后，在 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 控件的默认行为中，仍将引发 <xref:System.Windows.Controls.Button> 事件。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-321">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="9f4e6-322">结果如下图所示：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-322">The result is shown in the following figure:</span></span>

![省略号按钮和第二个窗口](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="9f4e6-324">数据模板</span><span class="sxs-lookup"><span data-stu-id="9f4e6-324">Data templates</span></span>

<span data-ttu-id="9f4e6-325">使用控件模板可以指定控件的外观，而使用数据模板则可以指定控件内容的外观。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-325">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="9f4e6-326">数据模板经常用于改进绑定数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-326">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="9f4e6-327">下图显示了 <xref:System.Windows.Controls.ListBox> 绑定到对象集合的的默认外观 `Task` ，其中每个任务都具有名称、说明和优先级：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-327">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![具有默认外观的列表框](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="9f4e6-329">默认外观是你对 <xref:System.Windows.Controls.ListBox>的期望。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-329">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="9f4e6-330">但是，每个任务的默认外观仅包含任务名称。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-330">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="9f4e6-331">若要显示任务名称、描述和优先级，必须使用 <xref:System.Windows.Controls.ListBox> 更改 <xref:System.Windows.DataTemplate>控件绑定列表项的默认外观。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-331">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="9f4e6-332">下面的 XAML 定义了这样的 <xref:System.Windows.DataTemplate> ，它通过使用特性应用于每个任务 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> ：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-332">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

<span data-ttu-id="9f4e6-333">下图显示了此代码的效果：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-333">The following figure shows the effect of this code:</span></span>

![使用数据模板的列表框](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="9f4e6-335">注意， <xref:System.Windows.Controls.ListBox> 已保留其行为和整体外观；仅列表框显示的内容外观已更改。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-335">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="9f4e6-336">有关详细信息，请参阅[数据模板化概述](data/data-templating-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-336">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="9f4e6-337">样式</span><span class="sxs-lookup"><span data-stu-id="9f4e6-337">Styles</span></span>

<span data-ttu-id="9f4e6-338">通过样式功能，开发人员和设计人员能够对其产品的特定外观进行标准化。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-338">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="9f4e6-339">WPF 提供了一个强样式模型，其基础是 <xref:System.Windows.Style> 元素。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-339">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="9f4e6-340">下面的示例创建一个样式，该样式将窗口上的每个的背景色设置 <xref:System.Windows.Controls.Button> 为 `Orange` ：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-340">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

<span data-ttu-id="9f4e6-341">由于此样式针对所有 <xref:System.Windows.Controls.Button> 控件，因此将自动应用于窗口中的所有按钮，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-341">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![两个橙色按钮](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="9f4e6-343">有关详细信息，请参阅[样式和模板](../../desktop-wpf/fundamentals/styles-templates-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-343">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="9f4e6-344">资源</span><span class="sxs-lookup"><span data-stu-id="9f4e6-344">Resources</span></span>

<span data-ttu-id="9f4e6-345">应用程序中的控件应共享相同的外观，它可以包括从字体和背景色到控件模板、数据模板和样式的所有内容。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-345">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="9f4e6-346">你可以对用户界面资源使用 WPF 支持，以将这些资源封装在一个位置以便重复使用。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-346">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="9f4e6-347">下面的示例定义了一个由和共享的通用背景色 <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label> ：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-347">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

<span data-ttu-id="9f4e6-348">此示例通过使用 `Window.Resources` 属性元素实现背景色资源。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-348">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="9f4e6-349">此资源可供 <xref:System.Windows.Window>的所有子级使用。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-349">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="9f4e6-350">有各种资源作用域，具体如下（按解析顺序列出）：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-350">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="9f4e6-351">单个控件（使用继承的 <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> 属性）。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-351">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="9f4e6-352"><xref:System.Windows.Window> 或 <xref:System.Windows.Controls.Page> （也使用继承的 <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> 属性）。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-352">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="9f4e6-353"><xref:System.Windows.Application> （使用 <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> 属性）。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-353">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="9f4e6-354">这些不同种类的作用域在定义和共享资源的方式方面为你提供了灵活性。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-354">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="9f4e6-355">作为直接将你的资源与特定作用域关联的替代方法，可以通过使用单独的 <xref:System.Windows.ResourceDictionary> （可以在应用程序的其他部分引用）打包一个或多个资源。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-355">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="9f4e6-356">例如，下面的示例定义资源字典中的默认背景色：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-356">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="9f4e6-357">下面的示例引用上一个示例中定义的资源字典，以便在应用程序之间共享：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-357">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

<span data-ttu-id="9f4e6-358">资源和资源字典是 WPF 主题和皮肤支持的基础。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-358">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="9f4e6-359">有关详细信息，请参阅[资源](../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-359">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="9f4e6-360">自定义控件</span><span class="sxs-lookup"><span data-stu-id="9f4e6-360">Custom controls</span></span>

<span data-ttu-id="9f4e6-361">尽管 WPF 提供了大量自定义支持，但你仍可能会遇到现有 WPF 控件不满足你的应用程序或其用户的需求的情况。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-361">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="9f4e6-362">出现这种情况的原因有：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-362">This can occur when:</span></span>

- <span data-ttu-id="9f4e6-363">不能通过自定义现有 WPF 实现的外观和感觉创建所需的用户界面。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-363">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="9f4e6-364">现有 WPF 实现不支持（或很难支持）所需的行为。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-364">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="9f4e6-365">但是，此时，你可以充分利用三个 WPF 模型中的一个来创建新的控件。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-365">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="9f4e6-366">每个模型都针对一个特定的方案并要求你的自定义控件派生自特定 WPF 基类。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-366">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="9f4e6-367">下面列出了这三个模型：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-367">The three models are listed here:</span></span>

- <span data-ttu-id="9f4e6-368">**用户控件模型**。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-368">**User Control Model**.</span></span> <span data-ttu-id="9f4e6-369">自定义控件派生自 <xref:System.Windows.Controls.UserControl> 并由一个或多个其他控件组成。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-369">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="9f4e6-370">**控件模型**。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-370">**Control Model**.</span></span> <span data-ttu-id="9f4e6-371">自定义控件派生自 <xref:System.Windows.Controls.Control> ，并用于生成使用模板将其行为与其外观分隔开来的实现，非常类似大多数 WPF 控件。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-371">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="9f4e6-372">派生自 <xref:System.Windows.Controls.Control> 使得你可以更自由地创建自定义用户界面（相较用户控件），但它可能需要花费更多精力。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-372">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="9f4e6-373">**框架元素模型**。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-373">**Framework Element Model**.</span></span> <span data-ttu-id="9f4e6-374">当其外观由自定义呈现逻辑（而不是模板）定义时，自定义控件派生自 <xref:System.Windows.FrameworkElement> 。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-374">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="9f4e6-375">下面的示例演示一个派生自的自定义数字向上/向下控件 <xref:System.Windows.Controls.UserControl> ：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-375">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="9f4e6-376">下面的示例演示了将用户控件合并到中所需的 XAML <xref:System.Windows.Window> ：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-376">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="9f4e6-377">下图显示 `NumericUpDown` 了中托管的控件 <xref:System.Windows.Window> ：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-377">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![自定义 UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="9f4e6-379">有关自定义控件的详细信息，请参阅[控件创作概述](controls/control-authoring-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-379">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="9f4e6-380">WPF 最佳做法</span><span class="sxs-lookup"><span data-stu-id="9f4e6-380">WPF best practices</span></span>

<span data-ttu-id="9f4e6-381">与任何开发平台一样，可以采用多种方式使用 WPF 以实现所需的结果。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-381">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="9f4e6-382">为确保你的 WPF 应用程序提供所需的用户体验并满足一般用户的需求，针对辅助功能、全球化和本地化以及性能提供了一些建议的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-382">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="9f4e6-383">有关详情，请参阅：</span><span class="sxs-lookup"><span data-stu-id="9f4e6-383">For more information, see:</span></span>

- [<span data-ttu-id="9f4e6-384">辅助功能</span><span class="sxs-lookup"><span data-stu-id="9f4e6-384">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="9f4e6-385">WPF 全球化和本地化</span><span class="sxs-lookup"><span data-stu-id="9f4e6-385">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="9f4e6-386">WPF 应用性能</span><span class="sxs-lookup"><span data-stu-id="9f4e6-386">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="9f4e6-387">WPF 安全性</span><span class="sxs-lookup"><span data-stu-id="9f4e6-387">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="9f4e6-388">后续步骤</span><span class="sxs-lookup"><span data-stu-id="9f4e6-388">Next steps</span></span>

<span data-ttu-id="9f4e6-389">我们已经了解了 WPF 的主要功能。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-389">We've looked at the key features of WPF.</span></span> <span data-ttu-id="9f4e6-390">现在可以生成你的第一个 WPF 应用。</span><span class="sxs-lookup"><span data-stu-id="9f4e6-390">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f4e6-391">演练：我的第一个 WPF 桌面应用</span><span class="sxs-lookup"><span data-stu-id="9f4e6-391">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="9f4e6-392">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f4e6-392">See also</span></span>

- [<span data-ttu-id="9f4e6-393">WPF 入门</span><span class="sxs-lookup"><span data-stu-id="9f4e6-393">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="9f4e6-394">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="9f4e6-394">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="9f4e6-395">WPF 社区资源</span><span class="sxs-lookup"><span data-stu-id="9f4e6-395">WPF community resources</span></span>](getting-started/community-feedback.md)
