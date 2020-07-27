---
title: 如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem
description: 了解如何使用 SelectedValue 和 SelectedValuePath 属性指定 Windows Presentation Foundation TreeView 的 SelectedItem 的值。
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: ddac2455dee0bf69d25307340eddd5364e43e823
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166280"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem
此示例演示如何使用 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 和 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 属性来指定的的值 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> 。  
  
## <a name="example"></a>示例  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>属性提供了一种 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 在中指定的的方法 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> 。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>表示集合中的一个对象 <xref:System.Windows.Controls.ItemsControl.Items%2A> ，并 <xref:System.Windows.Controls.TreeView> 显示选定项的单个属性的值。 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>属性指定属性的路径，该属性用于确定属性的值 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 。 本主题中的示例阐释了这一概念。  
  
 下面的示例演示一个 <xref:System.Windows.Data.XmlDataProvider> 包含雇员信息的。  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 下面的示例定义一个 <xref:System.Windows.HierarchicalDataTemplate> ，它显示的 `EmployeeName` 和 `EmployeeWorkDay` `Employee` 。 请注意，不 <xref:System.Windows.HierarchicalDataTemplate> 会指定 `EmployeeNumber` 作为模板的一部分。  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 下面的示例演示一个 <xref:System.Windows.Controls.TreeView> ，它使用之前定义的， <xref:System.Windows.HierarchicalDataTemplate> 并将 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 属性设置为 `EmployeeNumber` 。 当你 `EmployeeName` 在中选择时 <xref:System.Windows.Controls.TreeView> ， <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 属性将返回 `EmployeeInfo` 对应于所选的数据项 `EmployeeName` 。 但是，由于将 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 此的 <xref:System.Windows.Controls.TreeView> 设置为，因此将 `EmployeeNumber` <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 设置为 `EmployeeNumber` 。  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView 概述](treeview-overview.md)
- [操作指南主题](treeview-how-to-topics.md)
