---
title: 演练：创建自定义数据流块类型
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
ms.openlocfilehash: 37857e465bf4089dbeecc4cfd532d0702f795495
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284697"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a><span data-ttu-id="2c39a-102">演练：创建自定义数据流块类型</span><span class="sxs-lookup"><span data-stu-id="2c39a-102">Walkthrough: Creating a Custom Dataflow Block Type</span></span>
<span data-ttu-id="2c39a-103">尽管 TPL 数据流库提供了多种可启用各种功能的数据流块类型，但也可以创建自定义块类型。</span><span class="sxs-lookup"><span data-stu-id="2c39a-103">Although the TPL Dataflow Library provides several dataflow block types that enable a variety of functionality, you can also create custom block types.</span></span> <span data-ttu-id="2c39a-104">本文档介绍了如何创建实现自定义行为的数据流块类型。</span><span class="sxs-lookup"><span data-stu-id="2c39a-104">This document describes how to create a dataflow block type that implements custom behavior.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2c39a-105">系统必备</span><span class="sxs-lookup"><span data-stu-id="2c39a-105">Prerequisites</span></span>  
 <span data-ttu-id="2c39a-106">阅读本文档前，请先阅读[数据流](dataflow-task-parallel-library.md)。</span><span class="sxs-lookup"><span data-stu-id="2c39a-106">Read [Dataflow](dataflow-task-parallel-library.md) before you read this document.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a><span data-ttu-id="2c39a-107">定义滑动窗口数据流块</span><span class="sxs-lookup"><span data-stu-id="2c39a-107">Defining the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="2c39a-108">假设数据流应用要求缓冲输入值，并以滑动窗口方式输出值。</span><span class="sxs-lookup"><span data-stu-id="2c39a-108">Consider a dataflow application that requires that input values be buffered and then output in a sliding window manner.</span></span> <span data-ttu-id="2c39a-109">例如，如果输入值为 {0, 1, 2, 3, 4, 5}，且窗口大小为 3，那么滑动窗口数据流块生成输出数组 {0, 1, 2}、{1, 2, 3}、{2, 3, 4} 和 {3, 4, 5}。</span><span class="sxs-lookup"><span data-stu-id="2c39a-109">For example, for the input values {0, 1, 2, 3, 4, 5} and a window size of three, a sliding window dataflow block produces the output arrays {0, 1, 2}, {1, 2, 3}, {2, 3, 4}, and {3, 4, 5}.</span></span> <span data-ttu-id="2c39a-110">下面各部分介绍了两种方式，用于创建实现此自定义行为的数据流块类型。</span><span class="sxs-lookup"><span data-stu-id="2c39a-110">The following sections describe two ways to create a dataflow block type that implements this custom behavior.</span></span> <span data-ttu-id="2c39a-111">第一种方式是，使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> 方法将 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 对象和 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 对象的功能合并到一个传播器块中。</span><span class="sxs-lookup"><span data-stu-id="2c39a-111">The first technique uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to combine the functionality of an <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object and an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object into one propagator block.</span></span> <span data-ttu-id="2c39a-112">第二种方式是，定义派生自 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> 的类，并结合现有功能执行自定义行为。</span><span class="sxs-lookup"><span data-stu-id="2c39a-112">The second technique defines a class that derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> and combines existing functionality to perform custom behavior.</span></span>  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="2c39a-113">使用 Encapsulate 方法定义滑动窗口数据流块</span><span class="sxs-lookup"><span data-stu-id="2c39a-113">Using the Encapsulate Method to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="2c39a-114">下面的示例使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> 方法通过目标和源创建传播器块。</span><span class="sxs-lookup"><span data-stu-id="2c39a-114">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to create a propagator block from a target and a source.</span></span> <span data-ttu-id="2c39a-115">使用传播器块，可以将源块和目标块用作数据的接收方和发送方。</span><span class="sxs-lookup"><span data-stu-id="2c39a-115">A propagator block enables a source block and a target block to act as a receiver and sender of data.</span></span>  
  
 <span data-ttu-id="2c39a-116">如果需要自定义数据流功能，但不需要提供其他方法、属性或字段的类型，此方式就很有用。</span><span class="sxs-lookup"><span data-stu-id="2c39a-116">This technique is useful when you require custom dataflow functionality, but you do not require a type that provides additional methods, properties, or fields.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="2c39a-117">派生自 IPropagatorBlock 以定义滑动窗口数据流块</span><span class="sxs-lookup"><span data-stu-id="2c39a-117">Deriving from IPropagatorBlock to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="2c39a-118">下面的示例展示了 `SlidingWindowBlock` 类。</span><span class="sxs-lookup"><span data-stu-id="2c39a-118">The following example shows the `SlidingWindowBlock` class.</span></span> <span data-ttu-id="2c39a-119">此类派生自 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>，可用作数据的源和目标。</span><span class="sxs-lookup"><span data-stu-id="2c39a-119">This class derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> so that it can act as both a source and a target of data.</span></span> <span data-ttu-id="2c39a-120">与上一示例中所述一样，`SlidingWindowBlock` 类是在现有数据流块类型的基础之上构建而成。</span><span class="sxs-lookup"><span data-stu-id="2c39a-120">As in the previous example, the `SlidingWindowBlock` class is built on existing dataflow block types.</span></span> <span data-ttu-id="2c39a-121">不同之处在于，`SlidingWindowBlock` 类还实现了 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 和 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> 接口所需的方法。</span><span class="sxs-lookup"><span data-stu-id="2c39a-121">However, the `SlidingWindowBlock` class also implements the methods that are required by the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, and <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfaces.</span></span> <span data-ttu-id="2c39a-122">这些方法全都将工作转发给预定义的数据流块类型成员。</span><span class="sxs-lookup"><span data-stu-id="2c39a-122">These methods all forward work to the predefined dataflow block type members.</span></span> <span data-ttu-id="2c39a-123">例如，`Post` 方法将工作转交给也是 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 对象的 `m_target` 数据成员。</span><span class="sxs-lookup"><span data-stu-id="2c39a-123">For example, the `Post` method defers work to the `m_target` data member, which is also an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object.</span></span>  
  
 <span data-ttu-id="2c39a-124">如果需要自定义数据流功能，还需要提供其他方法、属性或字段的类型，此方式就很有用。</span><span class="sxs-lookup"><span data-stu-id="2c39a-124">This technique is useful when you require custom dataflow functionality, and also require a type that provides additional methods, properties, or fields.</span></span> <span data-ttu-id="2c39a-125">例如，`SlidingWindowBlock` 类也派生自 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601>，这样就可以提供 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 和 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> 方法了。</span><span class="sxs-lookup"><span data-stu-id="2c39a-125">For example, the `SlidingWindowBlock` class also derives from <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> so that it can provide the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> and <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> methods.</span></span> <span data-ttu-id="2c39a-126">`SlidingWindowBlock` 类还具有扩展性，体现在提供 `WindowSize` 属性，以检索滑动窗口中的元素数量。</span><span class="sxs-lookup"><span data-stu-id="2c39a-126">The `SlidingWindowBlock` class also demonstrates extensibility by providing the `WindowSize` property, which retrieves the number of elements in the sliding window.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a><span data-ttu-id="2c39a-127">完整示例</span><span class="sxs-lookup"><span data-stu-id="2c39a-127">The Complete Example</span></span>  
 <span data-ttu-id="2c39a-128">下面的示例显示此演练的完整代码。</span><span class="sxs-lookup"><span data-stu-id="2c39a-128">The following example shows the complete code for this walkthrough.</span></span> <span data-ttu-id="2c39a-129">它还展示了如何在对块执行写入和读取操作并将结果打印到控制台的方法中使用两个滑动窗口块。</span><span class="sxs-lookup"><span data-stu-id="2c39a-129">It also demonstrates how to use the both sliding window blocks in a method that writes to the block, reads from it, and prints the results to the console.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="2c39a-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c39a-130">See also</span></span>

- [<span data-ttu-id="2c39a-131">数据流</span><span class="sxs-lookup"><span data-stu-id="2c39a-131">Dataflow</span></span>](dataflow-task-parallel-library.md)
