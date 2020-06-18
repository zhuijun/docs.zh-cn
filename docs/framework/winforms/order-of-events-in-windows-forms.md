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
# <a name="order-of-events-in-windows-forms"></a>Windows 窗体中的事件顺序
对于依次处理其中每个事件的开发人员，Windows 窗体应用程序中引发事件的顺序非常具有吸引力。 当出现需要谨慎处理事件的情况时（例如，在重绘窗体的某些部件时），有必要了解运行时引发事件的确切顺序。 本主题提供了应用程序和控件的生存期中几个重要阶段中的事件顺序的详细信息。 有关鼠标输入事件顺序的特定详细信息，请参阅[中的鼠标事件 Windows 窗体](mouse-events-in-windows-forms.md)。 有关 Windows 窗体中事件的概述，请参阅[事件概述](events-overview-windows-forms.md)。 有关事件处理程序的构成的详细信息，请参阅[事件处理程序概述](event-handlers-overview-windows-forms.md)。  
  
## <a name="application-startup-and-shutdown-events"></a>应用程序启动和关闭事件  
 <xref:System.Windows.Forms.Form> 和 <xref:System.Windows.Forms.Control> 类公开一组与应用程序启动和关闭相关的事件。 Windows 窗体应用程序启动时，主窗体的启动事件将按照以下顺序引发：  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 应用程序关闭时，主窗体的关闭事件将按照以下顺序引发：  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 在主窗体关闭事件后，将引发 <xref:System.Windows.Forms.Application> 类的 <xref:System.Windows.Forms.Application.ApplicationExit> 事件。  
  
> [!NOTE]
> Visual Basic 2005 包括其他应用程序事件，例如 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> 和 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>。  
  
## <a name="focus-and-validation-events"></a>焦点和验证事件  
 当通过使用键盘（TAB、SHIFT+TAB 等），通过调用 <xref:System.Windows.Forms.Control.Select%2A> 或 <xref:System.Windows.Forms.Control.SelectNextControl%2A> 方法，或通过将 <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> 属性设置为当前窗体来更改焦点时，<xref:System.Windows.Forms.Control> 类的焦点事件将按以下顺序发生：  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 当通过使用鼠标或调用 <xref:System.Windows.Forms.Control.Focus%2A> 方法更改焦点时，<xref:System.Windows.Forms.Control> 类的焦点事件将按以下顺序发生：  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>另请参阅

- [在 Windows 窗体中创建事件处理程序](creating-event-handlers-in-windows-forms.md)
