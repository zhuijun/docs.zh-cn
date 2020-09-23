---
title: 如何：引用对象的当前实例
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 64d21fe4aaf6fd34bf880373a7ab3067fb67820e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077054"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="2b4a0-102">如何：引用对象的当前实例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b4a0-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>

<span data-ttu-id="2b4a0-103">对象的 *当前实例* 是当前在其中执行代码的实例。</span><span class="sxs-lookup"><span data-stu-id="2b4a0-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="2b4a0-104">使用 `Me` 关键字引用当前实例。</span><span class="sxs-lookup"><span data-stu-id="2b4a0-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="2b4a0-105">引用当前实例</span><span class="sxs-lookup"><span data-stu-id="2b4a0-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="2b4a0-106">使用 `Me` 关键字，通常使用对象变量的名称。</span><span class="sxs-lookup"><span data-stu-id="2b4a0-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="2b4a0-107">尽管 `Me` 的行为与对象变量类似，但不能对其进行声明或向其分配任何内容。</span><span class="sxs-lookup"><span data-stu-id="2b4a0-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="2b4a0-108">`Me` 始终引用当前实例。</span><span class="sxs-lookup"><span data-stu-id="2b4a0-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b4a0-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="2b4a0-109">See also</span></span>

- [<span data-ttu-id="2b4a0-110">对象变量</span><span class="sxs-lookup"><span data-stu-id="2b4a0-110">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="2b4a0-111">对象变量赋值</span><span class="sxs-lookup"><span data-stu-id="2b4a0-111">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="2b4a0-112">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="2b4a0-112">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
