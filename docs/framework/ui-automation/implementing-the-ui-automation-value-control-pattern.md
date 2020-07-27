---
title: 实现 UI 自动化 Value 控件模式
description: 在 UI 自动化中查看实现 Value 控件模式的准则和约定。 了解 Ivalueprovider 必需接口的必需成员。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: a15c0b50996e2c0dfdc937bc9565d5f9ba20c992
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168204"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a><span data-ttu-id="30694-104">实现 UI 自动化 Value 控件模式</span><span class="sxs-lookup"><span data-stu-id="30694-104">Implementing the UI Automation Value Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="30694-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="30694-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="30694-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="30694-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="30694-107">本主题介绍了实现 <xref:System.Windows.Automation.Provider.IValueProvider>的准则和约定，包括有关事件和属性的信息。</span><span class="sxs-lookup"><span data-stu-id="30694-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IValueProvider>, including information on events and properties.</span></span> <span data-ttu-id="30694-108">本主题的结尾列出了指向其他参考资料的链接。</span><span class="sxs-lookup"><span data-stu-id="30694-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="30694-109"><xref:System.Windows.Automation.ValuePattern> 控件模式用于支持具有未跨越范围的内部值的控件，以及可用字符串表示的控件。</span><span class="sxs-lookup"><span data-stu-id="30694-109">The <xref:System.Windows.Automation.ValuePattern> control pattern is used to support controls that have an intrinsic value not spanning a range and that can be represented as a string.</span></span> <span data-ttu-id="30694-110">此字符串是可编辑的，具体取决于控件及其设置。</span><span class="sxs-lookup"><span data-stu-id="30694-110">This string can be editable, depending on the control and its settings.</span></span> <span data-ttu-id="30694-111">有关实现此模式的控件的示例，请参阅 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="30694-111">For examples of controls that implement this pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="30694-112">实现准则和约定</span><span class="sxs-lookup"><span data-stu-id="30694-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="30694-113">在实现 Value 控件模式时，请注意以下准则和约定：</span><span class="sxs-lookup"><span data-stu-id="30694-113">When implementing the Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="30694-114">如果任何项的值是可编辑的，则诸如 <xref:System.Windows.Automation.ControlType.ListItem> 和 <xref:System.Windows.Automation.ControlType.TreeItem> 等控件必须支持 <xref:System.Windows.Automation.ValuePattern> ，而无论控件的当前编辑模式。</span><span class="sxs-lookup"><span data-stu-id="30694-114">Controls such as <xref:System.Windows.Automation.ControlType.ListItem> and <xref:System.Windows.Automation.ControlType.TreeItem> must support <xref:System.Windows.Automation.ValuePattern> if the value of any of the items is editable, regardless of the current edit mode of the control.</span></span> <span data-ttu-id="30694-115">如果子项是可编辑的，则父控件还必须支持 <xref:System.Windows.Automation.ValuePattern> 。</span><span class="sxs-lookup"><span data-stu-id="30694-115">The parent control must also support <xref:System.Windows.Automation.ValuePattern> if the child items are editable.</span></span>  
  
 <span data-ttu-id="30694-116">![可编辑的列表项。](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")</span><span class="sxs-lookup"><span data-stu-id="30694-116">![Editable list item.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")</span></span>  
<span data-ttu-id="30694-117">可编辑列表项的示例</span><span class="sxs-lookup"><span data-stu-id="30694-117">Example of an Editable List Item</span></span>  
  
- <span data-ttu-id="30694-118">单行编辑控件支持通过实现 <xref:System.Windows.Automation.Provider.IValueProvider>编程访问其内容。</span><span class="sxs-lookup"><span data-stu-id="30694-118">Single-line edit controls support programmatic access to their contents by implementing <xref:System.Windows.Automation.Provider.IValueProvider>.</span></span> <span data-ttu-id="30694-119">但是，多行编辑控件不实现 <xref:System.Windows.Automation.Provider.IValueProvider>；相反，它们通过实现 <xref:System.Windows.Automation.Provider.ITextProvider>来提供对其内容的访问。</span><span class="sxs-lookup"><span data-stu-id="30694-119">However, multi-line edit controls do not implement <xref:System.Windows.Automation.Provider.IValueProvider>; instead they provide access to their content by implementing <xref:System.Windows.Automation.Provider.ITextProvider>.</span></span>  
  
- <span data-ttu-id="30694-120">若要检索多行编辑控件的文本内容，控件必须实现 <xref:System.Windows.Automation.Provider.ITextProvider>。</span><span class="sxs-lookup"><span data-stu-id="30694-120">To retrieve the textual contents of a multi-line edit control, the control must implement <xref:System.Windows.Automation.Provider.ITextProvider>.</span></span> <span data-ttu-id="30694-121">但是， <xref:System.Windows.Automation.Provider.ITextProvider> 不支持设置控件的值。</span><span class="sxs-lookup"><span data-stu-id="30694-121">However, <xref:System.Windows.Automation.Provider.ITextProvider> does not support setting the value of a control.</span></span>  
  
