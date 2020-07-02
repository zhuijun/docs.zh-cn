---
title: 如何：在 XAML 中使用视图对数据进行排序和分组
description: 了解如何在 Windows Presentation Foundation （WPF）中创建用于分组、排序和筛选的数据集合视图。
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: a4f8e2de9345dba8e4ea0d3a16a32d57a9adb55c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621673"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="57b2f-103">如何：在 XAML 中使用视图对数据进行排序和分组</span><span class="sxs-lookup"><span data-stu-id="57b2f-103">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="57b2f-104">此示例演示如何在中创建数据集合的视图 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="57b2f-104">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="57b2f-105">视图允许对当前项的分组、排序、筛选和概念功能进行分组、排序、筛选和排序。</span><span class="sxs-lookup"><span data-stu-id="57b2f-105">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57b2f-106">示例</span><span class="sxs-lookup"><span data-stu-id="57b2f-106">Example</span></span>  
 <span data-ttu-id="57b2f-107">在下面的示例中，名为 "*位置*" 的静态资源定义为 "*位置*" 对象的集合，其中每个*位置*对象都由城市名称和状态组成。</span><span class="sxs-lookup"><span data-stu-id="57b2f-107">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="57b2f-108">前缀*src*映射到定义了数据源*位置*的命名空间。</span><span class="sxs-lookup"><span data-stu-id="57b2f-108">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="57b2f-109">前缀*scm*映射到 `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` ， *dat*映射到 `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"` 。</span><span class="sxs-lookup"><span data-stu-id="57b2f-109">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="57b2f-110">下面的示例创建数据集合的视图，该视图按 city 名称进行排序并按状态分组。</span><span class="sxs-lookup"><span data-stu-id="57b2f-110">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="57b2f-111">然后，该视图可以是绑定源，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="57b2f-111">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="57b2f-112">若要绑定到资源中定义的 XML 数据 <xref:System.Windows.Data.XmlDataProvider> ，请在 XML 名称之前加上 @ 符号。</span><span class="sxs-lookup"><span data-stu-id="57b2f-112">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="57b2f-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="57b2f-113">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="57b2f-114">获取数据集合的默认视图</span><span class="sxs-lookup"><span data-stu-id="57b2f-114">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="57b2f-115">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="57b2f-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="57b2f-116">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="57b2f-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
