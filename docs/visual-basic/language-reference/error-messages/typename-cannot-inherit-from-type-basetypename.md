---
title: “<typename>”将对基 <type> 的访问扩展到程序集的外部，因此无法从 <basetypename>“<type>”继承
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 5adb5a74c220c7b2f95ac7370040a7fa2bd34299
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872070"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="c4bc5-102">“\<typename>”将对基 \<type> 的访问扩展到程序集的外部，因此无法从 \<basetypename>“\<type>”继承</span><span class="sxs-lookup"><span data-stu-id="c4bc5-102">'\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>

<span data-ttu-id="c4bc5-103">类或接口继承自基类或接口，但具有限制性较低的访问级别。</span><span class="sxs-lookup"><span data-stu-id="c4bc5-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="c4bc5-104">例如， `Public` 接口从 `Friend` 接口继承，或 `Protected` 从 `Private` 类继承。</span><span class="sxs-lookup"><span data-stu-id="c4bc5-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="c4bc5-105">这会公开要访问的基类或接口超出目标级别。</span><span class="sxs-lookup"><span data-stu-id="c4bc5-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="c4bc5-106">**错误 ID：** BC30910</span><span class="sxs-lookup"><span data-stu-id="c4bc5-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c4bc5-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="c4bc5-107">To correct this error</span></span>  
  
- <span data-ttu-id="c4bc5-108">更改派生类或接口的访问级别，使其至少与基类或接口的访问级别具有相同的限制。</span><span class="sxs-lookup"><span data-stu-id="c4bc5-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="c4bc5-109">- 或 -</span><span class="sxs-lookup"><span data-stu-id="c4bc5-109">-or-</span></span>  
  
- <span data-ttu-id="c4bc5-110">如果需要限制性较低的访问级别，请删除 `Inherits` 语句。</span><span class="sxs-lookup"><span data-stu-id="c4bc5-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="c4bc5-111">不能从更受限制的基类或接口继承。</span><span class="sxs-lookup"><span data-stu-id="c4bc5-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4bc5-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4bc5-112">See also</span></span>

- [<span data-ttu-id="c4bc5-113">Class 语句</span><span class="sxs-lookup"><span data-stu-id="c4bc5-113">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="c4bc5-114">Interface 语句</span><span class="sxs-lookup"><span data-stu-id="c4bc5-114">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="c4bc5-115">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="c4bc5-115">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="c4bc5-116">Visual Basic 中的访问级别</span><span class="sxs-lookup"><span data-stu-id="c4bc5-116">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
