---
title: 使用 CodeDom
description: 使用代码文档对象模型 (CodeDOM) 来组合对象图，该模型提供表示多种常见源代码元素的类型。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
ms.openlocfilehash: 476d8c18f386f889855c664147b1ee20995dc6f9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865211"
---
# <a name="using-the-codedom"></a><span data-ttu-id="bd262-103">使用 CodeDom</span><span class="sxs-lookup"><span data-stu-id="bd262-103">Using the CodeDOM</span></span>
<span data-ttu-id="bd262-104">CodeDOM 提供表示多种常见源代码元素的类型。</span><span class="sxs-lookup"><span data-stu-id="bd262-104">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="bd262-105">可以设计一个程序，它使用 CodeDOM 元素生成源代码模型来组合对象图。</span><span class="sxs-lookup"><span data-stu-id="bd262-105">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="bd262-106">对于支持的编程语言，可使用 CodeDOM 代码生成器将此对象图呈现为源代码。</span><span class="sxs-lookup"><span data-stu-id="bd262-106">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="bd262-107">还可使用 CodeDOM 将源代码编译为二进制程序集。</span><span class="sxs-lookup"><span data-stu-id="bd262-107">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="bd262-108">CodeDOM 的常见用途包括：</span><span class="sxs-lookup"><span data-stu-id="bd262-108">Some common uses for the CodeDOM include:</span></span>  
  
