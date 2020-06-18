---
title: 设置控件的 tab 键顺序
description: 了解如何设置 Windows 窗体上的控件的 tab 键顺序。 使用 Visual Studio 设置 tab 键顺序，或在属性窗口中使用 TabIndex 属性。
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d16da1ac73cc030b92bb36c4bfa3a79985339bf
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903350"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a><span data-ttu-id="e3643-104">如何：在 Windows 窗体上设置 tab 键顺序</span><span class="sxs-lookup"><span data-stu-id="e3643-104">How to: Set the tab order on Windows Forms</span></span>

<span data-ttu-id="e3643-105">Tab 键顺序是用户通过按 Tab 键将焦点从一个控件移动到另一个控件的顺序。</span><span class="sxs-lookup"><span data-stu-id="e3643-105">The tab order is the order in which a user moves focus from one control to another by pressing the Tab key.</span></span> <span data-ttu-id="e3643-106">每个窗体都具有自己的 tab 键顺序。</span><span class="sxs-lookup"><span data-stu-id="e3643-106">Each form has its own tab order.</span></span> <span data-ttu-id="e3643-107">默认情况下，tab 键顺序与您创建控件的顺序相同。</span><span class="sxs-lookup"><span data-stu-id="e3643-107">By default, the tab order is the same as the order in which you created the controls.</span></span> <span data-ttu-id="e3643-108">Tab 顺序编号从0开始。</span><span class="sxs-lookup"><span data-stu-id="e3643-108">Tab-order numbering begins with zero.</span></span>

## <a name="to-set-the-tab-order-of-a-control"></a><span data-ttu-id="e3643-109">设置控件的 tab 键顺序</span><span class="sxs-lookup"><span data-stu-id="e3643-109">To set the tab order of a control</span></span>

1. <span data-ttu-id="e3643-110">在 Visual Studio 的 "**视图**" 菜单上，选择 **"Tab 键顺序**"。</span><span class="sxs-lookup"><span data-stu-id="e3643-110">In Visual Studio, on the **View** menu, select **Tab Order**.</span></span>

   <span data-ttu-id="e3643-111">这会激活窗体上的 tab 键顺序选择模式。</span><span class="sxs-lookup"><span data-stu-id="e3643-111">This activates the tab-order selection mode on the form.</span></span> <span data-ttu-id="e3643-112"><xref:System.Windows.Forms.Control.TabIndex%2A>每个控件的左上角会出现一个数字（表示属性）。</span><span class="sxs-lookup"><span data-stu-id="e3643-112">A number (representing the <xref:System.Windows.Forms.Control.TabIndex%2A> property) appears in the upper-left corner of each control.</span></span>

2. <span data-ttu-id="e3643-113">按顺序单击控件以建立所需的 tab 键顺序。</span><span class="sxs-lookup"><span data-stu-id="e3643-113">Click the controls sequentially to establish the tab order you want.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e3643-114">控件在 tab 键顺序中的位置可设置为大于或等于0的任何值。</span><span class="sxs-lookup"><span data-stu-id="e3643-114">A control's place within the tab order can be set to any value greater than or equal to 0.</span></span> <span data-ttu-id="e3643-115">发生重复时，将对两个控件的 z 顺序进行计算，并使控件位于顶部。</span><span class="sxs-lookup"><span data-stu-id="e3643-115">When duplicates occur, the z-order of the two controls is evaluated and the control on top is tabbed to first.</span></span> <span data-ttu-id="e3643-116">（Z 顺序是窗体上的控件沿窗体的 z 轴 [深度] 的可视化分层。</span><span class="sxs-lookup"><span data-stu-id="e3643-116">(The z-order is the visual layering of controls on a form along the form's z-axis [depth].</span></span> <span data-ttu-id="e3643-117">Z 顺序确定哪些控件位于其他控件前面。）有关 z 顺序的详细信息，请参阅[Windows 窗体上的分层对象](how-to-layer-objects-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e3643-117">The z-order determines which controls are in front of other controls.) For more information on z-order, see [Layering Objects on Windows Forms](how-to-layer-objects-on-windows-forms.md).</span></span>

