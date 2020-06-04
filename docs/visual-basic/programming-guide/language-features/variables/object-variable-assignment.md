---
title: 对象变量赋值
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: 9ae1a307e8c886166d516140b7f100a411cedcfa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410369"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="10f75-102">对象变量赋值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10f75-102">Object Variable Assignment (Visual Basic)</span></span>

<span data-ttu-id="10f75-103">使用常规赋值语句将对象分配给对象变量。</span><span class="sxs-lookup"><span data-stu-id="10f75-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="10f75-104">可以分配对象表达式或[Nothing](../../../language-reference/nothing.md)关键字，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="10f75-104">You can assign an object expression or the [Nothing](../../../language-reference/nothing.md) keyword, as the following example illustrates.</span></span>

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

<span data-ttu-id="10f75-105">`Nothing`表示当前没有对象分配给该变量。</span><span class="sxs-lookup"><span data-stu-id="10f75-105">`Nothing` means there is no object currently assigned to the variable.</span></span>

## <a name="initialization"></a><span data-ttu-id="10f75-106">初始化</span><span class="sxs-lookup"><span data-stu-id="10f75-106">Initialization</span></span>

<span data-ttu-id="10f75-107">当你的代码开始运行时，你的对象变量将初始化为 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="10f75-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="10f75-108">其声明包含初始化的将重新初始化为在执行声明语句时指定的值。</span><span class="sxs-lookup"><span data-stu-id="10f75-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>

<span data-ttu-id="10f75-109">可以通过使用[New](../../../language-reference/operators/new-operator.md)关键字在声明中包含初始化。</span><span class="sxs-lookup"><span data-stu-id="10f75-109">You can include initialization in your declaration by using the [New](../../../language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="10f75-110">以下声明语句声明对象变量 `testUri` 并 `ver` 为其分配特定的对象。</span><span class="sxs-lookup"><span data-stu-id="10f75-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="10f75-111">每个都使用适当类的重载构造函数之一来初始化对象。</span><span class="sxs-lookup"><span data-stu-id="10f75-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a><span data-ttu-id="10f75-112">Disassociation</span><span class="sxs-lookup"><span data-stu-id="10f75-112">Disassociation</span></span>

<span data-ttu-id="10f75-113">设置对象变量以使 `Nothing` 变量与任何特定对象的关联停止。</span><span class="sxs-lookup"><span data-stu-id="10f75-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="10f75-114">这样可以防止意外更改变量来更改对象。</span><span class="sxs-lookup"><span data-stu-id="10f75-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="10f75-115">它还允许您测试对象变量是否指向有效对象，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="10f75-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

<span data-ttu-id="10f75-116">如果变量所引用的对象在另一应用程序中，则此测试无法确定该应用程序是否已终止或只是使该对象无效。</span><span class="sxs-lookup"><span data-stu-id="10f75-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>

<span data-ttu-id="10f75-117">值为的对象变量 `Nothing` 也称为*空引用*。</span><span class="sxs-lookup"><span data-stu-id="10f75-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>

## <a name="current-instance"></a><span data-ttu-id="10f75-118">当前实例</span><span class="sxs-lookup"><span data-stu-id="10f75-118">Current Instance</span></span>

<span data-ttu-id="10f75-119">对象的*当前实例*是当前正在执行代码的实例。</span><span class="sxs-lookup"><span data-stu-id="10f75-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="10f75-120">由于所有代码都在过程中执行，因此当前实例是在其中调用过程的实例。</span><span class="sxs-lookup"><span data-stu-id="10f75-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>

<span data-ttu-id="10f75-121">`Me`关键字充当引用当前实例的对象变量。</span><span class="sxs-lookup"><span data-stu-id="10f75-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="10f75-122">如果过程不是[共享](../../../language-reference/modifiers/shared.md)的，它可以使用 `Me` 关键字获取指向当前实例的指针。</span><span class="sxs-lookup"><span data-stu-id="10f75-122">If a procedure is not [Shared](../../../language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="10f75-123">共享过程不能与类的特定实例相关联。</span><span class="sxs-lookup"><span data-stu-id="10f75-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>

<span data-ttu-id="10f75-124">使用 `Me` 对于将当前实例传递到另一个模块中的过程特别有用。</span><span class="sxs-lookup"><span data-stu-id="10f75-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="10f75-125">例如，假设您有多个 XML 文档，并且想要将一些标准文本添加到其中。</span><span class="sxs-lookup"><span data-stu-id="10f75-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="10f75-126">下面的示例定义了用于执行此操作的过程。</span><span class="sxs-lookup"><span data-stu-id="10f75-126">The following example defines a procedure to do this.</span></span>

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

<span data-ttu-id="10f75-127">然后，每个 XML 文档对象都可以调用该过程，并将其当前实例作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="10f75-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="10f75-128">下面的示例对这种情况进行了演示。</span><span class="sxs-lookup"><span data-stu-id="10f75-128">The following example demonstrates this.</span></span>

```vb
addStandardText(Me)
```

## <a name="see-also"></a><span data-ttu-id="10f75-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10f75-129">See also</span></span>

- [<span data-ttu-id="10f75-130">对象变量</span><span class="sxs-lookup"><span data-stu-id="10f75-130">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="10f75-131">对象变量声明</span><span class="sxs-lookup"><span data-stu-id="10f75-131">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="10f75-132">对象变量值</span><span class="sxs-lookup"><span data-stu-id="10f75-132">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="10f75-133">如何：在 Visual Basic 中声明对象变量并为它分配对象</span><span class="sxs-lookup"><span data-stu-id="10f75-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="10f75-134">如何：使对象变量不引用任何实例</span><span class="sxs-lookup"><span data-stu-id="10f75-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="10f75-135">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="10f75-135">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
