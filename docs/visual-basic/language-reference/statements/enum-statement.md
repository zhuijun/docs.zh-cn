---
title: Enum 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 976cc68d67c69ec86918962ab2dd3406d15aed9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404727"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="efbd9-102">Enum 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efbd9-102">Enum Statement (Visual Basic)</span></span>

<span data-ttu-id="efbd9-103">声明枚举并定义其成员的值。</span><span class="sxs-lookup"><span data-stu-id="efbd9-103">Declares an enumeration and defines the values of its members.</span></span>

## <a name="syntax"></a><span data-ttu-id="efbd9-104">语法</span><span class="sxs-lookup"><span data-stu-id="efbd9-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a><span data-ttu-id="efbd9-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="efbd9-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="efbd9-106">可选。</span><span class="sxs-lookup"><span data-stu-id="efbd9-106">Optional.</span></span> <span data-ttu-id="efbd9-107">应用于此枚举的特性的列表。</span><span class="sxs-lookup"><span data-stu-id="efbd9-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="efbd9-108">必须将[特性列表](attribute-list.md)括在尖括号（" `<` " 和 " `>` "）中。</span><span class="sxs-lookup"><span data-stu-id="efbd9-108">You must enclose the [attribute list](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

  <span data-ttu-id="efbd9-109"><xref:System.FlagsAttribute>特性指示枚举实例的值可以包含多个枚举成员，并且每个成员表示枚举值中的一个位域。</span><span class="sxs-lookup"><span data-stu-id="efbd9-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>

