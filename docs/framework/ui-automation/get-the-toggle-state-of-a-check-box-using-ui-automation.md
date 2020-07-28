---
title: 使用 UI 自动化获取复选框的切换状态
description: 请参阅代码示例，该示例演示如何使用 Microsoft UI 自动化获取控件（如复选框）的切换状态。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, getting toggle states of check boxes
- check boxes, getting toggle states of
- getting, toggle states of check boxes
ms.assetid: 84fc31a3-175f-4e93-90a0-dd29d89b77ce
ms.openlocfilehash: 36ec205a572fd6c9e52eec9d2c3e0618ddb0a07b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164144"
---
# <a name="get-the-toggle-state-of-a-check-box-using-ui-automation"></a><span data-ttu-id="cc4b3-103">使用 UI 自动化获取复选框的切换状态</span><span class="sxs-lookup"><span data-stu-id="cc4b3-103">Get the Toggle State of a Check Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="cc4b3-104">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="cc4b3-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cc4b3-105">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="cc4b3-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cc4b3-106">本主题演示如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 来获取控件的切换状态。</span><span class="sxs-lookup"><span data-stu-id="cc4b3-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to get the toggle state of a control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc4b3-107">示例</span><span class="sxs-lookup"><span data-stu-id="cc4b3-107">Example</span></span>  
 <span data-ttu-id="cc4b3-108">此示例使用 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> 类的方法 <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.TogglePattern> 从控件中获取对象，并返回其 <xref:System.Windows.Automation.ToggleState> 属性。</span><span class="sxs-lookup"><span data-stu-id="cc4b3-108">This example uses the <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to obtain a <xref:System.Windows.Automation.TogglePattern> object from a control and return its <xref:System.Windows.Automation.ToggleState> property.</span></span>  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]
