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
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="53255-103">演练：在 WPF 中承载 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="53255-103">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="53255-104">提供了许多具有丰富功能集的控件。</span><span class="sxs-lookup"><span data-stu-id="53255-104">provides many controls with a rich feature set.</span></span> <span data-ttu-id="53255-105">但是，有时可能需要使用页面上 Windows 窗体控件 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="53255-105">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="53255-106">例如，您可能在现有 Windows 窗体控件中有大量投资，或者您可能有一个提供独特功能的 Windows 窗体控件。</span><span class="sxs-lookup"><span data-stu-id="53255-106">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>

<span data-ttu-id="53255-107">本演练演示如何 <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> 使用代码在页面上承载 Windows 窗体控件 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="53255-107">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="53255-108">有关本演练中所示任务的完整代码列表，请参阅[在 WPF 中承载 Windows 窗体控件示例](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)。</span><span class="sxs-lookup"><span data-stu-id="53255-108">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="53255-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="53255-109">Prerequisites</span></span>

<span data-ttu-id="53255-110">若要完成本演练，必须具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="53255-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="53255-111">承载 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="53255-111">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="53255-112">承载 MaskedTextBox 控件</span><span class="sxs-lookup"><span data-stu-id="53255-112">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="53255-113">创建一个名为的 WPF 应用程序项目 `HostingWfInWpf` 。</span><span class="sxs-lookup"><span data-stu-id="53255-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="53255-114">添加对下列程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="53255-114">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="53255-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="53255-115">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="53255-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="53255-116">System.Windows.Forms</span></span>

3. <span data-ttu-id="53255-117">在 WPF 设计器中打开 Mainwindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="53255-117">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="53255-118">命名 <xref:System.Windows.Controls.Grid> 元素 `grid1` 。</span><span class="sxs-lookup"><span data-stu-id="53255-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="53255-119">在设计视图或 XAML 视图中，选择 <xref:System.Windows.Window> 元素。</span><span class="sxs-lookup"><span data-stu-id="53255-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="53255-120">在属性窗口中，单击 "**事件**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="53255-120">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="53255-121">双击该 <xref:System.Windows.FrameworkElement.Loaded> 事件。</span><span class="sxs-lookup"><span data-stu-id="53255-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="53255-122">插入以下代码以处理 <xref:System.Windows.FrameworkElement.Loaded> 事件。</span><span class="sxs-lookup"><span data-stu-id="53255-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="53255-123">在该文件的顶部，添加以下 `Imports` 或 `using` 语句。</span><span class="sxs-lookup"><span data-stu-id="53255-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="53255-124">按 F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="53255-124">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="53255-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53255-125">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="53255-126">在 Visual Studio 中设计 XAML</span><span class="sxs-lookup"><span data-stu-id="53255-126">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="53255-127">演练：使用 XAML 在 WPF 中承载 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="53255-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="53255-128">演练：在 WPF 中托管 Windows 窗体复合控件</span><span class="sxs-lookup"><span data-stu-id="53255-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="53255-129">演练：在 Windows 窗体中承载 WPF 复合控件</span><span class="sxs-lookup"><span data-stu-id="53255-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="53255-130">Windows 窗体控件和等效的 WPF 控件</span><span class="sxs-lookup"><span data-stu-id="53255-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="53255-131">在 WPF 示例中承载 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="53255-131">Hosting a Windows Forms Control in WPF Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
