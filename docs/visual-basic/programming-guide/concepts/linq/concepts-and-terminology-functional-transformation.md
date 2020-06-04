---
title: 概念和术语（功能转换）
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: 4a63630d431a0972fb1a61981306a41e6f4926e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410859"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a><span data-ttu-id="5ab31-102">概念和术语（功能转换）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5ab31-102">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>
<span data-ttu-id="5ab31-103">本主题介绍纯函数转换的概念和术语。</span><span class="sxs-lookup"><span data-stu-id="5ab31-103">This topic introduces the concepts and terminology of pure functional transformations.</span></span> <span data-ttu-id="5ab31-104">与更加传统的命令性编程方式相比，用来转换数据的函数转换方法所生成的代码往往编程速度更快、含义更明确、更易于调试和维护。</span><span class="sxs-lookup"><span data-stu-id="5ab31-104">The functional transformation approach to transforming data yields code that is often quicker to program, more expressive, and easier to debug and maintain than more traditional, imperative programming.</span></span>

<span data-ttu-id="5ab31-105">请注意，本节中的主题并不是要透彻解释函数编程。</span><span class="sxs-lookup"><span data-stu-id="5ab31-105">Note that the topics in this section are not intended to fully explain functional programming.</span></span> <span data-ttu-id="5ab31-106">这些主题只是介绍函数编程的一些功能，这些功能降低了将 XML 从一种形状转换为另一种形状的难度。</span><span class="sxs-lookup"><span data-stu-id="5ab31-106">Instead, these topics identify some of the functional programming capabilities that make it easier to transform XML from one shape to another.</span></span>

## <a name="what-is-pure-functional-transformation"></a><span data-ttu-id="5ab31-107">什么是纯函数转换？</span><span class="sxs-lookup"><span data-stu-id="5ab31-107">What Is Pure Functional Transformation?</span></span>

<span data-ttu-id="5ab31-108">在纯函数转换  中，称为“纯函数”  的一组函数定义如何将一组结构化数据从其原始格式转换为另一种格式。</span><span class="sxs-lookup"><span data-stu-id="5ab31-108">In *pure functional transformation*, a set of functions, called *pure functions*, define how to transform a set of structured data from its original form into another form.</span></span> <span data-ttu-id="5ab31-109">“纯”表示这些函数是可组合的  ，这要求这些函数具有以下特点：</span><span class="sxs-lookup"><span data-stu-id="5ab31-109">The word "pure" indicates that the functions are *composable*, which requires that they are:</span></span>

- <span data-ttu-id="5ab31-110">独立  ，这样函数就可以自由排序和重新排列，而不会与程序的其他部分相互牵连和依赖。</span><span class="sxs-lookup"><span data-stu-id="5ab31-110">*Self-contained*, so that they can be freely ordered and rearranged without entanglement or interdependencies with the rest of the program.</span></span> <span data-ttu-id="5ab31-111">纯转换不了解其环境，对环境也没有任何影响。</span><span class="sxs-lookup"><span data-stu-id="5ab31-111">Pure transformations have no knowledge of or effect upon their environment.</span></span> <span data-ttu-id="5ab31-112">也就是说，用在转换中的函数没有负作用  。</span><span class="sxs-lookup"><span data-stu-id="5ab31-112">That is, the functions used in the transformation have no *side effects*.</span></span>

- <span data-ttu-id="5ab31-113">无状态  ，因而对相同输入执行相同的函数或特定的一组函数将始终产生相同的输出。</span><span class="sxs-lookup"><span data-stu-id="5ab31-113">*Stateless*, so that executing the same function or specific set of functions on the same input will always result in the same output.</span></span> <span data-ttu-id="5ab31-114">纯转换对于先前对它的使用没有记忆。</span><span class="sxs-lookup"><span data-stu-id="5ab31-114">Pure transformations have no memory of their prior use.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ab31-115">在本教程的其余部分，术语“纯函数”用于概括表示编程方法，而不是具体的语言功能。</span><span class="sxs-lookup"><span data-stu-id="5ab31-115">In the rest of this tutorial, the term "pure function" is used in a general sense to indicate a programming approach, and not a specific language feature.</span></span>
>
> <span data-ttu-id="5ab31-116">请注意，纯函数必须作为函数实现 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="5ab31-116">Note that pure functions must be implemented as functions in Visual Basic.</span></span>
>
> <span data-ttu-id="5ab31-117">此外，不要将纯函数与 C++ 中的纯虚方法混淆。</span><span class="sxs-lookup"><span data-stu-id="5ab31-117">Also, you should not confuse pure functions with pure virtual methods in C++.</span></span> <span data-ttu-id="5ab31-118">后者表示包含类是抽象的，并且不提供方法体。</span><span class="sxs-lookup"><span data-stu-id="5ab31-118">The latter indicates that the containing class is abstract and that no method body is supplied.</span></span>

### <a name="functional-programming"></a><span data-ttu-id="5ab31-119">函数编程</span><span class="sxs-lookup"><span data-stu-id="5ab31-119">Functional Programming</span></span>

