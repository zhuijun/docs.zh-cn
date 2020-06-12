---
title: 正则表达式中的编译和重复使用
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET Framework regular expressions, engines
- .NET Framework regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
ms.openlocfilehash: 54f14a4f31bef00dd222686cc523935b2d9dd5fa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279033"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a><span data-ttu-id="f1c98-102">正则表达式中的编译和重复使用</span><span class="sxs-lookup"><span data-stu-id="f1c98-102">Compilation and Reuse in Regular Expressions</span></span>
<span data-ttu-id="f1c98-103">通过了解正则表达式引擎编译表达式的方式以及正则表达式的缓存方式，可以优化大量使用正则表达式的应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="f1c98-103">You can optimize the performance of applications that make extensive use of regular expressions by understanding how the regular expression engine compiles expressions and by understanding how regular expressions are cached.</span></span> <span data-ttu-id="f1c98-104">本主题介绍编译和缓存。</span><span class="sxs-lookup"><span data-stu-id="f1c98-104">This topic discusses both compilation and caching.</span></span>  
  
## <a name="compiled-regular-expressions"></a><span data-ttu-id="f1c98-105">已编译的正则表达式</span><span class="sxs-lookup"><span data-stu-id="f1c98-105">Compiled Regular Expressions</span></span>  
 <span data-ttu-id="f1c98-106">默认情况下，正则表达式引擎将正则表达式编译成内部指令序列（这些指令序列是不同于 Microsoft 中间语言 (MSIL) 的高级代码）。</span><span class="sxs-lookup"><span data-stu-id="f1c98-106">By default, the regular expression engine compiles a regular expression to a sequence of internal instructions (these are high-level codes that are different from Microsoft intermediate language, or MSIL).</span></span> <span data-ttu-id="f1c98-107">当引擎执行正则表达式时，会解释内部代码。</span><span class="sxs-lookup"><span data-stu-id="f1c98-107">When the engine executes a regular expression, it interprets the internal codes.</span></span>  
  
 <span data-ttu-id="f1c98-108">如果 <xref:System.Text.RegularExpressions.Regex> 对象是通过 <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> 选项构造而成，它会将正则表达式编译为显式 MSIL 代码，而不是高级正则表达式内部指令。</span><span class="sxs-lookup"><span data-stu-id="f1c98-108">If a <xref:System.Text.RegularExpressions.Regex> object is constructed with the <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> option, it compiles the regular expression to explicit MSIL code instead of high-level regular expression internal instructions.</span></span> <span data-ttu-id="f1c98-109">这样，.NET 的实时 (JIT) 编译器便可以将表达式转换为本机代码以获得更高的性能。</span><span class="sxs-lookup"><span data-stu-id="f1c98-109">This allows .NET's just-in-time (JIT) compiler to convert the expression to native machine code for higher performance.</span></span>  <span data-ttu-id="f1c98-110">构造 <xref:System.Text.RegularExpressions.Regex> 对象的成本可能会更高，但执行其匹配项的开销可能会小得多。</span><span class="sxs-lookup"><span data-stu-id="f1c98-110">The cost of constructing the <xref:System.Text.RegularExpressions.Regex> object may be higher, but the cost of performing matches with it is likely to be much smaller.</span></span>

 <span data-ttu-id="f1c98-111">替换方法是，使用预编译正则表达式。</span><span class="sxs-lookup"><span data-stu-id="f1c98-111">An alternative is to use precompiled regular expressions.</span></span> <span data-ttu-id="f1c98-112">可以使用 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> 方法，将所有表达式都编译到可重用的 DLL 中。</span><span class="sxs-lookup"><span data-stu-id="f1c98-112">You can compile all of your expressions into a reusable DLL by using the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> method.</span></span> <span data-ttu-id="f1c98-113">这样一来，就无需在运行时编译，同时还仍受益于已编译正则表达式的速度优势。</span><span class="sxs-lookup"><span data-stu-id="f1c98-113">This avoids the need to compile at run time while still benefiting from the speed of compiled regular expressions.</span></span>  
  
