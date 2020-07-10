---
title: 在 TextBox 控件中查看多行
description: 了解如何通过设置 "多行"、"换行" 和 "滚动条" 属性，在 "Windows 窗体 TextBox" 控件中查看多行。
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174466"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="d4bb2-103">如何：在 Windows 窗体 TextBox 控件中查看多个行</span><span class="sxs-lookup"><span data-stu-id="d4bb2-103">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="d4bb2-104">默认情况下，Windows 窗体 <xref:System.Windows.Forms.TextBox> 控件显示单行文本，而不显示滚动条。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-104">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="d4bb2-105">如果文本长度超过可用空间，则仅部分文本可见。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-105">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="d4bb2-106">可以通过将 <xref:System.Windows.Forms.TextBox.Multiline%2A> 、 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 和 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 属性设置为合适的值来更改此默认行为。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-106">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="d4bb2-107">在 TextBox 控件中显示回车符</span><span class="sxs-lookup"><span data-stu-id="d4bb2-107">To display a carriage return in the TextBox control</span></span>  
  
- <span data-ttu-id="d4bb2-108">若要在多行中显示回车符 <xref:System.Windows.Forms.TextBox> ，请使用 <xref:System.Environment.NewLine%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-108">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="d4bb2-109">请注意， () 的转义符解释 \\ 是特定于语言的。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-109">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="d4bb2-110">Visual Basic `Chr$(13) & Chr$(10)` 用于回车符和换行符的组合。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-110">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="d4bb2-111">在 TextBox 控件中查看多行</span><span class="sxs-lookup"><span data-stu-id="d4bb2-111">To view multiple lines in the TextBox control</span></span>  
  
1. <span data-ttu-id="d4bb2-112">将 <xref:System.Windows.Forms.TextBox.Multiline%2A> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-112">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="d4bb2-113">如果 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> `true` 默认)  (，则控件中的文本将显示为一个或多个段落; 否则，它将显示为一个列表，在此列表中，可能会在控件的边缘剪裁一些行。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-113">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2. <span data-ttu-id="d4bb2-114">将 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 属性设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-114">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="d4bb2-115">值</span><span class="sxs-lookup"><span data-stu-id="d4bb2-115">Value</span></span>|<span data-ttu-id="d4bb2-116">说明</span><span class="sxs-lookup"><span data-stu-id="d4bb2-116">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="d4bb2-117">如果文本将是几乎始终适合控件的段落，请使用此值。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-117">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="d4bb2-118">如果文本太长而无法同时显示，用户可以使用鼠标指针在控件内移动。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-118">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="d4bb2-119">如果要显示行列表，则使用此值，其中某些行的长度可能超过控件的宽度 <xref:System.Windows.Forms.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-119">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="d4bb2-120">如果列表的长度可能超过控件的高度，则使用此值。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-120">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3. <span data-ttu-id="d4bb2-121">将 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 属性设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-121">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="d4bb2-122">值</span><span class="sxs-lookup"><span data-stu-id="d4bb2-122">Value</span></span>|<span data-ttu-id="d4bb2-123">说明</span><span class="sxs-lookup"><span data-stu-id="d4bb2-123">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="d4bb2-124">控件中的文本不会自动换行，因此它将向右滚动，直至到达换行符。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-124">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="d4bb2-125">如果选择了 <xref:System.Windows.Forms.ScrollBars.Horizontal> "滚动条" 或上方，则使用此值 <xref:System.Windows.Forms.ScrollBars.Both> 。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-125">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="d4bb2-126">`true`（默认值）</span><span class="sxs-lookup"><span data-stu-id="d4bb2-126">`true` (default)</span></span>|<span data-ttu-id="d4bb2-127">不会显示水平滚动条。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-127">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="d4bb2-128">如果选择了 <xref:System.Windows.Forms.ScrollBars.Vertical> "滚动条" 或上方，则使用此值 <xref:System.Windows.Forms.ScrollBars.None> 来显示一个或多个段落。</span><span class="sxs-lookup"><span data-stu-id="d4bb2-128">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4bb2-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4bb2-129">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="d4bb2-130">TextBox 控件概述</span><span class="sxs-lookup"><span data-stu-id="d4bb2-130">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="d4bb2-131">如何：控制 Windows 窗体 TextBox 控件中的插入点</span><span class="sxs-lookup"><span data-stu-id="d4bb2-131">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="d4bb2-132">如何：使用 Windows 窗体 TextBox 控件创建密码文本框</span><span class="sxs-lookup"><span data-stu-id="d4bb2-132">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="d4bb2-133">如何：创建只读文本框</span><span class="sxs-lookup"><span data-stu-id="d4bb2-133">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="d4bb2-134">如何：在字符串中添加引号</span><span class="sxs-lookup"><span data-stu-id="d4bb2-134">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="d4bb2-135">如何：在 Windows 窗体 TextBox 控件中选择文本</span><span class="sxs-lookup"><span data-stu-id="d4bb2-135">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="d4bb2-136">TextBox 控件</span><span class="sxs-lookup"><span data-stu-id="d4bb2-136">TextBox Control</span></span>](textbox-control-windows-forms.md)
