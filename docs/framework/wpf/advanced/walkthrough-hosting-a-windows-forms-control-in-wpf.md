---
title: 在 WPF 中承载 Windows 窗体控件
description: 了解如何在 Windows Presentation Foundation 中承载 Windows 窗体控件，该控件已经提供许多具有丰富功能集的控件。
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164980"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>演练：在 WPF 中承载 Windows 窗体控件

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了许多具有丰富功能集的控件。 但是，有时可能需要使用页面上 Windows 窗体控件 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 例如，您可能在现有 Windows 窗体控件中有大量投资，或者您可能有一个提供独特功能的 Windows 窗体控件。

本演练演示如何 <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> 使用代码在页面上承载 Windows 窗体控件 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。

有关本演练中所示任务的完整代码列表，请参阅[在 WPF 中承载 Windows 窗体控件示例](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)。

## <a name="prerequisites"></a>先决条件

若要完成本演练，必须具有 Visual Studio。

## <a name="hosting-the-windows-forms-control"></a>承载 Windows 窗体控件

### <a name="to-host-the-maskedtextbox-control"></a>承载 MaskedTextBox 控件

1. 创建一个名为的 WPF 应用程序项目 `HostingWfInWpf` 。

2. 添加对下列程序集的引用。

    - WindowsFormsIntegration

    - System.Windows.Forms

3. 在 WPF 设计器中打开 Mainwindow.xaml。

4. 命名 <xref:System.Windows.Controls.Grid> 元素 `grid1` 。

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. 在设计视图或 XAML 视图中，选择 <xref:System.Windows.Window> 元素。

6. 在属性窗口中，单击 "**事件**" 选项卡。

7. 双击该 <xref:System.Windows.FrameworkElement.Loaded> 事件。

8. 插入以下代码以处理 <xref:System.Windows.FrameworkElement.Loaded> 事件。

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. 在该文件的顶部，添加以下 `Imports` 或 `using` 语句。

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. 按 F5 生成并运行应用程序。

## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中设计 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [演练：使用 XAML 在 WPF 中承载 Windows 窗体控件](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [演练：在 WPF 中托管 Windows 窗体复合控件](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [演练：在 Windows 窗体中承载 WPF 复合控件](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows 窗体控件和等效的 WPF 控件](windows-forms-controls-and-equivalent-wpf-controls.md)
- [在 WPF 示例中承载 Windows 窗体控件](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
