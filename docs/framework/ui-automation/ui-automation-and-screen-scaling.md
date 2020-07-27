---
title: UI 自动化和屏幕缩放
description: 了解 Windows 和 UI 自动化如何处理屏幕缩放。 DWM 对所有应用程序进行默认缩放，UI 自动化客户端应用必须考虑到这些应用程序。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: 99239d7bac2e556d4da0d74f36c68916da7c688a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164011"
---
# <a name="ui-automation-and-screen-scaling"></a><span data-ttu-id="dafa1-104">UI 自动化和屏幕缩放</span><span class="sxs-lookup"><span data-stu-id="dafa1-104">UI Automation and Screen Scaling</span></span>
> [!NOTE]
> <span data-ttu-id="dafa1-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="dafa1-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="dafa1-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="dafa1-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
<span data-ttu-id="dafa1-107">从 Windows Vista 开始，Windows 使用户能够更改每英寸点数（dpi）设置，以便屏幕上的大多数用户界面（UI）元素显示得更大。</span><span class="sxs-lookup"><span data-stu-id="dafa1-107">Starting with Windows Vista, Windows enables users to change the dots per inch (dpi) setting so that most user interface (UI) elements on the screen appear larger.</span></span> <span data-ttu-id="dafa1-108">尽管此功能在 Windows 中很长可用，但在以前的版本中，必须由应用程序实现缩放。</span><span class="sxs-lookup"><span data-stu-id="dafa1-108">Although this feature has long been available in Windows, in previous versions the scaling had to be implemented by applications.</span></span> <span data-ttu-id="dafa1-109">从 Windows Vista 开始，桌面窗口管理器对所有不处理其自身缩放的应用程序执行默认缩放。</span><span class="sxs-lookup"><span data-stu-id="dafa1-109">Starting with Windows Vista, the Desktop Window Manager performs default scaling for all applications that do not handle their own scaling.</span></span> <span data-ttu-id="dafa1-110">UI 自动化客户端应用程序必须考虑到此功能。</span><span class="sxs-lookup"><span data-stu-id="dafa1-110">UI Automation client applications must take this feature into account.</span></span>  
  
