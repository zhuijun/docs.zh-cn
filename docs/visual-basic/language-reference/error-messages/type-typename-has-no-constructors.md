---
title: 类型“<typename>”没有构造函数
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: de0d825c7eec603f3ad1e43b1e4aaa0cc78fd1db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408500"
---
# <a name="type-typename-has-no-constructors"></a><span data-ttu-id="a1c96-102">类型“\<typename>”没有构造函数</span><span class="sxs-lookup"><span data-stu-id="a1c96-102">Type '\<typename>' has no constructors</span></span>
<span data-ttu-id="a1c96-103">某个类型不支持对 `Sub New()` 的调用。</span><span class="sxs-lookup"><span data-stu-id="a1c96-103">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="a1c96-104">一个可能的原因是编译器或二进制文件被损坏。</span><span class="sxs-lookup"><span data-stu-id="a1c96-104">One possible cause is a corrupted compiler or binary file.</span></span>  
  
 <span data-ttu-id="a1c96-105">**错误 ID：** BC30251</span><span class="sxs-lookup"><span data-stu-id="a1c96-105">**Error ID:** BC30251</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a1c96-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="a1c96-106">To correct this error</span></span>  
  
1. <span data-ttu-id="a1c96-107">如果该类型位于其他项目或一个引用的文件中，则重新安装此项目或文件。</span><span class="sxs-lookup"><span data-stu-id="a1c96-107">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>  
  
2. <span data-ttu-id="a1c96-108">如果该类型位于同一个项目中，则重新编译包含该类型的程序集。</span><span class="sxs-lookup"><span data-stu-id="a1c96-108">If the type is in the same project, recompile the assembly containing the type.</span></span>  
  
3. <span data-ttu-id="a1c96-109">如果错误重复出现，请重新安装 Visual Basic 编译器。</span><span class="sxs-lookup"><span data-stu-id="a1c96-109">If the error recurs, reinstall the Visual Basic compiler.</span></span>  
  
4. <span data-ttu-id="a1c96-110">如果仍然出现错误，则收集有关该情况的信息并通知 Microsoft 产品支持服务。</span><span class="sxs-lookup"><span data-stu-id="a1c96-110">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c96-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1c96-111">See also</span></span>

- [<span data-ttu-id="a1c96-112">对象和类</span><span class="sxs-lookup"><span data-stu-id="a1c96-112">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="a1c96-113">与我们交流</span><span class="sxs-lookup"><span data-stu-id="a1c96-113">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
