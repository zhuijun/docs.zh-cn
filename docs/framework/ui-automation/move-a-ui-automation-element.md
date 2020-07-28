---
title: 移动 UI 自动化元素
description: 请参阅示例代码，该代码演示如何将 UI 自动化元素移到指定的屏幕位置。 它使用 WindowPattern 和 TransformPattern 控件模式。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- moving elements
- elements, moving
- UI Automation, moving elements
ms.assetid: 4042cb44-e27e-4a03-ac36-9be1eed65b47
ms.openlocfilehash: 4c8bec4e6d7a241588a3ab261cb80ce9ac242024
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166141"
---
# <a name="move-a-ui-automation-element"></a><span data-ttu-id="25462-104">移动 UI 自动化元素</span><span class="sxs-lookup"><span data-stu-id="25462-104">Move a UI Automation Element</span></span>
> [!NOTE]
> <span data-ttu-id="25462-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="25462-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="25462-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="25462-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="25462-107">此示例演示如何将 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 元素移到指定的屏幕位置。</span><span class="sxs-lookup"><span data-stu-id="25462-107">This example demonstrates how to move a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element to a specified screen location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25462-108">示例</span><span class="sxs-lookup"><span data-stu-id="25462-108">Example</span></span>  
 <span data-ttu-id="25462-109">下面的示例使用 <xref:System.Windows.Automation.WindowPattern> 和 <xref:System.Windows.Automation.TransformPattern> 控件模式以编程方式将 Win32 目标应用程序移到不同的屏幕位置并跟踪 <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent> 。</span><span class="sxs-lookup"><span data-stu-id="25462-109">The following example uses the <xref:System.Windows.Automation.WindowPattern> and <xref:System.Windows.Automation.TransformPattern> control patterns to programmatically move a Win32 target application to discrete screen locations and track the <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent>.</span></span>  
  
 [!code-csharp[WindowMove#1301](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1301)]
 [!code-vb[WindowMove#1301](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1301)]  
[!code-csharp[WindowMove#1300](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1300)]
[!code-vb[WindowMove#1300](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1300)]  
  
## <a name="see-also"></a><span data-ttu-id="25462-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="25462-110">See also</span></span>

- [<span data-ttu-id="25462-111">WindowPattern 示例</span><span class="sxs-lookup"><span data-stu-id="25462-111">WindowPattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/WindowMove)