- <span data-ttu-id="30694-122"><xref:System.Windows.Automation.Provider.IValueProvider> 不支持检索格式设置信息或子字符串值。</span><span class="sxs-lookup"><span data-stu-id="30694-122"><xref:System.Windows.Automation.Provider.IValueProvider> does not support the retrieval of formatting information or substring values.</span></span> <span data-ttu-id="30694-123">在这些情况下，请实现 <xref:System.Windows.Automation.Provider.ITextProvider> 。</span><span class="sxs-lookup"><span data-stu-id="30694-123">Implement <xref:System.Windows.Automation.Provider.ITextProvider> in these scenarios.</span></span>  
  
- <span data-ttu-id="30694-124"><xref:System.Windows.Automation.Provider.IValueProvider>必须由控件（如下面所示的 Microsoft Word 中的**颜色选取器**选择控件）实现，该控件支持颜色值（例如 "黄色"）与等效的内部 RGB 结构之间的字符串映射。</span><span class="sxs-lookup"><span data-stu-id="30694-124"><xref:System.Windows.Automation.Provider.IValueProvider> must be implemented by controls such as the **Color Picker** selection control from Microsoft Word (illustrated below), which supports string mapping between a color value (for example, "yellow") and an equivalent internal RGB structure.</span></span>  
  
 <span data-ttu-id="30694-125">![突出显示黄色的颜色选取器。](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span><span class="sxs-lookup"><span data-stu-id="30694-125">![Color picker with yellow highlighted.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span></span>  
<span data-ttu-id="30694-126">颜色样本字符串映射的示例</span><span class="sxs-lookup"><span data-stu-id="30694-126">Example of Color Swatch String Mapping</span></span>  
  
- <span data-ttu-id="30694-127">在允许调用 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> 之前，控件应将其 `true` 设置为 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> ，并将其 `false` 设置为 <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="30694-127">A control should have its <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> set to `true` and its <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> set to `false` before allowing a call to <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-ivalueprovider"></a><span data-ttu-id="30694-128">IValueProvider 必需的成员</span><span class="sxs-lookup"><span data-stu-id="30694-128">Required Members for IValueProvider</span></span>  
 <span data-ttu-id="30694-129">实现 <xref:System.Windows.Automation.Provider.IValueProvider>需要以下属性和方法。</span><span class="sxs-lookup"><span data-stu-id="30694-129">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IValueProvider>.</span></span>  
  
|<span data-ttu-id="30694-130">必需的成员</span><span class="sxs-lookup"><span data-stu-id="30694-130">Required members</span></span>|<span data-ttu-id="30694-131">成员类型</span><span class="sxs-lookup"><span data-stu-id="30694-131">Member type</span></span>|<span data-ttu-id="30694-132">说明</span><span class="sxs-lookup"><span data-stu-id="30694-132">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|<span data-ttu-id="30694-133">属性</span><span class="sxs-lookup"><span data-stu-id="30694-133">Property</span></span>|<span data-ttu-id="30694-134">无</span><span class="sxs-lookup"><span data-stu-id="30694-134">None</span></span>|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|<span data-ttu-id="30694-135">属性</span><span class="sxs-lookup"><span data-stu-id="30694-135">Property</span></span>|<span data-ttu-id="30694-136">无</span><span class="sxs-lookup"><span data-stu-id="30694-136">None</span></span>|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|<span data-ttu-id="30694-137">方法</span><span class="sxs-lookup"><span data-stu-id="30694-137">Method</span></span>|<span data-ttu-id="30694-138">无</span><span class="sxs-lookup"><span data-stu-id="30694-138">None</span></span>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="30694-139">例外</span><span class="sxs-lookup"><span data-stu-id="30694-139">Exceptions</span></span>  
 <span data-ttu-id="30694-140">提供程序必须引发以下异常。</span><span class="sxs-lookup"><span data-stu-id="30694-140">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="30694-141">例外类型</span><span class="sxs-lookup"><span data-stu-id="30694-141">Exception type</span></span>|<span data-ttu-id="30694-142">条件</span><span class="sxs-lookup"><span data-stu-id="30694-142">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="30694-143">-如果以不正确的格式（如格式不正确的日期）将特定于区域设置的信息传递给控件，则为。</span><span class="sxs-lookup"><span data-stu-id="30694-143">-   If locale-specific information is passed to a control in an incorrect format such as an incorrectly formatted date.</span></span>|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="30694-144">-如果无法将新值从字符串转换为控件可识别的格式，则为。</span><span class="sxs-lookup"><span data-stu-id="30694-144">-   If a new value cannot be converted from a string to a format the control recognizes.</span></span>|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="30694-145">-当尝试操作未启用的控件时。</span><span class="sxs-lookup"><span data-stu-id="30694-145">-   When an attempt is made to manipulate a control that is not enabled.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30694-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30694-146">See also</span></span>

- [<span data-ttu-id="30694-147">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="30694-147">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="30694-148">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="30694-148">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="30694-149">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="30694-149">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="30694-150">ValuePattern 插入文本示例</span><span class="sxs-lookup"><span data-stu-id="30694-150">ValuePattern Insert Text Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [<span data-ttu-id="30694-151">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="30694-151">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="30694-152">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="30694-152">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
