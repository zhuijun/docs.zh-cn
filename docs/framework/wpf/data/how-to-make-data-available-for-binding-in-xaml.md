---
title: 如何：使数据可用于 XAML 中的绑定
description: 根据应用程序在 Windows Presentation Foundation （WPF）中的需要，发现可使数据可用的各种方式。
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 16618ce8b19f5dd5854c4d126e7fc455f0428a28
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620789"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="2eda9-103">如何：使数据可用于 XAML 中的绑定</span><span class="sxs-lookup"><span data-stu-id="2eda9-103">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="2eda9-104">本主题讨论可用于在中绑定数据的各种方法 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，具体取决于应用程序的需求。</span><span class="sxs-lookup"><span data-stu-id="2eda9-104">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2eda9-105">示例</span><span class="sxs-lookup"><span data-stu-id="2eda9-105">Example</span></span>  
 <span data-ttu-id="2eda9-106">如果你要从绑定到的公共语言运行时（CLR）对象 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，则可以使对象可用于绑定的一种方法是将其定义为资源，并为其提供 `x:Key` 。</span><span class="sxs-lookup"><span data-stu-id="2eda9-106">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="2eda9-107">在下面的示例中，具有一个 `Person` 名为的字符串属性的对象 `PersonName` 。</span><span class="sxs-lookup"><span data-stu-id="2eda9-107">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="2eda9-108">在 `Person` 名为的 `<src>` 命名空间中定义了对象（在突出显示的包含元素的行中） `SDKSample` 。</span><span class="sxs-lookup"><span data-stu-id="2eda9-108">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="2eda9-109">然后，可以将该 <xref:System.Windows.Controls.TextBlock> 控件绑定到中的对象 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，因为包含该元素的突出显示的行会 `<TextBlock>` 显示。</span><span class="sxs-lookup"><span data-stu-id="2eda9-109">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span>
  
 <span data-ttu-id="2eda9-110">或者，可以使用 <xref:System.Windows.Data.ObjectDataProvider> 类，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="2eda9-110">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="2eda9-111">可以采用相同的方式定义绑定，如包含元素的突出显示的行所 `<TextBlock>` 示。</span><span class="sxs-lookup"><span data-stu-id="2eda9-111">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="2eda9-112">在此特定示例中，结果是相同的：具有 <xref:System.Windows.Controls.TextBlock> 文本内容的 `Joe` 。</span><span class="sxs-lookup"><span data-stu-id="2eda9-112">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="2eda9-113">但是， <xref:System.Windows.Data.ObjectDataProvider> 类提供了一些功能，如可以绑定到方法的结果。</span><span class="sxs-lookup"><span data-stu-id="2eda9-113">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="2eda9-114"><xref:System.Windows.Data.ObjectDataProvider>如果需要它提供的功能，则可以选择使用类。</span><span class="sxs-lookup"><span data-stu-id="2eda9-114">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="2eda9-115">但是，如果要绑定到已创建的对象，则需要 `DataContext` 在代码中设置，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="2eda9-115">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="2eda9-116">若要使用类访问用于绑定的 XML 数据 <xref:System.Windows.Data.XmlDataProvider> ，请参阅[使用 XMLDataProvider 和 XPath 查询绑定到 xml 数据](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="2eda9-116">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="2eda9-117">若要使用类访问用于绑定的 XML 数据 <xref:System.Windows.Data.ObjectDataProvider> ，请参阅 binding [to XDocument、SYSTEM.XML.LINQ.XELEMENT> 或 LINQ For XML 查询结果](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。</span><span class="sxs-lookup"><span data-stu-id="2eda9-117">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="2eda9-118">有关指定要绑定到的数据的多种方式的信息，请参阅[指定绑定源](how-to-specify-the-binding-source.md)。</span><span class="sxs-lookup"><span data-stu-id="2eda9-118">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="2eda9-119">有关可以绑定到的数据类型或者如何实现您自己的公共语言运行时（CLR）对象进行绑定的信息，请参阅[绑定源概述](binding-sources-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2eda9-119">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eda9-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="2eda9-120">See also</span></span>

- [<span data-ttu-id="2eda9-121">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="2eda9-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="2eda9-122">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="2eda9-122">How-to Topics</span></span>](data-binding-how-to-topics.md)
