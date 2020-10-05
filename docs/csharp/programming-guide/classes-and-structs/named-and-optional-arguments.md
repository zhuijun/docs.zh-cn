---
title: 命名参数和可选参数 - C# 编程指南
description: C# 中的命名参数按名称而不是位置指定参数。 可以省略可选元素。
ms.date: 09/25/2020
ms.custom: contperfq1
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: a0606d6acccb47347c663a9fe3ffb8ab65b0ecec
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438004"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="8b743-104">命名实参和可选实参（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="8b743-104">Named and Optional Arguments (C# Programming Guide)</span></span>

<span data-ttu-id="8b743-105">C# 4 介绍命名实参和可选实参。</span><span class="sxs-lookup"><span data-stu-id="8b743-105">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="8b743-106">通过命名实参，你可以为形参指定实参，方法是将实参与该形参的名称匹配，而不是与形参在形参列表中的位置匹配。</span><span class="sxs-lookup"><span data-stu-id="8b743-106">*Named arguments* enable you to specify an argument for a parameter by matching the argument with its name rather than with its position in the parameter list.</span></span> <span data-ttu-id="8b743-107">通过*可选参数*，你可以为某些形参省略实参。</span><span class="sxs-lookup"><span data-stu-id="8b743-107">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="8b743-108">这两种技术都可与方法、索引器、构造函数和委托一起使用。</span><span class="sxs-lookup"><span data-stu-id="8b743-108">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>

<span data-ttu-id="8b743-109">使用命名参数和可选参数时，将按实参出现在实参列表（而不是形参列表）中的顺序计算这些实参。</span><span class="sxs-lookup"><span data-stu-id="8b743-109">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>

<span data-ttu-id="8b743-110">通过命名形参和可选形参，你可以为所选形参提供实参。</span><span class="sxs-lookup"><span data-stu-id="8b743-110">Named and optional parameters enable you to supply arguments for selected parameters.</span></span> <span data-ttu-id="8b743-111">此功能极大地方便了对 COM 接口（例如 Microsoft Office 自动化 API）的调用。</span><span class="sxs-lookup"><span data-stu-id="8b743-111">This capability greatly eases calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="8b743-112">命名实参</span><span class="sxs-lookup"><span data-stu-id="8b743-112">Named Arguments</span></span>

<span data-ttu-id="8b743-113">有了命名实参，你将不再匹配形参在所调用方法的形参列表中的顺序。</span><span class="sxs-lookup"><span data-stu-id="8b743-113">Named arguments free you from matching the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="8b743-114">每个实参的形参都可按形参名称进行指定。</span><span class="sxs-lookup"><span data-stu-id="8b743-114">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="8b743-115">例如，通过以函数定义的顺序按位置发送实参，可以调用打印订单详细信息（例如卖家姓名、订单号和产品名称）的函数。</span><span class="sxs-lookup"><span data-stu-id="8b743-115">For example, a function that prints order details (such as, seller name, order number & product name) can be called by sending arguments by position, in the order defined by the function.</span></span>

```csharp
PrintOrderDetails("Gift Shop", 31, "Red Mug");
```

<span data-ttu-id="8b743-116">如果不记得形参的顺序，但却知道其名称，则可以按任意顺序发送实参。</span><span class="sxs-lookup"><span data-stu-id="8b743-116">If you don't remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>

```csharp
PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");
PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);
```

<span data-ttu-id="8b743-117">命名实参还可以标识每个实参所表示的含义，从而改进代码的可读性。</span><span class="sxs-lookup"><span data-stu-id="8b743-117">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="8b743-118">在下面的示例方法中，`sellerName` 不得为 NULL 或空白符。</span><span class="sxs-lookup"><span data-stu-id="8b743-118">In the example method below, the `sellerName` can't be null or white space.</span></span> <span data-ttu-id="8b743-119">由于 `sellerName` 和 `productName` 都是字符串类型，所以使用命名实参而不是按位置发送实参是有意义的，可以区分这两种类型并减少代码阅读者的困惑。</span><span class="sxs-lookup"><span data-stu-id="8b743-119">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
<span data-ttu-id="8b743-120">当命名实参与位置实参一起使用时，只要</span><span class="sxs-lookup"><span data-stu-id="8b743-120">Named arguments, when used with positional arguments, are valid as long as</span></span>

- <span data-ttu-id="8b743-121">没有后接任何位置实参或</span><span class="sxs-lookup"><span data-stu-id="8b743-121">they're not followed by any positional arguments, or</span></span>

    ```csharp
    PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");
    ```

- <span data-ttu-id="8b743-122">以 C# 7.2 开头，则它们就有效并用在正确位置。</span><span class="sxs-lookup"><span data-stu-id="8b743-122">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="8b743-123">在以下示例中，形参 `orderNum` 位于正确的位置，但未显式命名。</span><span class="sxs-lookup"><span data-stu-id="8b743-123">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

    ```csharp
    PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");
    ```

<span data-ttu-id="8b743-124">遵循任何无序命名参数的位置参数无效。</span><span class="sxs-lookup"><span data-stu-id="8b743-124">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

