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
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="47f5c-103">如何：在代码中创建绑定</span><span class="sxs-lookup"><span data-stu-id="47f5c-103">How to: Create a Binding in Code</span></span>
<span data-ttu-id="47f5c-104">此示例演示如何 <xref:System.Windows.Data.Binding> 在代码中创建和设置。</span><span class="sxs-lookup"><span data-stu-id="47f5c-104">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47f5c-105">示例</span><span class="sxs-lookup"><span data-stu-id="47f5c-105">Example</span></span>  
 <span data-ttu-id="47f5c-106"><xref:System.Windows.FrameworkElement>类和 <xref:System.Windows.FrameworkContentElement> 类都公开 `SetBinding` 方法。</span><span class="sxs-lookup"><span data-stu-id="47f5c-106">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="47f5c-107">如果要绑定继承其中任一类的元素，可以 <xref:System.Windows.FrameworkElement.SetBinding%2A> 直接调用方法。</span><span class="sxs-lookup"><span data-stu-id="47f5c-107">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="47f5c-108">下面的示例创建一个名为的类，该类 `MyData` 包含一个名为的属性 `MyDataProperty` 。</span><span class="sxs-lookup"><span data-stu-id="47f5c-108">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="47f5c-109">下面的示例演示如何创建绑定对象来设置绑定的源。</span><span class="sxs-lookup"><span data-stu-id="47f5c-109">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="47f5c-110">该示例使用 <xref:System.Windows.FrameworkElement.SetBinding%2A> 将控件的 <xref:System.Windows.Controls.TextBlock.Text%2A> 属性绑定 `myText` <xref:System.Windows.Controls.TextBlock> 到 `MyDataProperty` 。</span><span class="sxs-lookup"><span data-stu-id="47f5c-110">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="47f5c-111">有关完整的代码示例，请参阅[仅限代码的绑定示例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="47f5c-111">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="47f5c-112"><xref:System.Windows.FrameworkElement.SetBinding%2A>您可以使用类的静态方法，而不是调用 <xref:System.Windows.Data.BindingOperations.SetBinding%2A> <xref:System.Windows.Data.BindingOperations> 。</span><span class="sxs-lookup"><span data-stu-id="47f5c-112">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="47f5c-113">下面的示例调用， <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> 而不是 <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> 绑定 `myText` 到 `myDataProperty` 。</span><span class="sxs-lookup"><span data-stu-id="47f5c-113">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="47f5c-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="47f5c-114">See also</span></span>

- [<span data-ttu-id="47f5c-115">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="47f5c-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="47f5c-116">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="47f5c-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
