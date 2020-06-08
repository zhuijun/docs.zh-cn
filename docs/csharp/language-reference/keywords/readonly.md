---
title: readonly 关键字 - C# 参考
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 66a096e8831f72a2216e8ba5dd9866046504624f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368616"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="6480a-102">readonly（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="6480a-102">readonly (C# Reference)</span></span>

<span data-ttu-id="6480a-103">`readonly` 关键字是一个可在四个上下文中使用的修饰符：</span><span class="sxs-lookup"><span data-stu-id="6480a-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="6480a-104">在[字段声明](#readonly-field-example)中，`readonly` 指示只能在声明期间或在同一个类的构造函数中向字段赋值。</span><span class="sxs-lookup"><span data-stu-id="6480a-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="6480a-105">可以在字段声明和构造函数中多次分配和重新分配只读字段。</span><span class="sxs-lookup"><span data-stu-id="6480a-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="6480a-106">构造函数退出后，不能分配 `readonly` 字段。</span><span class="sxs-lookup"><span data-stu-id="6480a-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="6480a-107">此规则对于值类型和引用类型具有不同的含义：</span><span class="sxs-lookup"><span data-stu-id="6480a-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="6480a-108">由于值类型直接包含数据，因此属于 `readonly` 值类型的字段不可变。</span><span class="sxs-lookup"><span data-stu-id="6480a-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="6480a-109">由于引用类型包含对其数据的引用，因此属于 `readonly` 引用类型的字段必须始终引用同一对象。</span><span class="sxs-lookup"><span data-stu-id="6480a-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="6480a-110">该对象是可变的。</span><span class="sxs-lookup"><span data-stu-id="6480a-110">That object isn't immutable.</span></span> <span data-ttu-id="6480a-111">`readonly` 修饰符可防止字段替换为引用类型的其他实例。</span><span class="sxs-lookup"><span data-stu-id="6480a-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="6480a-112">但是，修饰符不会阻止通过只读字段修改字段的实例数据。</span><span class="sxs-lookup"><span data-stu-id="6480a-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="6480a-113">包含属于可变引用类型的外部可见只读字段的外部可见类型可能存在安全漏洞，可能会触发警告 [CA2104](/visualstudio/code-quality/ca2104)：“不要声明只读可变引用类型。”</span><span class="sxs-lookup"><span data-stu-id="6480a-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="6480a-114">在 `readonly struct` 类型定义中，`readonly` 指示结构类型是不可变的。</span><span class="sxs-lookup"><span data-stu-id="6480a-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="6480a-115">有关详细信息，请参阅[结构类型](../builtin-types/struct.md)一文中的 [`readonly` 结构](../builtin-types/struct.md#readonly-struct)一节。</span><span class="sxs-lookup"><span data-stu-id="6480a-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="6480a-116">在结构类型内的实例成员声明中，`readonly` 指示实例成员不修改结构的状态。</span><span class="sxs-lookup"><span data-stu-id="6480a-116">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="6480a-117">有关详细信息，请参阅[结构类型](../builtin-types/struct.md)一文中的 [`readonly` 实例成员](../builtin-types/struct.md#readonly-instance-members)部分。</span><span class="sxs-lookup"><span data-stu-id="6480a-117">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="6480a-118">在 [`ref readonly` 方法返回](#ref-readonly-return-example)中，`readonly` 修饰符指示该方法返回一个引用，且不允许向该引用写入内容。</span><span class="sxs-lookup"><span data-stu-id="6480a-118">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="6480a-119">在 C# 7.2 中添加了 `readonly struct` 和 `ref readonly` 上下文。</span><span class="sxs-lookup"><span data-stu-id="6480a-119">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="6480a-120">在 C# 8.0 中添加了 `readonly` 结构成员</span><span class="sxs-lookup"><span data-stu-id="6480a-120">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="6480a-121">Readonly 字段示例</span><span class="sxs-lookup"><span data-stu-id="6480a-121">Readonly field example</span></span>

<span data-ttu-id="6480a-122">在此示例中，即使在类构造函数中给字段 `year` 赋了值，也无法在方法 `ChangeYear` 中更改其值：</span><span class="sxs-lookup"><span data-stu-id="6480a-122">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="6480a-123">只能在下列上下文中对 `readonly` 字段进行赋值：</span><span class="sxs-lookup"><span data-stu-id="6480a-123">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="6480a-124">在声明中初始化变量时，例如：</span><span class="sxs-lookup"><span data-stu-id="6480a-124">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="6480a-125">在包含实例字段声明的类的实例构造函数中。</span><span class="sxs-lookup"><span data-stu-id="6480a-125">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="6480a-126">在包含静态字段声明的类的静态构造函数中。</span><span class="sxs-lookup"><span data-stu-id="6480a-126">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="6480a-127">只有在这些构造函数上下文中，将 `readonly` 字段作为 [out](out-parameter-modifier.md) 或 [ref](ref.md) 参数传递才有效。</span><span class="sxs-lookup"><span data-stu-id="6480a-127">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="6480a-128">`readonly` 关键字不同于 [const](const.md) 关键字。</span><span class="sxs-lookup"><span data-stu-id="6480a-128">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="6480a-129">`const` 字段只能在该字段的声明中初始化。</span><span class="sxs-lookup"><span data-stu-id="6480a-129">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="6480a-130">可以在字段声明和任何构造函数中多次分配 `readonly` 字段。</span><span class="sxs-lookup"><span data-stu-id="6480a-130">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="6480a-131">因此，根据所使用的构造函数，`readonly` 字段可能具有不同的值。</span><span class="sxs-lookup"><span data-stu-id="6480a-131">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="6480a-132">另外，虽然 `const` 字段是编译时常量，但 `readonly` 字段可用于运行时常量，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="6480a-132">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="6480a-133">在前面的示例中，如果使用类似以下示例的语句：</span><span class="sxs-lookup"><span data-stu-id="6480a-133">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="6480a-134">你将收到编译器错误消息：</span><span class="sxs-lookup"><span data-stu-id="6480a-134">you'll get the compiler error message:</span></span>

<span data-ttu-id="6480a-135">**无法对只读的字段赋值（构造函数或变量初始值指定项中除外）**</span><span class="sxs-lookup"><span data-stu-id="6480a-135">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="6480a-136">Ref readonly 返回示例</span><span class="sxs-lookup"><span data-stu-id="6480a-136">Ref readonly return example</span></span>

<span data-ttu-id="6480a-137">`ref return` 上的 `readonly` 修饰符指示返回的引用无法修改。</span><span class="sxs-lookup"><span data-stu-id="6480a-137">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="6480a-138">下面的示例返回了一个对来源的引用。</span><span class="sxs-lookup"><span data-stu-id="6480a-138">The following example returns a reference to the origin.</span></span> <span data-ttu-id="6480a-139">它使用 `readonly` 修饰符来指示调用方无法修改来源：</span><span class="sxs-lookup"><span data-stu-id="6480a-139">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="6480a-140">所返回的类型不需要为 `readonly struct`。</span><span class="sxs-lookup"><span data-stu-id="6480a-140">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="6480a-141">`ref` 能返回的任何类型都能由 `ref readonly` 返回。</span><span class="sxs-lookup"><span data-stu-id="6480a-141">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6480a-142">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="6480a-142">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="6480a-143">你还可查看语言规范建议：</span><span class="sxs-lookup"><span data-stu-id="6480a-143">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="6480a-144">readonly ref 和 readonly 结构</span><span class="sxs-lookup"><span data-stu-id="6480a-144">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="6480a-145">readonly 结构成员</span><span class="sxs-lookup"><span data-stu-id="6480a-145">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="6480a-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="6480a-146">See also</span></span>

- [<span data-ttu-id="6480a-147">C# 参考</span><span class="sxs-lookup"><span data-stu-id="6480a-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6480a-148">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="6480a-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6480a-149">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="6480a-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6480a-150">修饰符</span><span class="sxs-lookup"><span data-stu-id="6480a-150">Modifiers</span></span>](index.md)
- [<span data-ttu-id="6480a-151">const</span><span class="sxs-lookup"><span data-stu-id="6480a-151">const</span></span>](const.md)
- [<span data-ttu-id="6480a-152">字段</span><span class="sxs-lookup"><span data-stu-id="6480a-152">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
