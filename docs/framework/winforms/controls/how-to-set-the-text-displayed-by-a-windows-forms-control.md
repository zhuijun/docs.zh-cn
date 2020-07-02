---
title: 设置控件显示的文本
description: 了解如何设置 Windows 窗体控件显示的文本。 使用 Text 属性设置或返回文本，或使用 Font 属性更改字体。
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: 35bae5830bfee8ab91f7b6c7b9dcc6d6b8db00ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622843"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="38f76-104">如何：设置 Windows 窗体控件显示的文本</span><span class="sxs-lookup"><span data-stu-id="38f76-104">How to: Set the text displayed by a Windows Forms control</span></span>

<span data-ttu-id="38f76-105">Windows 窗体控件通常会显示一些与控件的主要功能相关的文本。</span><span class="sxs-lookup"><span data-stu-id="38f76-105">Windows Forms controls usually display some text that's related to the primary function of the control.</span></span> <span data-ttu-id="38f76-106">例如， <xref:System.Windows.Forms.Button> 控件通常会显示一个标题，指示在单击该按钮时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="38f76-106">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed if the button is clicked.</span></span> <span data-ttu-id="38f76-107">对于所有控件而言，都可通过使用 <xref:System.Windows.Forms.Control.Text%2A> 属性来设置或返回文本。</span><span class="sxs-lookup"><span data-stu-id="38f76-107">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="38f76-108">可以使用 <xref:System.Windows.Forms.Control.Font%2A> 属性更改字体。</span><span class="sxs-lookup"><span data-stu-id="38f76-108">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>

<span data-ttu-id="38f76-109">还可以使用[设计器](#designer)设置文本。</span><span class="sxs-lookup"><span data-stu-id="38f76-109">You can also set the text by using the [designer](#designer).</span></span>

## <a name="programmatic"></a><span data-ttu-id="38f76-110">编程</span><span class="sxs-lookup"><span data-stu-id="38f76-110">Programmatic</span></span>

1. <span data-ttu-id="38f76-111">将 <xref:System.Windows.Forms.Control.Text%2A> 属性设置为字符串。</span><span class="sxs-lookup"><span data-stu-id="38f76-111">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>

   <span data-ttu-id="38f76-112">若要创建带下划线的访问键，请在将作为访问密钥的字母前包含一个 "与" 符号（&）。</span><span class="sxs-lookup"><span data-stu-id="38f76-112">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>

2. <span data-ttu-id="38f76-113">将 <xref:System.Windows.Forms.Control.Font%2A> 属性设置为类型 <xref:System.Drawing.Font> 的对象。</span><span class="sxs-lookup"><span data-stu-id="38f76-113">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > <span data-ttu-id="38f76-114">可使用转义符来显示用户界面元素中的特殊字符，通常对这些元素（如菜单项）有着不同的解释。</span><span class="sxs-lookup"><span data-stu-id="38f76-114">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="38f76-115">例如，下面的代码行将菜单项的文本设置为 "现在为完全不同的内容 &"：</span><span class="sxs-lookup"><span data-stu-id="38f76-115">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a><span data-ttu-id="38f76-116">设计器</span><span class="sxs-lookup"><span data-stu-id="38f76-116">Designer</span></span>

1. <span data-ttu-id="38f76-117">在 Visual Studio 的 "**属性**" 窗口中，将控件的 " **Text** " 属性设置为相应的字符串。</span><span class="sxs-lookup"><span data-stu-id="38f76-117">In the **Properties** window in Visual Studio, set the **Text** property of the control to an appropriate string.</span></span>

   <span data-ttu-id="38f76-118">若要创建带下划线的快捷键，请在将作为快捷键的字母前包含 "and" 符（&）。</span><span class="sxs-lookup"><span data-stu-id="38f76-118">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>

2. <span data-ttu-id="38f76-119">在 "**属性**" 窗口中，选择 "字体" 属性旁边的省略号按钮（ ![ 省略号按钮（...），位于 Visual Studio 属性窗口中 ](./media/visual-studio-ellipsis-button.png) ）。 **Font**</span><span class="sxs-lookup"><span data-stu-id="38f76-119">In the **Properties** window, select the ellipsis button (![Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) next to the **Font** property.</span></span>

   <span data-ttu-id="38f76-120">在 "标准字体" 对话框中，选择所需的字体、字体样式、大小、效果（如删除线或下划线）和脚本。</span><span class="sxs-lookup"><span data-stu-id="38f76-120">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="38f76-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="38f76-121">See also</span></span>

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="38f76-122">如何：创建 Windows 窗体控件的访问键</span><span class="sxs-lookup"><span data-stu-id="38f76-122">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="38f76-123">如何：响应 Windows 窗体按钮的单击</span><span class="sxs-lookup"><span data-stu-id="38f76-123">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
