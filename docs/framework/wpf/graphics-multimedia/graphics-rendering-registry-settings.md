---
title: 图形呈现注册表设置
description: 了解如何在 Windows Presentation Foundation （WPF）中使用注册表设置进行故障排除、调试和产品支持。
ms.date: 03/30/2017
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
ms.openlocfilehash: a2c6cfa5a207ae89c053f6ee81597f01458b5933
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853758"
---
# <a name="graphics-rendering-registry-settings"></a><span data-ttu-id="886ba-103">图形呈现注册表设置</span><span class="sxs-lookup"><span data-stu-id="886ba-103">Graphics Rendering Registry Settings</span></span>
<span data-ttu-id="886ba-104">本主题概述了影响 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 图形呈现注册表设置。</span><span class="sxs-lookup"><span data-stu-id="886ba-104">This topic provides an overview of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] graphics rendering registry settings that affect [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>  

<a name="overview"></a>
## <a name="when-to-use-graphics-rendering-registry-settings"></a><span data-ttu-id="886ba-105">何时使用图形呈现注册表设置</span><span class="sxs-lookup"><span data-stu-id="886ba-105">When to Use Graphics Rendering Registry Settings</span></span>  
 <span data-ttu-id="886ba-106">这些注册表设置为故障排除、调试和产品支持目的而提供。</span><span class="sxs-lookup"><span data-stu-id="886ba-106">These registry settings are provided for troubleshooting, debugging, and product support purposes.</span></span> <span data-ttu-id="886ba-107">由于对注册表的更改会影响所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序，应用程序永远不应该自动或在安装期间更改这些注册表项。</span><span class="sxs-lookup"><span data-stu-id="886ba-107">Because changes to the registry affect all [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, your application should never alter these registry keys automatically, or during installation.</span></span>  
  
<a name="xpdmandwddm"></a>
## <a name="what-are-xpdm-and-wddm"></a><span data-ttu-id="886ba-108">什么是 XPDM 和 WDDM？</span><span class="sxs-lookup"><span data-stu-id="886ba-108">What are XPDM and WDDM?</span></span>  
 <span data-ttu-id="886ba-109">某些图形呈现注册表设置具有不同的默认值，具体取决于视频卡使用的是 XPDM 还是 WDDM 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="886ba-109">Some of the graphics rendering registry settings have different default values, depending on whether your video card uses an XPDM or WDDM driver.</span></span> <span data-ttu-id="886ba-110">XPDM 是 Microsoft Windows XP 显示驱动程序模型，而 WDDM 是 Windows 显示器驱动程序模型。</span><span class="sxs-lookup"><span data-stu-id="886ba-110">XPDM is the Microsoft Windows XP Display Driver Model and WDDM is the Windows Display Driver Model.</span></span> <span data-ttu-id="886ba-111">WDDM 在运行 Windows Vista 和 Windows 7 的计算机上可用。</span><span class="sxs-lookup"><span data-stu-id="886ba-111">WDDM is available on computers running Windows Vista and Windows 7.</span></span> <span data-ttu-id="886ba-112">在运行 Windows Vista、Microsoft Windows XP 和 Microsoft Windows Server 2003 的计算机上，可以使用 XPDM。</span><span class="sxs-lookup"><span data-stu-id="886ba-112">XPDM is available on computers running Windows Vista, Microsoft Windows XP, and Microsoft Windows Server 2003.</span></span> <span data-ttu-id="886ba-113">有关 WDDM 的详细信息，请参阅[Windows 显示驱动程序模型（WDDM）设计指南](/windows-hardware/drivers/display/windows-vista-display-driver-model-design-guide)。</span><span class="sxs-lookup"><span data-stu-id="886ba-113">For more information about WDDM, see [Windows Display Driver Model (WDDM) Design Guide](/windows-hardware/drivers/display/windows-vista-display-driver-model-design-guide).</span></span>  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a><span data-ttu-id="886ba-114">注册表设置</span><span class="sxs-lookup"><span data-stu-id="886ba-114">Registry Settings</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="886ba-115">提供了四个注册表设置来控制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 呈现：</span><span class="sxs-lookup"><span data-stu-id="886ba-115">provides four registry settings for controlling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rendering:</span></span>  
  
|<span data-ttu-id="886ba-116">设置</span><span class="sxs-lookup"><span data-stu-id="886ba-116">Setting</span></span>|<span data-ttu-id="886ba-117">说明</span><span class="sxs-lookup"><span data-stu-id="886ba-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="886ba-118">**禁用硬件加速选项**</span><span class="sxs-lookup"><span data-stu-id="886ba-118">**Disable Hardware Acceleration Option**</span></span>|<span data-ttu-id="886ba-119">指定是否应启用硬件加速。</span><span class="sxs-lookup"><span data-stu-id="886ba-119">Specifies whether hardware acceleration should be enabled.</span></span>|  
|<span data-ttu-id="886ba-120">**最大多重采样值**</span><span class="sxs-lookup"><span data-stu-id="886ba-120">**Maximum Multisample Value**</span></span>|<span data-ttu-id="886ba-121">指定使3D 内容抗锯齿的多级分级。</span><span class="sxs-lookup"><span data-stu-id="886ba-121">Specifies the degree of multisampling for antialiasing 3D content.</span></span>|  
|<span data-ttu-id="886ba-122">**必需的视频驱动程序日期设置**</span><span class="sxs-lookup"><span data-stu-id="886ba-122">**Required Video Driver Date Setting**</span></span>|<span data-ttu-id="886ba-123">指定系统是否对 2004 年 11 月之前发布的驱动程序禁用硬件加速。</span><span class="sxs-lookup"><span data-stu-id="886ba-123">Specifies whether the system disables hardware acceleration for drivers released before November 2004.</span></span>|  
|<span data-ttu-id="886ba-124">**使用参考光栅器选项**</span><span class="sxs-lookup"><span data-stu-id="886ba-124">**Use Reference Rasterizer Option**</span></span>|<span data-ttu-id="886ba-125">指定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是否应使用参考光栅器。</span><span class="sxs-lookup"><span data-stu-id="886ba-125">Specifies whether [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] should use the reference rasterizer.</span></span>|  
  
 <span data-ttu-id="886ba-126">知道如何引用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 注册表设置的任何外部配置实用工具都可以访问这些设置。</span><span class="sxs-lookup"><span data-stu-id="886ba-126">These settings can be accessed by any external configuration utility that knows how to reference the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] registry settings.</span></span> <span data-ttu-id="886ba-127">还可以通过使用 Windows 注册表编辑器直接访问这些值来创建或修改这些设置。</span><span class="sxs-lookup"><span data-stu-id="886ba-127">These settings can also be created or modified by accessing the values directly by using the Windows Registry Editor.</span></span>  
  
<a name="disablehardwareacceleration"></a>
## <a name="disable-hardware-acceleration-option"></a><span data-ttu-id="886ba-128">禁用硬件加速选项</span><span class="sxs-lookup"><span data-stu-id="886ba-128">Disable Hardware Acceleration Option</span></span>  
  
|<span data-ttu-id="886ba-129">注册表项</span><span class="sxs-lookup"><span data-stu-id="886ba-129">Registry key</span></span>|<span data-ttu-id="886ba-130">值类型</span><span class="sxs-lookup"><span data-stu-id="886ba-130">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|<span data-ttu-id="886ba-131">DWORD</span><span class="sxs-lookup"><span data-stu-id="886ba-131">DWORD</span></span>|  
  
 <span data-ttu-id="886ba-132">使用“禁用硬件加速选项”\*\*\*\*，可以出于调试和测试目的而关闭硬件加速。</span><span class="sxs-lookup"><span data-stu-id="886ba-132">The **disable hardware acceleration option** enables you to turn off hardware acceleration for debugging and test purposes.</span></span> <span data-ttu-id="886ba-133">查看应用程序中的呈现项目时，尝试关闭硬件加速。</span><span class="sxs-lookup"><span data-stu-id="886ba-133">When you see rendering artifacts in an application, try turning off hardware acceleration.</span></span> <span data-ttu-id="886ba-134">如果项目消失，则视频驱动程序可能有问题。</span><span class="sxs-lookup"><span data-stu-id="886ba-134">If the artifact disappears, the problem might be with your video driver.</span></span>  
  
 <span data-ttu-id="886ba-135">“禁用硬件加速选项”\*\*\*\* 是一个等于 0 或 1 的 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="886ba-135">The **disable hardware acceleration option** is a DWORD value that is either 0 or 1.</span></span> <span data-ttu-id="886ba-136">如果值为 1，表示禁用硬件加速。</span><span class="sxs-lookup"><span data-stu-id="886ba-136">A value of 1 disables hardware acceleration.</span></span> <span data-ttu-id="886ba-137">如果值为 0，表示启用硬件加速，前提是系统满足硬件加速要求；有关详细信息，请参阅[图形呈现层](../advanced/graphics-rendering-tiers.md)。</span><span class="sxs-lookup"><span data-stu-id="886ba-137">A value of 0 enables hardware acceleration, provided the system meets hardware acceleration requirements; for more information, see [Graphics Rendering Tiers](../advanced/graphics-rendering-tiers.md).</span></span>  
  
<a name="maxmultisample"></a>
## <a name="maximum-multisample-value"></a><span data-ttu-id="886ba-138">最大多重采样值</span><span class="sxs-lookup"><span data-stu-id="886ba-138">Maximum Multisample Value</span></span>  
  
|<span data-ttu-id="886ba-139">注册表项</span><span class="sxs-lookup"><span data-stu-id="886ba-139">Registry key</span></span>|<span data-ttu-id="886ba-140">值类型</span><span class="sxs-lookup"><span data-stu-id="886ba-140">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|<span data-ttu-id="886ba-141">DWORD</span><span class="sxs-lookup"><span data-stu-id="886ba-141">DWORD</span></span>|  
  
 <span data-ttu-id="886ba-142">"**最大多级采样值**" 使您可以调整三维内容的最大抗锯齿量。</span><span class="sxs-lookup"><span data-stu-id="886ba-142">The **maximum multisample value** enables you to adjust the maximum amount of antialiasing of 3D content.</span></span> <span data-ttu-id="886ba-143">使用此级别禁用 Windows Vista 中的3D 抗锯齿功能。</span><span class="sxs-lookup"><span data-stu-id="886ba-143">Use this level to disable 3D antialiasing in Windows Vista.</span></span>  
  
 <span data-ttu-id="886ba-144">“最大多重采样值”\*\*\*\* 是一个 DWORD 值，范围为从 0 到 16。</span><span class="sxs-lookup"><span data-stu-id="886ba-144">The **maximum multisample value** is a DWORD value that ranges from 0 to 16.</span></span> <span data-ttu-id="886ba-145">如果值为0，则表示应禁用3D 内容的多采样抗锯齿，如果视频卡支持，则值为16将尝试使用最多16x 的多级采样抗锯齿。</span><span class="sxs-lookup"><span data-stu-id="886ba-145">A value of 0 specifies that multisample antialiasing of 3D content should be disabled, and a value of 16 will attempt to use up to 16x multisample antialiasing, if supported by the video card.</span></span> <span data-ttu-id="886ba-146">请注意，在使用 XPDM 驱动程序的计算机上设置此注册表项值将导致应用程序使用大量附加视频内存，降低三维呈现的性能，并且可能会引入呈现错误和稳定性问题。</span><span class="sxs-lookup"><span data-stu-id="886ba-146">Beware that setting this registry key value on computers using XPDM drivers will cause applications to use a large amount of additional video memory, decrease the performance of 3D rendering, and has the potential to introduce rendering errors and stability problems.</span></span>  
  
 <span data-ttu-id="886ba-147">当未设置此注册表项时， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 将默认为 0（对于 XPDM 驱动程序）和 4（对于 WDDM 驱动程序）。</span><span class="sxs-lookup"><span data-stu-id="886ba-147">When this registry key is not set, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] defaults to 0 for XPDM drivers and 4 for WDDM drivers.</span></span>  
  
