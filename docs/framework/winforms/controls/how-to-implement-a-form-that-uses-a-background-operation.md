---
title: 如何：实现使用后台操作的窗体
description: 了解如何实现一个 Windows 窗体，该窗体使用后台操作，以便一个操作可以继续运行，同时另一个操作继续运行。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: 23bf4bc02fbf998d92dfce6d84e4e337cbefe7d9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174518"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>如何：实现使用后台操作的窗体
以下示例程序创建一个计算 Fibonacci 数字的窗体。 计算在独立于用户界面线程的线程上运行，因此用户界面将随计算继续运行，不会延迟。  
  
 Visual Studio 中对此任务提供广泛支持。  
  
 另请参阅[演练：实现使用后台操作的窗体](walkthrough-implementing-a-form-that-uses-a-background-operation.md)。  
  
## <a name="example"></a>示例  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
- 对 System、System.Drawing 和 System.Windows.Forms 程序集的引用。  
  
## <a name="robust-programming"></a>可靠编程  
  
> [!CAUTION]
> 使用任何一种多线程都可能引起极为严重和复杂的 Bug。 在实现任何使用多线程处理的解决方案之前，请参阅[托管线程处理最佳做法](../../../standard/threading/managed-threading-best-practices.md)。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [基于事件的异步模式概述](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [托管线程处理的最佳做法](../../../standard/threading/managed-threading-best-practices.md)
