---
title: 如何：实现依赖属性
description: 通过使用 DependencyProperty 字段来支持公共语言运行时属性，在 Windows Presentation Foundation 中定义依赖属性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 673f653a9b02627efcccdfe08c4812ca0834217c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165088"
---
# <a name="how-to-implement-a-dependency-property"></a>如何：实现依赖属性
此示例演示如何使用字段返回公共语言运行时（CLR）属性 <xref:System.Windows.DependencyProperty> ，从而定义依赖属性。 定义自己的属性并需要其支持 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 功能的诸多方面（包括样式、数据绑定、继承、动画和默认值）时，应将其作为依赖属性实现。  
  
## <a name="example"></a>示例  
 下面的示例首先通过调用方法来注册依赖属性 <xref:System.Windows.DependencyProperty.Register%2A> 。 用于存储依赖项属性的名称和特征的标识符字段的名称必须是您在调用期间为 <xref:System.Windows.DependencyProperty.Name%2A> 依赖项属性选择的名称 <xref:System.Windows.DependencyProperty.Register%2A> ，并且附加了文本字符串 `Property` 。 例如，如果向注册依赖属性 <xref:System.Windows.DependencyProperty.Name%2A> `Location` ，则必须将为依赖属性定义的标识符字段命名为 `LocationProperty` 。  
  
 在此示例中，依赖属性的名称及其 CLR 访问器是 `State` ; 标识符字段为 `StateProperty` ; 属性的类型为 <xref:System.Boolean> ; 而注册依赖属性的类型为 `MyStateControl` 。  
  
 如果不遵循此命名模式，则设计器可能无法正确地报告属性，而且属性系统样式应用程序的某些方面可能不会以预期的方式工作。  
  
 还可为依赖属性指定默认元数据。 此示例将 `State` 依赖属性的默认值注册为 `false`。  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 若要详细了解如何以及为什么要实现依赖属性的 CLR 属性，请参阅[依赖属性概述](dependency-properties-overview.md)。  
  
## <a name="see-also"></a>另请参阅

- [依赖项属性概述](dependency-properties-overview.md)
- [操作指南主题](properties-how-to-topics.md)
