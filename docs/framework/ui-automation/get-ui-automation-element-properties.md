---
title: 获取 UI 自动化元素的属性
description: 请参阅说明和一个示例，其中演示了如何检索 UI 自动化元素的当前或缓存的属性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 277822c9d89046bfbad50df16bce83da7dd45b3b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164103"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="9d2c7-103">获取 UI 自动化元素的属性</span><span class="sxs-lookup"><span data-stu-id="9d2c7-103">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="9d2c7-104">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="9d2c7-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9d2c7-105">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="9d2c7-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="9d2c7-106">本主题说明如何检索元素的属性 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9d2c7-106">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="9d2c7-107">获取当前属性值</span><span class="sxs-lookup"><span data-stu-id="9d2c7-107">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="9d2c7-108">获取要 <xref:System.Windows.Automation.AutomationElement> 获取其属性的。</span><span class="sxs-lookup"><span data-stu-id="9d2c7-108">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="9d2c7-109">调用 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> 或检索 <xref:System.Windows.Automation.AutomationElement.Current%2A> 属性结构，并从其成员之一获取值。</span><span class="sxs-lookup"><span data-stu-id="9d2c7-109">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="9d2c7-110">获取缓存的属性值</span><span class="sxs-lookup"><span data-stu-id="9d2c7-110">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="9d2c7-111">获取要 <xref:System.Windows.Automation.AutomationElement> 获取其属性的。</span><span class="sxs-lookup"><span data-stu-id="9d2c7-111">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="9d2c7-112">必须已在中指定了属性 <xref:System.Windows.Automation.CacheRequest> 。</span><span class="sxs-lookup"><span data-stu-id="9d2c7-112">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="9d2c7-113">调用 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> 或检索 <xref:System.Windows.Automation.AutomationElement.Cached%2A> 属性结构，并从其成员之一获取值。</span><span class="sxs-lookup"><span data-stu-id="9d2c7-113">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d2c7-114">示例</span><span class="sxs-lookup"><span data-stu-id="9d2c7-114">Example</span></span>  
 <span data-ttu-id="9d2c7-115">下面的示例演示了检索的当前属性的各种方法 <xref:System.Windows.Automation.AutomationElement> 。</span><span class="sxs-lookup"><span data-stu-id="9d2c7-115">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="9d2c7-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="9d2c7-116">See also</span></span>

- [<span data-ttu-id="9d2c7-117">客户端的 UI 自动化属性</span><span class="sxs-lookup"><span data-stu-id="9d2c7-117">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="9d2c7-118">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="9d2c7-118">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="9d2c7-119">在 UI 自动化客户端中缓存</span><span class="sxs-lookup"><span data-stu-id="9d2c7-119">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
