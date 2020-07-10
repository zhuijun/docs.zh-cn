---
title: TextBox 控件
description: 了解 Windows 窗体 TextBox 控件的各个方面，包括将它用于可编辑文本并使其成为只读的。
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- TextBox control [Windows Forms]
ms.assetid: e5a06987-8aec-4271-b196-2245ba992d62
ms.openlocfilehash: 026f6d2653e41dabd3db7490660b6ce19846d397
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174440"
---
# <a name="textbox-control-windows-forms"></a><span data-ttu-id="563db-103">TextBox 控件（Windows 窗体）</span><span class="sxs-lookup"><span data-stu-id="563db-103">TextBox Control (Windows Forms)</span></span>
<span data-ttu-id="563db-104">Windows 窗体文本框用于获取用户的输入或显示文本。</span><span class="sxs-lookup"><span data-stu-id="563db-104">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="563db-105">`TextBox`控件通常用于可编辑文本，但也可将其设为只读。</span><span class="sxs-lookup"><span data-stu-id="563db-105">The `TextBox` control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="563db-106">文本框可显示多个行，将文本自动换行到控件大小，并添加基本格式设置。</span><span class="sxs-lookup"><span data-stu-id="563db-106">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="563db-107">`TextBox`控件对于显示或输入到控件中的文本允许使用一种格式。</span><span class="sxs-lookup"><span data-stu-id="563db-107">The `TextBox` control allows a single format for text displayed or entered in the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="563db-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="563db-108">In This Section</span></span>  
 [<span data-ttu-id="563db-109">TextBox 控件概述</span><span class="sxs-lookup"><span data-stu-id="563db-109">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)  
 <span data-ttu-id="563db-110">说明此控件的本质及其主要功能和属性。</span><span class="sxs-lookup"><span data-stu-id="563db-110">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="563db-111">如何：控制 Windows 窗体 TextBox 控件中的插入点</span><span class="sxs-lookup"><span data-stu-id="563db-111">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 <span data-ttu-id="563db-112">提供有关指定在编辑控件第一次获得焦点时插入点出现位置的说明。</span><span class="sxs-lookup"><span data-stu-id="563db-112">Gives directions for specifying where the insertion point appears when an edit control first gets the focus.</span></span>  
  
 [<span data-ttu-id="563db-113">如何：使用 Windows 窗体 TextBox 控件创建密码文本框</span><span class="sxs-lookup"><span data-stu-id="563db-113">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="563db-114">说明如何隐藏在文本框中键入的内容。</span><span class="sxs-lookup"><span data-stu-id="563db-114">Explains how to conceal what is typed into a text box.</span></span>  
  
 [<span data-ttu-id="563db-115">如何：创建只读文本框</span><span class="sxs-lookup"><span data-stu-id="563db-115">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)  
 <span data-ttu-id="563db-116">描述如何防止更改文本框的内容。</span><span class="sxs-lookup"><span data-stu-id="563db-116">Describes how to prevent the contents of a text box from being changed.</span></span>  
  
 [<span data-ttu-id="563db-117">如何：在字符串中添加引号</span><span class="sxs-lookup"><span data-stu-id="563db-117">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 <span data-ttu-id="563db-118">说明如何将引号添加到文本框中的字符串。</span><span class="sxs-lookup"><span data-stu-id="563db-118">Explains adding quotation marks to a string in a text box.</span></span>  
  
 [<span data-ttu-id="563db-119">如何：在 Windows 窗体 TextBox 控件中选择文本</span><span class="sxs-lookup"><span data-stu-id="563db-119">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="563db-120">说明如何突出显示文本框中的文本。</span><span class="sxs-lookup"><span data-stu-id="563db-120">Explains how to highlight text in a text box.</span></span>  
  
 [<span data-ttu-id="563db-121">如何：在 Windows 窗体 TextBox 控件中查看多个行</span><span class="sxs-lookup"><span data-stu-id="563db-121">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="563db-122">描述如何使文本框可滚动。</span><span class="sxs-lookup"><span data-stu-id="563db-122">Describes how to make a text box scrollable.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="563db-123">引用</span><span class="sxs-lookup"><span data-stu-id="563db-123">Reference</span></span>  
 <span data-ttu-id="563db-124"><xref:System.Windows.Forms.TextBox> 类</span><span class="sxs-lookup"><span data-stu-id="563db-124"><xref:System.Windows.Forms.TextBox> class</span></span>  
 <span data-ttu-id="563db-125">对此类进行描述，并提供指向其所有成员的链接。</span><span class="sxs-lookup"><span data-stu-id="563db-125">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="563db-126">相关章节</span><span class="sxs-lookup"><span data-stu-id="563db-126">Related Sections</span></span>  
 [<span data-ttu-id="563db-127">在 Windows 窗体上使用的控件</span><span class="sxs-lookup"><span data-stu-id="563db-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="563db-128">提供 Windows 窗体控件的完整列表，附带其使用情况相关信息的链接。</span><span class="sxs-lookup"><span data-stu-id="563db-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
