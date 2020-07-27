---
title: 实现 UI 自动化 RangeValue 控件模式
description: 查看在 UI 自动化中实现 RangeValue 控件模式的准则和约定。 请参阅 Irangevalueprovider 必需接口的必需成员。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: ccb6aeb5f8451975d7e2e9649bbb82c0c3ae23d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164077"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="27f2d-104">实现 UI 自动化 RangeValue 控件模式</span><span class="sxs-lookup"><span data-stu-id="27f2d-104">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="27f2d-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="27f2d-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="27f2d-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="27f2d-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="27f2d-107">本主题介绍了实现 <xref:System.Windows.Automation.Provider.IRangeValueProvider>的准则和约定，包括有关事件和属性的信息。</span><span class="sxs-lookup"><span data-stu-id="27f2d-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="27f2d-108">本主题的结尾列出了指向其他参考资料的链接。</span><span class="sxs-lookup"><span data-stu-id="27f2d-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="27f2d-109"><xref:System.Windows.Automation.RangeValuePattern> 控件模式用于支持可被设置为范围内的某个值的控件。</span><span class="sxs-lookup"><span data-stu-id="27f2d-109">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="27f2d-110">有关实现此控件模式的控件示例，请参阅 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="27f2d-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="27f2d-111">实现准则和约定</span><span class="sxs-lookup"><span data-stu-id="27f2d-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="27f2d-112">在实现 Range Value 控件模式时，请注意以下准则和约定：</span><span class="sxs-lookup"><span data-stu-id="27f2d-112">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="27f2d-113">控件允许基于区域设置或用户首选项来校准支持的属性。</span><span class="sxs-lookup"><span data-stu-id="27f2d-113">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="27f2d-114">这样的一个示例是温度计控件，它可被设置为以华氏或摄氏显示温度。</span><span class="sxs-lookup"><span data-stu-id="27f2d-114">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="27f2d-115">具有不明确范围值的控件（如进度栏或滑块）应对这些值进行规范化。</span><span class="sxs-lookup"><span data-stu-id="27f2d-115">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="27f2d-116">![进度栏。](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="27f2d-116">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="27f2d-117">进度栏的示例，其中值为整数类型，最小和最大属性值分别被规范化为 0 和 100</span><span class="sxs-lookup"><span data-stu-id="27f2d-117">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="27f2d-118">IRangeValueProvider 必需的成员</span><span class="sxs-lookup"><span data-stu-id="27f2d-118">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="27f2d-119">必需的成员</span><span class="sxs-lookup"><span data-stu-id="27f2d-119">Required member</span></span>|<span data-ttu-id="27f2d-120">成员类型</span><span class="sxs-lookup"><span data-stu-id="27f2d-120">Member type</span></span>|<span data-ttu-id="27f2d-121">说明</span><span class="sxs-lookup"><span data-stu-id="27f2d-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="27f2d-122">属性</span><span class="sxs-lookup"><span data-stu-id="27f2d-122">Property</span></span>|<span data-ttu-id="27f2d-123">无</span><span class="sxs-lookup"><span data-stu-id="27f2d-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="27f2d-124">属性</span><span class="sxs-lookup"><span data-stu-id="27f2d-124">Property</span></span>|<span data-ttu-id="27f2d-125">无</span><span class="sxs-lookup"><span data-stu-id="27f2d-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="27f2d-126">属性</span><span class="sxs-lookup"><span data-stu-id="27f2d-126">Property</span></span>|<span data-ttu-id="27f2d-127">无</span><span class="sxs-lookup"><span data-stu-id="27f2d-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="27f2d-128">属性</span><span class="sxs-lookup"><span data-stu-id="27f2d-128">Property</span></span>|<span data-ttu-id="27f2d-129">无</span><span class="sxs-lookup"><span data-stu-id="27f2d-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="27f2d-130">属性</span><span class="sxs-lookup"><span data-stu-id="27f2d-130">Property</span></span>|<span data-ttu-id="27f2d-131">无</span><span class="sxs-lookup"><span data-stu-id="27f2d-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="27f2d-132">属性</span><span class="sxs-lookup"><span data-stu-id="27f2d-132">Property</span></span>|<span data-ttu-id="27f2d-133">无</span><span class="sxs-lookup"><span data-stu-id="27f2d-133">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="27f2d-134">方法</span><span class="sxs-lookup"><span data-stu-id="27f2d-134">Methods</span></span>|<span data-ttu-id="27f2d-135">无</span><span class="sxs-lookup"><span data-stu-id="27f2d-135">None</span></span>|  
  
 <span data-ttu-id="27f2d-136">没有与此控件模式关联的事件。</span><span class="sxs-lookup"><span data-stu-id="27f2d-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="27f2d-137">例外</span><span class="sxs-lookup"><span data-stu-id="27f2d-137">Exceptions</span></span>  
 <span data-ttu-id="27f2d-138">提供程序必须引发以下异常。</span><span class="sxs-lookup"><span data-stu-id="27f2d-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="27f2d-139">例外类型</span><span class="sxs-lookup"><span data-stu-id="27f2d-139">Exception type</span></span>|<span data-ttu-id="27f2d-140">条件</span><span class="sxs-lookup"><span data-stu-id="27f2d-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="27f2d-141">使用一个大于<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> 或小于 <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> 的值调用 <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>。</span><span class="sxs-lookup"><span data-stu-id="27f2d-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27f2d-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27f2d-142">See also</span></span>

- [<span data-ttu-id="27f2d-143">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="27f2d-143">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="27f2d-144">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="27f2d-144">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="27f2d-145">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="27f2d-145">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="27f2d-146">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="27f2d-146">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="27f2d-147">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="27f2d-147">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
