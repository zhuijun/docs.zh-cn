---
title: <type1>“<typename>”必须为接口“<interfacename>”实现“<methodname>”
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 90d2b6d70390bfb732af4a5868c935de61d18f94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408492"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="f505a-102">\<type1>“\<typename>”必须为接口“\<interfacename>”实现“\<methodname>”</span><span class="sxs-lookup"><span data-stu-id="f505a-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="f505a-103">类或结构声明实现接口，但不实现由接口定义的过程。</span><span class="sxs-lookup"><span data-stu-id="f505a-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="f505a-104">必须实现接口的每个成员。</span><span class="sxs-lookup"><span data-stu-id="f505a-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="f505a-105">**错误 ID：** BC30149</span><span class="sxs-lookup"><span data-stu-id="f505a-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f505a-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="f505a-106">To correct this error</span></span>  
  
1. <span data-ttu-id="f505a-107">使用在接口中定义的相同名称和签名声明过程。</span><span class="sxs-lookup"><span data-stu-id="f505a-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="f505a-108">请确保至少包含 `End Function` 或 `End Sub` 语句。</span><span class="sxs-lookup"><span data-stu-id="f505a-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="f505a-109">将 `Implements` 子句添加到或语句的末尾 `Function` `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="f505a-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="f505a-110">例如：</span><span class="sxs-lookup"><span data-stu-id="f505a-110">For example:</span></span>  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f505a-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f505a-111">See also</span></span>

- [<span data-ttu-id="f505a-112">Implements 语句</span><span class="sxs-lookup"><span data-stu-id="f505a-112">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="f505a-113">接口</span><span class="sxs-lookup"><span data-stu-id="f505a-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
