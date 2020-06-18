---
title: 对控件进行线程安全的调用
ms.date: 02/19/2019
description: 了解如何通过线程安全的方式调用跨线程控件来实现应用程序中的多线程处理。
dev_langs:
- csharp
- vb
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
ms.openlocfilehash: b5f4de7bd3d8d89de98dbe27e2dbf360763670d0
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904177"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>如何：对 Windows 窗体控件进行线程安全调用

多线程处理可以提高 Windows 窗体应用的性能，但对 Windows 窗体控件的访问本质上不是线程安全的。 多线程处理可以将你的代码公开给非常严重且复杂的 bug。 处理控件的两个或多个线程可能会强制控件处于不一致状态并导致争用情况、死锁和冻结或挂起。 如果在应用程序中实现多线程处理，请确保以线程安全的方式调用跨线程控件。 有关详细信息，请参阅[托管线程处理最佳做法](../../../standard/threading/managed-threading-best-practices.md)。

可以通过两种方法从未创建该控件的线程安全调用 Windows 窗体控件。 您可以使用 <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> 方法调用在主线程中创建的委托，该委托又调用控件。 或者，你可以实现 <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> ，它使用事件驱动模型将后台线程中完成的工作与报表上的结果进行分隔。

## <a name="unsafe-cross-thread-calls"></a>不安全的跨线程调用

直接从未创建控件的线程调用控件是不安全的。 下面的代码段演示了对控件的不安全调用 <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> 。 `Button1_Click`事件处理程序创建一个新 `WriteTextUnsafe` 线程，该线程直接设置主线程的 <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> 属性。

```csharp
private void Button1_Click(object sender, EventArgs e)
{
    thread2 = new Thread(new ThreadStart(WriteTextUnsafe));
    thread2.Start();
}
private void WriteTextUnsafe()
{
    textBox1.Text = "This text was set unsafely.";
}
```

```vb
Private Sub Button1_Click(ByVal sender As Object, e As EventArgs) Handles Button1.Click
    Thread2 = New Thread(New ThreadStart(AddressOf WriteTextUnsafe))
    Thread2.Start()
End Sub

Private Sub WriteTextUnsafe()
    TextBox1.Text = "This text was set unsafely."
End Sub
```

Visual Studio 调试器通过引发 <xref:System.InvalidOperationException> 消息（**跨线程操作无效）来检测这些不安全的线程调用。控件 "" 从创建它的线程之外的其他线程访问。** 在 <xref:System.InvalidOperationException> Visual Studio 调试过程中，对于不安全的跨线程调用始终出现，在应用运行时可能会发生。 你应修复此问题，但你可以通过将 <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> 属性设置为来禁用异常 `false` 。

## <a name="safe-cross-thread-calls"></a>安全的跨线程调用

下面的代码示例演示了两种从未创建 Windows 窗体控件的线程安全调用的方法：

1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>方法，它从主线程调用委托以调用控件。
2. 一个 <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> 组件，它提供事件驱动模型。

在这两个示例中，后台线程休眠一秒钟，以模拟在该线程中完成的工作。

可以从 c # 或 Visual Basic 命令行 .NET Framework 应用生成并运行这些示例。 有关详细信息，请参阅[命令行生成与 csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[从命令行生成（Visual Basic）](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。

从 .NET Core 3.0 开始，还可以从具有 .NET Core Windows 窗体* \<folder name> .csproj*项目文件的文件夹生成并运行示例作为 Windows .net core 应用。

## <a name="example-use-the-invoke-method-with-a-delegate"></a>示例：对委托使用 Invoke 方法

下面的示例演示了一种用于确保对 Windows 窗体控件进行线程安全调用的模式。 它查询 <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> 属性，该属性将控件的创建线程 id 与调用线程 id 进行比较。 如果线程 Id 相同，则它会直接调用控件。 如果线程 Id 不同，则 <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> 使用主线程中的委托调用方法，这将对控件进行实际调用。

`SafeCallDelegate`允许设置 <xref:System.Windows.Forms.TextBox> 控件的 <xref:System.Windows.Forms.TextBox.Text%2A> 属性。 `WriteTextSafe`方法查询 <xref:System.Windows.Forms.Control.InvokeRequired%2A> 。 如果 <xref:System.Windows.Forms.Control.InvokeRequired%2A> 返回 `true` ，则将 `WriteTextSafe` 传递 `SafeCallDelegate` 给 <xref:System.Windows.Forms.Control.Invoke%2A> 方法以对控件进行实际调用。 如果 <xref:System.Windows.Forms.Control.InvokeRequired%2A> 返回 `false` ，则 `WriteTextSafe` <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> 直接设置。 `Button1_Click`事件处理程序创建新线程并运行 `WriteTextSafe` 方法。

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>示例：使用 BackgroundWorker 事件处理程序

实现多线程处理的一种简单方法是使用 <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> 组件，该组件使用事件驱动模型。 后台线程运行 <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> 不与主线程交互的事件。 主线程运行 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> 和 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> 事件处理程序，这些处理程序可以调用主线程的控件。

若要通过使用进行线程安全调用 <xref:System.ComponentModel.BackgroundWorker> ，请在后台线程中创建方法来完成工作，并将其绑定到 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件。 在主线程中创建另一个方法来报告后台工作的结果，并将其绑定到 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 或 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件。 若要启动后台线程，请调用 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType> 。

该示例使用 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件处理程序设置 <xref:System.Windows.Forms.TextBox> 控件的 <xref:System.Windows.Forms.TextBox.Text%2A> 属性。 有关使用事件的示例 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> ，请参见 <xref:System.ComponentModel.BackgroundWorker> 。

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>另请参阅

- <xref:System.ComponentModel.BackgroundWorker>
- [如何：在后台运行操作](how-to-run-an-operation-in-the-background.md)
- [如何：实现使用后台操作的窗体](how-to-implement-a-form-that-uses-a-background-operation.md)
- [利用 .NET Framework 开发自定义 Windows 窗体控件](developing-custom-windows-forms-controls.md)
