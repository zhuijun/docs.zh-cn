---
title: 使用属性 - C# 编程指南
description: 这些示例演示如何使用 C# 中的属性。 了解 get 和 set 访问器如何实现读取和写入访问，并了解属性的用法。
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: 51ca0a37022c99bfbd9d61f2cc47f529d535e72a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864652"
---
# <a name="using-properties-c-programming-guide"></a><span data-ttu-id="c6c2a-104">使用属性（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="c6c2a-104">Using Properties (C# Programming Guide)</span></span>

<span data-ttu-id="c6c2a-105">属性结合了字段和方法的多个方面。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-105">Properties combine aspects of both fields and methods.</span></span> <span data-ttu-id="c6c2a-106">对于对象的用户来说，属性似乎是一个字段，访问属性需要相同的语法。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-106">To the user of an object, a property appears to be a field, accessing the property requires the same syntax.</span></span> <span data-ttu-id="c6c2a-107">对于类的实现者来说，属性是一两个代码块，表示 [get](../../language-reference/keywords/get.md) 访问器和/或 [set](../../language-reference/keywords/set.md) 访问器。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-107">To the implementer of a class, a property is one or two code blocks, representing a [get](../../language-reference/keywords/get.md) accessor and/or a [set](../../language-reference/keywords/set.md) accessor.</span></span> <span data-ttu-id="c6c2a-108">读取属性时，执行 `get` 访问器的代码块；向属性赋予新值时，执行 `set` 访问器的代码块。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-108">The code block for the `get` accessor is executed when the property is read; the code block for the `set` accessor is executed when the property is assigned a new value.</span></span> <span data-ttu-id="c6c2a-109">将不带 `set` 访问器的属性视为只读。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-109">A property without a `set` accessor is considered read-only.</span></span> <span data-ttu-id="c6c2a-110">将不带 `get` 访问器的属性视为只写。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-110">A property without a `get` accessor is considered write-only.</span></span> <span data-ttu-id="c6c2a-111">将具有以上两个访问器的属性视为读写。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-111">A property that has both accessors is read-write.</span></span>

<span data-ttu-id="c6c2a-112">与字段不同，属性不会被归类为变量。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-112">Unlike fields, properties are not classified as variables.</span></span> <span data-ttu-id="c6c2a-113">因此，不能将属性作为 [ref](../../language-reference/keywords/ref.md) 或 [out](../../language-reference/keywords/out-parameter-modifier.md) 参数传递。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-113">Therefore, you cannot pass a property as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>

<span data-ttu-id="c6c2a-114">属性具有许多用途：它们可以先验证数据，再允许进行更改；可以在类上透明地公开数据，其中数据实际是从某个其他源（如数据库）检索到的；可以在数据发生更改时采取措施，例如引发事件或更改其他字段的值。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-114">Properties have many uses: they can validate data before allowing a change; they can transparently expose data on a class where that data is actually retrieved from some other source, such as a database; they can take an action when data is changed, such as raising an event, or changing the value of other fields.</span></span>

<span data-ttu-id="c6c2a-115">通过依次指定字段的访问级别、属性类型、属性名、声明 `get` 访问器和/或 `set` 访问器的代码块，在类块中声明属性。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-115">Properties are declared in the class block by specifying the access level of the field, followed by the type of the property, followed by the name of the property, and followed by a code block that declares a `get`-accessor and/or a `set` accessor.</span></span> <span data-ttu-id="c6c2a-116">例如：</span><span class="sxs-lookup"><span data-stu-id="c6c2a-116">For example:</span></span>

[!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]

<span data-ttu-id="c6c2a-117">此示例中将 `Month` 声明为属性，以便 `set` 访问器可确保 `Month` 值设置在 1 至 12 之间。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-117">In this example, `Month` is declared as a property so that the `set` accessor can make sure that the `Month` value is set between 1 and 12.</span></span> <span data-ttu-id="c6c2a-118">`Month` 属性使用私有字段跟踪实际值。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-118">The `Month` property uses a private field to track the actual value.</span></span> <span data-ttu-id="c6c2a-119">属性的数据的实际位置通常被称为属性的“后备存储”。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-119">The real location of a property's data is often referred to as the property's "backing store."</span></span> <span data-ttu-id="c6c2a-120">属性使用私有字段作为后备存储，这很常见。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-120">It is common for properties to use private fields as a backing store.</span></span> <span data-ttu-id="c6c2a-121">将字段被标记为私有，确保只能通过调用属性来对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-121">The field is marked private in order to make sure that it can only be changed by calling the property.</span></span> <span data-ttu-id="c6c2a-122">有关公共和专用访问限制的详细信息，请参阅[访问修饰符](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-122">For more information about public and private access restrictions, see [Access Modifiers](./access-modifiers.md).</span></span>

