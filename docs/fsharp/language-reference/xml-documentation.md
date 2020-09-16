---
title: XML 文档
description: '了解有关 F # 的支持，以便从注释生成文档。'
ms.date: 09/15/2020
ms.openlocfilehash: a5bec20f27c23caee951cda2dc5d17808f69d384
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679398"
---
# <a name="document-your-code-with-xml-comments"></a><span data-ttu-id="f478d-103">使用 XML 注释记录代码</span><span class="sxs-lookup"><span data-stu-id="f478d-103">Document your code with XML comments</span></span>

<span data-ttu-id="f478d-104">可以在 F # 中生成三斜杠 (///) 代码注释中的文档。</span><span class="sxs-lookup"><span data-stu-id="f478d-104">You can produce documentation from triple-slash (///) code comments in F#.</span></span> <span data-ttu-id="f478d-105">XML 注释可以在代码文件中的声明之前 () 或签名 ( fsi.exe) 文件中。</span><span class="sxs-lookup"><span data-stu-id="f478d-105">XML comments can precede declarations in code files (.fs) or signature (.fsi) files.</span></span>

<span data-ttu-id="f478d-106">XML 文档注释是一种特殊注释，添加在任何用户定义的类型或成员的定义上方。</span><span class="sxs-lookup"><span data-stu-id="f478d-106">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="f478d-107">其特殊之处在于其可由编译器处理，由此在编译时生成 XML 文档文件。</span><span class="sxs-lookup"><span data-stu-id="f478d-107">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="f478d-108">编译器生成的 XML 文件可以与 .NET 程序集一起分发，以便 Ide 可以使用工具提示来显示关于类型或成员的快速信息。</span><span class="sxs-lookup"><span data-stu-id="f478d-108">The compiler-generated XML file can be distributed alongside your .NET assembly so that IDEs can use tooltips to show quick information about types or members.</span></span> <span data-ttu-id="f478d-109">此外，可以通过 [fsdocs](http://fsprojects.github.io/FSharp.Formatting/) 等工具运行 XML 文件，以生成 API 参考网站。</span><span class="sxs-lookup"><span data-stu-id="f478d-109">Additionally, the XML file can be run through tools like [fsdocs](http://fsprojects.github.io/FSharp.Formatting/) to generate API reference websites.</span></span>

<span data-ttu-id="f478d-110">编译器将忽略 XML 文档注释，就像所有其他注释一样，除非启用下述选项，以在编译时检查注释的有效性和完整性。</span><span class="sxs-lookup"><span data-stu-id="f478d-110">XML documentation comments, like all other comments, are ignored by the compiler, unless the options described below are enabled to check the validity and completeness of comments at compile-time.</span></span>

<span data-ttu-id="f478d-111">可通过执行下列操作之一在编译时生成 XML 文件：</span><span class="sxs-lookup"><span data-stu-id="f478d-111">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="f478d-112">可以将元素添加 `GenerateDocumentationFile` 到 `<PropertyGroup>` 项目文件的部分中 `.fsproj` ，这会在项目目录中生成一个 XML 文件，该文件与程序集具有相同的根文件名。</span><span class="sxs-lookup"><span data-stu-id="f478d-112">You can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your `.fsproj` project file, which generates an XML file in the project directory with the same root filename as the assembly.</span></span> <span data-ttu-id="f478d-113">例如：</span><span class="sxs-lookup"><span data-stu-id="f478d-113">For example:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

- <span data-ttu-id="f478d-114">如果使用 Visual Studio 开发应用程序，右键单击项目并选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="f478d-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="f478d-115">在属性对话框中，选择“生成”  选项卡，然后选中“XML 文档文件”  。</span><span class="sxs-lookup"><span data-stu-id="f478d-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="f478d-116">还可以更改编译器写入文件的位置。</span><span class="sxs-lookup"><span data-stu-id="f478d-116">You can also change the location to which the compiler writes the file.</span></span>

<span data-ttu-id="f478d-117">可以通过两种方式编写 XML 文档注释：带和不带 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="f478d-117">There are two ways to write XML documentation comments: with and without XML tags.</span></span> <span data-ttu-id="f478d-118">两者都使用三斜杠注释。</span><span class="sxs-lookup"><span data-stu-id="f478d-118">Both use triple-slash comments.</span></span>

## <a name="comments-without-xml-tags"></a><span data-ttu-id="f478d-119">无 XML 标记的注释</span><span class="sxs-lookup"><span data-stu-id="f478d-119">Comments without XML tags</span></span>

<span data-ttu-id="f478d-120">如果 `///` 注释未以开头，则 `<` 整个注释文本将被视为紧随其后的代码构造的摘要文档。</span><span class="sxs-lookup"><span data-stu-id="f478d-120">If a `///` comment does not start with a `<` then the entire comment text is taken as the summary documentation for the code construct that immediately follows.</span></span> <span data-ttu-id="f478d-121">如果只想编写每个构造的简短摘要，请使用此方法。</span><span class="sxs-lookup"><span data-stu-id="f478d-121">Use this method when you want to write only a brief summary for each construct.</span></span>

<span data-ttu-id="f478d-122">文档准备期间，注释将编码为 XML，因此等字符 `<` `>` 和 `&` 无需转义。</span><span class="sxs-lookup"><span data-stu-id="f478d-122">The comment is encoded to XML during documentation preparation, so characters such as `<`, `>` and `&` need not be escaped.</span></span> <span data-ttu-id="f478d-123">如果未显式指定摘要标记，则不应指定其他标记，如 **param** 或 **返回** 标记。</span><span class="sxs-lookup"><span data-stu-id="f478d-123">If you don't specify a summary tag explicitly, you should not specify other tags, such as **param** or **returns** tags.</span></span>

<span data-ttu-id="f478d-124">下面的示例显示了不带 XML 标记的替代方法。</span><span class="sxs-lookup"><span data-stu-id="f478d-124">The following example shows the alternative method, without XML tags.</span></span> <span data-ttu-id="f478d-125">在此示例中，注释中的整个文本都被视为一个摘要。</span><span class="sxs-lookup"><span data-stu-id="f478d-125">In this example, the entire text in the comment is considered a summary.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="comments-with-xml-tags"></a><span data-ttu-id="f478d-126">带有 XML 标记的注释</span><span class="sxs-lookup"><span data-stu-id="f478d-126">Comments with XML tags</span></span>

<span data-ttu-id="f478d-127">如果注释正文以 `<` (正常开始 `<summary>`) 则使用 xml 标记将其视为 xml 格式的注释正文。</span><span class="sxs-lookup"><span data-stu-id="f478d-127">If a comment body begins with `<` (normally `<summary>`) then it is treated as an XML formatted comment body using XML tags.</span></span> <span data-ttu-id="f478d-128">使用此第二个参数，您可以为简短摘要、附加备注、每个参数和类型参数的文档和所引发的异常以及对返回值的说明单独指定备注。</span><span class="sxs-lookup"><span data-stu-id="f478d-128">This second enables you to specify separate notes for a short summary, additional remarks, documentation for each parameter and type parameter and exceptions thrown, and a description of the return value.</span></span>

<span data-ttu-id="f478d-129">下面是签名文件中的典型 XML 文档注释：</span><span class="sxs-lookup"><span data-stu-id="f478d-129">The following is a typical XML documentation comment in a signature file:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="recommended-tags"></a><span data-ttu-id="f478d-130">建议的标记</span><span class="sxs-lookup"><span data-stu-id="f478d-130">Recommended Tags</span></span>

<span data-ttu-id="f478d-131">如果使用的是 XML 标记，下表描述了在 F # XML 代码注释中识别的外部标记。</span><span class="sxs-lookup"><span data-stu-id="f478d-131">If you are using XML tags, the following table describes the outer tags recognized in F# XML code comments.</span></span>

| <span data-ttu-id="f478d-132">标记语法</span><span class="sxs-lookup"><span data-stu-id="f478d-132">Tag syntax</span></span>                                  | <span data-ttu-id="f478d-133">说明</span><span class="sxs-lookup"><span data-stu-id="f478d-133">Description</span></span> |
|---------------------------------------------|-----------|
| <span data-ttu-id="f478d-134">`<summary>`**_全文_**`</summary>`</span><span class="sxs-lookup"><span data-stu-id="f478d-134">`<summary>`**_text_**`</summary>`</span></span>           | <span data-ttu-id="f478d-135">指定 *文本* 为程序元素的简短说明。</span><span class="sxs-lookup"><span data-stu-id="f478d-135">Specifies that *text* is a brief description of the program element.</span></span> <span data-ttu-id="f478d-136">描述通常是一两个句子。</span><span class="sxs-lookup"><span data-stu-id="f478d-136">The description is usually one or two sentences.</span></span>|
| <span data-ttu-id="f478d-137">`<remarks>`**_全文_**`</remarks>`</span><span class="sxs-lookup"><span data-stu-id="f478d-137">`<remarks>`**_text_**`</remarks>`</span></span>           | <span data-ttu-id="f478d-138">指定 *文本* 包含有关程序元素的补充信息。</span><span class="sxs-lookup"><span data-stu-id="f478d-138">Specifies that *text* contains supplementary information about the program element.</span></span>|
| <span data-ttu-id="f478d-139">`<param name="`**_名称_** `">`**_描述_**`</param>`</span><span class="sxs-lookup"><span data-stu-id="f478d-139">`<param name="`**_name_**`">`**_description_**`</param>`</span></span> | <span data-ttu-id="f478d-140">指定函数或方法参数的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="f478d-140">Specifies the name and description for a function or method parameter.</span></span>|
| <span data-ttu-id="f478d-141">`<typeparam name="`**_名称_** `">`**_描述_**`</typeparam>`</span><span class="sxs-lookup"><span data-stu-id="f478d-141">`<typeparam name="`**_name_**`">`**_description_**`</typeparam>`</span></span> | <span data-ttu-id="f478d-142">指定类型参数的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="f478d-142">Specifies the name and description for a type parameter.</span></span>|
| <span data-ttu-id="f478d-143">`<returns>`**_全文_**`</returns>`</span><span class="sxs-lookup"><span data-stu-id="f478d-143">`<returns>`**_text_**`</returns>`</span></span>           | <span data-ttu-id="f478d-144">指定 *文本* 描述函数或方法的返回值。</span><span class="sxs-lookup"><span data-stu-id="f478d-144">Specifies that *text* describes the return value of a function or method.</span></span>|
| <span data-ttu-id="f478d-145">`<exception cref="`**_类型_** `">`**_描述_**`</exception>`</span><span class="sxs-lookup"><span data-stu-id="f478d-145">`<exception cref="`**_type_**`">`**_description_**`</exception>`</span></span> |<span data-ttu-id="f478d-146">指定可以生成的异常的类型以及引发此异常的情况。</span><span class="sxs-lookup"><span data-stu-id="f478d-146">Specifies the type of exception that can be generated and the circumstances under which it is thrown.</span></span>|
| <span data-ttu-id="f478d-147">`<seealso cref="`**_对_**`"/>`</span><span class="sxs-lookup"><span data-stu-id="f478d-147">`<seealso cref="`**_reference_**`"/>`</span></span>      | <span data-ttu-id="f478d-148">指定另一种类型的文档的链接。</span><span class="sxs-lookup"><span data-stu-id="f478d-148">Specifies a See Also link to the documentation for another type.</span></span> <span data-ttu-id="f478d-149">*引用*是显示在 XML 文档文件中的名称。</span><span class="sxs-lookup"><span data-stu-id="f478d-149">The *reference* is the name as it appears in the XML documentation file.</span></span> <span data-ttu-id="f478d-150">另请参阅链接通常显示在文档页的底部。</span><span class="sxs-lookup"><span data-stu-id="f478d-150">See Also links usually appear at the bottom of a documentation page.</span></span>|

<span data-ttu-id="f478d-151">下表描述了 "说明" 部分中使用的标记：</span><span class="sxs-lookup"><span data-stu-id="f478d-151">The following table describes the tags for use inside description sections:</span></span>

| <span data-ttu-id="f478d-152">标记语法</span><span class="sxs-lookup"><span data-stu-id="f478d-152">Tag syntax</span></span>                                | <span data-ttu-id="f478d-153">说明</span><span class="sxs-lookup"><span data-stu-id="f478d-153">Description</span></span> |
|-------------------------------------------|-------------|
| <span data-ttu-id="f478d-154">`<para>`**_全文_**`</para>`</span><span class="sxs-lookup"><span data-stu-id="f478d-154">`<para>`**_text_**`</para>`</span></span>               | <span data-ttu-id="f478d-155">指定文本段落。</span><span class="sxs-lookup"><span data-stu-id="f478d-155">Specifies a paragraph of text.</span></span> <span data-ttu-id="f478d-156">用于分隔 **备注** 标记内的文本。</span><span class="sxs-lookup"><span data-stu-id="f478d-156">This is used to separate text inside the **remarks** tag.</span></span>|
| <span data-ttu-id="f478d-157">`<code>`**_全文_**`</code>`</span><span class="sxs-lookup"><span data-stu-id="f478d-157">`<code>`**_text_**`</code>`</span></span>               | <span data-ttu-id="f478d-158">指定 *文本* 为多行代码。</span><span class="sxs-lookup"><span data-stu-id="f478d-158">Specifies that *text* is multiple lines of code.</span></span> <span data-ttu-id="f478d-159">文档生成器可以使用此标记以适用于代码的字体显示文本。</span><span class="sxs-lookup"><span data-stu-id="f478d-159">This tag can be used by documentation generators to display text in a font that is appropriate for code.</span></span>|
| <span data-ttu-id="f478d-160">`<paramref name="`**_路径名_**`"/>`</span><span class="sxs-lookup"><span data-stu-id="f478d-160">`<paramref name="`**_name_**`"/>`</span></span>         | <span data-ttu-id="f478d-161">指定对同一文档注释中的参数的引用。</span><span class="sxs-lookup"><span data-stu-id="f478d-161">Specifies a reference to a parameter in the same documentation comment.</span></span>|
| <span data-ttu-id="f478d-162">`<typeparamref name="`**_路径名_**`"/>`</span><span class="sxs-lookup"><span data-stu-id="f478d-162">`<typeparamref name="`**_name_**`"/>`</span></span>     | <span data-ttu-id="f478d-163">指定对同一文档注释中类型参数的引用。</span><span class="sxs-lookup"><span data-stu-id="f478d-163">Specifies a reference to a type parameter in the same documentation comment.</span></span>|
| <span data-ttu-id="f478d-164">`<c>`**_全文_**`</c>`</span><span class="sxs-lookup"><span data-stu-id="f478d-164">`<c>`**_text_**`</c>`</span></span>                     | <span data-ttu-id="f478d-165">指定 *文本* 为内联代码。</span><span class="sxs-lookup"><span data-stu-id="f478d-165">Specifies that *text* is inline code.</span></span> <span data-ttu-id="f478d-166">文档生成器可以使用此标记以适用于代码的字体显示文本。</span><span class="sxs-lookup"><span data-stu-id="f478d-166">This tag can be used by documentation generators to display text in a font that is appropriate for code.</span></span>|
| <span data-ttu-id="f478d-167">`<see cref="`**_参考_** `">`**_文本_**`</see>`</span><span class="sxs-lookup"><span data-stu-id="f478d-167">`<see cref="`**_reference_**`">`**_text_**`</see>`</span></span> | <span data-ttu-id="f478d-168">指定指向其他程序元素的内联链接。</span><span class="sxs-lookup"><span data-stu-id="f478d-168">Specifies an inline link to another program element.</span></span> <span data-ttu-id="f478d-169">*引用*是显示在 XML 文档文件中的名称。</span><span class="sxs-lookup"><span data-stu-id="f478d-169">The *reference* is the name as it appears in the XML documentation file.</span></span> <span data-ttu-id="f478d-170">*文本*是链接中显示的文本。</span><span class="sxs-lookup"><span data-stu-id="f478d-170">The *text* is the text shown in the link.</span></span>|

### <a name="user-defined-tags"></a><span data-ttu-id="f478d-171">用户定义的标记</span><span class="sxs-lookup"><span data-stu-id="f478d-171">User-defined tags</span></span>

<span data-ttu-id="f478d-172">前面的标记表示由 F # 编译器和典型的 F # 编辑器工具识别的标记。</span><span class="sxs-lookup"><span data-stu-id="f478d-172">The previous tags represent those that are recognized by the F# compiler and typical F# editor tooling.</span></span> <span data-ttu-id="f478d-173">但用户可随意定义自己的标记。</span><span class="sxs-lookup"><span data-stu-id="f478d-173">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="f478d-174">诸如 fsdocs 之类的工具将支持额外的标记，例如 [\<namespacedoc>](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1031-xmldoc-extensions.md) 。</span><span class="sxs-lookup"><span data-stu-id="f478d-174">Tools like fsdocs bring support for extra tags like [\<namespacedoc>](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1031-xmldoc-extensions.md).</span></span>
<span data-ttu-id="f478d-175">自定义或内部文档生成工具也可与标准标记配合使用，并支持 HTML 到 PDF 等多种输出格式。</span><span class="sxs-lookup"><span data-stu-id="f478d-175">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="compile-time-checking"></a><span data-ttu-id="f478d-176">编译时检查</span><span class="sxs-lookup"><span data-stu-id="f478d-176">Compile-time checking</span></span>

<span data-ttu-id="f478d-177">`--warnon:3390`启用后，编译器将验证 XML 语法和和标记中引用的参数 `<param>` `<paramref>` 。</span><span class="sxs-lookup"><span data-stu-id="f478d-177">When `--warnon:3390` is enabled, the compiler verifies the syntax of the XML and the parameters referred to in `<param>` and `<paramref>` tags.</span></span>

## <a name="documenting-f-constructs"></a><span data-ttu-id="f478d-178">记录 F # 构造</span><span class="sxs-lookup"><span data-stu-id="f478d-178">Documenting F# Constructs</span></span>

<span data-ttu-id="f478d-179">F # 构造（如模块、成员、联合用例和记录字段）在 `///` 声明之前立即由注释记录。</span><span class="sxs-lookup"><span data-stu-id="f478d-179">F# constructs such as modules, members, union cases and record fields are documented by a `///` comment immediately prior to their declaration.</span></span>
<span data-ttu-id="f478d-180">如果需要，可以通过 `///` 在参数列表之前提供注释来记录类的隐式构造函数。</span><span class="sxs-lookup"><span data-stu-id="f478d-180">If needed, implicit constructors of classes are documented by giving a `///` comment prior to the argument list.</span></span> <span data-ttu-id="f478d-181">例如：</span><span class="sxs-lookup"><span data-stu-id="f478d-181">For example:</span></span>

```fsharp
/// This is the type
type SomeType
      /// This is the implicit constructor
      (a: int, b: int) =

    /// This is the member
    member _.Sum() = a + b
```

## <a name="limitations"></a><span data-ttu-id="f478d-182">限制</span><span class="sxs-lookup"><span data-stu-id="f478d-182">Limitations</span></span>

<span data-ttu-id="f478d-183">C # 中不支持 c # 和其他 .NET 语言的 XML 文档的某些功能。</span><span class="sxs-lookup"><span data-stu-id="f478d-183">Some features of XML documentation in C# and other .NET languages are not supported in C#.</span></span>

- <span data-ttu-id="f478d-184">在 F # 中，交叉引用必须使用相应符号的完整 XML 签名，例如 `cref="T:System.Console"` 。</span><span class="sxs-lookup"><span data-stu-id="f478d-184">In F#, cross-references must use the full XML signature of the corresponding symbol, for example `cref="T:System.Console"`.</span></span>
  <span data-ttu-id="f478d-185">简单的 c # 样式交叉引用（如） `cref="Console"` 不会详细阐述为完整的 XML 签名，并且 F # 编译器不会检查这些元素。</span><span class="sxs-lookup"><span data-stu-id="f478d-185">Simple C#-style cross-references such as `cref="Console"` are not elaborated to full XML signatures and these elements are not checked by the F# compiler.</span></span> <span data-ttu-id="f478d-186">某些文档工具可能允许通过后续处理使用这些交叉引用，但应使用完整的签名。</span><span class="sxs-lookup"><span data-stu-id="f478d-186">Some documentation tooling may allow the use of these these cross-references by subsequent processing, but the full signatures should be used.</span></span>
  
- <span data-ttu-id="f478d-187">`<include>` `<inheritdoc>` F # 编译器不支持标记。</span><span class="sxs-lookup"><span data-stu-id="f478d-187">The tags `<include>`, `<inheritdoc>` are not supported by the F# compiler.</span></span> <span data-ttu-id="f478d-188">如果使用了错误，则不会给出任何错误，但它们只是复制到生成的文档文件，而不会影响生成的文档。</span><span class="sxs-lookup"><span data-stu-id="f478d-188">No error is given if they are used, but they are simply copied to the generated documentation file without otherwise affecting the documentation generated.</span></span>

- <span data-ttu-id="f478d-189">F # 编译器不检查交叉引用，即使 `-warnon:3390` 使用了也是如此。</span><span class="sxs-lookup"><span data-stu-id="f478d-189">Cross-references are not checked by the F# compiler, even when `-warnon:3390` is used.</span></span>

- <span data-ttu-id="f478d-190">`<typeparam>` `<typeparamref>` 即使使用了，也不会通过 F # 编译器检查标记和中使用的名称 `--warnon:3390` 。</span><span class="sxs-lookup"><span data-stu-id="f478d-190">The names used in the tags `<typeparam>` and `<typeparamref>` are not checked by the F# compiler, even when `--warnon:3390` is used.</span></span>

- <span data-ttu-id="f478d-191">如果缺少文档，甚至在使用时也不会发出警告 `--warnon:3390` 。</span><span class="sxs-lookup"><span data-stu-id="f478d-191">No warnings are given if documentation is missing, even when `--warnon:3390` is used.</span></span>

## <a name="recommendations"></a><span data-ttu-id="f478d-192">建议</span><span class="sxs-lookup"><span data-stu-id="f478d-192">Recommendations</span></span>

<span data-ttu-id="f478d-193">出于多种原因，建议编制代码文档。</span><span class="sxs-lookup"><span data-stu-id="f478d-193">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="f478d-194">下面是一些最佳实践，一般用例方案，以及在 F # 代码中使用 XML 文档标记时应了解的内容。</span><span class="sxs-lookup"><span data-stu-id="f478d-194">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your F# code.</span></span>

- <span data-ttu-id="f478d-195">启用 `--warnon:3390` 代码中的选项，以帮助确保 xml 文档是有效的 xml。</span><span class="sxs-lookup"><span data-stu-id="f478d-195">Enable the option `--warnon:3390` in your code to help ensure your XML documentation is valid XML.</span></span>

- <span data-ttu-id="f478d-196">请考虑从实现中添加签名文件来分隔长 XML 文档注释。</span><span class="sxs-lookup"><span data-stu-id="f478d-196">Consider adding signature files to separate long XML documentation comments from your implementation.</span></span>

- <span data-ttu-id="f478d-197">为保持一致性，应编制所有公共可见类型及其成员的文档。</span><span class="sxs-lookup"><span data-stu-id="f478d-197">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="f478d-198">如果必须这么做，请完整全面地完成这一操作。</span><span class="sxs-lookup"><span data-stu-id="f478d-198">If you must do it, do it all.</span></span>

- <span data-ttu-id="f478d-199">至少，模块、类型及其成员应具有普通 `///` 注释或 `<summary>` 标记。</span><span class="sxs-lookup"><span data-stu-id="f478d-199">At a bare minimum, modules, types and their members should have a plain `///` comment or `<summary>` tag.</span></span> <span data-ttu-id="f478d-200">这会显示在 F # 编辑工具中自动完成的工具提示窗口中。</span><span class="sxs-lookup"><span data-stu-id="f478d-200">This will show in an autocompletion tooltip window in F# editing tools.</span></span>

- <span data-ttu-id="f478d-201">应使用句号结尾的完整句子编写文档文本。</span><span class="sxs-lookup"><span data-stu-id="f478d-201">Documentation text should be written using complete sentences ending with full stops.</span></span>

## <a name="see-also"></a><span data-ttu-id="f478d-202">请参阅</span><span class="sxs-lookup"><span data-stu-id="f478d-202">See also</span></span>

- <span data-ttu-id="f478d-203">C [# XML 文档注释 &#40;c&#35; 编程指南&#41;](../../csharp/programming-guide/xmldoc/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f478d-203">[C# XML Documentation Comments &#40;C&#35; Programming Guide&#41;](../../csharp/programming-guide/xmldoc/index.md).</span></span>
- [<span data-ttu-id="f478d-204">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="f478d-204">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="f478d-205">编译器选项</span><span class="sxs-lookup"><span data-stu-id="f478d-205">Compiler Options</span></span>](compiler-options.md)