3. <span data-ttu-id="e3643-118">完成后，再次选择 "**视图**" 菜单上的 **"tab 键顺序**"，以退出 tab 键顺序模式。</span><span class="sxs-lookup"><span data-stu-id="e3643-118">When you have finished, select **Tab Order** on the **View** menu again to leave tab order mode.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e3643-119">无法获得焦点的控件以及禁用和不可见控件都没有 <xref:System.Windows.Forms.Control.TabIndex%2A> 属性，并且不包含在 tab 键顺序中。</span><span class="sxs-lookup"><span data-stu-id="e3643-119">Controls that cannot get the focus, as well as disabled and invisible controls, do not have a <xref:System.Windows.Forms.Control.TabIndex%2A> property and are not included in the tab order.</span></span> <span data-ttu-id="e3643-120">当用户按 Tab 键时，将跳过这些控件。</span><span class="sxs-lookup"><span data-stu-id="e3643-120">As a user presses the Tab key, these controls are skipped.</span></span>

<span data-ttu-id="e3643-121">或者，可以使用属性在属性窗口中设置 tab 键顺序 <xref:System.Windows.Forms.Control.TabIndex%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e3643-121">Alternatively, tab order can be set in the Properties window using the <xref:System.Windows.Forms.Control.TabIndex%2A> property.</span></span> <span data-ttu-id="e3643-122"><xref:System.Windows.Forms.Control.TabIndex%2A>控件的属性确定它在 tab 键顺序中的位置。</span><span class="sxs-lookup"><span data-stu-id="e3643-122">The <xref:System.Windows.Forms.Control.TabIndex%2A> property of a control determines where it is positioned in the tab order.</span></span> <span data-ttu-id="e3643-123">默认情况下，绘制的第一个控件的 <xref:System.Windows.Forms.Control.TabIndex%2A> 值为0，第二个控件的值为 <xref:System.Windows.Forms.Control.TabIndex%2A> 1，依此类推。</span><span class="sxs-lookup"><span data-stu-id="e3643-123">By default, the first control drawn has a <xref:System.Windows.Forms.Control.TabIndex%2A> value of 0, the second has a <xref:System.Windows.Forms.Control.TabIndex%2A> of 1, and so on.</span></span>

<span data-ttu-id="e3643-124">此外，默认情况下， <xref:System.Windows.Forms.GroupBox> 控件的 <xref:System.Windows.Forms.Control.TabIndex%2A> 值为整数。</span><span class="sxs-lookup"><span data-stu-id="e3643-124">Additionally, by default, a <xref:System.Windows.Forms.GroupBox> control has its own <xref:System.Windows.Forms.Control.TabIndex%2A> value, which is a whole number.</span></span> <span data-ttu-id="e3643-125"><xref:System.Windows.Forms.GroupBox>控件本身不能在运行时具有焦点。</span><span class="sxs-lookup"><span data-stu-id="e3643-125">A <xref:System.Windows.Forms.GroupBox> control itself cannot have focus at run time.</span></span> <span data-ttu-id="e3643-126">因此，中的每个控件 <xref:System.Windows.Forms.GroupBox> 都具有其自己的十进制 <xref:System.Windows.Forms.Control.TabIndex%2A> 值（从0开始）。</span><span class="sxs-lookup"><span data-stu-id="e3643-126">Thus, each control within a <xref:System.Windows.Forms.GroupBox> has its own decimal <xref:System.Windows.Forms.Control.TabIndex%2A> value, beginning with .0.</span></span> <span data-ttu-id="e3643-127">当然，随着 <xref:System.Windows.Forms.Control.TabIndex%2A> <xref:System.Windows.Forms.GroupBox> 控件的增加，其中的控件将相应递增。</span><span class="sxs-lookup"><span data-stu-id="e3643-127">Naturally, as the <xref:System.Windows.Forms.Control.TabIndex%2A> of a <xref:System.Windows.Forms.GroupBox> control is incremented, the controls within it will be incremented accordingly.</span></span> <span data-ttu-id="e3643-128">如果更改了 <xref:System.Windows.Forms.Control.TabIndex%2A> 5 到6之间的值，则 <xref:System.Windows.Forms.Control.TabIndex%2A> 该组中第一个控件的值将自动更改为6.0，依此类推。</span><span class="sxs-lookup"><span data-stu-id="e3643-128">If you changed a <xref:System.Windows.Forms.Control.TabIndex%2A> value from 5 to 6, the <xref:System.Windows.Forms.Control.TabIndex%2A> value of the first control in its group automatically changes to 6.0, and so on.</span></span>

