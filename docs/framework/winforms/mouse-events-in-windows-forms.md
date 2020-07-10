---
title: 鼠标事件
description: 了解如何从鼠标事件获取鼠标位置，并了解鼠标单击事件在 Windows 窗体控件中的引发顺序。
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: 640448109961ea5fdf3600ef9e72d7d10e8c9e49
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174375"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="673af-103">Windows 窗体中的鼠标事件</span><span class="sxs-lookup"><span data-stu-id="673af-103">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="673af-104">当处理鼠标输入时，通常想要知道鼠标指针的位置和鼠标按钮的状态。</span><span class="sxs-lookup"><span data-stu-id="673af-104">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="673af-105">本主题详细介绍如何从鼠标事件获取此信息，并说明在 Windows 窗体控件中引发的鼠标单击事件的顺序。</span><span class="sxs-lookup"><span data-stu-id="673af-105">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="673af-106">有关所有鼠标事件的列表和说明，请参阅[鼠标输入在 Windows 窗体中的工作原理](how-mouse-input-works-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="673af-106">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="673af-107">另请参阅[事件处理程序概述 (Windows 窗体) ](event-handlers-overview-windows-forms.md)和[事件概述 (Windows 窗体](events-overview-windows-forms.md)) 。</span><span class="sxs-lookup"><span data-stu-id="673af-107">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="673af-108">鼠标信息</span><span class="sxs-lookup"><span data-stu-id="673af-108">Mouse Information</span></span>

<span data-ttu-id="673af-109"><xref:System.Windows.Forms.MouseEventArgs> 将发送到与单击鼠标按钮和跟踪鼠标移动相关的鼠标事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="673af-109">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="673af-110"><xref:System.Windows.Forms.MouseEventArgs> 提供有关当前鼠标状态的信息，包括鼠标指针在客户端坐标中的位置、按下的鼠标按钮是哪一个以及是否已经滚动鼠标滚轮。</span><span class="sxs-lookup"><span data-stu-id="673af-110"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="673af-111">几个鼠标事件（例如通知鼠标指针进入或离开控件边界的时间）会向事件处理程序发送 <xref:System.EventArgs>，但不提供详细信息。</span><span class="sxs-lookup"><span data-stu-id="673af-111">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="673af-112">如果想要知道鼠标按钮当前的状态或鼠标指针的位置，并且希望避免处理鼠标事件，还可以使用 <xref:System.Windows.Forms.Control> 类的 <xref:System.Windows.Forms.Control.MouseButtons%2A> 和 <xref:System.Windows.Forms.Control.MousePosition%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="673af-112">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="673af-113"><xref:System.Windows.Forms.Control.MouseButtons%2A> 返回有关当前按下哪些鼠标按钮的信息。</span><span class="sxs-lookup"><span data-stu-id="673af-113"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="673af-114"><xref:System.Windows.Forms.Control.MousePosition%2A> 返回鼠标指针的屏幕坐标，等同于由 <xref:System.Windows.Forms.Cursor.Position%2A> 返回的值。</span><span class="sxs-lookup"><span data-stu-id="673af-114">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="673af-115">在屏幕坐标和客户端坐标之间转换</span><span class="sxs-lookup"><span data-stu-id="673af-115">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="673af-116">由于某些鼠标位置信息以客户端坐标提供，另一些以屏幕坐标提供，因此可能需要将某个点的位置信息从一个坐标系统转换到另一个坐标系统。</span><span class="sxs-lookup"><span data-stu-id="673af-116">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="673af-117">通过使用 <xref:System.Windows.Forms.Control> 类提供的 <xref:System.Windows.Forms.Control.PointToClient%2A> 和 <xref:System.Windows.Forms.Control.PointToScreen%2A> 方法可轻松完成此操作。</span><span class="sxs-lookup"><span data-stu-id="673af-117">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="673af-118">标准单击事件行为</span><span class="sxs-lookup"><span data-stu-id="673af-118">Standard Click Event Behavior</span></span>

