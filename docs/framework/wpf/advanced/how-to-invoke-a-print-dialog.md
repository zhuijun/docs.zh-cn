---
title: 如何：调用打印对话框
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 75a4160366766efbd19d6e8ae26fbec102e7f95b
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924495"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="0ff3e-102">如何：调用打印对话框</span><span class="sxs-lookup"><span data-stu-id="0ff3e-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="0ff3e-103">若要提供从应用程序打印的功能，只需创建并打开对象即可 <xref:System.Windows.Controls.PrintDialog> 。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ff3e-104">示例</span><span class="sxs-lookup"><span data-stu-id="0ff3e-104">Example</span></span>  
 <span data-ttu-id="0ff3e-105"><xref:System.Windows.Controls.PrintDialog>控件为 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 、配置和 XPS 作业提交提供单一入口点。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and XPS job submission.</span></span> <span data-ttu-id="0ff3e-106">控件易于使用，并且可以通过使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 标记或代码来实例化。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="0ff3e-107">下面的示例演示如何在代码中实例化和打开控件，以及如何从代码中进行打印。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="0ff3e-108">它还显示了如何确保对话框将为用户授予设置特定页面范围的选项。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="0ff3e-109">示例代码假定在 C：驱动器的根目录中有一个文件 FixedDocumentSequence。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="0ff3e-110">对话框打开后，用户将能够从其计算机上安装的打印机中进行选择。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="0ff3e-111">他们还可以选择[MICROSOFT XPS 文档编写器](/windows/win32/printdocs/microsoft-xps-document-writer)来创建 XML 纸张规范（XPS）文件而不是打印。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-111">They will also have the option of selecting the [Microsoft XPS Document Writer](/windows/win32/printdocs/microsoft-xps-document-writer) to create an XML Paper Specification (XPS) file instead of printing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ff3e-112"><xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>本主题中讨论的 WPF 控件不应与 <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> Windows 窗体的组件混淆。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of WPF, which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="0ff3e-113">严格地说，您可以使用 <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> 方法，而不必打开对话框。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="0ff3e-114">在这种意义上，控件可用作不可见的打印组件。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="0ff3e-115">但出于性能原因，最好是使用方法，或者使用的 <xref:System.Printing.PrintQueue.AddJob%2A> 多个 <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> 和 <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> 方法之一 <xref:System.Windows.Xps.XpsDocumentWriter> 。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="0ff3e-116">有关详细信息，请参阅[以编程方式打印 XPS 文件](how-to-programmatically-print-xps-files.md)。</span><span class="sxs-lookup"><span data-stu-id="0ff3e-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff3e-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ff3e-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="0ff3e-118">WPF 中的文档</span><span class="sxs-lookup"><span data-stu-id="0ff3e-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="0ff3e-119">打印概述</span><span class="sxs-lookup"><span data-stu-id="0ff3e-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="0ff3e-120">Microsoft XPS 文档编写器</span><span class="sxs-lookup"><span data-stu-id="0ff3e-120">Microsoft XPS Document Writer</span></span>](/windows/win32/printdocs/microsoft-xps-document-writer)
