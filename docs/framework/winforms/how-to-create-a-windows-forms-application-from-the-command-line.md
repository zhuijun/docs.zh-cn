---
title: 从命令行创建 Windows 窗体应用程序
titleSuffix: ''
description: 了解如何完成从命令行创建和运行 Windows 窗体应用程序的基本步骤。
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: b63bf884b9fd03a0510c7f240f19d7a14196971a
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903448"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="498f8-103">如何：从命令行创建 Windows 窗体应用程序</span><span class="sxs-lookup"><span data-stu-id="498f8-103">How to: Create a Windows Forms application from the command line</span></span>

<span data-ttu-id="498f8-104">下面的过程介绍从命令行创建和运行 Windows 窗体应用程序所必须完成的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="498f8-104">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="498f8-105">在 Visual Studio 中没有对这些过程的扩展支持。</span><span class="sxs-lookup"><span data-stu-id="498f8-105">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="498f8-106">另请参阅[演练：在 WPF 中承载 Windows 窗体控件](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="498f8-106">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>
  
## <a name="procedure"></a><span data-ttu-id="498f8-107">过程</span><span class="sxs-lookup"><span data-stu-id="498f8-107">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="498f8-108">若要创建窗体</span><span class="sxs-lookup"><span data-stu-id="498f8-108">To create the form</span></span>  
  
1. <span data-ttu-id="498f8-109">在空的代码文件中，键入以下 `Imports` 或 `using` 语句：</span><span class="sxs-lookup"><span data-stu-id="498f8-109">In an empty code file, type the following `Imports` or `using` statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="498f8-110">声明一个 `Form1` 从窗体类继承的名为的类：</span><span class="sxs-lookup"><span data-stu-id="498f8-110">Declare a class named `Form1` that inherits from the Form class:</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="498f8-111">为创建一个无参数的构造函数 `Form1` 。</span><span class="sxs-lookup"><span data-stu-id="498f8-111">Create a parameterless constructor for `Form1`.</span></span>
  
     <span data-ttu-id="498f8-112">将在后续过程中向构造函数添加更多代码。</span><span class="sxs-lookup"><span data-stu-id="498f8-112">You will add more code to the constructor in a subsequent procedure.</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="498f8-113">将 `Main` 方法添加到类。</span><span class="sxs-lookup"><span data-stu-id="498f8-113">Add a `Main` method to the class.</span></span>
  
    1. <span data-ttu-id="498f8-114">应用于 <xref:System.STAThreadAttribute> c # `Main` 方法以指定 Windows 窗体应用程序是单线程单元。</span><span class="sxs-lookup"><span data-stu-id="498f8-114">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="498f8-115">（Visual Basic 中不需要特性，因为使用 Visual Basic 开发的 Windows 窗体应用程序在默认情况下使用单线程单元模式。）</span><span class="sxs-lookup"><span data-stu-id="498f8-115">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="498f8-116">调用 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 以将操作系统样式应用于应用程序。</span><span class="sxs-lookup"><span data-stu-id="498f8-116">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="498f8-117">创建一个窗体实例，并运行。</span><span class="sxs-lookup"><span data-stu-id="498f8-117">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="498f8-118">编译并运行该应用程序</span><span class="sxs-lookup"><span data-stu-id="498f8-118">To compile and run the application</span></span>  
  
1. <span data-ttu-id="498f8-119">在.NET Framework 命令提示符处，导航到创建 `Form1` 类的目录。</span><span class="sxs-lookup"><span data-stu-id="498f8-119">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="498f8-120">编译该窗体。</span><span class="sxs-lookup"><span data-stu-id="498f8-120">Compile the form.</span></span>  
  
    - <span data-ttu-id="498f8-121">如果使用的是 c #，请键入：`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="498f8-121">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="498f8-122">如果使用 Visual Basic，请键入：`vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="498f8-122">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="498f8-123">在命令提示符处，键入：`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="498f8-123">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="498f8-124">添加控件和处理事件</span><span class="sxs-lookup"><span data-stu-id="498f8-124">Adding a control and handling an event</span></span>

<span data-ttu-id="498f8-125">上一过程中的步骤演示了如何只创建一个可编译和运行的基本 Windows 窗体。</span><span class="sxs-lookup"><span data-stu-id="498f8-125">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="498f8-126">下一个过程中将显示如何创建控件并将其添加到窗体中，以及如何处理控件的事件。</span><span class="sxs-lookup"><span data-stu-id="498f8-126">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="498f8-127">有关可添加到 Windows 窗体的控件的详细信息，请参阅[Windows 窗体控件](./controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="498f8-127">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>
  
 <span data-ttu-id="498f8-128">除了解如何创建 Windows 窗体应用程序外，还应了解基于事件的编程以及如何处理用户输入。</span><span class="sxs-lookup"><span data-stu-id="498f8-128">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="498f8-129">有关详细信息，请参阅[在 Windows 窗体中创建事件处理程序](creating-event-handlers-in-windows-forms.md)和[处理用户输入](./controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="498f8-129">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="498f8-130">若要声明一个按钮控件和处理其 click 事件</span><span class="sxs-lookup"><span data-stu-id="498f8-130">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="498f8-131">请声明一个名为 `button1` 的按钮控件。</span><span class="sxs-lookup"><span data-stu-id="498f8-131">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="498f8-132">在构造函数中，创建按钮，并设置其 <xref:System.Windows.Forms.Control.Size%2A>、<xref:System.Windows.Forms.Control.Location%2A> 和 <xref:System.Windows.Forms.Control.Text%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="498f8-132">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="498f8-133">向窗体添加按钮。</span><span class="sxs-lookup"><span data-stu-id="498f8-133">Add the button to the form.</span></span>  
  
     <span data-ttu-id="498f8-134">下面的代码示例演示如何声明 button 控件：</span><span class="sxs-lookup"><span data-stu-id="498f8-134">The following code example demonstrates how to declare the button control:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="498f8-135">创建一个方法来处理该按钮的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="498f8-135">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="498f8-136">在 Click 事件处理程序中，显示带有消息“Hello World”的 <xref:System.Windows.Forms.MessageBox>。</span><span class="sxs-lookup"><span data-stu-id="498f8-136">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="498f8-137">下面的代码示例演示如何处理按钮控件的单击事件：</span><span class="sxs-lookup"><span data-stu-id="498f8-137">The following code example demonstrates how to handle the button control's click event:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="498f8-138">将 <xref:System.Windows.Forms.Control.Click> 事件与创建的方法相关联。</span><span class="sxs-lookup"><span data-stu-id="498f8-138">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="498f8-139">下面的代码示例演示如何将事件与方法相关联。</span><span class="sxs-lookup"><span data-stu-id="498f8-139">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="498f8-140">编译并运行该应用程序，如之前过程中所述。</span><span class="sxs-lookup"><span data-stu-id="498f8-140">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="498f8-141">示例</span><span class="sxs-lookup"><span data-stu-id="498f8-141">Example</span></span>  

<span data-ttu-id="498f8-142">下面的代码示例是前面的过程中的完整示例：</span><span class="sxs-lookup"><span data-stu-id="498f8-142">The following code example is the complete example from the previous procedures:</span></span>
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="498f8-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="498f8-143">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="498f8-144">更改 Windows 窗体外观</span><span class="sxs-lookup"><span data-stu-id="498f8-144">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="498f8-145">增强 Windows 窗体应用程序</span><span class="sxs-lookup"><span data-stu-id="498f8-145">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="498f8-146">入门与 Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="498f8-146">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