- `accessmodifier`

  <span data-ttu-id="efbd9-110">可选。</span><span class="sxs-lookup"><span data-stu-id="efbd9-110">Optional.</span></span> <span data-ttu-id="efbd9-111">指定哪些代码可以访问此枚举。</span><span class="sxs-lookup"><span data-stu-id="efbd9-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="efbd9-112">可以是以下其中一个值：</span><span class="sxs-lookup"><span data-stu-id="efbd9-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="efbd9-113">公共</span><span class="sxs-lookup"><span data-stu-id="efbd9-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="efbd9-114">避免</span><span class="sxs-lookup"><span data-stu-id="efbd9-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="efbd9-115">友好</span><span class="sxs-lookup"><span data-stu-id="efbd9-115">Friend</span></span>](../modifiers/friend.md)

  - <span data-ttu-id="efbd9-116">专用 </span><span class="sxs-lookup"><span data-stu-id="efbd9-116">[Private](../modifiers/private.md)</span></span>

  - [<span data-ttu-id="efbd9-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="efbd9-117">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="efbd9-118">私有受保护</span><span class="sxs-lookup"><span data-stu-id="efbd9-118">Private Protected</span></span>](../modifiers/private-protected.md)

- `Shadows`

  <span data-ttu-id="efbd9-119">可选。</span><span class="sxs-lookup"><span data-stu-id="efbd9-119">Optional.</span></span> <span data-ttu-id="efbd9-120">指定此枚举重新声明并隐藏基类中具有相同名称的编程元素或重载元素集。</span><span class="sxs-lookup"><span data-stu-id="efbd9-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="efbd9-121">只能为枚举本身指定阴影，而不能在其任何成员上指定[阴影](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="efbd9-121">You can specify [Shadows](../modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>

- `enumerationname`

  <span data-ttu-id="efbd9-122">必需。</span><span class="sxs-lookup"><span data-stu-id="efbd9-122">Required.</span></span> <span data-ttu-id="efbd9-123">枚举的名称。</span><span class="sxs-lookup"><span data-stu-id="efbd9-123">Name of the enumeration.</span></span> <span data-ttu-id="efbd9-124">有关有效名称的信息，请参阅已[声明的元素名称](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="efbd9-124">For information on valid names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `datatype`

  <span data-ttu-id="efbd9-125">可选。</span><span class="sxs-lookup"><span data-stu-id="efbd9-125">Optional.</span></span> <span data-ttu-id="efbd9-126">枚举及其所有成员的数据类型。</span><span class="sxs-lookup"><span data-stu-id="efbd9-126">Data type of the enumeration and all its members.</span></span>

- `memberlist`

  <span data-ttu-id="efbd9-127">必需。</span><span class="sxs-lookup"><span data-stu-id="efbd9-127">Required.</span></span> <span data-ttu-id="efbd9-128">在此语句中声明的成员常量的列表。</span><span class="sxs-lookup"><span data-stu-id="efbd9-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="efbd9-129">多个成员出现在单独的源代码行上。</span><span class="sxs-lookup"><span data-stu-id="efbd9-129">Multiple members appear on individual source code lines.</span></span>

  <span data-ttu-id="efbd9-130">每个 `member` 都具有以下语法和部分：`[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="efbd9-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>

  |<span data-ttu-id="efbd9-131">组成部分</span><span class="sxs-lookup"><span data-stu-id="efbd9-131">Part</span></span>|<span data-ttu-id="efbd9-132">说明</span><span class="sxs-lookup"><span data-stu-id="efbd9-132">Description</span></span>|
  |---|---|
  |`membername`|<span data-ttu-id="efbd9-133">必需。</span><span class="sxs-lookup"><span data-stu-id="efbd9-133">Required.</span></span> <span data-ttu-id="efbd9-134">此成员的名称。</span><span class="sxs-lookup"><span data-stu-id="efbd9-134">Name of this member.</span></span>|
  |`initializer`|<span data-ttu-id="efbd9-135">可选。</span><span class="sxs-lookup"><span data-stu-id="efbd9-135">Optional.</span></span> <span data-ttu-id="efbd9-136">在编译时计算并分配给此成员的表达式。</span><span class="sxs-lookup"><span data-stu-id="efbd9-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|

- <span data-ttu-id="efbd9-137">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="efbd9-137">`End` `Enum`</span></span>

  <span data-ttu-id="efbd9-138">终止 `Enum` 块。</span><span class="sxs-lookup"><span data-stu-id="efbd9-138">Terminates the `Enum` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="efbd9-139">备注</span><span class="sxs-lookup"><span data-stu-id="efbd9-139">Remarks</span></span>

<span data-ttu-id="efbd9-140">如果你有一组在逻辑上彼此相关的不变值，则可以在枚举中将它们一起定义。</span><span class="sxs-lookup"><span data-stu-id="efbd9-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="efbd9-141">这为枚举及其成员提供有意义的名称，这些名称比它们的值更容易记忆。</span><span class="sxs-lookup"><span data-stu-id="efbd9-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="efbd9-142">然后，你可以在代码中的多个位置使用枚举成员。</span><span class="sxs-lookup"><span data-stu-id="efbd9-142">You can then use the enumeration members in many places in your code.</span></span>

<span data-ttu-id="efbd9-143">使用枚举的优点包括：</span><span class="sxs-lookup"><span data-stu-id="efbd9-143">The benefits of using enumerations include the following:</span></span>

- <span data-ttu-id="efbd9-144">减少由转置或错误错误导致的错误。</span><span class="sxs-lookup"><span data-stu-id="efbd9-144">Reduces errors caused by transposing or mistyping numbers.</span></span>

- <span data-ttu-id="efbd9-145">以后可以轻松地更改值。</span><span class="sxs-lookup"><span data-stu-id="efbd9-145">Makes it easy to change values in the future.</span></span>

- <span data-ttu-id="efbd9-146">使代码更易于阅读，这意味着会引入错误的可能性更小。</span><span class="sxs-lookup"><span data-stu-id="efbd9-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>

- <span data-ttu-id="efbd9-147">确保向前兼容性。</span><span class="sxs-lookup"><span data-stu-id="efbd9-147">Ensures forward compatibility.</span></span> <span data-ttu-id="efbd9-148">如果使用枚举，则如果将来有人更改了与成员名称相对应的值，你的代码将不太可能失败。</span><span class="sxs-lookup"><span data-stu-id="efbd9-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>

<span data-ttu-id="efbd9-149">枚举具有名称、基础数据类型和成员集。</span><span class="sxs-lookup"><span data-stu-id="efbd9-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="efbd9-150">每个成员都表示一个常量。</span><span class="sxs-lookup"><span data-stu-id="efbd9-150">Each member represents a constant.</span></span>

<span data-ttu-id="efbd9-151">在类、结构、模块或接口级别（在任何过程之外）声明的枚举是*成员枚举*。</span><span class="sxs-lookup"><span data-stu-id="efbd9-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="efbd9-152">它是声明它的类、结构、模块或接口的成员。</span><span class="sxs-lookup"><span data-stu-id="efbd9-152">It is a member of the class, structure, module, or interface that declares it.</span></span>

<span data-ttu-id="efbd9-153">成员枚举可以从其类、结构、模块或接口中的任何位置进行访问。</span><span class="sxs-lookup"><span data-stu-id="efbd9-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="efbd9-154">类、结构或模块外的代码必须使用该类、结构或模块的名称来限定成员枚举的名称。</span><span class="sxs-lookup"><span data-stu-id="efbd9-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="efbd9-155">您可以通过向源文件添加[Imports](imports-statement-net-namespace-and-type.md)语句来避免使用完全限定的名称。</span><span class="sxs-lookup"><span data-stu-id="efbd9-155">You can avoid the need to use fully qualified names by adding an [Imports](imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>

<span data-ttu-id="efbd9-156">在任何类、结构、模块或接口的命名空间级别声明的枚举是它所显示的命名空间的成员。</span><span class="sxs-lookup"><span data-stu-id="efbd9-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>

<span data-ttu-id="efbd9-157">枚举的*声明上下文*必须是源文件、命名空间、类、结构、模块或接口，不能是过程。</span><span class="sxs-lookup"><span data-stu-id="efbd9-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="efbd9-158">有关详细信息，请参阅[声明上下文和默认访问级别](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="efbd9-158">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="efbd9-159">您可以将属性作为一个整体应用于枚举，而不是单独应用于其成员。</span><span class="sxs-lookup"><span data-stu-id="efbd9-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="efbd9-160">属性将信息提供给程序集的元数据。</span><span class="sxs-lookup"><span data-stu-id="efbd9-160">An attribute contributes information to the assembly's metadata.</span></span>

## <a name="data-type"></a><span data-ttu-id="efbd9-161">数据类型</span><span class="sxs-lookup"><span data-stu-id="efbd9-161">Data Type</span></span>

<span data-ttu-id="efbd9-162">`Enum`语句可以声明枚举的数据类型。</span><span class="sxs-lookup"><span data-stu-id="efbd9-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="efbd9-163">每个成员都采用枚举的数据类型。</span><span class="sxs-lookup"><span data-stu-id="efbd9-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="efbd9-164">可以指定 `Byte` 、、 `Integer` `Long` 、 `SByte` 、、、 `Short` `UInteger` `ULong` 或 `UShort` 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>

<span data-ttu-id="efbd9-165">如果不 `datatype` 为枚举指定，则每个成员都采用其的数据类型 `initializer` 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="efbd9-166">如果同时指定 `datatype` 和 `initializer` ，的数据类型 `initializer` 必须可转换为 `datatype` 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="efbd9-167">如果两者都不 `datatype` `initializer` 存在，则数据类型默认为 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>

## <a name="initializing-members"></a><span data-ttu-id="efbd9-168">初始化成员</span><span class="sxs-lookup"><span data-stu-id="efbd9-168">Initializing Members</span></span>

<span data-ttu-id="efbd9-169">`Enum`语句可初始化中所选成员的内容 `memberlist` 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="efbd9-170">用于 `initializer` 提供要分配给成员的表达式。</span><span class="sxs-lookup"><span data-stu-id="efbd9-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>

<span data-ttu-id="efbd9-171">如果不 `initializer` 为成员指定，Visual Basic 会将其初始化为零（如果它是中的第一个 `member` `memberlist` ），或者将其值指定为大于前面的值 `member` 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>

<span data-ttu-id="efbd9-172">每个中提供的表达式 `initializer` 可以是文本的任意组合、已经定义的其他常数以及已定义的枚举成员（包括此枚举的上一个成员）。</span><span class="sxs-lookup"><span data-stu-id="efbd9-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="efbd9-173">可以使用算术运算符和逻辑运算符来合并此类元素。</span><span class="sxs-lookup"><span data-stu-id="efbd9-173">You can use arithmetic and logical operators to combine such elements.</span></span>

<span data-ttu-id="efbd9-174">不能在中使用变量或函数 `initializer` 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="efbd9-175">但是，可以使用转换关键字 `CByte` ，如和 `CShort` 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="efbd9-176">`AscW`如果使用常量或参数调用该方法，则还可以使用 `String` `Char` ，因为在编译时可对其进行计算。</span><span class="sxs-lookup"><span data-stu-id="efbd9-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

<span data-ttu-id="efbd9-177">枚举的值不能为浮点值。</span><span class="sxs-lookup"><span data-stu-id="efbd9-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="efbd9-178">如果为成员分配浮点值并且 `Option Strict` 将设置为 on，则会发生编译器错误。</span><span class="sxs-lookup"><span data-stu-id="efbd9-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="efbd9-179">如果 `Option Strict` 为 off，则将值自动转换为 `Enum` 类型。</span><span class="sxs-lookup"><span data-stu-id="efbd9-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>

<span data-ttu-id="efbd9-180">如果成员的值超出了基础数据类型允许的范围，或将任何成员初始化为基础数据类型允许的最大值，则编译器将报告错误。</span><span class="sxs-lookup"><span data-stu-id="efbd9-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>

## <a name="modifiers"></a><span data-ttu-id="efbd9-181">修饰符</span><span class="sxs-lookup"><span data-stu-id="efbd9-181">Modifiers</span></span>

<span data-ttu-id="efbd9-182">类、结构、模块和接口成员枚举默认为公共访问。</span><span class="sxs-lookup"><span data-stu-id="efbd9-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="efbd9-183">您可以使用访问修饰符调整其访问级别。</span><span class="sxs-lookup"><span data-stu-id="efbd9-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="efbd9-184">命名空间成员枚举默认为 friend 访问。</span><span class="sxs-lookup"><span data-stu-id="efbd9-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="efbd9-185">可以将其访问级别调整为 "公共"，而不是 "私有" 或 "受保护"。</span><span class="sxs-lookup"><span data-stu-id="efbd9-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="efbd9-186">有关详细信息，请参阅[Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="efbd9-186">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="efbd9-187">所有枚举成员均具有公共访问权限，因此不能对它们使用任何访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="efbd9-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="efbd9-188">但是，如果枚举本身具有限制性更高的访问级别，则将优先使用指定的枚举访问级别。</span><span class="sxs-lookup"><span data-stu-id="efbd9-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>

<span data-ttu-id="efbd9-189">默认情况下，所有枚举都是类型，其字段为常量。</span><span class="sxs-lookup"><span data-stu-id="efbd9-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="efbd9-190">因此 `Shared` ， `Static` `ReadOnly` 在声明枚举或其成员时，不能使用、和关键字。</span><span class="sxs-lookup"><span data-stu-id="efbd9-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>

## <a name="assigning-multiple-values"></a><span data-ttu-id="efbd9-191">分配多个值</span><span class="sxs-lookup"><span data-stu-id="efbd9-191">Assigning Multiple Values</span></span>

<span data-ttu-id="efbd9-192">枚举通常表示互斥的值。</span><span class="sxs-lookup"><span data-stu-id="efbd9-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="efbd9-193">通过 <xref:System.FlagsAttribute> 在声明中包含特性 `Enum` ，可以将多个值分配给枚举的实例。</span><span class="sxs-lookup"><span data-stu-id="efbd9-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="efbd9-194"><xref:System.FlagsAttribute>特性指定将枚举视为位域（即一组标志）。</span><span class="sxs-lookup"><span data-stu-id="efbd9-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="efbd9-195">它们称为*按位*枚举。</span><span class="sxs-lookup"><span data-stu-id="efbd9-195">These are called *bitwise* enumerations.</span></span>

<span data-ttu-id="efbd9-196">使用属性声明枚举时 <xref:System.FlagsAttribute> ，我们建议你使用2的幂，即1、2、4、8、16等值作为值。</span><span class="sxs-lookup"><span data-stu-id="efbd9-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="efbd9-197">我们还建议将 "无" 作为值为0的成员的名称。</span><span class="sxs-lookup"><span data-stu-id="efbd9-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="efbd9-198">有关其他指南，请参阅 <xref:System.FlagsAttribute> 和 <xref:System.Enum> 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>

## <a name="example"></a><span data-ttu-id="efbd9-199">示例</span><span class="sxs-lookup"><span data-stu-id="efbd9-199">Example</span></span>

<span data-ttu-id="efbd9-200">下面的示例演示如何使用 `Enum` 语句。</span><span class="sxs-lookup"><span data-stu-id="efbd9-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="efbd9-201">请注意，成员称为 `EggSizeEnum.Medium` ，而不是 `Medium` 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a><span data-ttu-id="efbd9-202">示例</span><span class="sxs-lookup"><span data-stu-id="efbd9-202">Example</span></span>

<span data-ttu-id="efbd9-203">下面的示例中的方法在类的外部 `Egg` 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="efbd9-204">因此， `EggSizeEnum` 完全限定为 `Egg.EggSizeEnum` 。</span><span class="sxs-lookup"><span data-stu-id="efbd9-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a><span data-ttu-id="efbd9-205">示例</span><span class="sxs-lookup"><span data-stu-id="efbd9-205">Example</span></span>

<span data-ttu-id="efbd9-206">下面的示例使用 `Enum` 语句来定义一组相关的命名常量值。</span><span class="sxs-lookup"><span data-stu-id="efbd9-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="efbd9-207">在这种情况下，值是可以选择为数据库设计数据输入窗体的颜色。</span><span class="sxs-lookup"><span data-stu-id="efbd9-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a><span data-ttu-id="efbd9-208">示例</span><span class="sxs-lookup"><span data-stu-id="efbd9-208">Example</span></span>

<span data-ttu-id="efbd9-209">下面的示例显示了包含正负数的值。</span><span class="sxs-lookup"><span data-stu-id="efbd9-209">The following example shows values that include both positive and negative numbers.</span></span>

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a><span data-ttu-id="efbd9-210">示例</span><span class="sxs-lookup"><span data-stu-id="efbd9-210">Example</span></span>

<span data-ttu-id="efbd9-211">在下面的示例中， `As` 子句用于指定 `datatype` 枚举的。</span><span class="sxs-lookup"><span data-stu-id="efbd9-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a><span data-ttu-id="efbd9-212">示例</span><span class="sxs-lookup"><span data-stu-id="efbd9-212">Example</span></span>

<span data-ttu-id="efbd9-213">下面的示例演示如何使用按位枚举。</span><span class="sxs-lookup"><span data-stu-id="efbd9-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="efbd9-214">可以将多个值分配给位枚举的实例。</span><span class="sxs-lookup"><span data-stu-id="efbd9-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="efbd9-215">`Enum`声明包含 <xref:System.FlagsAttribute> 特性，该特性指示可将枚举视为一组标志。</span><span class="sxs-lookup"><span data-stu-id="efbd9-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a><span data-ttu-id="efbd9-216">示例</span><span class="sxs-lookup"><span data-stu-id="efbd9-216">Example</span></span>

<span data-ttu-id="efbd9-217">下面的示例循环访问枚举。</span><span class="sxs-lookup"><span data-stu-id="efbd9-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="efbd9-218">它使用 <xref:System.Enum.GetNames%2A> 方法从枚举中检索成员名称的数组，并 <xref:System.Enum.GetValues%2A> 检索成员值的数组。</span><span class="sxs-lookup"><span data-stu-id="efbd9-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="efbd9-219">另请参阅</span><span class="sxs-lookup"><span data-stu-id="efbd9-219">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="efbd9-220">Const 语句</span><span class="sxs-lookup"><span data-stu-id="efbd9-220">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="efbd9-221">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="efbd9-221">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="efbd9-222">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="efbd9-222">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="efbd9-223">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="efbd9-223">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="efbd9-224">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="efbd9-224">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
