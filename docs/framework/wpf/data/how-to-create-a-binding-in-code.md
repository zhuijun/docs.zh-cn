---
title: 如何：在代码中创建绑定
description: 了解如何通过直接调用 SetBinding 方法在 Windows Presentation Foundation 应用程序中的代码中创建绑定。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: aa2a29f4c1262d8ac54641b856c297b284b23a38
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165803"
---
# <a name="how-to-create-a-binding-in-code"></a>如何：在代码中创建绑定
此示例演示如何 <xref:System.Windows.Data.Binding> 在代码中创建和设置。  
  
## <a name="example"></a>示例  
 <xref:System.Windows.FrameworkElement>类和 <xref:System.Windows.FrameworkContentElement> 类都公开 `SetBinding` 方法。 如果要绑定继承其中任一类的元素，可以 <xref:System.Windows.FrameworkElement.SetBinding%2A> 直接调用方法。  
  
 下面的示例创建一个名为的类，该类 `MyData` 包含一个名为的属性 `MyDataProperty` 。  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 下面的示例演示如何创建绑定对象来设置绑定的源。  该示例使用 <xref:System.Windows.FrameworkElement.SetBinding%2A> 将控件的 <xref:System.Windows.Controls.TextBlock.Text%2A> 属性绑定 `myText` <xref:System.Windows.Controls.TextBlock> 到 `MyDataProperty` 。  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 有关完整的代码示例，请参阅[仅限代码的绑定示例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90))。  
  
 <xref:System.Windows.FrameworkElement.SetBinding%2A>您可以使用类的静态方法，而不是调用 <xref:System.Windows.Data.BindingOperations.SetBinding%2A> <xref:System.Windows.Data.BindingOperations> 。 下面的示例调用， <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> 而不是 <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> 绑定 `myText` 到 `myDataProperty` 。  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>请参阅

- [数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)
- [操作指南主题](data-binding-how-to-topics.md)
