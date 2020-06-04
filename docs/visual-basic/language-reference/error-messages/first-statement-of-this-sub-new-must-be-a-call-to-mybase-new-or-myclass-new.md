---
title: 该“Sub New”的第一个语句必须是对“MyBase.New”或“MyClass.New”的调用（没有不带参数的可访问构造函数）
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 2b9d2568fb64e4af72733ad1f3dee58aaee650e5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402974"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a><span data-ttu-id="2f880-102">该“Sub New”的第一个语句必须是对“MyBase.New”或“MyClass.New”的调用（没有不带参数的可访问构造函数）</span><span class="sxs-lookup"><span data-stu-id="2f880-102">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="2f880-103">此 "Sub New" 的第一条语句必须是对 "MyBase. New" 或 "MyClass" 的调用 \<basename> ，因为 "" 的基类 "" 没有 \<derivedname> 可在没有参数的情况下调用的可访问 "Sub New"。</span><span class="sxs-lookup"><span data-stu-id="2f880-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="2f880-104">在派生类中，每个构造函数都必须调用基类构造函数（ `MyBase.New` ）。</span><span class="sxs-lookup"><span data-stu-id="2f880-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="2f880-105">如果基类的构造函数不具有可由派生类访问的参数，则 `MyBase.New` 可以自动调用。</span><span class="sxs-lookup"><span data-stu-id="2f880-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="2f880-106">如果不是，则必须使用参数调用基类构造函数，这不能自动完成。</span><span class="sxs-lookup"><span data-stu-id="2f880-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="2f880-107">在这种情况下，每个派生类构造函数的第一条语句必须调用基类上的参数化构造函数，或调用派生类中的另一个构造函数，该构造函数将调用基类构造函数。</span><span class="sxs-lookup"><span data-stu-id="2f880-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="2f880-108">**错误 ID：** BC30148</span><span class="sxs-lookup"><span data-stu-id="2f880-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2f880-109">更正此错误</span><span class="sxs-lookup"><span data-stu-id="2f880-109">To correct this error</span></span>  
  
- <span data-ttu-id="2f880-110">请调用 `MyBase.New` 提供所需的参数，或调用进行此类调用的对等构造函数。</span><span class="sxs-lookup"><span data-stu-id="2f880-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="2f880-111">例如，如果基类的构造函数声明为 `Public Sub New(ByVal index as Integer)` ，则派生类构造函数中的第一条语句可能是 `MyBase.New(100)` 。</span><span class="sxs-lookup"><span data-stu-id="2f880-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f880-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f880-112">See also</span></span>

- [<span data-ttu-id="2f880-113">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="2f880-113">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
