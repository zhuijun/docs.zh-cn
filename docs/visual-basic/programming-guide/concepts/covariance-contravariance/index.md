---
title: 协变和逆变
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 11dd71a8cfde12b7af1de79e3f5a095f79d8aa6e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400625"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="4d9f8-102">协变和逆变 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d9f8-102">Covariance and Contravariance (Visual Basic)</span></span>

<span data-ttu-id="4d9f8-103">在 Visual Basic 中，协变和逆变能够实现数组类型、委托类型和泛型类型参数的隐式引用转换。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="4d9f8-104">协变保留分配兼容性，逆变则与之相反。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>

<span data-ttu-id="4d9f8-105">以下代码演示分配兼容性、协变和逆变之间的差异。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>

```vb
' Assignment compatibility.
Dim str As String = "test"
' An object of a more derived type is assigned to an object of a less derived type.
Dim obj As Object = str

' Covariance.
Dim strings As IEnumerable(Of String) = New List(Of String)()
' An object that is instantiated with a more derived type argument
' is assigned to an object instantiated with a less derived type argument.
' Assignment compatibility is preserved.
Dim objects As IEnumerable(Of Object) = strings

' Contravariance.
' Assume that there is the following method in the class:
' Shared Sub SetObject(ByVal o As Object)
' End Sub
Dim actObject As Action(Of Object) = AddressOf SetObject

' An object that is instantiated with a less derived type argument
' is assigned to an object instantiated with a more derived type argument.
' Assignment compatibility is reversed.
Dim actString As Action(Of String) = actObject
```

<span data-ttu-id="4d9f8-106">数组的协变使派生程度更大的类型的数组能够隐式转换为派生程度更小的类型的数组。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="4d9f8-107">但是此操作不是类型安全的操作，如以下代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-107">But this operation is not type safe, as shown in the following code example.</span></span>

```vb
Dim array() As Object = New String(10) {}
' The following statement produces a run-time exception.
' array(0) = 10
```

<span data-ttu-id="4d9f8-108">对方法组的协变和逆变支持允许将方法签名与委托类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="4d9f8-109">这样，不仅可以将具有匹配签名的方法分配给委托，还可以分配与委托类型指定的派生类型相比，返回派生程度更大的类型的方法（协变）或接受具有派生程度更小的类型的参数的方法（逆变）。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="4d9f8-110">有关详细信息，请参阅[委托中的变体 (Visual Basic)](variance-in-delegates.md) 和[使用委托中的变体 (Visual Basic)](using-variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-110">For more information, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](using-variance-in-delegates.md).</span></span>

<span data-ttu-id="4d9f8-111">以下代码示例演示对方法组的协变和逆变支持。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-111">The following code example shows covariance and contravariance support for method groups.</span></span>

```vb
Shared Function GetObject() As Object
    Return Nothing
End Function

Shared Sub SetObject(ByVal obj As Object)
End Sub

Shared Function GetString() As String
    Return ""
End Function

Shared Sub SetString(ByVal str As String)

End Sub

Shared Sub Test()
    ' Covariance. A delegate specifies a return type as object,
    ' but you can assign a method that returns a string.
    Dim del As Func(Of Object) = AddressOf GetString

    ' Contravariance. A delegate specifies a parameter type as string,
    ' but you can assign a method that takes an object.
    Dim del2 As Action(Of String) = AddressOf SetObject
End Sub
```

<span data-ttu-id="4d9f8-112">在 .NET Framework 4 或更高版本中，Visual Basic 支持泛型接口和委托中的协变和逆变，并允许隐式转换泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-112">In .NET Framework 4 or later, Visual Basic supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="4d9f8-113">有关详细信息，请参阅[泛型接口中的变体 (Visual Basic)](variance-in-generic-interfaces.md) 和[委托中的变体 (Visual Basic)](variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

<span data-ttu-id="4d9f8-114">以下代码示例演示泛型接口的隐式引用转换。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="4d9f8-115">如果泛型接口或委托的泛型参数被声明为协变或逆变，该泛型接口或委托则被称为“变体”。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="4d9f8-116">凭借 Visual Basic，能够创建自己的变体接口和委托。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="4d9f8-117">有关详细信息，请参阅[创建变体泛型接口 (Visual Basic)](creating-variant-generic-interfaces.md) 和[委托中的变体 (Visual Basic)](variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="4d9f8-118">相关主题</span><span class="sxs-lookup"><span data-stu-id="4d9f8-118">Related Topics</span></span>

|<span data-ttu-id="4d9f8-119">Title</span><span class="sxs-lookup"><span data-stu-id="4d9f8-119">Title</span></span>|<span data-ttu-id="4d9f8-120">说明</span><span class="sxs-lookup"><span data-stu-id="4d9f8-120">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="4d9f8-121">泛型接口中的变体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d9f8-121">Variance in Generic Interfaces (Visual Basic)</span></span>](variance-in-generic-interfaces.md)|<span data-ttu-id="4d9f8-122">讨论泛型接口中的协变和逆变，提供 .NET Framework 中的变体泛型接口列表。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|
|[<span data-ttu-id="4d9f8-123">创建变体泛型接口 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d9f8-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](creating-variant-generic-interfaces.md)|<span data-ttu-id="4d9f8-124">演示如何创建自定义变体接口。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-124">Shows how to create custom variant interfaces.</span></span>|
|[<span data-ttu-id="4d9f8-125">在泛型集合的接口中使用变体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d9f8-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="4d9f8-126">演示 <xref:System.Collections.Generic.IEnumerable%601> 接口和 <xref:System.IComparable%601> 接口中对协变和逆变的支持如何帮助重复使用代码。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|
|[<span data-ttu-id="4d9f8-127">委托中的变体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d9f8-127">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)|<span data-ttu-id="4d9f8-128">讨论泛型委托和非泛型委托中的协变和逆变，并提供 .NET Framework 中的变体泛型委托列表。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|
|[<span data-ttu-id="4d9f8-129">使用委托中的变体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d9f8-129">Using Variance in Delegates (Visual Basic)</span></span>](using-variance-in-delegates.md)|<span data-ttu-id="4d9f8-130">演示如何使用非泛型委托中的协变和逆变支持以将方法签名与委托类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|
|[<span data-ttu-id="4d9f8-131">对 Func 和 Action 泛型委托使用变体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d9f8-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="4d9f8-132">演示 `Func` 委托和 `Action` 委托中对协变和逆变的支持如何帮助重复使用代码。</span><span class="sxs-lookup"><span data-stu-id="4d9f8-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
