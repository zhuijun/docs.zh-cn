---
title: 代码协定
description: 探索代码协定，它提供了一种方法，用于指定 .NET 代码中的前置条件、后置条件和对象固定。
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
ms.openlocfilehash: 60f794373af75bd3f745c224e0a8c7a84192e4c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904138"
---
# <a name="code-contracts"></a><span data-ttu-id="e9974-103">代码协定</span><span class="sxs-lookup"><span data-stu-id="e9974-103">Code Contracts</span></span>

<span data-ttu-id="e9974-104">代码协定提供了在代码中指定前置条件、后置条件和对象固定的方法。</span><span class="sxs-lookup"><span data-stu-id="e9974-104">Code contracts provide a way to specify preconditions, postconditions, and object invariants in your code.</span></span> <span data-ttu-id="e9974-105">前置条件是输入方法或属性时必须满足的要求。</span><span class="sxs-lookup"><span data-stu-id="e9974-105">Preconditions are requirements that must be met when entering a method or property.</span></span> <span data-ttu-id="e9974-106">后置条件描述在方法或属性代码退出时的预期。</span><span class="sxs-lookup"><span data-stu-id="e9974-106">Postconditions describe expectations at the time the method or property code exits.</span></span> <span data-ttu-id="e9974-107">对象固定描述处于良好状态的类的预期状态。</span><span class="sxs-lookup"><span data-stu-id="e9974-107">Object invariants describe the expected state for a class that is in a good state.</span></span>

<span data-ttu-id="e9974-108">代码协定包含用于标记代码的类、用于编译时分析的静态分析器以及运行时分析器。</span><span class="sxs-lookup"><span data-stu-id="e9974-108">Code contracts include classes for marking your code, a static analyzer for compile-time analysis, and a runtime analyzer.</span></span> <span data-ttu-id="e9974-109">代码协定的类位于 <xref:System.Diagnostics.Contracts> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="e9974-109">The classes for code contracts can be found in the <xref:System.Diagnostics.Contracts> namespace.</span></span>

<span data-ttu-id="e9974-110">代码协定包括以下优点：</span><span class="sxs-lookup"><span data-stu-id="e9974-110">The benefits of code contracts include the following:</span></span>

- <span data-ttu-id="e9974-111">改进测试：代码协定提供静态协定验证、运行时检查和文档生成。</span><span class="sxs-lookup"><span data-stu-id="e9974-111">Improved testing: Code contracts provide static contract verification, runtime checking, and documentation generation.</span></span>

- <span data-ttu-id="e9974-112">自动测试工具：可通过过滤掉不满足前置条件的无意义的测试参数，使用代码协定来生成更有意义的单元测试。</span><span class="sxs-lookup"><span data-stu-id="e9974-112">Automatic testing tools: You can use code contracts to generate more meaningful unit tests by filtering out meaningless test arguments that do not satisfy preconditions.</span></span>

- <span data-ttu-id="e9974-113">静态验证：静态检查器无需运行程序即可决定是否存在任何协定冲突。</span><span class="sxs-lookup"><span data-stu-id="e9974-113">Static verification: The static checker can decide whether there are any contract violations without running the program.</span></span> <span data-ttu-id="e9974-114">它可检查隐式协定（如 null 取消引用和数组绑定）和显式协定。</span><span class="sxs-lookup"><span data-stu-id="e9974-114">It checks for implicit contracts, such as null dereferences and array bounds, and explicit contracts.</span></span>

