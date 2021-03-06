---
title: 如何：使用 SpinLock 进行低级别同步
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: ad254cb6208bff868e5fc689c502b7ddcc175ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137952"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>如何：使用 SpinLock 进行低级别同步

下面的示例展示了如何使用 <xref:System.Threading.SpinLock>。 在此示例中，关键部分执行的工作量最少，因而非常适合执行 <xref:System.Threading.SpinLock>。 与标准锁相比，增加一点工作量即可提升 <xref:System.Threading.SpinLock> 的性能。 但是，超过某个点时 SpinLock 将比标准锁开销更大。 可以使用分析工具中的并发分析功能，查看哪种类型的锁可以在程序中提供更好的性能。 有关详细信息，请参阅[并发可视化工具](/visualstudio/profiling/concurrency-visualizer)。  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 如果共享资源上的锁不会保留太长时间，<xref:System.Threading.SpinLock> 可能会很有用。 在这种情况下，多核计算机上的阻止线程可高效旋转几个周期，直到锁被释放。 通过旋转，线程不会受到阻止，这是一个占用大量 CPU 资源的进程。 在某些情况下，<xref:System.Threading.SpinLock> 会停止旋转，以防出现逻辑处理器资源不足或超线程系统上优先级反转的情况。  
  
 此示例使用 <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> 类，要求必须有用户同步，才能执行多线程访问。 在定目标到 .NET Framework 版本 4 的应用中，另一种选择是使用不需要任何用户锁的 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>。  
  
 请注意，在 <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType> 调用中使用 `false`（Visual Basic 中的 `False`）。 这可提供最佳性能。 在 IA64 架构上指定 `true`（Visual Basic 中为 `True`）可使用内存栅栏，这会刷新写入缓冲区以确保锁现在可用于其他线程退出。  
  
## <a name="see-also"></a>另请参阅

- [线程处理对象和功能](threading-objects-and-features.md)
- [lock 语句 (C#)](../../csharp/language-reference/keywords/lock-statement.md)
- [SyncLock 语句 (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
