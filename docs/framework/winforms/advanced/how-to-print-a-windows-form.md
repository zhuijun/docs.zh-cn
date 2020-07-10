---
title: 如何：打印 Windows 窗体
description: 了解如何使用 CopyFromScreen 方法以编程方式打印当前 Windows 窗体的副本。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: b59ea4b5347903b36a166c4f8ac0d8d7db18635e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174687"
---
# <a name="how-to-print-a-windows-form"></a>如何：打印 Windows 窗体
作为开发过程的一部分，通常需要打印 Windows 窗体的副本。 下面的代码示例演示如何使用方法打印当前窗体的副本 <xref:System.Drawing.Graphics.CopyFromScreen%2A> 。  
  
## <a name="example"></a>示例  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a>可靠编程  
 以下情况可能会导致异常：  
  
- 你没有访问打印机的权限。  
  
- 未安装打印机。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 若要运行此代码示例，您必须有权访问您的计算机所使用的打印机。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Drawing.Printing.PrintDocument>
- [如何：使用 GDI+ 呈现图像](how-to-render-images-with-gdi.md)
- [如何：打印 Windows 窗体中的图形](how-to-print-graphics-in-windows-forms.md)
