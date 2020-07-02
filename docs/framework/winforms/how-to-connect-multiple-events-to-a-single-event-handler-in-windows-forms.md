---
title: 如何：将多个事件连接到单个事件处理程序
description: '了解如何通过使用 c # 中属性窗口的事件视图，在 Windows 窗体中将多个事件连接到单个事件处理程序。'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621881"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="72e21-103">如何：将多个事件连接到 Windows 窗体中的单个事件处理程序</span><span class="sxs-lookup"><span data-stu-id="72e21-103">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="72e21-104">在应用程序设计中，你可能会发现需要对多个事件使用单个事件处理程序，或者有多个事件执行相同的过程。</span><span class="sxs-lookup"><span data-stu-id="72e21-104">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="72e21-105">例如，如果菜单命令与窗体上的按钮公开相同的功能，则它通常是一种功能强大的时间保护程序。</span><span class="sxs-lookup"><span data-stu-id="72e21-105">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="72e21-106">为此，可以使用 c # 中的属性窗口的 "事件" 视图，或者使用 " `Handles` Visual Basic 代码编辑器" 中的 "关键字" 和 "**类名**" 和 "**方法名称**" 下拉框。</span><span class="sxs-lookup"><span data-stu-id="72e21-106">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="72e21-107">在 Visual Basic 中将多个事件连接到单个事件处理程序</span><span class="sxs-lookup"><span data-stu-id="72e21-107">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="72e21-108">右键单击窗体，然后选择 "**查看代码**"。</span><span class="sxs-lookup"><span data-stu-id="72e21-108">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="72e21-109">从 "**类名称**" 下拉框中，选择一个要具有事件处理程序句柄的控件。</span><span class="sxs-lookup"><span data-stu-id="72e21-109">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="72e21-110">从 "**方法名称**" 下拉框中，选择希望事件处理程序处理的事件之一。</span><span class="sxs-lookup"><span data-stu-id="72e21-110">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="72e21-111">代码编辑器将插入相应的事件处理程序，并将插入点定位到方法中。</span><span class="sxs-lookup"><span data-stu-id="72e21-111">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="72e21-112">在下面的示例中，它是 <xref:System.Windows.Forms.Control.Click> 控件的事件 <xref:System.Windows.Forms.Button> 。</span><span class="sxs-lookup"><span data-stu-id="72e21-112">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="72e21-113">向子句附加要处理的其他事件 `Handles` 。</span><span class="sxs-lookup"><span data-stu-id="72e21-113">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="72e21-114">将相应代码添加到事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="72e21-114">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="72e21-115">将多个事件连接到 C 中的单个事件处理程序\#</span><span class="sxs-lookup"><span data-stu-id="72e21-115">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="72e21-116">选择要将事件处理程序连接到的控件。</span><span class="sxs-lookup"><span data-stu-id="72e21-116">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="72e21-117">在属性窗口中，单击 "**事件**" 按钮（"![事件" 按钮](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")）。</span><span class="sxs-lookup"><span data-stu-id="72e21-117">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="72e21-118">单击要处理的事件的名称。</span><span class="sxs-lookup"><span data-stu-id="72e21-118">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="72e21-119">在 "事件名称" 旁边的 "值" 部分中，单击下拉按钮以显示与要处理的事件的方法签名匹配的现有事件处理程序的列表。</span><span class="sxs-lookup"><span data-stu-id="72e21-119">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="72e21-120">从列表中选择相应的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="72e21-120">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="72e21-121">代码将添加到窗体中，以将事件绑定到现有的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="72e21-121">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e21-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="72e21-122">See also</span></span>

- [<span data-ttu-id="72e21-123">在 Windows 窗体中创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="72e21-123">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="72e21-124">事件处理程序概述</span><span class="sxs-lookup"><span data-stu-id="72e21-124">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
