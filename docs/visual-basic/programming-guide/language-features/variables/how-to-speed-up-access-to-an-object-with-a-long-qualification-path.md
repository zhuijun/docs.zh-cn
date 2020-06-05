---
title: 如何：加速访问具有长限定路径的对象
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: fe93e7bac2a21f1060d1f93765eb35e1ad0c7eb0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410407"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="26fe3-102">如何：加速访问具有长限定路径的对象 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26fe3-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="26fe3-103">如果经常访问的对象需要多个方法和属性的限定路径，则可以通过不重复限定路径来加快代码的速度。</span><span class="sxs-lookup"><span data-stu-id="26fe3-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="26fe3-104">可以通过两种方法来避免重复限定路径。</span><span class="sxs-lookup"><span data-stu-id="26fe3-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="26fe3-105">可以将对象分配给一个变量，也可以在 `With` ... 块中使用它。 `End With`</span><span class="sxs-lookup"><span data-stu-id="26fe3-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="26fe3-106">通过将严重限定对象赋给变量来加快对该对象的访问速度</span><span class="sxs-lookup"><span data-stu-id="26fe3-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="26fe3-107">声明经常访问的对象类型的变量。</span><span class="sxs-lookup"><span data-stu-id="26fe3-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="26fe3-108">指定声明的初始化部分中的限定路径。</span><span class="sxs-lookup"><span data-stu-id="26fe3-108">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="26fe3-109">使用变量访问对象的成员。</span><span class="sxs-lookup"><span data-stu-id="26fe3-109">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="26fe3-110">若要通过使用 With，加速对严重限定对象的访问结尾为块</span><span class="sxs-lookup"><span data-stu-id="26fe3-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="26fe3-111">将限定路径放在 `With` 语句中。</span><span class="sxs-lookup"><span data-stu-id="26fe3-111">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="26fe3-112">在语句前面的块内访问对象的成员 `With` `End With` 。</span><span class="sxs-lookup"><span data-stu-id="26fe3-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="26fe3-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26fe3-113">See also</span></span>

- [<span data-ttu-id="26fe3-114">对象变量</span><span class="sxs-lookup"><span data-stu-id="26fe3-114">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="26fe3-115">With...End With 语句</span><span class="sxs-lookup"><span data-stu-id="26fe3-115">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
