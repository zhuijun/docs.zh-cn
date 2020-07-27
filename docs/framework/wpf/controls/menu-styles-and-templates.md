---
title: Menu 样式和模板
description: 了解 Windows Presentation Foundation 菜单控件的样式和模板。 修改 System.windows.controls.controltemplate>，为控件指定独特的外观。
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 5187e4a479609686e39e043808931141ca52078c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164545"
---
# <a name="menu-styles-and-templates"></a><span data-ttu-id="ca03d-104">Menu 样式和模板</span><span class="sxs-lookup"><span data-stu-id="ca03d-104">Menu Styles and Templates</span></span>
<span data-ttu-id="ca03d-105">本主题描述控件的样式和模板 <xref:System.Windows.Controls.Menu> 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.Menu> control.</span></span> <span data-ttu-id="ca03d-106">您可以修改默认值 <xref:System.Windows.Controls.ControlTemplate> ，为控件指定独特的外观。</span><span class="sxs-lookup"><span data-stu-id="ca03d-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ca03d-107">有关详细信息，请参阅为[控件创建模板](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="ca03d-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="menu-parts"></a><span data-ttu-id="ca03d-108">菜单部件</span><span class="sxs-lookup"><span data-stu-id="ca03d-108">Menu Parts</span></span>  
 <span data-ttu-id="ca03d-109"><xref:System.Windows.Controls.Menu>控件没有任何命名部分。</span><span class="sxs-lookup"><span data-stu-id="ca03d-109">The <xref:System.Windows.Controls.Menu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="ca03d-110">为创建时 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Menu> ，模板可能包含 <xref:System.Windows.Controls.ItemsPresenter> 内的 <xref:System.Windows.Controls.ScrollViewer> 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-110">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.Menu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="ca03d-111">（ <xref:System.Windows.Controls.ItemsPresenter> 显示中的每一项 <xref:System.Windows.Controls.Menu> ; <xref:System.Windows.Controls.ScrollViewer> 允许在控件中滚动）。</span><span class="sxs-lookup"><span data-stu-id="ca03d-111">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.Menu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="ca03d-112">如果不 <xref:System.Windows.Controls.ItemsPresenter> 是的直接子级 <xref:System.Windows.Controls.ScrollViewer> ，则必须指定 <xref:System.Windows.Controls.ItemsPresenter> 名称 `ItemsPresenter` 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-112">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menu-states"></a><span data-ttu-id="ca03d-113">菜单状态</span><span class="sxs-lookup"><span data-stu-id="ca03d-113">Menu States</span></span>  
 <span data-ttu-id="ca03d-114">下表列出了控件的可视状态 <xref:System.Windows.Controls.Menu> 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-114">The following table lists the visual states for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="ca03d-115">VisualState 名称</span><span class="sxs-lookup"><span data-stu-id="ca03d-115">VisualState Name</span></span>|<span data-ttu-id="ca03d-116">VisualStateGroup 名称</span><span class="sxs-lookup"><span data-stu-id="ca03d-116">VisualStateGroup Name</span></span>|<span data-ttu-id="ca03d-117">说明</span><span class="sxs-lookup"><span data-stu-id="ca03d-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ca03d-118">有效</span><span class="sxs-lookup"><span data-stu-id="ca03d-118">Valid</span></span>|<span data-ttu-id="ca03d-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ca03d-119">ValidationStates</span></span>|<span data-ttu-id="ca03d-120">控件使用 <xref:System.Windows.Controls.Validation> 类， <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加属性为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ca03d-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ca03d-121">InvalidFocused</span></span>|<span data-ttu-id="ca03d-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ca03d-122">ValidationStates</span></span>|<span data-ttu-id="ca03d-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性是 `true` 控件具有焦点。</span><span class="sxs-lookup"><span data-stu-id="ca03d-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ca03d-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ca03d-124">InvalidUnfocused</span></span>|<span data-ttu-id="ca03d-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ca03d-125">ValidationStates</span></span>|<span data-ttu-id="ca03d-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性是 `true` 控件没有焦点。</span><span class="sxs-lookup"><span data-stu-id="ca03d-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menuitem-parts"></a><span data-ttu-id="ca03d-127">MenuItem 部分</span><span class="sxs-lookup"><span data-stu-id="ca03d-127">MenuItem Parts</span></span>  
 <span data-ttu-id="ca03d-128">下表列出了控件的已命名部件 <xref:System.Windows.Controls.Menu> 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-128">The following table lists the named parts for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="ca03d-129">组成部分</span><span class="sxs-lookup"><span data-stu-id="ca03d-129">Part</span></span>|<span data-ttu-id="ca03d-130">类型</span><span class="sxs-lookup"><span data-stu-id="ca03d-130">Type</span></span>|<span data-ttu-id="ca03d-131">说明</span><span class="sxs-lookup"><span data-stu-id="ca03d-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ca03d-132">PART_Popup</span><span class="sxs-lookup"><span data-stu-id="ca03d-132">PART_Popup</span></span>|<xref:System.Windows.Controls.Primitives.Popup>|<span data-ttu-id="ca03d-133">子菜单的区域。</span><span class="sxs-lookup"><span data-stu-id="ca03d-133">The area for the submenu.</span></span>|  
  
 <span data-ttu-id="ca03d-134">为创建时 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.MenuItem> ，模板可能包含 <xref:System.Windows.Controls.ItemsPresenter> 内的 <xref:System.Windows.Controls.ScrollViewer> 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-134">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.MenuItem>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="ca03d-135">（ <xref:System.Windows.Controls.ItemsPresenter> 显示中的每一项 <xref:System.Windows.Controls.MenuItem> ; <xref:System.Windows.Controls.ScrollViewer> 允许在控件中滚动）。</span><span class="sxs-lookup"><span data-stu-id="ca03d-135">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.MenuItem>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="ca03d-136">如果不 <xref:System.Windows.Controls.ItemsPresenter> 是的直接子级 <xref:System.Windows.Controls.ScrollViewer> ，则必须指定 <xref:System.Windows.Controls.ItemsPresenter> 名称 `ItemsPresenter` 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-136">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menuitem-states"></a><span data-ttu-id="ca03d-137">MenuItem 状态</span><span class="sxs-lookup"><span data-stu-id="ca03d-137">MenuItem States</span></span>  
 <span data-ttu-id="ca03d-138">下表列出了控件的可视状态 <xref:System.Windows.Controls.MenuItem> 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-138">The following table lists the visual states for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
|<span data-ttu-id="ca03d-139">VisualState 名称</span><span class="sxs-lookup"><span data-stu-id="ca03d-139">VisualState Name</span></span>|<span data-ttu-id="ca03d-140">VisualStateGroup 名称</span><span class="sxs-lookup"><span data-stu-id="ca03d-140">VisualStateGroup Name</span></span>|<span data-ttu-id="ca03d-141">说明</span><span class="sxs-lookup"><span data-stu-id="ca03d-141">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ca03d-142">有效</span><span class="sxs-lookup"><span data-stu-id="ca03d-142">Valid</span></span>|<span data-ttu-id="ca03d-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ca03d-143">ValidationStates</span></span>|<span data-ttu-id="ca03d-144">控件使用 <xref:System.Windows.Controls.Validation> 类， <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加属性为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-144">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ca03d-145">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ca03d-145">InvalidFocused</span></span>|<span data-ttu-id="ca03d-146">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ca03d-146">ValidationStates</span></span>|<span data-ttu-id="ca03d-147"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性是 `true` 控件具有焦点。</span><span class="sxs-lookup"><span data-stu-id="ca03d-147">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ca03d-148">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ca03d-148">InvalidUnfocused</span></span>|<span data-ttu-id="ca03d-149">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ca03d-149">ValidationStates</span></span>|<span data-ttu-id="ca03d-150"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性是 `true` 控件没有焦点。</span><span class="sxs-lookup"><span data-stu-id="ca03d-150">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a><span data-ttu-id="ca03d-151">Menu 和 MenuItem System.windows.controls.controltemplate> 示例</span><span class="sxs-lookup"><span data-stu-id="ca03d-151">Menu and MenuItem ControlTemplate Example</span></span>  
 <span data-ttu-id="ca03d-152">下面的示例演示如何为控件定义 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Menu> 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-152">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 <span data-ttu-id="ca03d-153">下面的示例演示如何为控件定义 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.MenuItem> 。</span><span class="sxs-lookup"><span data-stu-id="ca03d-153">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 <span data-ttu-id="ca03d-154">下面的示例定义了 `MenuScrollViewer` ，在前面的示例中使用了。</span><span class="sxs-lookup"><span data-stu-id="ca03d-154">The following example defines the `MenuScrollViewer`, which is used in the previous example.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <span data-ttu-id="ca03d-155">这些 <xref:System.Windows.Controls.ControlTemplate> 示例使用以下一个或多个资源。</span><span class="sxs-lookup"><span data-stu-id="ca03d-155">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ca03d-156">有关完整示例，请参阅[使用 ControlTemplates 设置样式示例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="ca03d-156">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca03d-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca03d-157">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ca03d-158">Control 样式和模板</span><span class="sxs-lookup"><span data-stu-id="ca03d-158">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ca03d-159">控件自定义</span><span class="sxs-lookup"><span data-stu-id="ca03d-159">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ca03d-160">样式设置和模板化</span><span class="sxs-lookup"><span data-stu-id="ca03d-160">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ca03d-161">创建控件模板</span><span class="sxs-lookup"><span data-stu-id="ca03d-161">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
