---
title: XslTransform 类实现 XSLT 处理器
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
ms.openlocfilehash: eec5d6588d907e2d12b588ab3bfe743d6d1eaff9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281604"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="4874c-102">XslTransform 类实现 XSLT 处理器</span><span class="sxs-lookup"><span data-stu-id="4874c-102">XslTransform Class Implements the XSLT Processor</span></span>

> [!NOTE]
> <span data-ttu-id="4874c-103"><xref:System.Xml.Xsl.XslTransform> 类在 .NET Framework 2.0 中已过时。</span><span class="sxs-lookup"><span data-stu-id="4874c-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="4874c-104">可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 类执行可扩展样式表语言转换 (XSLT) 转换。</span><span class="sxs-lookup"><span data-stu-id="4874c-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="4874c-105">请参阅[使用 XslCompiledTransform 类](using-the-xslcompiledtransform-class.md)和[从 XslTransform 类迁移](migrating-from-the-xsltransform-class.md)，以获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="4874c-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="4874c-106"><xref:System.Xml.Xsl.XslTransform> 类是实现 XSL 转换 (XSLT) 1.0 版建议的 XSLT 处理器。</span><span class="sxs-lookup"><span data-stu-id="4874c-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="4874c-107"><xref:System.Xml.Xsl.XslTransform.Load%2A> 方法定位并读取样式表，<xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法转换给定的源文档。</span><span class="sxs-lookup"><span data-stu-id="4874c-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="4874c-108">任何实现了 <xref:System.Xml.XPath.IXPathNavigable> 接口的存储区都可以用作 <xref:System.Xml.Xsl.XslTransform> 的源文档。</span><span class="sxs-lookup"><span data-stu-id="4874c-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="4874c-109">.NET Framework 当前在 <xref:System.Xml.XmlDocument>、<xref:System.Xml.XmlDataDocument> 和 <xref:System.Xml.XPath.XPathDocument> 上实现了 <xref:System.Xml.XPath.IXPathNavigable> 接口，所以它们都可以用作转换的输入源文档。</span><span class="sxs-lookup"><span data-stu-id="4874c-109">The .NET Framework currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>

<span data-ttu-id="4874c-110">.NET Framework 中的 <xref:System.Xml.Xsl.XslTransform> 对象仅支持用以下命名空间定义的 XSLT 1.0 规范：</span><span class="sxs-lookup"><span data-stu-id="4874c-110">The <xref:System.Xml.Xsl.XslTransform> object in the .NET Framework only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

<span data-ttu-id="4874c-111">样式表可以用 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法从下列类之一中加载：</span><span class="sxs-lookup"><span data-stu-id="4874c-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>

- <span data-ttu-id="4874c-112">XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4874c-112">XPathNavigator</span></span>

- <span data-ttu-id="4874c-113">XmlReader</span><span class="sxs-lookup"><span data-stu-id="4874c-113">XmlReader</span></span>

- <span data-ttu-id="4874c-114">表示 URI 的字符串</span><span class="sxs-lookup"><span data-stu-id="4874c-114">A string representing a URL</span></span>

<span data-ttu-id="4874c-115">上面的每个输入类分别有不同的 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4874c-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="4874c-116">有些方法接受其中一个类与 <xref:System.Xml.XmlResolver> 类的组合作为参数。</span><span class="sxs-lookup"><span data-stu-id="4874c-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="4874c-117"><xref:System.Xml.XmlResolver> 定位由样式表中的 `<xsl:import>` 或 `<xsl:include>` 引用的资源。</span><span class="sxs-lookup"><span data-stu-id="4874c-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="4874c-118">下列方法以字符串、<xref:System.Xml.XmlReader> 或 <xref:System.Xml.XPath.XPathNavigator> 作为输入。</span><span class="sxs-lookup"><span data-stu-id="4874c-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>

```vb
Overloads Public Sub Load(String)
```

```csharp
public void Load(string);
```

```vb
Overloads Public Sub Load(String, XmlResolver)
```

```csharp
public void Load(string, XmlResolver);
```

```vb
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)
```

