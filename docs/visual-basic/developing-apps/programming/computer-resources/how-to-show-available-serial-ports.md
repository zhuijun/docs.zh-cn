---
title: 如何：显示可用的串行端口
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: e7a9166f1879ed0850ca893bed307a0318298bbb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401818"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="09a3f-102">如何：在 Visual Basic 中显示可用的串行端口</span><span class="sxs-lookup"><span data-stu-id="09a3f-102">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="09a3f-103">本主题介绍在 Visual Basic 中如何使用 `My.Computer.Ports` 显示计算机的可用串行端口。</span><span class="sxs-lookup"><span data-stu-id="09a3f-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="09a3f-104">若要使用户可以选择要使用的端口，请将串行端口的名称置于 <xref:System.Windows.Forms.ListBox> 控件中。</span><span class="sxs-lookup"><span data-stu-id="09a3f-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09a3f-105">示例</span><span class="sxs-lookup"><span data-stu-id="09a3f-105">Example</span></span>  

 <span data-ttu-id="09a3f-106">此示例循环访问 `My.Computer.Ports.SerialPortNames` 属性返回的所有字符串。</span><span class="sxs-lookup"><span data-stu-id="09a3f-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="09a3f-107">这些字符串是计算机上的可用串行端口的名称。</span><span class="sxs-lookup"><span data-stu-id="09a3f-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="09a3f-108">通常，用户从可用端口列表中选择应用程序应使用的串行端口。</span><span class="sxs-lookup"><span data-stu-id="09a3f-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="09a3f-109">在此示例中，串行端口名称存储在 <xref:System.Windows.Forms.ListBox> 控件中。</span><span class="sxs-lookup"><span data-stu-id="09a3f-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="09a3f-110">有关详细信息，请参阅 [ListBox 控件](../../../../framework/winforms/controls/listbox-control-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="09a3f-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="09a3f-111">此代码示例也可作为 IntelliSense 代码片段。</span><span class="sxs-lookup"><span data-stu-id="09a3f-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="09a3f-112">它位于代码片段选取器的“连接和网络”中。 </span><span class="sxs-lookup"><span data-stu-id="09a3f-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="09a3f-113">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="09a3f-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09a3f-114">编译代码</span><span class="sxs-lookup"><span data-stu-id="09a3f-114">Compiling the Code</span></span>  

 <span data-ttu-id="09a3f-115">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="09a3f-115">This example requires:</span></span>  
  
- <span data-ttu-id="09a3f-116">对 System.Windows.Forms.dll 的项目引用。</span><span class="sxs-lookup"><span data-stu-id="09a3f-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="09a3f-117">对 <xref:System.Windows.Forms> 命名空间成员的访问权限。</span><span class="sxs-lookup"><span data-stu-id="09a3f-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="09a3f-118">如果未在代码中完全限定成员名称，则添加 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="09a3f-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="09a3f-119">有关详细信息，请参阅 [Imports 语句（.NET 命名空间和类型）](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="09a3f-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="09a3f-120">窗体具有名为 `ListBox1` 的 <xref:System.Windows.Forms.ListBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="09a3f-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="09a3f-121">可靠编程</span><span class="sxs-lookup"><span data-stu-id="09a3f-121">Robust Programming</span></span>  

 <span data-ttu-id="09a3f-122">不必使用 <xref:System.Windows.Forms.ListBox> 控件显示可用串行端口名称。</span><span class="sxs-lookup"><span data-stu-id="09a3f-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="09a3f-123">相反，可以使用 <xref:System.Windows.Forms.ComboBox> 或其他控件。</span><span class="sxs-lookup"><span data-stu-id="09a3f-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="09a3f-124">如果应用程序不需要来自用户的响应，则可以使用 <xref:System.Windows.Forms.TextBox> 控件显示信息。</span><span class="sxs-lookup"><span data-stu-id="09a3f-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09a3f-125">在 Windows 98 上运行时，`My.Computer.Ports.SerialPortNames` 返回的端口名称可能不正确。</span><span class="sxs-lookup"><span data-stu-id="09a3f-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="09a3f-126">若要防止应用程序错误，请在使用端口名称打开端口时使用异常处理（如 `Try...Catch...Finally` 语句或 `Using` 语句）。</span><span class="sxs-lookup"><span data-stu-id="09a3f-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a3f-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09a3f-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="09a3f-128">如何：使用连接到串行端口的调制解调器拨号</span><span class="sxs-lookup"><span data-stu-id="09a3f-128">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="09a3f-129">如何：将字符串发送到串行端口</span><span class="sxs-lookup"><span data-stu-id="09a3f-129">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="09a3f-130">如何：从串行端口接收字符串</span><span class="sxs-lookup"><span data-stu-id="09a3f-130">How to: Receive Strings From Serial Ports</span></span>](how-to-receive-strings-from-serial-ports.md)
