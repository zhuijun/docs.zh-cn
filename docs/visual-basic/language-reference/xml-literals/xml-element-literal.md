---
title: XML 元素文本
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6a91de4e279816bafd29f46bb4f5422cbd934ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400184"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="1190e-102">XML 元素文本 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1190e-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="1190e-103">表示对象的文本 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="1190e-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="1190e-104">语法</span><span class="sxs-lookup"><span data-stu-id="1190e-104">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="1190e-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="1190e-105">Parts</span></span>

- `<`

  <span data-ttu-id="1190e-106">必需。</span><span class="sxs-lookup"><span data-stu-id="1190e-106">Required.</span></span> <span data-ttu-id="1190e-107">打开开始元素标记。</span><span class="sxs-lookup"><span data-stu-id="1190e-107">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="1190e-108">必需。</span><span class="sxs-lookup"><span data-stu-id="1190e-108">Required.</span></span> <span data-ttu-id="1190e-109">元素名称。</span><span class="sxs-lookup"><span data-stu-id="1190e-109">Name of the element.</span></span> <span data-ttu-id="1190e-110">格式为以下格式之一：</span><span class="sxs-lookup"><span data-stu-id="1190e-110">The format is one of the following:</span></span>

  - <span data-ttu-id="1190e-111">元素名称的文本文本，格式为 `[ePrefix:]eName` ，其中：</span><span class="sxs-lookup"><span data-stu-id="1190e-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="1190e-112">组成部分</span><span class="sxs-lookup"><span data-stu-id="1190e-112">Part</span></span>|<span data-ttu-id="1190e-113">说明</span><span class="sxs-lookup"><span data-stu-id="1190e-113">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="1190e-114">可选。</span><span class="sxs-lookup"><span data-stu-id="1190e-114">Optional.</span></span> <span data-ttu-id="1190e-115">元素的 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="1190e-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="1190e-116">必须是一个全局 XML 命名空间，该命名空间是使用 `Imports` 文件中的语句或项目级别定义的，或是在此元素或父元素中定义的本地 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="1190e-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="1190e-117">必需。</span><span class="sxs-lookup"><span data-stu-id="1190e-117">Required.</span></span> <span data-ttu-id="1190e-118">元素名称。</span><span class="sxs-lookup"><span data-stu-id="1190e-118">Name of the element.</span></span> <span data-ttu-id="1190e-119">格式为以下格式之一：</span><span class="sxs-lookup"><span data-stu-id="1190e-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="1190e-120">文本。</span><span class="sxs-lookup"><span data-stu-id="1190e-120">- Literal text.</span></span> <span data-ttu-id="1190e-121">请参阅已[声明的 XML 元素和属性的名称](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="1190e-121">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="1190e-122">-窗体的嵌入式表达式 `<%= eNameExp %>` 。</span><span class="sxs-lookup"><span data-stu-id="1190e-122">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="1190e-123">的类型 `eNameExp` 必须为 `String` 或可隐式转换为的类型 <xref:System.Xml.Linq.XName> 。</span><span class="sxs-lookup"><span data-stu-id="1190e-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="1190e-124">窗体的嵌入式表达式 `<%= nameExp %>` 。</span><span class="sxs-lookup"><span data-stu-id="1190e-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="1190e-125">的类型 `nameExp` 必须为 `String` 或可隐式转换为的类型 <xref:System.Xml.Linq.XName> 。</span><span class="sxs-lookup"><span data-stu-id="1190e-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="1190e-126">元素的结束标记中不允许使用嵌入式表达式。</span><span class="sxs-lookup"><span data-stu-id="1190e-126">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="1190e-127">可选。</span><span class="sxs-lookup"><span data-stu-id="1190e-127">Optional.</span></span> <span data-ttu-id="1190e-128">在文本中声明的属性的列表。</span><span class="sxs-lookup"><span data-stu-id="1190e-128">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="1190e-129">每个 `attribute` 都具有以下语法之一：</span><span class="sxs-lookup"><span data-stu-id="1190e-129">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="1190e-130">属性分配，格式为 `[aPrefix:]aName=aValue` ，其中：</span><span class="sxs-lookup"><span data-stu-id="1190e-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="1190e-131">组成部分</span><span class="sxs-lookup"><span data-stu-id="1190e-131">Part</span></span>|<span data-ttu-id="1190e-132">说明</span><span class="sxs-lookup"><span data-stu-id="1190e-132">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="1190e-133">可选。</span><span class="sxs-lookup"><span data-stu-id="1190e-133">Optional.</span></span> <span data-ttu-id="1190e-134">特性的 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="1190e-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="1190e-135">必须是使用语句定义的全局 XML 命名空间 `Imports` ，或此元素或父元素中定义的本地 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="1190e-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="1190e-136">必需。</span><span class="sxs-lookup"><span data-stu-id="1190e-136">Required.</span></span> <span data-ttu-id="1190e-137">属性的名称。</span><span class="sxs-lookup"><span data-stu-id="1190e-137">Name of the attribute.</span></span> <span data-ttu-id="1190e-138">格式为以下格式之一：</span><span class="sxs-lookup"><span data-stu-id="1190e-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="1190e-139">文本。</span><span class="sxs-lookup"><span data-stu-id="1190e-139">- Literal text.</span></span> <span data-ttu-id="1190e-140">请参阅已[声明的 XML 元素和属性的名称](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="1190e-140">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="1190e-141">-窗体的嵌入式表达式 `<%= aNameExp %>` 。</span><span class="sxs-lookup"><span data-stu-id="1190e-141">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="1190e-142">的类型 `aNameExp` 必须为 `String` 或可隐式转换为的类型 <xref:System.Xml.Linq.XName> 。</span><span class="sxs-lookup"><span data-stu-id="1190e-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="1190e-143">可选。</span><span class="sxs-lookup"><span data-stu-id="1190e-143">Optional.</span></span> <span data-ttu-id="1190e-144">特性的值。</span><span class="sxs-lookup"><span data-stu-id="1190e-144">Value of the attribute.</span></span> <span data-ttu-id="1190e-145">格式为以下格式之一：</span><span class="sxs-lookup"><span data-stu-id="1190e-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="1190e-146">文本文本，用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="1190e-146">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="1190e-147">-窗体的嵌入式表达式 `<%= aValueExp %>` 。</span><span class="sxs-lookup"><span data-stu-id="1190e-147">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="1190e-148">允许任何类型。</span><span class="sxs-lookup"><span data-stu-id="1190e-148">Any type is allowed.</span></span>|

  - <span data-ttu-id="1190e-149">窗体的嵌入式表达式 `<%= aExp %>` 。</span><span class="sxs-lookup"><span data-stu-id="1190e-149">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="1190e-150">可选。</span><span class="sxs-lookup"><span data-stu-id="1190e-150">Optional.</span></span> <span data-ttu-id="1190e-151">指示元素是一个空元素，不包含内容。</span><span class="sxs-lookup"><span data-stu-id="1190e-151">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="1190e-152">必需。</span><span class="sxs-lookup"><span data-stu-id="1190e-152">Required.</span></span> <span data-ttu-id="1190e-153">结束开始或空元素标记。</span><span class="sxs-lookup"><span data-stu-id="1190e-153">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="1190e-154">可选。</span><span class="sxs-lookup"><span data-stu-id="1190e-154">Optional.</span></span> <span data-ttu-id="1190e-155">元素的内容。</span><span class="sxs-lookup"><span data-stu-id="1190e-155">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="1190e-156">每个 `content` 可以是以下各项之一：</span><span class="sxs-lookup"><span data-stu-id="1190e-156">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="1190e-157">文本。</span><span class="sxs-lookup"><span data-stu-id="1190e-157">Literal text.</span></span> <span data-ttu-id="1190e-158">如果存在任何文本，则中的所有空白都 `elementContents` 非常重要。</span><span class="sxs-lookup"><span data-stu-id="1190e-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="1190e-159">窗体的嵌入式表达式 `<%= contentExp %>` 。</span><span class="sxs-lookup"><span data-stu-id="1190e-159">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="1190e-160">XML 元素文本。</span><span class="sxs-lookup"><span data-stu-id="1190e-160">XML element literal.</span></span>

  - <span data-ttu-id="1190e-161">XML 注释文本。</span><span class="sxs-lookup"><span data-stu-id="1190e-161">XML comment literal.</span></span> <span data-ttu-id="1190e-162">请参阅[XML 注释文本](xml-comment-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="1190e-162">See [XML Comment Literal](xml-comment-literal.md).</span></span>

  - <span data-ttu-id="1190e-163">XML 处理指令文本。</span><span class="sxs-lookup"><span data-stu-id="1190e-163">XML processing instruction literal.</span></span> <span data-ttu-id="1190e-164">请参阅[XML 处理指令文本](xml-processing-instruction-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="1190e-164">See [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="1190e-165">XML CDATA 文本。</span><span class="sxs-lookup"><span data-stu-id="1190e-165">XML CDATA literal.</span></span> <span data-ttu-id="1190e-166">请参阅[XML CDATA 文本](xml-cdata-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="1190e-166">See [XML CDATA Literal](xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="1190e-167">可选。</span><span class="sxs-lookup"><span data-stu-id="1190e-167">Optional.</span></span> <span data-ttu-id="1190e-168">表示元素的结束标记。</span><span class="sxs-lookup"><span data-stu-id="1190e-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="1190e-169">`name`如果是嵌入式表达式的结果，则不允许使用可选参数。</span><span class="sxs-lookup"><span data-stu-id="1190e-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="1190e-170">返回值</span><span class="sxs-lookup"><span data-stu-id="1190e-170">Return Value</span></span>

<span data-ttu-id="1190e-171">一个 <xref:System.Xml.Linq.XElement> 对象。</span><span class="sxs-lookup"><span data-stu-id="1190e-171">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="1190e-172">备注</span><span class="sxs-lookup"><span data-stu-id="1190e-172">Remarks</span></span>

<span data-ttu-id="1190e-173">您可以在代码中使用 XML 元素文本语法来创建 <xref:System.Xml.Linq.XElement> 对象。</span><span class="sxs-lookup"><span data-stu-id="1190e-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="1190e-174">XML 文本可以跨多行，而无需使用行继续符。</span><span class="sxs-lookup"><span data-stu-id="1190e-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="1190e-175">此功能使你能够从 XML 文档复制内容并将其直接粘贴到 Visual Basic 程序。</span><span class="sxs-lookup"><span data-stu-id="1190e-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="1190e-176">利用窗体的嵌入式表达式，你可以向 `<%= exp %>` XML 元素文本添加动态信息。</span><span class="sxs-lookup"><span data-stu-id="1190e-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="1190e-177">有关详细信息，请参阅[XML 中的嵌入式表达式](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1190e-177">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="1190e-178">Visual Basic 编译器将 XML 元素文本转换为对构造函数的调用， <xref:System.Xml.Linq.XElement.%23ctor%2A> 并在需要时将其转换为 <xref:System.Xml.Linq.XAttribute.%23ctor%2A> 构造函数。</span><span class="sxs-lookup"><span data-stu-id="1190e-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="1190e-179">XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="1190e-179">XML Namespaces</span></span>

<span data-ttu-id="1190e-180">当你必须在代码中多次使用同一命名空间中的元素创建 XML 文本时，XML 命名空间前缀非常有用。</span><span class="sxs-lookup"><span data-stu-id="1190e-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="1190e-181">你可以使用全局 XML 命名空间前缀，该前缀是使用语句定义的 `Imports` ，或者是使用特性语法定义的本地前缀 `xmlns:xmlPrefix="xmlNamespace"` 。</span><span class="sxs-lookup"><span data-stu-id="1190e-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="1190e-182">有关详细信息，请参阅[Imports 语句（XML 命名空间）](../statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="1190e-182">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="1190e-183">根据 XML 命名空间的作用域规则，本地前缀优先于全局前缀。</span><span class="sxs-lookup"><span data-stu-id="1190e-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="1190e-184">但是，如果 XML 文本定义了 XML 命名空间，则该命名空间不能用于出现在嵌入表达式中的表达式。</span><span class="sxs-lookup"><span data-stu-id="1190e-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="1190e-185">嵌入的表达式只能访问全局 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="1190e-185">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="1190e-186">Visual Basic 编译器将 XML 文本使用的每个全局 XML 命名空间转换为生成的代码中的一个本地命名空间定义。</span><span class="sxs-lookup"><span data-stu-id="1190e-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="1190e-187">不使用的全局 XML 命名空间不会出现在生成的代码中。</span><span class="sxs-lookup"><span data-stu-id="1190e-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="1190e-188">示例</span><span class="sxs-lookup"><span data-stu-id="1190e-188">Example</span></span>

<span data-ttu-id="1190e-189">下面的示例演示如何创建一个具有两个嵌套空元素的简单 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="1190e-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="1190e-190">该示例显示以下文本。</span><span class="sxs-lookup"><span data-stu-id="1190e-190">The example displays the following text.</span></span> <span data-ttu-id="1190e-191">请注意，文本将保留空元素的结构。</span><span class="sxs-lookup"><span data-stu-id="1190e-191">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="1190e-192">示例</span><span class="sxs-lookup"><span data-stu-id="1190e-192">Example</span></span>

<span data-ttu-id="1190e-193">下面的示例演示如何使用嵌入的表达式来命名元素并创建属性。</span><span class="sxs-lookup"><span data-stu-id="1190e-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="1190e-194">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="1190e-194">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="1190e-195">示例</span><span class="sxs-lookup"><span data-stu-id="1190e-195">Example</span></span>

<span data-ttu-id="1190e-196">下面的示例声明 `ns` 作为 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="1190e-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="1190e-197">然后，它使用命名空间的前缀创建 XML 文本，并显示该元素的最终形式。</span><span class="sxs-lookup"><span data-stu-id="1190e-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="1190e-198">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="1190e-198">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="1190e-199">请注意，编译器将全局 XML 命名空间的前缀转换为 XML 命名空间的前缀定义。</span><span class="sxs-lookup"><span data-stu-id="1190e-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="1190e-200">\<ns:middle>元素重新定义元素的 XML 命名空间前缀 \<ns:inner1> 。</span><span class="sxs-lookup"><span data-stu-id="1190e-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="1190e-201">但是， \<ns:inner2> 元素使用语句定义的命名空间 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="1190e-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="1190e-202">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1190e-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="1190e-203">已声明的 XML 元素和属性的名称</span><span class="sxs-lookup"><span data-stu-id="1190e-203">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="1190e-204">XML 注释文本</span><span class="sxs-lookup"><span data-stu-id="1190e-204">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="1190e-205">XML CDATA 文本</span><span class="sxs-lookup"><span data-stu-id="1190e-205">XML CDATA Literal</span></span>](xml-cdata-literal.md)
- [<span data-ttu-id="1190e-206">XML 文本</span><span class="sxs-lookup"><span data-stu-id="1190e-206">XML Literals</span></span>](index.md)
- [<span data-ttu-id="1190e-207">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="1190e-207">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="1190e-208">XML 中的嵌入式表达式</span><span class="sxs-lookup"><span data-stu-id="1190e-208">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="1190e-209">Imports 语句（XML 命名空间）</span><span class="sxs-lookup"><span data-stu-id="1190e-209">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
