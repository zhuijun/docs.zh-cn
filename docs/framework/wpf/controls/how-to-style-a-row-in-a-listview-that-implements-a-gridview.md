---
title: 如何：在使用 GridView 的 ListView 中为行的样式
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 4b8b8e2f1b2d7207a37205d981bf2dab3f65122e
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271940"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="47e34-102">如何：为实现 GridView 的 ListView 中的行设置样式</span><span class="sxs-lookup"><span data-stu-id="47e34-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="47e34-103">此示例演示如何对使用模式的控件中的行进行样式 <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> 。</span><span class="sxs-lookup"><span data-stu-id="47e34-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47e34-104">示例</span><span class="sxs-lookup"><span data-stu-id="47e34-104">Example</span></span>  
 <span data-ttu-id="47e34-105"><xref:System.Windows.Controls.ListView>通过 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 在控件上设置，可以在控件中设置行的样式 <xref:System.Windows.Controls.ListView> 。</span><span class="sxs-lookup"><span data-stu-id="47e34-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="47e34-106">为表示为对象的项设置样式 <xref:System.Windows.Controls.ListViewItem> 。</span><span class="sxs-lookup"><span data-stu-id="47e34-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="47e34-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>引用 <xref:System.Windows.Controls.ControlTemplate> 用于显示行内容的对象。</span><span class="sxs-lookup"><span data-stu-id="47e34-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="47e34-108">下面的示例从中提取的完整示例显示了存储在 XML 数据库中的歌曲信息的集合。</span><span class="sxs-lookup"><span data-stu-id="47e34-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an XML database.</span></span> <span data-ttu-id="47e34-109">数据库中的每首歌都有一个评级字段，此字段的值指定了歌曲信息行的显示方式。</span><span class="sxs-lookup"><span data-stu-id="47e34-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="47e34-110">下面的示例演示如何为 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListViewItem> 表示歌曲集中歌曲的对象定义。</span><span class="sxs-lookup"><span data-stu-id="47e34-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="47e34-111">用于 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ControlTemplate> 指定如何显示歌曲信息行的引用对象。</span><span class="sxs-lookup"><span data-stu-id="47e34-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="47e34-112">下面的示例演示了一个 <xref:System.Windows.Controls.ControlTemplate> 向行添加文本字符串的 `"Strongly Recommended"` 。</span><span class="sxs-lookup"><span data-stu-id="47e34-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="47e34-113">此模板在中引用 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ，并显示歌曲的评分值为 5 (五个) 。</span><span class="sxs-lookup"><span data-stu-id="47e34-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="47e34-114"><xref:System.Windows.Controls.ControlTemplate>包含一个 <xref:System.Windows.Controls.GridViewRowPresenter> 对象，该对象按照视图模式的定义在列中布局行的内容 <xref:System.Windows.Controls.GridView> 。</span><span class="sxs-lookup"><span data-stu-id="47e34-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="47e34-115">下面的示例定义 <xref:System.Windows.Controls.GridView> 。</span><span class="sxs-lookup"><span data-stu-id="47e34-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="47e34-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="47e34-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="47e34-117">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="47e34-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="47e34-118">ListView 概述</span><span class="sxs-lookup"><span data-stu-id="47e34-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="47e34-119">样式设置和模板化</span><span class="sxs-lookup"><span data-stu-id="47e34-119">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
