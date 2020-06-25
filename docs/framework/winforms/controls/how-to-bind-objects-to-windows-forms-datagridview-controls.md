---
title: 将对象绑定到 DataGridView 控件
description: 了解如何将对象集合绑定到 Windows 窗体 DataGridView 控件，以便每个对象显示为单独的行。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: add0047937b404dcec1ea12bac8053bb9bdfcf1c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325862"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="d755a-103">如何：将对象绑定到 Windows 窗体 DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="d755a-103">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="d755a-104">下面的代码示例演示如何将对象集合绑定到 <xref:System.Windows.Forms.DataGridView> 控件，以便每个对象可显示为单独的一行。</span><span class="sxs-lookup"><span data-stu-id="d755a-104">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="d755a-105">此示例还演示了如何显示 <xref:System.Windows.Forms.DataGridViewComboBoxColumn> 中具有枚举类型的属性，从而使组合框下拉列表包含枚举值。</span><span class="sxs-lookup"><span data-stu-id="d755a-105">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d755a-106">示例</span><span class="sxs-lookup"><span data-stu-id="d755a-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d755a-107">编译代码</span><span class="sxs-lookup"><span data-stu-id="d755a-107">Compiling the Code</span></span>  
 <span data-ttu-id="d755a-108">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="d755a-108">This example requires:</span></span>  
  
- <span data-ttu-id="d755a-109">对 System 和 System.Windows.Forms 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="d755a-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d755a-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d755a-110">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="d755a-111">在 Windows 窗体 DataGridView 控件中显示数据</span><span class="sxs-lookup"><span data-stu-id="d755a-111">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d755a-112">如何：访问绑定到 Windows 窗体 DataGridView 行的对象</span><span class="sxs-lookup"><span data-stu-id="d755a-112">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
