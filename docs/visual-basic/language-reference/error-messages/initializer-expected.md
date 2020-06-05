---
title: 应为初始值设定项
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 13fa8917f228661fc44f5e0920d91c596e250c38
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402832"
---
# <a name="initializer-expected"></a><span data-ttu-id="09a0e-102">应为初始值设定项</span><span class="sxs-lookup"><span data-stu-id="09a0e-102">Initializer expected</span></span>
<span data-ttu-id="09a0e-103">您尝试使用对象初始值设定项声明类的实例，其中初始化列表为空，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="09a0e-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="09a0e-104">至少必须在初始值设定项列表中初始化一个字段或属性，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="09a0e-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="09a0e-105">**错误 ID：** BC30996</span><span class="sxs-lookup"><span data-stu-id="09a0e-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="09a0e-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="09a0e-106">To correct this error</span></span>  
  
1. <span data-ttu-id="09a0e-107">在初始值设定项中初始化至少一个字段或属性，或不使用对象初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="09a0e-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a0e-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09a0e-108">See also</span></span>

- [<span data-ttu-id="09a0e-109">对象初始值设定项：命名和匿名类型</span><span class="sxs-lookup"><span data-stu-id="09a0e-109">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="09a0e-110">如何：使用对象初始值设定项声明对象</span><span class="sxs-lookup"><span data-stu-id="09a0e-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
