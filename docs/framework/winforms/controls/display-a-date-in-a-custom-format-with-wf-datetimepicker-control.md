---
title: 使用 DateTimePicker 控件以自定义格式显示日期
description: 了解如何使用 Windows 窗体 DateTimePicker 控件设置控件中日期和时间的显示格式。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: 773070136e4fd43ab1bf510ebcaf6b0aa6a7ba8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325828"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>如何：使用 Windows 窗体 DateTimePicker 控件以自定义格式显示日期
Windows 窗体 <xref:System.Windows.Forms.DateTimePicker> 控件使您可以灵活地设置控件中日期和时间的显示格式。 <xref:System.Windows.Forms.DateTimePicker.Format%2A>属性允许您从中列出的预定义格式中进行选择 <xref:System.Windows.Forms.DateTimePickerFormat> 。 如果这些都不能满足您的需要，则可以使用中列出的格式字符来创建自己的格式样式 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> 。  
  
### <a name="to-display-a-custom-format"></a>显示自定义格式  
  
1. 将 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 属性设置为 `DateTimePickerFormat.Custom`。  
  
2. 将 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> 属性设置为格式字符串。  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a>向格式化值添加文本  
  
1. 使用单引号将不是格式字符（如 "M"）或分隔符（如 "："）的任何字符括起来。 例如，以下格式字符串将显示英语（美国）区域性中格式为 "今日：05:30:31 星期五3月02，2012" 的当前日期。  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     根据区域性设置的不同，不包含在单引号中的任何字符都可以更改。 例如，上述格式字符串将显示英语（美国）区域性中格式为 "今日：05:30:31 星期五3月02，2012" 的当前日期。 请注意，第一个冒号括在单引号中，因为它不应作为 "hh： mm： ss" 中的分隔字符。 在另一种区域性中，该格式可能显示为 "今天是：05.30.31 星期五02： 2012"。  
  
## <a name="see-also"></a>另请参阅

- [DateTimePicker 控件](datetimepicker-control-windows-forms.md)
- [如何：使用 Windows 窗体 DateTimePicker 控件设置和返回日期](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
