---
title: 响应按钮单击
description: 了解如何响应 Windows 窗体按钮单击。 Windows 窗体按钮控件的最基本用法是在单击按钮时运行一些代码。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: 5c458d56dbd6f1cab8e88bdbb86ede958367e5c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619723"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="ddc7a-104">如何：响应 Windows 窗体按钮的单击</span><span class="sxs-lookup"><span data-stu-id="ddc7a-104">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="ddc7a-105">Windows 窗体控件的最基本用途 <xref:System.Windows.Forms.Button> 是在单击按钮时运行一些代码。</span><span class="sxs-lookup"><span data-stu-id="ddc7a-105">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="ddc7a-106">单击 <xref:System.Windows.Forms.Button> 控件还会生成一些其他事件，例如 <xref:System.Windows.Forms.Control.MouseEnter> 、 <xref:System.Windows.Forms.Control.MouseDown> 和 <xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="ddc7a-106">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="ddc7a-107">如果要为这些相关事件附加事件处理程序，请确保它们的操作不会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="ddc7a-107">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="ddc7a-108">例如，如果单击该按钮会清除用户在文本框中键入的信息，则将鼠标指针暂停在按钮上不会显示工具提示，而不会显示现在不存在的信息。</span><span class="sxs-lookup"><span data-stu-id="ddc7a-108">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="ddc7a-109">如果用户尝试双击 <xref:System.Windows.Forms.Button> 控件，则每次单击都将单独处理; 也就是说，控件不支持双击事件。</span><span class="sxs-lookup"><span data-stu-id="ddc7a-109">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="ddc7a-110">响应按钮单击</span><span class="sxs-lookup"><span data-stu-id="ddc7a-110">To respond to a button click</span></span>  
  
- <span data-ttu-id="ddc7a-111">在按钮的 " `Click` <xref:System.EventHandler> 编写代码" 中，运行。</span><span class="sxs-lookup"><span data-stu-id="ddc7a-111">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="ddc7a-112">`Button1_Click`必须绑定到控件。</span><span class="sxs-lookup"><span data-stu-id="ddc7a-112">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="ddc7a-113">有关详细信息，请参阅[如何：在运行时为 Windows 窗体创建事件处理程序](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc7a-113">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ddc7a-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="ddc7a-114">See also</span></span>

- [<span data-ttu-id="ddc7a-115">Button 控件概述</span><span class="sxs-lookup"><span data-stu-id="ddc7a-115">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="ddc7a-116">选择 Windows 窗体 Button 控件的方法</span><span class="sxs-lookup"><span data-stu-id="ddc7a-116">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="ddc7a-117">Button 控件</span><span class="sxs-lookup"><span data-stu-id="ddc7a-117">Button Control</span></span>](button-control-windows-forms.md)
