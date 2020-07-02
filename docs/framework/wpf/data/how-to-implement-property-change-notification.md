---
title: 如何：实现属性更改通知
description: 启用属性，以便在 Windows Presentation Foundation （WPF）中的属性值更改时，自动通知绑定源。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: 6c298930b7b1f812e94ea6add8f53c67d3453530
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620776"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="685bc-103">如何：实现属性更改通知</span><span class="sxs-lookup"><span data-stu-id="685bc-103">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="685bc-104">若要支持 <xref:System.Windows.Data.BindingMode.OneWay> 或 <xref:System.Windows.Data.BindingMode.TwoWay> 绑定以使绑定目标属性能够自动反映绑定源的动态更改（例如，在用户编辑窗体时自动更新预览窗格），类需要提供适当的属性更改通知。</span><span class="sxs-lookup"><span data-stu-id="685bc-104">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="685bc-105">此示例演示如何创建实现的类 <xref:System.ComponentModel.INotifyPropertyChanged> 。</span><span class="sxs-lookup"><span data-stu-id="685bc-105">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="685bc-106">示例</span><span class="sxs-lookup"><span data-stu-id="685bc-106">Example</span></span>  
 <span data-ttu-id="685bc-107">若要实现 <xref:System.ComponentModel.INotifyPropertyChanged> ，需要声明 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件并创建 `OnPropertyChanged` 方法。</span><span class="sxs-lookup"><span data-stu-id="685bc-107">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="685bc-108">然后，对于每个需要更改通知的属性，只要进行了更新，就可以调用 `OnPropertyChanged`。</span><span class="sxs-lookup"><span data-stu-id="685bc-108">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="685bc-109">若要查看如何 `Person` 使用类来支持绑定的示例 <xref:System.Windows.Data.BindingMode.TwoWay> ，请参阅[控制文本框文本更新源的时间](how-to-control-when-the-textbox-text-updates-the-source.md)。</span><span class="sxs-lookup"><span data-stu-id="685bc-109">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="685bc-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="685bc-110">See also</span></span>

- [<span data-ttu-id="685bc-111">绑定源概述</span><span class="sxs-lookup"><span data-stu-id="685bc-111">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="685bc-112">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="685bc-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="685bc-113">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="685bc-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
