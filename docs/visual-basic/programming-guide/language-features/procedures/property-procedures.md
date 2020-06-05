---
title: Property 过程
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: cb5b0e12512e476b7c96bbfb19f8e4f470f6b498
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363728"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="51c3e-102">Property 过程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51c3e-102">Property Procedures (Visual Basic)</span></span>

<span data-ttu-id="51c3e-103">属性过程是一系列 Visual Basic 语句，这些语句操作模块、类或结构上的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="51c3e-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="51c3e-104">属性过程也称为*属性访问器*。</span><span class="sxs-lookup"><span data-stu-id="51c3e-104">Property procedures are also known as *property accessors*.</span></span>

<span data-ttu-id="51c3e-105">Visual Basic 为以下属性过程提供：</span><span class="sxs-lookup"><span data-stu-id="51c3e-105">Visual Basic provides for the following property procedures:</span></span>

- <span data-ttu-id="51c3e-106">`Get`过程返回属性的值。</span><span class="sxs-lookup"><span data-stu-id="51c3e-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="51c3e-107">当您访问表达式中的属性时，将调用它。</span><span class="sxs-lookup"><span data-stu-id="51c3e-107">It is called when you access the property in an expression.</span></span>
- <span data-ttu-id="51c3e-108">`Set`过程将属性设置为一个值，包括对象引用。</span><span class="sxs-lookup"><span data-stu-id="51c3e-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="51c3e-109">向属性赋值时，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="51c3e-109">It is called when you assign a value to the property.</span></span>

<span data-ttu-id="51c3e-110">通常使用和语句来成对定义属性过程 `Get` `Set` ，但是，如果属性是只读的（[Get 语句](../../../language-reference/statements/get-statement.md)）或只写的（[Set 语句](../../../language-reference/statements/set-statement.md)），则可以单独定义任何一个过程。</span><span class="sxs-lookup"><span data-stu-id="51c3e-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../language-reference/statements/set-statement.md)).</span></span>

<span data-ttu-id="51c3e-111">`Get` `Set` 使用自动实现的属性时，可以忽略和过程。</span><span class="sxs-lookup"><span data-stu-id="51c3e-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="51c3e-112">有关详细信息，请参阅[自动实现的属性](./auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="51c3e-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>

<span data-ttu-id="51c3e-113">可以在类、结构和模块中定义属性。</span><span class="sxs-lookup"><span data-stu-id="51c3e-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="51c3e-114">`Public`默认情况下，属性为，这意味着您可以从应用程序中可访问该属性的容器的任何位置调用它们。</span><span class="sxs-lookup"><span data-stu-id="51c3e-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>

