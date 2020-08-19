---
title: 记录
description: '了解 F # 记录如何表示命名值的简单聚合，还可以选择包含成员。'
ms.date: 08/15/2020
ms.openlocfilehash: 182b2e83c3940c866197052af102787a96e49c54
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559045"
---
# <a name="records"></a><span data-ttu-id="1ac5e-103">记录</span><span class="sxs-lookup"><span data-stu-id="1ac5e-103">Records</span></span>

<span data-ttu-id="1ac5e-104">记录表示已命名值的简单聚合，可选择包含成员。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-104">Records represent simple aggregates of named values, optionally with members.</span></span> <span data-ttu-id="1ac5e-105">它们可以是结构或引用类型。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-105">They can either be structs or reference types.</span></span>  <span data-ttu-id="1ac5e-106">默认情况下，它们是引用类型。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ac5e-107">语法</span><span class="sxs-lookup"><span data-stu-id="1ac5e-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="1ac5e-108">备注</span><span class="sxs-lookup"><span data-stu-id="1ac5e-108">Remarks</span></span>

<span data-ttu-id="1ac5e-109">在前面的语法中， *typename* 是记录类型的名称， *label1* 和 *label2* 是值的名称（称为 *标签*）， *type1* 和 *type2* 是这些值的类型。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="1ac5e-110">*成员列表* 是此类型的成员的可选列表。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="1ac5e-111">您可以使用 `[<Struct>]` 属性来创建结构记录，而不是引用类型的记录。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="1ac5e-112">下面是一些示例。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-112">Following are some examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="1ac5e-113">每个标签都在单独的行上时，分号是可选的。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="1ac5e-114">您可以在称为 *记录表达式*的表达式中设置值。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="1ac5e-115">如果标签与其他记录类型) 的 (完全不同，则编译器将从使用的标签推断类型。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="1ac5e-116">大括号 ( {} ) 将记录表达式括起来。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="1ac5e-117">下面的代码演示了一个记录表达式，该表达式使用带有标签、和的三个 float 元素初始化记录 `x` `y` `z` 。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="1ac5e-118">如果有另一种类型也具有相同标签，请不要使用缩写形式。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="1ac5e-119">最近声明的类型的标签优先于以前声明的类型的标签，因此在前面的示例中， `mypoint3D` 将推断为 `Point3D` 。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="1ac5e-120">可以显式指定记录类型，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="1ac5e-121">与类类型一样，可以为记录类型定义方法。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="1ac5e-122">使用记录表达式创建记录</span><span class="sxs-lookup"><span data-stu-id="1ac5e-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="1ac5e-123">您可以通过使用记录中定义的标签来初始化记录。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="1ac5e-124">这样做的表达式称为 " *记录表达式*"。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="1ac5e-125">使用大括号将记录表达式括起来，并使用分号作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="1ac5e-126">下面的示例演示如何创建记录。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="1ac5e-127">记录表达式和类型定义中最后一个字段后面的分号是可选的，不管这些字段是否都在同一行中。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="1ac5e-128">创建记录时，必须为每个字段提供值。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="1ac5e-129">不能引用任何字段的初始化表达式中其他字段的值。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="1ac5e-130">在下面的代码中，的类型 `myRecord2` 是从字段的名称推断出来的。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="1ac5e-131">还可以选择显式指定类型名称。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="1ac5e-132">当必须复制现有记录，并且可能更改某些字段值时，另一种形式的记录构造会很有用。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="1ac5e-133">下面的代码行阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="1ac5e-134">这种形式的记录表达式称为 " *复制和更新记录表达式*"。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="1ac5e-135">记录在默认情况下是不可变的;不过，您可以使用复制和更新表达式轻松创建修改后的记录。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="1ac5e-136">还可以显式指定可变字段。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="1ac5e-137">不要将 DefaultValue 属性用于记录字段。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="1ac5e-138">更好的方法是使用初始化为默认值的字段定义记录的默认实例，然后使用复制和更新记录表达式来设置不同于默认值的任何字段。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="creating-mutually-recursive-records"></a><span data-ttu-id="1ac5e-139">创建相互递归记录</span><span class="sxs-lookup"><span data-stu-id="1ac5e-139">Creating Mutually Recursive Records</span></span>

<span data-ttu-id="1ac5e-140">在创建记录时，可能需要让它依赖于以后要定义的另一种类型。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-140">Sometime when creating a record, you may want to have it depend on another type that you would like to define afterwards.</span></span> <span data-ttu-id="1ac5e-141">这是一种编译错误，除非你将记录类型定义为 "互相递归"。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-141">This is a compile error unless you define the record types to be mutually recursive.</span></span>

<span data-ttu-id="1ac5e-142">定义相互递归的记录是通过关键字来完成的 `and` 。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-142">Defining mutually recursive records is done with the `and` keyword.</span></span> <span data-ttu-id="1ac5e-143">这使你可以将两个或更多个记录类型链接在一起。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-143">This lets you link 2 or more record types together.</span></span>

