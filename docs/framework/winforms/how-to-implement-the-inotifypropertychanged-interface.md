---
title: 如何：实现 INotifyPropertyChanged 接口
description: 了解如何实现 Windows 窗体数据绑定中使用的业务对象上的 INotifyPropertyChanged 接口。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 83d2ef32787d2dbcd877bc77dcede10111098f8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619263"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>如何：实现 INotifyPropertyChanged 接口
下面的代码示例演示如何实现 <xref:System.ComponentModel.INotifyPropertyChanged> 接口。 在 Windows 窗体数据绑定中使用的业务对象上实现此接口。 实现时，接口会与绑定控件通信，属性会对业务对象进行更改。  
  
## <a name="example"></a>示例  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [如何：应用 PropertyNameChanged 模式](how-to-apply-the-propertynamechanged-pattern.md)
- [Windows 窗体数据绑定](windows-forms-data-binding.md)
- [如何：使用 BindingSource 和 INotifyPropertyChanged 接口引发更改通知](./controls/raise-change-notifications--bindingsource.md)
- [Windows 窗体数据绑定中的更改通知](change-notification-in-windows-forms-data-binding.md)
