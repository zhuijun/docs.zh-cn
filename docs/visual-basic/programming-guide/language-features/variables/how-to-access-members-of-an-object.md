---
title: 如何：访问对象的成员
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 2826a3c98b9f19b08cc943d0f67cdd34ac90f526
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410537"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="24490-102">如何：访问对象的成员 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24490-102">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="24490-103">如果对象变量引用某个对象，则通常需要使用该对象的成员，例如其方法、属性、字段和事件。</span><span class="sxs-lookup"><span data-stu-id="24490-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="24490-104">例如，在创建新的 <xref:System.Windows.Forms.Form> 对象后，你可能需要设置其 <xref:System.Windows.Forms.Control.Text%2A> 属性或调用其 <xref:System.Windows.Forms.Control.Focus%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="24490-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="24490-105">访问成员</span><span class="sxs-lookup"><span data-stu-id="24490-105">Accessing Members</span></span>

<span data-ttu-id="24490-106">您可以通过引用对象的变量来访问该对象的成员。</span><span class="sxs-lookup"><span data-stu-id="24490-106">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="24490-107">访问对象的成员</span><span class="sxs-lookup"><span data-stu-id="24490-107">To access members of an object</span></span>

- <span data-ttu-id="24490-108">在 `.` 对象变量名称和成员名称之间使用成员访问运算符（）。</span><span class="sxs-lookup"><span data-stu-id="24490-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="24490-109">如果该成员是[共享](../../../language-reference/modifiers/shared.md)的，则不需要使用变量来访问它。</span><span class="sxs-lookup"><span data-stu-id="24490-109">If the member is [Shared](../../../language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="24490-110">访问已知类型的对象成员</span><span class="sxs-lookup"><span data-stu-id="24490-110">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="24490-111">如果在编译时知道对象的类型，则可以对引用它的变量使用*早期绑定*。</span><span class="sxs-lookup"><span data-stu-id="24490-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="24490-112">访问在编译时知道其类型的对象成员</span><span class="sxs-lookup"><span data-stu-id="24490-112">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="24490-113">将对象变量声明为要分配给变量的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="24490-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="24490-114">使用 `Option Strict On` ，你只能将 <xref:System.Windows.Forms.Form> 对象（或派生自的类型的对象 <xref:System.Windows.Forms.Form> ）分配给 `extraForm` 。</span><span class="sxs-lookup"><span data-stu-id="24490-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="24490-115">如果您已定义了一个使用扩大转换的类或结构 `CType` <xref:System.Windows.Forms.Form> ，则还可以将该类或结构分配给 `extraForm` 。</span><span class="sxs-lookup"><span data-stu-id="24490-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="24490-116">在 `.` 对象变量名称和成员名称之间使用成员访问运算符（）。</span><span class="sxs-lookup"><span data-stu-id="24490-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="24490-117">您可以访问特定于类的所有方法和属性 <xref:System.Windows.Forms.Form> ，无论 `Option Strict` 设置是什么。</span><span class="sxs-lookup"><span data-stu-id="24490-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="24490-118">访问类型未知的对象的成员</span><span class="sxs-lookup"><span data-stu-id="24490-118">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="24490-119">如果在编译时不知道对象的类型，则必须对引用它的任何变量使用*后期绑定*。</span><span class="sxs-lookup"><span data-stu-id="24490-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="24490-120">访问在编译时不知道其类型的对象成员</span><span class="sxs-lookup"><span data-stu-id="24490-120">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="24490-121">将对象变量声明为[对象数据类型](../../../language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="24490-121">Declare the object variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="24490-122">（将变量声明为与 `Object` 将其声明为相同 <xref:System.Object?displayProperty=nameWithType> 。）</span><span class="sxs-lookup"><span data-stu-id="24490-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="24490-123">使用 `Option Strict On` ，你只可以访问在类上定义的成员 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="24490-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="24490-124">在 `.` 对象变量名称和成员名称之间使用成员访问运算符（）。</span><span class="sxs-lookup"><span data-stu-id="24490-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="24490-125">若要能够访问分配给对象变量的任何对象的成员，必须设置 `Option Strict Off` 。</span><span class="sxs-lookup"><span data-stu-id="24490-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="24490-126">当你执行此操作时，编译器无法保证给定成员由分配给变量的对象公开。</span><span class="sxs-lookup"><span data-stu-id="24490-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="24490-127">如果对象未公开尝试访问的成员，则 <xref:System.MemberAccessException> 会出现异常。</span><span class="sxs-lookup"><span data-stu-id="24490-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="24490-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24490-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="24490-129">对象变量</span><span class="sxs-lookup"><span data-stu-id="24490-129">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="24490-130">对象变量声明</span><span class="sxs-lookup"><span data-stu-id="24490-130">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="24490-131">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="24490-131">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="24490-132">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="24490-132">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
