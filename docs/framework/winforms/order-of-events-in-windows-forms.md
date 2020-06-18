---
title: 事件顺序
description: 了解有关应用程序和控件生存期内几个重要阶段 Windows 窗体中的事件顺序的详细信息。
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: b16d544d11500b2c684e87a915fc4b8eec071faa
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904333"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="e7da0-103">Windows 窗体中的事件顺序</span><span class="sxs-lookup"><span data-stu-id="e7da0-103">Order of Events in Windows Forms</span></span>
<span data-ttu-id="e7da0-104">对于依次处理其中每个事件的开发人员，Windows 窗体应用程序中引发事件的顺序非常具有吸引力。</span><span class="sxs-lookup"><span data-stu-id="e7da0-104">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="e7da0-105">当出现需要谨慎处理事件的情况时（例如，在重绘窗体的某些部件时），有必要了解运行时引发事件的确切顺序。</span><span class="sxs-lookup"><span data-stu-id="e7da0-105">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="e7da0-106">本主题提供了应用程序和控件的生存期中几个重要阶段中的事件顺序的详细信息。</span><span class="sxs-lookup"><span data-stu-id="e7da0-106">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="e7da0-107">有关鼠标输入事件顺序的特定详细信息，请参阅[中的鼠标事件 Windows 窗体](mouse-events-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e7da0-107">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="e7da0-108">有关 Windows 窗体中事件的概述，请参阅[事件概述](events-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e7da0-108">For an overview of events in Windows Forms, see [Events Overview](events-overview-windows-forms.md).</span></span> <span data-ttu-id="e7da0-109">有关事件处理程序的构成的详细信息，请参阅[事件处理程序概述](event-handlers-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e7da0-109">For details about the makeup of event handlers, see [Event Handlers Overview](event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="e7da0-110">应用程序启动和关闭事件</span><span class="sxs-lookup"><span data-stu-id="e7da0-110">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="e7da0-111"><xref:System.Windows.Forms.Form> 和 <xref:System.Windows.Forms.Control> 类公开一组与应用程序启动和关闭相关的事件。</span><span class="sxs-lookup"><span data-stu-id="e7da0-111">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="e7da0-112">Windows 窗体应用程序启动时，主窗体的启动事件将按照以下顺序引发：</span><span class="sxs-lookup"><span data-stu-id="e7da0-112">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="e7da0-113">应用程序关闭时，主窗体的关闭事件将按照以下顺序引发：</span><span class="sxs-lookup"><span data-stu-id="e7da0-113">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="e7da0-114">在主窗体关闭事件后，将引发 <xref:System.Windows.Forms.Application> 类的 <xref:System.Windows.Forms.Application.ApplicationExit> 事件。</span><span class="sxs-lookup"><span data-stu-id="e7da0-114">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7da0-115">Visual Basic 2005 包括其他应用程序事件，例如 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> 和 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e7da0-115">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="e7da0-116">焦点和验证事件</span><span class="sxs-lookup"><span data-stu-id="e7da0-116">Focus and Validation Events</span></span>  
 <span data-ttu-id="e7da0-117">当通过使用键盘（TAB、SHIFT+TAB 等），通过调用 <xref:System.Windows.Forms.Control.Select%2A> 或 <xref:System.Windows.Forms.Control.SelectNextControl%2A> 方法，或通过将 <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> 属性设置为当前窗体来更改焦点时，<xref:System.Windows.Forms.Control> 类的焦点事件将按以下顺序发生：</span><span class="sxs-lookup"><span data-stu-id="e7da0-117">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="e7da0-118">当通过使用鼠标或调用 <xref:System.Windows.Forms.Control.Focus%2A> 方法更改焦点时，<xref:System.Windows.Forms.Control> 类的焦点事件将按以下顺序发生：</span><span class="sxs-lookup"><span data-stu-id="e7da0-118">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="e7da0-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7da0-119">See also</span></span>

- [<span data-ttu-id="e7da0-120">在 Windows 窗体中创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="e7da0-120">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
