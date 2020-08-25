---
title: let 绑定
description: '了解如何使用 F # "let" 绑定，该绑定将标识符与值或函数关联起来。'
ms.date: 05/16/2016
ms.openlocfilehash: 6f2396f480c5e6c631d0022f4732419ee5b07db6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812219"
---
# <a name="let-bindings"></a><span data-ttu-id="f8c71-103">let 绑定</span><span class="sxs-lookup"><span data-stu-id="f8c71-103">let Bindings</span></span>

<span data-ttu-id="f8c71-104">*绑定*将标识符与值或函数关联。</span><span class="sxs-lookup"><span data-stu-id="f8c71-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="f8c71-105">使用 `let` 关键字可将名称绑定到值或函数。</span><span class="sxs-lookup"><span data-stu-id="f8c71-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8c71-106">语法</span><span class="sxs-lookup"><span data-stu-id="f8c71-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="f8c71-107">备注</span><span class="sxs-lookup"><span data-stu-id="f8c71-107">Remarks</span></span>

<span data-ttu-id="f8c71-108">`let`关键字用于定义一个或多个名称的值或函数值的绑定表达式。</span><span class="sxs-lookup"><span data-stu-id="f8c71-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="f8c71-109">表达式的最简单形式是将 `let` 名称绑定到简单值，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f8c71-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="f8c71-110">如果使用新行将表达式与标识符分隔开，则必须缩进表达式的每一行，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="f8c71-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="f8c71-111">例如，可以指定包含名称的模式，而不只是名称，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="f8c71-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="f8c71-112">*主体表达式*是使用其名称的表达式。</span><span class="sxs-lookup"><span data-stu-id="f8c71-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="f8c71-113">主体表达式显示在其自己的行上，并与关键字中的第一个字符完全对齐 `let` ：</span><span class="sxs-lookup"><span data-stu-id="f8c71-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="f8c71-114">`let`绑定可以出现在模块级别、类类型的定义或本地范围中，如函数定义中的。</span><span class="sxs-lookup"><span data-stu-id="f8c71-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="f8c71-115">`let`位于模块或类类型中的顶级绑定不需要具有主体表达式，而在其他范围级别，则需要主体表达式。</span><span class="sxs-lookup"><span data-stu-id="f8c71-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="f8c71-116">绑定名称可在定义点后使用，但在 `let` 绑定出现之前不会出现，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="f8c71-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="f8c71-117">函数绑定</span><span class="sxs-lookup"><span data-stu-id="f8c71-117">Function Bindings</span></span>

