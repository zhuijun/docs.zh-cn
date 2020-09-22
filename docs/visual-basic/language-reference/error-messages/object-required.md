---
title: 需要对象
ms.date: 07/20/2015
f1_keywords:
- vbrID424
ms.assetid: afdc660b-81a5-4c92-ac7e-9c3a3105fc16
ms.openlocfilehash: 5384dc603d51b31c252c9cad0775a453210f29ff
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873642"
---
# <a name="object-required-visual-basic"></a><span data-ttu-id="e03f4-102">需要对象 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e03f4-102">Object required (Visual Basic)</span></span>

<span data-ttu-id="e03f4-103">对属性和方法的引用通常需要显式对象限定符。</span><span class="sxs-lookup"><span data-stu-id="e03f4-103">References to properties and methods often require an explicit object qualifier.</span></span> <span data-ttu-id="e03f4-104">这就是这种情况。</span><span class="sxs-lookup"><span data-stu-id="e03f4-104">This is such a case.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e03f4-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="e03f4-105">To correct this error</span></span>  
  
1. <span data-ttu-id="e03f4-106">检查对对象属性或方法的引用是否具有有效的对象限定符。</span><span class="sxs-lookup"><span data-stu-id="e03f4-106">Check that references to an object property or method have valid object qualifier.</span></span> <span data-ttu-id="e03f4-107">如果未提供对象限定符，请指定它。</span><span class="sxs-lookup"><span data-stu-id="e03f4-107">Specify an object qualifier if you didn't provide one.</span></span>  
  
2. <span data-ttu-id="e03f4-108">检查对象限定符的拼写，并确保对象在您引用它的程序部分中可见。</span><span class="sxs-lookup"><span data-stu-id="e03f4-108">Check the spelling of the object qualifier and make sure the object is visible in the part of the program in which you are referencing it.</span></span>  
  
3. <span data-ttu-id="e03f4-109">如果向宿主应用程序的 " **文件打开** " 命令提供路径，请检查其中的参数是否正确。</span><span class="sxs-lookup"><span data-stu-id="e03f4-109">If a path is supplied to a host application's **File Open** command, check that the arguments in it are correct.</span></span>  
  
4. <span data-ttu-id="e03f4-110">检查对象的文档，并确保操作有效。</span><span class="sxs-lookup"><span data-stu-id="e03f4-110">Check the object's documentation and make sure the action is valid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e03f4-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e03f4-111">See also</span></span>

- [<span data-ttu-id="e03f4-112">错误类型</span><span class="sxs-lookup"><span data-stu-id="e03f4-112">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
