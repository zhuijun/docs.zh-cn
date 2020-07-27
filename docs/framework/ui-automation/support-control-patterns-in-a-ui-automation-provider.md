---
title: 在 UI 自动化提供程序中支持控件模式
description: 了解如何在 UI 自动化提供程序上实现支持控件模式，以便客户端应用程序可以操作控件并从中获取数据。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: 82300499520be6b820b361ebdeb56bbf3716afab
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163507"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="60d1e-103">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="60d1e-103">Support Control Patterns in a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="60d1e-104">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="60d1e-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="60d1e-105">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="60d1e-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="60d1e-106">本主题演示如何在 UI 自动化提供程序上实现一个或多个控件模式，以便客户端应用程序可以操作控件并从中获取数据。</span><span class="sxs-lookup"><span data-stu-id="60d1e-106">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>

## <a name="support-control-patterns"></a><span data-ttu-id="60d1e-107">支持控件模式</span><span class="sxs-lookup"><span data-stu-id="60d1e-107">Support Control Patterns</span></span>

1. <span data-ttu-id="60d1e-108">为元素应支持的控件模式实现相应的接口，例如为 为 <xref:System.Windows.Automation.Provider.IInvokeProvider> 实现 <xref:System.Windows.Automation.InvokePattern>。</span><span class="sxs-lookup"><span data-stu-id="60d1e-108">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>

2. <span data-ttu-id="60d1e-109">返回包含 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>实现中每个控件接口的实现的对象</span><span class="sxs-lookup"><span data-stu-id="60d1e-109">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>

## <a name="example"></a><span data-ttu-id="60d1e-110">示例</span><span class="sxs-lookup"><span data-stu-id="60d1e-110">Example</span></span>

<span data-ttu-id="60d1e-111">下面的示例演示了对单项选择自定义列表框实现 <xref:System.Windows.Automation.Provider.ISelectionProvider> 。</span><span class="sxs-lookup"><span data-stu-id="60d1e-111">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="60d1e-112">它返回三个属性并获取当前所选的项。</span><span class="sxs-lookup"><span data-stu-id="60d1e-112">It returns three properties and gets the currently selected item.</span></span>

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a><span data-ttu-id="60d1e-113">示例</span><span class="sxs-lookup"><span data-stu-id="60d1e-113">Example</span></span>

<span data-ttu-id="60d1e-114">下面的示例演示了返回实现 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> 的类的 <xref:System.Windows.Automation.Provider.ISelectionProvider>的实现。</span><span class="sxs-lookup"><span data-stu-id="60d1e-114">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="60d1e-115">大多数列表框控件还支持其他模式，但在此示例中，为 `Nothing` 所有其他模式标识符返回了 null 引用（在 Microsoft Visual Basic .net 中）。</span><span class="sxs-lookup"><span data-stu-id="60d1e-115">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a><span data-ttu-id="60d1e-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60d1e-116">See also</span></span>

- [<span data-ttu-id="60d1e-117">UI 自动化提供程序概述</span><span class="sxs-lookup"><span data-stu-id="60d1e-117">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="60d1e-118">服务器端 UI 自动化提供程序的实现</span><span class="sxs-lookup"><span data-stu-id="60d1e-118">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