<a name="Scaling_in_Windows_Vista"></a>
## <a name="scaling-in-windows-vista"></a><span data-ttu-id="dafa1-111">Windows Vista 中的缩放</span><span class="sxs-lookup"><span data-stu-id="dafa1-111">Scaling in Windows Vista</span></span>  
 <span data-ttu-id="dafa1-112">默认 dpi 设置为96，这意味着96像素的宽度或高度均为1。</span><span class="sxs-lookup"><span data-stu-id="dafa1-112">The default dpi setting is 96, which means that 96 pixels occupy a width or height of one notional inch.</span></span> <span data-ttu-id="dafa1-113">“一英寸”的确切度量取决于监视器的大小和物理分辨率。</span><span class="sxs-lookup"><span data-stu-id="dafa1-113">The exact measure of an "inch" depends on the size and physical resolution of the monitor.</span></span> <span data-ttu-id="dafa1-114">例如，在 12 英寸宽、水平分辨率为 1280 像素的监视器上，96 像素的水平线将扩展大约 9/10 英寸。</span><span class="sxs-lookup"><span data-stu-id="dafa1-114">For example, on a monitor 12 inches wide, at a horizontal resolution of 1280 pixels, a horizontal line of 96 pixels extends about 9/10 of an inch.</span></span>  
  
 <span data-ttu-id="dafa1-115">更改 dpi 设置与更改屏幕分辨率不同。</span><span class="sxs-lookup"><span data-stu-id="dafa1-115">Changing the dpi setting is not the same as changing the screen resolution.</span></span> <span data-ttu-id="dafa1-116">通过 dpi 缩放，屏幕上的物理像素数保持不变。</span><span class="sxs-lookup"><span data-stu-id="dafa1-116">With dpi scaling, the number of physical pixels on the screen remains the same.</span></span> <span data-ttu-id="dafa1-117">但是，缩放将应用于 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 元素的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="dafa1-117">However, scaling is applied to the size and location of [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="dafa1-118">桌面窗口管理器 (DWM) 可以自动对桌面和未显式要求缩放的应用程序执行这种扩展。</span><span class="sxs-lookup"><span data-stu-id="dafa1-118">This scaling can be performed automatically by the Desktop Window Manager (DWM) for the desktop and for applications that do not explicitly ask not to be scaled.</span></span>  
  
 <span data-ttu-id="dafa1-119">实际上，当用户将缩放比例设置为 120 dpi 时，屏幕上的垂直或水平英寸将增大25%。</span><span class="sxs-lookup"><span data-stu-id="dafa1-119">In effect, when the user sets the scale factor to 120 dpi, a vertical or horizontal inch on the screen becomes bigger by 25 percent.</span></span> <span data-ttu-id="dafa1-120">所有尺寸会相应缩放。</span><span class="sxs-lookup"><span data-stu-id="dafa1-120">All dimensions are scaled accordingly.</span></span> <span data-ttu-id="dafa1-121">应用程序窗口距屏幕顶端和左边缘的偏移量将增大 25%。</span><span class="sxs-lookup"><span data-stu-id="dafa1-121">The offset of an application window from the top and left edges of the screen increases by 25 percent.</span></span> <span data-ttu-id="dafa1-122">如果启用了应用程序缩放，且应用程序不能识别 dpi，则窗口的大小将以相同的比例增加，以及其包含的所有元素的偏移量和大小 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dafa1-122">If application scaling is enabled and the application is not dpi-aware, the size of the window increases in the same proportion, along with the offsets and sizes of all [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements it contains.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dafa1-123">默认情况下，当用户将 dpi 设置为120时，DWM 不会对非 dpi 感知的应用程序执行缩放，但当 dpi 设置为自定义值144或更高时，将执行此功能。</span><span class="sxs-lookup"><span data-stu-id="dafa1-123">By default, the DWM does not perform scaling for non-dpi-aware applications when the user sets the dpi to 120, but does perform it when the dpi is set to a custom value of 144 or higher.</span></span> <span data-ttu-id="dafa1-124">但是，用户可以重写默认行为。</span><span class="sxs-lookup"><span data-stu-id="dafa1-124">However, the user can override the default behavior.</span></span>  
  
 <span data-ttu-id="dafa1-125">屏幕缩放为以任何方式与屏幕坐标有关的应用程序带来了新的挑战。</span><span class="sxs-lookup"><span data-stu-id="dafa1-125">Screen scaling creates new challenges for applications that are concerned in any way with screen coordinates.</span></span> <span data-ttu-id="dafa1-126">屏幕现在包含两个坐标系：物理和逻辑。</span><span class="sxs-lookup"><span data-stu-id="dafa1-126">The screen now contains two coordinate systems: physical and logical.</span></span> <span data-ttu-id="dafa1-127">点的物理坐标是距原点左上部的实际偏移量（以像素为单位）。</span><span class="sxs-lookup"><span data-stu-id="dafa1-127">The physical coordinates of a point are the actual offset in pixels from the top left of the origin.</span></span> <span data-ttu-id="dafa1-128">如果像素本身进行了缩放，则逻辑坐标为缩放后的偏移量。</span><span class="sxs-lookup"><span data-stu-id="dafa1-128">The logical coordinates are the offsets as they would be if the pixels themselves were scaled.</span></span>  
  
 <span data-ttu-id="dafa1-129">假定你设计了一个对话框，其按钮位于坐标 (100, 48) 处。</span><span class="sxs-lookup"><span data-stu-id="dafa1-129">Suppose you design a dialog box with a button at coordinates (100, 48).</span></span> <span data-ttu-id="dafa1-130">此对话框在默认的 96 dpi 下显示时，该按钮位于的物理坐标（100，48）。</span><span class="sxs-lookup"><span data-stu-id="dafa1-130">When this dialog box is displayed at the default 96 dpi, the button is located at physical coordinates of (100, 48).</span></span> <span data-ttu-id="dafa1-131">在 120 dpi 处，它位于（125，60）的物理坐标。</span><span class="sxs-lookup"><span data-stu-id="dafa1-131">At 120 dpi, it is located at physical coordinates of (125, 60).</span></span> <span data-ttu-id="dafa1-132">但在任何 dpi 设置上，逻辑坐标都是相同的：（100，48）。</span><span class="sxs-lookup"><span data-stu-id="dafa1-132">But the logical coordinates are the same at any dpi setting: (100, 48).</span></span>  
  
 <span data-ttu-id="dafa1-133">逻辑坐标非常重要，因为它们使操作系统和应用程序的行为保持一致，而不考虑 dpi 设置。</span><span class="sxs-lookup"><span data-stu-id="dafa1-133">Logical coordinates are important, because they make the behavior of the operating system and applications consistent regardless of the dpi setting.</span></span> <span data-ttu-id="dafa1-134">例如，正常情况下， <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> 将返回逻辑坐标。</span><span class="sxs-lookup"><span data-stu-id="dafa1-134">For example, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normally returns the logical coordinates.</span></span> <span data-ttu-id="dafa1-135">如果将光标移至对话框中的某个元素上，则将返回相同的坐标，而不考虑 dpi 设置。</span><span class="sxs-lookup"><span data-stu-id="dafa1-135">If you move the cursor over an element in a dialog box, the same coordinates are returned regardless of the dpi setting.</span></span> <span data-ttu-id="dafa1-136">如果在（100，100）处绘制控件，则该控件将绘制到这些逻辑坐标，并将在任何 dpi 设置中占用相同的相对位置。</span><span class="sxs-lookup"><span data-stu-id="dafa1-136">If you draw a control at (100, 100), it is drawn to those logical coordinates, and will occupy the same relative position at any dpi setting.</span></span>  
  
<a name="Scaling_in_UI_Automation_Clients"></a>
## <a name="scaling-in-ui-automation-clients"></a><span data-ttu-id="dafa1-137">UI 自动化客户端中的缩放</span><span class="sxs-lookup"><span data-stu-id="dafa1-137">Scaling in UI Automation Clients</span></span>  
 <span data-ttu-id="dafa1-138">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]API 不使用逻辑坐标。</span><span class="sxs-lookup"><span data-stu-id="dafa1-138">The [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API does not use logical coordinates.</span></span> <span data-ttu-id="dafa1-139">下面的方法和属性将返回物理坐标或将其用作参数。</span><span class="sxs-lookup"><span data-stu-id="dafa1-139">The following methods and properties either return physical coordinates or take them as parameters.</span></span>  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 <span data-ttu-id="dafa1-140">默认情况下，在非 96 dpi 环境中运行的 UI 自动化客户端应用程序将不能从这些方法和属性中获得正确的结果。</span><span class="sxs-lookup"><span data-stu-id="dafa1-140">By default, a UI Automation client application running in a non-96- dpi environment will not be able to obtain correct results from these methods and properties.</span></span> <span data-ttu-id="dafa1-141">例如，由于光标的位置是逻辑坐标，客户端不能仅将这些坐标传递到 <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> 以获取光标下的元素。</span><span class="sxs-lookup"><span data-stu-id="dafa1-141">For example, because the cursor position is in logical coordinates, the client cannot simply pass these coordinates to <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> to obtain the element that is under the cursor.</span></span> <span data-ttu-id="dafa1-142">此外，该应用程序不能正确将 Windows 放置在其客户端区域之外。</span><span class="sxs-lookup"><span data-stu-id="dafa1-142">In addition, the application will not be able to correctly place windows outside its client area.</span></span>  
  
 <span data-ttu-id="dafa1-143">解决方法分两个部分。</span><span class="sxs-lookup"><span data-stu-id="dafa1-143">The solution is in two parts.</span></span>  
  
1. <span data-ttu-id="dafa1-144">首先，使客户端应用程序可感知 dpi。</span><span class="sxs-lookup"><span data-stu-id="dafa1-144">First, make the client application dpi-aware.</span></span> <span data-ttu-id="dafa1-145">为此，请 `SetProcessDPIAware` 在启动时调用 Win32 函数。</span><span class="sxs-lookup"><span data-stu-id="dafa1-145">To do this, call the Win32 function `SetProcessDPIAware` at startup.</span></span> <span data-ttu-id="dafa1-146">在托管代码中，以下声明使得此函数可用。</span><span class="sxs-lookup"><span data-stu-id="dafa1-146">In managed code, the following declaration makes this function available.</span></span>  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     <span data-ttu-id="dafa1-147">此函数使整个进程 dpi 感知，这意味着属于该进程的所有窗口都是无比例的。</span><span class="sxs-lookup"><span data-stu-id="dafa1-147">This function makes the entire process dpi-aware, meaning that all windows that belong to the process are unscaled.</span></span> <span data-ttu-id="dafa1-148">例如，在[荧光笔示例](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)中，构成突出显示矩形的四个窗口位于从 UI 自动化获取的物理坐标上，而非逻辑坐标。</span><span class="sxs-lookup"><span data-stu-id="dafa1-148">In the [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), for instance, the four windows that make up the highlight rectangle are located at the physical coordinates obtained from UI Automation, not the logical coordinates.</span></span> <span data-ttu-id="dafa1-149">如果该示例不能识别 dpi，则会在桌面上的逻辑坐标处绘制突出显示，这将导致非 96 dpi 环境中出现不正确的位置。</span><span class="sxs-lookup"><span data-stu-id="dafa1-149">If the sample were not dpi-aware, the highlight would be drawn at the logical coordinates on the desktop, which would result in incorrect placement in a non-96- dpi environment.</span></span>  
  
2. <span data-ttu-id="dafa1-150">若要获取光标坐标，请调用 Win32 函数 `GetPhysicalCursorPos` 。</span><span class="sxs-lookup"><span data-stu-id="dafa1-150">To get cursor coordinates, call the Win32 function `GetPhysicalCursorPos`.</span></span> <span data-ttu-id="dafa1-151">下面的示例演示如何声明和使用此函数。</span><span class="sxs-lookup"><span data-stu-id="dafa1-151">The following example shows how to declare and use this function.</span></span>  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> <span data-ttu-id="dafa1-152">请勿使用 <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="dafa1-152">Do not use <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dafa1-153">未定义此属性在扩展环境下客户端窗口以外的行为。</span><span class="sxs-lookup"><span data-stu-id="dafa1-153">The behavior of this property outside client windows in a scaled environment is undefined.</span></span>  
  
 <span data-ttu-id="dafa1-154">如果你的应用程序使用非 dpi 感知的应用程序执行直接的跨进程通信，则可以使用 Win32 函数和在逻辑和物理坐标之间 `PhysicalToLogicalPoint` 转换 `LogicalToPhysicalPoint` 。</span><span class="sxs-lookup"><span data-stu-id="dafa1-154">If your application performs direct cross-process communication with non- dpi-aware applications, you may have convert between logical and physical coordinates by using the Win32 functions `PhysicalToLogicalPoint` and `LogicalToPhysicalPoint`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dafa1-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dafa1-155">See also</span></span>

- [<span data-ttu-id="dafa1-156">Highlighter Sample</span><span class="sxs-lookup"><span data-stu-id="dafa1-156">Highlighter Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