<span data-ttu-id="5ab31-120">函数编程  是一种编程方法，直接支持纯函数转换。</span><span class="sxs-lookup"><span data-stu-id="5ab31-120">*Functional programming* is a programming approach that directly supports pure functional transformation.</span></span>

<span data-ttu-id="5ab31-121">学术团体对诸如 ML、Scheme、Haskell 和 F# 等通用函数编程语言一直抱有浓厚的兴趣。</span><span class="sxs-lookup"><span data-stu-id="5ab31-121">Historically, general-purpose functional programming languages, such as ML, Scheme, Haskell, and F#, have been primarily of interest to the academic community.</span></span> <span data-ttu-id="5ab31-122">尽管始终可以在 Visual Basic 中编写纯函数转换，但这样做的难度并未成为大多数程序员的诱人选项。</span><span class="sxs-lookup"><span data-stu-id="5ab31-122">Although it has always been possible to write pure functional transformations in Visual Basic, the difficulty of doing so has not made it an attractive option to most programmers.</span></span> <span data-ttu-id="5ab31-123">但在 Visual Basic 的更高版本中，诸如 lambda 表达式和类型推理这样的新语言构造使其功能编程更加简单、更高效。</span><span class="sxs-lookup"><span data-stu-id="5ab31-123">With later versions of Visual Basic, however, new language constructs such as lambda expressions and type inference make it functional programming much easier and more productive.</span></span>

