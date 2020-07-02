---
title: 带有分组框控件的组控件
description: 了解如何使用 Windows 窗体分组框控件对控件进行分组，以便可以创建相关元素的可视分组。
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: f84c495a18f4ae5e04367f024a1e2849f1ed59f9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618059"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a>如何：使用 Windows 窗体 GroupBox 控件对控件分组
Windows 窗体 <xref:System.Windows.Forms.GroupBox> 控件用于对其他控件进行分组。 分组控件有三个原因：  
  
- 为清晰的用户界面创建相关窗体元素的可视分组。  
  
- 创建编程分组（例如，单选按钮）。  
  
- 用于在设计时将控件作为一个单元移动。  
  
### <a name="to-create-a-group-of-controls"></a>创建一组控件  
  
1. <xref:System.Windows.Forms.GroupBox>在窗体上绘制控件。  
  
2. 将其他控件添加到分组框，并在组框中绘制每个控件。  
  
     如果要将现有控件置于分组框中，则可以选择所有控件，将它们剪切到剪贴板，选择 <xref:System.Windows.Forms.GroupBox> 控件，然后将其粘贴到分组框中。 您还可以将其拖动到分组框中。  
  
3. 将 <xref:System.Windows.Forms.GroupBox.Text%2A> "分组框" 的属性设置为相应的标题。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.GroupBox>
- [GroupBox 控件](groupbox-control-windows-forms.md)
