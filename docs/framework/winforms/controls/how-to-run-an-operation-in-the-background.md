---
title: 如何：在后台运行操作
description: 了解如何使用 BackgroundWorker 类在后台运行耗时 Windows 窗体操作。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
ms.openlocfilehash: 6b2a97f5acf1e906dfe141aee62e99a4e50dca9f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621569"
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="7f40d-103">如何：在后台运行操作</span><span class="sxs-lookup"><span data-stu-id="7f40d-103">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="7f40d-104">如果某项操作需要很长时间才能完成，而你不希望造成用户界面的延迟，则可以使用 <xref:System.ComponentModel.BackgroundWorker> 类在另一个线程上运行此操作。</span><span class="sxs-lookup"><span data-stu-id="7f40d-104">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="7f40d-105">以下代码示例显示如何在后台运行耗时的操作。</span><span class="sxs-lookup"><span data-stu-id="7f40d-105">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="7f40d-106">此窗体具有“启动”\*\*\*\* 和“取消”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="7f40d-106">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="7f40d-107">单击“启动”\*\*\*\* 按钮运行异步操作。</span><span class="sxs-lookup"><span data-stu-id="7f40d-107">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="7f40d-108">单击“取消”\*\*\*\* 按钮停止运行异步操作。</span><span class="sxs-lookup"><span data-stu-id="7f40d-108">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="7f40d-109">每个操作的结果显示在 <xref:System.Windows.Forms.MessageBox> 中。</span><span class="sxs-lookup"><span data-stu-id="7f40d-109">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="7f40d-110">Visual Studio 中对此任务提供广泛支持。</span><span class="sxs-lookup"><span data-stu-id="7f40d-110">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="7f40d-111">另请参阅[演练：在后台运行操作](walkthrough-running-an-operation-in-the-background.md)。</span><span class="sxs-lookup"><span data-stu-id="7f40d-111">Also see [Walkthrough: Running an Operation in the Background](walkthrough-running-an-operation-in-the-background.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f40d-112">示例</span><span class="sxs-lookup"><span data-stu-id="7f40d-112">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f40d-113">编译代码</span><span class="sxs-lookup"><span data-stu-id="7f40d-113">Compiling the Code</span></span>  
 <span data-ttu-id="7f40d-114">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="7f40d-114">This example requires:</span></span>  
  
- <span data-ttu-id="7f40d-115">对 System、System.Drawing 和 System.Windows.Forms 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="7f40d-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f40d-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="7f40d-116">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="7f40d-117">如何：实现使用后台操作的窗体</span><span class="sxs-lookup"><span data-stu-id="7f40d-117">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="7f40d-118">BackgroundWorker 组件</span><span class="sxs-lookup"><span data-stu-id="7f40d-118">BackgroundWorker Component</span></span>](backgroundworker-component.md)