```csharp
public void Load(XmlReader, XmlResolver, Evidence);
```

```vb
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)
```

```csharp
public void Load(XPathNavigator, XmlResolver, Evidence);
```

<span data-ttu-id="4874c-119">上面所示的多数 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法都接受 <xref:System.Xml.XmlResolver> 作为参数。</span><span class="sxs-lookup"><span data-stu-id="4874c-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="4874c-120"><xref:System.Xml.XmlResolver> 用于加载该样式表以及 xsl:import 和 xsl:include 元素中引用的任何样式表。</span><span class="sxs-lookup"><span data-stu-id="4874c-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>

<span data-ttu-id="4874c-121">多数 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法还接受 evidence 作为参数。</span><span class="sxs-lookup"><span data-stu-id="4874c-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="4874c-122">evidence 参数是与样式表关联的 <xref:System.Security.Policy.Evidence>。</span><span class="sxs-lookup"><span data-stu-id="4874c-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="4874c-123">样式表的安全级别影响它引用的所有资源的安全级别，例如包含的脚本、使用的任何 `document()` 函数以及 <xref:System.Xml.Xsl.XsltArgumentList> 使用的任何扩展对象。</span><span class="sxs-lookup"><span data-stu-id="4874c-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="4874c-124">如果样式表是使用一个包含 URL 参数但没有提供证据的 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法加载的，该样式表的证据将通过结合给定的 URL 与其站点和区域计算得出。</span><span class="sxs-lookup"><span data-stu-id="4874c-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>

<span data-ttu-id="4874c-125">如果未提供 URI 或证据，那么样式表的 证据集就完全受信任。</span><span class="sxs-lookup"><span data-stu-id="4874c-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="4874c-126">不要从不受信任的源加载样式表或将不受信任的扩展对象添加到 <xref:System.Xml.Xsl.XsltArgumentList>。</span><span class="sxs-lookup"><span data-stu-id="4874c-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="4874c-127">若要详细了解安全级别和证据及其对脚本的影响，请参阅[使用 \<msxsl:script> 编写 XSLT 样式表脚本](xslt-stylesheet-scripting-using-msxsl-script.md)。</span><span class="sxs-lookup"><span data-stu-id="4874c-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="4874c-128">若要了解安全级别和证据及其对扩展对象的影响，请参阅[样式表参数和扩展对象的 XsltArgumentList](xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="4874c-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>

