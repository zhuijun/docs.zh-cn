---
title: 在 WPF 中创建模板 - .NET 桌面
description: 了解如何在 Windows Presentation Foundation 和 .NET Core 中创建和引用控件模板。
author: adegeo
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c372659676b450cde789c96e45c7ec5de2aea194
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325721"
---
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="8a069-103">创建控件模板</span><span class="sxs-lookup"><span data-stu-id="8a069-103">Create a template for a control</span></span>

<span data-ttu-id="8a069-104">使用 Windows Presentation Foundation (WPF)，可以使用自己的可重用模板自定义现有控件的可视结构和行为。</span><span class="sxs-lookup"><span data-stu-id="8a069-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="8a069-105">可以对应用程序、窗口和页面全局应用模板，也可以将模板直接应用于控件。</span><span class="sxs-lookup"><span data-stu-id="8a069-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="8a069-106">需要新建控件的大多数场景均可改为为现有控件创建新模板。</span><span class="sxs-lookup"><span data-stu-id="8a069-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="8a069-107">本文将介绍如何为 <xref:System.Windows.Controls.Button> 控件创建新的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="8a069-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="8a069-108">何时创建 ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="8a069-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="8a069-109">控件有许多属性，例如 <xref:System.Windows.Controls.Border.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A> 和 <xref:System.Windows.Controls.Control.FontFamily%2A>。</span><span class="sxs-lookup"><span data-stu-id="8a069-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="8a069-110">这些属性控制控件外观的不同方面，但可通过设置这些属性进行的更改有限。</span><span class="sxs-lookup"><span data-stu-id="8a069-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="8a069-111">例如，可以从 <xref:System.Windows.Controls.CheckBox> 中将 <xref:System.Windows.Controls.Control.Foreground%2A> 属性设置为蓝色，并将 <xref:System.Windows.Controls.Control.FontStyle%2A> 设置为斜体。</span><span class="sxs-lookup"><span data-stu-id="8a069-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="8a069-112">要自定义设置控件中其他属性无法实现的控件外观时，则创建 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="8a069-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="8a069-113">在多数用户界面中，按钮的总体外观相同：即一个包含某些文本的矩形。</span><span class="sxs-lookup"><span data-stu-id="8a069-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="8a069-114">若想要创建一个圆形的按钮，可以创建一个继承自该按钮或重新创建该按钮功能的新控件。</span><span class="sxs-lookup"><span data-stu-id="8a069-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="8a069-115">此外，新用户控件还会提供圆形视觉对象。</span><span class="sxs-lookup"><span data-stu-id="8a069-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="8a069-116">通过自定义现有控件的可视布局，可以避免创建新控件。</span><span class="sxs-lookup"><span data-stu-id="8a069-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="8a069-117">借助圆形按钮，可创建具有所需可视布局的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="8a069-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="8a069-118">另一方面，如果你需要具有新功能、其他属性和新设置的控件，可创建新的 <xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="8a069-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a069-119">先决条件</span><span class="sxs-lookup"><span data-stu-id="8a069-119">Prerequisites</span></span>

<span data-ttu-id="8a069-120">创建新的 WPF 应用程序，在 MainWindow.xaml（或选择的其他窗口）的 \<Window> 元素中设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="8a069-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

<span data-ttu-id="8a069-121">将 \<Window> 元素的内容设置为以下 XAML：</span><span class="sxs-lookup"><span data-stu-id="8a069-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="8a069-122">最后，MainWindow.xaml 文件应如下所示：</span><span class="sxs-lookup"><span data-stu-id="8a069-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="8a069-123">如果你运行应用程序，它将如下所示：</span><span class="sxs-lookup"><span data-stu-id="8a069-123">If you run the application, it looks like the following:</span></span>

