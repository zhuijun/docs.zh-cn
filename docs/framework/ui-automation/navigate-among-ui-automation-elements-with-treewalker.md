---
title: 使用 TreeWalker 在 UI 自动化元素之间导航
description: 请参阅代码示例，该示例演示如何使用 TreeWalker 类在 UI 自动化元素之间导航。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: e1784862433083f15d600ea2ec39aee2323bbd12
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168024"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="95965-103">使用 TreeWalker 在 UI 自动化元素之间导航</span><span class="sxs-lookup"><span data-stu-id="95965-103">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
> <span data-ttu-id="95965-104">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="95965-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="95965-105">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="95965-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="95965-106">本主题包含示例代码，该代码演示如何 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 使用类在元素间导航 <xref:System.Windows.Automation.TreeWalker> 。</span><span class="sxs-lookup"><span data-stu-id="95965-106">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95965-107">示例</span><span class="sxs-lookup"><span data-stu-id="95965-107">Example</span></span>  
 <span data-ttu-id="95965-108">下面的示例使用 <xref:System.Windows.Automation.TreeWalker.GetParent%2A> 遍历 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 树，直到它找到根元素或桌面。</span><span class="sxs-lookup"><span data-stu-id="95965-108">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="95965-109">紧靠下面的元素，它是指定元素的父窗口。</span><span class="sxs-lookup"><span data-stu-id="95965-109">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="95965-110">示例</span><span class="sxs-lookup"><span data-stu-id="95965-110">Example</span></span>  
 <span data-ttu-id="95965-111">下面的示例使用 <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> 和 <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> 创建 <xref:System.Windows.Forms.TreeView> ，它显示 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 控件视图中的元素的整个子树以及已启用的子树。</span><span class="sxs-lookup"><span data-stu-id="95965-111">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="95965-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95965-112">See also</span></span>

- [<span data-ttu-id="95965-113">获取 UI 自动化元素</span><span class="sxs-lookup"><span data-stu-id="95965-113">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
