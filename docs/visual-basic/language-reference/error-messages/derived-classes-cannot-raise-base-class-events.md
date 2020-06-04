---
title: 派生类无法引发基类事件
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: c59212a28ba27123a7db9163ff7437c159a3d310
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409694"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="c119e-102">派生类无法引发基类事件</span><span class="sxs-lookup"><span data-stu-id="c119e-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="c119e-103">事件只能从声明它的声明空间引发。</span><span class="sxs-lookup"><span data-stu-id="c119e-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="c119e-104">因此，类无法从任何其他类（甚至是从中派生的类）引发事件。</span><span class="sxs-lookup"><span data-stu-id="c119e-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="c119e-105">**错误 ID：** BC30029</span><span class="sxs-lookup"><span data-stu-id="c119e-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c119e-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="c119e-106">To correct this error</span></span>  
  
- <span data-ttu-id="c119e-107">移动 `Event` 语句或 `RaiseEvent` 语句，使其位于同一个类中。</span><span class="sxs-lookup"><span data-stu-id="c119e-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c119e-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c119e-108">See also</span></span>

- [<span data-ttu-id="c119e-109">Event 语句</span><span class="sxs-lookup"><span data-stu-id="c119e-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="c119e-110">RaiseEvent 语句</span><span class="sxs-lookup"><span data-stu-id="c119e-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
