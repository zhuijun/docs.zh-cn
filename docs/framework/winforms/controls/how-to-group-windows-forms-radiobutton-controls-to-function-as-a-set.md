---
title: 将单选按钮控件作为一个集进行分组
description: 了解如何对 Windows 窗体单选按钮控件进行分组，以便独立于其他集工作。
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325920"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="f5c92-103">如何：按功能分组 Windows 窗体 RadioButton 控件</span><span class="sxs-lookup"><span data-stu-id="f5c92-103">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="f5c92-104">Windows 窗体 <xref:System.Windows.Forms.RadioButton> 控件旨在为用户选择两个或多个设置，只能将其中一个设置分配给过程或对象。</span><span class="sxs-lookup"><span data-stu-id="f5c92-104">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="f5c92-105">例如，一组 <xref:System.Windows.Forms.RadioButton> 控件可以针对订单显示包托架的选择，但将仅使用其中一个运营商。</span><span class="sxs-lookup"><span data-stu-id="f5c92-105">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="f5c92-106">因此 <xref:System.Windows.Forms.RadioButton> ，一次只能选择一个，即使它是功能组的一部分也是如此。</span><span class="sxs-lookup"><span data-stu-id="f5c92-106">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="f5c92-107">可以通过在容器（如 <xref:System.Windows.Forms.Panel> 控件、 <xref:System.Windows.Forms.GroupBox> 控件或窗体）中绘制单选按钮来对其进行分组。</span><span class="sxs-lookup"><span data-stu-id="f5c92-107">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="f5c92-108">直接添加到窗体中的所有单选按钮都将成为一个组。</span><span class="sxs-lookup"><span data-stu-id="f5c92-108">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="f5c92-109">若要添加单独的组，则必须将它们放在面板或组框中。</span><span class="sxs-lookup"><span data-stu-id="f5c92-109">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="f5c92-110">有关面板或分组框的详细信息，请参阅[Panel 控件概述](panel-control-overview-windows-forms.md)或[分组框控件概述](groupbox-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="f5c92-110">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="f5c92-111">将单选按钮控件分组为独立于其他集的功能</span><span class="sxs-lookup"><span data-stu-id="f5c92-111">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="f5c92-112">从 " <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> **工具箱**" 的 " **Windows 窗体**" 选项卡中将或控件拖到窗体上。</span><span class="sxs-lookup"><span data-stu-id="f5c92-112">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="f5c92-113"><xref:System.Windows.Forms.RadioButton>在或控件上绘制控件 <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> 。</span><span class="sxs-lookup"><span data-stu-id="f5c92-113">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c92-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5c92-114">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="f5c92-115">RadioButton 控件概述</span><span class="sxs-lookup"><span data-stu-id="f5c92-115">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="f5c92-116">Panel 控件概述</span><span class="sxs-lookup"><span data-stu-id="f5c92-116">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="f5c92-117">GroupBox 控件概述</span><span class="sxs-lookup"><span data-stu-id="f5c92-117">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="f5c92-118">CheckBox 控件概述</span><span class="sxs-lookup"><span data-stu-id="f5c92-118">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="f5c92-119">RadioButton 控件</span><span class="sxs-lookup"><span data-stu-id="f5c92-119">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