## <a name="the-regular-expressions-cache"></a><span data-ttu-id="f1c98-114">正则表达式缓存</span><span class="sxs-lookup"><span data-stu-id="f1c98-114">The Regular Expressions Cache</span></span>  
 <span data-ttu-id="f1c98-115">为了提高性能，正则表达式引擎为已编译的正则表达式维护了一个应用程序范围的缓存。</span><span class="sxs-lookup"><span data-stu-id="f1c98-115">To improve performance, the regular expression engine maintains an application-wide cache of compiled regular expressions.</span></span> <span data-ttu-id="f1c98-116">该缓存只存储静态方法调用中使用的正则表达式模式。</span><span class="sxs-lookup"><span data-stu-id="f1c98-116">The cache stores regular expression patterns that are used only in static method calls.</span></span> <span data-ttu-id="f1c98-117">（不缓存提供给实例方法的正则表达式模式。）这样，在每次使用正则表达式时，就无需将正则表达式重新分析成高级字节代码。</span><span class="sxs-lookup"><span data-stu-id="f1c98-117">(Regular expression patterns supplied to instance methods are not cached.) This avoids the need to reparse an expression into high-level byte code each time it is used.</span></span>  
  
 <span data-ttu-id="f1c98-118">缓存正则表达式数上限由 `static`（Visual Basic 中的 `Shared`）<xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> 属性的值决定。</span><span class="sxs-lookup"><span data-stu-id="f1c98-118">The maximum number of cached regular expressions is determined by the value of the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f1c98-119">默认情况下，正则表达式引擎最多可缓存 15 个已编译的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="f1c98-119">By default, the regular expression engine caches up to 15 compiled regular expressions.</span></span> <span data-ttu-id="f1c98-120">如果已编译正则表达式的数目超过缓存大小，则丢弃最早使用的正则表达式并缓存新的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="f1c98-120">If the number of compiled regular expressions exceeds the cache size, the least recently used regular expression is discarded and the new regular expression is cached.</span></span>  
  
 <span data-ttu-id="f1c98-121">应用程序可通过以下两种方式之一来重用正则表达式：</span><span class="sxs-lookup"><span data-stu-id="f1c98-121">Your application can reuse regular expressions in one of the following two ways:</span></span>  
  
- <span data-ttu-id="f1c98-122">使用 <xref:System.Text.RegularExpressions.Regex> 对象的静态方法定义正则表达式。</span><span class="sxs-lookup"><span data-stu-id="f1c98-122">By using a static method of the <xref:System.Text.RegularExpressions.Regex> object to define the regular expression.</span></span> <span data-ttu-id="f1c98-123">如果要使用的正则表达式模式已由其他静态方法调用定义，则正则表达式引擎将尝试从缓存中检索该模式。</span><span class="sxs-lookup"><span data-stu-id="f1c98-123">If you're using a regular expression pattern that has already been defined by another static method call, the regular expression engine will try to retrieve it from the cache.</span></span> <span data-ttu-id="f1c98-124">如果它在缓存中不可用，则引擎将编译正则表达式并将其添加到缓存中。</span><span class="sxs-lookup"><span data-stu-id="f1c98-124">If it's not available in the cache, the engine will compile the regular expression and add it to the cache.</span></span>
  
- <span data-ttu-id="f1c98-125">重用现有 <xref:System.Text.RegularExpressions.Regex> 对象（只要需要使用正则表达式模式）。</span><span class="sxs-lookup"><span data-stu-id="f1c98-125">By reusing an existing <xref:System.Text.RegularExpressions.Regex> object as long as its regular expression pattern is needed.</span></span>  
  
 <span data-ttu-id="f1c98-126">鉴于对象实例化和正则表达式编译产生的开销，因此创建并迅速销毁大量 <xref:System.Text.RegularExpressions.Regex> 对象的进程成本非常高。</span><span class="sxs-lookup"><span data-stu-id="f1c98-126">Because of the overhead of object instantiation and regular expression compilation, creating and rapidly destroying numerous <xref:System.Text.RegularExpressions.Regex> objects is a very expensive process.</span></span> <span data-ttu-id="f1c98-127">对于使用大量不同正则表达式的应用，可以调用静态方法 `Regex`，并尽量增加正则表达式缓存大小，从而优化性能。</span><span class="sxs-lookup"><span data-stu-id="f1c98-127">For applications that use a large number of different regular expressions, you can optimize performance by using calls to static `Regex` methods and possibly by increasing the size of the regular expression cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c98-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="f1c98-128">See also</span></span>

- [<span data-ttu-id="f1c98-129">.NET 正则表达式</span><span class="sxs-lookup"><span data-stu-id="f1c98-129">.NET Regular Expressions</span></span>](regular-expressions.md)
