---
title: 从 UI 自动化提供程序中引发事件
description: 请参阅演示如何从 UI 自动化提供程序引发事件的示例。 它在自定义按钮控件的实现中引发 UI 自动化事件。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 75af4d05172e2417d44f76beab486de5eb3a4ba7
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168108"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="9a6a7-104">从 UI 自动化提供程序中引发事件</span><span class="sxs-lookup"><span data-stu-id="9a6a7-104">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="9a6a7-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9a6a7-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="9a6a7-107">本主题包含演示如何从 UI 自动化提供程序中引发事件的代码示例。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-107">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a6a7-108">示例</span><span class="sxs-lookup"><span data-stu-id="9a6a7-108">Example</span></span>  
 <span data-ttu-id="9a6a7-109">下面的示例在自定义按钮控件的实现中引发了 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-109">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="9a6a7-110">该实现使 UI 自动化客户端应用程序能够模拟按钮单击。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-110">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="9a6a7-111">若要避免不必要的处理，示例将检查 <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> 以确定是否应引发事件。</span><span class="sxs-lookup"><span data-stu-id="9a6a7-111">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="9a6a7-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a6a7-112">See also</span></span>

- [<span data-ttu-id="9a6a7-113">UI 自动化提供程序概述</span><span class="sxs-lookup"><span data-stu-id="9a6a7-113">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