- <span data-ttu-id="e9974-115">参考文档：文档生成器扩充具有协定信息的现有 XML 文档文件。</span><span class="sxs-lookup"><span data-stu-id="e9974-115">Reference documentation: The documentation generator augments existing XML documentation files with contract information.</span></span> <span data-ttu-id="e9974-116">还提供了可与 [Sandcastle ](https://github.com/EWSoftware/SHFB)一起使用的样式表，因此，生成的文档页具有协定部分。</span><span class="sxs-lookup"><span data-stu-id="e9974-116">There are also style sheets that can be used with [Sandcastle](https://github.com/EWSoftware/SHFB) so that the generated documentation pages have contract sections.</span></span>

<span data-ttu-id="e9974-117">所有 .NET Framework 语言可立即使用协定；无需编写特定分析器或编译器。</span><span class="sxs-lookup"><span data-stu-id="e9974-117">All .NET Framework languages can immediately take advantage of contracts; you do not have to write a special parser or compiler.</span></span> <span data-ttu-id="e9974-118">Visual Studio 外接程序使你可以指定要执行的代码协定分析的级别。</span><span class="sxs-lookup"><span data-stu-id="e9974-118">A Visual Studio add-in lets you specify the level of code contract analysis to be performed.</span></span> <span data-ttu-id="e9974-119">分析器可确认协定的格式是否标准（类型检查和名称解析），并且可以 Microsoft 中间语言 (MSIL) 格式生成约定的已编译形式。</span><span class="sxs-lookup"><span data-stu-id="e9974-119">The analyzers can confirm that the contracts are well-formed (type checking and name resolution) and can produce a compiled form of the contracts in Microsoft intermediate language (MSIL) format.</span></span> <span data-ttu-id="e9974-120">通过在 Visual Studio 中创建协定，你可以使用工具提供的标准 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="e9974-120">Authoring contracts in Visual Studio lets you take advantage of the standard IntelliSense provided by the tool.</span></span>

<span data-ttu-id="e9974-121">协定类中的大多数方法都进行条件编译；即，编译器仅在你定义特殊符号 CONTRACTS_FULL 时才使用 `#define` 指令发出对这些方法的调用。</span><span class="sxs-lookup"><span data-stu-id="e9974-121">Most methods in the contract class are conditionally compiled; that is, the compiler emits calls to these methods only when  you define a special symbol, CONTRACTS_FULL, by using the `#define` directive.</span></span> <span data-ttu-id="e9974-122">借助 CONTRACTS_FULL，你无需需使用 `#ifdef` 指令就可将协定写入代码；还可生成两种不同的版本：一种带有协定，一种未带协定。</span><span class="sxs-lookup"><span data-stu-id="e9974-122">CONTRACTS_FULL lets you write contracts in your code without using `#ifdef` directives; you can produce different builds, some with contracts, and some without.</span></span>

<span data-ttu-id="e9974-123">有关使用代码协定的工具和详细说明，请参阅 Visual Studio marketplace 网站上的[代码协定](https://marketplace.visualstudio.com/items?itemName=RiSEResearchinSoftwareEngineering.CodeContractsforNET)。</span><span class="sxs-lookup"><span data-stu-id="e9974-123">For tools and detailed instructions for using code contracts, see [Code Contracts](https://marketplace.visualstudio.com/items?itemName=RiSEResearchinSoftwareEngineering.CodeContractsforNET) on the Visual Studio marketplace site.</span></span>

## <a name="preconditions"></a><span data-ttu-id="e9974-124">Preconditions</span><span class="sxs-lookup"><span data-stu-id="e9974-124">Preconditions</span></span>

<span data-ttu-id="e9974-125">可使用 <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> 方法表达前置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-125">You can express preconditions by using the <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e9974-126">前置条件在方法被调用时指定状态。</span><span class="sxs-lookup"><span data-stu-id="e9974-126">Preconditions specify state when a method is invoked.</span></span> <span data-ttu-id="e9974-127">它们通常用于指定有效的参数值。</span><span class="sxs-lookup"><span data-stu-id="e9974-127">They are generally used to specify valid parameter values.</span></span> <span data-ttu-id="e9974-128">前置条件中提到的所有成员至少都必须与方法本身一样可以访问；否则，方法的调用方可能无法理解此前置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-128">All members that are mentioned in preconditions must be at least as accessible as the method itself; otherwise, the precondition might not be understood by all callers of a method.</span></span> <span data-ttu-id="e9974-129">条件必须无副作用。</span><span class="sxs-lookup"><span data-stu-id="e9974-129">The condition must have no side-effects.</span></span> <span data-ttu-id="e9974-130">运行时分析器确定前置条件失败时的运行时行为。</span><span class="sxs-lookup"><span data-stu-id="e9974-130">The run-time behavior of failed preconditions is determined by the runtime analyzer.</span></span>

<span data-ttu-id="e9974-131">例如，以下前置条件表示参数 `x` 必须为非 null。</span><span class="sxs-lookup"><span data-stu-id="e9974-131">For example, the following precondition expresses that parameter `x` must be non-null.</span></span>

```csharp
Contract.Requires(x != null);
```

<span data-ttu-id="e9974-132">如果你的代码必须在前置条件失败时引发特定异常，可使用 <xref:System.Diagnostics.Contracts.Contract.Requires%2A> 的泛型重载，如下所示。</span><span class="sxs-lookup"><span data-stu-id="e9974-132">If your code must throw a particular exception on failure of a precondition, you can use the generic overload of <xref:System.Diagnostics.Contracts.Contract.Requires%2A> as follows.</span></span>

```csharp
Contract.Requires<ArgumentNullException>(x != null, "x");
```

### <a name="legacy-requires-statements"></a><span data-ttu-id="e9974-133">旧版需要语句</span><span class="sxs-lookup"><span data-stu-id="e9974-133">Legacy Requires Statements</span></span>

<span data-ttu-id="e9974-134">大多数代码包含一些参数验证，其形式为 `if`-`then`-`throw` 代码。</span><span class="sxs-lookup"><span data-stu-id="e9974-134">Most code contains some parameter validation in the form of `if`-`then`-`throw` code.</span></span> <span data-ttu-id="e9974-135">在以下情况中，协定工具将这些语句识别为前置条件：</span><span class="sxs-lookup"><span data-stu-id="e9974-135">The contract tools recognize these statements as preconditions in the following cases:</span></span>

- <span data-ttu-id="e9974-136">这些语句显示在方法中任何其他语句之前。</span><span class="sxs-lookup"><span data-stu-id="e9974-136">The statements appear before any other statements in a method.</span></span>

- <span data-ttu-id="e9974-137">整组此类语句后面接显式 <xref:System.Diagnostics.Contracts.Contract> 方法调用，如对 <xref:System.Diagnostics.Contracts.Contract.Requires%2A>、<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>、<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A> 或 <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> 方法的调用。</span><span class="sxs-lookup"><span data-stu-id="e9974-137">The entire set of such statements is followed by an explicit <xref:System.Diagnostics.Contracts.Contract> method call, such as a call to the <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, or <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> method.</span></span>

<span data-ttu-id="e9974-138">`if`-`then`-`throw` 语句显示为此形式时，工具会将其识别为旧的 `requires` 语句。</span><span class="sxs-lookup"><span data-stu-id="e9974-138">When `if`-`then`-`throw` statements appear in this form, the tools recognize them as legacy `requires` statements.</span></span> <span data-ttu-id="e9974-139">如果 `if`-`then`-`throw` 序列后未接其他协定，则代码以 <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> 方法结束。</span><span class="sxs-lookup"><span data-stu-id="e9974-139">If no other contracts follow the `if`-`then`-`throw` sequence, end the code with the <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> method.</span></span>

```csharp
if (x == null) throw new ...
Contract.EndContractBlock(); // All previous "if" checks are preconditions
```

<span data-ttu-id="e9974-140">请注意，上述测试中的条件是取反的前置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-140">Note that the condition in the preceding test is a negated precondition.</span></span> <span data-ttu-id="e9974-141">（实际前提条件为 `x != null` 。）求反的前置条件受到严格限制：必须按前面的示例所示编写：也就是说，它不应包含 `else` 子句，并且子句的主体 `then` 必须是单个 `throw` 语句。</span><span class="sxs-lookup"><span data-stu-id="e9974-141">(The actual precondition would be `x != null`.) A negated precondition is highly restricted: It must be written as shown in the previous example; that is, it should contain no `else` clauses, and the body of the `then` clause must be a single `throw` statement.</span></span> <span data-ttu-id="e9974-142">`if` 测试受纯度和可见性规则约束（请参阅[使用准则](#usage_guidelines)），但 `throw` 表达式仅受纯度规则约束。</span><span class="sxs-lookup"><span data-stu-id="e9974-142">The `if` test is subject to both purity and visibility rules (see [Usage Guidelines](#usage_guidelines)), but the `throw` expression is subject only to purity rules.</span></span> <span data-ttu-id="e9974-143">但是，引发的异常类型必须与发生协定的方法同样可见。</span><span class="sxs-lookup"><span data-stu-id="e9974-143">However, the type of the exception thrown must be as visible as the method in which the contract occurs.</span></span>

## <a name="postconditions"></a><span data-ttu-id="e9974-144">Postconditions</span><span class="sxs-lookup"><span data-stu-id="e9974-144">Postconditions</span></span>

<span data-ttu-id="e9974-145">后置条件是方法终止时的方法的状态协定。</span><span class="sxs-lookup"><span data-stu-id="e9974-145">Postconditions are contracts for the state of a method when it terminates.</span></span> <span data-ttu-id="e9974-146">刚好退出方法前检查后置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-146">The postcondition is checked just before exiting a method.</span></span> <span data-ttu-id="e9974-147">运行时分析器确定后置条件失败时的运行时行为。</span><span class="sxs-lookup"><span data-stu-id="e9974-147">The run-time behavior of failed postconditions is determined by the runtime analyzer.</span></span>

<span data-ttu-id="e9974-148">与前置条件不同，后置条件可能引用可见性较低的成员。</span><span class="sxs-lookup"><span data-stu-id="e9974-148">Unlike preconditions, postconditions may reference members with less visibility.</span></span> <span data-ttu-id="e9974-149">客户端可能无法理解或利用后置条件使用私有状态表达的某些信息，但这不影响客户端正确使用方法的能力。</span><span class="sxs-lookup"><span data-stu-id="e9974-149">A client may not be able to understand or make use of some of the information expressed by a postcondition using private state, but this does not affect the client's ability to use the method correctly.</span></span>

### <a name="standard-postconditions"></a><span data-ttu-id="e9974-150">标准后置条件</span><span class="sxs-lookup"><span data-stu-id="e9974-150">Standard Postconditions</span></span>

<span data-ttu-id="e9974-151">可使用 <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> 方法表达标准后置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-151">You can express standard postconditions by using the <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> method.</span></span> <span data-ttu-id="e9974-152">后置条件表示方法正常终止时必须为 `true` 的条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-152">Postconditions express a condition that must be `true` upon normal termination of the method.</span></span>

```csharp
Contract.Ensures(this.F > 0);
```

### <a name="exceptional-postconditions"></a><span data-ttu-id="e9974-153">异常后置条件</span><span class="sxs-lookup"><span data-stu-id="e9974-153">Exceptional Postconditions</span></span>

<span data-ttu-id="e9974-154">异常后置条件是在方法引发特定异常时应为 `true` 的后置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-154">Exceptional postconditions are postconditions that should be `true` when a particular exception is thrown by a method.</span></span> <span data-ttu-id="e9974-155">可使用 <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> 方法来指定这些后置条件，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="e9974-155">You can specify these postconditions by using the <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> method, as the following example shows.</span></span>

```csharp
Contract.EnsuresOnThrow<T>(this.F > 0);
```

<span data-ttu-id="e9974-156">自变量是指每次引发作为 `T` 的子类型的异常时必须为 `true` 的条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-156">The argument is the condition that must be `true` whenever an exception that is a subtype of `T` is thrown.</span></span>

<span data-ttu-id="e9974-157">有一些异常类型很难在异常后置条件中使用。</span><span class="sxs-lookup"><span data-stu-id="e9974-157">There are some exception types that are difficult to use in an exceptional postcondition.</span></span> <span data-ttu-id="e9974-158">例如，若要使用 `T` 的 <xref:System.Exception> 类型，则无论引发的异常类型如何（即使是堆栈溢出或其他不可控制的异常），方法都必须保证条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-158">For example, using the type <xref:System.Exception> for `T` requires the method to guarantee the condition regardless of the type of exception that is thrown, even if it is a stack overflow or other impossible-to-control exception.</span></span> <span data-ttu-id="e9974-159">应仅将异常后置条件用于调用成员时可能引发的特定异常，例如，当对 <xref:System.TimeZoneInfo> 方法调用引发 <xref:System.InvalidTimeZoneException> 时。</span><span class="sxs-lookup"><span data-stu-id="e9974-159">You should use exceptional postconditions only for specific exceptions that might be thrown when a member is called, for example, when an <xref:System.InvalidTimeZoneException> is thrown for a <xref:System.TimeZoneInfo> method call.</span></span>

### <a name="special-postconditions"></a><span data-ttu-id="e9974-160">特殊后置条件</span><span class="sxs-lookup"><span data-stu-id="e9974-160">Special Postconditions</span></span>

<span data-ttu-id="e9974-161">以下方法可能仅在后置条件中使用：</span><span class="sxs-lookup"><span data-stu-id="e9974-161">The following methods may be used only within postconditions:</span></span>

- <span data-ttu-id="e9974-162">通过使用表达式 `Contract.Result<T>()`（其中 `T` 替换为方法的返回类型），可引用后置条件中的方法返回值。</span><span class="sxs-lookup"><span data-stu-id="e9974-162">You can refer to method return values in postconditions by using the expression `Contract.Result<T>()`, where `T` is replaced by the return type of the method.</span></span> <span data-ttu-id="e9974-163">编译器无法推断出类型时，必须显式提供此类型。</span><span class="sxs-lookup"><span data-stu-id="e9974-163">When the compiler is unable to infer the type, you must explicitly provide it.</span></span> <span data-ttu-id="e9974-164">例如，C# 编译器无法推断不带任何参数的方法类型，因此它需要后置条件 `Contract.Ensures(0 <Contract.Result<int>())`。返回类型为 `void` 的方法无法引用后置条件中的 `Contract.Result<T>()`。</span><span class="sxs-lookup"><span data-stu-id="e9974-164">For example, the C# compiler is unable to infer types for methods that do not take any arguments, so it requires the following postcondition: `Contract.Ensures(0 <Contract.Result<int>())` Methods with a return type of `void` cannot refer to `Contract.Result<T>()` in their postconditions.</span></span>

- <span data-ttu-id="e9974-165">后置条件中的预状态值是指方法或属性开头的表达式的值。</span><span class="sxs-lookup"><span data-stu-id="e9974-165">A prestate value in a postcondition refers to the value of an expression at the start of a method or property.</span></span> <span data-ttu-id="e9974-166">它使用表达式 `Contract.OldValue<T>(e)`，其中 `T` 是 `e` 的类型。</span><span class="sxs-lookup"><span data-stu-id="e9974-166">It uses the expression `Contract.OldValue<T>(e)`, where `T` is the type of `e`.</span></span> <span data-ttu-id="e9974-167">每次编译器可推断出类型时，都可发出泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="e9974-167">You can omit the generic type argument whenever the compiler is able to infer its type.</span></span> <span data-ttu-id="e9974-168">（例如，c # 编译器始终会推断类型，因为它采用了参数。）在中可能出现的情况 `e` 和可能出现旧表达式的上下文中有几个限制。</span><span class="sxs-lookup"><span data-stu-id="e9974-168">(For example, the C# compiler always infers the type because it takes an argument.) There are several restrictions on what can occur in `e` and the contexts in which an old expression may appear.</span></span> <span data-ttu-id="e9974-169">旧表达式中不能包含其他旧表达式。</span><span class="sxs-lookup"><span data-stu-id="e9974-169">An old expression cannot contain another old expression.</span></span> <span data-ttu-id="e9974-170">最重要的是，旧表达式必须引用方法前置条件状态中的一个值。</span><span class="sxs-lookup"><span data-stu-id="e9974-170">Most importantly, an old expression must refer to a value that existed in the method's precondition state.</span></span> <span data-ttu-id="e9974-171">换言之，只要方法前置条件为 `true`，此表达式都必须可以进行计算。</span><span class="sxs-lookup"><span data-stu-id="e9974-171">In other words, it must be an expression that can be evaluated as long as the method's precondition is `true`.</span></span> <span data-ttu-id="e9974-172">以下是此规则的几个实例。</span><span class="sxs-lookup"><span data-stu-id="e9974-172">Here are several instances of that rule.</span></span>

  - <span data-ttu-id="e9974-173">方法的前置条件状态中必须存在值。</span><span class="sxs-lookup"><span data-stu-id="e9974-173">The value must exist in the method's precondition state.</span></span> <span data-ttu-id="e9974-174">若要引用对象上的字段，前提条件必须保证对象始终为非 null。</span><span class="sxs-lookup"><span data-stu-id="e9974-174">In order to reference a field on an object, the preconditions must guarantee that the object is always non-null.</span></span>

  - <span data-ttu-id="e9974-175">不能引用旧表达式中方法的返回值：</span><span class="sxs-lookup"><span data-stu-id="e9974-175">You cannot refer to the method's return value in an old expression:</span></span>

      ```csharp
      Contract.OldValue(Contract.Result<int>() + x) // ERROR
      ```

  - <span data-ttu-id="e9974-176">不能引用旧表达式中的 `out` 参数。</span><span class="sxs-lookup"><span data-stu-id="e9974-176">You cannot refer to `out` parameters in an old expression.</span></span>

  - <span data-ttu-id="e9974-177">如果限定符的范围取决于方法的返回值，则旧表达式不能依赖限定符的绑定变量：</span><span class="sxs-lookup"><span data-stu-id="e9974-177">An old expression cannot depend on the bound variable of a quantifier if the range of the quantifier depends on the return value of the method:</span></span>

      ```csharp
      Contract.ForAll(0, Contract.Result<int>(), i => Contract.OldValue(xs[i]) > 3); // ERROR
      ```

  - <span data-ttu-id="e9974-178">旧表达式不能引用 <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> 或 <xref:System.Diagnostics.Contracts.Contract.Exists%2A> 调用中的匿名委托的参数，除非它被用作方法调用的索引器或自变量：</span><span class="sxs-lookup"><span data-stu-id="e9974-178">An old expression cannot refer to the parameter of the anonymous delegate in a <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> or <xref:System.Diagnostics.Contracts.Contract.Exists%2A> call unless it is used as an indexer or argument to a method call:</span></span>

      ```csharp
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(xs[i]) > 3); // OK
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(i) > 3); // ERROR
      ```

  - <span data-ttu-id="e9974-179">如果旧表达式的值取决于匿名委托的任一参数，匿名委托的主体中不能出现旧表达式，除非匿名委托是 <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> 或 <xref:System.Diagnostics.Contracts.Contract.Exists%2A> 方法的参数：</span><span class="sxs-lookup"><span data-stu-id="e9974-179">An old expression cannot occur in the body of an anonymous delegate if the value of the old expression depends on any of the parameters of the anonymous delegate, unless the anonymous delegate is an argument to the <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> or <xref:System.Diagnostics.Contracts.Contract.Exists%2A> method:</span></span>

      ```csharp
      Method(... (T t) => Contract.OldValue(... t ...) ...); // ERROR
      ```

  - <span data-ttu-id="e9974-180">`Out` 参数出现问题，因为协定显示在方法主体之前，而大多数编译器不允许引用后置条件中的 `out` 参数。</span><span class="sxs-lookup"><span data-stu-id="e9974-180">`Out` parameters present a problem because contracts appear before the body of the method, and most compilers do not allow references to `out` parameters in postconditions.</span></span> <span data-ttu-id="e9974-181">若要解决此问题，<xref:System.Diagnostics.Contracts.Contract> 类需提供 <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> 方法，它允许基于 `out` 参数的后置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-181">To solve this problem, the <xref:System.Diagnostics.Contracts.Contract> class provides the <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> method, which allows a postcondition based on an `out` parameter.</span></span>

      ```csharp
      public void OutParam(out int x)
      {
          Contract.Ensures(Contract.ValueAtReturn(out x) == 3);
          x = 3;
      }
      ```

      <span data-ttu-id="e9974-182">与 <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> 方法一样，每次编译器能推断出类型时都可发出泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="e9974-182">As with the <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> method, you can omit the generic type parameter whenever the compiler is able to infer its type.</span></span> <span data-ttu-id="e9974-183">协定重写程序将方法调用替换为 `out` 参数的值。</span><span class="sxs-lookup"><span data-stu-id="e9974-183">The contract rewriter replaces the method call with the value of the `out` parameter.</span></span> <span data-ttu-id="e9974-184"><xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> 方法仅可在后置条件中出现。</span><span class="sxs-lookup"><span data-stu-id="e9974-184">The <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> method may appear only in postconditions.</span></span> <span data-ttu-id="e9974-185">方法的自变量必须为 `out` 参数或结构 `out` 参数的字段。</span><span class="sxs-lookup"><span data-stu-id="e9974-185">The argument to the method must be an `out` parameter or a field of a structure `out` parameter.</span></span> <span data-ttu-id="e9974-186">在引用结构构造函数后置条件中的字段时，后者也非常有用。</span><span class="sxs-lookup"><span data-stu-id="e9974-186">The latter is also useful when referring to fields in the postcondition of a structure constructor.</span></span>

      > [!NOTE]
      > <span data-ttu-id="e9974-187">目前，代码协定分析工具不会检查 `out` 参数是否正确初始化，并且忽略它在后置条件中的描述。</span><span class="sxs-lookup"><span data-stu-id="e9974-187">Currently, the code contract analysis tools do not check whether `out` parameters are initialized properly and disregard their mention in the postcondition.</span></span> <span data-ttu-id="e9974-188">因此，在先前示例中，如果协定后面的行使用了 `x` 的值而不是为其分配一个整数，编译器不会发出正确错误。</span><span class="sxs-lookup"><span data-stu-id="e9974-188">Therefore, in the previous example, if the line after the contract had used the value of `x` instead of assigning an integer to it, a compiler would not issue the correct error.</span></span> <span data-ttu-id="e9974-189">但是，在未定义 CONTRACTS_FULL 预处理器符号的版本（如 asa 发布版本）中，编译器将发出错误。</span><span class="sxs-lookup"><span data-stu-id="e9974-189">However, on a build where the CONTRACTS_FULL preprocessor symbol is not defined (such asa release build), the compiler will issue an error.</span></span>

## <a name="invariants"></a><span data-ttu-id="e9974-190">固定协定</span><span class="sxs-lookup"><span data-stu-id="e9974-190">Invariants</span></span>

<span data-ttu-id="e9974-191">对象固定是指无论何时对象对客户端可见都应适合类的每个实例的条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-191">Object invariants are conditions that should be true for each instance of a class whenever that object is visible to a client.</span></span> <span data-ttu-id="e9974-192">它们表示对象被视为正确的条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-192">They express the conditions under which the object is considered to be correct.</span></span>

<span data-ttu-id="e9974-193">固定协定方法的标识方式是以 <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> 属性进行标记。</span><span class="sxs-lookup"><span data-stu-id="e9974-193">The invariant methods are identified by being marked with the <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> attribute.</span></span> <span data-ttu-id="e9974-194">除了 <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> 方法的调用序列（其中每个调用指定一个固定协定），固定协定方法不可包含任何代码，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="e9974-194">The invariant methods must contain no code except for a sequence of calls to the <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> method, each of which specifies an individual invariant, as shown in the following example.</span></span>

```csharp
[ContractInvariantMethod]
protected void ObjectInvariant ()
{
    Contract.Invariant(this.y >= 0);
    Contract.Invariant(this.x > this.y);
    ...
}
```

<span data-ttu-id="e9974-195">固定协定由 CONTRACTS_FULL 预处理器符号有条件地进行定义。</span><span class="sxs-lookup"><span data-stu-id="e9974-195">Invariants are conditionally defined by the CONTRACTS_FULL preprocessor symbol.</span></span> <span data-ttu-id="e9974-196">在运行时检查期间，每次公共方法结束都要检查固定协定。</span><span class="sxs-lookup"><span data-stu-id="e9974-196">During run-time checking, invariants are checked at the end of each public method.</span></span> <span data-ttu-id="e9974-197">如果固定协定提到相同类中的公共方法，则将禁用通常在此公共方法结束时执行的固定协定检查。</span><span class="sxs-lookup"><span data-stu-id="e9974-197">If an invariant mentions a public method in the same class, the invariant check that would normally happen at the end of that public method is disabled.</span></span> <span data-ttu-id="e9974-198">相反，仅在此方法的最外层方法调用结束时进行检查。</span><span class="sxs-lookup"><span data-stu-id="e9974-198">Instead, the check occurs only at the end of the outermost method call to that class.</span></span> <span data-ttu-id="e9974-199">如果因调用其他类上的方法而重新输入类，也会发生此类情况。</span><span class="sxs-lookup"><span data-stu-id="e9974-199">This also happens if the class is re-entered because of a call to a method on another class.</span></span> <span data-ttu-id="e9974-200">不会检查对象终结器和实现的固定条件 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e9974-200">Invariants are not checked for an object finalizer and an <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span>

<a name="usage_guidelines"></a>

## <a name="usage-guidelines"></a><span data-ttu-id="e9974-201">使用准则</span><span class="sxs-lookup"><span data-stu-id="e9974-201">Usage Guidelines</span></span>

### <a name="contract-ordering"></a><span data-ttu-id="e9974-202">协定顺序</span><span class="sxs-lookup"><span data-stu-id="e9974-202">Contract Ordering</span></span>

<span data-ttu-id="e9974-203">下表显示编写方法协定时应使用的元素顺序。</span><span class="sxs-lookup"><span data-stu-id="e9974-203">The following table shows the order of elements you should use when you write method contracts.</span></span>

|`If-then-throw statements`|<span data-ttu-id="e9974-204">向后兼容的公共前置条件</span><span class="sxs-lookup"><span data-stu-id="e9974-204">Backward-compatible public preconditions</span></span>|
|-|-|
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|<span data-ttu-id="e9974-205">所有公共前置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-205">All public preconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|<span data-ttu-id="e9974-206">所有的公共（正常）后置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-206">All public (normal) postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|<span data-ttu-id="e9974-207">所有的公共（正常）后置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-207">All public exceptional postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|<span data-ttu-id="e9974-208">所有的私有/内部（正常）后置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-208">All private/internal (normal) postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|<span data-ttu-id="e9974-209">所有的私有/内部（正常）后置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-209">All private/internal exceptional postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|<span data-ttu-id="e9974-210">如果使用没有任何其他协定的 `if`-`then`-`throw` 样式前置条件，请调用 <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> 以表示之前所有的 if 检查均为前置条件。</span><span class="sxs-lookup"><span data-stu-id="e9974-210">If using `if`-`then`-`throw` style preconditions without any other contracts, place a call to <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> to indicate that all previous if checks are preconditions.</span></span>|

<a name="purity"></a>

### <a name="purity"></a><span data-ttu-id="e9974-211">纯度</span><span class="sxs-lookup"><span data-stu-id="e9974-211">Purity</span></span>

<span data-ttu-id="e9974-212">协定中调用的所有方法都必须是纯方法；即，它们不能更新任何预存在的状态。</span><span class="sxs-lookup"><span data-stu-id="e9974-212">All methods that are called within a contract must be pure; that is, they must not update any preexisting state.</span></span> <span data-ttu-id="e9974-213">纯方法可修改输入纯方法后创建的对象。</span><span class="sxs-lookup"><span data-stu-id="e9974-213">A pure method is allowed to modify objects that have been created after entry into the pure method.</span></span>

<span data-ttu-id="e9974-214">目前代码协定工具假定以下代码元素为纯元素：</span><span class="sxs-lookup"><span data-stu-id="e9974-214">Code contract tools currently assume that the following code elements are pure:</span></span>

- <span data-ttu-id="e9974-215">标记有 <xref:System.Diagnostics.Contracts.PureAttribute> 的方法。</span><span class="sxs-lookup"><span data-stu-id="e9974-215">Methods that are marked with the <xref:System.Diagnostics.Contracts.PureAttribute>.</span></span>

- <span data-ttu-id="e9974-216">标记有 <xref:System.Diagnostics.Contracts.PureAttribute>（此属性适用于所有类型的方法）的类型。</span><span class="sxs-lookup"><span data-stu-id="e9974-216">Types that are marked with the <xref:System.Diagnostics.Contracts.PureAttribute> (the attribute applies to all the type's methods).</span></span>

- <span data-ttu-id="e9974-217">属性 get 访问器。</span><span class="sxs-lookup"><span data-stu-id="e9974-217">Property get accessors.</span></span>

- <span data-ttu-id="e9974-218">运算符（名称以“op”开头且具有一个或两个参数和非 void 返回类型的静态方法）。</span><span class="sxs-lookup"><span data-stu-id="e9974-218">Operators (static methods whose names start with "op", and that have one or two parameters and a non-void return type).</span></span>

- <span data-ttu-id="e9974-219">完全限定名以“System.Diagnostics.Contracts.Contract”、“System.String”、“System.IO.Path”或“System.Type”开头的所有方法。</span><span class="sxs-lookup"><span data-stu-id="e9974-219">Any method whose fully qualified name begins with "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path", or "System.Type".</span></span>

- <span data-ttu-id="e9974-220">任何调用的委托，前提条件是委托类型本身具有 <xref:System.Diagnostics.Contracts.PureAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="e9974-220">Any invoked delegate, provided that the delegate type itself is attributed with the <xref:System.Diagnostics.Contracts.PureAttribute>.</span></span> <span data-ttu-id="e9974-221">委托类型 <xref:System.Predicate%601?displayProperty=nameWithType> 和 <xref:System.Comparison%601?displayProperty=nameWithType> 被视为纯类型。</span><span class="sxs-lookup"><span data-stu-id="e9974-221">The delegate types <xref:System.Predicate%601?displayProperty=nameWithType> and <xref:System.Comparison%601?displayProperty=nameWithType> are considered pure.</span></span>

<a name="visibility"></a>

### <a name="visibility"></a><span data-ttu-id="e9974-222">可见性</span><span class="sxs-lookup"><span data-stu-id="e9974-222">Visibility</span></span>

<span data-ttu-id="e9974-223">协定中提到的所有成员至少必须与包含它们的方法一样可见。</span><span class="sxs-lookup"><span data-stu-id="e9974-223">All members mentioned in a contract must be at least as visible as the method in which they appear.</span></span> <span data-ttu-id="e9974-224">例如，公共方法的前置条件中不可提及私有字段；客户端在调用方法前不可验证此类协定。</span><span class="sxs-lookup"><span data-stu-id="e9974-224">For example, a private field cannot be mentioned in a precondition for a public method; clients cannot validate such a contract before they call the method.</span></span> <span data-ttu-id="e9974-225">但是，如果字段标记有 <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>，则不受这些规则限制。</span><span class="sxs-lookup"><span data-stu-id="e9974-225">However, if the field is marked with the <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, it is exempt from these rules.</span></span>

## <a name="example"></a><span data-ttu-id="e9974-226">示例</span><span class="sxs-lookup"><span data-stu-id="e9974-226">Example</span></span>

<span data-ttu-id="e9974-227">下面的示例显示了代码协定的用法。</span><span class="sxs-lookup"><span data-stu-id="e9974-227">The following example shows the use of code contracts.</span></span>

[!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
[!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