<span data-ttu-id="5ab31-124">有关函数编程的详细信息，请参阅[函数编程与命令式编程（Visual Basic）](functional-programming-vs-imperative-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab31-124">For more information about functional programming, see [Functional Programming vs. Imperative Programming (Visual Basic)](functional-programming-vs-imperative-programming.md).</span></span>

#### <a name="domain-specific-fp-languages"></a><span data-ttu-id="5ab31-125">特定于域的 FP 语言</span><span class="sxs-lookup"><span data-stu-id="5ab31-125">Domain-Specific FP Languages</span></span>

<span data-ttu-id="5ab31-126">虽然通用函数编程语言并未得到广泛采用，但特定于域的函数编程语言却得到了较为成功的应用。</span><span class="sxs-lookup"><span data-stu-id="5ab31-126">Although general functional programming languages have not been widely adopted, specific domain-specific functional programming languages have had better success.</span></span> <span data-ttu-id="5ab31-127">例如，级联样式表 (CSS) 用于确定许多网页的外观，可扩展样式表转换语言 (XSLT) 样式表广泛应用于 XML 数据操作中。</span><span class="sxs-lookup"><span data-stu-id="5ab31-127">For example, Cascading Style Sheets (CSS) are used to determine the look and feel of many Web pages, and Extensible Stylesheet Language Transformations (XSLT) style sheets are used extensively in XML data manipulation.</span></span> <span data-ttu-id="5ab31-128">有关 XSLT 的详细信息，请参阅 [XSLT 转换](../../../../standard/data/xml/xslt-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab31-128">For more information about XSLT, see [XSLT Transformations](../../../../standard/data/xml/xslt-transformations.md).</span></span>

## <a name="terminology"></a><span data-ttu-id="5ab31-129">术语</span><span class="sxs-lookup"><span data-stu-id="5ab31-129">Terminology</span></span>

<span data-ttu-id="5ab31-130">下表定义了一些与函数转换相关的术语。</span><span class="sxs-lookup"><span data-stu-id="5ab31-130">The following table defines some terms related to functional transformations.</span></span>

<span data-ttu-id="5ab31-131">高阶（第一类）函数</span><span class="sxs-lookup"><span data-stu-id="5ab31-131">higher-order (first-class) function </span></span>\
<span data-ttu-id="5ab31-132">可作为编程对象的一种函数。</span><span class="sxs-lookup"><span data-stu-id="5ab31-132">A function that can be treated as a programmatic object.</span></span> <span data-ttu-id="5ab31-133">例如，高阶函数可以传递到其他函数或从其他函数返回。</span><span class="sxs-lookup"><span data-stu-id="5ab31-133">For example, a higher-order function can be passed to or returned from other functions.</span></span> <span data-ttu-id="5ab31-134">在 Visual Basic 中，委托和 lambda 表达式是支持高阶函数的语言功能。</span><span class="sxs-lookup"><span data-stu-id="5ab31-134">In Visual Basic, delegates and lambda expressions are language features that support higher-order functions.</span></span> <span data-ttu-id="5ab31-135">若要编写高阶函数，需要声明一个或多个自变量来接受委托，而在调用该函数时通常使用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="5ab31-135">To write a higher-order function, you declare one or more arguments to take delegates, and you often use lambda expressions when calling it.</span></span> <span data-ttu-id="5ab31-136">许多标准查询运算符都属于高阶函数。</span><span class="sxs-lookup"><span data-stu-id="5ab31-136">Many of the standard query operators are higher-order functions.</span></span>

<span data-ttu-id="5ab31-137">有关详细信息，请参阅[标准查询运算符概述（Visual Basic）](standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab31-137">For more information, see [Standard Query Operators Overview (Visual Basic)](standard-query-operators-overview.md).</span></span>

<span data-ttu-id="5ab31-138">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="5ab31-138">lambda expression </span></span>\
<span data-ttu-id="5ab31-139">实质上是一个匿名的内联函数，可用在任何需要委托类型的地方。</span><span class="sxs-lookup"><span data-stu-id="5ab31-139">Essentially, an inline anonymous function that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="5ab31-140">这是对 lambda 表达式的一个简化的定义，但足以满足本教程的需要。</span><span class="sxs-lookup"><span data-stu-id="5ab31-140">This is a simplified definition of lambda expressions, but it is adequate for the purposes of this tutorial.</span></span>

<span data-ttu-id="5ab31-141">有关 Lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab31-141">For more information about, see [Lambda Expressions](../../language-features/procedures/lambda-expressions.md).</span></span>

<span data-ttu-id="5ab31-142">集合</span><span class="sxs-lookup"><span data-stu-id="5ab31-142">collection </span></span>\
<span data-ttu-id="5ab31-143">结构化的一组数据，通常具有统一的类型。</span><span class="sxs-lookup"><span data-stu-id="5ab31-143">A structured set of data, usually of a uniform type.</span></span> <span data-ttu-id="5ab31-144">若要与 LINQ 兼容，集合必须实现 <xref:System.Collections.IEnumerable> 接口或 <xref:System.Linq.IQueryable> 接口（或它们对应的泛型接口 <xref:System.Collections.Generic.IEnumerator%601> 或 <xref:System.Linq.IQueryable%601> 之一）。</span><span class="sxs-lookup"><span data-stu-id="5ab31-144">To be compatible with LINQ, a collection must implement the <xref:System.Collections.IEnumerable> interface or the <xref:System.Linq.IQueryable> interface (or one of their generic counterparts, <xref:System.Collections.Generic.IEnumerator%601> or <xref:System.Linq.IQueryable%601>).</span></span>

<span data-ttu-id="5ab31-145">元组（匿名类型）</span><span class="sxs-lookup"><span data-stu-id="5ab31-145">tuple (anonymous types) </span></span>\
<span data-ttu-id="5ab31-146">一个数学概念，元组是一个有限的对象序列，每个对象具有特定的类型。</span><span class="sxs-lookup"><span data-stu-id="5ab31-146">A mathematical concept, a tuple is a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="5ab31-147">元组也称为有序列表。</span><span class="sxs-lookup"><span data-stu-id="5ab31-147">A tuple is also known as an ordered list.</span></span> <span data-ttu-id="5ab31-148">匿名类型是此概念的语言实现，支持在声明未命名类类型的同时实例化该类型的对象。</span><span class="sxs-lookup"><span data-stu-id="5ab31-148">Anonymous types are a language implementation of this concept, which enable an unnamed class type to be declared and an object of that type to be instantiated at the same time.</span></span>

<span data-ttu-id="5ab31-149">有关详细信息，请参阅[匿名类型](../../language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab31-149">For more information, see  [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

<span data-ttu-id="5ab31-150">类型推理（隐式确定类型）</span><span class="sxs-lookup"><span data-stu-id="5ab31-150">type inference (implicit typing) </span></span>\
<span data-ttu-id="5ab31-151">在没有显式类型声明的情况下编译器确定变量类型的能力。</span><span class="sxs-lookup"><span data-stu-id="5ab31-151">The ability of a compiler to determine the type of a variable in the absence of an explicit type declaration.</span></span>

<span data-ttu-id="5ab31-152">有关详细信息，请参阅[局部类型推理](../../language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab31-152">For more information, see [Local Type Inference](../../language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="5ab31-153">延迟执行和迟缓计算</span><span class="sxs-lookup"><span data-stu-id="5ab31-153">deferred execution and lazy evaluation </span></span>\
<span data-ttu-id="5ab31-154">延迟表达式的计算，直到实际需要它的求解值。</span><span class="sxs-lookup"><span data-stu-id="5ab31-154">The delaying of evaluation of an expression until its resolved value is actually required.</span></span> <span data-ttu-id="5ab31-155">集合中支持延迟执行。</span><span class="sxs-lookup"><span data-stu-id="5ab31-155">Deferred execution is supported in collections.</span></span>

<span data-ttu-id="5ab31-156">有关详细信息，请参阅[基本查询操作（Visual Basic）](basic-query-operations.md)和[LINQ to XML 中的延迟执行和迟缓计算（Visual Basic）](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab31-156">For more information, see [Basic Query Operations (Visual Basic)](basic-query-operations.md) and [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="5ab31-157">本节各处的代码示例中将使用这些语言功能。</span><span class="sxs-lookup"><span data-stu-id="5ab31-157">These language features will be used in code samples throughout this section.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ab31-158">请参阅</span><span class="sxs-lookup"><span data-stu-id="5ab31-158">See also</span></span>

- [<span data-ttu-id="5ab31-159">纯功能转换简介（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5ab31-159">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="5ab31-160">函数编程与命令式编程（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5ab31-160">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](functional-programming-vs-imperative-programming.md)
