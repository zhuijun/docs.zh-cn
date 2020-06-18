---
title: 如何：在窗体一级处理键盘输入
description: 了解如何在消息到达控件之前，在窗体级别处理 Windows 窗体的键盘输入。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: 6f0695b6f665a613e0e4e001a4f9bbfc09dd45ed
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904151"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="ce4c9-103">如何：在窗体一级处理键盘输入</span><span class="sxs-lookup"><span data-stu-id="ce4c9-103">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="ce4c9-104">Windows 窗体能够在消息到达控件之前处理窗体级别的键盘消息。</span><span class="sxs-lookup"><span data-stu-id="ce4c9-104">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="ce4c9-105">本主题演示如何完成此任务。</span><span class="sxs-lookup"><span data-stu-id="ce4c9-105">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="ce4c9-106">处理窗体级别的键盘消息</span><span class="sxs-lookup"><span data-stu-id="ce4c9-106">To handle a keyboard message at the form level</span></span>  
  
- <span data-ttu-id="ce4c9-107">处理启动窗体的 <xref:System.Windows.Forms.Control.KeyPress> 或 <xref:System.Windows.Forms.Control.KeyDown> 事件，并将该窗体的 <xref:System.Windows.Forms.Form.KeyPreview%2A> 属性设置为 `true`，以便在键盘消息到达窗体上的任何控件之前接收到键盘消息。</span><span class="sxs-lookup"><span data-stu-id="ce4c9-107">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="ce4c9-108">以下代码示例通过检测所有的数字键以及使用“1”、“4”和“7”来处理 <xref:System.Windows.Forms.Control.KeyPress> 事件。</span><span class="sxs-lookup"><span data-stu-id="ce4c9-108">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="ce4c9-109">示例</span><span class="sxs-lookup"><span data-stu-id="ce4c9-109">Example</span></span>  
 <span data-ttu-id="ce4c9-110">以下代码示例是上述示例的整个应用程序。</span><span class="sxs-lookup"><span data-stu-id="ce4c9-110">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="ce4c9-111">此应用程序包括一个 <xref:System.Windows.Forms.TextBox> 和几个允许你从 <xref:System.Windows.Forms.TextBox> 中移动焦点的控件。</span><span class="sxs-lookup"><span data-stu-id="ce4c9-111">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="ce4c9-112">显示剩余键时，主要 <xref:System.Windows.Forms.Form> 的 <xref:System.Windows.Forms.Control.KeyPress> 事件使用“1”、“4”和“7”，而 <xref:System.Windows.Forms.TextBox> 的 <xref:System.Windows.Forms.Control.KeyPress> 事件使用“2”、“5”和“8”。</span><span class="sxs-lookup"><span data-stu-id="ce4c9-112">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="ce4c9-113">比较在 <xref:System.Windows.Forms.TextBox> 具有焦点时按数字键的 <xref:System.Windows.Forms.MessageBox> 输出以及在焦点位于其他控件上时按数字键的 <xref:System.Windows.Forms.MessageBox> 输出。</span><span class="sxs-lookup"><span data-stu-id="ce4c9-113">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ce4c9-114">编译代码</span><span class="sxs-lookup"><span data-stu-id="ce4c9-114">Compiling the Code</span></span>  
 <span data-ttu-id="ce4c9-115">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="ce4c9-115">This example requires:</span></span>  
  
- <span data-ttu-id="ce4c9-116">对 System、System.Drawing 和 System.Windows.Forms 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="ce4c9-116">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce4c9-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce4c9-117">See also</span></span>

- [<span data-ttu-id="ce4c9-118">Windows 窗体应用程序中的键盘输入</span><span class="sxs-lookup"><span data-stu-id="ce4c9-118">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