<span data-ttu-id="c6c2a-123">自动实现的属性为简单属性声明提供简化的语法。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-123">Auto-implemented properties provide simplified syntax for simple property declarations.</span></span> <span data-ttu-id="c6c2a-124">有关详细信息，请参阅[自动实现的属性](auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-124">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>

## <a name="the-get-accessor"></a><span data-ttu-id="c6c2a-125">get 访问器</span><span class="sxs-lookup"><span data-stu-id="c6c2a-125">The get Accessor</span></span>

<span data-ttu-id="c6c2a-126">`get` 访问器的正文类似于方法。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-126">The body of the `get` accessor resembles that of a method.</span></span> <span data-ttu-id="c6c2a-127">它必须返回属性类型的值。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-127">It must return a value of the property type.</span></span> <span data-ttu-id="c6c2a-128">执行 `get` 访问器等效于读取字段的值。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-128">The execution of the `get` accessor is equivalent to reading the value of the field.</span></span> <span data-ttu-id="c6c2a-129">例如，在从 `get` 访问器返回私有变量且已启用优化时，对 `get` 访问器方法的调用由编译器内联，因此不存在方法调用开销。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-129">For example, when you are returning the private variable from the `get` accessor and optimizations are enabled, the call to the `get` accessor method is inlined by the compiler so there is no method-call overhead.</span></span> <span data-ttu-id="c6c2a-130">但是，无法内联虚拟 `get` 访问器方法，因为编译器在编译时不知道在运行时实际可调用哪些方法。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-130">However, a virtual `get` accessor method cannot be inlined because the compiler does not know at compile-time which method may actually be called at run time.</span></span> <span data-ttu-id="c6c2a-131">以下是一个 `get` 访问器，它返回私有字段 `_name` 的值：</span><span class="sxs-lookup"><span data-stu-id="c6c2a-131">The following is a `get` accessor that returns the value of a private field `_name`:</span></span>

[!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]

<span data-ttu-id="c6c2a-132">引用属性时，除了作为赋值目标外，还调用 `get` 访问器读取属性值。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-132">When you reference the property, except as the target of an assignment, the `get` accessor is invoked to read the value of the property.</span></span> <span data-ttu-id="c6c2a-133">例如：</span><span class="sxs-lookup"><span data-stu-id="c6c2a-133">For example:</span></span>

[!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]

<span data-ttu-id="c6c2a-134">`get` 访问器必须以 [return](../../language-reference/keywords/return.md) 或 [throw](../../language-reference/keywords/throw.md) 语句结尾，且控件不能超出访问器正文。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-134">The `get` accessor must end in a [return](../../language-reference/keywords/return.md) or [throw](../../language-reference/keywords/throw.md) statement, and control cannot flow off the accessor body.</span></span>

<span data-ttu-id="c6c2a-135">使用 `get` 访问器更改对象的状态是一种糟糕的编程风格。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-135">It is a bad programming style to change the state of the object by using the `get` accessor.</span></span> <span data-ttu-id="c6c2a-136">例如，以下访问器将产生在每次访问 `_number` 字段时更改对象状态的副作用。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-136">For example, the following accessor produces the side effect of changing the state of the object every time that the `_number` field is accessed.</span></span>

[!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]

<span data-ttu-id="c6c2a-137">`get` 访问器可以用于返回字段值或计算并返回字段值。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-137">The `get` accessor can be used to return the field value or to compute it and return it.</span></span> <span data-ttu-id="c6c2a-138">例如：</span><span class="sxs-lookup"><span data-stu-id="c6c2a-138">For example:</span></span>

[!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]

<span data-ttu-id="c6c2a-139">在上一个代码段中，如果不给 `Name` 属性赋值，它将返回值 `NA`。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-139">In the previous code segment, if you do not assign a value to the `Name` property, it will return the value `NA`.</span></span>

## <a name="the-set-accessor"></a><span data-ttu-id="c6c2a-140">set 访问器</span><span class="sxs-lookup"><span data-stu-id="c6c2a-140">The set Accessor</span></span>