<span data-ttu-id="1ac5e-144">例如，下面的代码将 `Person` 和类型定义 `Address` 为互相递归：</span><span class="sxs-lookup"><span data-stu-id="1ac5e-144">For example, the following code defines a `Person` and `Address` type as mutually recursive:</span></span>

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string
    Occupant: Person }
```

<span data-ttu-id="1ac5e-145">如果要定义前面的示例而不包含 `and` 关键字，则不会进行编译。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-145">If you were to define the previous example without the `and` keyword, then it would not compile.</span></span> <span data-ttu-id="1ac5e-146">`and`对于相互递归定义，关键字是必需的。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-146">The `and` keyword is required for mutually recursive definitions.</span></span>

## <a name="pattern-matching-with-records"></a><span data-ttu-id="1ac5e-147">与记录匹配的模式</span><span class="sxs-lookup"><span data-stu-id="1ac5e-147">Pattern Matching with Records</span></span>

<span data-ttu-id="1ac5e-148">记录可以与模式匹配一起使用。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-148">Records can be used with pattern matching.</span></span> <span data-ttu-id="1ac5e-149">可以显式指定某些字段，并为其他字段提供在发生匹配时将分配的变量。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-149">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="1ac5e-150">下面的代码示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-150">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="1ac5e-151">此代码的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-151">The output of this code is as follows.</span></span>

```console
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="records-and-members"></a><span data-ttu-id="1ac5e-152">记录和成员</span><span class="sxs-lookup"><span data-stu-id="1ac5e-152">Records and members</span></span>

<span data-ttu-id="1ac5e-153">您可以在记录上指定成员，这一点与类的处理方式相同。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-153">You can specify members on records much like you can with classes.</span></span> <span data-ttu-id="1ac5e-154">不支持字段。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-154">There is no support for fields.</span></span> <span data-ttu-id="1ac5e-155">常见的方法是定义一个 `Default` 静态成员以便于构建简单的记录：</span><span class="sxs-lookup"><span data-stu-id="1ac5e-155">A common approach is to define a `Default` static member for easy record construction:</span></span>

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    static member Default =
        { Name = "Phillip"
          Age = 12
          Address = "123 happy fun street" }

let defaultPerson = Person.Default
```

<span data-ttu-id="1ac5e-156">如果使用自我标识符，则该标识符引用其成员被调用的记录的实例：</span><span class="sxs-lookup"><span data-stu-id="1ac5e-156">If you use a self identifier, that identifier refers to the instance of the record whose member is called:</span></span>

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    member this.WeirdToString() =
        this.Name + this.Address + string this.Age

let p = { Name = "a"; Age = 12; Address = "abc123 }
let weirdString = p.WeirdToString()
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="1ac5e-157">记录和类之间的差异</span><span class="sxs-lookup"><span data-stu-id="1ac5e-157">Differences Between Records and Classes</span></span>

<span data-ttu-id="1ac5e-158">记录字段与类的不同之处在于，它们会自动作为属性公开，并在创建和复制记录时使用。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-158">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="1ac5e-159">记录构造也不同于类构造。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-159">Record construction also differs from class construction.</span></span> <span data-ttu-id="1ac5e-160">在记录类型中，不能定义构造函数。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-160">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="1ac5e-161">相反，本主题中介绍的构造语法适用。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-161">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="1ac5e-162">类在构造函数参数、字段和属性之间没有直接关系。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-162">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="1ac5e-163">与联合和结构类型一样，记录具有结构相等性语义。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-163">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="1ac5e-164">类具有引用相等性语义。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-164">Classes have reference equality semantics.</span></span> <span data-ttu-id="1ac5e-165">下面的代码示例展示了此操作。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-165">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="1ac5e-166">此代码的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="1ac5e-166">The output of this code is as follows:</span></span>

```console
The records are equal.
```

<span data-ttu-id="1ac5e-167">如果你用类编写相同的代码，则两个类对象将不相等，因为这两个值将表示堆上的两个对象，并且仅 (比较地址，除非类类型重写 `System.Object.Equals`) 的方法。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-167">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="1ac5e-168">如果需要记录的引用相等性，请在 `[<ReferenceEquality>]` 记录上方添加属性。</span><span class="sxs-lookup"><span data-stu-id="1ac5e-168">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ac5e-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ac5e-169">See also</span></span>

- [<span data-ttu-id="1ac5e-170">F# 类型</span><span class="sxs-lookup"><span data-stu-id="1ac5e-170">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="1ac5e-171">类</span><span class="sxs-lookup"><span data-stu-id="1ac5e-171">Classes</span></span>](classes.md)
- [<span data-ttu-id="1ac5e-172">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="1ac5e-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1ac5e-173">引用相等</span><span class="sxs-lookup"><span data-stu-id="1ac5e-173">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [<span data-ttu-id="1ac5e-174">模式匹配</span><span class="sxs-lookup"><span data-stu-id="1ac5e-174">Pattern Matching</span></span>](pattern-matching.md)
