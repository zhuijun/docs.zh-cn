---
title: 如何：用 OpenFileDialog 组件打开文件
ms.date: 02/11/2019
description: 了解如何使用 OpenFileDialog 组件打开 Windows 对话框以浏览和选择文件。
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d571885011b0f0c723c73a417f294f30f96952f4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904424"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="391b9-103">如何：用 OpenFileDialog 打开文件</span><span class="sxs-lookup"><span data-stu-id="391b9-103">How to: Open files with the OpenFileDialog</span></span>

<span data-ttu-id="391b9-104"><xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>组件打开 Windows 对话框以浏览和选择文件。</span><span class="sxs-lookup"><span data-stu-id="391b9-104">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="391b9-105">若要打开并读取选定的文件，可以使用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> 方法，或创建类的实例 <xref:System.IO.StreamReader?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="391b9-105">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="391b9-106">下面的示例演示了这两种方法。</span><span class="sxs-lookup"><span data-stu-id="391b9-106">The following examples show both approaches.</span></span>

<span data-ttu-id="391b9-107">在 .NET Framework 中，若要获取或设置 <xref:System.Windows.Forms.FileDialog.FileName%2A> 属性，需要类授予的特权级别 <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="391b9-107">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="391b9-108">示例运行 <xref:System.Security.Permissions.FileIOPermission> 权限检查，如果在部分信任上下文中运行，则会引发异常，因为权限不足。</span><span class="sxs-lookup"><span data-stu-id="391b9-108">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="391b9-109">有关详细信息，请参阅[代码访问安全性基础知识](../../misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="391b9-109">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="391b9-110">可以从 c # 或 Visual Basic 命令行 .NET Framework 应用生成并运行这些示例。</span><span class="sxs-lookup"><span data-stu-id="391b9-110">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="391b9-111">有关详细信息，请参阅[命令行生成与 csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[从命令行生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="391b9-111">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="391b9-112">从 .NET Core 3.0 开始，还可以从具有 .NET Core Windows 窗体\* \<folder name> .csproj\*项目文件的文件夹生成并运行示例作为 Windows .net core 应用。</span><span class="sxs-lookup"><span data-stu-id="391b9-112">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="391b9-113">示例：使用 StreamReader 将文件作为流进行读取</span><span class="sxs-lookup"><span data-stu-id="391b9-113">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="391b9-114">下面的示例使用 Windows 窗体 <xref:System.Windows.Forms.Button> 控件的 <xref:System.Windows.Forms.Control.Click> 事件处理程序， <xref:System.Windows.Forms.OpenFileDialog> 通过方法打开 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 。</span><span class="sxs-lookup"><span data-stu-id="391b9-114">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="391b9-115">用户选择文件并选择 **"确定"** 后，类的实例将 <xref:System.IO.StreamReader> 读取该文件并在窗体的文本框中显示其内容。</span><span class="sxs-lookup"><span data-stu-id="391b9-115">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="391b9-116">有关从文件流读取的详细信息，请参阅 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 和 <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="391b9-116">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="391b9-117">示例：使用 OpenFile 通过筛选的选定内容打开文件</span><span class="sxs-lookup"><span data-stu-id="391b9-117">Example: Open a file from a filtered selection with OpenFile</span></span>

<span data-ttu-id="391b9-118">下面的示例使用 <xref:System.Windows.Forms.Button> 控件的 <xref:System.Windows.Forms.Control.Click> 事件处理程序打开 <xref:System.Windows.Forms.OpenFileDialog> 带有筛选器的，该筛选器只显示文本文件。</span><span class="sxs-lookup"><span data-stu-id="391b9-118">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="391b9-119">用户选择一个文本文件并选择 **"确定"** 后，该 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法将用于在记事本中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="391b9-119">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="391b9-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="391b9-120">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="391b9-121">OpenFileDialog 组件</span><span class="sxs-lookup"><span data-stu-id="391b9-121">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
