---
title: 在类构造函数中使用类的默认实例可能会导致无限递归调用
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 5d239fdb7dcc5c488bf0341043b810ec7dadc083
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100316"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="9e73c-102">在类构造函数中使用类的默认实例可能会导致无限递归调用</span><span class="sxs-lookup"><span data-stu-id="9e73c-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>

<span data-ttu-id="9e73c-103">已在类的构造函数中使用类的默认实例。</span><span class="sxs-lookup"><span data-stu-id="9e73c-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="9e73c-104">这可能会导致无限递归调用（也称为无限循环）。</span><span class="sxs-lookup"><span data-stu-id="9e73c-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9e73c-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="9e73c-105">To correct this error</span></span>  
  
- <span data-ttu-id="9e73c-106">从类构造函数中删除默认实例。</span><span class="sxs-lookup"><span data-stu-id="9e73c-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e73c-107">请参阅</span><span class="sxs-lookup"><span data-stu-id="9e73c-107">See also</span></span>

- [<span data-ttu-id="9e73c-108">构造函数</span><span class="sxs-lookup"><span data-stu-id="9e73c-108">Constructors</span></span>](../programming-guide/concepts/object-oriented-programming.md#constructors)
