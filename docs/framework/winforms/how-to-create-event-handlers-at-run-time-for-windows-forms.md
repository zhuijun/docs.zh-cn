---
title: 如何：在运行时创建事件处理程序
description: 了解如何在运行时使用 Visual Studio 中的 Windows 窗体设计器创建事件处理程序。 此操作允许您在运行时连接事件处理程序。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 857076c46377b3276154d9b193d4bbe51841828f
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325808"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="14e7c-104">如何：在运行时为 Windows 窗体创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="14e7c-104">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="14e7c-105">除了使用 Visual Studio 中的 Windows 窗体设计器创建事件之外，还可以在运行时创建事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="14e7c-105">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="14e7c-106">该操作允许在运行时根据代码中的条件连接相应的事件处理程序，而不是在程序刚启动时连接事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="14e7c-106">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="14e7c-107">在运行时创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="14e7c-107">Create an event handler at run time</span></span>

1. <span data-ttu-id="14e7c-108">打开要向其添加事件处理程序的窗体。</span><span class="sxs-lookup"><span data-stu-id="14e7c-108">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="14e7c-109">对于要处理的事件，将带有其方法签名的方法添加到窗体上。</span><span class="sxs-lookup"><span data-stu-id="14e7c-109">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="14e7c-110">例如，如果您正在处理控件的 <xref:System.Windows.Forms.Control.Click> 事件 <xref:System.Windows.Forms.Button> ，则会创建如下所示的方法：</span><span class="sxs-lookup"><span data-stu-id="14e7c-110">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

    ```vb
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)
       ' Add event handler code here.
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
    // Add event handler code here.
    }
    ```

    ```cpp
    private:
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          // Add event handler code here.
       }
    ```

3. <span data-ttu-id="14e7c-111">根据应用程序添加相应的事件处理程序代码。</span><span class="sxs-lookup"><span data-stu-id="14e7c-111">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="14e7c-112">确定要为其创建事件处理程序的窗体或控件。</span><span class="sxs-lookup"><span data-stu-id="14e7c-112">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="14e7c-113">在窗体类的方法中添加代码，以指定用于处理事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="14e7c-113">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="14e7c-114">例如，下面的代码指定事件处理程序 `button1_Click` 处理控件的 <xref:System.Windows.Forms.Control.Click> 事件 <xref:System.Windows.Forms.Button> ：</span><span class="sxs-lookup"><span data-stu-id="14e7c-114">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="14e7c-115"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A>上面的 Visual Basic 代码中演示的方法将为该按钮建立一个 click 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="14e7c-115">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="14e7c-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14e7c-116">See also</span></span>

- [<span data-ttu-id="14e7c-117">在 Windows 窗体中创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="14e7c-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="14e7c-118">事件处理程序概述</span><span class="sxs-lookup"><span data-stu-id="14e7c-118">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="14e7c-119">Visual Basic 中继承的事件处理程序疑难解答</span><span class="sxs-lookup"><span data-stu-id="14e7c-119">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