<span data-ttu-id="c6c2a-141">`set` 访问器类似于返回类型为 [void](../../language-reference/builtin-types/void.md) 的方法。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-141">The `set` accessor resembles a method whose return type is [void](../../language-reference/builtin-types/void.md).</span></span> <span data-ttu-id="c6c2a-142">它使用名为 `value` 的隐式参数，该参数的类型为属性的类型。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-142">It uses an implicit parameter called `value`, whose type is the type of the property.</span></span> <span data-ttu-id="c6c2a-143">在下面的示例中，将 `set` 访问器添加到 `Name` 属性：</span><span class="sxs-lookup"><span data-stu-id="c6c2a-143">In the following example, a `set` accessor is added to the `Name` property:</span></span>

[!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]

<span data-ttu-id="c6c2a-144">向属性赋值时，通过使用提供新值的自变量调用 `set` 访问器。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-144">When you assign a value to the property, the `set` accessor is invoked by using an argument that provides the new value.</span></span> <span data-ttu-id="c6c2a-145">例如：</span><span class="sxs-lookup"><span data-stu-id="c6c2a-145">For example:</span></span>

[!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]

<span data-ttu-id="c6c2a-146">为 `set` 访问器中的本地变量声明使用隐式参数名 `value` 是错误的。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-146">It is an error to use the implicit parameter name, `value`, for a local variable declaration in a `set` accessor.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6c2a-147">备注</span><span class="sxs-lookup"><span data-stu-id="c6c2a-147">Remarks</span></span>

