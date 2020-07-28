---
title: 演练：使用 XAML 创建按钮
description: 本演练介绍如何创建一个动画按钮，以便在使用 XAML 的 Windows Presentation Foundation 应用程序中使用。
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 136d1ad5d6fefd70f0d977e5287ae75f06c52d36
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164842"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="f4f4c-103">演练：使用 XAML 创建按钮</span><span class="sxs-lookup"><span data-stu-id="f4f4c-103">Walkthrough: Create a Button by Using XAML</span></span>

<span data-ttu-id="f4f4c-104">本演练的目的是了解如何创建在 Windows Presentation Foundation （WPF）应用程序中使用的动画按钮。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-104">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="f4f4c-105">本演练使用样式和模板来创建自定义的按钮资源，以允许在按钮声明中重复使用代码和按钮逻辑分离。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-105">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="f4f4c-106">本演练完全是在中编写的 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-106">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4f4c-107">本演练将指导你完成通过键入或复制并粘贴 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 到 Visual Studio 中创建应用程序的步骤。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-107">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Visual Studio.</span></span> <span data-ttu-id="f4f4c-108">如果希望了解如何使用设计器创建相同的应用程序，请参阅[使用 Microsoft Expression Blend 创建按钮](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-108">If you would prefer to learn how to use a designer to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>

<span data-ttu-id="f4f4c-109">下图显示了 "已完成" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-109">The following figure shows the finished buttons.</span></span>