```csharp
// This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
```

## <a name="example"></a><span data-ttu-id="8b743-125">示例</span><span class="sxs-lookup"><span data-stu-id="8b743-125">Example</span></span>

<span data-ttu-id="8b743-126">以下代码执行本节以及某些其他节中的示例。</span><span class="sxs-lookup"><span data-stu-id="8b743-126">The following code implements the examples from this section along with some additional ones.</span></span>  

[!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]

## <a name="optional-arguments"></a><span data-ttu-id="8b743-127">可选实参</span><span class="sxs-lookup"><span data-stu-id="8b743-127">Optional Arguments</span></span>

<span data-ttu-id="8b743-128">方法、构造函数、索引器或委托的定义可以指定其形参为必需还是可选。</span><span class="sxs-lookup"><span data-stu-id="8b743-128">The definition of a method, constructor, indexer, or delegate can specify its parameters are required or optional.</span></span> <span data-ttu-id="8b743-129">任何调用都必须为所有必需的形参提供实参，但可以为可选的形参省略实参。</span><span class="sxs-lookup"><span data-stu-id="8b743-129">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>

<span data-ttu-id="8b743-130">每个可选形参都有一个默认值作为其定义的一部分。</span><span class="sxs-lookup"><span data-stu-id="8b743-130">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="8b743-131">如果没有为该形参发送实参，则使用默认值。</span><span class="sxs-lookup"><span data-stu-id="8b743-131">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="8b743-132">默认值必须是以下类型的表达式之一：</span><span class="sxs-lookup"><span data-stu-id="8b743-132">A default value must be one of the following types of expressions:</span></span>
  
- <span data-ttu-id="8b743-133">常量表达式；</span><span class="sxs-lookup"><span data-stu-id="8b743-133">a constant expression;</span></span>  
- <span data-ttu-id="8b743-134">`new ValType()` 形式的表达式，其中 `ValType` 是值类型，例如 [enum](../../language-reference/builtin-types/enum.md) 或 [struct](../../language-reference/builtin-types/struct.md)；</span><span class="sxs-lookup"><span data-stu-id="8b743-134">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/builtin-types/enum.md) or a [struct](../../language-reference/builtin-types/struct.md);</span></span>
- <span data-ttu-id="8b743-135">[default(ValType)](../../language-reference/operators/default.md) 形式的表达式，其中 `ValType` 是值类型。</span><span class="sxs-lookup"><span data-stu-id="8b743-135">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>

<span data-ttu-id="8b743-136">可选参数定义于参数列表的末尾和必需参数之后。</span><span class="sxs-lookup"><span data-stu-id="8b743-136">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="8b743-137">如果调用方为一系列可选形参中的任意一个形参提供了实参，则它必须为前面的所有可选形参提供实参。</span><span class="sxs-lookup"><span data-stu-id="8b743-137">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="8b743-138">实参列表中不支持使用逗号分隔的间隔。</span><span class="sxs-lookup"><span data-stu-id="8b743-138">Comma-separated gaps in the argument list aren't supported.</span></span> <span data-ttu-id="8b743-139">例如，在以下代码中，使用一个必选形参和两个可选形参定义实例方法 `ExampleMethod`。</span><span class="sxs-lookup"><span data-stu-id="8b743-139">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]

<span data-ttu-id="8b743-140">下面对 `ExampleMethod` 的调用会导致编译器错误，原因是为第三个形参而不是为第二个形参提供了实参。</span><span class="sxs-lookup"><span data-stu-id="8b743-140">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>

```csharp
//anExample.ExampleMethod(3, ,4);
```

<span data-ttu-id="8b743-141">但是，如果知道第三个形参的名称，则可以使用命名实参来完成此任务。</span><span class="sxs-lookup"><span data-stu-id="8b743-141">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>

```csharp
anExample.ExampleMethod(3, optionalint: 4);
```

<span data-ttu-id="8b743-142">IntelliSense 使用括号表示可选形参，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="8b743-142">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>

![显示 ExampleMethod 方法的 IntelliSense 快速信息的屏幕截图。](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)

> [!NOTE]
> <span data-ttu-id="8b743-144">此外，还可通过使用 .NET <xref:System.Runtime.InteropServices.OptionalAttribute> 类声明可选参数。</span><span class="sxs-lookup"><span data-stu-id="8b743-144">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="8b743-145">`OptionalAttribute` 形参不需要默认值。</span><span class="sxs-lookup"><span data-stu-id="8b743-145">`OptionalAttribute` parameters do not require a default value.</span></span>

## <a name="example"></a><span data-ttu-id="8b743-146">示例</span><span class="sxs-lookup"><span data-stu-id="8b743-146">Example</span></span>

<span data-ttu-id="8b743-147">在以下示例中，`ExampleClass` 的构造函数具有一个可选形参。</span><span class="sxs-lookup"><span data-stu-id="8b743-147">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="8b743-148">实例方法 `ExampleMethod` 具有一个必选形参（`required`）和两个可选形参（`optionalstr` 和 `optionalint`）。</span><span class="sxs-lookup"><span data-stu-id="8b743-148">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="8b743-149">`Main` 中的代码演示了可用于调用构造函数和方法的不同方式。</span><span class="sxs-lookup"><span data-stu-id="8b743-149">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]