<span data-ttu-id="673af-119">如果想要以正确的顺序处理鼠标单击事件，则需要了解在 Windows 窗体控件中引发的单击事件的顺序。</span><span class="sxs-lookup"><span data-stu-id="673af-119">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="673af-120">当按下鼠标按钮（不论哪个鼠标按钮）并释放时，所有 Windows 窗体控件将以相同的顺序引发单击事件，下表中注明的个别控件除外：</span><span class="sxs-lookup"><span data-stu-id="673af-120">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="673af-121">下表显示单击鼠标按钮所引发事件的顺序：</span><span class="sxs-lookup"><span data-stu-id="673af-121">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="673af-122"><xref:System.Windows.Forms.Control.MouseDown> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-122"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="673af-123"><xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-123"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="673af-124"><xref:System.Windows.Forms.Control.MouseClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-124"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="673af-125"><xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-125"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="673af-126">下面是双击鼠标按钮所引发事件的顺序：</span><span class="sxs-lookup"><span data-stu-id="673af-126">The following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="673af-127"><xref:System.Windows.Forms.Control.MouseDown> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-127"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="673af-128"><xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-128"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="673af-129"><xref:System.Windows.Forms.Control.MouseClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-129"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="673af-130"><xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-130"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="673af-131"><xref:System.Windows.Forms.Control.MouseDown> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-131"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="673af-132"><xref:System.Windows.Forms.Control.DoubleClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-132"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="673af-133">（此顺序可能不同，具体取决于相关控件的 <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> 样式位是否设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="673af-133">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="673af-134">有关如何设置 <xref:System.Windows.Forms.ControlStyles> 位的详细信息，请参阅 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法。）</span><span class="sxs-lookup"><span data-stu-id="673af-134">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="673af-135"><xref:System.Windows.Forms.Control.MouseDoubleClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-135"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="673af-136"><xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-136"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="673af-137">有关演示鼠标单击事件顺序的代码示例，请参阅[如何：处理 Windows 窗体控件中的用户输入事件](how-to-handle-user-input-events-in-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="673af-137">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="673af-138">个别控件</span><span class="sxs-lookup"><span data-stu-id="673af-138">Individual Controls</span></span>

<span data-ttu-id="673af-139">以下控件不符合标准鼠标单击事件行为：</span><span class="sxs-lookup"><span data-stu-id="673af-139">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > <span data-ttu-id="673af-140">对于 <xref:System.Windows.Forms.ComboBox> 控件，如果用户单击编辑字段、按钮或列表中的某个项，将发生稍后详细说明的事件行为。</span><span class="sxs-lookup"><span data-stu-id="673af-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="673af-141">左键单击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="673af-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="673af-142">右键单击：不会引发任何单击事件</span><span class="sxs-lookup"><span data-stu-id="673af-142">Right click: No click events raised</span></span>

  - <span data-ttu-id="673af-143">左键双击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>；<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="673af-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="673af-144">右键双击：不会引发任何单击事件</span><span class="sxs-lookup"><span data-stu-id="673af-144">Right double-click: No click events raised</span></span>

- <span data-ttu-id="673af-145"><xref:System.Windows.Forms.TextBox>、<xref:System.Windows.Forms.RichTextBox>、<xref:System.Windows.Forms.ListBox>、<xref:System.Windows.Forms.MaskedTextBox> 和 <xref:System.Windows.Forms.CheckedListBox> 控件</span><span class="sxs-lookup"><span data-stu-id="673af-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="673af-146">当用户单击这些控件内的任意位置时，将发生稍后详细说明的事件行为。</span><span class="sxs-lookup"><span data-stu-id="673af-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="673af-147">左键单击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="673af-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="673af-148">右键单击：不会引发任何单击事件</span><span class="sxs-lookup"><span data-stu-id="673af-148">Right click: No click events raised</span></span>

  - <span data-ttu-id="673af-149">左键双击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>、<xref:System.Windows.Forms.Control.DoubleClick>、<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="673af-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="673af-150">右键双击：不会引发任何单击事件</span><span class="sxs-lookup"><span data-stu-id="673af-150">Right double-click: No click events raised</span></span>

- <span data-ttu-id="673af-151"><xref:System.Windows.Forms.ListView> 控件</span><span class="sxs-lookup"><span data-stu-id="673af-151"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="673af-152">仅当用户单击 <xref:System.Windows.Forms.ListView> 控件中的项时，才会发生稍后详细说明的事件行为。</span><span class="sxs-lookup"><span data-stu-id="673af-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="673af-153">单击该控件上其他任意位置不会引发任何事件。</span><span class="sxs-lookup"><span data-stu-id="673af-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="673af-154">除了稍后说明的事件外，还有 <xref:System.Windows.Forms.ListView.BeforeLabelEdit> 和 <xref:System.Windows.Forms.ListView.AfterLabelEdit> 事件，如果想要对 <xref:System.Windows.Forms.ListView> 控件进行验证，你可能会对这些事件感兴趣。</span><span class="sxs-lookup"><span data-stu-id="673af-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="673af-155">左键单击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="673af-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="673af-156">右键单击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="673af-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="673af-157">左键双击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>；<xref:System.Windows.Forms.Control.DoubleClick>、<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="673af-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="673af-158">右键双击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>；<xref:System.Windows.Forms.Control.DoubleClick>、<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="673af-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="673af-159"><xref:System.Windows.Forms.TreeView> 控件</span><span class="sxs-lookup"><span data-stu-id="673af-159"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="673af-160">仅当用户单击 <xref:System.Windows.Forms.TreeView> 控件中的项或项的右侧时，才会发生稍后详细说明的事件行为。</span><span class="sxs-lookup"><span data-stu-id="673af-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="673af-161">单击该控件上其他任意位置不会引发任何事件。</span><span class="sxs-lookup"><span data-stu-id="673af-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="673af-162">除了稍后说明的事件，还有 <xref:System.Windows.Forms.TreeView.BeforeCheck>、<xref:System.Windows.Forms.TreeView.BeforeSelect>、<xref:System.Windows.Forms.TreeView.BeforeLabelEdit>、<xref:System.Windows.Forms.TreeView.AfterSelect>、<xref:System.Windows.Forms.TreeView.AfterCheck> 和 <xref:System.Windows.Forms.TreeView.AfterLabelEdit> 事件，如果想要对 <xref:System.Windows.Forms.TreeView> 控件进行验证，你可能会对这些事件感兴趣。</span><span class="sxs-lookup"><span data-stu-id="673af-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="673af-163">左键单击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="673af-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="673af-164">右键单击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="673af-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="673af-165">左键双击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>；<xref:System.Windows.Forms.Control.DoubleClick>、<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="673af-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="673af-166">右键双击：<xref:System.Windows.Forms.Control.Click>、<xref:System.Windows.Forms.Control.MouseClick>；<xref:System.Windows.Forms.Control.DoubleClick>、<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="673af-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="673af-167">切换控件的绘制行为</span><span class="sxs-lookup"><span data-stu-id="673af-167">Painting behavior of toggle controls</span></span>

<span data-ttu-id="673af-168">切换控件（如派生自 <xref:System.Windows.Forms.ButtonBase> 类的控件）具有独特的绘制行为和鼠标单击事件：</span><span class="sxs-lookup"><span data-stu-id="673af-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="673af-169">用户按下鼠标按钮。</span><span class="sxs-lookup"><span data-stu-id="673af-169">The user presses the mouse button.</span></span>

2. <span data-ttu-id="673af-170">控件以按下状态进行绘制。</span><span class="sxs-lookup"><span data-stu-id="673af-170">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="673af-171">引发 <xref:System.Windows.Forms.Control.MouseDown> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="673af-172">用户释放鼠标按钮。</span><span class="sxs-lookup"><span data-stu-id="673af-172">The user releases the mouse button.</span></span>

5. <span data-ttu-id="673af-173">控件以引发状态进行绘制。</span><span class="sxs-lookup"><span data-stu-id="673af-173">The control paints in the raised state.</span></span>

6. <span data-ttu-id="673af-174">引发 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="673af-175">引发 <xref:System.Windows.Forms.Control.MouseClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="673af-176">引发 <xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="673af-177">如果用户在鼠标按钮处于按下状态时将指针移出切换控件（例如在鼠标按下时将鼠标从 <xref:System.Windows.Forms.Button> 控件移出），那么切换控件将以引发状态进行绘制，并且只发生 <xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="673af-178">在这种情况下，将不会发生 <xref:System.Windows.Forms.Control.Click> 或 <xref:System.Windows.Forms.Control.MouseClick> 事件。</span><span class="sxs-lookup"><span data-stu-id="673af-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="673af-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="673af-179">See also</span></span>

- [<span data-ttu-id="673af-180">Windows 窗体应用程序中的鼠标输入</span><span class="sxs-lookup"><span data-stu-id="673af-180">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
