---
title: 权限被拒绝
ms.date: 07/20/2015
f1_keywords:
- vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
ms.openlocfilehash: 5ac585a86a783f36642545e368b1c2e694b89f62
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871163"
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="18797-102">权限被拒绝 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18797-102">Permission denied (Visual Basic)</span></span>

<span data-ttu-id="18797-103">尝试写入到写保护的磁盘或访问锁定的文件。</span><span class="sxs-lookup"><span data-stu-id="18797-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18797-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="18797-104">To correct this error</span></span>  
  
1. <span data-ttu-id="18797-105">若要打开写保护的文件，请更改文件的写保护特性。</span><span class="sxs-lookup"><span data-stu-id="18797-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2. <span data-ttu-id="18797-106">请确保其他进程未锁定该文件，并等待打开该文件，直到另一个进程释放它。</span><span class="sxs-lookup"><span data-stu-id="18797-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3. <span data-ttu-id="18797-107">若要访问注册表，请检查你的用户权限是否包括此类型的注册表访问权限。</span><span class="sxs-lookup"><span data-stu-id="18797-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18797-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18797-108">See also</span></span>

- [<span data-ttu-id="18797-109">错误类型</span><span class="sxs-lookup"><span data-stu-id="18797-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
