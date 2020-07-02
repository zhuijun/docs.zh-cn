---
title: 如何：在设计时为 Windows 窗体上的控件设置 ToolTip
description: 了解如何以编程方式或在 Visual Studio 的 Windows 窗体设计器中设置控件的工具提示。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 144ba5b6bffb4a538e345f7b2df4a453fc6fd63d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618020"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="a3787-103">如何：在设计时在 Windows 窗体上设置控件的工具提示</span><span class="sxs-lookup"><span data-stu-id="a3787-103">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="a3787-104">可以 <xref:System.Windows.Forms.ToolTip> 在代码中或在 Visual Studio 的 Windows 窗体设计器中设置字符串。</span><span class="sxs-lookup"><span data-stu-id="a3787-104">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="a3787-105">有关组件的详细信息 <xref:System.Windows.Forms.ToolTip> ，请参阅[ToolTip 组件概述](tooltip-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="a3787-105">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="a3787-106">以编程方式设置工具提示</span><span class="sxs-lookup"><span data-stu-id="a3787-106">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="a3787-107">添加将显示工具提示的控件。</span><span class="sxs-lookup"><span data-stu-id="a3787-107">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="a3787-108">使用 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 组件的方法 <xref:System.Windows.Forms.ToolTip> 。</span><span class="sxs-lookup"><span data-stu-id="a3787-108">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

    ```vb
    ' In this example, Button1 is the control to display the ToolTip.
    ToolTip1.SetToolTip(Button1, "Save changes")
    ```

    ```csharp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1.SetToolTip(button1, "Save changes");
    ```

    ```cpp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1->SetToolTip(button1, "Save changes");
    ```

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="a3787-109">在设计器中设置工具提示</span><span class="sxs-lookup"><span data-stu-id="a3787-109">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="a3787-110">在 Visual Studio 中，将 <xref:System.Windows.Forms.ToolTip> 组件添加到窗体。</span><span class="sxs-lookup"><span data-stu-id="a3787-110">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="a3787-111">选择将显示工具提示的控件，或将其添加到窗体中。</span><span class="sxs-lookup"><span data-stu-id="a3787-111">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="a3787-112">在 "**属性**" 窗口中，将 " **ToolTip1 上的工具提示**" 设置为适当的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="a3787-112">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="a3787-113">以编程方式删除工具提示</span><span class="sxs-lookup"><span data-stu-id="a3787-113">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="a3787-114">使用 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 组件的方法 <xref:System.Windows.Forms.ToolTip> 。</span><span class="sxs-lookup"><span data-stu-id="a3787-114">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

    ```vb
    ' In this example, Button1 is the control displaying the ToolTip.
    ToolTip1.SetToolTip(Button1, Nothing)
    ```

    ```csharp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1.SetToolTip(button1, null);
    ```

    ```cpp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1->SetToolTip(button1, NULL);
    ```

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="a3787-115">在设计器中删除工具提示</span><span class="sxs-lookup"><span data-stu-id="a3787-115">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="a3787-116">在 Visual Studio 中，选择显示工具提示的控件。</span><span class="sxs-lookup"><span data-stu-id="a3787-116">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="a3787-117">在 "**属性**" 窗口中，删除**ToolTip1 上的工具提示**中的文本。</span><span class="sxs-lookup"><span data-stu-id="a3787-117">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3787-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="a3787-118">See also</span></span>

- [<span data-ttu-id="a3787-119">ToolTip 组件概述</span><span class="sxs-lookup"><span data-stu-id="a3787-119">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="a3787-120">如何：更改 Windows 窗体 ToolTip 组件的延迟</span><span class="sxs-lookup"><span data-stu-id="a3787-120">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="a3787-121">ToolTip 组件</span><span class="sxs-lookup"><span data-stu-id="a3787-121">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
