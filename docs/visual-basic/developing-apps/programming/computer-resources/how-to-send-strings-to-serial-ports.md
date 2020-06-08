---
title: 如何：将字符串发送到串行端口
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: f78df9cf1bd75432ea645c4dcc06498915ceee49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360288"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="235b2-102">如何：在 Visual Basic 中将字符串发送到串行端口</span><span class="sxs-lookup"><span data-stu-id="235b2-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="235b2-103">本主题介绍在 Visual Basic 中如何使用 `My.Computer.Ports` 将字符串发送到计算机的串行端口。</span><span class="sxs-lookup"><span data-stu-id="235b2-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="235b2-104">示例</span><span class="sxs-lookup"><span data-stu-id="235b2-104">Example</span></span>  

 <span data-ttu-id="235b2-105">本示例将字符串发送到 COM1 串行端口。</span><span class="sxs-lookup"><span data-stu-id="235b2-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="235b2-106">你可能需要使用计算机上的其他串行端口。</span><span class="sxs-lookup"><span data-stu-id="235b2-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="235b2-107">使用 `My.Computer.Ports.OpenSerialPort` 方法获取对端口的引用。</span><span class="sxs-lookup"><span data-stu-id="235b2-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="235b2-108">有关详细信息，请参阅 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。</span><span class="sxs-lookup"><span data-stu-id="235b2-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="235b2-109">`Using` 块允许应用程序在即使会生成异常的情况下也关闭串行端口。</span><span class="sxs-lookup"><span data-stu-id="235b2-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="235b2-110">操作串行端口的所有代码都应出现在此块中，或者出现在 `Try...Catch...Finally` 块中。</span><span class="sxs-lookup"><span data-stu-id="235b2-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="235b2-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A> 方法将数据发送到串行端口。</span><span class="sxs-lookup"><span data-stu-id="235b2-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="235b2-112">编译代码</span><span class="sxs-lookup"><span data-stu-id="235b2-112">Compiling the Code</span></span>  
  
- <span data-ttu-id="235b2-113">本示例假定计算机正在使用 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="235b2-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="235b2-114">可靠编程</span><span class="sxs-lookup"><span data-stu-id="235b2-114">Robust Programming</span></span>  

 <span data-ttu-id="235b2-115">本示例假定计算机正在使用 `COM1`；为了获得更大的灵活性，代码应允许用户从可用端口列表中选择所需的串行端口。</span><span class="sxs-lookup"><span data-stu-id="235b2-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="235b2-116">有关详细信息，请参阅[如何：显示可用的串行端口](how-to-show-available-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="235b2-116">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="235b2-117">本示例使用 `Using` 块来确保应用程序在即使会引发异常的情况下也关闭端口。</span><span class="sxs-lookup"><span data-stu-id="235b2-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="235b2-118">有关详细信息，请参阅 [Using 语句](../../../language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="235b2-118">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="235b2-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="235b2-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="235b2-120">如何：使用连接到串行端口的调制解调器拨号</span><span class="sxs-lookup"><span data-stu-id="235b2-120">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="235b2-121">如何：显示可用的串行端口</span><span class="sxs-lookup"><span data-stu-id="235b2-121">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
