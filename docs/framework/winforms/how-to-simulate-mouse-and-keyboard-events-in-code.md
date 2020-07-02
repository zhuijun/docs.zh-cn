---
title: 如何：在代码中模拟鼠标和键盘事件
description: 了解如何使用 Windows 窗体提供的选项来以编程方式模拟鼠标和键盘输入。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboards [Windows Forms], event simulation
- user input [Windows Forms], simulating
- SendKeys [Windows Forms], using
- mouse clicks [Windows Forms], simulating
- mouse [Windows Forms], event simulation
ms.assetid: 6abcb67e-3766-4af2-9590-bf5dabd17e41
ms.openlocfilehash: 3c60533479352151ac4f28690413ebc7d8e5879d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619242"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a><span data-ttu-id="0a572-103">如何：在代码中模拟鼠标和键盘事件</span><span class="sxs-lookup"><span data-stu-id="0a572-103">How to: Simulate Mouse and Keyboard Events in Code</span></span>

<span data-ttu-id="0a572-104">Windows 窗体提供多个选项，用于以编程方式模拟鼠标和键盘输入。</span><span class="sxs-lookup"><span data-stu-id="0a572-104">Windows Forms provides several options for programmatically simulating mouse and keyboard input.</span></span> <span data-ttu-id="0a572-105">本主题将简要阐述这些选项。</span><span class="sxs-lookup"><span data-stu-id="0a572-105">This topic provides an overview of these options.</span></span>

## <a name="simulating-mouse-input"></a><span data-ttu-id="0a572-106">模拟鼠标输入</span><span class="sxs-lookup"><span data-stu-id="0a572-106">Simulating Mouse Input</span></span>

<span data-ttu-id="0a572-107">模拟鼠标事件的最佳方法是调用 `On`*EventName* 方法，引发要模拟的鼠标事件。</span><span class="sxs-lookup"><span data-stu-id="0a572-107">The best way to simulate mouse events is to call the `On`*EventName* method that raises the mouse event you want to simulate.</span></span> <span data-ttu-id="0a572-108">此选项通常只在自定义控件和窗体内可用，因为引发事件的方法受到保护且只能在控件或窗体内访问。</span><span class="sxs-lookup"><span data-stu-id="0a572-108">This option is usually possible only within custom controls and forms, because the methods that raise events are protected and cannot be accessed outside the control or form.</span></span> <span data-ttu-id="0a572-109">例如，以下步骤说明了如何在代码中模拟单击鼠标右键按钮的操作。</span><span class="sxs-lookup"><span data-stu-id="0a572-109">For example, the following steps illustrate how to simulate clicking the right mouse button in code.</span></span>

#### <a name="to-programmatically-click-the-right-mouse-button"></a><span data-ttu-id="0a572-110">若要以编程方式单击鼠标右键按钮</span><span class="sxs-lookup"><span data-stu-id="0a572-110">To programmatically click the right mouse button</span></span>

1. <span data-ttu-id="0a572-111">创建 <xref:System.Windows.Forms.MouseEventArgs> ，其 <xref:System.Windows.Forms.MouseEventArgs.Button%2A> 属性设置为 <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> 值。</span><span class="sxs-lookup"><span data-stu-id="0a572-111">Create a <xref:System.Windows.Forms.MouseEventArgs> whose <xref:System.Windows.Forms.MouseEventArgs.Button%2A> property is set to the <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> value.</span></span>

2. <span data-ttu-id="0a572-112">调用 <xref:System.Windows.Forms.Control.OnMouseClick%2A> 方法，其中参数为此 <xref:System.Windows.Forms.MouseEventArgs> 。</span><span class="sxs-lookup"><span data-stu-id="0a572-112">Call the <xref:System.Windows.Forms.Control.OnMouseClick%2A> method with this <xref:System.Windows.Forms.MouseEventArgs> as the argument.</span></span>

