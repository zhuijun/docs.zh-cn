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
# <a name="graphics-rendering-registry-settings"></a>图形呈现注册表设置
本主题概述了影响 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 图形呈现注册表设置。  

<a name="overview"></a>
## <a name="when-to-use-graphics-rendering-registry-settings"></a>何时使用图形呈现注册表设置  
 这些注册表设置为故障排除、调试和产品支持目的而提供。 由于对注册表的更改会影响所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序，应用程序永远不应该自动或在安装期间更改这些注册表项。  
  
<a name="xpdmandwddm"></a>
## <a name="what-are-xpdm-and-wddm"></a>什么是 XPDM 和 WDDM？  
 某些图形呈现注册表设置具有不同的默认值，具体取决于视频卡使用的是 XPDM 还是 WDDM 驱动程序。 XPDM 是 Microsoft Windows XP 显示驱动程序模型，而 WDDM 是 Windows 显示器驱动程序模型。 WDDM 在运行 Windows Vista 和 Windows 7 的计算机上可用。 在运行 Windows Vista、Microsoft Windows XP 和 Microsoft Windows Server 2003 的计算机上，可以使用 XPDM。 有关 WDDM 的详细信息，请参阅[Windows 显示驱动程序模型（WDDM）设计指南](/windows-hardware/drivers/display/windows-vista-display-driver-model-design-guide)。  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>注册表设置  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了四个注册表设置来控制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 呈现：  
  
|设置|说明|  
|-------------|-----------------|  
|**禁用硬件加速选项**|指定是否应启用硬件加速。|  
|**最大多重采样值**|指定使3D 内容抗锯齿的多级分级。|  
|**必需的视频驱动程序日期设置**|指定系统是否对 2004 年 11 月之前发布的驱动程序禁用硬件加速。|  
|**使用参考光栅器选项**|指定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是否应使用参考光栅器。|  
  
 知道如何引用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 注册表设置的任何外部配置实用工具都可以访问这些设置。 还可以通过使用 Windows 注册表编辑器直接访问这些值来创建或修改这些设置。  
  
<a name="disablehardwareacceleration"></a>
## <a name="disable-hardware-acceleration-option"></a>禁用硬件加速选项  
  
|注册表项|值类型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 使用“禁用硬件加速选项”****，可以出于调试和测试目的而关闭硬件加速。 查看应用程序中的呈现项目时，尝试关闭硬件加速。 如果项目消失，则视频驱动程序可能有问题。  
  
 “禁用硬件加速选项”**** 是一个等于 0 或 1 的 DWORD 值。 如果值为 1，表示禁用硬件加速。 如果值为 0，表示启用硬件加速，前提是系统满足硬件加速要求；有关详细信息，请参阅[图形呈现层](../advanced/graphics-rendering-tiers.md)。  
  
<a name="maxmultisample"></a>
## <a name="maximum-multisample-value"></a>最大多重采样值  
  
|注册表项|值类型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 "**最大多级采样值**" 使您可以调整三维内容的最大抗锯齿量。 使用此级别禁用 Windows Vista 中的3D 抗锯齿功能。  
  
 “最大多重采样值”**** 是一个 DWORD 值，范围为从 0 到 16。 如果值为0，则表示应禁用3D 内容的多采样抗锯齿，如果视频卡支持，则值为16将尝试使用最多16x 的多级采样抗锯齿。 请注意，在使用 XPDM 驱动程序的计算机上设置此注册表项值将导致应用程序使用大量附加视频内存，降低三维呈现的性能，并且可能会引入呈现错误和稳定性问题。  
  
 当未设置此注册表项时， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 将默认为 0（对于 XPDM 驱动程序）和 4（对于 WDDM 驱动程序）。  
  
<a name="requiredvideodriverdatesetting"></a>
## <a name="required-video-driver-date-setting"></a>必需的视频驱动程序日期设置  
  
|注册表项|值类型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|String|  
  
 2004年11月，Microsoft 发布了新版本的驱动程序测试指南;此日期之后编写的驱动程序提供更好的稳定性。 默认情况下，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 将为这些驱动程序使用硬件加速管道，并将回退到此日期之前发布的 XPDM 驱动程序的软件呈现。  
  
 使用“必需的视频驱动程序日期设置”****，可以为 XPDM 驱动程序指定最早备用日期。 如果确信视频驱动程序足够稳定，可支持 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，应仅指定早于 2004 年 11 月的日期。  
  
 必需的视频驱动程序采用以下格式的字符串：  
  
| |  
|-|  
|*YYYY* `/`*MM* `/` *DD*|  
  
 其中 *YYYY* 是四位数年份，*MM* 是两位数月份，而 *DD* 是两位数日期。 当未设置此值时，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用 2004 年 11 月作为必需的视频驱动程序日期。  
  
<a name="usereferencerasterizeroption"></a>
## <a name="use-reference-rasterizer-option"></a>使用参考光栅器选项  
  
|注册表项|值类型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **使用 "使用参考光栅" 选项**，您可以强制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 进入模拟硬件呈现模式以进行调试： [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 进入硬件模式，但使用 Microsoft Direct3D reference 软件光栅程序，d3dref9.dll，而不是实际的硬件设备。  
  
 参考光栅器非常缓慢，但可以绕过视频驱动程序以避免由驱动程序问题导致的任何呈现问题。 出于此原因，可使用参考光栅器确定呈现问题是否由视频驱动程序导致。 d3dref9.dll 文件必须位于应用程序可访问它的位置，如系统路径或应用程序的本地目录中的任何位置。  
  
 “使用参考光栅器选项”**** 采用 DWORD 值。 值为 0 指示不使用参考光栅器。 任何其他非零值都强制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用参考光栅器。  
  
## <a name="see-also"></a>另请参阅

- [图形呈现层](../advanced/graphics-rendering-tiers.md)
- [WPF 图形呈现疑难解答](wpf-graphics-rendering-overview.md)
