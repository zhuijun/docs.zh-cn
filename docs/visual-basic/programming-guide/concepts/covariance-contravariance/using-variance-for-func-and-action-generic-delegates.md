---
title: 对 Func 和 Action 泛型委托使用变体
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: f824d2422d67f1395d21a0863ca8c95d9f108989
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375753"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="27f63-102">对 Func 和 Action 泛型委托使用变体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27f63-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>

<span data-ttu-id="27f63-103">这些示例演示如何使用 `Func` 和 `Action` 泛型委托中的协变和逆变来启用重用方法并为代码中提供更多的灵活性。</span><span class="sxs-lookup"><span data-stu-id="27f63-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>

<span data-ttu-id="27f63-104">有关协变和逆变的详细信息，请参阅[委托中的变体（Visual Basic）](variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="27f63-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="27f63-105">使用具有协变类型参数的委托</span><span class="sxs-lookup"><span data-stu-id="27f63-105">Using Delegates with Covariant Type Parameters</span></span>

<span data-ttu-id="27f63-106">下例阐释了泛型 `Func` 委托中的协变支持的益处。</span><span class="sxs-lookup"><span data-stu-id="27f63-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="27f63-107">`FindByTitle` 方法采用 `String` 类型的一个参数，并返回 `Employee` 类型的一个对象。</span><span class="sxs-lookup"><span data-stu-id="27f63-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="27f63-108">但是，可将此方法分配给 `Func(Of String, Person)` 委托，因为 `Employee` 继承 `Person`。</span><span class="sxs-lookup"><span data-stu-id="27f63-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>

```vb
' Simple hierarchy of classes.
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class Finder
    Public Shared Function FindByTitle(
        ByVal title As String) As Employee
        ' This is a stub for a method that returns
        ' an employee that has the specified title.
        Return New Employee
    End Function

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim findEmployee As Func(Of String, Employee) =
            AddressOf FindByTitle

        ' The delegate expects a method to return Person,
        ' but you can assign it a method that returns Employee.
        Dim findPerson As Func(Of String, Person) =
            AddressOf FindByTitle

        ' You can also assign a delegate
        ' that returns a more derived type to a delegate
        ' that returns a less derived type.
        findPerson = findEmployee
    End Sub
End Class
```

## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="27f63-109">使用具有逆变类型参数的委托</span><span class="sxs-lookup"><span data-stu-id="27f63-109">Using Delegates with Contravariant Type Parameters</span></span>

<span data-ttu-id="27f63-110">下例阐释了泛型 `Action` 委托中的逆变支持的益处。</span><span class="sxs-lookup"><span data-stu-id="27f63-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="27f63-111">`AddToContacts` 方法采用 `Person` 类型的一个参数。</span><span class="sxs-lookup"><span data-stu-id="27f63-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="27f63-112">但是，可将此方法分配给 `Action(Of Employee)` 委托，因为 `Employee` 继承 `Person`。</span><span class="sxs-lookup"><span data-stu-id="27f63-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>

```vb
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class AddressBook
    Shared Sub AddToContacts(ByVal person As Person)
        ' This method adds a Person object
        ' to a contact list.
    End Sub

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim addPersonToContacts As Action(Of Person) =
            AddressOf AddToContacts

        ' The Action delegate expects
        ' a method that has an Employee parameter,
        ' but you can assign it a method that has a Person parameter
        ' because Employee derives from Person.
        Dim addEmployeeToContacts As Action(Of Employee) =
            AddressOf AddToContacts

        ' You can also assign a delegate
        ' that accepts a less derived parameter
        ' to a delegate that accepts a more derived parameter.
        addEmployeeToContacts = addPersonToContacts
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="27f63-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27f63-113">See also</span></span>

- [<span data-ttu-id="27f63-114">协变和逆变 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27f63-114">Covariance and Contravariance (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="27f63-115">泛型</span><span class="sxs-lookup"><span data-stu-id="27f63-115">Generics</span></span>](../../../../standard/generics/index.md)