<span data-ttu-id="f4f4c-110">![使用 XAML 创建的自定义按钮](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="f4f4c-110">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-basic-buttons"></a><span data-ttu-id="f4f4c-111">创建基本按钮</span><span class="sxs-lookup"><span data-stu-id="f4f4c-111">Create Basic Buttons</span></span>

<span data-ttu-id="f4f4c-112">首先创建一个新项目，并向该窗口添加几个按钮。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-112">Let's start by creating a new project and adding a few buttons to the window.</span></span>

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="f4f4c-113">创建新的 WPF 项目并向窗口中添加按钮</span><span class="sxs-lookup"><span data-stu-id="f4f4c-113">To create a new WPF project and add buttons to the window</span></span>

1. <span data-ttu-id="f4f4c-114">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-114">Start Visual Studio.</span></span>

2. <span data-ttu-id="f4f4c-115">**创建新的 WPF 项目：** 在 "**文件**" 菜单上，指向 "**新建**"，然后单击 "**项目**"。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-115">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="f4f4c-116">找到**Windows 应用程序（WPF）** 模板，并将项目命名为 "AnimatedButton"。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-116">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="f4f4c-117">这将创建应用程序的主干。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-117">This will create the skeleton for the application.</span></span>

3. <span data-ttu-id="f4f4c-118">**添加基本的默认按钮：** 此演练所需的所有文件都由模板提供。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-118">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="f4f4c-119">在解决方案资源管理器中双击 Window1.xaml 文件，将其打开。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-119">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="f4f4c-120">默认情况下， <xref:System.Windows.Controls.Grid> window1.xaml 中有一个元素。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-120">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="f4f4c-121"><xref:System.Windows.Controls.Grid> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 通过键入或复制以下突出显示的代码并将其粘贴到 window1.xaml 中，删除元素并向页面添加几个按钮：</span><span class="sxs-lookup"><span data-stu-id="f4f4c-121">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>

    ```xaml
    <Window x:Class="AnimatedButton.Window1"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      Title="AnimatedButton" Height="300" Width="300"
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>
    </Window>
    ```

     <span data-ttu-id="f4f4c-122">按 F5 运行该应用程序;应会看到如下图所示的一组按钮。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-122">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>

     <span data-ttu-id="f4f4c-123">![三个基本按钮](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="f4f4c-123">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>

     <span data-ttu-id="f4f4c-124">现在，您已创建了基本按钮，接下来在 Window1.xaml 文件中完成工作。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-124">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="f4f4c-125">本演练的其余部分侧重于 app.xaml 文件，为按钮定义样式和模板。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-125">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>

## <a name="set-basic-properties"></a><span data-ttu-id="f4f4c-126">设置基本属性</span><span class="sxs-lookup"><span data-stu-id="f4f4c-126">Set Basic Properties</span></span>

<span data-ttu-id="f4f4c-127">接下来，让我们在这些按钮上设置一些属性，以控制按钮的外观和布局。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-127">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="f4f4c-128">您将使用资源来定义整个应用程序的按钮属性，而不是单独设置按钮的属性。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-128">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="f4f4c-129">应用程序资源在概念上类似于网页的外部级联样式表（CSS）;但是，资源比级联样式表（CSS）要强大得多，如本演练结束时所见。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-129">Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="f4f4c-130">若要了解有关资源的详细信息，请参阅[XAML 资源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-130">To learn more about resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="f4f4c-131">使用样式设置按钮的基本属性</span><span class="sxs-lookup"><span data-stu-id="f4f4c-131">To use styles to set basic properties on the buttons</span></span>

1. <span data-ttu-id="f4f4c-132">**定义应用程序 .resources 块：** 打开 app.xaml 并添加以下突出显示的标记（如果尚未存在）：</span><span class="sxs-lookup"><span data-stu-id="f4f4c-132">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>

    ```xaml
    <Application x:Class="AnimatedButton.App"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      StartupUri="Window1.xaml"
      >
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>
    </Application>
    ```

     <span data-ttu-id="f4f4c-133">资源范围由定义资源的位置确定。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-133">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="f4f4c-134">在 app.xaml 文件中定义中的资源 `Application.Resources` ，可以从应用程序中的任何位置使用资源。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-134">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="f4f4c-135">若要了解有关定义资源范围的详细信息，请参阅[XAML 资源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-135">To learn more about defining the scope of your resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

2. <span data-ttu-id="f4f4c-136">**创建样式，并使用它定义基本属性值：** 将以下标记添加到 `Application.Resources` 块。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-136">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="f4f4c-137">此标记创建一个 <xref:System.Windows.Style> ，它应用于应用程序中的所有按钮，将 <xref:System.Windows.FrameworkElement.Width%2A> 按钮的设置为90，将设置 <xref:System.Windows.FrameworkElement.Margin%2A> 为10：</span><span class="sxs-lookup"><span data-stu-id="f4f4c-137">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="f4f4c-138"><xref:System.Windows.Style.TargetType%2A>属性指定样式应用于所有类型的对象 <xref:System.Windows.Controls.Button> 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-138">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="f4f4c-139">每个 <xref:System.Windows.Setter> 为设置一个不同的属性值 <xref:System.Windows.Style> 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-139">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="f4f4c-140">因此，应用程序中的每个按钮的宽度均为90，边距为10。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-140">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="f4f4c-141">如果按 F5 运行该应用程序，将看到以下窗口。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-141">If you press F5 to run the application, you see the following window.</span></span>

     <span data-ttu-id="f4f4c-142">![宽度为 90、边距为 10 的按钮](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="f4f4c-142">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>

     <span data-ttu-id="f4f4c-143">您还可以对样式进行更多的操作，其中包括多种方法来微调目标对象、指定复杂的属性值，甚至使用样式作为其他样式的输入。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-143">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="f4f4c-144">有关详细信息，请参阅[样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-144">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

3. <span data-ttu-id="f4f4c-145">**将样式属性值设置为资源：** 通过资源，可以使用一种简单的方法来重复使用通常定义的对象和值。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-145">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="f4f4c-146">使用资源来定义复杂值非常有用，使代码更具模块化。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-146">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="f4f4c-147">将以下突出显示的标记添加到 app.config。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-147">Add the following highlighted markup to app.xaml.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="f4f4c-148">直接在 `Application.Resources` 块下面创建一个名为 "GrayBlueGradientBrush" 的资源。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-148">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="f4f4c-149">此资源定义水平渐变。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-149">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="f4f4c-150">此资源可用作应用程序中任意位置的属性值，包括属性在按钮样式 setter 中的值 <xref:System.Windows.Controls.Control.Background%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-150">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="f4f4c-151">现在，所有按钮的 <xref:System.Windows.Controls.Control.Background%2A> 属性值都是此渐变。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-151">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>

     <span data-ttu-id="f4f4c-152">按 F5 运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-152">Press F5 to run the application.</span></span> <span data-ttu-id="f4f4c-153">其外观应如下所示。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-153">It should look like the following.</span></span>

     <span data-ttu-id="f4f4c-154">![具有渐变背景的按钮](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="f4f4c-154">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>

## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="f4f4c-155">创建定义按钮外观的模板</span><span class="sxs-lookup"><span data-stu-id="f4f4c-155">Create a Template That Defines the Look of the Button</span></span>

<span data-ttu-id="f4f4c-156">在本部分中，将创建一个自定义按钮外观（表示）的模板。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-156">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="f4f4c-157">按钮表示由多个对象组成，其中包括矩形和其他组件，用于为按钮指定独特的外观。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-157">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>

<span data-ttu-id="f4f4c-158">到目前为止，控件在应用程序中的外观控件限制为更改按钮的属性。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-158">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="f4f4c-159">如果要对按钮的外观进行更多的根式更改，会怎么样？</span><span class="sxs-lookup"><span data-stu-id="f4f4c-159">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="f4f4c-160">模板可以强大地控制对象的表示形式。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-160">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="f4f4c-161">由于可以在样式内使用模板，因此可以将模板应用于样式应用到的所有对象（在本演练中为按钮）。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-161">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="f4f4c-162">使用模板定义按钮的外观</span><span class="sxs-lookup"><span data-stu-id="f4f4c-162">To use the template to define the look of the button</span></span>

1. <span data-ttu-id="f4f4c-163">**设置模板：** 由于控件（如 <xref:System.Windows.Controls.Button> 具有 <xref:System.Windows.Controls.Control.Template%2A> 属性），因此可以定义模板属性值，就像我们使用在中设置的其他属性值一样 <xref:System.Windows.Style> <xref:System.Windows.Setter> 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-163">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="f4f4c-164">将以下突出显示的标记添加到按钮样式。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-164">Add the following highlighted markup to your button style.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"
        StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>
      </Style>
    </Application.Resources>
    ```

2. <span data-ttu-id="f4f4c-165">**更改按钮演示：** 此时，需要定义模板。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-165">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="f4f4c-166">添加以下突出显示的标记。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-166">Add the following highlighted markup.</span></span> <span data-ttu-id="f4f4c-167">此标记指定两个 <xref:System.Windows.Shapes.Rectangle> 具有舍入边缘的元素，后跟一个 <xref:System.Windows.Controls.DockPanel> 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-167">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="f4f4c-168"><xref:System.Windows.Controls.DockPanel>用于承载 <xref:System.Windows.Controls.ContentPresenter> 按钮的。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-168">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="f4f4c-169"><xref:System.Windows.Controls.ContentPresenter>显示按钮的内容。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-169">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="f4f4c-170">在本演练中，内容是文本（"Button 1"、"Button 2"、"Button 3"）。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-170">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="f4f4c-171">所有模板组件（矩形和 <xref:System.Windows.Controls.DockPanel> ）都在中进行布局 <xref:System.Windows.Controls.Grid> 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-171">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="f4f4c-172">按 F5 运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-172">Press F5 to run the application.</span></span> <span data-ttu-id="f4f4c-173">其外观应如下所示。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-173">It should look like the following.</span></span>

     ![具有3个按钮的窗口](./media/custom-button-animatedbutton-4.gif)

3. <span data-ttu-id="f4f4c-175">**将 Glasseffect 添加到模板：** 接下来，你将添加玻璃。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-175">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="f4f4c-176">首先，创建一些创建玻璃渐变效果的资源。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-176">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="f4f4c-177">在块中的任何位置添加这些渐变资源 `Application.Resources` ：</span><span class="sxs-lookup"><span data-stu-id="f4f4c-177">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>

    ```xaml
    <Application.Resources>
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />
        <GradientStop Color="Transparent" Offset="0.4" />
        <GradientStop Color="WhiteSmoke" Offset="0.5" />
        <GradientStop Color="Transparent" Offset="0.75" />
        <GradientStop Color="WhiteSmoke" Offset="0.9" />
        <GradientStop Color="Transparent" Offset="1" />
      </GradientStopCollection>
      <LinearGradientBrush x:Key="MyGlassBrushResource"
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />
    <!-- Styles and other resources below here. -->
    ```

     <span data-ttu-id="f4f4c-178">这些资源用作在 <xref:System.Windows.Shapes.Shape.Fill%2A> 按钮模板的中插入的矩形的 <xref:System.Windows.Controls.Grid> 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-178">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="f4f4c-179">将以下突出显示的标记添加到模板。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-179">Add the following highlighted markup to the template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"
          ClipToBounds="True">

        <!-- Outer Rectangle with rounded corners. -->
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

        <!-- Inner Rectangle with rounded corners. -->
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />

        <!-- Glass Rectangle -->
        <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch"
          StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
          Fill="{StaticResource MyGlassBrushResource}"
          RenderTransformOrigin="0.5,0.5">
          <Rectangle.Stroke>
            <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
              <LinearGradientBrush.GradientStops>
                <GradientStop Offset="0.0" Color="LightBlue" />
                <GradientStop Offset="1.0" Color="Gray" />
              </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
          </Rectangle.Stroke>
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
          <Rectangle.BitmapEffect>
            <BevelBitmapEffect />
          </Rectangle.BitmapEffect>
        </Rectangle>

        <!-- Present Text of the button. -->
        <DockPanel Name="myContentPresenterDockPanel">
          <ContentPresenter x:Name="myContentPresenter" Margin="20"
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
        </DockPanel>
      </Grid>
    </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="f4f4c-180">请注意， <xref:System.Windows.UIElement.Opacity%2A> `x:Name` 属性为 "glassCube" 的矩形的为0，因此，在运行该示例时，看不到顶部显示的玻璃矩形。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-180">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="f4f4c-181">这是因为，稍后我们会将触发器添加到模板中，以便用户与按钮交互时。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-181">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="f4f4c-182">不过，现在可以通过 <xref:System.Windows.UIElement.Opacity%2A> 将值更改为1并运行应用程序来查看按钮的外观。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-182">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="f4f4c-183">请参阅下图。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-183">See the following figure.</span></span> <span data-ttu-id="f4f4c-184">继续下一步之前，请将 <xref:System.Windows.UIElement.Opacity%2A> 返回回0。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-184">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>

     <span data-ttu-id="f4f4c-185">![使用 XAML 创建的自定义按钮](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="f4f4c-185">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-button-interactivity"></a><span data-ttu-id="f4f4c-186">创建按钮交互性</span><span class="sxs-lookup"><span data-stu-id="f4f4c-186">Create Button Interactivity</span></span>

<span data-ttu-id="f4f4c-187">在本部分中，你将创建属性触发器和事件触发器，以更改属性值，并运行动画来响应用户操作，例如，将鼠标指针移到按钮上并单击。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-187">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>

<span data-ttu-id="f4f4c-188">添加交互（鼠标悬停、鼠标离开、单击等）的一种简单方法是在模板或样式中定义触发器。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-188">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="f4f4c-189">若要创建 <xref:System.Windows.Trigger> ，请定义属性 "condition"，例如： button <xref:System.Windows.UIElement.IsMouseOver%2A> 属性值等于 `true` 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-189">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="f4f4c-190">然后，定义在触发器条件为 true 时执行的 setter （操作）。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-190">You then define setters (actions) that take place when the trigger condition is true.</span></span>

### <a name="to-create-button-interactivity"></a><span data-ttu-id="f4f4c-191">若要创建按钮交互性</span><span class="sxs-lookup"><span data-stu-id="f4f4c-191">To create button interactivity</span></span>

1. <span data-ttu-id="f4f4c-192">**添加模板触发器：** 将突出显示的标记添加到模板。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-192">**Add template triggers:** Add the highlighted markup to your template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}"
          Height="{TemplateBinding Height}" ClipToBounds="True">

          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch" Stroke="Transparent"
            StrokeThickness="20"
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"
          />

          <!-- Glass Rectangle -->
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch"
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
            Fill="{StaticResource MyGlassBrushResource}"
            RenderTransformOrigin="0.5,0.5">
            <Rectangle.Stroke>
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
                <LinearGradientBrush.GradientStops>
                  <GradientStop Offset="0.0" Color="LightBlue" />
                  <GradientStop Offset="1.0" Color="Gray" />
                </LinearGradientBrush.GradientStops>
              </LinearGradientBrush>
            </Rectangle.Stroke>

            <!-- These transforms have no effect as they
                 are declared here.
                 The reason the transforms are included is to be targets
                 for animation (see later). -->
            <Rectangle.RenderTransform>
              <TransformGroup>
                <ScaleTransform />
                <RotateTransform />
              </TransformGroup>
            </Rectangle.RenderTransform>

              <!-- A BevelBitmapEffect is applied to give the button a
                   "Beveled" look. -->
            <Rectangle.BitmapEffect>
              <BevelBitmapEffect />
            </Rectangle.BitmapEffect>
          </Rectangle>

          <!-- Present Text of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20"
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>

        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>
      </ControlTemplate>
    </Setter.Value>
    ```

2. <span data-ttu-id="f4f4c-193">**添加属性触发器：** 将突出显示的标记添加到 `ControlTemplate.Triggers` 块：</span><span class="sxs-lookup"><span data-stu-id="f4f4c-193">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     <span data-ttu-id="f4f4c-194">按 F5 运行应用程序，并在按钮上运行鼠标指针时查看效果。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-194">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>

3. <span data-ttu-id="f4f4c-195">**添加焦点触发器：** 接下来，我们将添加一些类似的 setter 来处理按钮有焦点的情况（例如，用户单击后）。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-195">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->
      <Trigger Property="IsMouseOver" Value="True">

        <!-- Below are three property settings that occur when the
             condition is met (user mouses over button).  -->
        <!-- Change the color of the outer rectangle when user          mouses over it. -->
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />

        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />

        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">
          <Setter.Value>
            <BlurBitmapEffect Radius="1" />
          </Setter.Value>
        </Setter>
      </Trigger>
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>

    </ControlTemplate.Triggers>
    ```

     <span data-ttu-id="f4f4c-196">按 F5 运行应用程序，并单击其中一个按钮。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-196">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="f4f4c-197">请注意，单击按钮后，按钮会保持突出显示，因为它仍有焦点。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-197">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="f4f4c-198">如果单击另一个按钮，新按钮会获得焦点，而最后一个按钮丢失。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-198">If you click another button, the new button gains focus while the last one loses it.</span></span>

4. <span data-ttu-id="f4f4c-199">**添加动画** <xref:System.Windows.UIElement.MouseEnter>**和** <xref:System.Windows.UIElement.MouseLeave>**:** 接下来，将一些动画添加到触发器。  </span><span class="sxs-lookup"><span data-stu-id="f4f4c-199">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="f4f4c-200">将以下标记添加到块内的任意位置 `ControlTemplate.Triggers` 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-200">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>

    ```xaml
    <!-- Animations that start when mouse enters and leaves button. -->
    <EventTrigger RoutedEvent="Mouse.MouseEnter">
      <EventTrigger.Actions>
        <BeginStoryboard Name="mouseEnterBeginStoryboard">
          <Storyboard>
          <!-- This animation makes the glass rectangle shrink in the X direction. -->
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"
              By="-0.1" Duration="0:0:0.5" />
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->
            <DoubleAnimation
            Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"
              By="-0.1" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    <EventTrigger RoutedEvent="Mouse.MouseLeave">
      <EventTrigger.Actions>
        <!-- Stopping the storyboard sets all animated properties back to default. -->
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="f4f4c-201">当鼠标指针移到按钮上并在指针离开时返回到正常大小时，玻璃矩形会收缩。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-201">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>

     <span data-ttu-id="f4f4c-202">当指针进入按钮（引发事件）时，会触发两个动画 <xref:System.Windows.UIElement.MouseEnter> 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-202">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="f4f4c-203">这些动画沿 X 和 Y 轴收缩玻璃矩形。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-203">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="f4f4c-204">请注意元素上的属性 <xref:System.Windows.Media.Animation.DoubleAnimation> ，即 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-204">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="f4f4c-205"><xref:System.Windows.Media.Animation.Timeline.Duration%2A>指定动画每半秒出现一次，并 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 指定玻璃缩小10%。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-205">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>

     <span data-ttu-id="f4f4c-206">第二个事件触发器（ <xref:System.Windows.UIElement.MouseLeave> ）只是停止第一个触发器。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-206">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="f4f4c-207">停止时 <xref:System.Windows.Media.Animation.Storyboard> ，所有动画属性都将恢复为其默认值。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-207">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="f4f4c-208">因此，当用户将指针移到按钮上时，按钮返回到鼠标指针移到按钮上之前的状态。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-208">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="f4f4c-209">有关动画的详细信息，请参阅[动画概述](../graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-209">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

5. <span data-ttu-id="f4f4c-210">在**单击按钮时添加动画：** 最后一步是在用户单击按钮时添加触发器。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-210">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="f4f4c-211">在块中的任意位置添加以下标记 `ControlTemplate.Triggers` ：</span><span class="sxs-lookup"><span data-stu-id="f4f4c-211">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <!-- Animation fires when button is clicked, causing glass to spin.  -->
    <EventTrigger RoutedEvent="Button.Click">
      <EventTrigger.Actions>
        <BeginStoryboard>
          <Storyboard>
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"
              By="360" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="f4f4c-212">按 F5 运行应用程序，然后单击其中一个按钮。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-212">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="f4f4c-213">单击按钮时，玻璃矩形会旋转。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-213">When you click a button, the glass rectangle spins around.</span></span>

## <a name="summary"></a><span data-ttu-id="f4f4c-214">总结</span><span class="sxs-lookup"><span data-stu-id="f4f4c-214">Summary</span></span>
 <span data-ttu-id="f4f4c-215">在本演练中，您执行了以下练习：</span><span class="sxs-lookup"><span data-stu-id="f4f4c-215">In this walkthrough, you performed the following exercises:</span></span>

- <span data-ttu-id="f4f4c-216">目标 <xref:System.Windows.Style> 为对象类型（ <xref:System.Windows.Controls.Button> ）。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-216">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>

- <span data-ttu-id="f4f4c-217">使用的整个应用程序中的按钮的受控基本属性 <xref:System.Windows.Style> 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-217">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>

- <span data-ttu-id="f4f4c-218">创建了一些资源，如用于资源库属性值的渐变 <xref:System.Windows.Style> 。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-218">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>

- <span data-ttu-id="f4f4c-219">通过将模板应用于按钮，自定义了整个应用程序中的按钮的外观。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-219">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>

- <span data-ttu-id="f4f4c-220">用于响应用户操作（如、和）的按钮的自定义行为， <xref:System.Windows.UIElement.MouseEnter> <xref:System.Windows.UIElement.MouseLeave> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 其中包含动画效果。</span><span class="sxs-lookup"><span data-stu-id="f4f4c-220">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4f4c-221">请参阅</span><span class="sxs-lookup"><span data-stu-id="f4f4c-221">See also</span></span>

- [<span data-ttu-id="f4f4c-222">使用 Microsoft Expression Blend 创建按钮</span><span class="sxs-lookup"><span data-stu-id="f4f4c-222">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="f4f4c-223">样式设置和模板化</span><span class="sxs-lookup"><span data-stu-id="f4f4c-223">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f4f4c-224">动画概述</span><span class="sxs-lookup"><span data-stu-id="f4f4c-224">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="f4f4c-225">使用纯色和渐变进行绘制概述</span><span class="sxs-lookup"><span data-stu-id="f4f4c-225">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="f4f4c-226">位图效果概述</span><span class="sxs-lookup"><span data-stu-id="f4f4c-226">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
