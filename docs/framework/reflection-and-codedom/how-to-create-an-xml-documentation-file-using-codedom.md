---
title: 如何：使用 CodeDOM 创建 XML 文档文件
description: 在此详细示例中，了解如何使用代码文档对象模型 (CodeDOM) 生成用于创建 XML 文档文件的代码。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
ms.openlocfilehash: f905b996910c6cfbc62378cc4cd6bb8c0e0e6fd4
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865146"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="4a373-103">如何：使用 CodeDOM 创建 XML 文档文件</span><span class="sxs-lookup"><span data-stu-id="4a373-103">How to: Create an XML documentation file using CodeDOM</span></span>

<span data-ttu-id="4a373-104">可使用 CodeDOM 创建生成 XML 文档的代码。</span><span class="sxs-lookup"><span data-stu-id="4a373-104">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="4a373-105">该进程包括创建包含 XML 文档注释的 CodeDOM 图、生成代码和通过创建 XML 文档输出的编译器选项编译生成的代码。</span><span class="sxs-lookup"><span data-stu-id="4a373-105">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
## <a name="create-a-codedom-graph"></a><span data-ttu-id="4a373-106">创建 CodeDOM 图</span><span class="sxs-lookup"><span data-stu-id="4a373-106">Create a CodeDOM graph</span></span>
  
1. <span data-ttu-id="4a373-107">为示例应用程序创建包含 CodeDOM 图的 <xref:System.CodeDom.CodeCompileUnit>。</span><span class="sxs-lookup"><span data-stu-id="4a373-107">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2. <span data-ttu-id="4a373-108">使用 <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> 构造函数（`docComment` 参数设置为 `true`）创建 XML 文档注释元素和文本。</span><span class="sxs-lookup"><span data-stu-id="4a373-108">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="4a373-109">从 CodeCompileUnit 生成代码</span><span class="sxs-lookup"><span data-stu-id="4a373-109">Generate the code from the CodeCompileUnit</span></span>
  
1. <span data-ttu-id="4a373-110">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 方法生成代码并创建要编译的源文件。</span><span class="sxs-lookup"><span data-stu-id="4a373-110">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="4a373-111">编译代码并生成文档文件</span><span class="sxs-lookup"><span data-stu-id="4a373-111">Compile the code and generate the documentation file</span></span>
  
1. <span data-ttu-id="4a373-112">将 /doc 编译器选项添加到 <xref:System.CodeDom.Compiler.CompilerParameters> 对象的 <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> 属性中，然后将该对象传递给 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> 方法，以便在编译代码时创建 XML 文档文件。</span><span class="sxs-lookup"><span data-stu-id="4a373-112">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="4a373-113">示例</span><span class="sxs-lookup"><span data-stu-id="4a373-113">Example</span></span>

<span data-ttu-id="4a373-114">以下代码示例创建一个包含文档注释的 CodeDOM 图，从该图生成一个代码文件，然后编译该文件并创建一个关联的 XML 文档文件。</span><span class="sxs-lookup"><span data-stu-id="4a373-114">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="4a373-115">该代码示例在 HelloWorldDoc.xml 文件中创建以下 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="4a373-115">The code example creates the following XML documentation in the *HelloWorldDoc.xml* file.</span></span>  
  
```xml  
<?xml version="1.0" ?>
<doc>  
  <assembly>  
    <name>HelloWorld</name>
  </assembly>  
  <members>  
    <member name="T:Samples.Class1">  
      <summary>  
        Create a Hello World application.
      </summary>
      <seealso cref="M:Samples.Class1.Main" />
    </member>  
    <member name="M:Samples.Class1.Main">  
      <summary>  
        Main method for HelloWorld application.
        <para>Add a new paragraph to the description.</para>
      </summary>  
    </member>  
  </members>  
</doc>  
```  
  
## <a name="compile-permissions"></a><span data-ttu-id="4a373-116">编译权限</span><span class="sxs-lookup"><span data-stu-id="4a373-116">Compile permissions</span></span>
  
<span data-ttu-id="4a373-117">需要 `FullTrust` 权限集才可成功执行此代码示例。</span><span class="sxs-lookup"><span data-stu-id="4a373-117">This code example requires the `FullTrust` permission set to execute successfully.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4a373-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="4a373-118">See also</span></span>

- [<span data-ttu-id="4a373-119">使用 XML 记录代码 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a373-119">Document your code with XML (Visual Basic)</span></span>](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="4a373-120">XML 文档注释</span><span class="sxs-lookup"><span data-stu-id="4a373-120">XML documentation comments</span></span>](../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="4a373-121">XML 文档 (C++)</span><span class="sxs-lookup"><span data-stu-id="4a373-121">XML documentation (C++)</span></span>](/cpp/ide/xml-documentation-visual-cpp)
