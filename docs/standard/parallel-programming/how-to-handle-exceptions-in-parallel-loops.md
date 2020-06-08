---
title: 如何：处理并行循环中的异常
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 87405425e85ed16d10b3e8b382c6e414fff10ddf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278527"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>如何：处理并行循环中的异常
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 重载没有任何用于处理可能引发的异常的特殊机制。 在这一方面，它们类似于常规 `for` 和 `foreach` 循环（在 Visual Basic 中为 `For` 和 `For Each`）；未处理的异常会导致循环在当前运行的迭代完成后立即终止。
  
 向并行循环添加自己的异常处理逻辑时，将处理类似于在多个线程上同时引发相似异常的情况，以及一个线程上引发异常导致另一个线程上引发另一个异常的情况。 你可以通过将循环中的所有异常包装到一个 <xref:System.AggregateException?displayProperty=nameWithType> 中处理这两种情况。 下面的示例演示了一种可能的方法。  
  
> [!NOTE]
> 某些情况下，当启用“仅我的代码”后，Visual Studio 会在引发异常的行中断运行并显示一条错误消息，该消息显示“用户代码未处理异常”。 此错误是良性的。 可以按 F5 继续运行，并请参阅下面示例中所示的异常处理行为。 为了阻止 Visual Studio 在第一个错误出现时中断，只需依次转到“工具”、“选项”、“调试”、“常规”  下，取消选中“仅我的代码”复选框即可。  
  
## <a name="example"></a>示例  
 在此示例中，所有异常都被捕获，并包装到引发的 <xref:System.AggregateException?displayProperty=nameWithType> 中。 调用方可以决定要处理哪些异常。  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>另请参阅

- [数据并行](data-parallelism-task-parallel-library.md)
- [PLINQ 和 TPL 中的 Lambda 表达式](lambda-expressions-in-plinq-and-tpl.md)
