---
title: 对话框概述
description: 了解可用于收集和显示信息的 Windows Foundation 演示文稿（WPF）中的各种对话框。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
ms.openlocfilehash: 822604dd694f2f6260496872fd7a1a8440a62535
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618137"
---
# <a name="dialog-boxes-overview"></a><span data-ttu-id="b3090-103">对话框概述</span><span class="sxs-lookup"><span data-stu-id="b3090-103">Dialog boxes overview</span></span>
<span data-ttu-id="b3090-104">独立的应用程序通常具有主窗口，该窗口显示应用程序操作的主数据，并公开功能以便通过 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 菜单栏、工具栏和状态栏等机制来处理这些数据。</span><span class="sxs-lookup"><span data-stu-id="b3090-104">Standalone applications typically have a main window that both displays the main data over which the application operates and exposes the functionality to process that data through [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mechanisms like menu bars, tool bars, and status bars.</span></span> <span data-ttu-id="b3090-105">重要的应用程序可能还会显示其他窗口来执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b3090-105">A non-trivial application may also display additional windows to do the following:</span></span>  
  
- <span data-ttu-id="b3090-106">向用户显示特定信息。</span><span class="sxs-lookup"><span data-stu-id="b3090-106">Display specific information to users.</span></span>  
  
- <span data-ttu-id="b3090-107">从用户处收集信息。</span><span class="sxs-lookup"><span data-stu-id="b3090-107">Gather information from users.</span></span>  
  
- <span data-ttu-id="b3090-108">同时显示并收集信息。</span><span class="sxs-lookup"><span data-stu-id="b3090-108">Both display and gather information.</span></span>  
  
 <span data-ttu-id="b3090-109">这些类型的 windows 称为*对话框*，有两种类型：模式和无模式。</span><span class="sxs-lookup"><span data-stu-id="b3090-109">These types of windows are known as *dialog boxes*, and there are two types: modal and modeless.</span></span>  
  
 <span data-ttu-id="b3090-110">当函数需要用户的其他数据继续时，该函数将显示一个*模式*对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-110">A *modal* dialog box is displayed by a function when the function needs additional data from a user to continue.</span></span> <span data-ttu-id="b3090-111">由于函数依赖于模式对话框收集数据，模式对话框还会在其保持打开状态时防止用户激活应用程序中的其他窗口。</span><span class="sxs-lookup"><span data-stu-id="b3090-111">Because the function depends on the modal dialog box to gather data, the modal dialog box also prevents a user from activating other windows in the application while it remains open.</span></span> <span data-ttu-id="b3090-112">在大多数情况下，通过按 **"确定" 或 "** **取消**" 按钮，用户可以通过模式对话框使用模式对话框发出的信号。</span><span class="sxs-lookup"><span data-stu-id="b3090-112">In most cases, a modal dialog box allows a user to signal when they have finished with the modal dialog box by pressing either an **OK** or **Cancel** button.</span></span> <span data-ttu-id="b3090-113">按 **"确定"** 按钮表示用户已输入数据，并希望该函数继续处理该数据。</span><span class="sxs-lookup"><span data-stu-id="b3090-113">Pressing the **OK** button indicates that a user has entered data and wants the function to continue processing with that data.</span></span> <span data-ttu-id="b3090-114">按 "**取消**" 按钮表示用户要停止执行该函数。</span><span class="sxs-lookup"><span data-stu-id="b3090-114">Pressing the **Cancel** button indicates that a user wants to stop the function from executing altogether.</span></span> <span data-ttu-id="b3090-115">最常见的模式对话框示例显示为可以打开、保存并打印数据。</span><span class="sxs-lookup"><span data-stu-id="b3090-115">The most common examples of modal dialog boxes are shown to open, save, and print data.</span></span>  
  
 <span data-ttu-id="b3090-116">另一方面，*无模式*对话框不会阻止用户在打开时激活其他窗口。</span><span class="sxs-lookup"><span data-stu-id="b3090-116">A *modeless* dialog box, on the other hand, does not prevent a user from activating other windows while it is open.</span></span> <span data-ttu-id="b3090-117">例如，如果用户想要在某个文档中查找特定字的出现次数，主窗口通常会打开一个对话框，询问用户要查找的字是什么。</span><span class="sxs-lookup"><span data-stu-id="b3090-117">For example, if a user wants to find occurrences of a particular word in a document, a main window will often open a dialog box to ask a user what word they are looking for.</span></span> <span data-ttu-id="b3090-118">查找字并不会防止用户编辑文档，因此对话框无需为模式对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-118">Since finding a word doesn't prevent a user from editing the document, however, the dialog box doesn't need to be modal.</span></span> <span data-ttu-id="b3090-119">无模式对话框至少提供了一个关闭对话框的 "**关闭**" 按钮，还可以提供用于执行特定功能的其他按钮，如 "**查找下**一个" 按钮，以查找下一个与搜索条件匹配的单词。</span><span class="sxs-lookup"><span data-stu-id="b3090-119">A modeless dialog box at least provides a **Close** button to close the dialog box, and may provide additional buttons to execute specific functions, such as a **Find Next** button to find the next word that matches the find criteria of a word search.</span></span>  
  
 <span data-ttu-id="b3090-120">Windows Presentation Foundation （WPF）允许您创建几种类型的对话框，包括消息框、通用对话框和自定义对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-120">Windows Presentation Foundation (WPF) allows you to create several types of dialog boxes, including message boxes, common dialog boxes, and custom dialog boxes.</span></span> <span data-ttu-id="b3090-121">本主题将讨论每个，[对话框示例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)提供了匹配的示例。</span><span class="sxs-lookup"><span data-stu-id="b3090-121">This topic discusses each, and the [Dialog Box Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) provides matching examples.</span></span>  

<a name="Message_Boxes"></a>
## <a name="message-boxes"></a><span data-ttu-id="b3090-122">消息框</span><span class="sxs-lookup"><span data-stu-id="b3090-122">Message boxes</span></span>  
 <span data-ttu-id="b3090-123">*消息框*是一个对话框，可用于显示文本信息，并允许用户通过按钮做出决定。</span><span class="sxs-lookup"><span data-stu-id="b3090-123">A *message box* is a dialog box that can be used to display textual information and to allow users to make decisions with buttons.</span></span> <span data-ttu-id="b3090-124">下图显示的消息框显示文本信息、提出问题并向用户提供了三个按钮来回答问题。</span><span class="sxs-lookup"><span data-stu-id="b3090-124">The following figure shows a message box that displays textual information, asks a question, and provides the user with three buttons to answer the question.</span></span>  
  
 ![一个 "字处理器" 对话框，询问您是否要在应用程序关闭之前保存对文档所做的更改。](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 <span data-ttu-id="b3090-126">若要创建消息框，请使用 <xref:System.Windows.MessageBox> 类。</span><span class="sxs-lookup"><span data-stu-id="b3090-126">To create a message box, you use the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="b3090-127"><xref:System.Windows.MessageBox>允许使用如下所示的代码配置消息框文本、标题、图标和按钮。</span><span class="sxs-lookup"><span data-stu-id="b3090-127"><xref:System.Windows.MessageBox> lets you configure the message box text, title, icon, and buttons, using code like the following.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 <span data-ttu-id="b3090-128">若要显示消息框，请调用 `static` <xref:System.Windows.MessageBox.Show%2A> 方法，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="b3090-128">To show a message box, you call the `static`<xref:System.Windows.MessageBox.Show%2A> method, as demonstrated in the following code.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 <span data-ttu-id="b3090-129">当显示消息框的代码需要检测并处理用户决定（按下了哪个按钮）时，该代码可以检查消息框的结果，如以下代码中所示。</span><span class="sxs-lookup"><span data-stu-id="b3090-129">When code that shows a message box needs to detect and process the user's decision (which button was pressed), the code can inspect the message box result, as shown in the following code.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 <span data-ttu-id="b3090-130">有关使用消息框的详细信息，请参阅 <xref:System.Windows.MessageBox> 、 [MessageBox 示例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)和[对话框示例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)。</span><span class="sxs-lookup"><span data-stu-id="b3090-130">For more information on using message boxes, see <xref:System.Windows.MessageBox>, [MessageBox Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox), and [Dialog Box Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox).</span></span>  
  
 <span data-ttu-id="b3090-131">尽管 <xref:System.Windows.MessageBox> 可能提供了一个简单的对话框用户体验，但使用的优点 <xref:System.Windows.MessageBox> 是，这是唯一一种可由在部分信任安全沙箱中运行的应用程序（请参阅[安全性](../security-wpf.md)）（如 XAML 浏览器应用程序（xbap））显示的窗口。</span><span class="sxs-lookup"><span data-stu-id="b3090-131">Although <xref:System.Windows.MessageBox> may offer a simple dialog box user experience, the advantage of using <xref:System.Windows.MessageBox> is that is the only type of window that can be shown by applications that run within a partial trust security sandbox (see [Security](../security-wpf.md)), such as XAML browser applications (XBAPs).</span></span>  
  
 <span data-ttu-id="b3090-132">大多数对话框显示和收集比消息框结果更复杂的数据，包括文本、选项（复选框）、互斥选项（单选按钮）和列表选项（列表框、组合框、下拉列表框）。</span><span class="sxs-lookup"><span data-stu-id="b3090-132">Most dialog boxes display and gather more complex data than the result of a message box, including text, selection (check boxes), mutually exclusive selection (radio buttons), and list selection (list boxes, combo boxes, drop-down list boxes).</span></span> <span data-ttu-id="b3090-133">对于这些应用程序，Windows Presentation Foundation （WPF）提供了几个常见对话框，并允许您创建自己的对话框，但使用完全信任的应用程序仅限于运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="b3090-133">For these, Windows Presentation Foundation (WPF) provides several common dialog boxes and allows you to create your own dialog boxes, although the use of either is limited to applications running with full trust.</span></span>  
  
<a name="Common_Dialogs"></a>
## <a name="common-dialog-boxes"></a><span data-ttu-id="b3090-134">通用对话框</span><span class="sxs-lookup"><span data-stu-id="b3090-134">Common dialog boxes</span></span>  
 <span data-ttu-id="b3090-135">Windows 实现了各种适用于所有应用程序的可重复使用的对话框，包括打开文件、保存文件和打印的对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-135">Windows implements a variety of reusable dialog boxes that are common to all applications, including dialog boxes for opening files, saving files, and printing.</span></span> <span data-ttu-id="b3090-136">这些对话框由操作系统实现，因此可以在运行于该操作系统上的所有应用程序之间共享，这对用户体验的一致性很有帮助；当用户熟悉一个应用程序中操作系统所提供的对话框时，他们就无需再去了解如何在其他应用程序中使用该对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-136">Since these dialog boxes are implemented by the operating system, they can be shared among all the applications that run on the operating system, which helps user experience consistency; when users are familiar with the use of an operating system-provided dialog box in one application, they don't need to learn how to use that dialog box in other applications.</span></span> <span data-ttu-id="b3090-137">由于这些对话框可用于所有应用程序，并且它们有助于提供一致的用户体验，因此它们被称为*通用对话框*。</span><span class="sxs-lookup"><span data-stu-id="b3090-137">Because these dialog boxes are available to all applications and because they help provide a consistent user experience, they are known as *common dialog boxes*.</span></span>  
  
 <span data-ttu-id="b3090-138">Windows Presentation Foundation （WPF）封装打开的文件、保存文件和打印通用对话框，并将其作为托管类公开，以便您在独立的应用程序中使用。</span><span class="sxs-lookup"><span data-stu-id="b3090-138">Windows Presentation Foundation (WPF) encapsulates the open file, save file, and print common dialog boxes and exposes them as managed classes for you to use in standalone applications.</span></span> <span data-ttu-id="b3090-139">本主题提供每个通用对话框的简要概述。</span><span class="sxs-lookup"><span data-stu-id="b3090-139">This topic provides a brief overview of each.</span></span>  
  
<a name="Open_File_Dialog"></a>
### <a name="open-file-dialog"></a><span data-ttu-id="b3090-140">"打开文件" 对话框</span><span class="sxs-lookup"><span data-stu-id="b3090-140">Open File dialog</span></span>  
 <span data-ttu-id="b3090-141">如下图中所示的打开文件对话框由文件打开功能用于检索要打开文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b3090-141">The open file dialog box, shown in the following figure, is used by file opening functionality to retrieve the name of a file to open.</span></span>  
  
 ![显示要检索文件的位置的打开对话框。](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 <span data-ttu-id="b3090-143">通用的 "打开文件" 对话框作为类实现 <xref:Microsoft.Win32.OpenFileDialog> ，位于 <xref:Microsoft.Win32> 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="b3090-143">The common open file dialog box is implemented as the <xref:Microsoft.Win32.OpenFileDialog> class and is located in the <xref:Microsoft.Win32> namespace.</span></span> <span data-ttu-id="b3090-144">以下代码显示了如何创建、配置和显示打开文件对话框以及如何处理结果。</span><span class="sxs-lookup"><span data-stu-id="b3090-144">The following code shows how to create, configure, and show one, and how to process the result.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 <span data-ttu-id="b3090-145">有关 "打开文件" 对话框的详细信息，请参阅 <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b3090-145">For more information on the open file dialog box, see <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3090-146"><xref:Microsoft.Win32.OpenFileDialog>可用于安全地检索使用部分信任运行的应用程序的文件名（请参阅[安全性](../security-wpf.md)）。</span><span class="sxs-lookup"><span data-stu-id="b3090-146"><xref:Microsoft.Win32.OpenFileDialog> can be used to safely retrieve file names by applications running with partial trust (see [Security](../security-wpf.md)).</span></span>  
  
<a name="Save_File_Dialog"></a>
### <a name="save-file-dialog-box"></a><span data-ttu-id="b3090-147">保存文件对话框</span><span class="sxs-lookup"><span data-stu-id="b3090-147">Save File dialog box</span></span>  
 <span data-ttu-id="b3090-148">如下图中所示的保存文件对话框由文件保存功能用以检索要保存的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b3090-148">The save file dialog box, shown in the following figure, is used by file saving functionality to retrieve the name of a file to save.</span></span>  
  
 ![显示文件保存位置的 "另存为" 对话框。](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 <span data-ttu-id="b3090-150">"公共保存文件" 对话框作为 <xref:Microsoft.Win32.SaveFileDialog> 类实现，位于 <xref:Microsoft.Win32> 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="b3090-150">The common save file dialog box is implemented as the <xref:Microsoft.Win32.SaveFileDialog> class, and is located in the <xref:Microsoft.Win32> namespace.</span></span> <span data-ttu-id="b3090-151">以下代码显示了如何创建、配置和显示打开文件对话框以及如何处理结果。</span><span class="sxs-lookup"><span data-stu-id="b3090-151">The following code shows how to create, configure, and show one, and how to process the result.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 <span data-ttu-id="b3090-152">有关 "保存文件" 对话框的详细信息，请参阅 <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b3090-152">For more information on the save file dialog box, see <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.</span></span>  
  
<a name="Print_Dialog"></a>
### <a name="print-dialog-box"></a><span data-ttu-id="b3090-153">“打印”对话框</span><span class="sxs-lookup"><span data-stu-id="b3090-153">Print dialog box</span></span>

<span data-ttu-id="b3090-154">如下图中所示的打印对话框由打印功能用以选择和配置用户想要将数据打印到的打印机。</span><span class="sxs-lookup"><span data-stu-id="b3090-154">The print dialog box, shown in the following figure, is used by printing functionality to choose and configure the printer that a user would like to print data to.</span></span>  
  
![显示 "打印" 对话框的屏幕截图。](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
<span data-ttu-id="b3090-156">常见的 "打印" 对话框作为类实现 <xref:System.Windows.Controls.PrintDialog> ，位于 <xref:System.Windows.Controls> 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="b3090-156">The common print dialog box is implemented as the <xref:System.Windows.Controls.PrintDialog> class, and is located in the <xref:System.Windows.Controls> namespace.</span></span> <span data-ttu-id="b3090-157">以下代码显示了如何创建、配置和显示打印对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-157">The following code shows how to create, configure, and show one.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 <span data-ttu-id="b3090-158">有关 "打印" 对话框的详细信息，请参阅 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b3090-158">For more information on the print dialog box, see <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b3090-159">有关在 WPF 中打印的详细讨论，请参阅[打印概述](../advanced/printing-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b3090-159">For detailed discussion of printing in WPF, see [Printing Overview](../advanced/printing-overview.md).</span></span>  
  
<a name="Custom_Dialog_Boxes"></a>
## <a name="custom-dialog-boxes"></a><span data-ttu-id="b3090-160">自定义对话框</span><span class="sxs-lookup"><span data-stu-id="b3090-160">Custom dialog boxes</span></span>

<span data-ttu-id="b3090-161">尽管通用对话框很有用并应尽可能使用，但它们并不支持特定于域的对话框的要求。</span><span class="sxs-lookup"><span data-stu-id="b3090-161">While common dialog boxes are useful, and should be used when possible, they do not support the requirements of domain-specific dialog boxes.</span></span> <span data-ttu-id="b3090-162">在这些情况下，就需要创建自己的对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-162">In these cases, you need to create your own dialog boxes.</span></span> <span data-ttu-id="b3090-163">如我们所见，对话框是具有特殊行为的窗口。</span><span class="sxs-lookup"><span data-stu-id="b3090-163">As we'll see, a dialog box is a window with special behaviors.</span></span> <span data-ttu-id="b3090-164"><xref:System.Windows.Window>实现这些行为，因此，您可以使用 <xref:System.Windows.Window> 创建自定义的模式对话框和无模式对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-164"><xref:System.Windows.Window> implements those behaviors and, consequently, you use <xref:System.Windows.Window> to create custom modal and modeless dialog boxes.</span></span>  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>
### <a name="creating-a-modal-custom-dialog-box"></a><span data-ttu-id="b3090-165">创建模式自定义对话框</span><span class="sxs-lookup"><span data-stu-id="b3090-165">Creating a modal custom dialog box</span></span>

<span data-ttu-id="b3090-166">本主题说明如何使用 <xref:System.Windows.Window> 对话框作为示例来创建典型的模式对话框实现 `Margins` （请参阅[对话框示例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)）。</span><span class="sxs-lookup"><span data-stu-id="b3090-166">This topic shows how to use <xref:System.Windows.Window> to create a typical modal dialog box implementation, using the `Margins` dialog box as an example (see [Dialog Box Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)).</span></span> <span data-ttu-id="b3090-167">`Margins`下图显示了该对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-167">The `Margins` dialog box is shown in the following figure.</span></span>  
  
 !["边距" 对话框，其中包含用于定义左边距、上边距、右边距和下边距的字段。](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a><span data-ttu-id="b3090-169">配置模式对话框</span><span class="sxs-lookup"><span data-stu-id="b3090-169">Configuring a modal dialog box</span></span>

<span data-ttu-id="b3090-170">典型对话框的用户界面包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="b3090-170">The user interface for a typical dialog box includes the following:</span></span>  
  
- <span data-ttu-id="b3090-171">收集所需数据要求的各种控件。</span><span class="sxs-lookup"><span data-stu-id="b3090-171">The various controls that are required to gather the desired data.</span></span>  
  
- <span data-ttu-id="b3090-172">用户单击以关闭对话框、返回到函数并继续处理的 **"确定"** 按钮。</span><span class="sxs-lookup"><span data-stu-id="b3090-172">An **OK** button that users click to close the dialog box, return to the function, and continue processing.</span></span>  
  
- <span data-ttu-id="b3090-173">一个 "**取消**" 按钮，用户单击该按钮可关闭对话框并停止该函数进一步处理。</span><span class="sxs-lookup"><span data-stu-id="b3090-173">A **Cancel** button that users click to close the dialog box and stop the function from further processing.</span></span>  
  
- <span data-ttu-id="b3090-174">标题栏中的 "**关闭**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b3090-174">A **Close** button in the title bar.</span></span>  
  
- <span data-ttu-id="b3090-175">图标。</span><span class="sxs-lookup"><span data-stu-id="b3090-175">An icon.</span></span>  
  
- <span data-ttu-id="b3090-176">**最小化**、**最大化**和**还原**按钮。</span><span class="sxs-lookup"><span data-stu-id="b3090-176">**Minimize**, **Maximize**, and **Restore** buttons.</span></span>  
  
- <span data-ttu-id="b3090-177">最小化、最大化、还原和关闭对话框的**系统**菜单。</span><span class="sxs-lookup"><span data-stu-id="b3090-177">A **System** menu to minimize, maximize, restore, and close the dialog box.</span></span>  
  
- <span data-ttu-id="b3090-178">打开对话框的窗口上方和中心的位置。</span><span class="sxs-lookup"><span data-stu-id="b3090-178">A position above and in the center of the window that opened the dialog box.</span></span>  
  
- <span data-ttu-id="b3090-179">能够在可能的情况下调整大小，以防止对话框太小，并为用户提供有用的默认大小。</span><span class="sxs-lookup"><span data-stu-id="b3090-179">The ability to be resized where possible to prevent the dialog box from being too small, and to provide the user with a useful default size.</span></span> <span data-ttu-id="b3090-180">这要求您同时设置默认维度和最小维度。</span><span class="sxs-lookup"><span data-stu-id="b3090-180">This requires that you set both the default and a minimum dimensions.</span></span>  
  
- <span data-ttu-id="b3090-181">用来使 "**取消**" 按钮按下的键盘快捷方式。</span><span class="sxs-lookup"><span data-stu-id="b3090-181">The ESC key as a keyboard shortcut that causes the **Cancel** button to be pressed.</span></span> <span data-ttu-id="b3090-182">可以通过将 <xref:System.Windows.Controls.Button.IsCancel%2A> "**取消**" 按钮的属性设置为来执行此操作 `true` 。</span><span class="sxs-lookup"><span data-stu-id="b3090-182">You do this by setting the <xref:System.Windows.Controls.Button.IsCancel%2A> property of the **Cancel** button to `true`.</span></span>  
  
- <span data-ttu-id="b3090-183">输入（或返回）键的键盘快捷方式，使 **"确定"** 按钮处于按下状态。</span><span class="sxs-lookup"><span data-stu-id="b3090-183">The ENTER (or RETURN) key as a keyboard shortcut that causes the **OK** button to be pressed.</span></span> <span data-ttu-id="b3090-184">可以通过设置 <xref:System.Windows.Controls.Button.IsDefault%2A> **"确定"** 按钮的属性来执行此操作 `true` 。</span><span class="sxs-lookup"><span data-stu-id="b3090-184">You do this by setting the <xref:System.Windows.Controls.Button.IsDefault%2A> property of the **OK** button `true`.</span></span>  
  
<span data-ttu-id="b3090-185">以下代码演示了这种配置。</span><span class="sxs-lookup"><span data-stu-id="b3090-185">The following code demonstrates this configuration.</span></span>  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
<span data-ttu-id="b3090-186">对话框用户体验还扩展到打开对话框的窗口菜单栏。</span><span class="sxs-lookup"><span data-stu-id="b3090-186">The user experience for a dialog box also extends into the menu bar of the window that opens the dialog box.</span></span> <span data-ttu-id="b3090-187">当菜单项运行需要用户通过对话框交互才能继续运行的函数时，函数的菜单项标题上会有一个省略号，如此处所示。</span><span class="sxs-lookup"><span data-stu-id="b3090-187">When a menu item runs a function that requires user interaction through a dialog box before the function can continue, the menu item for the function will have an ellipsis in its header, as shown here.</span></span>  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
<span data-ttu-id="b3090-188">当菜单项运行的函数显示无需用户交互的对话框（如“关于”对话框）时，则不需要省略号。</span><span class="sxs-lookup"><span data-stu-id="b3090-188">When a menu item runs a function that displays a dialog box which does not require user interaction, such as an About dialog box, an ellipsis is not required.</span></span>  
  
#### <a name="opening-a-modal-dialog-box"></a><span data-ttu-id="b3090-189">打开模式对话框</span><span class="sxs-lookup"><span data-stu-id="b3090-189">Opening a modal dialog box</span></span>

<span data-ttu-id="b3090-190">对话框通常显示为用户选择菜单项来执行特定于域的函数的结果，比如在字处理器中设置文档边距。</span><span class="sxs-lookup"><span data-stu-id="b3090-190">A dialog box is typically shown as a result of a user selecting a menu item to perform a domain-specific function, such as setting the margins of a document in a word processor.</span></span> <span data-ttu-id="b3090-191">将窗口显示为对话框类似于显示普通窗口，只是它需要其他特定于对话框的配置。</span><span class="sxs-lookup"><span data-stu-id="b3090-191">Showing a window as a dialog box is similar to showing a normal window, although it requires additional dialog box-specific configuration.</span></span> <span data-ttu-id="b3090-192">以下代码中显示了实例化、配置和打开对话框的整个过程。</span><span class="sxs-lookup"><span data-stu-id="b3090-192">The entire process of instantiating, configuring, and opening a dialog box is shown in the following code.</span></span>  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

<span data-ttu-id="b3090-193">此处的代码将默认信息（当前边距）传递到对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-193">Here, the code passes default information (the current margins) to the dialog box.</span></span> <span data-ttu-id="b3090-194">它还将 <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> 属性设置为对显示对话框的窗口的引用。</span><span class="sxs-lookup"><span data-stu-id="b3090-194">It also sets the <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> property with a reference to the window that is showing the dialog box.</span></span> <span data-ttu-id="b3090-195">通常，您应始终设置一个对话框的所有者，以提供对所有对话框均通用的窗口状态相关行为（有关详细信息，请参阅[WPF Windows 概述](wpf-windows-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="b3090-195">In general, you should always set the owner for a dialog box to provide window state-related behaviors that are common to all dialog boxes (see [WPF Windows Overview](wpf-windows-overview.md) for more information).</span></span>

> [!NOTE]
> <span data-ttu-id="b3090-196">必须提供所有者才能支持对话框的用户界面（UI）自动化（请参阅[UI 自动化概述](../../ui-automation/ui-automation-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="b3090-196">You must provide an owner to support user interface (UI) automation for dialog boxes (see [UI Automation Overview](../../ui-automation/ui-automation-overview.md)).</span></span>

<span data-ttu-id="b3090-197">对话框配置完成后，将通过调用方法以模式方式显示该对话框 <xref:System.Windows.Window.ShowDialog%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b3090-197">After the dialog box is configured, it is shown modally by calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span>  
  
#### <a name="validating-user-provided-data"></a><span data-ttu-id="b3090-198">验证用户提供的数据</span><span class="sxs-lookup"><span data-stu-id="b3090-198">Validating user-provided data</span></span>

<span data-ttu-id="b3090-199">当打开对话框并且用户提供所需数据时，对话框出于以下原因负责确保提供的数据有效：</span><span class="sxs-lookup"><span data-stu-id="b3090-199">When a dialog box is opened and the user provides the required data, a dialog box is responsible for ensuring that the provided data is valid for the following reasons:</span></span>  
  
- <span data-ttu-id="b3090-200">从安全角度，应该验证所有输入。</span><span class="sxs-lookup"><span data-stu-id="b3090-200">From a security perspective, all input should be validated.</span></span>  
  
- <span data-ttu-id="b3090-201">从特定于域的角度，数据验证可以防止代码处理错误数据，这可能引发异常。</span><span class="sxs-lookup"><span data-stu-id="b3090-201">From a domain-specific perspective, data validation prevents erroneous data from being processed by the code, which could potentially throw exceptions.</span></span>  
  
- <span data-ttu-id="b3090-202">从用户体验角度，对话框可以帮助用户显示他们输入的哪些数据无效。</span><span class="sxs-lookup"><span data-stu-id="b3090-202">From a user-experience perspective, a dialog box can help users by showing them which data they have entered is invalid.</span></span>  
  
- <span data-ttu-id="b3090-203">从性能角度，多层应用程序中的数据验证可以减少客户端和应用程序层之间的往返次数，尤其当应用程序由 Web 服务或基于服务器的数据库构成时。</span><span class="sxs-lookup"><span data-stu-id="b3090-203">From a performance perspective, data validation in a multi-tier application can reduce the number of round trips between the client and the application tiers, particularly when the application is composed of Web services or server-based databases.</span></span>  

<span data-ttu-id="b3090-204">若要在 WPF 中验证绑定的控件，需要定义一个验证规则并将其与绑定相关联。</span><span class="sxs-lookup"><span data-stu-id="b3090-204">To validate a bound control in WPF, you need to define a validation rule and associate it with the binding.</span></span> <span data-ttu-id="b3090-205">验证规则是派生自的自定义类 <xref:System.Windows.Controls.ValidationRule> 。</span><span class="sxs-lookup"><span data-stu-id="b3090-205">A validation rule is a custom class that derives from <xref:System.Windows.Controls.ValidationRule>.</span></span> <span data-ttu-id="b3090-206">下面的示例演示了一个验证规则， `MarginValidationRule` 该规则检查绑定值是否为 <xref:System.Double> 并且在指定的范围内。</span><span class="sxs-lookup"><span data-stu-id="b3090-206">The following example shows a validation rule, `MarginValidationRule`, which checks that a bound value is a <xref:System.Double> and is within a specified range.</span></span>  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

<span data-ttu-id="b3090-207">在此代码中，验证规则的验证逻辑是通过重写方法来实现的 <xref:System.Windows.Controls.ValidationRule.Validate%2A> ，该方法将验证数据并返回相应的 <xref:System.Windows.Controls.ValidationResult> 。</span><span class="sxs-lookup"><span data-stu-id="b3090-207">In this code, the validation logic of a validation rule is implemented by overriding the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method, which validates the data and returns an appropriate <xref:System.Windows.Controls.ValidationResult>.</span></span>  

<span data-ttu-id="b3090-208">要将验证规则与绑定控件进行关联，可以使用以下标记。</span><span class="sxs-lookup"><span data-stu-id="b3090-208">To associate the validation rule with the bound control, you use the following markup.</span></span>  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

<span data-ttu-id="b3090-209">一旦将验证规则关联，WPF 就会在将数据输入绑定控件时自动应用它。</span><span class="sxs-lookup"><span data-stu-id="b3090-209">Once the validation rule is associated, WPF will automatically apply it when data is entered into the bound control.</span></span> <span data-ttu-id="b3090-210">当控件包含无效数据时，WPF 将在无效控件周围显示红色边框，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="b3090-210">When a control contains invalid data, WPF will display a red border around the invalid control, as shown in the following figure.</span></span>  
  
!["边距" 对话框，其中包含一条围绕无效左边距值的红色边框。](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

<span data-ttu-id="b3090-212">在用户输入有效数据之前，WPF 不会将用户限制为无效控件。</span><span class="sxs-lookup"><span data-stu-id="b3090-212">WPF does not restrict a user to the invalid control until they have entered valid data.</span></span> <span data-ttu-id="b3090-213">这对于对话框来说很好，无论数据是否有效用户都应该可以自由导航到对话框中的控件。</span><span class="sxs-lookup"><span data-stu-id="b3090-213">This is good behavior for a dialog box; a user should be able to freely navigate the controls in a dialog box whether or not data is valid.</span></span> <span data-ttu-id="b3090-214">但是，这意味着用户可以输入无效数据，并按 **"确定"** 按钮。</span><span class="sxs-lookup"><span data-stu-id="b3090-214">However, this means a user can enter invalid data and press the **OK** button.</span></span> <span data-ttu-id="b3090-215">出于此原因，当按下 **"确定"** 按钮时，您的代码还需要通过处理事件来验证对话框中的所有控件 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 。</span><span class="sxs-lookup"><span data-stu-id="b3090-215">For this reason, your code also needs to validate all controls in a dialog box when the **OK** button is pressed by handling the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

<span data-ttu-id="b3090-216">此代码枚举窗口上的所有依赖项对象，如果任何对象无效（由返回 <xref:System.Windows.Controls.Validation.GetHasError%2A> ，则无效的控件获得焦点，该 `IsValid` 方法将返回 `false` ，并且该窗口被视为无效。</span><span class="sxs-lookup"><span data-stu-id="b3090-216">This code enumerates all dependency objects on a window and, if any are invalid (as returned by <xref:System.Windows.Controls.Validation.GetHasError%2A>, the invalid control gets the focus, the `IsValid` method returns `false`, and the window is considered invalid.</span></span>  
  
<span data-ttu-id="b3090-217">一旦对话框有效，就可以安全关闭并返回。</span><span class="sxs-lookup"><span data-stu-id="b3090-217">Once a dialog box is valid, it can safely close and return.</span></span> <span data-ttu-id="b3090-218">作为返回过程的一部分，需要将结果返回到调用函数。</span><span class="sxs-lookup"><span data-stu-id="b3090-218">As part of the return process, it needs to return a result to the calling function.</span></span>  
  
#### <a name="setting-the-modal-dialog-result"></a><span data-ttu-id="b3090-219">设置模式对话框结果</span><span class="sxs-lookup"><span data-stu-id="b3090-219">Setting the modal dialog result</span></span>

<span data-ttu-id="b3090-220">使用打开对话框 <xref:System.Windows.Window.ShowDialog%2A> 的方法与调用方法类似：使用等待打开对话框的代码 <xref:System.Windows.Window.ShowDialog%2A> 直到 <xref:System.Windows.Window.ShowDialog%2A> 返回。</span><span class="sxs-lookup"><span data-stu-id="b3090-220">Opening a dialog box using <xref:System.Windows.Window.ShowDialog%2A> is fundamentally like calling a method: the code that opened the dialog box using <xref:System.Windows.Window.ShowDialog%2A> waits until <xref:System.Windows.Window.ShowDialog%2A> returns.</span></span> <span data-ttu-id="b3090-221">当 <xref:System.Windows.Window.ShowDialog%2A> 返回时，调用它的代码需要根据用户是按下 "**确定"** 按钮还是 "**取消**" 按钮来决定是继续处理还是停止处理。</span><span class="sxs-lookup"><span data-stu-id="b3090-221">When <xref:System.Windows.Window.ShowDialog%2A> returns, the code that called it needs to decide whether to continue processing or stop processing, based on whether the user pressed the **OK** button or the **Cancel** button.</span></span> <span data-ttu-id="b3090-222">为了便于此决定，此对话框需要将用户的选择返回为 <xref:System.Boolean> 从方法返回的值 <xref:System.Windows.Window.ShowDialog%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b3090-222">To facilitate this decision, the dialog box needs to return the user's choice as a <xref:System.Boolean> value that is returned from the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span>  

<span data-ttu-id="b3090-223">单击 **"确定"** 按钮后， <xref:System.Windows.Window.ShowDialog%2A> 应返回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="b3090-223">When the **OK** button is clicked, <xref:System.Windows.Window.ShowDialog%2A> should return `true`.</span></span> <span data-ttu-id="b3090-224">这是通过 <xref:System.Windows.Window.DialogResult%2A> 在单击 **"确定"** 按钮时设置对话框的属性来实现的。</span><span class="sxs-lookup"><span data-stu-id="b3090-224">This is achieved by setting the <xref:System.Windows.Window.DialogResult%2A> property of the dialog box when the **OK** button is clicked.</span></span>  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

<span data-ttu-id="b3090-225">请注意，设置 <xref:System.Windows.Window.DialogResult%2A> 属性还会使窗口自动关闭，从而减少了显式调用的需要 <xref:System.Windows.Window.Close%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b3090-225">Note that setting the <xref:System.Windows.Window.DialogResult%2A> property also causes the window to close automatically, which alleviates the need to explicitly call <xref:System.Windows.Window.Close%2A>.</span></span>  
  
<span data-ttu-id="b3090-226">单击 "**取消**" 按钮后， <xref:System.Windows.Window.ShowDialog%2A> 应返回 `false` ，这也需要设置 <xref:System.Windows.Window.DialogResult%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="b3090-226">When the **Cancel** button is clicked, <xref:System.Windows.Window.ShowDialog%2A> should return `false`, which also requires setting the <xref:System.Windows.Window.DialogResult%2A> property.</span></span>  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

<span data-ttu-id="b3090-227">当按钮的 <xref:System.Windows.Controls.Button.IsCancel%2A> 属性设置为 `true` ，并且用户按下 "**取消**" 按钮或 ESC 键时， <xref:System.Windows.Window.DialogResult%2A> 将自动设置为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="b3090-227">When a button's <xref:System.Windows.Controls.Button.IsCancel%2A> property is set to `true` and the user presses either the **Cancel** button or the ESC key, <xref:System.Windows.Window.DialogResult%2A> is automatically set to `false`.</span></span> <span data-ttu-id="b3090-228">下面的标记与前面的代码具有相同的效果，无需处理 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="b3090-228">The following markup has the same effect as the preceding code, without the need to handle the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

<span data-ttu-id="b3090-229">`false`当用户按下标题栏中的 "**关闭**" 按钮或从 "**系统**" 菜单中选择 "**关闭**" 菜单项时，将自动返回一个对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-229">A dialog box automatically returns `false` when a user presses the **Close** button in the title bar or chooses the **Close** menu item from the **System** menu.</span></span>  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a><span data-ttu-id="b3090-230">处理从模式对话框返回的数据</span><span class="sxs-lookup"><span data-stu-id="b3090-230">Processing data returned from a modal dialog box</span></span>  

<span data-ttu-id="b3090-231">当 <xref:System.Windows.Window.DialogResult%2A> 由对话框设置时，打开它的函数可以通过在返回时检查属性来获取对话框结果 <xref:System.Windows.Window.DialogResult%2A> <xref:System.Windows.Window.ShowDialog%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b3090-231">When <xref:System.Windows.Window.DialogResult%2A> is set by a dialog box, the function that opened it can get the dialog box result by inspecting the <xref:System.Windows.Window.DialogResult%2A> property when <xref:System.Windows.Window.ShowDialog%2A> returns.</span></span>  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

<span data-ttu-id="b3090-232">如果对话框结果为 `true` ，则该函数将使用它作为提示来检索和处理用户提供的数据。</span><span class="sxs-lookup"><span data-stu-id="b3090-232">If the dialog result is `true`, the function uses that as a cue to retrieve and process the data provided by the user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3090-233"><xref:System.Windows.Window.ShowDialog%2A>返回后，将无法重新打开对话框。</span><span class="sxs-lookup"><span data-stu-id="b3090-233">After <xref:System.Windows.Window.ShowDialog%2A> has returned, a dialog box cannot be reopened.</span></span> <span data-ttu-id="b3090-234">相反，需要创建新实例。</span><span class="sxs-lookup"><span data-stu-id="b3090-234">Instead, you need to create a new instance.</span></span>

<span data-ttu-id="b3090-235">如果对话框结果为 `false` ，则该函数应正确结束处理。</span><span class="sxs-lookup"><span data-stu-id="b3090-235">If the dialog result is `false`, the function should end processing appropriately.</span></span>  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>
### <a name="creating-a-modeless-custom-dialog-box"></a><span data-ttu-id="b3090-236">创建无模式自定义对话框</span><span class="sxs-lookup"><span data-stu-id="b3090-236">Creating a modeless custom dialog box</span></span>

<span data-ttu-id="b3090-237">无模式对话框（如下图中所示的“查找”对话框）与模式对话框具有相同的基本外观。</span><span class="sxs-lookup"><span data-stu-id="b3090-237">A modeless dialog box, such as the Find Dialog Box shown in the following figure, has the same fundamental appearance as the modal dialog box.</span></span>  

![显示 "查找" 对话框的屏幕截图。](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

<span data-ttu-id="b3090-239">但行为稍有不同，如以下各节中所述。</span><span class="sxs-lookup"><span data-stu-id="b3090-239">However, the behavior is slightly different, as described in the following sections.</span></span>  
  
#### <a name="opening-a-modeless-dialog-box"></a><span data-ttu-id="b3090-240">打开无模式对话框</span><span class="sxs-lookup"><span data-stu-id="b3090-240">Opening a modeless dialog box</span></span>

<span data-ttu-id="b3090-241">无模式对话框通过调用 <xref:System.Windows.Window.Show%2A> 方法打开。</span><span class="sxs-lookup"><span data-stu-id="b3090-241">A modeless dialog box is opened by calling the <xref:System.Windows.Window.Show%2A> method.</span></span>  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  

[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

<span data-ttu-id="b3090-242">与不同 <xref:System.Windows.Window.ShowDialog%2A> ，会 <xref:System.Windows.Window.Show%2A> 立即返回。</span><span class="sxs-lookup"><span data-stu-id="b3090-242">Unlike <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> returns immediately.</span></span> <span data-ttu-id="b3090-243">因此，调用窗口无法判断无模式对话框何时关闭，也就不知道何时检查对话框结果或从对话框获取数据进行进一步处理。</span><span class="sxs-lookup"><span data-stu-id="b3090-243">Consequently, the calling window cannot tell when the modeless dialog box is closed and, therefore, does not know when to check for a dialog box result or get data from the dialog box for further processing.</span></span> <span data-ttu-id="b3090-244">相反，对话框需要创建替代方法来将数据返回到调用窗口进行处理。</span><span class="sxs-lookup"><span data-stu-id="b3090-244">Instead, the dialog box needs to create an alternative way to return data to the calling window for processing.</span></span>  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a><span data-ttu-id="b3090-245">处理从无模式对话框返回的数据</span><span class="sxs-lookup"><span data-stu-id="b3090-245">Processing data returned from a modeless dialog box</span></span>  

<span data-ttu-id="b3090-246">在此示例中， `FindDialogBox` 可能会向主窗口返回一个或多个查找结果，具体取决于在没有任何特定频率的情况下搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="b3090-246">In this example, the `FindDialogBox` may return one or more find results to the main window, depending on the text being searched for without any specific frequency.</span></span> <span data-ttu-id="b3090-247">和模式对话框一样，无模式对话框也可以使用属性返回结果。</span><span class="sxs-lookup"><span data-stu-id="b3090-247">As with a modal dialog box, a modeless dialog box can return results using properties.</span></span> <span data-ttu-id="b3090-248">但拥有对话框的窗口需要了解何时检查那些属性。</span><span class="sxs-lookup"><span data-stu-id="b3090-248">However, the window that owns the dialog box needs to know when to check those properties.</span></span> <span data-ttu-id="b3090-249">实现此目的的一种方法是用对话框实现事件，只要找到文本就引发它。</span><span class="sxs-lookup"><span data-stu-id="b3090-249">One way to enable this is for the dialog box to implement an event that is raised whenever text is found.</span></span> <span data-ttu-id="b3090-250">`FindDialogBox``TextFoundEvent`为此目的实现，这首先需要委托。</span><span class="sxs-lookup"><span data-stu-id="b3090-250">`FindDialogBox` implements the `TextFoundEvent` for this purpose, which first requires a delegate.</span></span>  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

<span data-ttu-id="b3090-251">使用 `TextFoundEventHandler` 委托 `FindDialogBox` 实现 `TextFoundEvent` 。</span><span class="sxs-lookup"><span data-stu-id="b3090-251">Using the `TextFoundEventHandler` delegate, `FindDialogBox` implements the `TextFoundEvent`.</span></span>
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

<span data-ttu-id="b3090-252">因此， `Find` 在找到搜索结果时，可以引发事件。</span><span class="sxs-lookup"><span data-stu-id="b3090-252">Consequently, `Find` can raise the event when a search result is found.</span></span>  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

<span data-ttu-id="b3090-253">所有者窗口则需要注册和处理此事件。</span><span class="sxs-lookup"><span data-stu-id="b3090-253">The owner window then needs to register with and handle this event.</span></span>

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a><span data-ttu-id="b3090-254">关闭无模式对话框</span><span class="sxs-lookup"><span data-stu-id="b3090-254">Closing a modeless dialog box</span></span>

<span data-ttu-id="b3090-255">由于不 <xref:System.Windows.Window.DialogResult%2A> 需要设置，因此可以使用系统提供机制关闭无模式对话框，其中包括：</span><span class="sxs-lookup"><span data-stu-id="b3090-255">Because <xref:System.Windows.Window.DialogResult%2A> does not need to be set, a modeless dialog can be closed using system provide mechanisms, including the following:</span></span>  
  
- <span data-ttu-id="b3090-256">单击标题栏中的 "**关闭**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b3090-256">Clicking the **Close** button in the title bar.</span></span>  
  
- <span data-ttu-id="b3090-257">按 ALT+F4。</span><span class="sxs-lookup"><span data-stu-id="b3090-257">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="b3090-258">从 "**系统**" 菜单中选择 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="b3090-258">Choosing **Close** from the **System** menu.</span></span>  
  
<span data-ttu-id="b3090-259">或者， <xref:System.Windows.Window.Close%2A> 当单击 "**关闭**" 按钮时，您的代码可以调用。</span><span class="sxs-lookup"><span data-stu-id="b3090-259">Alternatively, your code can call <xref:System.Windows.Window.Close%2A> when the **Close** button is clicked.</span></span>  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a><span data-ttu-id="b3090-260">请参阅</span><span class="sxs-lookup"><span data-stu-id="b3090-260">See also</span></span>

- [<span data-ttu-id="b3090-261">Popup 概述</span><span class="sxs-lookup"><span data-stu-id="b3090-261">Popup Overview</span></span>](../controls/popup-overview.md)
- [<span data-ttu-id="b3090-262">对话框示例</span><span class="sxs-lookup"><span data-stu-id="b3090-262">Dialog Box Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
