---
title: 响应 CheckBox 单击
description: 了解如何对 Windows 窗体应用程序进行编程，使其根据复选框的状态执行一些操作。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
ms.openlocfilehash: 58944bc421f990343b6c58484aaab3d79c8bda5e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174492"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="8effa-103">如何：响应 Windows 窗体 CheckBox 的单击</span><span class="sxs-lookup"><span data-stu-id="8effa-103">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="8effa-104">每当用户单击 Windows 窗体控件时 <xref:System.Windows.Forms.CheckBox> ， <xref:System.Windows.Forms.Control.Click> 就会发生该事件。</span><span class="sxs-lookup"><span data-stu-id="8effa-104">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="8effa-105">您可以对应用程序进行编程，根据复选框的状态执行某些操作。</span><span class="sxs-lookup"><span data-stu-id="8effa-105">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="8effa-106">响应复选框单击</span><span class="sxs-lookup"><span data-stu-id="8effa-106">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="8effa-107">在 <xref:System.Windows.Forms.Control.Click> 事件处理程序中，使用 <xref:System.Windows.Forms.CheckBox.Checked%2A> 属性确定控件的状态，并执行任何必要的操作。</span><span class="sxs-lookup"><span data-stu-id="8effa-107">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="8effa-108">如果用户尝试双击 <xref:System.Windows.Forms.CheckBox> 控件，则每次单击都将单独处理; 也就是说， <xref:System.Windows.Forms.CheckBox> 控件不支持双击事件。</span><span class="sxs-lookup"><span data-stu-id="8effa-108">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8effa-109">如果该 <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> 属性 `true` (默认的) ，则在 <xref:System.Windows.Forms.CheckBox> 单击该属性时将自动选择或清除它。</span><span class="sxs-lookup"><span data-stu-id="8effa-109">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="8effa-110">否则，必须在 <xref:System.Windows.Forms.CheckBox.Checked%2A> 发生事件时手动设置属性 <xref:System.Windows.Forms.Control.Click> 。</span><span class="sxs-lookup"><span data-stu-id="8effa-110">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="8effa-111">你还可以使用 <xref:System.Windows.Forms.CheckBox> 控件来确定操作过程。</span><span class="sxs-lookup"><span data-stu-id="8effa-111">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="8effa-112">单击复选框时确定操作过程</span><span class="sxs-lookup"><span data-stu-id="8effa-112">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="8effa-113">使用 case 语句来查询属性的值 <xref:System.Windows.Forms.CheckBox.CheckState%2A> ，以确定操作过程。</span><span class="sxs-lookup"><span data-stu-id="8effa-113">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="8effa-114">当 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 属性设置为时 `true` ， <xref:System.Windows.Forms.CheckBox.CheckState%2A> 属性可能会返回三个可能的值，这些值表示要检查的框、被取消选中的框或第三个不确定状态，在此状态下，将显示一个灰显外观，指示选项不可用。</span><span class="sxs-lookup"><span data-stu-id="8effa-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="8effa-115">当 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 属性设置为时 `true` ，属性将 <xref:System.Windows.Forms.CheckBox.Checked%2A> 返回 `true` <xref:System.Windows.Forms.CheckState.Checked> 和 <xref:System.Windows.Forms.CheckState.Indeterminate> 。</span><span class="sxs-lookup"><span data-stu-id="8effa-115">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8effa-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8effa-116">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="8effa-117">CheckBox 控件概述</span><span class="sxs-lookup"><span data-stu-id="8effa-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="8effa-118">如何：使用 Windows 窗体 CheckBox 控件设置选项</span><span class="sxs-lookup"><span data-stu-id="8effa-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="8effa-119">CheckBox 控件</span><span class="sxs-lookup"><span data-stu-id="8effa-119">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
