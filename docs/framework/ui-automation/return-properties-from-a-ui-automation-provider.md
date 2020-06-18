---
title: 从 UI 自动化提供程序返回属性
description: 了解 UI 自动化提供程序如何才能将元素的属性返回到 .NET 中的客户端应用程序。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
ms.openlocfilehash: 14a42c73d1dfb942a7e60ce7a72c3a5aea2b820c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903827"
---
# <a name="return-properties-from-a-ui-automation-provider"></a><span data-ttu-id="4f3ee-103">从 UI 自动化提供程序返回属性</span><span class="sxs-lookup"><span data-stu-id="4f3ee-103">Return Properties from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="4f3ee-104">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="4f3ee-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4f3ee-105">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="4f3ee-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="4f3ee-106">本主题包含显示 UI 自动化提供程序如何才能将元素的属性返回到客户端应用程序的示例代码。</span><span class="sxs-lookup"><span data-stu-id="4f3ee-106">This topic contains sample code that shows how a UI Automation provider can return properties of an element to client applications.</span></span>  
  
 <span data-ttu-id="4f3ee-107">对于不显式支持的任何属性，则提供程序必须返回 `null` （Visual Basic 中为`Nothing` ）。</span><span class="sxs-lookup"><span data-stu-id="4f3ee-107">For any property it does not explicitly support, the provider must return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="4f3ee-108">这样可确保 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 试图获取来自另一个源（如宿主窗口提供程序）的属性。</span><span class="sxs-lookup"><span data-stu-id="4f3ee-108">This ensures that [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] attempts to obtain the property from another source, such as the host window provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f3ee-109">示例</span><span class="sxs-lookup"><span data-stu-id="4f3ee-109">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="4f3ee-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f3ee-110">See also</span></span>

- [<span data-ttu-id="4f3ee-111">UI 自动化提供程序概述</span><span class="sxs-lookup"><span data-stu-id="4f3ee-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="4f3ee-112">服务器端 UI 自动化提供程序的实现</span><span class="sxs-lookup"><span data-stu-id="4f3ee-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
