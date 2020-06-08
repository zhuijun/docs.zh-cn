---
title: 如何：从串行端口接收字符串
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 93b6b47d89d05331c85a6459bba7d6fd5e2e3377
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401831"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="be1bb-102">如何：在 Visual Basic 中从串行端口接收字符串</span><span class="sxs-lookup"><span data-stu-id="be1bb-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>

<span data-ttu-id="be1bb-103">本主题介绍在 Visual Basic 中如何使用 `My.Computer.Ports` 从计算机的串行端口接收字符串。</span><span class="sxs-lookup"><span data-stu-id="be1bb-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="be1bb-104">从串行端口接收字符串</span><span class="sxs-lookup"><span data-stu-id="be1bb-104">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="be1bb-105">初始化返回字符串。</span><span class="sxs-lookup"><span data-stu-id="be1bb-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="be1bb-106">确定应提供字符串的串行端口。</span><span class="sxs-lookup"><span data-stu-id="be1bb-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="be1bb-107">此示例假定它是 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="be1bb-107">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="be1bb-108">使用 `My.Computer.Ports.OpenSerialPort` 方法获取对端口的引用。</span><span class="sxs-lookup"><span data-stu-id="be1bb-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="be1bb-109">有关详细信息，请参阅 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。</span><span class="sxs-lookup"><span data-stu-id="be1bb-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="be1bb-110">`Try...Catch...Finally` 块允许应用程序在即使会生成异常的情况下也关闭串行端口。</span><span class="sxs-lookup"><span data-stu-id="be1bb-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="be1bb-111">操作串行端口的所有代码都应出现在此块中。</span><span class="sxs-lookup"><span data-stu-id="be1bb-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="be1bb-112">创建 `Do` 循环，用于读取文本行，直到没有更多行可用。</span><span class="sxs-lookup"><span data-stu-id="be1bb-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="be1bb-113">使用 <xref:System.IO.Ports.SerialPort.ReadLine> 方法来从串行端口读取下一个可用的文本行。</span><span class="sxs-lookup"><span data-stu-id="be1bb-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="be1bb-114">使用 `If` 语句可确定 <xref:System.IO.Ports.SerialPort.ReadLine> 方法是否返回 `Nothing`（这意味着没有更多文本可用）。</span><span class="sxs-lookup"><span data-stu-id="be1bb-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="be1bb-115">如果它未返回 `Nothing`，则退出 `Do` 循环。</span><span class="sxs-lookup"><span data-stu-id="be1bb-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="be1bb-116">向 `If` 语句添加 `Else` 块以处理实际读取字符串的情况。</span><span class="sxs-lookup"><span data-stu-id="be1bb-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="be1bb-117">该块将来自串行端口的字符串追加到返回字符串。</span><span class="sxs-lookup"><span data-stu-id="be1bb-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="be1bb-118">返回字符串。</span><span class="sxs-lookup"><span data-stu-id="be1bb-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="be1bb-119">示例</span><span class="sxs-lookup"><span data-stu-id="be1bb-119">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="be1bb-120">此代码示例也可作为 IntelliSense 代码片段。</span><span class="sxs-lookup"><span data-stu-id="be1bb-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="be1bb-121">它位于代码片段选取器的“连接和网络”中。 </span><span class="sxs-lookup"><span data-stu-id="be1bb-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="be1bb-122">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="be1bb-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be1bb-123">编译代码</span><span class="sxs-lookup"><span data-stu-id="be1bb-123">Compiling the Code</span></span>  

 <span data-ttu-id="be1bb-124">本示例假定计算机正在使用 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="be1bb-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="be1bb-125">可靠编程</span><span class="sxs-lookup"><span data-stu-id="be1bb-125">Robust Programming</span></span>  

 <span data-ttu-id="be1bb-126">本示例假定计算机正在使用 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="be1bb-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="be1bb-127">为了获得更大的灵活性，代码应允许用户从可用端口列表中选择所需的串行端口。</span><span class="sxs-lookup"><span data-stu-id="be1bb-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="be1bb-128">有关详细信息，请参阅[如何：显示可用的串行端口](how-to-show-available-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="be1bb-128">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="be1bb-129">此示例使用 `Try...Catch...Finally` 块确保应用程序关闭端口以及捕获任何超时异常。</span><span class="sxs-lookup"><span data-stu-id="be1bb-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="be1bb-130">有关详细信息，请参阅 [Try...Catch...Finally 语句](../../../language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="be1bb-130">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be1bb-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be1bb-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="be1bb-132">如何：使用连接到串行端口的调制解调器拨号</span><span class="sxs-lookup"><span data-stu-id="be1bb-132">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="be1bb-133">如何：将字符串发送到串行端口</span><span class="sxs-lookup"><span data-stu-id="be1bb-133">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="be1bb-134">如何：显示可用的串行端口</span><span class="sxs-lookup"><span data-stu-id="be1bb-134">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
