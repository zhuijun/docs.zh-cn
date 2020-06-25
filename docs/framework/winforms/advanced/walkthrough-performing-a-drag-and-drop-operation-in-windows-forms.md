---
title: 演练：执行拖放操作
description: 了解如何在 Windows 窗体中执行拖放操作，方法是处理一系列事件，最值得注意的是 System.windows.dragdrop.dragenter>、System.windows.dragdrop.dragleave> 和 System.windows.dragdrop.drop> 事件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 83bfda875e2fdec3981bbcb8f8f7be00db342440
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325824"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="c7947-103">演练：在 Windows 窗体中执行拖放操作</span><span class="sxs-lookup"><span data-stu-id="c7947-103">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="c7947-104">若要在基于 Windows 的应用程序中执行拖放操作，必须处理一系列事件，最值得注意的是 <xref:System.Windows.Forms.Control.DragEnter> 、 <xref:System.Windows.Forms.Control.DragLeave> 和 <xref:System.Windows.Forms.Control.DragDrop> 事件。</span><span class="sxs-lookup"><span data-stu-id="c7947-104">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="c7947-105">通过使用这些事件的事件参数中的可用信息，可以轻松地实现拖放操作。</span><span class="sxs-lookup"><span data-stu-id="c7947-105">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="c7947-106">拖动数据</span><span class="sxs-lookup"><span data-stu-id="c7947-106">Dragging Data</span></span>  
 <span data-ttu-id="c7947-107">所有拖放操作都从拖动开始。</span><span class="sxs-lookup"><span data-stu-id="c7947-107">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="c7947-108">在方法中实现了开始拖动时要收集的数据的功能 <xref:System.Windows.Forms.Control.DoDragDrop%2A> 。</span><span class="sxs-lookup"><span data-stu-id="c7947-108">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="c7947-109">在下面的示例中，该 <xref:System.Windows.Forms.Control.MouseDown> 事件用于启动拖动操作，因为它是最直观的（在按下鼠标按钮时，大多数拖放操作都将开始）。</span><span class="sxs-lookup"><span data-stu-id="c7947-109">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="c7947-110">但是，请记住，任何事件都可用于启动拖放过程。</span><span class="sxs-lookup"><span data-stu-id="c7947-110">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7947-111">某些控件具有特定于拖动的自定义事件。</span><span class="sxs-lookup"><span data-stu-id="c7947-111">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="c7947-112"><xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> 例如，和控件都有一个 <xref:System.Windows.Forms.TreeView.ItemDrag> 事件。</span><span class="sxs-lookup"><span data-stu-id="c7947-112">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="c7947-113">启动拖动操作</span><span class="sxs-lookup"><span data-stu-id="c7947-113">To start a drag operation</span></span>  
  
1. <span data-ttu-id="c7947-114">在将 <xref:System.Windows.Forms.Control.MouseDown> 开始拖动的控件的事件中，使用 `DoDragDrop` 方法设置要拖动的数据，并允许拖动的效果。</span><span class="sxs-lookup"><span data-stu-id="c7947-114">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="c7947-115">有关详细信息，请参阅 <xref:System.Windows.Forms.DragEventArgs.Data%2A> 和 <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>。</span><span class="sxs-lookup"><span data-stu-id="c7947-115">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="c7947-116">下面的示例演示如何启动拖动操作。</span><span class="sxs-lookup"><span data-stu-id="c7947-116">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="c7947-117">拖放开始的控件是一个 <xref:System.Windows.Forms.Button> 控件，要拖动的数据是表示控件属性的字符串 <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button> ，而允许的效果可以是复制或移动。</span><span class="sxs-lookup"><span data-stu-id="c7947-117">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="c7947-118">任何数据都可用作方法中的参数 `DoDragDrop` ; 在上面的示例中，使用了 <xref:System.Windows.Forms.Control.Text%2A> 控件的属性 <xref:System.Windows.Forms.Button> （而不是对值进行硬编码或从数据集检索数据），因为该属性与要拖动的位置（ <xref:System.Windows.Forms.Button> 控件）相关。</span><span class="sxs-lookup"><span data-stu-id="c7947-118">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="c7947-119">在将拖放操作合并到基于 Windows 的应用程序中时，请牢记这一点。</span><span class="sxs-lookup"><span data-stu-id="c7947-119">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="c7947-120">当拖动操作生效时，您可以处理 <xref:System.Windows.Forms.Control.QueryContinueDrag> 事件，该事件将 "询问" 系统的权限才能继续执行拖动操作。</span><span class="sxs-lookup"><span data-stu-id="c7947-120">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="c7947-121">当处理此方法时，它还是调用将对拖动操作产生影响的方法（例如， <xref:System.Windows.Forms.TreeNode> 当光标悬停在控件中时展开控件中的）的适当点 <xref:System.Windows.Forms.TreeView> 。</span><span class="sxs-lookup"><span data-stu-id="c7947-121">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="c7947-122">放置数据</span><span class="sxs-lookup"><span data-stu-id="c7947-122">Dropping Data</span></span>  
 <span data-ttu-id="c7947-123">开始从 Windows 窗体或控件上的某个位置拖动数据后，当然会想要将其放置在某处。</span><span class="sxs-lookup"><span data-stu-id="c7947-123">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="c7947-124">当光标经过为放置数据而进行了正确配置的窗体或控件区域时，会发生改变。</span><span class="sxs-lookup"><span data-stu-id="c7947-124">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="c7947-125">Windows 窗体或控件内的任何区域都可以通过设置 <xref:System.Windows.Forms.Control.AllowDrop%2A> 属性并处理 <xref:System.Windows.Forms.Control.DragEnter> 和事件来接受删除的数据 <xref:System.Windows.Forms.Control.DragDrop> 。</span><span class="sxs-lookup"><span data-stu-id="c7947-125">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="c7947-126">执行放置</span><span class="sxs-lookup"><span data-stu-id="c7947-126">To perform a drop</span></span>  
  
