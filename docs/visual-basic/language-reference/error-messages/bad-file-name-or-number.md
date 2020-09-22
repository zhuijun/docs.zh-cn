---
title: 错误的文件名或文件号
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: d57a9e78e6ae179d3050e5a92399ca731fa16ba7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874907"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="cdba7-102">错误的文件名或文件号</span><span class="sxs-lookup"><span data-stu-id="cdba7-102">Bad file name or number</span></span>

<span data-ttu-id="cdba7-103">尝试访问指定的文件时出错。</span><span class="sxs-lookup"><span data-stu-id="cdba7-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="cdba7-104">此错误的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="cdba7-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="cdba7-105">语句引用的文件具有未在语句中指定 `FileOpen` 或在语句中指定的、 `FileOpen` 但随后已关闭的文件。</span><span class="sxs-lookup"><span data-stu-id="cdba7-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="cdba7-106">语句引用的文件的数量超出了文件编号范围。</span><span class="sxs-lookup"><span data-stu-id="cdba7-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="cdba7-107">语句引用的文件名或编号无效。</span><span class="sxs-lookup"><span data-stu-id="cdba7-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cdba7-108">更正此错误</span><span class="sxs-lookup"><span data-stu-id="cdba7-108">To correct this error</span></span>  
  
1. <span data-ttu-id="cdba7-109">请确保在语句中指定了文件名 `FileOpen` 。</span><span class="sxs-lookup"><span data-stu-id="cdba7-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="cdba7-110">请注意，如果调用 `FileClose` 不带参数的语句，则可能会无意中关闭所有打开的文件。</span><span class="sxs-lookup"><span data-stu-id="cdba7-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="cdba7-111">如果你的代码生成了文件号算法，请确保数字有效。</span><span class="sxs-lookup"><span data-stu-id="cdba7-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="cdba7-112">检查文件名，确保它们符合操作系统约定。</span><span class="sxs-lookup"><span data-stu-id="cdba7-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdba7-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cdba7-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="cdba7-114">Visual Basic 命名约定</span><span class="sxs-lookup"><span data-stu-id="cdba7-114">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
