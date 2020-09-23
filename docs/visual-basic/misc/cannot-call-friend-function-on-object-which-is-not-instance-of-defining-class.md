---
title: 在不是定义类的实例的对象上不能调用友元函数
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: fe95f80d42fc12ab2829db899fe295e32f358db6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059803"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="e0917-102">在不是定义类的实例的对象上不能调用友元函数</span><span class="sxs-lookup"><span data-stu-id="e0917-102">Cannot call friend function on object which is not an instance of defining class</span></span>

<span data-ttu-id="e0917-103">尝试调用某个类的 `Friend` 过程，或者尝试跨进程或跨线程访问 `Friend` 属性或方法。</span><span class="sxs-lookup"><span data-stu-id="e0917-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="e0917-104">`Friend` 过程可从类外部的模块中调用，但该模块是在其中定义该类的项目的一部分。</span><span class="sxs-lookup"><span data-stu-id="e0917-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e0917-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="e0917-105">To correct this error</span></span>  
  
- <span data-ttu-id="e0917-106">确保从模块中调用或访问该过程，此模块是在其中定义该类的项目的一部分。</span><span class="sxs-lookup"><span data-stu-id="e0917-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0917-107">请参阅</span><span class="sxs-lookup"><span data-stu-id="e0917-107">See also</span></span>

- [<span data-ttu-id="e0917-108">Friend</span><span class="sxs-lookup"><span data-stu-id="e0917-108">Friend</span></span>](../language-reference/modifiers/friend.md)
