---
title: 自动缩放
description: 了解自动缩放如何使在一台计算机上设计的窗体及其控件在另一台计算机上正确显示。
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: 93d6b9097c85d7fa7ca88b405ee3d3654e51304b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903683"
---
# <a name="automatic-scaling-in-windows-forms"></a>Windows 窗体中的自动缩放

借助自动缩放功能，在某台计算机上以某种显示分辨率或系统字体设计的窗体及其控件可以在其他计算机上以不同的显示分辨率或系统字体适当显示。 它确保窗体及其控件将以智能方式调整大小，以便与本机 Windows 以及用户和其他开发人员的计算机上的其他应用程序保持一致。 支持自动缩放和视觉样式的 .NET Framework，使 .NET Framework 应用程序与每个用户的计算机上的本机 Windows 应用程序保持一致的外观和感觉。

大多数情况下，自动缩放在 .NET Framework 版本2.0 及更高版本中按预期方式工作。 但是，字体方案更改可能会产生问题。 有关如何解决此问题的示例，请参阅[如何：在 Windows 窗体应用程序中响应字体方案更改](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md)。

## <a name="need-for-automatic-scaling"></a>需要自动缩放

若不进行自动缩放，在分辨率或字体更改时，为某个显示分辨率或字体设计的应用程序将显示太大或太小。 例如，如果应用程序是使用 Tahoma 9 point 作为基准而设计的，则在系统字体为 Tahoma 12 point 的计算机上运行时，若不进行调整它将显示太小。 与其他应用程序相比，呈现的文本元素（如标题、菜单、文本框内容等）要小一些。 此外，包含文本的用户界面 (UI) 元素（如标题栏、菜单和很多控件）的大小均取决于所使用的字体。 在此示例中，这些元素的显示也相对小一些。

如果应用程序是针对某种显示分辨率设计的，会发生类似情况。 最常见的显示分辨率为每英寸96点（DPI），这等于100% 的显示比例，但分辨率显示支持125%、150%、200% （分别等于120、144和 192 DPI），更常见。 如果不进行调整，针对某个分辨率设计的应用程序（特别是基于图形的应用程序）在其他分辨率上运行时就会显示太大或太小。

自动缩放寻求解决这些问题，方法是更具相对字体大小或显示分辨率自动调整窗体及其子控件的大小。 Windows 操作系统支持使用一种名为对话框单位的相对度量单位的自动缩放对话框。 对话框单位基于系统字体，并且它与像素的关系可由 Win32 SDK 函数 `GetDialogBaseUnits` 确定。 当用户更改 Windows 使用的主题时，所有对话框均自动进行相应调整。 此外，.NET Framework 支持根据默认系统字体或显示分辨率进行自动缩放。 或者，可在应用程序中禁用自动缩放。

## <a name="original-support-for-automatic-scaling"></a>自动缩放的初始支持

.NET Framework 的版本1.0 和1.1 支持自动缩放，这种方式依赖于 UI 使用的 Windows 默认字体（由 Win32 SDK 值**DEFAULT_GUI_FONT**表示）。 通常，此字体只在显示分辨率更改时才更改。 已使用以下机制来实现自动缩放：

1. 在设计时，将 <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> 属性（现已弃用）设置为开发人员计算机上默认系统字体的高度和宽度。

2. 在运行时，用户计算机的默认系统字体用于初始化 <xref:System.Windows.Forms.Form> 类的 <xref:System.Windows.Forms.Control.Font%2A> 属性。

3. 在显示窗体前，调用 <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> 方法以缩放窗体。 此方法计算 <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> 和 <xref:System.Windows.Forms.Control.Font%2A> 的相对缩放大小，然后调用 <xref:System.Windows.Forms.Control.Scale%2A> 方法来实际缩放窗体及其子窗体。

4. 更新 <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> 的值，以便对 <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> 的后续调用不会逐渐调整窗体大小。

虽然此机制足够实现大多数目的时，但具有以下限制：

- 由于 <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> 属性将基准字体大小表示为整数值，因此当窗体通过多个分辨率循环时，将会出现舍入误差。

- 自动缩放仅在 <xref:System.Windows.Forms.Form> 类中实现，无法在 <xref:System.Windows.Forms.ContainerControl> 类中实现。 因此，只有在用户控件的分辨率设计为与窗体的相同且在设计时置于窗体时，用户控件才可正确缩放。

