---
title: 在 Visual Studio 中调试表达式树 (C#)
description: 了解 Visual Studio 中的 DebugView 属性。 了解如何使用此属性分析表达式树的结构和内容。
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 5dcf56f96ecdbfdc3f4cb171fdb30b96456b59c9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91154127"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="e5b49-104">在 Visual Studio 中调试表达式树 (C#)</span><span class="sxs-lookup"><span data-stu-id="e5b49-104">Debugging Expression Trees in Visual Studio (C#)</span></span>

<span data-ttu-id="e5b49-105">可以在调试应用程序时分析表达式树的结构和内容。</span><span class="sxs-lookup"><span data-stu-id="e5b49-105">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="e5b49-106">要快速了解表达式树结构，可以使用 `DebugView` 属性，该属性[使用特殊语法](debugview-syntax.md)表示表达式树。</span><span class="sxs-lookup"><span data-stu-id="e5b49-106">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="e5b49-107">（请注意，`DebugView` 仅在调试模式下可用。）</span><span class="sxs-lookup"><span data-stu-id="e5b49-107">(Note that `DebugView` is available only in debug mode.)</span></span>  

![VS 调试器中的表达式树的 DebugView 屏幕截图。](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="e5b49-109">由于 `DebugView` 是一个字符串，因此可以使用[内置文本可视化工具](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)在多行中进行查看，方法是从 `DebugView` 标签旁边的放大镜图标中选择“文本可视化工具”。</span><span class="sxs-lookup"><span data-stu-id="e5b49-109">Since `DebugView` is a string, you can use the [built-in Text Visualizer](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![应用于 DebugView 结果的文本可视化工具的屏幕截图。](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="e5b49-111">或者，可以为表达式树安装和使用[自定义可视化工具](/visualstudio/debugger/create-custom-visualizers-of-data)，例如：</span><span class="sxs-lookup"><span data-stu-id="e5b49-111">Alternatively, you can install and use [a custom visualizer](/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="e5b49-112">[可读表达式](https://github.com/agileobjects/ReadableExpressions)（[MIT 许可证](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)，可以从 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers) 中获取）使用各种呈现选项将表达式树呈现为可设置主题的 C# 代码：</span><span class="sxs-lookup"><span data-stu-id="e5b49-112">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![可读表达式可视化工具的屏幕截图。](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="e5b49-114">[表达式树可视化工具](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md)（[MIT 许可证](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)）提供表达式树及其各个节点的树视图：</span><span class="sxs-lookup"><span data-stu-id="e5b49-114">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes:</span></span>

  ![表达式树可视化工具的屏幕截图。](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="e5b49-116">打开表达式树的可视化工具</span><span class="sxs-lookup"><span data-stu-id="e5b49-116">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="e5b49-117">单击“数据提示”、“监视”窗口、“自动”窗口或“本地”窗口中表达式树旁边显示的放大镜图标   。</span><span class="sxs-lookup"><span data-stu-id="e5b49-117">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="e5b49-118">显示可用的可视化工具列表：</span><span class="sxs-lookup"><span data-stu-id="e5b49-118">A list of available visualizers is displayed.:</span></span>

    ![显示从 Visual Studio 中打开可视化工具的屏幕截图。](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="e5b49-120">单击要使用的可视化工具。</span><span class="sxs-lookup"><span data-stu-id="e5b49-120">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b49-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="e5b49-121">See also</span></span>

- [<span data-ttu-id="e5b49-122">表达式树 (C#)</span><span class="sxs-lookup"><span data-stu-id="e5b49-122">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="e5b49-123">在 Visual Studio 中进行调试</span><span class="sxs-lookup"><span data-stu-id="e5b49-123">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="e5b49-124">创建自定义可视化工具</span><span class="sxs-lookup"><span data-stu-id="e5b49-124">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="e5b49-125">`DebugView` 语法</span><span class="sxs-lookup"><span data-stu-id="e5b49-125">`DebugView` syntax</span></span>](debugview-syntax.md)
