---
title: 使用 UI 自动化查找和突出显示文本
description: 使用 UI 自动化查找和突出显示文本。 示例按顺序在文本控件内容中搜索和突出显示字符串的每个匹配项。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
ms.openlocfilehash: e4aca4b5ccdbc429a3d6267afc09b9f8b99cd7e9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164199"
---
# <a name="find-and-highlight-text-using-ui-automation"></a><span data-ttu-id="f3b7d-104">使用 UI 自动化查找和突出显示文本</span><span class="sxs-lookup"><span data-stu-id="f3b7d-104">Find and Highlight Text Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="f3b7d-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="f3b7d-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f3b7d-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="f3b7d-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f3b7d-107">本主题演示如何使用在文本控件的内容中按顺序搜索和突出显示字符串的每个匹配项 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f3b7d-107">This topic demonstrates how to sequentially search for and highlight each occurrence of a string within the content of a text control using [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3b7d-108">示例</span><span class="sxs-lookup"><span data-stu-id="f3b7d-108">Example</span></span>  
 <span data-ttu-id="f3b7d-109">下面的示例 <xref:System.Windows.Automation.TextPattern> 从文本控件获取对象。</span><span class="sxs-lookup"><span data-stu-id="f3b7d-109">The following example obtains a <xref:System.Windows.Automation.TextPattern> object from a text control.</span></span> <span data-ttu-id="f3b7d-110"><xref:System.Windows.Automation.Text.TextPatternRange>然后，使用此的属性创建一个对象，该对象表示整个文档的文本内容 <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> <xref:System.Windows.Automation.TextPattern> 。</span><span class="sxs-lookup"><span data-stu-id="f3b7d-110">A <xref:System.Windows.Automation.Text.TextPatternRange> object, representing the textual content of the entire document, is then created using the <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> property of this <xref:System.Windows.Automation.TextPattern>.</span></span> <span data-ttu-id="f3b7d-111">然后，将 <xref:System.Windows.Automation.Text.TextPatternRange> 为顺序搜索和突出显示功能创建其他两个对象。</span><span class="sxs-lookup"><span data-stu-id="f3b7d-111">Two additional <xref:System.Windows.Automation.Text.TextPatternRange> objects are then created for the sequential search and highlight functionality.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a><span data-ttu-id="f3b7d-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3b7d-112">See also</span></span>

- [<span data-ttu-id="f3b7d-113">使用 UI 自动化查找和突出显示文本</span><span class="sxs-lookup"><span data-stu-id="f3b7d-113">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
