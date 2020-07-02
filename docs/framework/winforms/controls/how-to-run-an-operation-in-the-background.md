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
# <a name="how-to-run-an-operation-in-the-background"></a>如何：在后台运行操作
如果某项操作需要很长时间才能完成，而你不希望造成用户界面的延迟，则可以使用 <xref:System.ComponentModel.BackgroundWorker> 类在另一个线程上运行此操作。  
  
 以下代码示例显示如何在后台运行耗时的操作。 此窗体具有“启动”**** 和“取消”**** 按钮。 单击“启动”**** 按钮运行异步操作。 单击“取消”**** 按钮停止运行异步操作。 每个操作的结果显示在 <xref:System.Windows.Forms.MessageBox> 中。  
  
 Visual Studio 中对此任务提供广泛支持。  
  
 另请参阅[演练：在后台运行操作](walkthrough-running-an-operation-in-the-background.md)。  
  
## <a name="example"></a>示例  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
- 对 System、System.Drawing 和 System.Windows.Forms 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [如何：实现使用后台操作的窗体](how-to-implement-a-form-that-uses-a-background-operation.md)
- [BackgroundWorker 组件](backgroundworker-component.md)
