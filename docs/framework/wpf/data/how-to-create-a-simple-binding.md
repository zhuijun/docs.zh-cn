---
title: 如何：创建简单绑定
description: 在 Windows Presentation Foundation （WPF）中通过此操作方法示例为应用程序创建一个简单绑定。
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618696"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="4d709-103">如何：创建简单绑定</span><span class="sxs-lookup"><span data-stu-id="4d709-103">How to: Create a Simple Binding</span></span>
<span data-ttu-id="4d709-104">此示例演示如何创建一个简单的 <xref:System.Windows.Data.Binding> 。</span><span class="sxs-lookup"><span data-stu-id="4d709-104">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d709-105">示例</span><span class="sxs-lookup"><span data-stu-id="4d709-105">Example</span></span>  
 <span data-ttu-id="4d709-106">在此示例中，具有一个 `Person` 名为的字符串属性的对象 `PersonName` 。</span><span class="sxs-lookup"><span data-stu-id="4d709-106">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="4d709-107">`Person`对象是在名为的命名空间中定义的 `SDKSample` 。</span><span class="sxs-lookup"><span data-stu-id="4d709-107">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="4d709-108">在下面的示例中，包含元素的突出显示的行将 `<src>` 实例化 `Person` 对象，其 `PersonName` 属性值为 `Joe` 。</span><span class="sxs-lookup"><span data-stu-id="4d709-108">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="4d709-109">此操作在节中完成 `Resources` ，并分配了 `x:Key` 。</span><span class="sxs-lookup"><span data-stu-id="4d709-109">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="4d709-110">包含元素的突出显示行将 `<TextBlock>` <xref:System.Windows.Controls.TextBlock> 控件绑定到 `PersonName` 属性。</span><span class="sxs-lookup"><span data-stu-id="4d709-110">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="4d709-111">因此，将 <xref:System.Windows.Controls.TextBlock> 显示值 "Joe"。</span><span class="sxs-lookup"><span data-stu-id="4d709-111">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d709-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="4d709-112">See also</span></span>

- [<span data-ttu-id="4d709-113">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="4d709-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="4d709-114">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="4d709-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