<span data-ttu-id="0a572-113">有关自定义控件的详细信息，请参阅[设计时开发 Windows 窗体控件](./controls/developing-windows-forms-controls-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="0a572-113">For more information on custom controls, see [Developing Windows Forms Controls at Design Time](./controls/developing-windows-forms-controls-at-design-time.md).</span></span>

<span data-ttu-id="0a572-114">还可使用其他方法模拟鼠标输入。</span><span class="sxs-lookup"><span data-stu-id="0a572-114">There are other ways to simulate mouse input.</span></span> <span data-ttu-id="0a572-115">例如，可以编程方式设置表示状态（通常通过鼠标输入设置）的控件属性（如 <xref:System.Windows.Forms.CheckBox.Checked%2A> 控件的 <xref:System.Windows.Forms.CheckBox> 属性），也可以直接调用连接到要模拟的事件的委托。</span><span class="sxs-lookup"><span data-stu-id="0a572-115">For example, you can programmatically set a control property that represents a state that is typically set through mouse input (such as the <xref:System.Windows.Forms.CheckBox.Checked%2A> property of the <xref:System.Windows.Forms.CheckBox> control), or you can directly call the delegate that is attached to the event you want to simulate.</span></span>

## <a name="simulating-keyboard-input"></a><span data-ttu-id="0a572-116">模拟键盘输入</span><span class="sxs-lookup"><span data-stu-id="0a572-116">Simulating Keyboard Input</span></span>

<span data-ttu-id="0a572-117">除了可通过上面讨论的鼠标输入策略来模拟键盘输入，Windows 窗体还提供了 <xref:System.Windows.Forms.SendKeys> 类，可将击键发送到活动的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0a572-117">Although you can simulate keyboard input by using the strategies discussed above for mouse input, Windows Forms also provides the <xref:System.Windows.Forms.SendKeys> class for sending keystrokes to the active application.</span></span>

> [!CAUTION]
> <span data-ttu-id="0a572-118">如果你的应用程序旨在用于全球各种键盘，使用 <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> 可能会产生不可预知的结果，应当避免。</span><span class="sxs-lookup"><span data-stu-id="0a572-118">If your application is intended for international use with a variety of keyboards, the use of <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> could yield unpredictable results and should be avoided.</span></span>

> [!NOTE]
> <span data-ttu-id="0a572-119"><xref:System.Windows.Forms.SendKeys> 类已更新为 .NET Framework 3.0，从而可用于在 Windows Vista 上运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0a572-119">The <xref:System.Windows.Forms.SendKeys> class has been updated for the .NET Framework 3.0 to enable its use in applications that run on Windows Vista.</span></span> <span data-ttu-id="0a572-120">Windows Vista 增强的安全性（称为用户帐户控件或 UAC）可避免以前的实现按预期运行。</span><span class="sxs-lookup"><span data-stu-id="0a572-120">The enhanced security of Windows Vista (known as User Account Control or UAC) prevents the previous implementation from working as expected.</span></span>
>
> <span data-ttu-id="0a572-121"><xref:System.Windows.Forms.SendKeys> 类容易遭受某些开发人员不得不解决的计时问题。</span><span class="sxs-lookup"><span data-stu-id="0a572-121">The <xref:System.Windows.Forms.SendKeys> class is susceptible to timing issues, which some developers have had to work around.</span></span> <span data-ttu-id="0a572-122">更新后的实现仍然容易遇到计时问题，但速度稍微快一些，并且可能需要更改解决方法。</span><span class="sxs-lookup"><span data-stu-id="0a572-122">The updated implementation is still susceptible to timing issues, but is slightly faster and may require changes to the workarounds.</span></span> <span data-ttu-id="0a572-123"><xref:System.Windows.Forms.SendKeys> 类先尝试使用以前的实现，失败后再使用新的实现。</span><span class="sxs-lookup"><span data-stu-id="0a572-123">The <xref:System.Windows.Forms.SendKeys> class tries to use the previous implementation first, and if that fails, uses the new implementation.</span></span> <span data-ttu-id="0a572-124">因此， <xref:System.Windows.Forms.SendKeys> 类在不同操作系统上的运行方式可能不同。</span><span class="sxs-lookup"><span data-stu-id="0a572-124">As a result, the <xref:System.Windows.Forms.SendKeys> class may behave differently on different operating systems.</span></span> <span data-ttu-id="0a572-125">此外，当 <xref:System.Windows.Forms.SendKeys> 类使用新的实现时， <xref:System.Windows.Forms.SendKeys.SendWait%2A> 方法不会等到消息被处理后才将其发送至其他进程。</span><span class="sxs-lookup"><span data-stu-id="0a572-125">Additionally, when the <xref:System.Windows.Forms.SendKeys> class uses the new implementation, the <xref:System.Windows.Forms.SendKeys.SendWait%2A> method will not wait for messages to be processed when they are sent to another process.</span></span>
>
> <span data-ttu-id="0a572-126">如果如论使用何种操作系统，你的应用程序均依赖于一致的行为，则可通过将以下应用程序设置添加至 app.config 文件强制执行 <xref:System.Windows.Forms.SendKeys> 类以使用新的实现。</span><span class="sxs-lookup"><span data-stu-id="0a572-126">If your application relies on consistent behavior regardless of the operating system, you can force the <xref:System.Windows.Forms.SendKeys> class to use the new implementation by adding the following application setting to your app.config file.</span></span>
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> <span data-ttu-id="0a572-127">若要强制执行 <xref:System.Windows.Forms.SendKeys> 类以使用以前的实现，请改用 `"JournalHook"` 值。</span><span class="sxs-lookup"><span data-stu-id="0a572-127">To force the <xref:System.Windows.Forms.SendKeys> class to use the previous implementation, use the value `"JournalHook"` instead.</span></span>

#### <a name="to-send-a-keystroke-to-the-same-application"></a><span data-ttu-id="0a572-128">若要将击键发送到相同的应用程序</span><span class="sxs-lookup"><span data-stu-id="0a572-128">To send a keystroke to the same application</span></span>

1. <span data-ttu-id="0a572-129">调用 <xref:System.Windows.Forms.SendKeys.Send%2A> 类或 <xref:System.Windows.Forms.SendKeys.SendWait%2A> 类的 <xref:System.Windows.Forms.SendKeys> 方法。</span><span class="sxs-lookup"><span data-stu-id="0a572-129">Call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method of the <xref:System.Windows.Forms.SendKeys> class.</span></span> <span data-ttu-id="0a572-130">指定的击键将由应用程序的活动控件接收。</span><span class="sxs-lookup"><span data-stu-id="0a572-130">The specified keystrokes will be received by the active control of the application.</span></span> <span data-ttu-id="0a572-131">下面的代码示例使用 <xref:System.Windows.Forms.SendKeys.Send%2A> 模拟用户双击窗体表面时按 ENTER 键的操作。</span><span class="sxs-lookup"><span data-stu-id="0a572-131">The following code example uses <xref:System.Windows.Forms.SendKeys.Send%2A> to simulate pressing the ENTER key when the user double-clicks the surface of the form.</span></span> <span data-ttu-id="0a572-132">此示例假定 <xref:System.Windows.Forms.Form> 具有一个选项卡索引为 0 的 <xref:System.Windows.Forms.Button> 控件。</span><span class="sxs-lookup"><span data-stu-id="0a572-132">This example assumes a <xref:System.Windows.Forms.Form> with a single <xref:System.Windows.Forms.Button> control that has a tab index of 0.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a><span data-ttu-id="0a572-133">若要将击键发送到不同的应用程序</span><span class="sxs-lookup"><span data-stu-id="0a572-133">To send a keystroke to a different application</span></span>

1. <span data-ttu-id="0a572-134">激活将接收击键的应用程序窗口，然后调用 <xref:System.Windows.Forms.SendKeys.Send%2A> 或 <xref:System.Windows.Forms.SendKeys.SendWait%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0a572-134">Activate the application window that will receive the keystrokes, and then call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method.</span></span> <span data-ttu-id="0a572-135">由于托管的方法均不会激活其他应用程序，所以必须使用本机 Windows 方法将焦点强制设置到其他应用程序上。</span><span class="sxs-lookup"><span data-stu-id="0a572-135">Because there is no managed method to activate another application, you must use native Windows methods to force focus on other applications.</span></span> <span data-ttu-id="0a572-136">下面的代码示例使用平台调用来调用 `FindWindow` 和 `SetForegroundWindow` 方法以激活计算器应用程序窗口，然后调用 <xref:System.Windows.Forms.SendKeys.SendWait%2A> 向计算器应用程序发出一系列计算。</span><span class="sxs-lookup"><span data-stu-id="0a572-136">The following code example uses platform invoke to call the `FindWindow` and `SetForegroundWindow` methods to activate the Calculator application window, and then calls <xref:System.Windows.Forms.SendKeys.SendWait%2A> to issue a series of calculations to the Calculator application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0a572-137">可查找计算器应用程序的 `FindWindow` 调用的正确参数因 Windows 版本而异。</span><span class="sxs-lookup"><span data-stu-id="0a572-137">The correct parameters of the `FindWindow` call that locates the Calculator application vary based on your version of Windows.</span></span>  <span data-ttu-id="0a572-138">下面的代码查找 Windows 7 上的计算器应用程序。</span><span class="sxs-lookup"><span data-stu-id="0a572-138">The following code finds the Calculator application on Windows 7.</span></span> <span data-ttu-id="0a572-139">在 Windows Vista 上，将第一个参数更改为 "SciCalc"。</span><span class="sxs-lookup"><span data-stu-id="0a572-139">On Windows Vista, change the first parameter to "SciCalc".</span></span> <span data-ttu-id="0a572-140">可使用 Spy++ 工具（Visual Studio 附带）确定正确的参数。</span><span class="sxs-lookup"><span data-stu-id="0a572-140">You can use the Spy++ tool, included with Visual Studio, to determine the correct parameters.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a><span data-ttu-id="0a572-141">示例</span><span class="sxs-lookup"><span data-stu-id="0a572-141">Example</span></span>

<span data-ttu-id="0a572-142">以下代码示例显示上述代码示例的完整应用程序。</span><span class="sxs-lookup"><span data-stu-id="0a572-142">The following code example is the complete application for the previous code examples.</span></span>

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="0a572-143">编译代码</span><span class="sxs-lookup"><span data-stu-id="0a572-143">Compiling the Code</span></span>

<span data-ttu-id="0a572-144">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="0a572-144">This example requires:</span></span>

- <span data-ttu-id="0a572-145">对 System、System.Drawing 和 System.Windows.Forms 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="0a572-145">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a572-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="0a572-146">See also</span></span>

- [<span data-ttu-id="0a572-147">Windows 窗体中的用户输入</span><span class="sxs-lookup"><span data-stu-id="0a572-147">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)
