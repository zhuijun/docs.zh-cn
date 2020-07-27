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
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="66902-103">如何：实现依赖属性</span><span class="sxs-lookup"><span data-stu-id="66902-103">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="66902-104">此示例演示如何使用字段返回公共语言运行时（CLR）属性 <xref:System.Windows.DependencyProperty> ，从而定义依赖属性。</span><span class="sxs-lookup"><span data-stu-id="66902-104">This example shows how to back a common language runtime (CLR) property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="66902-105">定义自己的属性并需要其支持 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 功能的诸多方面（包括样式、数据绑定、继承、动画和默认值）时，应将其作为依赖属性实现。</span><span class="sxs-lookup"><span data-stu-id="66902-105">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66902-106">示例</span><span class="sxs-lookup"><span data-stu-id="66902-106">Example</span></span>  
 <span data-ttu-id="66902-107">下面的示例首先通过调用方法来注册依赖属性 <xref:System.Windows.DependencyProperty.Register%2A> 。</span><span class="sxs-lookup"><span data-stu-id="66902-107">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="66902-108">用于存储依赖项属性的名称和特征的标识符字段的名称必须是您在调用期间为 <xref:System.Windows.DependencyProperty.Name%2A> 依赖项属性选择的名称 <xref:System.Windows.DependencyProperty.Register%2A> ，并且附加了文本字符串 `Property` 。</span><span class="sxs-lookup"><span data-stu-id="66902-108">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="66902-109">例如，如果向注册依赖属性 <xref:System.Windows.DependencyProperty.Name%2A> `Location` ，则必须将为依赖属性定义的标识符字段命名为 `LocationProperty` 。</span><span class="sxs-lookup"><span data-stu-id="66902-109">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="66902-110">在此示例中，依赖属性的名称及其 CLR 访问器是 `State` ; 标识符字段为 `StateProperty` ; 属性的类型为 <xref:System.Boolean> ; 而注册依赖属性的类型为 `MyStateControl` 。</span><span class="sxs-lookup"><span data-stu-id="66902-110">In this example, the name of the dependency property and its CLR accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="66902-111">如果不遵循此命名模式，则设计器可能无法正确地报告属性，而且属性系统样式应用程序的某些方面可能不会以预期的方式工作。</span><span class="sxs-lookup"><span data-stu-id="66902-111">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="66902-112">还可为依赖属性指定默认元数据。</span><span class="sxs-lookup"><span data-stu-id="66902-112">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="66902-113">此示例将 `State` 依赖属性的默认值注册为 `false`。</span><span class="sxs-lookup"><span data-stu-id="66902-113">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="66902-114">若要详细了解如何以及为什么要实现依赖属性的 CLR 属性，请参阅[依赖属性概述](dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="66902-114">For more information about how and why to implement a dependency property, as opposed to just backing a CLR property with a private field, see [Dependency Properties Overview](dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66902-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66902-115">See also</span></span>

- [<span data-ttu-id="66902-116">依赖项属性概述</span><span class="sxs-lookup"><span data-stu-id="66902-116">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="66902-117">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="66902-117">How-to Topics</span></span>](properties-how-to-topics.md)