<span data-ttu-id="f8c71-118">函数绑定遵循值绑定规则，只不过函数绑定包括函数名称和参数，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="f8c71-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="f8c71-119">通常，参数是模式，如元组模式：</span><span class="sxs-lookup"><span data-stu-id="f8c71-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="f8c71-120">`let`绑定表达式的计算结果为最后一个表达式的值。</span><span class="sxs-lookup"><span data-stu-id="f8c71-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="f8c71-121">因此，在下面的代码示例中，的值 `result` 从计算得出 `100 * function3 (1, 2)` ，其计算结果为 `300` 。</span><span class="sxs-lookup"><span data-stu-id="f8c71-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="f8c71-122">有关详细信息，请参阅[函数](index.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c71-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="f8c71-123">类型批注</span><span class="sxs-lookup"><span data-stu-id="f8c71-123">Type Annotations</span></span>

<span data-ttu-id="f8c71-124">您可以通过包含冒号 (： ) 后跟类型名称，并将其括在括号中来指定参数的类型。</span><span class="sxs-lookup"><span data-stu-id="f8c71-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="f8c71-125">还可以通过在最后一个参数后面追加冒号和类型来指定返回值的类型。</span><span class="sxs-lookup"><span data-stu-id="f8c71-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="f8c71-126">的完整类型注释 `function1` （带有整数作为参数类型）将如下所示。</span><span class="sxs-lookup"><span data-stu-id="f8c71-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="f8c71-127">如果没有显式类型参数，则使用类型推理来确定函数的参数类型。</span><span class="sxs-lookup"><span data-stu-id="f8c71-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="f8c71-128">这可能包括自动将参数类型通用化为泛型。</span><span class="sxs-lookup"><span data-stu-id="f8c71-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="f8c71-129">有关详细信息，请参阅 [自动泛化](../generics/automatic-generalization.md) 和 [类型推理](../type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c71-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="f8c71-130">类中的 let 绑定</span><span class="sxs-lookup"><span data-stu-id="f8c71-130">let Bindings in Classes</span></span>

<span data-ttu-id="f8c71-131">`let`绑定可以出现在类类型中，但不能出现在结构或记录类型中。</span><span class="sxs-lookup"><span data-stu-id="f8c71-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="f8c71-132">若要在类类型中使用 let 绑定，此类必须具有主构造函数。</span><span class="sxs-lookup"><span data-stu-id="f8c71-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="f8c71-133">构造函数参数必须出现在类定义中的类型名称之后。</span><span class="sxs-lookup"><span data-stu-id="f8c71-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="f8c71-134">`let`类类型中的绑定定义此类类型的私有字段和成员，并且在类型中 `do` 构成类型的主构造函数的代码。</span><span class="sxs-lookup"><span data-stu-id="f8c71-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="f8c71-135">下面的代码示例显示了 `MyClass` 具有私有字段和的类 `field1` `field2` 。</span><span class="sxs-lookup"><span data-stu-id="f8c71-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="f8c71-136">和的作用 `field1` 域 `field2` 仅限于在其中声明它们的类型。</span><span class="sxs-lookup"><span data-stu-id="f8c71-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="f8c71-137">有关详细信息，请参阅类和[类](../classes.md) [ `let` 中的绑定](../members/let-bindings-in-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c71-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="f8c71-138">Let 绑定中的类型参数</span><span class="sxs-lookup"><span data-stu-id="f8c71-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="f8c71-139">`let`模块级别、类型或计算表达式中的绑定可以具有显式类型参数。</span><span class="sxs-lookup"><span data-stu-id="f8c71-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="f8c71-140">表达式中的 let 绑定，如函数定义中的，不能具有类型参数。</span><span class="sxs-lookup"><span data-stu-id="f8c71-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="f8c71-141">有关详细信息，请参阅[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c71-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="f8c71-142">Let 绑定上的属性</span><span class="sxs-lookup"><span data-stu-id="f8c71-142">Attributes on let Bindings</span></span>

<span data-ttu-id="f8c71-143">特性可应用于模块中的顶级 `let` 绑定，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="f8c71-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="f8c71-144">Let 绑定的作用域和可访问性</span><span class="sxs-lookup"><span data-stu-id="f8c71-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="f8c71-145">使用 let 绑定声明的实体的作用域仅限于包含作用域的部分 (例如，绑定显示后的函数、模块、文件或类) 。</span><span class="sxs-lookup"><span data-stu-id="f8c71-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="f8c71-146">因此，可以说，let binding 将名称引入到作用域中。</span><span class="sxs-lookup"><span data-stu-id="f8c71-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="f8c71-147">在模块中，只要模块可访问，模块的客户端就可以访问一个允许绑定值或函数，因为模块中的 let 绑定将编译为模块的公共函数。</span><span class="sxs-lookup"><span data-stu-id="f8c71-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="f8c71-148">与此相反，让类中的绑定对于类是私有的。</span><span class="sxs-lookup"><span data-stu-id="f8c71-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="f8c71-149">通常情况下，模块中的函数必须由客户端代码使用时的模块名称限定。</span><span class="sxs-lookup"><span data-stu-id="f8c71-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="f8c71-150">例如，如果模块 `Module1` 具有函数 `function1` ，则用户将指定 `Module1.function1` 以引用函数。</span><span class="sxs-lookup"><span data-stu-id="f8c71-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="f8c71-151">模块用户可以使用导入声明使该模块内的函数可供使用，而无需由模块名称限定。</span><span class="sxs-lookup"><span data-stu-id="f8c71-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="f8c71-152">在上述示例中，在这种情况下，模块的用户可以打开该模块，方法是使用导入声明打开 `Module1` ，然后 `function1` 直接引用。</span><span class="sxs-lookup"><span data-stu-id="f8c71-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

<span data-ttu-id="f8c71-153">某些模块的属性为 [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html)，这意味着它们公开的函数必须使用模块的名称进行限定。</span><span class="sxs-lookup"><span data-stu-id="f8c71-153">Some modules have the attribute [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="f8c71-154">例如，F # List 模块具有此属性。</span><span class="sxs-lookup"><span data-stu-id="f8c71-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="f8c71-155">有关模块和访问控制的详细信息，请参阅 [模块](../modules.md) 和 [访问控制](../access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c71-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8c71-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="f8c71-156">See also</span></span>

- [<span data-ttu-id="f8c71-157">函数</span><span class="sxs-lookup"><span data-stu-id="f8c71-157">Functions</span></span>](index.md)
- [<span data-ttu-id="f8c71-158">`let` 类中的绑定</span><span class="sxs-lookup"><span data-stu-id="f8c71-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
