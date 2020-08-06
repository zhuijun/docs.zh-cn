---
title: 强制转换和类型转换 - C# 编程指南
description: 了解强制转换和类型转换，例如隐式、显式（强制转换）和用户定义的转换。
ms.date: 07/06/2020
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 040b5679b1e6666a7f0308e5990781a2ef86c530
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381952"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a><span data-ttu-id="4be33-103">强制转换和类型转换（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="4be33-103">Casting and type conversions (C# Programming Guide)</span></span>

<span data-ttu-id="4be33-104">由于 C# 是在编译时静态类型化的，因此变量在声明后就无法再次声明，或无法分配另一种类型的值，除非该类型可以隐式转换为变量的类型。</span><span class="sxs-lookup"><span data-stu-id="4be33-104">Because C# is statically-typed at compile time, after a variable is declared, it cannot be declared again or assigned a value of another type unless that type is implicitly convertible to the variable's type.</span></span> <span data-ttu-id="4be33-105">例如，`string` 无法隐式转换为 `int`。</span><span class="sxs-lookup"><span data-stu-id="4be33-105">For example, the `string` cannot be implicitly converted to `int`.</span></span> <span data-ttu-id="4be33-106">因此，在将 `i` 声明为 `int` 后，无法将字符串“Hello”分配给它，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="4be33-106">Therefore, after you declare `i` as an `int`, you cannot assign the string "Hello" to it, as the following code shows:</span></span>

```csharp
int i;

// error CS0029: Cannot implicitly convert type 'string' to 'int'
i = "Hello";
```

<span data-ttu-id="4be33-107">但有时可能需要将值复制到其他类型的变量或方法参数中。</span><span class="sxs-lookup"><span data-stu-id="4be33-107">However, you might sometimes need to copy a value into a variable or method parameter of another type.</span></span> <span data-ttu-id="4be33-108">例如，可能需要将一个整数变量传递给参数类型化为 `double` 的方法。</span><span class="sxs-lookup"><span data-stu-id="4be33-108">For example, you might have an integer variable that you need to pass to a method whose parameter is typed as `double`.</span></span> <span data-ttu-id="4be33-109">或者可能需要将类变量分配给接口类型的变量。</span><span class="sxs-lookup"><span data-stu-id="4be33-109">Or you might need to assign a class variable to a variable of an interface type.</span></span> <span data-ttu-id="4be33-110">这些类型的操作称为类型转换。</span><span class="sxs-lookup"><span data-stu-id="4be33-110">These kinds of operations are called *type conversions*.</span></span> <span data-ttu-id="4be33-111">在 C# 中，可以执行以下几种类型的转换：</span><span class="sxs-lookup"><span data-stu-id="4be33-111">In C#, you can perform the following kinds of conversions:</span></span>

- <span data-ttu-id="4be33-112">**隐式转换**：由于这种转换始终会成功且不会导致数据丢失，因此无需使用任何特殊语法。</span><span class="sxs-lookup"><span data-stu-id="4be33-112">**Implicit conversions**: No special syntax is required because the conversion always succeeds and no data will be lost.</span></span> <span data-ttu-id="4be33-113">示例包括从较小整数类型到较大整数类型的转换以及从派生类到基类的转换。</span><span class="sxs-lookup"><span data-stu-id="4be33-113">Examples include conversions from smaller to larger integral types, and conversions from derived classes to base classes.</span></span>