<span data-ttu-id="8b743-150">前面的代码演示了一些示例，其中不会正确应用可选形参。</span><span class="sxs-lookup"><span data-stu-id="8b743-150">The preceding code shows a number of examples where optional parameters aren't applied correctly.</span></span> <span data-ttu-id="8b743-151">第一个示例说明了必须为第一个形参提供实参，这是必需的。</span><span class="sxs-lookup"><span data-stu-id="8b743-151">The first illustrates that an argument must be supplied for the first parameter, which is required.</span></span>
  
## <a name="com-interfaces"></a><span data-ttu-id="8b743-152">COM 接口</span><span class="sxs-lookup"><span data-stu-id="8b743-152">COM Interfaces</span></span>

<span data-ttu-id="8b743-153">命名实参和可选实参，以及对动态对象的支持大大提高了与 COM API（例如 Office Automation API）的互操作性。</span><span class="sxs-lookup"><span data-stu-id="8b743-153">Named and optional arguments, along with support for dynamic objects, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>

<span data-ttu-id="8b743-154">例如，Microsoft Office Excel 的 <xref:Microsoft.Office.Interop.Excel.Range> 接口中的 <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> 方法有七个可选形参。</span><span class="sxs-lookup"><span data-stu-id="8b743-154">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="8b743-155">这些形参如下图所示：</span><span class="sxs-lookup"><span data-stu-id="8b743-155">These parameters are shown in the following illustration:</span></span>

![显示 AutoFormat 方法的 IntelliSense 快速信息的屏幕截图。](./media/named-and-optional-arguments/autoformat-method-parameters.png)

<span data-ttu-id="8b743-157">在 C# 3.0 以及早期版本中，每个形参都需要一个实参，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="8b743-157">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]

<span data-ttu-id="8b743-158">但是，可以通过使用 C# 4.0 中引入的命名实参和可选实参来大大简化对 `AutoFormat` 的调用。</span><span class="sxs-lookup"><span data-stu-id="8b743-158">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="8b743-159">如果不希望更改形参的默认值，则可以通过使用命名实参和可选实参来省略可选形参的实参。</span><span class="sxs-lookup"><span data-stu-id="8b743-159">Named and optional arguments enable you to omit the argument for an optional parameter if you don't want to change the parameter's default value.</span></span> <span data-ttu-id="8b743-160">在下面的调用中，仅为 7 个形参中的其中一个指定了值。</span><span class="sxs-lookup"><span data-stu-id="8b743-160">In the following call, a value is specified for only one of the seven parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]

<span data-ttu-id="8b743-161">有关详细信息和示例，请参阅[如何在 Office 编程中使用命名参数和可选参数](./how-to-use-named-and-optional-arguments-in-office-programming.md)和[如何使用 C# 功能访问 Office 互操作性对象](../interop/how-to-access-office-onterop-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="8b743-161">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to access Office interop objects by using C# features](../interop/how-to-access-office-onterop-objects.md).</span></span>
  
## <a name="overload-resolution"></a><span data-ttu-id="8b743-162">重载决策</span><span class="sxs-lookup"><span data-stu-id="8b743-162">Overload Resolution</span></span>

<span data-ttu-id="8b743-163">使用命名实参和可选实参将在以下方面对重载决策产生影响：</span><span class="sxs-lookup"><span data-stu-id="8b743-163">Use of named and optional arguments affects overload resolution in the following ways:</span></span>

- <span data-ttu-id="8b743-164">如果方法、索引器或构造函数的每个参数是可选的，或按名称或位置对应于调用语句中的单个自变量，且该自变量可转换为参数的类型，则方法、索引器或构造函数为执行的候选项。</span><span class="sxs-lookup"><span data-stu-id="8b743-164">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
- <span data-ttu-id="8b743-165">如果找到多个候选项，则会将用于首选转换的重载决策规则应用于显式指定的自变量。</span><span class="sxs-lookup"><span data-stu-id="8b743-165">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="8b743-166">将忽略可选形参已省略的实参。</span><span class="sxs-lookup"><span data-stu-id="8b743-166">Omitted arguments for optional parameters are ignored.</span></span>
- <span data-ttu-id="8b743-167">如果两个候选项不相上下，则会将没有可选形参的候选项作为首选项，对于这些可选形参，已在调用中为其省略了实参。</span><span class="sxs-lookup"><span data-stu-id="8b743-167">If two candidates are judged to be equally good, preference goes to a candidate that doesn't have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="8b743-168">重载决策通常首选具有较少形参的候选项。</span><span class="sxs-lookup"><span data-stu-id="8b743-168">Overload resolution generally prefers candidates that have fewer parameters.</span></span>
  
## <a name="c-language-specification"></a><span data-ttu-id="8b743-169">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="8b743-169">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
