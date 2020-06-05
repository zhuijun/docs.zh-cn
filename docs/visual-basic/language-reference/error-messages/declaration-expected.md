---
title: 需要声明
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 237622d0dc6c57f66d402f491a6191a5911574e2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409733"
---
# <a name="declaration-expected"></a><span data-ttu-id="1bbe0-102">需要声明</span><span class="sxs-lookup"><span data-stu-id="1bbe0-102">Declaration expected</span></span>
<span data-ttu-id="1bbe0-103">Nondeclarative 语句，如赋值语句或循环语句，在任何过程外发生。</span><span class="sxs-lookup"><span data-stu-id="1bbe0-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="1bbe0-104">仅允许在过程外使用声明。</span><span class="sxs-lookup"><span data-stu-id="1bbe0-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="1bbe0-105">或者，在没有声明关键字（如或）的情况下声明编程元素 `Dim` `Const` 。</span><span class="sxs-lookup"><span data-stu-id="1bbe0-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="1bbe0-106">**错误 ID：** BC30188</span><span class="sxs-lookup"><span data-stu-id="1bbe0-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1bbe0-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="1bbe0-107">To correct this error</span></span>  
  
- <span data-ttu-id="1bbe0-108">将 nondeclarative 语句移到过程的主体。</span><span class="sxs-lookup"><span data-stu-id="1bbe0-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
- <span data-ttu-id="1bbe0-109">使用适当的声明关键字开始声明。</span><span class="sxs-lookup"><span data-stu-id="1bbe0-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
- <span data-ttu-id="1bbe0-110">确保声明关键字没有拼写错误。</span><span class="sxs-lookup"><span data-stu-id="1bbe0-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bbe0-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bbe0-111">See also</span></span>

- [<span data-ttu-id="1bbe0-112">过程</span><span class="sxs-lookup"><span data-stu-id="1bbe0-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="1bbe0-113">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="1bbe0-113">Dim Statement</span></span>](../statements/dim-statement.md)