- <span data-ttu-id="4be33-114">**显式转换（强制转换）** ：必须使用[强制转换表达式](../../language-reference/operators/type-testing-and-cast.md#cast-expression)，才能执行显式转换。</span><span class="sxs-lookup"><span data-stu-id="4be33-114">**Explicit conversions (casts)**: Explicit conversions require a [cast expression](../../language-reference/operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="4be33-115">在转换中可能丢失信息时或在出于其他原因转换可能不成功时，必须进行强制转换。</span><span class="sxs-lookup"><span data-stu-id="4be33-115">Casting is required when information might be lost in the conversion, or when the conversion might not succeed for other reasons.</span></span> <span data-ttu-id="4be33-116">典型的示例包括从数值到精度较低或范围较小的类型的转换和从基类实例到派生类的转换。</span><span class="sxs-lookup"><span data-stu-id="4be33-116">Typical examples include numeric conversion to a type that has less precision or a smaller range, and conversion of a base-class instance to a derived class.</span></span>

- <span data-ttu-id="4be33-117">**用户定义的转换**：用户定义的转换是使用特殊方法执行，这些方法可定义为在没有基类和派生类关系的自定义类型之间启用显式转换和隐式转换。</span><span class="sxs-lookup"><span data-stu-id="4be33-117">**User-defined conversions**: User-defined conversions are performed by special methods that you can define to enable explicit and implicit conversions between custom types that do not have a base class–derived class relationship.</span></span> <span data-ttu-id="4be33-118">有关详细信息，请参阅[用户定义转换运算符](../../language-reference/operators/user-defined-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="4be33-118">For more information, see [User-defined conversion operators](../../language-reference/operators/user-defined-conversion-operators.md).</span></span>

- <span data-ttu-id="4be33-119">**使用帮助程序类进行转换**：若要在非兼容类型（如整数和 <xref:System.DateTime?displayProperty=nameWithType> 对象，或十六进制字符串和字节数组）之间转换，可使用 <xref:System.BitConverter?displayProperty=nameWithType> 类、<xref:System.Convert?displayProperty=nameWithType> 类和内置数值类型的 `Parse` 方法（如 <xref:System.Int32.Parse%2A?displayProperty=nameWithType>）。</span><span class="sxs-lookup"><span data-stu-id="4be33-119">**Conversions with helper classes**: To convert between non-compatible types, such as integers and <xref:System.DateTime?displayProperty=nameWithType> objects, or hexadecimal strings and byte arrays, you can use the <xref:System.BitConverter?displayProperty=nameWithType> class, the <xref:System.Convert?displayProperty=nameWithType> class, and the `Parse` methods of the built-in numeric types, such as <xref:System.Int32.Parse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4be33-120">有关详细信息，请参见[如何将字节数组转换为 int](./how-to-convert-a-byte-array-to-an-int.md)、[如何将字符串转换为数字](./how-to-convert-a-string-to-a-number.md)和[如何在十六进制字符串与数值类型之间转换](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4be33-120">For more information, see [How to convert a byte array to an int](./how-to-convert-a-byte-array-to-an-int.md), [How to convert a string to a number](./how-to-convert-a-string-to-a-number.md), and [How to convert between hexadecimal strings and numeric types](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span></span>

## <a name="implicit-conversions"></a><span data-ttu-id="4be33-121">隐式转换</span><span class="sxs-lookup"><span data-stu-id="4be33-121">Implicit conversions</span></span>

<span data-ttu-id="4be33-122">对于内置数值类型，如果要存储的值无需截断或四舍五入即可适应变量，则可以进行隐式转换。</span><span class="sxs-lookup"><span data-stu-id="4be33-122">For built-in numeric types, an implicit conversion can be made when the value to be stored can fit into the variable without being truncated or rounded off.</span></span> <span data-ttu-id="4be33-123">对于整型类型，这意味着源类型的范围是目标类型范围的正确子集。</span><span class="sxs-lookup"><span data-stu-id="4be33-123">For integral types, this means the range of the source type is a proper subset of the range for the target type.</span></span> <span data-ttu-id="4be33-124">例如，[long](../../language-reference/builtin-types/integral-numeric-types.md) 类型的变量（64 位整数）能够存储 [int](../../language-reference/builtin-types/integral-numeric-types.md)（32 位整数）可存储的任何值。</span><span class="sxs-lookup"><span data-stu-id="4be33-124">For example, a variable of type [long](../../language-reference/builtin-types/integral-numeric-types.md) (64-bit integer) can store any value that an [int](../../language-reference/builtin-types/integral-numeric-types.md) (32-bit integer) can store.</span></span> <span data-ttu-id="4be33-125">在下面的示例中，编译器先将右侧的 `num` 值隐式转换为 `long` 类型，再将它赋给 `bigNum`。</span><span class="sxs-lookup"><span data-stu-id="4be33-125">In the following example, the compiler implicitly converts the value of `num` on the right to a type `long` before assigning it to `bigNum`.</span></span>

[!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]

<span data-ttu-id="4be33-126">有关所有隐式数值转换的完整列表，请参阅[内置数值转换](../../language-reference/builtin-types/numeric-conversions.md)一文的[隐式数值转换表](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions)部分。</span><span class="sxs-lookup"><span data-stu-id="4be33-126">For a complete list of all implicit numeric conversions, see the [Implicit numeric conversions](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions) section of the [Built-in numeric conversions](../../language-reference/builtin-types/numeric-conversions.md) article.</span></span>

<span data-ttu-id="4be33-127">对于引用类型，隐式转换始终存在于从一个类转换为该类的任何一个直接或间接的基类或接口的情况。</span><span class="sxs-lookup"><span data-stu-id="4be33-127">For reference types, an implicit conversion always exists from a class to any one of its direct or indirect base classes or interfaces.</span></span> <span data-ttu-id="4be33-128">由于派生类始终包含基类的所有成员，因此不必使用任何特殊语法。</span><span class="sxs-lookup"><span data-stu-id="4be33-128">No special syntax is necessary because a derived class always contains all the members of a base class.</span></span>

```csharp
Derived d = new Derived();

// Always OK.
Base b = d;
```

## <a name="explicit-conversions"></a><span data-ttu-id="4be33-129">显式转换</span><span class="sxs-lookup"><span data-stu-id="4be33-129">Explicit conversions</span></span>

<span data-ttu-id="4be33-130">但是，如果进行转换可能会导致信息丢失，则编译器会要求执行显式转换，显式转换也称为强制转换。</span><span class="sxs-lookup"><span data-stu-id="4be33-130">However, if a conversion cannot be made without a risk of losing information, the compiler requires that you perform an explicit conversion, which is called a *cast*.</span></span> <span data-ttu-id="4be33-131">强制转换是显式告知编译器以下信息的一种方式：你打算进行转换且你知道可能会发生数据丢失，或者你知道强制转换有可能在运行时失败。</span><span class="sxs-lookup"><span data-stu-id="4be33-131">A cast is a way of explicitly informing the compiler that you intend to make the conversion and that you are aware that data loss might occur, or the cast may fail at runtime.</span></span> <span data-ttu-id="4be33-132">若要执行强制转换，请在要转换的值或变量前面的括号中指定要强制转换到的类型。</span><span class="sxs-lookup"><span data-stu-id="4be33-132">To perform a cast, specify the type that you are casting to in parentheses in front of the value or variable to be converted.</span></span> <span data-ttu-id="4be33-133">下面的程序将 [double](../../language-reference/builtin-types/floating-point-numeric-types.md) 强制转换为 [int](../../language-reference/builtin-types/integral-numeric-types.md)。如不强制转换则该程序不会进行编译。</span><span class="sxs-lookup"><span data-stu-id="4be33-133">The following program casts a [double](../../language-reference/builtin-types/floating-point-numeric-types.md) to an [int](../../language-reference/builtin-types/integral-numeric-types.md). The program will not compile without the cast.</span></span>

[!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]

<span data-ttu-id="4be33-134">有关支持的显式数值转换的完整列表，请参阅[内置数值转换](../../language-reference/builtin-types/numeric-conversions.md)一文的[显式数值转换](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions)部分。</span><span class="sxs-lookup"><span data-stu-id="4be33-134">For a complete list of supported explicit numeric conversions, see the [Explicit numeric conversions](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) section of the [Built-in numeric conversions](../../language-reference/builtin-types/numeric-conversions.md) article.</span></span>

<span data-ttu-id="4be33-135">对于引用类型，如果需要从基类型转换为派生类型，则必须进行显式强制转换：</span><span class="sxs-lookup"><span data-stu-id="4be33-135">For reference types, an explicit cast is required if you need to convert from a base type to a derived type:</span></span>

```csharp
// Create a new derived type.
Giraffe g = new Giraffe();

// Implicit conversion to base type is safe.
Animal a = g;

// Explicit conversion is required to cast back
// to derived type. Note: This will compile but will
// throw an exception at run time if the right-side
// object is not in fact a Giraffe.
Giraffe g2 = (Giraffe)a;
```

<span data-ttu-id="4be33-136">引用类型之间的强制转换操作不会更改基础对象的运行时类型；它只更改用作对该对象引用的值的类型。</span><span class="sxs-lookup"><span data-stu-id="4be33-136">A cast operation between reference types does not change the run-time type of the underlying object; it only changes the type of the value that is being used as a reference to that object.</span></span> <span data-ttu-id="4be33-137">有关详细信息，请参阅[多态性](../classes-and-structs/polymorphism.md)。</span><span class="sxs-lookup"><span data-stu-id="4be33-137">For more information, see [Polymorphism](../classes-and-structs/polymorphism.md).</span></span>

## <a name="type-conversion-exceptions-at-run-time"></a><span data-ttu-id="4be33-138">运行时的类型转换异常</span><span class="sxs-lookup"><span data-stu-id="4be33-138">Type conversion exceptions at run time</span></span>

<span data-ttu-id="4be33-139">在某些引用类型转换中，编译器无法确定强制转换是否会有效。</span><span class="sxs-lookup"><span data-stu-id="4be33-139">In some reference type conversions, the compiler cannot determine whether a cast will be valid.</span></span> <span data-ttu-id="4be33-140">正确进行编译的强制转换操作有可能在运行时失败。</span><span class="sxs-lookup"><span data-stu-id="4be33-140">It is possible for a cast operation that compiles correctly to fail at run time.</span></span> <span data-ttu-id="4be33-141">如下面的示例所示，类型转换在运行时失败将导致引发 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="4be33-141">As shown in the following example, a type cast that fails at run time will cause an <xref:System.InvalidCastException> to be thrown.</span></span>

[!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]

<span data-ttu-id="4be33-142">`Test` 方法有一个 `Animal` 形式参数，因此，将实际参数 `a` 显式强制转换为 `Reptile` 会造成危险的假设。</span><span class="sxs-lookup"><span data-stu-id="4be33-142">The `Test` method has an `Animal` parameter, thus explicitly casting the argument `a` to a `Reptile` makes a dangerous assumption.</span></span> <span data-ttu-id="4be33-143">更安全的做法是不要做出假设，而是检查类型。</span><span class="sxs-lookup"><span data-stu-id="4be33-143">It is safer to not make assumptions, but rather check the type.</span></span> <span data-ttu-id="4be33-144">C# 提供 [is](../../language-reference/operators/type-testing-and-cast.md#is-operator) 运算符，使你可以在实际执行强制转换之前测试兼容性。</span><span class="sxs-lookup"><span data-stu-id="4be33-144">C# provides the [is](../../language-reference/operators/type-testing-and-cast.md#is-operator) operator to enable you to test for compatibility before actually performing a cast.</span></span> <span data-ttu-id="4be33-145">有关详细信息，请参阅[如何使用模式匹配以及 as 和 is 运算符安全地进行强制转换](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="4be33-145">For more information, see [How to safely cast using pattern matching and the as and is operators](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4be33-146">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="4be33-146">C# language specification</span></span>

<span data-ttu-id="4be33-147">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[转换](~/_csharplang/spec/conversions.md)部分。</span><span class="sxs-lookup"><span data-stu-id="4be33-147">For more information, see the [Conversions](~/_csharplang/spec/conversions.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4be33-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="4be33-148">See also</span></span>

- [<span data-ttu-id="4be33-149">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="4be33-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4be33-150">类型</span><span class="sxs-lookup"><span data-stu-id="4be33-150">Types</span></span>](./index.md)
- [<span data-ttu-id="4be33-151">强制转换表达式</span><span class="sxs-lookup"><span data-stu-id="4be33-151">Cast expression</span></span>](../../language-reference/operators/type-testing-and-cast.md#cast-expression)
- [<span data-ttu-id="4be33-152">用户定义转换运算符</span><span class="sxs-lookup"><span data-stu-id="4be33-152">User-defined conversion operators</span></span>](../../language-reference/operators/user-defined-conversion-operators.md)
- <span data-ttu-id="4be33-153">[通用类型转换](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="4be33-153">[Generalized Type Conversion](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))</span></span>
- [<span data-ttu-id="4be33-154">如何将字符串转换为数字</span><span class="sxs-lookup"><span data-stu-id="4be33-154">How to convert a string to a number</span></span>](./how-to-convert-a-string-to-a-number.md)
