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
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="a39e7-103">如何：实现 INotifyPropertyChanged 接口</span><span class="sxs-lookup"><span data-stu-id="a39e7-103">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="a39e7-104">下面的代码示例演示如何实现 <xref:System.ComponentModel.INotifyPropertyChanged> 接口。</span><span class="sxs-lookup"><span data-stu-id="a39e7-104">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="a39e7-105">在 Windows 窗体数据绑定中使用的业务对象上实现此接口。</span><span class="sxs-lookup"><span data-stu-id="a39e7-105">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="a39e7-106">实现时，接口会与绑定控件通信，属性会对业务对象进行更改。</span><span class="sxs-lookup"><span data-stu-id="a39e7-106">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a39e7-107">示例</span><span class="sxs-lookup"><span data-stu-id="a39e7-107">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a39e7-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="a39e7-108">See also</span></span>

- [<span data-ttu-id="a39e7-109">如何：应用 PropertyNameChanged 模式</span><span class="sxs-lookup"><span data-stu-id="a39e7-109">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="a39e7-110">Windows 窗体数据绑定</span><span class="sxs-lookup"><span data-stu-id="a39e7-110">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="a39e7-111">如何：使用 BindingSource 和 INotifyPropertyChanged 接口引发更改通知</span><span class="sxs-lookup"><span data-stu-id="a39e7-111">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="a39e7-112">Windows 窗体数据绑定中的更改通知</span><span class="sxs-lookup"><span data-stu-id="a39e7-112">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
