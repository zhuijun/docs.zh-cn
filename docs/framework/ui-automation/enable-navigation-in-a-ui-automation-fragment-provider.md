---
title: 在 UI 自动化片段提供程序中启用导航
description: 阅读一个示例，该示例演示如何在 UI 自动化提供程序中为片段中的元素启用导航。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: bf9e43e9d70b9191fba93e5efa4eae544196c735
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168489"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="f726e-103">在 UI 自动化片段提供程序中启用导航</span><span class="sxs-lookup"><span data-stu-id="f726e-103">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
> <span data-ttu-id="f726e-104">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="f726e-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f726e-105">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="f726e-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f726e-106">本主题包含示例代码，该示例代码演示如何为片段中的元素启用在 UI 自动化提供程序中导航的功能。</span><span class="sxs-lookup"><span data-stu-id="f726e-106">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f726e-107">示例</span><span class="sxs-lookup"><span data-stu-id="f726e-107">Example</span></span>  
 <span data-ttu-id="f726e-108">下面的示例代码为列表中的列表项实现 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A></span><span class="sxs-lookup"><span data-stu-id="f726e-108">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="f726e-109">父元素是列表框元素，且同级元素是列表集合中的其他项。</span><span class="sxs-lookup"><span data-stu-id="f726e-109">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="f726e-110">对于无效的方向，该方法返回 `null` （在 Visual Basic 中则返回`Nothing` ）；在本例中，将返回 <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> 和 <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>，因为该元素没有任何子级。</span><span class="sxs-lookup"><span data-stu-id="f726e-110">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="f726e-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f726e-111">See also</span></span>

- [<span data-ttu-id="f726e-112">UI 自动化提供程序概述</span><span class="sxs-lookup"><span data-stu-id="f726e-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="f726e-113">服务器端 UI 自动化提供程序的实现</span><span class="sxs-lookup"><span data-stu-id="f726e-113">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