1. <span data-ttu-id="c7947-127">将 <xref:System.Windows.Forms.Control.AllowDrop%2A> 属性设置为 true。</span><span class="sxs-lookup"><span data-stu-id="c7947-127">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="c7947-128">在 `DragEnter` 将发生放置的控件的事件中，确保正在拖动的数据为可接受的类型（在本例中为 <xref:System.Windows.Forms.Control.Text%2A> ）。</span><span class="sxs-lookup"><span data-stu-id="c7947-128">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="c7947-129">然后，该代码设置在将其放到枚举中的某个值时发生的效果 <xref:System.Windows.Forms.DragDropEffects> 。</span><span class="sxs-lookup"><span data-stu-id="c7947-129">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="c7947-130">有关详细信息，请参阅 <xref:System.Windows.Forms.DragEventArgs.Effect%2A>。</span><span class="sxs-lookup"><span data-stu-id="c7947-130">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="c7947-131">您可以 <xref:System.Windows.Forms.DataFormats> 通过将自己的对象指定为方法的参数来定义自己的 <xref:System.Object> <xref:System.Windows.Forms.DataObject.SetData%2A> 。</span><span class="sxs-lookup"><span data-stu-id="c7947-131">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="c7947-132">在进行该操作时，请确保指定的对象可序列化。</span><span class="sxs-lookup"><span data-stu-id="c7947-132">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="c7947-133">有关详细信息，请参阅 <xref:System.Runtime.Serialization.ISerializable>。</span><span class="sxs-lookup"><span data-stu-id="c7947-133">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="c7947-134">在 <xref:System.Windows.Forms.Control.DragDrop> 将发生放置的控件的事件中，使用 <xref:System.Windows.Forms.DataObject.GetData%2A> 方法检索要拖动的数据。</span><span class="sxs-lookup"><span data-stu-id="c7947-134">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="c7947-135">有关详细信息，请参阅 <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>。</span><span class="sxs-lookup"><span data-stu-id="c7947-135">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="c7947-136">在下面的示例中， <xref:System.Windows.Forms.TextBox> 控件是要拖动到的控件（将在其中发生放置）。</span><span class="sxs-lookup"><span data-stu-id="c7947-136">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="c7947-137">该代码将 <xref:System.Windows.Forms.Control.Text%2A> 控件的属性设置 <xref:System.Windows.Forms.TextBox> 为等于正在拖动的数据。</span><span class="sxs-lookup"><span data-stu-id="c7947-137">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="c7947-138">此外，还可以使用 <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> 属性，这样，根据拖放操作期间按下的键，会发生某些效果（例如，在按下 CTRL 键时复制拖动数据的标准）。</span><span class="sxs-lookup"><span data-stu-id="c7947-138">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7947-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7947-139">See also</span></span>

- [<span data-ttu-id="c7947-140">如何：将数据添加到剪贴板</span><span class="sxs-lookup"><span data-stu-id="c7947-140">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="c7947-141">如何：从剪贴板检索数据</span><span class="sxs-lookup"><span data-stu-id="c7947-141">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="c7947-142">拖放操作和剪贴板支持</span><span class="sxs-lookup"><span data-stu-id="c7947-142">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
