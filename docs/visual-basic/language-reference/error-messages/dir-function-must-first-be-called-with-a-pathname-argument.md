---
title: 必须首先用一个“PathName”自变量调用“Dir”函数
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1064a44f7c266b9dcce05dfddedef6bb1e919999
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874457"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="98d80-102">必须首先用一个“PathName”自变量调用“Dir”函数</span><span class="sxs-lookup"><span data-stu-id="98d80-102">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="98d80-103">对函数的初始调用 `Dir` 不包含 `PathName` 参数。</span><span class="sxs-lookup"><span data-stu-id="98d80-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="98d80-104">对的第一次调用 `Dir` 必须包含 `PathName` ，但对的后续调用 `Dir` 不需要包含参数来检索下一项。</span><span class="sxs-lookup"><span data-stu-id="98d80-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="98d80-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="98d80-105">To correct this error</span></span>  
  
1. <span data-ttu-id="98d80-106">`PathName`在函数调用中提供参数。</span><span class="sxs-lookup"><span data-stu-id="98d80-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d80-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98d80-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
