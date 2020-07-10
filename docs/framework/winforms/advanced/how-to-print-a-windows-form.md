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
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="b7417-103">如何：打印 Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="b7417-103">How to: Print a Windows Form</span></span>
<span data-ttu-id="b7417-104">作为开发过程的一部分，通常需要打印 Windows 窗体的副本。</span><span class="sxs-lookup"><span data-stu-id="b7417-104">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="b7417-105">下面的代码示例演示如何使用方法打印当前窗体的副本 <xref:System.Drawing.Graphics.CopyFromScreen%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b7417-105">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7417-106">示例</span><span class="sxs-lookup"><span data-stu-id="b7417-106">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b7417-107">可靠编程</span><span class="sxs-lookup"><span data-stu-id="b7417-107">Robust Programming</span></span>  
 <span data-ttu-id="b7417-108">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="b7417-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b7417-109">你没有访问打印机的权限。</span><span class="sxs-lookup"><span data-stu-id="b7417-109">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="b7417-110">未安装打印机。</span><span class="sxs-lookup"><span data-stu-id="b7417-110">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b7417-111">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="b7417-111">.NET Framework Security</span></span>  
 <span data-ttu-id="b7417-112">若要运行此代码示例，您必须有权访问您的计算机所使用的打印机。</span><span class="sxs-lookup"><span data-stu-id="b7417-112">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7417-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7417-113">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="b7417-114">如何：使用 GDI+ 呈现图像</span><span class="sxs-lookup"><span data-stu-id="b7417-114">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="b7417-115">如何：打印 Windows 窗体中的图形</span><span class="sxs-lookup"><span data-stu-id="b7417-115">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
