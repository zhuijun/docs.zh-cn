---
title: 如何：在 FlowLayoutPanel 控件中锚定和停靠子控件
description: 了解如何以编程方式在 Windows 窗体 FlowLayoutPanel 控件中锚定和停靠子控件。
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: b4fb3bf6d148a526a75926bd67c1f967286332bf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174531"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="3bdab-103">如何：在 FlowLayoutPanel 控件中锚定和停靠子控件</span><span class="sxs-lookup"><span data-stu-id="3bdab-103">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>

<span data-ttu-id="3bdab-104"><xref:System.Windows.Forms.FlowLayoutPanel> 控件支持其子控件中的 <xref:System.Windows.Forms.Control.Anchor%2A> 和 <xref:System.Windows.Forms.Control.Dock%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="3bdab-104">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="3bdab-105">在 FlowLayoutPanel 控件中锚定和停靠子控件</span><span class="sxs-lookup"><span data-stu-id="3bdab-105">To anchor and dock child controls in a FlowLayoutPanel control</span></span>

1. <span data-ttu-id="3bdab-106">在窗体上创建一个 <xref:System.Windows.Forms.FlowLayoutPanel> 控件。</span><span class="sxs-lookup"><span data-stu-id="3bdab-106">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>

2. <span data-ttu-id="3bdab-107">将 <xref:System.Windows.Forms.Control.Width%2A> 控件的设置 <xref:System.Windows.Forms.FlowLayoutPanel> 为**300**，并将其设置 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 为 <xref:System.Windows.Forms.FlowDirection.TopDown> 。</span><span class="sxs-lookup"><span data-stu-id="3bdab-107">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

3. <span data-ttu-id="3bdab-108">创建两个 <xref:System.Windows.Forms.Button> 控件，并将它们放入 <xref:System.Windows.Forms.FlowLayoutPanel> 控件中。</span><span class="sxs-lookup"><span data-stu-id="3bdab-108">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

4. <span data-ttu-id="3bdab-109">将 <xref:System.Windows.Forms.Control.Width%2A> 第一个按钮的设置为**200**。</span><span class="sxs-lookup"><span data-stu-id="3bdab-109">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>

5. <span data-ttu-id="3bdab-110">将第二个按钮的 <xref:System.Windows.Forms.Control.Dock%2A> 属性设置为 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="3bdab-110">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3bdab-111">第二个按钮采用与第一个按钮相同的宽度。</span><span class="sxs-lookup"><span data-stu-id="3bdab-111">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="3bdab-112">它不在 <xref:System.Windows.Forms.FlowLayoutPanel> 控件的宽度范围内拉伸。</span><span class="sxs-lookup"><span data-stu-id="3bdab-112">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="3bdab-113">将第二个按钮的 <xref:System.Windows.Forms.Control.Dock%2A> 属性设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="3bdab-113">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="3bdab-114">这将导致该按钮采用其原始的宽度。</span><span class="sxs-lookup"><span data-stu-id="3bdab-114">This causes the button to assume its original width.</span></span>

7. <span data-ttu-id="3bdab-115">将第二个按钮的 <xref:System.Windows.Forms.Control.Anchor%2A> 属性设置为 `Left, Right`。</span><span class="sxs-lookup"><span data-stu-id="3bdab-115">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3bdab-116">第二个按钮采用与第一个按钮相同的宽度。</span><span class="sxs-lookup"><span data-stu-id="3bdab-116">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="3bdab-117">它不在 <xref:System.Windows.Forms.FlowLayoutPanel> 控件的宽度范围内拉伸。</span><span class="sxs-lookup"><span data-stu-id="3bdab-117">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="3bdab-118">这是在 <xref:System.Windows.Forms.FlowLayoutPanel> 控件中锚定和停靠的一般规则：对于垂直流方向，<xref:System.Windows.Forms.FlowLayoutPanel> 控件计算列中最宽子控件的隐含列的宽度。</span><span class="sxs-lookup"><span data-stu-id="3bdab-118">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="3bdab-119">对齐或拉伸此列中具有 <xref:System.Windows.Forms.Control.Anchor%2A> 或 <xref:System.Windows.Forms.Control.Dock%2A> 属性的所有其他控件以适合此隐含列。</span><span class="sxs-lookup"><span data-stu-id="3bdab-119">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="3bdab-120">该行为以相似的方式在水平流方向工作。</span><span class="sxs-lookup"><span data-stu-id="3bdab-120">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="3bdab-121"><xref:System.Windows.Forms.FlowLayoutPanel> 控件计算行中最高子控件的隐含行的高度，并对齐此行中所有停靠的或锚定的子控件或调整其大小以适应隐含行。</span><span class="sxs-lookup"><span data-stu-id="3bdab-121">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>

## <a name="example"></a><span data-ttu-id="3bdab-122">示例</span><span class="sxs-lookup"><span data-stu-id="3bdab-122">Example</span></span>

<span data-ttu-id="3bdab-123">下图显示了四个按钮，它们相对于 <xref:System.Windows.Forms.FlowLayoutPanel> 中的蓝色按钮锚定和停靠。</span><span class="sxs-lookup"><span data-stu-id="3bdab-123">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="3bdab-124"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 为 <xref:System.Windows.Forms.FlowDirection.LeftToRight>。</span><span class="sxs-lookup"><span data-stu-id="3bdab-124">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>

<span data-ttu-id="3bdab-125">![FlowLayoutPanel 锚定](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="3bdab-125">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>

<span data-ttu-id="3bdab-126">下图显示了四个按钮，它们相对于 <xref:System.Windows.Forms.FlowLayoutPanel> 中的蓝色按钮锚定和停靠。</span><span class="sxs-lookup"><span data-stu-id="3bdab-126">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="3bdab-127"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 为 <xref:System.Windows.Forms.FlowDirection.TopDown>。</span><span class="sxs-lookup"><span data-stu-id="3bdab-127">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

<span data-ttu-id="3bdab-128">![FlowLayoutPanel 锚定](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="3bdab-128">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>

<span data-ttu-id="3bdab-129">以下代码示例演示了 <xref:System.Windows.Forms.FlowLayoutPanel> 控件中 <xref:System.Windows.Forms.Button> 控件的各种 <xref:System.Windows.Forms.Control.Anchor%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="3bdab-129">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a><span data-ttu-id="3bdab-130">编译代码</span><span class="sxs-lookup"><span data-stu-id="3bdab-130">Compiling the Code</span></span>

<span data-ttu-id="3bdab-131">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="3bdab-131">This example requires:</span></span>

- <span data-ttu-id="3bdab-132">对 System、System.Data、System.Drawing 和 System.Windows.Forms 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="3bdab-132">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bdab-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3bdab-133">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="3bdab-134">FlowLayoutPanel 控件概述</span><span class="sxs-lookup"><span data-stu-id="3bdab-134">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
