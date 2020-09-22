---
title: “<membername>”在继承接口“<interfacename1>”和“<interfacename2>”之间不明确
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 8fb8f84b07c488c817fd85fdd256d9aca7558a77
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873799"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a><span data-ttu-id="74d8d-102">“\<membername>”在继承接口“\<interfacename1>”和“\<interfacename2>”之间不明确</span><span class="sxs-lookup"><span data-stu-id="74d8d-102">'\<membername>' is ambiguous across the inherited interfaces '\<interfacename1>' and '\<interfacename2>'</span></span>

<span data-ttu-id="74d8d-103">接口从多个接口继承具有相同名称的两个或多个成员。</span><span class="sxs-lookup"><span data-stu-id="74d8d-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>  
  
 <span data-ttu-id="74d8d-104">**错误 ID：** BC30685</span><span class="sxs-lookup"><span data-stu-id="74d8d-104">**Error ID:** BC30685</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="74d8d-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="74d8d-105">To correct this error</span></span>  
  
- <span data-ttu-id="74d8d-106">将值强制转换为要使用的基接口;例如：</span><span class="sxs-lookup"><span data-stu-id="74d8d-106">Cast the value to the base interface that you want to use; for example:</span></span>  
  
    ```vb  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="74d8d-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74d8d-107">See also</span></span>

- [<span data-ttu-id="74d8d-108">接口</span><span class="sxs-lookup"><span data-stu-id="74d8d-108">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
