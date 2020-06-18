---
title: 使用 UI 自动化获取混合文本特性的详细信息
description: 使用 .NET API 的 System.web 命名空间中的托管 UI 自动化类获取混合文本特性详细信息。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 111d110be9365c4a58f2bd2b033c1ff4e3a6a95d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903852"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a><span data-ttu-id="da7d7-103">使用 UI 自动化获取混合文本特性的详细信息</span><span class="sxs-lookup"><span data-stu-id="da7d7-103">Obtain Mixed Text Attribute Details Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="da7d7-104">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="da7d7-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="da7d7-105">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="da7d7-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="da7d7-106">本主题展示如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 从跨多个特性值的文本范围获取文本特性详细信息。</span><span class="sxs-lookup"><span data-stu-id="da7d7-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values.</span></span> <span data-ttu-id="da7d7-107">文本范围可以与文档、连续选择的文本、非连续选择的文本集合或文档的整个文本内容中的插入符号的当前位置相对应（或使选择范围退化）。</span><span class="sxs-lookup"><span data-stu-id="da7d7-107">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da7d7-108">示例</span><span class="sxs-lookup"><span data-stu-id="da7d7-108">Example</span></span>  
 <span data-ttu-id="da7d7-109">下面的代码示例演示如何从一个文本范围内获取 <xref:System.Windows.Automation.TextPattern.FontNameAttribute> ，其中 <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> 返回 <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> 对象。</span><span class="sxs-lookup"><span data-stu-id="da7d7-109">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.</span></span>  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <span data-ttu-id="da7d7-110">与 <xref:System.Windows.Automation.TextPattern> 类结合使用时， <xref:System.Windows.Automation.Text.TextPatternRange> 控件模式支持基本的文本特性、属性和方法。</span><span class="sxs-lookup"><span data-stu-id="da7d7-110">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="da7d7-111">对于不受 <xref:System.Windows.Automation.TextPattern> 或 <xref:System.Windows.Automation.Text.TextPatternRange>支持的特定于控件的功能， <xref:System.Windows.Automation.AutomationElement> 类为 UI 自动化客户端提供用于访问对应的本机对象模型的方法。</span><span class="sxs-lookup"><span data-stu-id="da7d7-111">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da7d7-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da7d7-112">See also</span></span>

- [<span data-ttu-id="da7d7-113">UI 自动化 TextPattern 概述</span><span class="sxs-lookup"><span data-stu-id="da7d7-113">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="da7d7-114">使用 UI 自动化向文本框添加内容</span><span class="sxs-lookup"><span data-stu-id="da7d7-114">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="da7d7-115">使用 UI 自动化查找和突出显示文本</span><span class="sxs-lookup"><span data-stu-id="da7d7-115">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="da7d7-116">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="da7d7-116">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="da7d7-117">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="da7d7-117">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="da7d7-118">使用 UI 自动化获取文本特性</span><span class="sxs-lookup"><span data-stu-id="da7d7-118">Obtain Text Attributes Using UI Automation</span></span>](obtain-text-attributes-using-ui-automation.md)
