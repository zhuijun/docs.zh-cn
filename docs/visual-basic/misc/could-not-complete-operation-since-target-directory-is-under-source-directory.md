---
title: 未能完成操作，因为目标目录位于源目录下
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: d159b9bb3a765a2fefe99fa15dff42e979fda9e3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079134"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="f70a4-102">未能完成操作，因为目标目录位于源目录下</span><span class="sxs-lookup"><span data-stu-id="f70a4-102">Could not complete operation since target directory is under source directory</span></span>

<span data-ttu-id="f70a4-103">循环操作已失败。</span><span class="sxs-lookup"><span data-stu-id="f70a4-103">A cyclic operation has failed.</span></span> <span data-ttu-id="f70a4-104">循环操作正在循环，因此无法完成。</span><span class="sxs-lookup"><span data-stu-id="f70a4-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="f70a4-105">例如，对象 A 可能会尝试从对象 B 中继承，而后者反之从对象 A 中继承。</span><span class="sxs-lookup"><span data-stu-id="f70a4-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f70a4-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="f70a4-106">To correct this error</span></span>  
  
- <span data-ttu-id="f70a4-107">继承时，请确保没有任何循环引用。</span><span class="sxs-lookup"><span data-stu-id="f70a4-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f70a4-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="f70a4-108">See also</span></span>

- [<span data-ttu-id="f70a4-109">错误类型</span><span class="sxs-lookup"><span data-stu-id="f70a4-109">Error Types</span></span>](../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="f70a4-110">在 Visual Studio 调试器中使用断点</span><span class="sxs-lookup"><span data-stu-id="f70a4-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
