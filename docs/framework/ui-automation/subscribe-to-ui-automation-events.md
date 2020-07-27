---
title: 订阅 UI 自动化事件
description: 请参阅如何订阅由 UI 自动化提供程序引发的事件。 示例代码将注册控件时引发的事件的事件处理程序。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
ms.openlocfilehash: 8f456702657c70837c6137e3e60335110361bcd9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163533"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="81d90-104">订阅 UI 自动化事件</span><span class="sxs-lookup"><span data-stu-id="81d90-104">Subscribe to UI Automation Events</span></span>
> [!NOTE]
> <span data-ttu-id="81d90-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="81d90-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="81d90-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="81d90-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="81d90-107">本主题演示如何订阅 UI 自动化提供程序引发的事件。</span><span class="sxs-lookup"><span data-stu-id="81d90-107">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81d90-108">示例</span><span class="sxs-lookup"><span data-stu-id="81d90-108">Example</span></span>  
 <span data-ttu-id="81d90-109">下面的代码示例为调用控件（如按钮）时引发的事件注册事件处理程序，并在应用程序窗体关闭时删除该事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="81d90-109">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="81d90-110">事件由作为参数传递到 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> 的 <xref:System.Windows.Automation.AutomationEvent> 标识。</span><span class="sxs-lookup"><span data-stu-id="81d90-110">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="81d90-111">示例</span><span class="sxs-lookup"><span data-stu-id="81d90-111">Example</span></span>  
 <span data-ttu-id="81d90-112">下面的示例演示如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 来订阅当焦点更改时引发的事件。</span><span class="sxs-lookup"><span data-stu-id="81d90-112">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="81d90-113">事件处理程序将在可在应用程序关闭时调用的方法中注销，或在不再需要 UI 事件通知时注销。</span><span class="sxs-lookup"><span data-stu-id="81d90-113">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="81d90-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="81d90-114">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="81d90-115">UI 自动化事件概述</span><span class="sxs-lookup"><span data-stu-id="81d90-115">UI Automation Events Overview</span></span>](ui-automation-events-overview.md)
