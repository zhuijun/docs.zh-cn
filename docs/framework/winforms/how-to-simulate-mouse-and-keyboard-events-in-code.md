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
ms.openlocfilehash: 9b453787f7fa7f5041f75e04d65557a0a3838bee
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904359"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>如何：在代码中模拟鼠标和键盘事件

Windows 窗体提供多个选项，用于以编程方式模拟鼠标和键盘输入。 本主题将简要阐述这些选项。

## <a name="simulating-mouse-input"></a>模拟鼠标输入

模拟鼠标事件的最佳方法是调用 `On`*EventName* 方法，引发要模拟的鼠标事件。 此选项通常只在自定义控件和窗体内可用，因为引发事件的方法受到保护且只能在控件或窗体内访问。 例如，以下步骤说明了如何在代码中模拟单击鼠标右键按钮的操作。

#### <a name="to-programmatically-click-the-right-mouse-button"></a>若要以编程方式单击鼠标右键按钮

1. 创建 <xref:System.Windows.Forms.MouseEventArgs> ，其 <xref:System.Windows.Forms.MouseEventArgs.Button%2A> 属性设置为 <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> 值。

2. 调用 <xref:System.Windows.Forms.Control.OnMouseClick%2A> 方法，其中参数为此 <xref:System.Windows.Forms.MouseEventArgs> 。

有关自定义控件的详细信息，请参阅[设计时开发 Windows 窗体控件](./controls/developing-windows-forms-controls-at-design-time.md)。

还可使用其他方法模拟鼠标输入。 例如，可以编程方式设置表示状态（通常通过鼠标输入设置）的控件属性（如 <xref:System.Windows.Forms.CheckBox.Checked%2A> 控件的 <xref:System.Windows.Forms.CheckBox> 属性），也可以直接调用连接到要模拟的事件的委托。

## <a name="simulating-keyboard-input"></a>模拟键盘输入

除了可通过上面讨论的鼠标输入策略来模拟键盘输入，Windows 窗体还提供了 <xref:System.Windows.Forms.SendKeys> 类，可将击键发送到活动的应用程序。

> [!CAUTION]
> 如果你的应用程序旨在用于全球各种键盘，使用 <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> 可能会产生不可预知的结果，应当避免。

> [!NOTE]
> <xref:System.Windows.Forms.SendKeys> 类已更新为 .NET Framework 3.0，从而可用于在 Windows Vista 上运行的应用程序。 Windows Vista 增强的安全性（称为用户帐户控件或 UAC）可避免以前的实现按预期运行。
>
> <xref:System.Windows.Forms.SendKeys> 类容易遭受某些开发人员不得不解决的计时问题。 更新后的实现仍然容易遇到计时问题，但速度稍微快一些，并且可能需要更改解决方法。 <xref:System.Windows.Forms.SendKeys> 类先尝试使用以前的实现，失败后再使用新的实现。 因此， <xref:System.Windows.Forms.SendKeys> 类在不同操作系统上的运行方式可能不同。 此外，当 <xref:System.Windows.Forms.SendKeys> 类使用新的实现时， <xref:System.Windows.Forms.SendKeys.SendWait%2A> 方法不会等到消息被处理后才将其发送至其他进程。
>
> 如果如论使用何种操作系统，你的应用程序均依赖于一致的行为，则可通过将以下应用程序设置添加至 app.config 文件强制执行 <xref:System.Windows.Forms.SendKeys> 类以使用新的实现。
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> 若要强制执行 <xref:System.Windows.Forms.SendKeys> 类以使用以前的实现，请改用 `"JournalHook"` 值。

#### <a name="to-send-a-keystroke-to-the-same-application"></a>若要将击键发送到相同的应用程序

1. 调用 <xref:System.Windows.Forms.SendKeys.Send%2A> 类或 <xref:System.Windows.Forms.SendKeys.SendWait%2A> 类的 <xref:System.Windows.Forms.SendKeys> 方法。 指定的击键将由应用程序的活动控件接收。 下面的代码示例使用 <xref:System.Windows.Forms.SendKeys.Send%2A> 模拟用户双击窗体表面时按 ENTER 键的操作。 此示例假定 <xref:System.Windows.Forms.Form> 具有一个选项卡索引为 0 的 <xref:System.Windows.Forms.Button> 控件。

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a>若要将击键发送到不同的应用程序

1. 激活将接收击键的应用程序窗口，然后调用 <xref:System.Windows.Forms.SendKeys.Send%2A> 或 <xref:System.Windows.Forms.SendKeys.SendWait%2A> 方法。 由于托管的方法均不会激活其他应用程序，所以必须使用本机 Windows 方法将焦点强制设置到其他应用程序上。 下面的代码示例使用平台调用来调用 `FindWindow` 和 `SetForegroundWindow` 方法以激活计算器应用程序窗口，然后调用 <xref:System.Windows.Forms.SendKeys.SendWait%2A> 向计算器应用程序发出一系列计算。

    > [!NOTE]
    > 可查找计算器应用程序的 `FindWindow` 调用的正确参数因 Windows 版本而异。  下面的代码查找 Windows 7 上的计算器应用程序。 在 Windows Vista 上，将第一个参数更改为 "SciCalc"。 可使用 Spy++ 工具（Visual Studio 附带）确定正确的参数。

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a>示例

以下代码示例显示上述代码示例的完整应用程序。

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a>编译代码

此示例需要：

- 对 System、System.Drawing 和 System.Windows.Forms 程序集的引用。

## <a name="see-also"></a>另请参阅

- [Windows 窗体中的用户输入](user-input-in-windows-forms.md)
