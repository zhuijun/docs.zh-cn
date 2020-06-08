---
title: 如何：使用连接到串行端口的调制解调器拨号
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: e55ce6399dae435fbd5b2f730d4d0848c98d8955
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363262"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="e5a14-102">如何：在 Visual Basic 中使用连接到串行端口的调制解调器拨号</span><span class="sxs-lookup"><span data-stu-id="e5a14-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="e5a14-103">本主题介绍如何在 Visual Basic 中使用 `My.Computer.Ports` 进行调制解调器拨号。</span><span class="sxs-lookup"><span data-stu-id="e5a14-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="e5a14-104">通常，调制解调器连接到计算机的某个串行端口。</span><span class="sxs-lookup"><span data-stu-id="e5a14-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="e5a14-105">若要使应用程序与调制解调器通信，必须将命令发送到相应的串行端口。</span><span class="sxs-lookup"><span data-stu-id="e5a14-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="e5a14-106">调制解调器拨号</span><span class="sxs-lookup"><span data-stu-id="e5a14-106">To dial a modem</span></span>  
  
1. <span data-ttu-id="e5a14-107">确定调制解调器连接到的串行端口。</span><span class="sxs-lookup"><span data-stu-id="e5a14-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="e5a14-108">此示例假定调制解调器在 COM1 上。</span><span class="sxs-lookup"><span data-stu-id="e5a14-108">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="e5a14-109">使用 `My.Computer.Ports.OpenSerialPort` 方法获取对端口的引用。</span><span class="sxs-lookup"><span data-stu-id="e5a14-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="e5a14-110">有关详细信息，请参阅 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。</span><span class="sxs-lookup"><span data-stu-id="e5a14-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="e5a14-111">`Using` 块允许应用程序在即使会生成异常的情况下也关闭串行端口。</span><span class="sxs-lookup"><span data-stu-id="e5a14-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="e5a14-112">操作串行端口的所有代码都应出现在此块中，或者出现在 `Try...Catch...Finally` 块中。</span><span class="sxs-lookup"><span data-stu-id="e5a14-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="e5a14-113">设置 `DtrEnable` 属性，指示计算机已准备好接受从调制解调器传入的传输。</span><span class="sxs-lookup"><span data-stu-id="e5a14-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="e5a14-114">通过 <xref:System.IO.Ports.SerialPort.Write%2A> 方法将拨号命令和电话号码从串行端口发送到调制解调器。</span><span class="sxs-lookup"><span data-stu-id="e5a14-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="e5a14-115">示例</span><span class="sxs-lookup"><span data-stu-id="e5a14-115">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="e5a14-116">此代码示例也可作为 IntelliSense 代码片段。</span><span class="sxs-lookup"><span data-stu-id="e5a14-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="e5a14-117">它位于代码片段选取器的“连接和网络”中。 </span><span class="sxs-lookup"><span data-stu-id="e5a14-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="e5a14-118">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="e5a14-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e5a14-119">编译代码</span><span class="sxs-lookup"><span data-stu-id="e5a14-119">Compiling the Code</span></span>  

 <span data-ttu-id="e5a14-120">该示例需要引用 <xref:System?displayProperty=nameWithType> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="e5a14-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e5a14-121">可靠编程</span><span class="sxs-lookup"><span data-stu-id="e5a14-121">Robust Programming</span></span>  

 <span data-ttu-id="e5a14-122">此示例假定调制解调器已连接 COM1。</span><span class="sxs-lookup"><span data-stu-id="e5a14-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="e5a14-123">建议使代码允许用户从可用端口列表中选择所需串行端口。</span><span class="sxs-lookup"><span data-stu-id="e5a14-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="e5a14-124">有关详细信息，请参阅[如何：显示可用的串行端口](how-to-show-available-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a14-124">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="e5a14-125">本示例使用 `Using` 块来确保应用程序在即使会引发异常的情况下也关闭端口。</span><span class="sxs-lookup"><span data-stu-id="e5a14-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="e5a14-126">有关详细信息，请参阅 [Using 语句](../../../language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a14-126">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="e5a14-127">在本例中，应用程序拨打调制解调器后断开了串行端口。</span><span class="sxs-lookup"><span data-stu-id="e5a14-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="e5a14-128">实际上，需要将数据传入和传出调制解调器。</span><span class="sxs-lookup"><span data-stu-id="e5a14-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="e5a14-129">有关详细信息，请参阅[如何：从串行端口接收字符串](how-to-receive-strings-from-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a14-129">For more information, see [How to: Receive Strings From Serial Ports](how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a14-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5a14-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="e5a14-131">如何：将字符串发送到串行端口</span><span class="sxs-lookup"><span data-stu-id="e5a14-131">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="e5a14-132">如何：从串行端口接收字符串</span><span class="sxs-lookup"><span data-stu-id="e5a14-132">How to: Receive Strings From Serial Ports</span></span>](how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="e5a14-133">如何：显示可用的串行端口</span><span class="sxs-lookup"><span data-stu-id="e5a14-133">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
