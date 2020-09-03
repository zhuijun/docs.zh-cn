---
description: 了解 C# 中的值类型、种类以及内置值类型
title: 值类型 - C# 参考
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 7826e71fee235d32655ccfbc9060c3bbb48d76c5
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134765"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="f495c-103">值类型（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="f495c-103">Value types (C# reference)</span></span>

<span data-ttu-id="f495c-104">值类型\*\* 和[引用类型](../keywords/reference-types.md)是 C# 类型的两个主要类别。</span><span class="sxs-lookup"><span data-stu-id="f495c-104">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="f495c-105">值类型的变量包含类型的实例。</span><span class="sxs-lookup"><span data-stu-id="f495c-105">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="f495c-106">它不同于引用类型的变量，后者包含对类型实例的引用。</span><span class="sxs-lookup"><span data-stu-id="f495c-106">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="f495c-107">默认情况下，在[分配](../operators/assignment-operator.md)中，通过将实参传递给方法并返回方法结果来复制变量值。</span><span class="sxs-lookup"><span data-stu-id="f495c-107">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="f495c-108">对于值类型变量，会复制相应的类型实例。</span><span class="sxs-lookup"><span data-stu-id="f495c-108">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="f495c-109">以下示例演示了该行为：</span><span class="sxs-lookup"><span data-stu-id="f495c-109">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="f495c-110">如前面的示例所示，对值类型变量的操作只影响存储在变量中的值类型实例。</span><span class="sxs-lookup"><span data-stu-id="f495c-110">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="f495c-111">如果值类型包含引用类型的数据成员，则在复制值类型实例时，只会复制对引用类型实例的引用。</span><span class="sxs-lookup"><span data-stu-id="f495c-111">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="f495c-112">副本和原始值类型实例都具有对同一引用类型实例的访问权限。</span><span class="sxs-lookup"><span data-stu-id="f495c-112">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="f495c-113">以下示例演示了该行为：</span><span class="sxs-lookup"><span data-stu-id="f495c-113">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="f495c-114">若要使代码更不易出错、更可靠，请定义并使用不可变的值类型。</span><span class="sxs-lookup"><span data-stu-id="f495c-114">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="f495c-115">本文仅为演示目的使用可变值类型。</span><span class="sxs-lookup"><span data-stu-id="f495c-115">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="f495c-116">值类型的种类</span><span class="sxs-lookup"><span data-stu-id="f495c-116">Kinds of value types</span></span>

<span data-ttu-id="f495c-117">值类型可以是以下种类之一：</span><span class="sxs-lookup"><span data-stu-id="f495c-117">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="f495c-118">[结构类型](struct.md)，用于封装数据和相关功能</span><span class="sxs-lookup"><span data-stu-id="f495c-118">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="f495c-119">[枚举类型](enum.md)，由一组命名常数定义，表示一个选择或选择组合</span><span class="sxs-lookup"><span data-stu-id="f495c-119">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="f495c-120">[可为 null 值类型](nullable-value-types.md) `T?` 表示其基础值类型 `T` 的所有值及额外的 [null](../keywords/null.md) 值。</span><span class="sxs-lookup"><span data-stu-id="f495c-120">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="f495c-121">不能将 `null` 分配给值类型的变量，除非它是可为 null 的值类型。</span><span class="sxs-lookup"><span data-stu-id="f495c-121">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="f495c-122">内置值类型</span><span class="sxs-lookup"><span data-stu-id="f495c-122">Built-in value types</span></span>

<span data-ttu-id="f495c-123">C# 提供以下内置值类型，也称为“简单类型”\*\*：</span><span class="sxs-lookup"><span data-stu-id="f495c-123">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="f495c-124">整型数值类型</span><span class="sxs-lookup"><span data-stu-id="f495c-124">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="f495c-125">浮点型数值类型</span><span class="sxs-lookup"><span data-stu-id="f495c-125">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="f495c-126">[bool](bool.md)，表示布尔值</span><span class="sxs-lookup"><span data-stu-id="f495c-126">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="f495c-127">[char](char.md)，表示 Unicode UTF-16 字符</span><span class="sxs-lookup"><span data-stu-id="f495c-127">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="f495c-128">所有简单值都是结构类型，它们与其他结构类型的不同之处在于，它们允许特定的额外操作：</span><span class="sxs-lookup"><span data-stu-id="f495c-128">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="f495c-129">可以使用文字为简单类型提供值。</span><span class="sxs-lookup"><span data-stu-id="f495c-129">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="f495c-130">例如，`'A'` 是类型 `char` 的文本，`2001` 是类型 `int` 的文本。</span><span class="sxs-lookup"><span data-stu-id="f495c-130">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="f495c-131">可以使用 [const](../keywords/const.md) 关键字声明简单类型的常数。</span><span class="sxs-lookup"><span data-stu-id="f495c-131">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="f495c-132">不能具有其他结构类型的常数。</span><span class="sxs-lookup"><span data-stu-id="f495c-132">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="f495c-133">常数表达式的操作数都是简单类型的常数，在编译时进行评估。</span><span class="sxs-lookup"><span data-stu-id="f495c-133">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="f495c-134">从 C# 7.0 开始，C# 支持[值元组](value-tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="f495c-134">Beginning with C# 7.0, C# supports [value tuples](value-tuples.md).</span></span> <span data-ttu-id="f495c-135">值元组是值类型，而不是简单类型。</span><span class="sxs-lookup"><span data-stu-id="f495c-135">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f495c-136">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="f495c-136">C# language specification</span></span>

<span data-ttu-id="f495c-137">有关更多信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的以下部分：</span><span class="sxs-lookup"><span data-stu-id="f495c-137">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f495c-138">值类型</span><span class="sxs-lookup"><span data-stu-id="f495c-138">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="f495c-139">简单类型</span><span class="sxs-lookup"><span data-stu-id="f495c-139">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="f495c-140">变量</span><span class="sxs-lookup"><span data-stu-id="f495c-140">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="f495c-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f495c-141">See also</span></span>

- [<span data-ttu-id="f495c-142">C# 参考</span><span class="sxs-lookup"><span data-stu-id="f495c-142">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="f495c-143">引用类型</span><span class="sxs-lookup"><span data-stu-id="f495c-143">Reference types</span></span>](../keywords/reference-types.md)