<span data-ttu-id="4874c-129">若要了解安全级别和证据及其对 `document()` 函数的影响，请参阅[解析外部 XSLT 样式表和文档](resolving-external-xslt-style-sheets-and-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="4874c-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](resolving-external-xslt-style-sheets-and-documents.md).</span></span>

<span data-ttu-id="4874c-130">可以给样式表提供许多输入参数。</span><span class="sxs-lookup"><span data-stu-id="4874c-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="4874c-131">样式表也可以调用扩展对象上的函数。</span><span class="sxs-lookup"><span data-stu-id="4874c-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="4874c-132">参数和扩展对象都是使用 <xref:System.Xml.Xsl.XsltArgumentList> 类提供给样式表的。</span><span class="sxs-lookup"><span data-stu-id="4874c-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="4874c-133">有关 <xref:System.Xml.Xsl.XsltArgumentList> 的详细信息，请参阅<xref:System.Xml.Xsl.XsltArgumentList>。</span><span class="sxs-lookup"><span data-stu-id="4874c-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="4874c-134">XslTransform 类建议的安全用法</span><span class="sxs-lookup"><span data-stu-id="4874c-134">Recommended Secure Use of XslTransform Class</span></span>

<span data-ttu-id="4874c-135">样式表的安全特权取决于提供的证据。</span><span class="sxs-lookup"><span data-stu-id="4874c-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="4874c-136">下表概括了样式表的位置并说明了应提供的证据类型。</span><span class="sxs-lookup"><span data-stu-id="4874c-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>

- <span data-ttu-id="4874c-137">XSLT 样式表没有外部引用，或者样式表来自你信任的代码库。</span><span class="sxs-lookup"><span data-stu-id="4874c-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>

  - <span data-ttu-id="4874c-138">提供源自您的程序集的证据：</span><span class="sxs-lookup"><span data-stu-id="4874c-138">Provide the evidence from your assembly:</span></span>

    ```vb
    Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)

    XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);
    ```

- <span data-ttu-id="4874c-139">XSLT 样式表来自外部源。</span><span class="sxs-lookup"><span data-stu-id="4874c-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="4874c-140">源的来源已知而且有一个可验证的 URI。</span><span class="sxs-lookup"><span data-stu-id="4874c-140">The origin of the source is known and there is a verifiable URI.</span></span>

  - <span data-ttu-id="4874c-141">用 URI 创建证据。</span><span class="sxs-lookup"><span data-stu-id="4874c-141">Create evidence using the URI.</span></span>

    ```vb
    Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)

    XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);
    ```

- <span data-ttu-id="4874c-142">XSLT 样式表来自外部源。</span><span class="sxs-lookup"><span data-stu-id="4874c-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="4874c-143">源的来源未知。</span><span class="sxs-lookup"><span data-stu-id="4874c-143">The origin of the source is not known.</span></span>

  - <span data-ttu-id="4874c-144">将 evidence 设置为 `null`。</span><span class="sxs-lookup"><span data-stu-id="4874c-144">Set evidence to `null`.</span></span> <span data-ttu-id="4874c-145">脚本块将不进行处理，不支持 XSLT `document()` 函数，而且不允许特权扩展对象。</span><span class="sxs-lookup"><span data-stu-id="4874c-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>

    <span data-ttu-id="4874c-146">此外，您还可以将 `resolver` 参数设置为 `null`。这可确保不处理 `xsl:import` 和 `xsl:include` 元素。</span><span class="sxs-lookup"><span data-stu-id="4874c-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>

- <span data-ttu-id="4874c-147">XSLT 样式表来自外部源。</span><span class="sxs-lookup"><span data-stu-id="4874c-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="4874c-148">源的来源未知，但您需要脚本支持。</span><span class="sxs-lookup"><span data-stu-id="4874c-148">The origin of the source is not known, but you require script support.</span></span>

  - <span data-ttu-id="4874c-149">从调用方请求证据。</span><span class="sxs-lookup"><span data-stu-id="4874c-149">Request evidence from the caller.</span></span>

## <a name="transformation-of-xml-data"></a><span data-ttu-id="4874c-150">XML 数据的转换</span><span class="sxs-lookup"><span data-stu-id="4874c-150">Transformation of XML Data</span></span>

<span data-ttu-id="4874c-151">加载样式表后，转换过程将调用一个 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法并提供输入源文档，开始进行转换。</span><span class="sxs-lookup"><span data-stu-id="4874c-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="4874c-152">重载 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法以提供不同的转换输出。</span><span class="sxs-lookup"><span data-stu-id="4874c-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="4874c-153">转换可产生下列输出格式：</span><span class="sxs-lookup"><span data-stu-id="4874c-153">The transformation can result in the following output formats:</span></span>

- <xref:System.Xml.XmlReader>

- <xref:System.Xml.XmlWriter>

- <xref:System.IO.TextWriter>

- <xref:System.IO.Stream>

- <span data-ttu-id="4874c-154">文件的字符串 URL</span><span class="sxs-lookup"><span data-stu-id="4874c-154">String URL of file</span></span>

<span data-ttu-id="4874c-155">最后一种格式是字符串 URL，为转换位于 URL 中的输入文档并将文档写入输出 URL 提供了一种常用方案。</span><span class="sxs-lookup"><span data-stu-id="4874c-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="4874c-156">此 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法是从文件加载 XML 文档、执行 XSLT 转换并将输出写入文件的便捷方法。</span><span class="sxs-lookup"><span data-stu-id="4874c-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="4874c-157">这样，您就不必创建并加载输入源文档，然后写入文件流。</span><span class="sxs-lookup"><span data-stu-id="4874c-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="4874c-158">下面的代码示例显示了 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法的用法，使用字符串 URL 用作输入和输出：</span><span class="sxs-lookup"><span data-stu-id="4874c-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>

```vb
Dim xsltransform As XslTransform = New XslTransform()
xsltransform.Load("favorite.xsl")
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)
```

```csharp
XslTransform xsltransform = new XslTransform();
xsltransform.Load("favorite.xsl");
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);
```

## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="4874c-159">转换 XML 文档的节</span><span class="sxs-lookup"><span data-stu-id="4874c-159">Transforming a Section of an XML Document</span></span>

<span data-ttu-id="4874c-160">转换将应用于整个文档。</span><span class="sxs-lookup"><span data-stu-id="4874c-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="4874c-161">换句话说，如果你传入文档根节点以外的一个节点，并不能防止转换进程访问已加载文档的所有节点。</span><span class="sxs-lookup"><span data-stu-id="4874c-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="4874c-162">若要转换结果树片段，必须创建一个仅包含结果树片段的 <xref:System.Xml.XmlDocument>，并将该 <xref:System.Xml.XmlDocument> 传递给 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4874c-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="4874c-163">下面的示例对一个结果树片段执行转换。</span><span class="sxs-lookup"><span data-stu-id="4874c-163">The following example performs a transformation on a result tree fragment.</span></span>

```vb
Dim xslt As New XslTransform()
xslt.Load("print_root.xsl")
Dim doc As New XmlDocument()
doc.Load("library.xml")
' Create a new document containing just the result tree fragment.
Dim testNode As XmlNode = doc.DocumentElement.FirstChild
Dim tmpDoc As New XmlDocument()
tmpDoc.LoadXml(testNode.OuterXml)
' Pass the document containing the result tree fragment
' to the Transform method.
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)
```

```csharp
XslTransform xslt = new XslTransform();
xslt.Load("print_root.xsl");
XmlDocument doc = new XmlDocument();
doc.Load("library.xml");
// Create a new document containing just the result tree fragment.
XmlNode testNode = doc.DocumentElement.FirstChild;
XmlDocument tmpDoc = new XmlDocument();
tmpDoc.LoadXml(testNode.OuterXml);
// Pass the document containing the result tree fragment
// to the Transform method.
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");
xslt.Transform(tmpDoc, null, Console.Out, null);
```

<span data-ttu-id="4874c-164">该示例使用 library.xml 和 print_root.xsl 文件作为输入并将以下内容输出到控制台：</span><span class="sxs-lookup"><span data-stu-id="4874c-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console:</span></span>

```console
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl
Root node is book.
```

<span data-ttu-id="4874c-165">library.xml</span><span class="sxs-lookup"><span data-stu-id="4874c-165">library.xml</span></span>

```xml
<library>
  <book genre='novel' ISBN='1-861001-57-5'>
     <title>Pride And Prejudice</title>
  </book>
  <book genre='novel' ISBN='1-81920-21-2'>
     <title>Hook</title>
  </book>
</library>
```

<span data-ttu-id="4874c-166">print_root.xsl</span><span class="sxs-lookup"><span data-stu-id="4874c-166">print_root.xsl</span></span>

```xml
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >
  <output method="text" />
  <template match="/">
     Root node is  <value-of select="local-name(//*[position() = 1])" />
  </template>
</stylesheet>
```

## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="4874c-167">XSLT 从 .NET Framework 1.0 版到 .NET Framework 1.1 版的迁移</span><span class="sxs-lookup"><span data-stu-id="4874c-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>

<span data-ttu-id="4874c-168">下表显示 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法的已过时的 .NET Framework 1.0 版方法以及新的 .NET Framework 1.1 方法。</span><span class="sxs-lookup"><span data-stu-id="4874c-168">The following table shows the obsolete .NET Framework version 1.0 methods and new .NET Framework version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="4874c-169">新方法允许您通过指定证据来限制样式表的权限。</span><span class="sxs-lookup"><span data-stu-id="4874c-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>

|<span data-ttu-id="4874c-170">.NET Framework 版本 1.0 中已过时的 Load 方法</span><span class="sxs-lookup"><span data-stu-id="4874c-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="4874c-171">.NET Framework 版本 1.1 中替换的新 Load 方法</span><span class="sxs-lookup"><span data-stu-id="4874c-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|
|------------------------------------------------------|---------------------------------------------------------|
|<span data-ttu-id="4874c-172">Load(XPathNavigator input);</span><span class="sxs-lookup"><span data-stu-id="4874c-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="4874c-173">Load(XPathNavigator input, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="4874c-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="4874c-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span><span class="sxs-lookup"><span data-stu-id="4874c-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="4874c-175">Load(IXPathNavigable stylesheet);</span><span class="sxs-lookup"><span data-stu-id="4874c-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="4874c-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="4874c-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="4874c-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span><span class="sxs-lookup"><span data-stu-id="4874c-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="4874c-178">Load(XmlReader stylesheet);</span><span class="sxs-lookup"><span data-stu-id="4874c-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="4874c-179">Load(XmlReader stylesheet, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="4874c-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="4874c-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span><span class="sxs-lookup"><span data-stu-id="4874c-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|

<span data-ttu-id="4874c-181">下表显示 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法的已过时方法和新方法。</span><span class="sxs-lookup"><span data-stu-id="4874c-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="4874c-182">新方法接受 <xref:System.Xml.XmlResolver> 对象。</span><span class="sxs-lookup"><span data-stu-id="4874c-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>

|<span data-ttu-id="4874c-183">.NET Framework 版本 1.0 中已过时的 Transform 方法</span><span class="sxs-lookup"><span data-stu-id="4874c-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="4874c-184">.NET Framework 版本 1.1 中替换的新 Transform 方法</span><span class="sxs-lookup"><span data-stu-id="4874c-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|
|-----------------------------------------------------------|--------------------------------------------------------------|
|<span data-ttu-id="4874c-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="4874c-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="4874c-186">XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="4874c-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="4874c-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="4874c-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="4874c-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="4874c-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="4874c-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span><span class="sxs-lookup"><span data-stu-id="4874c-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="4874c-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="4874c-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="4874c-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span><span class="sxs-lookup"><span data-stu-id="4874c-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="4874c-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="4874c-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="4874c-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span><span class="sxs-lookup"><span data-stu-id="4874c-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="4874c-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="4874c-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="4874c-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span><span class="sxs-lookup"><span data-stu-id="4874c-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="4874c-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="4874c-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="4874c-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span><span class="sxs-lookup"><span data-stu-id="4874c-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="4874c-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="4874c-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="4874c-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span><span class="sxs-lookup"><span data-stu-id="4874c-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="4874c-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="4874c-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="4874c-201">Void Transform(String input, String output);</span><span class="sxs-lookup"><span data-stu-id="4874c-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="4874c-202">Void Transform(String input, String output, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="4874c-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|

<span data-ttu-id="4874c-203"><xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> 属性在 .NET Framework 1.1 版中已过时。</span><span class="sxs-lookup"><span data-stu-id="4874c-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in .NET Framework version 1.1.</span></span> <span data-ttu-id="4874c-204">应改用接受 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 对象的新 <xref:System.Xml.XmlResolver> 重载。</span><span class="sxs-lookup"><span data-stu-id="4874c-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>

## <a name="see-also"></a><span data-ttu-id="4874c-205">请参阅</span><span class="sxs-lookup"><span data-stu-id="4874c-205">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="4874c-206">XslTransform 类的 XSLT 转换</span><span class="sxs-lookup"><span data-stu-id="4874c-206">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="4874c-207">转换中的 XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4874c-207">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="4874c-208">转换中的 XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="4874c-208">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="4874c-209">XslTransform 的 XPathDocument 输入</span><span class="sxs-lookup"><span data-stu-id="4874c-209">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="4874c-210">XslTransform 的 XmlDataDocument 输入</span><span class="sxs-lookup"><span data-stu-id="4874c-210">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="4874c-211">XslTransform 的 XmlDocument 输入</span><span class="sxs-lookup"><span data-stu-id="4874c-211">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)
