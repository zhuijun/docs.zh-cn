---
title: TextBox 样式和模板
description: 了解 Windows Presentation Foundation TextBox 控件的样式和模板。 修改 System.windows.controls.controltemplate>，为控件指定独特的外观。
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 0e15fd40f5590ee46da49cc6c0d5fb30e051f7e4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164735"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="549f6-104">TextBox 样式和模板</span><span class="sxs-lookup"><span data-stu-id="549f6-104">TextBox Styles and Templates</span></span>
<span data-ttu-id="549f6-105">本主题描述控件的样式和模板 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="549f6-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="549f6-106">您可以修改默认值 <xref:System.Windows.Controls.ControlTemplate> ，为控件指定独特的外观。</span><span class="sxs-lookup"><span data-stu-id="549f6-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="549f6-107">有关详细信息，请参阅为[控件创建模板](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="549f6-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="549f6-108">TextBox 部分</span><span class="sxs-lookup"><span data-stu-id="549f6-108">TextBox Parts</span></span>  
 <span data-ttu-id="549f6-109">下表列出了控件的已命名部件 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="549f6-109">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="549f6-110">组成部分</span><span class="sxs-lookup"><span data-stu-id="549f6-110">Part</span></span>|<span data-ttu-id="549f6-111">类型</span><span class="sxs-lookup"><span data-stu-id="549f6-111">Type</span></span>|<span data-ttu-id="549f6-112">说明</span><span class="sxs-lookup"><span data-stu-id="549f6-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="549f6-113">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="549f6-113">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="549f6-114">一个可包含的可视元素 <xref:System.Windows.FrameworkElement> 。</span><span class="sxs-lookup"><span data-stu-id="549f6-114">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="549f6-115">的文本 <xref:System.Windows.Controls.TextBox> 显示在此元素中。</span><span class="sxs-lookup"><span data-stu-id="549f6-115">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="549f6-116">TextBox 状态</span><span class="sxs-lookup"><span data-stu-id="549f6-116">TextBox States</span></span>  
 <span data-ttu-id="549f6-117">下表列出了控件的可视状态 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="549f6-117">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="549f6-118">VisualState 名称</span><span class="sxs-lookup"><span data-stu-id="549f6-118">VisualState Name</span></span>|<span data-ttu-id="549f6-119">VisualStateGroup 名称</span><span class="sxs-lookup"><span data-stu-id="549f6-119">VisualStateGroup Name</span></span>|<span data-ttu-id="549f6-120">描述</span><span class="sxs-lookup"><span data-stu-id="549f6-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="549f6-121">普通</span><span class="sxs-lookup"><span data-stu-id="549f6-121">Normal</span></span>|<span data-ttu-id="549f6-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="549f6-122">CommonStates</span></span>|<span data-ttu-id="549f6-123">默认状态。</span><span class="sxs-lookup"><span data-stu-id="549f6-123">The default state.</span></span>|  
|<span data-ttu-id="549f6-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="549f6-124">MouseOver</span></span>|<span data-ttu-id="549f6-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="549f6-125">CommonStates</span></span>|<span data-ttu-id="549f6-126">鼠标指针悬停在控件上方。</span><span class="sxs-lookup"><span data-stu-id="549f6-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="549f6-127">已禁用</span><span class="sxs-lookup"><span data-stu-id="549f6-127">Disabled</span></span>|<span data-ttu-id="549f6-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="549f6-128">CommonStates</span></span>|<span data-ttu-id="549f6-129">已禁用控件。</span><span class="sxs-lookup"><span data-stu-id="549f6-129">The control is disabled.</span></span>|  
|<span data-ttu-id="549f6-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="549f6-130">ReadOnly</span></span>|<span data-ttu-id="549f6-131">CommonStates</span><span class="sxs-lookup"><span data-stu-id="549f6-131">CommonStates</span></span>|<span data-ttu-id="549f6-132">用户不能更改中的文本 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="549f6-132">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="549f6-133">已设定焦点</span><span class="sxs-lookup"><span data-stu-id="549f6-133">Focused</span></span>|<span data-ttu-id="549f6-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="549f6-134">FocusStates</span></span>|<span data-ttu-id="549f6-135">控件有焦点。</span><span class="sxs-lookup"><span data-stu-id="549f6-135">The control has focus.</span></span>|  
|<span data-ttu-id="549f6-136">失去焦点</span><span class="sxs-lookup"><span data-stu-id="549f6-136">Unfocused</span></span>|<span data-ttu-id="549f6-137">FocusStates</span><span class="sxs-lookup"><span data-stu-id="549f6-137">FocusStates</span></span>|<span data-ttu-id="549f6-138">控件没有焦点。</span><span class="sxs-lookup"><span data-stu-id="549f6-138">The control does not have focus.</span></span>|  
|<span data-ttu-id="549f6-139">有效</span><span class="sxs-lookup"><span data-stu-id="549f6-139">Valid</span></span>|<span data-ttu-id="549f6-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="549f6-140">ValidationStates</span></span>|<span data-ttu-id="549f6-141">控件使用 <xref:System.Windows.Controls.Validation> 类， <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加属性为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="549f6-141">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="549f6-142">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="549f6-142">InvalidFocused</span></span>|<span data-ttu-id="549f6-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="549f6-143">ValidationStates</span></span>|<span data-ttu-id="549f6-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性是 `true` 控件具有焦点。</span><span class="sxs-lookup"><span data-stu-id="549f6-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="549f6-145">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="549f6-145">InvalidUnfocused</span></span>|<span data-ttu-id="549f6-146">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="549f6-146">ValidationStates</span></span>|<span data-ttu-id="549f6-147"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性是 `true` 控件没有焦点。</span><span class="sxs-lookup"><span data-stu-id="549f6-147">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="549f6-148">TextBox System.windows.controls.controltemplate> 示例</span><span class="sxs-lookup"><span data-stu-id="549f6-148">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="549f6-149">下面的示例演示如何为控件定义 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="549f6-149">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="549f6-150">上一示例使用了一个或多个以下资源。</span><span class="sxs-lookup"><span data-stu-id="549f6-150">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="549f6-151">有关完整示例，请参阅[使用 ControlTemplates 设置样式示例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="549f6-151">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="549f6-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="549f6-152">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="549f6-153">Control 样式和模板</span><span class="sxs-lookup"><span data-stu-id="549f6-153">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="549f6-154">控件自定义</span><span class="sxs-lookup"><span data-stu-id="549f6-154">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="549f6-155">样式设置和模板化</span><span class="sxs-lookup"><span data-stu-id="549f6-155">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="549f6-156">创建控件模板</span><span class="sxs-lookup"><span data-stu-id="549f6-156">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