- 窗体及其子控件只可由计算机分辨率相同的多名开发人员进行同时设计。 同样，如果窗体依赖与父窗体关联的分辨率，也会被继承。

- 它与 .NET Framework 版本2.0 引入的较新布局管理器（如和）不兼容 <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> 。

- 它不支持直接基于与 .NET Compact Framework 的兼容性所需的显示分辨率进行缩放。

虽然此机制保留在 .NET Framework 版本2.0 中以保持向后兼容性，但它已被下一步所述的更可靠的缩放机制所取代。 因此，<xref:System.Windows.Forms.Form.AutoScale%2A><xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>、<xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> 和某些 <xref:System.Windows.Forms.Control.Scale%2A> 重载被标记为“已过时”。

> [!NOTE]
> 将旧代码升级到 .NET Framework 版本2.0 时，可以安全删除对这些成员的引用。

## <a name="current-support-for-automatic-scaling"></a>当前支持自动缩放

.NET Framework 版本2.0 通过引入对 Windows 窗体自动缩放的以下更改来 surmounts 以前的限制：

- 基本的缩放支持已移至 <xref:System.Windows.Forms.ContainerControl> 类，以便窗体、本机复合控件和用户控件均接收一致的缩放支持。 已添加新成员 <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>、<xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>、<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> 和 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>。

- <xref:System.Windows.Forms.Control> 类还具有使其可参与缩放并支持在同一个窗体上的混合缩放的几个新成员。 特别是 <xref:System.Windows.Forms.Control.Scale%2A>、<xref:System.Windows.Forms.Control.ScaleChildren%2A> 和 <xref:System.Windows.Forms.Control.GetScaledBounds%2A> 成员支持缩放。

- 已按照 <xref:System.Windows.Forms.AutoScaleMode> 枚举定义添加基于屏幕分辨率的缩放支持以补充系统字体支持。 此模式与支持的自动缩放兼容，使应用程序迁移更轻松 .NET Compact Framework。

- 已向自动缩放实现添加与布局管理器（如 <xref:System.Windows.Forms.FlowLayoutPanel> 和 <xref:System.Windows.Forms.TableLayoutPanel>）的兼容性。

- 缩放比例现在表示为浮点值，（通常采用 <xref:System.Drawing.SizeF> 结构），以便几乎消除舍入误差。

> [!CAUTION]
> 不支持任意混合的 DPI 和字体缩放模式。 虽然你可能成功使用某种模式（例如 DPI）缩放用户控件并以另一种模式（字体）将其放在窗体上，但混合使用一种模式下的基窗体和其他模式下的派生窗体时可能导致意外结果。

### <a name="automatic-scaling-in-action"></a>自动缩放操作

Windows 窗体现在使用以下逻辑自动缩放窗体及其内容：

1. 在设计时，每个 <xref:System.Windows.Forms.ContainerControl> 分别在 <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> 和 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> 中记录缩放模式及其当前的分辨率。

2. 在运行时，实际的分辨率存储在 <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> 属性中。 <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> 属性动态计算运行时和设计时缩放分辨率之间的比率。

3. 窗体加载时，如果 <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> 和 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> 的值不同，则调用 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> 方法来缩放控件及其子项。 此方法将挂起布局并调用 <xref:System.Windows.Forms.Control.Scale%2A> 方法来执行实际缩放。 随后将更新 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> 的值以避免渐进式缩放。

4. 在以下情况下也可自动调用 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>：

    - 如果缩放模式为 <xref:System.Windows.Forms.AutoScaleMode.Font>，则响应 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 事件。

    - 当容器控件的布局继续执行并在 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> 或 <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> 属性中检测到更改时。

    - 如上所述，当父 <xref:System.Windows.Forms.ContainerControl> 正在缩放时。 每个容器控件负责使用自己的比例因子（而不是其父容器的比例因子）缩放其子控件。

5. 子控件可通过多种方式修改其缩放行为：

    - 可重写 <xref:System.Windows.Forms.Control.ScaleChildren%2A> 属性以确定是否应缩放其子控件。

    - 可重写 <xref:System.Windows.Forms.Control.GetScaledBounds%2A> 方法以调整控件缩放到的边界，但不是调整缩放逻辑。

    - 可重写 <xref:System.Windows.Forms.Control.ScaleControl%2A> 方法以更改当前控件的缩放逻辑。

## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [使用视觉样式呈现控件](./controls/rendering-controls-with-visual-styles.md)
- [如何：通过避免自动缩放来改善性能](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)