<a name="requiredvideodriverdatesetting"></a>
## <a name="required-video-driver-date-setting"></a><span data-ttu-id="886ba-148">必需的视频驱动程序日期设置</span><span class="sxs-lookup"><span data-stu-id="886ba-148">Required Video Driver Date Setting</span></span>  
  
|<span data-ttu-id="886ba-149">注册表项</span><span class="sxs-lookup"><span data-stu-id="886ba-149">Registry key</span></span>|<span data-ttu-id="886ba-150">值类型</span><span class="sxs-lookup"><span data-stu-id="886ba-150">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|<span data-ttu-id="886ba-151">String</span><span class="sxs-lookup"><span data-stu-id="886ba-151">String</span></span>|  
  
 <span data-ttu-id="886ba-152">2004年11月，Microsoft 发布了新版本的驱动程序测试指南;此日期之后编写的驱动程序提供更好的稳定性。</span><span class="sxs-lookup"><span data-stu-id="886ba-152">In November, 2004, Microsoft released a new version of the driver testing guidelines; the drivers written after this date offer better stability.</span></span> <span data-ttu-id="886ba-153">默认情况下，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 将为这些驱动程序使用硬件加速管道，并将回退到此日期之前发布的 XPDM 驱动程序的软件呈现。</span><span class="sxs-lookup"><span data-stu-id="886ba-153">By default, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] will use the hardware acceleration pipeline for these drivers and will fall back to software rendering for XPDM drivers published before this date.</span></span>  
  
 <span data-ttu-id="886ba-154">使用“必需的视频驱动程序日期设置”\*\*\*\*，可以为 XPDM 驱动程序指定最早备用日期。</span><span class="sxs-lookup"><span data-stu-id="886ba-154">The **required video driver date setting** enables you to specify an alternate minimum date for XPDM drivers.</span></span> <span data-ttu-id="886ba-155">如果确信视频驱动程序足够稳定，可支持 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，应仅指定早于 2004 年 11 月的日期。</span><span class="sxs-lookup"><span data-stu-id="886ba-155">You should only specify a date earlier than November, 2004 if you are confident that your video driver is stable enough to support [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="886ba-156">必需的视频驱动程序采用以下格式的字符串：</span><span class="sxs-lookup"><span data-stu-id="886ba-156">The required video driver setting takes a string of the following format:</span></span>  
  
| |  
|-|  
|<span data-ttu-id="886ba-157">*YYYY* `/`*MM* `/` *DD*</span><span class="sxs-lookup"><span data-stu-id="886ba-157">*YYYY* `/` *MM* `/` *DD*</span></span>|  
  
 <span data-ttu-id="886ba-158">其中 *YYYY* 是四位数年份，*MM* 是两位数月份，而 *DD* 是两位数日期。</span><span class="sxs-lookup"><span data-stu-id="886ba-158">Where *YYYY* is the four-digit year, *MM* is the two-digit month, and *DD* is the two digit day.</span></span> <span data-ttu-id="886ba-159">当未设置此值时，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用 2004 年 11 月作为必需的视频驱动程序日期。</span><span class="sxs-lookup"><span data-stu-id="886ba-159">When this value is unset, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uses November, 2004 as its required video driver date.</span></span>  
  
<a name="usereferencerasterizeroption"></a>
## <a name="use-reference-rasterizer-option"></a><span data-ttu-id="886ba-160">使用参考光栅器选项</span><span class="sxs-lookup"><span data-stu-id="886ba-160">Use Reference Rasterizer Option</span></span>  
  
|<span data-ttu-id="886ba-161">注册表项</span><span class="sxs-lookup"><span data-stu-id="886ba-161">Registry key</span></span>|<span data-ttu-id="886ba-162">值类型</span><span class="sxs-lookup"><span data-stu-id="886ba-162">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|<span data-ttu-id="886ba-163">DWORD</span><span class="sxs-lookup"><span data-stu-id="886ba-163">DWORD</span></span>|  
  
 <span data-ttu-id="886ba-164">**使用 "使用参考光栅" 选项**，您可以强制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 进入模拟硬件呈现模式以进行调试： [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 进入硬件模式，但使用 Microsoft Direct3D reference 软件光栅程序，d3dref9.dll，而不是实际的硬件设备。</span><span class="sxs-lookup"><span data-stu-id="886ba-164">The **use reference rasterizer option** enables you to force [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] into a simulated hardware rendering mode for debugging: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] goes into hardware mode, but uses the Microsoft Direct3D reference software rasterizer, d3dref9.dll, instead of an actual hardware device.</span></span>  
  
 <span data-ttu-id="886ba-165">参考光栅器非常缓慢，但可以绕过视频驱动程序以避免由驱动程序问题导致的任何呈现问题。</span><span class="sxs-lookup"><span data-stu-id="886ba-165">The reference rasterizer is very slow, but bypasses your video driver to avoid any rendering issues caused by driver problems.</span></span> <span data-ttu-id="886ba-166">出于此原因，可使用参考光栅器确定呈现问题是否由视频驱动程序导致。</span><span class="sxs-lookup"><span data-stu-id="886ba-166">For this reason, you can use the reference rasterizer to determine if rendering issues are caused by the video driver.</span></span> <span data-ttu-id="886ba-167">d3dref9.dll 文件必须位于应用程序可访问它的位置，如系统路径或应用程序的本地目录中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="886ba-167">The d3dref9.dll file must be in a location where the application can access it, such as in any location in the system path or in the local directory of the application.</span></span>  
  
 <span data-ttu-id="886ba-168">“使用参考光栅器选项”\*\*\*\* 采用 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="886ba-168">The **use reference rasterizer option** takes a DWORD value.</span></span> <span data-ttu-id="886ba-169">值为 0 指示不使用参考光栅器。</span><span class="sxs-lookup"><span data-stu-id="886ba-169">A value of 0 indicates that the reference rasterizer is not used.</span></span> <span data-ttu-id="886ba-170">任何其他非零值都强制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用参考光栅器。</span><span class="sxs-lookup"><span data-stu-id="886ba-170">Any other non-zero value forces [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to use the reference rasterizer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="886ba-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="886ba-171">See also</span></span>

- [<span data-ttu-id="886ba-172">图形呈现层</span><span class="sxs-lookup"><span data-stu-id="886ba-172">Graphics Rendering Tiers</span></span>](../advanced/graphics-rendering-tiers.md)
- [<span data-ttu-id="886ba-173">WPF 图形呈现疑难解答</span><span class="sxs-lookup"><span data-stu-id="886ba-173">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
