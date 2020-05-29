---
title: using 静态指令 - C# 参考
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: bffbc026e8f7937db91d42b7a06a5b7bba3bc2f8
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396156"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="f82a6-102">using 静态指令（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="f82a6-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="f82a6-103">`using static` 指令指定一种类型，无需指定类型名称即可访问其静态成员和嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="f82a6-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="f82a6-104">语法为：</span><span class="sxs-lookup"><span data-stu-id="f82a6-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="f82a6-105">其中，fully-qualified-type-name 是无需指定类型名称即可访问其静态成员和嵌套类型的类型名称。</span><span class="sxs-lookup"><span data-stu-id="f82a6-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="f82a6-106">如果你不提供完全限定的类型名称（完整的命名空间名称以及类型名称），C# 便会生成编译器错误 [CS0246](../compiler-messages/cs0246.md)：“找不到类型名称或命名空间名称 ’type/namespace’ (是否缺少 using 指令或程序集引用?)”。</span><span class="sxs-lookup"><span data-stu-id="f82a6-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="f82a6-107">`using static` 指令适用于任何具有静态成员（或嵌套类型）的类型，即使该类型还具有实例成员。</span><span class="sxs-lookup"><span data-stu-id="f82a6-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="f82a6-108">但是，只能通过类型实例来调用实例成员。</span><span class="sxs-lookup"><span data-stu-id="f82a6-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="f82a6-109">`using static` 指令是在 C# 6 中引入的。</span><span class="sxs-lookup"><span data-stu-id="f82a6-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="f82a6-110">备注</span><span class="sxs-lookup"><span data-stu-id="f82a6-110">Remarks</span></span>

<span data-ttu-id="f82a6-111">通常，调用某个静态成员时，即会提供类型名称以及成员名称。</span><span class="sxs-lookup"><span data-stu-id="f82a6-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="f82a6-112">重复输入相同的类型名称来调用该类型的成员将生成详细的晦涩代码。</span><span class="sxs-lookup"><span data-stu-id="f82a6-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="f82a6-113">例如，`Circle` 类的以下定义引用 <xref:System.Math> 类的成员数。</span><span class="sxs-lookup"><span data-stu-id="f82a6-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="f82a6-114">通过消除每次引用成员时，显式引用 <xref:System.Math> 类的需求，`using static` 指令将生成更简洁的代码：</span><span class="sxs-lookup"><span data-stu-id="f82a6-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="f82a6-115">`using static` 仅导入可访问的静态成员和指定类型中声明的嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="f82a6-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="f82a6-116">不导入继承的成员。</span><span class="sxs-lookup"><span data-stu-id="f82a6-116">Inherited members are not imported.</span></span>  <span data-ttu-id="f82a6-117">可以从任何带 using static 指令的已命名类型导入，包括 Visual Basic 模块。</span><span class="sxs-lookup"><span data-stu-id="f82a6-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="f82a6-118">如果 F# 顶级函数在元数据中显示为一个已命名类型（其名称是有效的 C# 标识符）的静态成员，则可以导入该 F# 函数。</span><span class="sxs-lookup"><span data-stu-id="f82a6-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="f82a6-119">`using static` 使指定类型中声明的扩展方法可用于扩展方法查找。</span><span class="sxs-lookup"><span data-stu-id="f82a6-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="f82a6-120">但是，扩展方法的名称不导入到代码中非限定引用的作用域中。</span><span class="sxs-lookup"><span data-stu-id="f82a6-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="f82a6-121">同一编译单元或命名空间中通过不同 `using static` 命令从不同类型导入的具有相同名称的方法组成一个方法组。</span><span class="sxs-lookup"><span data-stu-id="f82a6-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="f82a6-122">这些方法组内的重载解决方法遵循一般 C# 规则。</span><span class="sxs-lookup"><span data-stu-id="f82a6-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="f82a6-123">示例</span><span class="sxs-lookup"><span data-stu-id="f82a6-123">Example</span></span>

<span data-ttu-id="f82a6-124">以下示例使用 `using static` 指令来提供 <xref:System.Console>、<xref:System.Math> 和 <xref:System.String> 类的静态成员，而无需指定其类型名称。</span><span class="sxs-lookup"><span data-stu-id="f82a6-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="f82a6-125">在此示例中，`using static` 指令也已经应用于 <xref:System.Double> 类型。</span><span class="sxs-lookup"><span data-stu-id="f82a6-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="f82a6-126">这使得在未指定类型名称情况下调用 <xref:System.Double.TryParse(System.String,System.Double@)> 方法成为可能。</span><span class="sxs-lookup"><span data-stu-id="f82a6-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="f82a6-127">但是，如此创建的代码可读性较差，因为这样有必要检查 `using static` 指令，以确定所调用的数值类型的 `TryParse` 方法。</span><span class="sxs-lookup"><span data-stu-id="f82a6-127">However, this creates less readable code, since it becomes necessary to check the `using static` directives to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="f82a6-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="f82a6-128">See also</span></span>

- [<span data-ttu-id="f82a6-129">using 指令</span><span class="sxs-lookup"><span data-stu-id="f82a6-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="f82a6-130">C# 参考</span><span class="sxs-lookup"><span data-stu-id="f82a6-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f82a6-131">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="f82a6-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f82a6-132">使用命名空间</span><span class="sxs-lookup"><span data-stu-id="f82a6-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="f82a6-133">命名空间</span><span class="sxs-lookup"><span data-stu-id="f82a6-133">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