<span data-ttu-id="c6c2a-148">可以将属性标记为 `public`、`private`、`protected`、`internal`、`protected internal` 或 `private protected`。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-148">Properties can be marked as `public`, `private`, `protected`, `internal`, `protected internal` or `private protected`.</span></span> <span data-ttu-id="c6c2a-149">这些访问修饰符定义该类的用户访问该属性的方式。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-149">These access modifiers define how users of the class can access the property.</span></span> <span data-ttu-id="c6c2a-150">相同属性的 `get` 和 `set` 访问器可以具有不同的访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-150">The `get` and `set` accessors for the same property may have different access modifiers.</span></span> <span data-ttu-id="c6c2a-151">例如，`get` 可能为 `public`允许从类型外部进行只读访问；而 `set` 可能为 `private` 或 `protected`。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-151">For example, the `get` may be `public` to allow read-only access from outside the type, and the `set` may be `private` or `protected`.</span></span> <span data-ttu-id="c6c2a-152">有关详细信息，请参阅[访问修饰符](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-152">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>

<span data-ttu-id="c6c2a-153">可以通过使用 `static` 关键字将属性声明为静态属性。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-153">A property may be declared as a static property by using the `static` keyword.</span></span> <span data-ttu-id="c6c2a-154">这使属性可供调用方在任何时候使用，即使不存在类的任何实例。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-154">This makes the property available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="c6c2a-155">有关详细信息，请参阅[静态类和静态类成员](./static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-155">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="c6c2a-156">可以通过使用 [virtual](../../language-reference/keywords/virtual.md) 关键字将属性标记为虚拟属性。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-156">A property may be marked as a virtual property by using the [virtual](../../language-reference/keywords/virtual.md) keyword.</span></span> <span data-ttu-id="c6c2a-157">这可使派生类使用 [override](../../language-reference/keywords/override.md) 关键字重写属性行为。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-157">This enables derived classes to override the property behavior by using the [override](../../language-reference/keywords/override.md) keyword.</span></span> <span data-ttu-id="c6c2a-158">有关这些选项的详细信息，请参阅[继承](inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-158">For more information about these options, see [Inheritance](inheritance.md).</span></span>

<span data-ttu-id="c6c2a-159">重写虚拟属性的属性也可以是 [sealed](../../language-reference/keywords/sealed.md)，指定对于派生类，它不再是虚拟的。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-159">A property overriding a virtual property can also be [sealed](../../language-reference/keywords/sealed.md), specifying that for derived classes it is no longer virtual.</span></span> <span data-ttu-id="c6c2a-160">最后，可以将属性声明为 [abstract](../../language-reference/keywords/abstract.md)。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-160">Lastly, a property can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="c6c2a-161">这意味着类中没有实现，派生类必须写入自己的实现。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-161">This means that there is no implementation in the class, and derived classes must write their own implementation.</span></span> <span data-ttu-id="c6c2a-162">有关这些选项的详细信息，请参阅[抽象类、密封类及类成员](abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-162">For more information about these options, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c6c2a-163">在 [static](../../language-reference/keywords/static.md) 属性的访问器上使用 [virtual](../../language-reference/keywords/virtual.md)、[abstract](../../language-reference/keywords/abstract.md) 或 [override](../../language-reference/keywords/override.md) 修饰符是错误的。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-163">It is an error to use a [virtual](../../language-reference/keywords/virtual.md), [abstract](../../language-reference/keywords/abstract.md), or [override](../../language-reference/keywords/override.md) modifier on an accessor of a [static](../../language-reference/keywords/static.md) property.</span></span>

## <a name="example"></a><span data-ttu-id="c6c2a-164">示例</span><span class="sxs-lookup"><span data-stu-id="c6c2a-164">Example</span></span>

<span data-ttu-id="c6c2a-165">此示例演示实例、静态和只读属性。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-165">This example demonstrates instance, static, and read-only properties.</span></span> <span data-ttu-id="c6c2a-166">它接收通过键盘键入的员工姓名，按 1 递增 `NumberOfEmployees`，并显示员工姓名和编号。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-166">It accepts the name of the employee from the keyboard, increments `NumberOfEmployees` by 1, and displays the Employee name and number.</span></span>

[!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]

## <a name="example"></a><span data-ttu-id="c6c2a-167">示例</span><span class="sxs-lookup"><span data-stu-id="c6c2a-167">Example</span></span>

<span data-ttu-id="c6c2a-168">此示例演示如何访问由派生类中同名的另一属性隐藏的基类中的属性：</span><span class="sxs-lookup"><span data-stu-id="c6c2a-168">This example demonstrates how to access a property in a base class that is hidden by another property that has the same name in a derived class:</span></span>

[!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]

<span data-ttu-id="c6c2a-169">以下内容是前一示例中的要点：</span><span class="sxs-lookup"><span data-stu-id="c6c2a-169">The following are important points in the previous example:</span></span>

- <span data-ttu-id="c6c2a-170">派生类中的属性 `Name` 隐藏基类中的属性 `Name`。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-170">The property `Name` in the derived class hides the property `Name` in the base class.</span></span> <span data-ttu-id="c6c2a-171">在这种情况下，`new` 修饰符用于派生类的属性声明中：</span><span class="sxs-lookup"><span data-stu-id="c6c2a-171">In such a case, the `new` modifier is used in the declaration of the property in the derived class:</span></span>

     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  

- <span data-ttu-id="c6c2a-172">`(Employee)` 转换用于访问基类中的隐藏属性：</span><span class="sxs-lookup"><span data-stu-id="c6c2a-172">The cast `(Employee)` is used to access the hidden property in the base class:</span></span>

     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]

     <span data-ttu-id="c6c2a-173">有关隐藏成员的详细信息，请参阅 [new 修饰符](../../language-reference/keywords/new-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-173">For more information about hiding members, see the [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>

## <a name="example"></a><span data-ttu-id="c6c2a-174">示例</span><span class="sxs-lookup"><span data-stu-id="c6c2a-174">Example</span></span>

<span data-ttu-id="c6c2a-175">在此示例中，两个类（`Cube` 和 `Square`）实现抽象类 `Shape`，并重写其抽象 `Area` 属性。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-175">In this example, two classes, `Cube` and `Square`, implement an abstract class, `Shape`, and override its abstract `Area` property.</span></span> <span data-ttu-id="c6c2a-176">请注意属性上的 [override](../../language-reference/keywords/override.md) 修饰符的使用。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-176">Note the use of the [override](../../language-reference/keywords/override.md) modifier on the properties.</span></span> <span data-ttu-id="c6c2a-177">程序接受将边长作为输入，计算正方形和立方体的面积。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-177">The program accepts the side as an input and calculates the areas for the square and cube.</span></span> <span data-ttu-id="c6c2a-178">它还接受将面积作为输入，计算正方形和立方体的相应边长。</span><span class="sxs-lookup"><span data-stu-id="c6c2a-178">It also accepts the area as an input and calculates the corresponding side for the square and cube.</span></span>

[!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]

## <a name="see-also"></a><span data-ttu-id="c6c2a-179">请参阅</span><span class="sxs-lookup"><span data-stu-id="c6c2a-179">See also</span></span>

- [<span data-ttu-id="c6c2a-180">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="c6c2a-180">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c6c2a-181">属性</span><span class="sxs-lookup"><span data-stu-id="c6c2a-181">Properties</span></span>](properties.md)
- [<span data-ttu-id="c6c2a-182">接口属性</span><span class="sxs-lookup"><span data-stu-id="c6c2a-182">Interface Properties</span></span>](interface-properties.md)
- [<span data-ttu-id="c6c2a-183">自动实现的属性</span><span class="sxs-lookup"><span data-stu-id="c6c2a-183">Auto-Implemented Properties</span></span>](auto-implemented-properties.md)