<span data-ttu-id="e3643-129">最后，可以按 tab 键顺序跳过窗体上的多个控件。</span><span class="sxs-lookup"><span data-stu-id="e3643-129">Finally, any control of the many on your form can be skipped in the tab order.</span></span> <span data-ttu-id="e3643-130">通常，在运行时连续按 Tab 会按 tab 键顺序选择每个控件。</span><span class="sxs-lookup"><span data-stu-id="e3643-130">Usually, pressing Tab successively at run time selects each control in the tab order.</span></span> <span data-ttu-id="e3643-131">通过关闭 <xref:System.Windows.Forms.Control.TabStop%2A> 属性，可以使控件按窗体的 tab 键顺序传递。</span><span class="sxs-lookup"><span data-stu-id="e3643-131">By turning off the <xref:System.Windows.Forms.Control.TabStop%2A> property, you can make a control be passed over in the tab order of the form.</span></span>

## <a name="to-remove-a-control-from-the-tab-order"></a><span data-ttu-id="e3643-132">从 tab 键顺序中删除控件</span><span class="sxs-lookup"><span data-stu-id="e3643-132">To remove a control from the tab order</span></span>

<span data-ttu-id="e3643-133"><xref:System.Windows.Forms.Control.TabStop%2A>在 "**属性**" 窗口中，将控件的属性设置为**false** 。</span><span class="sxs-lookup"><span data-stu-id="e3643-133">Set the control's <xref:System.Windows.Forms.Control.TabStop%2A> property to **false** in the **Properties** window.</span></span>

<span data-ttu-id="e3643-134">一个控件 <xref:System.Windows.Forms.Control.TabStop%2A> ，其属性已设置为 `false` 仍保持其在 tab 键顺序中的位置，即使当你使用 tab 键在控件之间进行切换时，也会跳过控件。</span><span class="sxs-lookup"><span data-stu-id="e3643-134">A control whose <xref:System.Windows.Forms.Control.TabStop%2A> property has been set to `false` still maintains its position in the tab order, even though the control is skipped when you cycle through the controls with the Tab key.</span></span>

> [!NOTE]
> <span data-ttu-id="e3643-135">单选按钮组在运行时具有单个制表位。</span><span class="sxs-lookup"><span data-stu-id="e3643-135">A radio button group has a single tab stop at run time.</span></span> <span data-ttu-id="e3643-136">选定的按钮（即，其 <xref:System.Windows.Forms.RadioButton.Checked%2A> 属性设置为的按钮）的 `true` <xref:System.Windows.Forms.Control.TabStop%2A> 属性自动设置为 `true` ，而其他按钮的 <xref:System.Windows.Forms.Control.TabStop%2A> 属性设置为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="e3643-136">The selected button (that is, the button with its <xref:System.Windows.Forms.RadioButton.Checked%2A> property set to `true`) has its <xref:System.Windows.Forms.Control.TabStop%2A> property automatically set to `true`, while the other buttons have their <xref:System.Windows.Forms.Control.TabStop%2A> property set to `false`.</span></span> <span data-ttu-id="e3643-137">有关分组控件的详细信息 <xref:System.Windows.Forms.RadioButton> ，请参阅将[Windows 窗体单选按钮控件分组为一个集](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)。</span><span class="sxs-lookup"><span data-stu-id="e3643-137">For more information about grouping <xref:System.Windows.Forms.RadioButton> controls, see [Grouping Windows Forms RadioButton Controls to Function as a Set](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3643-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3643-138">See also</span></span>

- [<span data-ttu-id="e3643-139">Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="e3643-139">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="e3643-140">在 Windows 窗体上使用的控件</span><span class="sxs-lookup"><span data-stu-id="e3643-140">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="e3643-141">根据功能列出的 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="e3643-141">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
