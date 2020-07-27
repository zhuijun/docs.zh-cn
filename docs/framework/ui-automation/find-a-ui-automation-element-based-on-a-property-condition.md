---
title: 基于属性条件查找 UI 自动化元素
description: 基于属性条件查找 UI 自动化元素。 根据特定属性或属性，在 UI 自动化树中查找元素。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 5e5fa4fde9049bd87b2722fa9b7d084d96ff6f42
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168440"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="de673-104">基于属性条件查找 UI 自动化元素</span><span class="sxs-lookup"><span data-stu-id="de673-104">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
> <span data-ttu-id="de673-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="de673-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="de673-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="de673-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="de673-107">本主题包含示例代码，该代码演示如何 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 基于特定属性在树中查找元素。</span><span class="sxs-lookup"><span data-stu-id="de673-107">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de673-108">示例</span><span class="sxs-lookup"><span data-stu-id="de673-108">Example</span></span>  
 <span data-ttu-id="de673-109">在下面的示例中，指定了一组属性条件，这些条件标识树中感兴趣的某个元素（或元素） <xref:System.Windows.Automation.AutomationElement> 。</span><span class="sxs-lookup"><span data-stu-id="de673-109">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="de673-110">然后，将使用合并一系列布尔操作的方法对所有匹配元素执行搜索， <xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AndCondition> 以限制匹配元素的数目。</span><span class="sxs-lookup"><span data-stu-id="de673-110">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de673-111">在从中搜索时 <xref:System.Windows.Automation.AutomationElement.RootElement%2A> ，应尝试仅获取直接子级。</span><span class="sxs-lookup"><span data-stu-id="de673-111">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="de673-112">对后代的搜索可能循环访问数百个甚至数千个元素，这可能导致堆栈溢出。</span><span class="sxs-lookup"><span data-stu-id="de673-112">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="de673-113">如果尝试在较低级别上获取特定元素，应该从应用程序窗口或者从较低级别的容器中开始搜索。</span><span class="sxs-lookup"><span data-stu-id="de673-113">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="de673-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de673-114">See also</span></span>

- <span data-ttu-id="de673-115">[InvokePattern 和 ExpandCollapsePattern 菜单项示例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="de673-115">[InvokePattern and ExpandCollapsePattern Menu Item Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="de673-116">获取 UI 自动化元素</span><span class="sxs-lookup"><span data-stu-id="de673-116">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="de673-117">使用 AutomationID 属性</span><span class="sxs-lookup"><span data-stu-id="de673-117">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
