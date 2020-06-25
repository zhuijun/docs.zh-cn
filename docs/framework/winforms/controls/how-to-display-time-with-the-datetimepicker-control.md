---
title: 如何：使用 DateTimePicker 控件显示时间
description: 了解如何使用 Windows 窗体 DateTimePicker 控件使用户可以选择日期和时间，并以指定的格式显示该日期和时间。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: ab584367a189d05e567bb57d386c6bf629201102
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325582"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="19171-103">如何：使用 DateTimePicker 控件显示时间</span><span class="sxs-lookup"><span data-stu-id="19171-103">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="19171-104">如果希望应用程序能够使用户选择日期和时间，并以指定的格式显示该日期和时间，请使用 <xref:System.Windows.Forms.DateTimePicker> 控件。</span><span class="sxs-lookup"><span data-stu-id="19171-104">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="19171-105">以下的过程说明如何使用 <xref:System.Windows.Forms.DateTimePicker> 控件来显示时间。</span><span class="sxs-lookup"><span data-stu-id="19171-105">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="19171-106">使用 DateTimePicker 控件来显示时间</span><span class="sxs-lookup"><span data-stu-id="19171-106">To display the time with the DateTimePicker control</span></span>  
  
1. <span data-ttu-id="19171-107">将 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 属性设置为 <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="19171-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="19171-108">将 <xref:System.Windows.Forms.DateTimePicker> 的 <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="19171-108">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="19171-109">示例</span><span class="sxs-lookup"><span data-stu-id="19171-109">Example</span></span>  
 <span data-ttu-id="19171-110">以下代码示例演示如何创建 <xref:System.Windows.Forms.DateTimePicker>，使用户可以仅选择时间。</span><span class="sxs-lookup"><span data-stu-id="19171-110">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="19171-111">编译代码</span><span class="sxs-lookup"><span data-stu-id="19171-111">Compiling the Code</span></span>  
 <span data-ttu-id="19171-112">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="19171-112">This example requires:</span></span>  
  
- <span data-ttu-id="19171-113">对 System、System.Data、System.Drawing 和 System.Windows.Forms 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="19171-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19171-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19171-114">See also</span></span>

- [<span data-ttu-id="19171-115">DateTimePicker 控件</span><span class="sxs-lookup"><span data-stu-id="19171-115">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
