---
title: 不再支持“Line”语句（Visual Basic 编译器错误）
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 4ca1538dbde0d585b7b421d60cde4531c00e9145
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873834"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="bc545-102">不再支持“Line”语句（Visual Basic 编译器错误）</span><span class="sxs-lookup"><span data-stu-id="bc545-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>

<span data-ttu-id="bc545-103">不再支持行语句。</span><span class="sxs-lookup"><span data-stu-id="bc545-103">Line statements are no longer supported.</span></span> <span data-ttu-id="bc545-104">文件 i/o 功能提供为 `Microsoft.VisualBasic.FileSystem.LineInput` ，图形功能作为提供 `System.Drawing.Graphics.DrawLine` 。</span><span class="sxs-lookup"><span data-stu-id="bc545-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="bc545-105">**错误 ID：** BC30830</span><span class="sxs-lookup"><span data-stu-id="bc545-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bc545-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="bc545-106">To correct this error</span></span>  
  
1. <span data-ttu-id="bc545-107">如果执行文件访问，请使用 `Microsoft.VisualBasic.FileSystem.LineInput` 。</span><span class="sxs-lookup"><span data-stu-id="bc545-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2. <span data-ttu-id="bc545-108">如果执行图形，则请使用 `System.Drawing.Graphics.Drawline`。</span><span class="sxs-lookup"><span data-stu-id="bc545-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc545-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc545-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="bc545-110">使用 Visual Basic 访问文件</span><span class="sxs-lookup"><span data-stu-id="bc545-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