- <span data-ttu-id="bd262-109">模板化代码生成：生成适用于 ASP.NET、XML Web 服务客户端代理、代码向导、设计器或其他代码发出机制的代码。</span><span class="sxs-lookup"><span data-stu-id="bd262-109">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
- <span data-ttu-id="bd262-110">动态编译：支持一种或多种语言的代码编译。</span><span class="sxs-lookup"><span data-stu-id="bd262-110">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="bd262-111">生成 CodeDOM 图</span><span class="sxs-lookup"><span data-stu-id="bd262-111">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="bd262-112"><xref:System.CodeDom> 命名空间提供用于表示源代码逻辑结构的类，独立于语言语法。</span><span class="sxs-lookup"><span data-stu-id="bd262-112">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="bd262-113">CodeDOM 图的结构</span><span class="sxs-lookup"><span data-stu-id="bd262-113">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="bd262-114">CodeDOM 图的结构类似于一个容器树。</span><span class="sxs-lookup"><span data-stu-id="bd262-114">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="bd262-115">每个可编译 CodeDOM 图的顶端容器或根部容器是 <xref:System.CodeDom.CodeCompileUnit>。</span><span class="sxs-lookup"><span data-stu-id="bd262-115">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="bd262-116">源代码模型中的每个元素都必须通过图中 <xref:System.CodeDom.CodeObject> 的属性链接至该图。</span><span class="sxs-lookup"><span data-stu-id="bd262-116">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="bd262-117">为示例 Hello World 程序生成源代码模型</span><span class="sxs-lookup"><span data-stu-id="bd262-117">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="bd262-118">下列演练提供如何生成 CodeDOM 对象图的示例，用以表示简单 Hello World 应用程序的代码。</span><span class="sxs-lookup"><span data-stu-id="bd262-118">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="bd262-119">有关此代码示例的完整源代码，请参阅 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 主题。</span><span class="sxs-lookup"><span data-stu-id="bd262-119">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="bd262-120">创建编译单元</span><span class="sxs-lookup"><span data-stu-id="bd262-120">Creating a compile unit</span></span>  
 <span data-ttu-id="bd262-121">CodeDOM 定义名为 <xref:System.CodeDom.CodeCompileUnit> 的对象，可引用 CodeDOM 对象图，该对象图塑造要编译的源代码的模型。</span><span class="sxs-lookup"><span data-stu-id="bd262-121">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="bd262-122">CodeCompileUnit 具有属性可用于存储对特性、命名空间和程序集的引用  。</span><span class="sxs-lookup"><span data-stu-id="bd262-122">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="bd262-123">派生自 <xref:System.CodeDom.Compiler.CodeDomProvider> 类的 CodeDom 提供程序包含处理 CodeCompileUnit 所引用的对象图的方法  。</span><span class="sxs-lookup"><span data-stu-id="bd262-123">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="bd262-124">若要为简单应用程序创建对象图，必须组合源代码模型，并通过 CodeCompileUnit 将其引用  。</span><span class="sxs-lookup"><span data-stu-id="bd262-124">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="bd262-125">可使用下例所示的语法来创建新的编译单元：</span><span class="sxs-lookup"><span data-stu-id="bd262-125">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="bd262-126"><xref:System.CodeDom.CodeSnippetCompileUnit> 可以包含已采用目标语言的源代码的一部分，但无法呈现为另一语言。</span><span class="sxs-lookup"><span data-stu-id="bd262-126">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="bd262-127">定义命名空间</span><span class="sxs-lookup"><span data-stu-id="bd262-127">Defining a namespace</span></span>  
 <span data-ttu-id="bd262-128">若要定义命名空间，请创建 <xref:System.CodeDom.CodeNamespace>，并使用适当的构造函数或设置其 Name 属性来为其分配名称  。</span><span class="sxs-lookup"><span data-stu-id="bd262-128">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="bd262-129">导入命名空间</span><span class="sxs-lookup"><span data-stu-id="bd262-129">Importing a namespace</span></span>  
 <span data-ttu-id="bd262-130">若要向命名空间添加命名空间导入指令，请添加 <xref:System.CodeDom.CodeNamespaceImport>，指示将命名空间导入 CodeNamespace.Imports 集合  。</span><span class="sxs-lookup"><span data-stu-id="bd262-130">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="bd262-131">下列代码添加导入，用于将 System 命名空间导入名为 `samples` 的 CodeNamespace 的 Imports 集合中    ：</span><span class="sxs-lookup"><span data-stu-id="bd262-131">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="bd262-132">将代码元素链接至对象图</span><span class="sxs-lookup"><span data-stu-id="bd262-132">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="bd262-133">形成 CodeDOM 图的所有代码元素都必须链接至作为树的根元素的 <xref:System.CodeDom.CodeCompileUnit>，方法是通过一系列直接引用自该图根对象属性的元素之间的引用。</span><span class="sxs-lookup"><span data-stu-id="bd262-133">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="bd262-134">将对象设置为容器对象的属性，以建立来自容器对象的引用。</span><span class="sxs-lookup"><span data-stu-id="bd262-134">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="bd262-135">下列语句将 `samples` CodeNamespace  添加至根 CodeCompileUnit  的 Namespaces  集合属性。</span><span class="sxs-lookup"><span data-stu-id="bd262-135">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="bd262-136">定义类型</span><span class="sxs-lookup"><span data-stu-id="bd262-136">Defining a type</span></span>  
 <span data-ttu-id="bd262-137">若要使用 CodeDOM 声明类、结构、接口或枚举，请创建新的 <xref:System.CodeDom.CodeTypeDeclaration>，然后为其分配名称。</span><span class="sxs-lookup"><span data-stu-id="bd262-137">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="bd262-138">下列示例使用构造函数重载来设置 Name 属性对此进行了演示  ：</span><span class="sxs-lookup"><span data-stu-id="bd262-138">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="bd262-139">若要向命名空间添加类型，请将代表要添加到命名空间的类型的 <xref:System.CodeDom.CodeTypeDeclaration> 添加到 CodeNamespace 的 Types 集合   。</span><span class="sxs-lookup"><span data-stu-id="bd262-139">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="bd262-140">下列示例演示如何向名为 `samples` 的 CodeNamespace 添加名为 `class1` 的类  ：</span><span class="sxs-lookup"><span data-stu-id="bd262-140">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="bd262-141">将类成员添加到类</span><span class="sxs-lookup"><span data-stu-id="bd262-141">Adding class members to a class</span></span>  
 <span data-ttu-id="bd262-142"><xref:System.CodeDom> 命名空间提供多种可用于表示类成员的元素。</span><span class="sxs-lookup"><span data-stu-id="bd262-142">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="bd262-143">每个类成员都可添加到 <xref:System.CodeDom.CodeTypeDeclaration> 的 Members 集合  。</span><span class="sxs-lookup"><span data-stu-id="bd262-143">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="bd262-144">为可执行程序定义代码入口点方法</span><span class="sxs-lookup"><span data-stu-id="bd262-144">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="bd262-145">若正在为可执行程序生成代码，则务必创建 <xref:System.CodeDom.CodeEntryPointMethod> 来表示应开始程序执行的方法，以指示程序的入口点。</span><span class="sxs-lookup"><span data-stu-id="bd262-145">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="bd262-146">下列示例演示如何定义入口点方法，该方法包含 <xref:System.CodeDom.CodeMethodInvokeExpression> 来调用 System.Console.WriteLine 以打印“Hello World!”  ：</span><span class="sxs-lookup"><span data-stu-id="bd262-146">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="bd262-147">下列语句向 `class1` 的 Members 集合添加名为 `Start` 的入口点方法  ：</span><span class="sxs-lookup"><span data-stu-id="bd262-147">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="bd262-148">现在，名为 `compileUnit` 的 <xref:System.CodeDom.CodeCompileUnit> 包含用于简单 Hello World 程序的 CodeDOM 图。</span><span class="sxs-lookup"><span data-stu-id="bd262-148">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="bd262-149">有关从 CodeDOM 图生成和编译代码的信息，请参阅[从 CodeDOM 图生成源代码并编译程序](generating-and-compiling-source-code-from-a-codedom-graph.md)。</span><span class="sxs-lookup"><span data-stu-id="bd262-149">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="bd262-150">有关生成 CodeDOM 图的详细信息</span><span class="sxs-lookup"><span data-stu-id="bd262-150">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="bd262-151">CodeDOM 支持多种常见的代码元素，可用于支持公共语言运行时的编程语言。</span><span class="sxs-lookup"><span data-stu-id="bd262-151">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="bd262-152">CodeDOM 不是为了提供可表示所有可能的编程语言功能的元素。</span><span class="sxs-lookup"><span data-stu-id="bd262-152">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="bd262-153">可在 <xref:System.CodeDom.CodeSnippetExpression>、<xref:System.CodeDom.CodeSnippetStatement>、<xref:System.CodeDom.CodeSnippetTypeMember> 或 <xref:System.CodeDom.CodeSnippetCompileUnit> 中封装无法通过 CodeDOM 元素轻易表示的代码。</span><span class="sxs-lookup"><span data-stu-id="bd262-153">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="bd262-154">但是，CodeDOM 无法自动将代码片段转换为其他语言。</span><span class="sxs-lookup"><span data-stu-id="bd262-154">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="bd262-155">有关各种 CodeDOM 类型的文档，请参阅 <xref:System.CodeDom> 命名空间的参考文档。</span><span class="sxs-lookup"><span data-stu-id="bd262-155">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="bd262-156">有关用于查找表示特定代码元素类型的 CodeDOM 元素的快速图表，请参阅 [CodeDOM 快速参考](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="bd262-156">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span></span>
