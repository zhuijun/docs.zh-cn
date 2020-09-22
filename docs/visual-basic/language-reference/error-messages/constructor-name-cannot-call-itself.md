---
title: 构造函数“<name>”不能调用自身
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: dce98a4deef8fbb0e8bc024244b815e23d51c790
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874574"
---
# <a name="constructor-name-cannot-call-itself"></a><span data-ttu-id="bc54f-102">构造函数“\<name>”不能调用自身</span><span class="sxs-lookup"><span data-stu-id="bc54f-102">Constructor '\<name>' cannot call itself</span></span>

<span data-ttu-id="bc54f-103">`Sub New`类或结构中的过程调用自身。</span><span class="sxs-lookup"><span data-stu-id="bc54f-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="bc54f-104">构造函数的目的是在第一次创建类或结构时初始化该类或结构的实例。</span><span class="sxs-lookup"><span data-stu-id="bc54f-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="bc54f-105">类或结构可以有多个构造函数，前提是它们都具有不同的参数列表。</span><span class="sxs-lookup"><span data-stu-id="bc54f-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="bc54f-106">除了自身之外，还允许构造函数调用另一个构造函数来执行其功能。</span><span class="sxs-lookup"><span data-stu-id="bc54f-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="bc54f-107">但构造函数调用自身是毫无意义的，事实上，如果允许，它会导致无限递归。</span><span class="sxs-lookup"><span data-stu-id="bc54f-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="bc54f-108">**错误 ID：** BC30298</span><span class="sxs-lookup"><span data-stu-id="bc54f-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bc54f-109">更正此错误</span><span class="sxs-lookup"><span data-stu-id="bc54f-109">To correct this error</span></span>  
  
1. <span data-ttu-id="bc54f-110">检查正在被调用的构造函数的参数列表。</span><span class="sxs-lookup"><span data-stu-id="bc54f-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="bc54f-111">它应不同于发出调用的构造函数的。</span><span class="sxs-lookup"><span data-stu-id="bc54f-111">It should be different from that of the constructor making the call.</span></span>  
  
2. <span data-ttu-id="bc54f-112">如果不打算调用另一个构造函数，请完全删除该 `Sub New` 调用。</span><span class="sxs-lookup"><span data-stu-id="bc54f-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc54f-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc54f-113">See also</span></span>

- [<span data-ttu-id="bc54f-114">对象生存期：如何创建和销毁对象</span><span class="sxs-lookup"><span data-stu-id="bc54f-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