<span data-ttu-id="51c3e-115">有关属性和变量的比较，请参阅[Visual Basic 中属性和变量之间的差异](differences-between-properties-and-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="51c3e-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="51c3e-116">声明语法</span><span class="sxs-lookup"><span data-stu-id="51c3e-116">Declaration syntax</span></span>

<span data-ttu-id="51c3e-117">属性本身由[属性语句](../../../language-reference/statements/property-statement.md)和语句中包含的代码块定义 `End Property` 。</span><span class="sxs-lookup"><span data-stu-id="51c3e-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="51c3e-118">在此块中，每个属性过程显示为包含在声明语句（ `Get` 或 `Set` ）和匹配声明中的内部块 `End` 。</span><span class="sxs-lookup"><span data-stu-id="51c3e-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>

<span data-ttu-id="51c3e-119">声明属性及其过程的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="51c3e-119">The syntax for declaring a property and its procedures is as follows:</span></span>

```vb
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]
    [AccessLevel] Get
        ' Statements of the Get procedure.
        ' The following statement returns an expression as the property's value.
        Return Expression
    End Get
    [AccessLevel] Set[(ByVal NewValue As DataType)]
        ' Statements of the Set procedure.
        ' The following statement assigns newvalue as the property's value.
        LValue = NewValue
    End Set
End Property
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

<span data-ttu-id="51c3e-120">`Modifiers`可以指定有关重载、重写、共享和隐藏的访问级别和信息，以及属性是只读还是只写。</span><span class="sxs-lookup"><span data-stu-id="51c3e-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="51c3e-121">`AccessLevel` `Get` 或过程的可以是 `Set` 比为属性本身指定的访问级别更严格的任何级别。</span><span class="sxs-lookup"><span data-stu-id="51c3e-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="51c3e-122">有关详细信息，请参阅[Property 语句](../../../language-reference/statements/property-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="51c3e-122">For more information, see [Property Statement](../../../language-reference/statements/property-statement.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="51c3e-123">数据类型</span><span class="sxs-lookup"><span data-stu-id="51c3e-123">Data Type</span></span>

<span data-ttu-id="51c3e-124">属性的数据类型和主体访问级别在语句中定义，而不是在 `Property` 属性过程中定义。</span><span class="sxs-lookup"><span data-stu-id="51c3e-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="51c3e-125">属性只能有一种数据类型。</span><span class="sxs-lookup"><span data-stu-id="51c3e-125">A property can have only one data type.</span></span> <span data-ttu-id="51c3e-126">例如，不能定义属性来存储 `Decimal` 值，而是检索 `Double` 值。</span><span class="sxs-lookup"><span data-stu-id="51c3e-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>

### <a name="access-level"></a><span data-ttu-id="51c3e-127">访问级别</span><span class="sxs-lookup"><span data-stu-id="51c3e-127">Access Level</span></span>

<span data-ttu-id="51c3e-128">但是，您可以为属性定义主体访问级别，并在它的某个属性过程中进一步限制访问级别。</span><span class="sxs-lookup"><span data-stu-id="51c3e-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="51c3e-129">例如，可以定义 `Public` 属性，然后定义 `Private Set` 过程。</span><span class="sxs-lookup"><span data-stu-id="51c3e-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="51c3e-130">此 `Get` 过程仍然有效 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="51c3e-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="51c3e-131">只能更改某个属性过程的访问级别，并且只能使其比主体访问级别更严格。</span><span class="sxs-lookup"><span data-stu-id="51c3e-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="51c3e-132">有关详细信息，请参阅[如何：声明具有混合访问级别的属性](how-to-declare-a-property-with-mixed-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="51c3e-132">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="51c3e-133">参数声明</span><span class="sxs-lookup"><span data-stu-id="51c3e-133">Parameter declaration</span></span>

<span data-ttu-id="51c3e-134">声明每个参数的方式与处理[Sub 过程](sub-procedures.md)的方法相同，只不过传递机制必须是 `ByVal` 。</span><span class="sxs-lookup"><span data-stu-id="51c3e-134">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>

<span data-ttu-id="51c3e-135">参数列表中每个参数的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="51c3e-135">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

<span data-ttu-id="51c3e-136">如果该参数是可选的，则还必须提供默认值作为其声明的一部分。</span><span class="sxs-lookup"><span data-stu-id="51c3e-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="51c3e-137">指定默认值的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="51c3e-137">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a><span data-ttu-id="51c3e-138">属性值</span><span class="sxs-lookup"><span data-stu-id="51c3e-138">Property value</span></span>

<span data-ttu-id="51c3e-139">在 `Get` 过程中，返回值作为属性的值提供给调用表达式。</span><span class="sxs-lookup"><span data-stu-id="51c3e-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>

<span data-ttu-id="51c3e-140">在 `Set` 过程中，新属性值将传递给语句的参数 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="51c3e-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="51c3e-141">如果显式声明了某个参数，则必须使用与属性相同的数据类型声明该参数。</span><span class="sxs-lookup"><span data-stu-id="51c3e-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="51c3e-142">如果不声明参数，编译器将使用隐式参数 `Value` 来表示要分配给属性的新值。</span><span class="sxs-lookup"><span data-stu-id="51c3e-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="51c3e-143">调用语法</span><span class="sxs-lookup"><span data-stu-id="51c3e-143">Calling syntax</span></span>

<span data-ttu-id="51c3e-144">通过引用属性，可以隐式调用属性过程。</span><span class="sxs-lookup"><span data-stu-id="51c3e-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="51c3e-145">使用属性的名称的方式与使用变量名称相同，只是必须为所有非可选参数提供值，并且必须将参数列表括在括号中。</span><span class="sxs-lookup"><span data-stu-id="51c3e-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="51c3e-146">如果未提供任何参数，则可以选择省略括号。</span><span class="sxs-lookup"><span data-stu-id="51c3e-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="51c3e-147">隐式调用过程的语法如下所示 `Set` ：</span><span class="sxs-lookup"><span data-stu-id="51c3e-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>

```vb
propertyname[(argumentlist)] = expression
```

<span data-ttu-id="51c3e-148">隐式调用过程的语法如下所示 `Get` ：</span><span class="sxs-lookup"><span data-stu-id="51c3e-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="51c3e-149">声明和调用的插图</span><span class="sxs-lookup"><span data-stu-id="51c3e-149">Illustration of declaration and call</span></span>

<span data-ttu-id="51c3e-150">以下属性将全名存储为两个构成名称：名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="51c3e-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="51c3e-151">在调用代码读取时 `fullName` ，此 `Get` 过程将组合这两个构成名称并返回全名。</span><span class="sxs-lookup"><span data-stu-id="51c3e-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="51c3e-152">当调用代码分配新的全名时，该 `Set` 过程会尝试将其分成两个构成名称。</span><span class="sxs-lookup"><span data-stu-id="51c3e-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="51c3e-153">如果找不到空间，则会将其存储为名字。</span><span class="sxs-lookup"><span data-stu-id="51c3e-153">If it does not find a space, it stores it all as the first name.</span></span>

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

<span data-ttu-id="51c3e-154">下面的示例演示对的属性过程的典型调用 `fullName` ：</span><span class="sxs-lookup"><span data-stu-id="51c3e-154">The following example shows typical calls to the property procedures of `fullName`:</span></span>

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a><span data-ttu-id="51c3e-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51c3e-155">See also</span></span>

- [<span data-ttu-id="51c3e-156">过程</span><span class="sxs-lookup"><span data-stu-id="51c3e-156">Procedures</span></span>](index.md)
- [<span data-ttu-id="51c3e-157">Function 过程</span><span class="sxs-lookup"><span data-stu-id="51c3e-157">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="51c3e-158">运算符过程</span><span class="sxs-lookup"><span data-stu-id="51c3e-158">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="51c3e-159">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="51c3e-159">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="51c3e-160">Visual Basic 中属性和变量的差异</span><span class="sxs-lookup"><span data-stu-id="51c3e-160">Differences Between Properties and Variables in Visual Basic</span></span>](differences-between-properties-and-variables.md)
- [<span data-ttu-id="51c3e-161">如何：创建属性</span><span class="sxs-lookup"><span data-stu-id="51c3e-161">How to: Create a Property</span></span>](how-to-create-a-property.md)
- [<span data-ttu-id="51c3e-162">如何：调用 Property 过程</span><span class="sxs-lookup"><span data-stu-id="51c3e-162">How to: Call a Property Procedure</span></span>](how-to-call-a-property-procedure.md)
- [<span data-ttu-id="51c3e-163">如何：在 Visual Basic 中声明和调用默认属性</span><span class="sxs-lookup"><span data-stu-id="51c3e-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="51c3e-164">如何：在属性中放置值</span><span class="sxs-lookup"><span data-stu-id="51c3e-164">How to: Put a Value in a Property</span></span>](how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="51c3e-165">如何：从属性获取值</span><span class="sxs-lookup"><span data-stu-id="51c3e-165">How to: Get a Value from a Property</span></span>](how-to-get-a-value-from-a-property.md)