![包含两个无样式的按钮的 WPF 窗口](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="8a069-125">创建 ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="8a069-125">Create a ControlTemplate</span></span>

<span data-ttu-id="8a069-126">声明 <xref:System.Windows.Controls.ControlTemplate> 的最常见方法是在 XAML 文件的 `Resources` 部分中声明为资源。</span><span class="sxs-lookup"><span data-stu-id="8a069-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="8a069-127">模板是资源，因此它们遵从适用于所有资源的相同范围规则。</span><span class="sxs-lookup"><span data-stu-id="8a069-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="8a069-128">简言之，声明模板的位置会影响模板的应用范围。</span><span class="sxs-lookup"><span data-stu-id="8a069-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="8a069-129">例如，如果在应用程序定义 XAML 文件的根元素中声明模板，则该模板可以在应用程序中的任何位置使用。</span><span class="sxs-lookup"><span data-stu-id="8a069-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="8a069-130">如果在窗口中定义模板，则仅该窗口中的控件可以使用该模板。</span><span class="sxs-lookup"><span data-stu-id="8a069-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="8a069-131">首先，将 `Window.Resources` 元素添加到 MainWindow.xaml 文件：</span><span class="sxs-lookup"><span data-stu-id="8a069-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="8a069-132">使用以下属性创建新的 \<ControlTemplate>：</span><span class="sxs-lookup"><span data-stu-id="8a069-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="8a069-133">**x:Key**</span><span class="sxs-lookup"><span data-stu-id="8a069-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="8a069-134">此控制模板很简单：</span><span class="sxs-lookup"><span data-stu-id="8a069-134">This control template will be simple:</span></span>

- <span data-ttu-id="8a069-135">控件的根元素 <xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="8a069-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="8a069-136">用于绘制按钮圆形外观的 <xref:System.Windows.Shapes.Ellipse></span><span class="sxs-lookup"><span data-stu-id="8a069-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="8a069-137">用于显示用户指定的按钮内容的 <xref:System.Windows.Controls.ContentPresenter></span><span class="sxs-lookup"><span data-stu-id="8a069-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="8a069-138">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="8a069-138">TemplateBinding</span></span>

<span data-ttu-id="8a069-139">创建新的 <xref:System.Windows.Controls.ControlTemplate> 时，可能仍然想要使用公共属性更改控件外观。</span><span class="sxs-lookup"><span data-stu-id="8a069-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="8a069-140">[TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 标记扩展将 <xref:System.Windows.Controls.ControlTemplate> 中元素的属性绑定到由控件定义的公共属性。</span><span class="sxs-lookup"><span data-stu-id="8a069-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="8a069-141">使用 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 时，可让控件属性用作模板参数。</span><span class="sxs-lookup"><span data-stu-id="8a069-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="8a069-142">换言之，设置控件属性后，该值将传递到包含 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 的元素。</span><span class="sxs-lookup"><span data-stu-id="8a069-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="8a069-143">椭圆形</span><span class="sxs-lookup"><span data-stu-id="8a069-143">Ellipse</span></span>

<span data-ttu-id="8a069-144">请注意，\<Ellipse> 元素的 :::no-loc text="Fill"::: 和 :::no-loc text="Stroke"::: 属性绑定到了控件的 <xref:System.Windows.Controls.Control.Foreground> 和 <xref:System.Windows.Controls.Control.Background> 属性  。</span><span class="sxs-lookup"><span data-stu-id="8a069-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="8a069-145">ContentPresenter</span><span class="sxs-lookup"><span data-stu-id="8a069-145">ContentPresenter</span></span>

<span data-ttu-id="8a069-146">此外，还将 [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) 元素添加到了模板。</span><span class="sxs-lookup"><span data-stu-id="8a069-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="8a069-147">此模板专为按钮设计，因此请注意该按钮继承自 <xref:System.Windows.Controls.ContentControl>。</span><span class="sxs-lookup"><span data-stu-id="8a069-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="8a069-148">此按钮会显示该元素的内容。</span><span class="sxs-lookup"><span data-stu-id="8a069-148">The button presents the content of the element.</span></span> <span data-ttu-id="8a069-149">可以在该按钮中设置任何内容，例如纯文本，甚至其他控件。</span><span class="sxs-lookup"><span data-stu-id="8a069-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="8a069-150">以下两个按钮均有效：</span><span class="sxs-lookup"><span data-stu-id="8a069-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="8a069-151">在前面的两个示例中，将文本和复选框设置为 [Button.Content](xref:System.Windows.Controls.ContentControl.Content) 属性。</span><span class="sxs-lookup"><span data-stu-id="8a069-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="8a069-152">设置为内容的任何内容都可通过 \<ContentPresenter> 显示，这是模板的功能。</span><span class="sxs-lookup"><span data-stu-id="8a069-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="8a069-153">若将 <xref:System.Windows.Controls.ControlTemplate> 应用到 <xref:System.Windows.Controls.ContentControl> 类型（例如 `Button`），将在元素树中搜索 <xref:System.Windows.Controls.ContentPresenter>。</span><span class="sxs-lookup"><span data-stu-id="8a069-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="8a069-154">若找到了 `ContentPresenter`，模板会自动将控件的 <xref:System.Windows.Controls.ContentControl.Content> 属性绑定到 `ContentPresenter`。</span><span class="sxs-lookup"><span data-stu-id="8a069-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="8a069-155">使用模板</span><span class="sxs-lookup"><span data-stu-id="8a069-155">Use the template</span></span>

<span data-ttu-id="8a069-156">找到本文开头声明的按钮。</span><span class="sxs-lookup"><span data-stu-id="8a069-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="8a069-157">将第二个按钮的 <xref:System.Windows.Controls.Control.Template> 属性设置为 `roundbutton` 资源：</span><span class="sxs-lookup"><span data-stu-id="8a069-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="8a069-158">若运行项目并查看结果，将看到此按钮具有圆形背景。</span><span class="sxs-lookup"><span data-stu-id="8a069-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![包含一个模板椭圆按钮的 WPF 窗口](media/create-apply-template/styled-button.png)

<span data-ttu-id="8a069-160">你可能已注意到，此按钮不是一个圆形，而是倾斜的。</span><span class="sxs-lookup"><span data-stu-id="8a069-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="8a069-161">由于 \<Ellipse> 元素的工作方式，它始终会扩展并填充可用空间。</span><span class="sxs-lookup"><span data-stu-id="8a069-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="8a069-162">将此按钮的 :::no-loc text="width"::: 和 :::no-loc text="height"::: 属性更改为同一个值，以使圆形均衡： </span><span class="sxs-lookup"><span data-stu-id="8a069-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![包含一个模板圆形按钮的 WPF 窗口](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="8a069-164">添加触发器</span><span class="sxs-lookup"><span data-stu-id="8a069-164">Add a Trigger</span></span>

<span data-ttu-id="8a069-165">即使已应用模板的按钮看上去与众不同，但它的行为与任何其他按钮相同。</span><span class="sxs-lookup"><span data-stu-id="8a069-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="8a069-166">若按下此按钮，将触发 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="8a069-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="8a069-167">不过，你可能已注意到，当你将鼠标移到此按钮上方时，此按钮的视觉对象不会改变。</span><span class="sxs-lookup"><span data-stu-id="8a069-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="8a069-168">这些视觉对象交互均由模板定义。</span><span class="sxs-lookup"><span data-stu-id="8a069-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="8a069-169">通过 WPF 提供的动态事件和属性系统，你可以监视特定属性是否是某个值，必要时还可重新设置模板样式。</span><span class="sxs-lookup"><span data-stu-id="8a069-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="8a069-170">在此示例中，你将监视按钮的 <xref:System.Windows.UIElement.IsMouseOver> 属性。</span><span class="sxs-lookup"><span data-stu-id="8a069-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="8a069-171">当鼠标位于控件上方时，使用新颜色设置 \<Ellipse> 的样式。</span><span class="sxs-lookup"><span data-stu-id="8a069-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="8a069-172">此触发器类型称为 PropertyTrigger。</span><span class="sxs-lookup"><span data-stu-id="8a069-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="8a069-173">必须为 \<Ellipse> 添加一个可引用的名称，以便于触发器起作用。</span><span class="sxs-lookup"><span data-stu-id="8a069-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="8a069-174">将其命名为“backgroundElement”。</span><span class="sxs-lookup"><span data-stu-id="8a069-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="8a069-175">接下来，将新的 <xref:System.Windows.Trigger> 添加到 [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) 集合。</span><span class="sxs-lookup"><span data-stu-id="8a069-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="8a069-176">此触发器将监视 `IsMouseOver` 事件是否为值 `true`。</span><span class="sxs-lookup"><span data-stu-id="8a069-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="8a069-177">接下来，将 \<Setter> 添加到 \<Trigger>，后者会将 \<Ellipse> 的 Fill 属性更改为一种新颜色   。</span><span class="sxs-lookup"><span data-stu-id="8a069-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="8a069-178">运行该项目。</span><span class="sxs-lookup"><span data-stu-id="8a069-178">Run the project.</span></span> <span data-ttu-id="8a069-179">请注意，将鼠标移到按钮上方时，\<Ellipse> 的颜色会改变。</span><span class="sxs-lookup"><span data-stu-id="8a069-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![鼠标移到 WPF 按钮上方，以更改填充色](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="8a069-181">使用 VisualState</span><span class="sxs-lookup"><span data-stu-id="8a069-181">Use a VisualState</span></span>

<span data-ttu-id="8a069-182">视觉状态由控件定义和触发。</span><span class="sxs-lookup"><span data-stu-id="8a069-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="8a069-183">例如，当鼠标移到控件上方时，将触发 `CommonStates.MouseOver` 状态。</span><span class="sxs-lookup"><span data-stu-id="8a069-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="8a069-184">可以基于控件的当前状态对属性更改进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="8a069-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="8a069-185">在上一个部分中，当 `IsMouseOver` 属性为 `true` 时，使用 \<PropertyTrigger> 可将按钮的前景色更改为 `AliceBlue`。</span><span class="sxs-lookup"><span data-stu-id="8a069-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="8a069-186">可改为创建一个视觉状态，来对此颜色的更改进行动画处理，以实现平稳过过渡。</span><span class="sxs-lookup"><span data-stu-id="8a069-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="8a069-187">有关 VisualStates 的详细信息，请参阅 [WPF 中的样式和模板](../fundamentals/styles-templates-overview.md#visual-states)。</span><span class="sxs-lookup"><span data-stu-id="8a069-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="8a069-188">若要将 \<PropertyTrigger> 转换为动画效果的视觉状态，首先要从模板删除 \<ControlTemplate.Triggers> 元素 。</span><span class="sxs-lookup"><span data-stu-id="8a069-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="8a069-189">接下来，在控件模板的 \<Grid> 根中，为 `CommonStates` 添加具有 \<VisualStateGroup> 的 \<VisualStateManager.VisualStateGroups> 元素  。</span><span class="sxs-lookup"><span data-stu-id="8a069-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="8a069-190">定义两种状态：`Normal` 和 `MouseOver`。</span><span class="sxs-lookup"><span data-stu-id="8a069-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="8a069-191">触发 \<VisualState> 时，将应用该状态中定义的任何动画。</span><span class="sxs-lookup"><span data-stu-id="8a069-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="8a069-192">为每种状态创建动画。</span><span class="sxs-lookup"><span data-stu-id="8a069-192">Create animations for each state.</span></span> <span data-ttu-id="8a069-193">动画位于 \<Storyboard> 元素中。</span><span class="sxs-lookup"><span data-stu-id="8a069-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="8a069-194">有关情节提要的详细信息，请参阅[情节提要概述](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8a069-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="8a069-195">普通</span><span class="sxs-lookup"><span data-stu-id="8a069-195">Normal</span></span>

  <span data-ttu-id="8a069-196">此状态对椭圆填充进行动画处理，将其还原为控件的 `Background` 颜色。</span><span class="sxs-lookup"><span data-stu-id="8a069-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="8a069-197">MouseOver</span><span class="sxs-lookup"><span data-stu-id="8a069-197">MouseOver</span></span>

  <span data-ttu-id="8a069-198">此状态对椭圆 `Background` 颜色进行动画处理，将其更改为新颜色 `Yellow`。</span><span class="sxs-lookup"><span data-stu-id="8a069-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="8a069-199">\<ControlTemplate> 现在应如下所示 。</span><span class="sxs-lookup"><span data-stu-id="8a069-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="8a069-200">运行该项目。</span><span class="sxs-lookup"><span data-stu-id="8a069-200">Run the project.</span></span> <span data-ttu-id="8a069-201">请注意，将鼠标移到按钮上方时，\<Ellipse> 的颜色会进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="8a069-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![鼠标移到 WPF 按钮上方，以更改填充色](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="8a069-203">后续步骤</span><span class="sxs-lookup"><span data-stu-id="8a069-203">Next steps</span></span>

- [<span data-ttu-id="8a069-204">在 WPF 中为控件创建样式</span><span class="sxs-lookup"><span data-stu-id="8a069-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="8a069-205">WPF 中的样式和模板</span><span class="sxs-lookup"><span data-stu-id="8a069-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="8a069-206">XAML 资源概述</span><span class="sxs-lookup"><span data-stu-id="8a069-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
