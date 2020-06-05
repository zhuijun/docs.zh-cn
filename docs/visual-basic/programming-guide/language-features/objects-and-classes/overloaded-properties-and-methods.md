---
title: 重载属性和方法
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: 1672f12773ece012c580253b6dafbf9d0ac8f07c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389147"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="9c8ff-102">重载属性和方法（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="9c8ff-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="9c8ff-103">重载是在具有相同名称但参数类型不同的类中创建多个过程、实例构造函数或属性。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="9c8ff-104">重载用法</span><span class="sxs-lookup"><span data-stu-id="9c8ff-104">Overloading usage</span></span>

<span data-ttu-id="9c8ff-105">当对象模型要求对不同数据类型进行操作的过程使用相同的名称时，重载特别有用。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="9c8ff-106">例如，可以显示几种不同数据类型的类可以具有如下所 `Display` 示的过程：</span><span class="sxs-lookup"><span data-stu-id="9c8ff-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="9c8ff-107">如果没有重载，则需要为每个过程创建不同的名称，即使它们执行相同的操作，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c8ff-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="9c8ff-108">重载使您可以更轻松地使用属性或方法，因为它提供了可使用的数据类型选择。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="9c8ff-109">例如， `Display` 先前讨论的重载方法可通过以下代码行调用：</span><span class="sxs-lookup"><span data-stu-id="9c8ff-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="9c8ff-110">在运行时，Visual Basic 会根据你指定的参数的数据类型调用正确过程。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="9c8ff-111">重载规则</span><span class="sxs-lookup"><span data-stu-id="9c8ff-111">Overloading rules</span></span>

 <span data-ttu-id="9c8ff-112">通过添加两个或多个具有相同名称的属性或方法，可以为类创建重载成员。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="9c8ff-113">除重载的派生成员以外，每个重载成员都必须具有不同的参数列表，并且在重载属性或过程时，不能将以下各项用作区分功能：</span><span class="sxs-lookup"><span data-stu-id="9c8ff-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="9c8ff-114">`ByVal` `ByRef` 应用于成员的修饰符（如或）或成员的参数。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="9c8ff-115">参数的名称</span><span class="sxs-lookup"><span data-stu-id="9c8ff-115">Names of parameters</span></span>

- <span data-ttu-id="9c8ff-116">过程的返回类型</span><span class="sxs-lookup"><span data-stu-id="9c8ff-116">Return types of procedures</span></span>

<span data-ttu-id="9c8ff-117">`Overloads`当重载时，关键字是可选的，但是，如果任何重载成员使用 `Overloads` 关键字，则所有其他具有相同名称的重载成员也必须指定此关键字。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="9c8ff-118">派生类可以重载具有相同参数和参数类型的成员的继承成员，这一过程称为*按名称和签名进行隐藏*。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="9c8ff-119">如果在 `Overloads` 按名称和签名进行隐藏时使用关键字，则将使用该成员的派生类的实现，而不是基类中的实现，并且该成员的所有其他重载将可用于派生类的实例。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="9c8ff-120">如果 `Overloads` 在使用具有相同参数和参数类型的成员重载继承成员时省略关键字，则会将重载称为*按名称隐藏*。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="9c8ff-121">按名称隐藏将替换成员的继承实现，并使所有其他重载不可用于派生类及其 decedents 的实例。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="9c8ff-122">`Overloads`和 `Shadows` 修饰符不能同时用于相同的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="9c8ff-123">示例</span><span class="sxs-lookup"><span data-stu-id="9c8ff-123">Example</span></span>

<span data-ttu-id="9c8ff-124">下面的示例创建了重载方法，这些方法 `String` 接受 `Decimal` 美元量的或表示形式，并返回包含销售税的字符串。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="9c8ff-125">使用此示例创建重载方法</span><span class="sxs-lookup"><span data-stu-id="9c8ff-125">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="9c8ff-126">打开一个新的项目并添加一个名为的类 `TaxClass` 。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-126">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="9c8ff-127">将以下代码添加到 `TaxClass` 类。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-127">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="9c8ff-128">将以下过程添加到窗体。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-128">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="9c8ff-129">向窗体添加一个按钮，并 `ShowTax` 从按钮的事件调用过程 `Button1_Click` 。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="9c8ff-130">运行项目，并单击窗体上的按钮以测试重载 `ShowTax` 过程。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="9c8ff-131">在运行时，编译器选择与所使用的参数匹配的适当重载函数。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="9c8ff-132">单击该按钮时，将首先调用重载的方法，该方法的 `Price` 参数为字符串，而 "Price" 是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="9c8ff-133">税率为 $5.12 "。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="9c8ff-134">`TaxAmount``Decimal`在第二次和消息 "Price 为十进制值" 的情况下调用。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="9c8ff-135">税率为 $5.12 "。</span><span class="sxs-lookup"><span data-stu-id="9c8ff-135">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c8ff-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c8ff-136">See also</span></span>

- [<span data-ttu-id="9c8ff-137">对象和类</span><span class="sxs-lookup"><span data-stu-id="9c8ff-137">Objects and Classes</span></span>](index.md)
- [<span data-ttu-id="9c8ff-138">Visual Basic 中的隐藏</span><span class="sxs-lookup"><span data-stu-id="9c8ff-138">Shadowing in Visual Basic</span></span>](../declared-elements/shadowing.md)
- [<span data-ttu-id="9c8ff-139">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="9c8ff-139">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="9c8ff-140">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="9c8ff-140">Inheritance Basics</span></span>](inheritance-basics.md)
- [<span data-ttu-id="9c8ff-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="9c8ff-141">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="9c8ff-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="9c8ff-142">ByVal</span></span>](../../../language-reference/modifiers/byval.md)
- [<span data-ttu-id="9c8ff-143">RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="9c8ff-143">ByRef</span></span>](../../../language-reference/modifiers/byref.md)
- [<span data-ttu-id="9c8ff-144">重载</span><span class="sxs-lookup"><span data-stu-id="9c8ff-144">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="9c8ff-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="9c8ff-145">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
