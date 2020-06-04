---
title: “<keyword>”只在实例方法中有效
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 537689405ea30bdd7c075320eba58a8723a93cdb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397397"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="68ef4-102">“\<keyword>”只在实例方法中有效</span><span class="sxs-lookup"><span data-stu-id="68ef4-102">'\<keyword>' is valid only within an instance method</span></span>
<span data-ttu-id="68ef4-103">`Me`、 `MyClass` 和 `MyBase` 关键字引用特定的类实例。</span><span class="sxs-lookup"><span data-stu-id="68ef4-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="68ef4-104">不能在共享或过程中使用它们 `Function` `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="68ef4-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="68ef4-105">**错误 ID：** BC30043</span><span class="sxs-lookup"><span data-stu-id="68ef4-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="68ef4-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="68ef4-106">To correct this error</span></span>  
  
- <span data-ttu-id="68ef4-107">从过程中删除关键字，或 `Shared` 从过程声明中删除关键字。</span><span class="sxs-lookup"><span data-stu-id="68ef4-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68ef4-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68ef4-108">See also</span></span>

- [<span data-ttu-id="68ef4-109">对象变量赋值</span><span class="sxs-lookup"><span data-stu-id="68ef4-109">Object Variable Assignment</span></span>](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="68ef4-110">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="68ef4-110">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="68ef4-111">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="68ef4-111">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
