---
title: 使用 UI 自动化公开表的内容
description: 请参阅如何使用 UI 自动化公开表的内容。 表格控件内每个单元格的内容和内部属性都是公开的。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables, exposing content of
- UI Automation, exposing content of tables
- exposing content of tables using UI Automation
ms.assetid: ac3c5eaa-49c7-4653-b83e-532e2a2604a2
ms.openlocfilehash: c6ceb05421547a7e84f612ed6da2bd7002bf095b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168466"
---
# <a name="expose-the-content-of-a-table-using-ui-automation"></a><span data-ttu-id="5ba4f-104">使用 UI 自动化公开表的内容</span><span class="sxs-lookup"><span data-stu-id="5ba4f-104">Expose the Content of a Table Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="5ba4f-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5ba4f-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5ba4f-107">本主题演示如何 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 使用来公开表格控件内每个单元格的内容和内部属性。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-107">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose the content and intrinsic properties of each cell within a tabular control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ba4f-108">示例</span><span class="sxs-lookup"><span data-stu-id="5ba4f-108">Example</span></span>  
 <span data-ttu-id="5ba4f-109">下面的代码示例演示如何获取一个 <xref:System.Windows.Automation.AutomationElement> 表示表格单元格内容的，还可以获得行和列索引、行和列范围等单元格的属性。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-109">The following code example demonstrates how to obtain a <xref:System.Windows.Automation.AutomationElement> that represents the content of a table cell; cell properties such as row and column indices, row and column spans, and row and column header information are also obtained.</span></span> <span data-ttu-id="5ba4f-110">此示例使用焦点更改事件处理程序来模拟实现的表格控件的键盘遍历 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-110">This example uses a focus change event handler to simulate keyboard traversal of a tabular control that implements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="5ba4f-111">针对每个表项的信息将在焦点更改事件上公开。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-111">Information for each table item is exposed on a focus change event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ba4f-112">由于焦点更改是全局桌面事件，因此应筛选表之外的焦点更改事件。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-112">Since focus changes are global desktop events, focus change events outside the table should be filtered.</span></span> <span data-ttu-id="5ba4f-113">有关相关的实现，请参阅[TrackFocus 示例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771428(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-113">See the [TrackFocus Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771428(v=vs.90)) for a related implementation.</span></span>  
  
 [!code-csharp[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#starttarget)]
 [!code-vb[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#starttarget)]  
[!code-csharp[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#gettableelement)]
[!code-vb[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#gettableelement)]  
[!code-csharp[UIATableItemPattern_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#101)]
[!code-vb[UIATableItemPattern_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#101)]  
[!code-csharp[UIATableItemPattern_snip#1015](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#1015)]
[!code-vb[UIATableItemPattern_snip#1015](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#1015)]  
[!code-csharp[UIATableItemPattern_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#102)]
[!code-vb[UIATableItemPattern_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#102)]  
[!code-csharp[UIATableItemPattern_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#103)]
[!code-vb[UIATableItemPattern_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="5ba4f-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ba4f-114">See also</span></span>

- [<span data-ttu-id="5ba4f-115">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="5ba4f-115">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="5ba4f-116">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="5ba4f-116">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="5ba4f-117">实现 UI 自动化 Table 控件模式</span><span class="sxs-lookup"><span data-stu-id="5ba4f-117">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="5ba4f-118">实现 UI 自动化 TableItem 控件模式</span><span class="sxs-lookup"><span data-stu-id="5ba4f-118">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="5ba4f-119">实现 UI 自动化 Grid 控件模式</span><span class="sxs-lookup"><span data-stu-id="5ba4f-119">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="5ba4f-120">实现 UI 自动化 GridItem 控件模式</span><span class="sxs-lookup"><span data-stu-id="5ba4f-120">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
