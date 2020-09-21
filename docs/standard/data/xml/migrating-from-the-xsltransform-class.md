---
title: 从 XslTransform 类迁移
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 32fac1b5ab339dd4c71d761cf07fcde99ce1f2fa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550158"
---
# <a name="migrating-from-the-xsltransform-class"></a><span data-ttu-id="19ad4-102">从 XslTransform 类迁移</span><span class="sxs-lookup"><span data-stu-id="19ad4-102">Migrating From the XslTransform Class</span></span>

<span data-ttu-id="19ad4-103">Visual Studio 2005 版本重新设计了 XSLT 体系结构。</span><span class="sxs-lookup"><span data-stu-id="19ad4-103">The XSLT architecture was redesigned in the Visual Studio 2005 release.</span></span> <span data-ttu-id="19ad4-104"><xref:System.Xml.Xsl.XslTransform> 类已由 <xref:System.Xml.Xsl.XslCompiledTransform> 类取代。</span><span class="sxs-lookup"><span data-stu-id="19ad4-104">The <xref:System.Xml.Xsl.XslTransform> class was replaced by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

<span data-ttu-id="19ad4-105">以下各节说明 <xref:System.Xml.Xsl.XslCompiledTransform> 和 <xref:System.Xml.Xsl.XslTransform> 类之间的一些主要区别。</span><span class="sxs-lookup"><span data-stu-id="19ad4-105">The following sections describe some of the main differences between the <xref:System.Xml.Xsl.XslCompiledTransform> and the <xref:System.Xml.Xsl.XslTransform> classes.</span></span>

## <a name="performance"></a><span data-ttu-id="19ad4-106">性能</span><span class="sxs-lookup"><span data-stu-id="19ad4-106">Performance</span></span>

<span data-ttu-id="19ad4-107"><xref:System.Xml.Xsl.XslCompiledTransform> 类在性能方面进行了许多改进。</span><span class="sxs-lookup"><span data-stu-id="19ad4-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class includes many performance improvements.</span></span> <span data-ttu-id="19ad4-108">新的 XSLT 处理器将 XSLT 样式表编译为公共中间格式，与公共语言运行库 (CLR) 对其他编程语言的操作类似。</span><span class="sxs-lookup"><span data-stu-id="19ad4-108">The new XSLT processor compiles the XSLT style sheet down to a common intermediate format, similar to what the common language runtime (CLR) does for other programming languages.</span></span> <span data-ttu-id="19ad4-109">样式表编译后，可以缓存并重复使用。</span><span class="sxs-lookup"><span data-stu-id="19ad4-109">Once the style sheet is compiled, it can be cached and reused.</span></span>

<span data-ttu-id="19ad4-110"><xref:System.Xml.Xsl.XslCompiledTransform> 类还进行了其他优化，使其比 <xref:System.Xml.Xsl.XslTransform> 类快得多。</span><span class="sxs-lookup"><span data-stu-id="19ad4-110">The <xref:System.Xml.Xsl.XslCompiledTransform> class also includes other optimizations that make it much faster than the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

> [!NOTE]
> <span data-ttu-id="19ad4-111">尽管 <xref:System.Xml.Xsl.XslCompiledTransform> 类的总体性能优于 <xref:System.Xml.Xsl.XslTransform> 类，但在首次对转换调用时，<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 类的 <xref:System.Xml.Xsl.XslCompiledTransform> 方法可能比 <xref:System.Xml.Xsl.XslTransform.Load%2A> 类的 <xref:System.Xml.Xsl.XslTransform> 方法慢。</span><span class="sxs-lookup"><span data-stu-id="19ad4-111">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="19ad4-112">这是因为必须先编译 XSLT 文件，才能加载该文件。</span><span class="sxs-lookup"><span data-stu-id="19ad4-112">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="19ad4-113">有关详细信息，请参阅以下博客文章：[XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)（XslCompiledTransform 比 XslTransform 慢？）</span><span class="sxs-lookup"><span data-stu-id="19ad4-113">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>

## <a name="security"></a><span data-ttu-id="19ad4-114">安全性</span><span class="sxs-lookup"><span data-stu-id="19ad4-114">Security</span></span>

<span data-ttu-id="19ad4-115">默认情况下，<xref:System.Xml.Xsl.XslCompiledTransform> 类禁用对 XSLT `document()` 函数和嵌入式脚本的支持。</span><span class="sxs-lookup"><span data-stu-id="19ad4-115">By default, the <xref:System.Xml.Xsl.XslCompiledTransform> class disables support for the XSLT `document()` function and embedded scripting.</span></span> <span data-ttu-id="19ad4-116">通过创建启用这些功能的 <xref:System.Xml.Xsl.XsltSettings> 对象并将其传递给 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法，可以启用这些功能。</span><span class="sxs-lookup"><span data-stu-id="19ad4-116">These features can be enabled by creating an <xref:System.Xml.Xsl.XsltSettings> object that has the features enabled and passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="19ad4-117">下面的示例演示如何启用脚本并执行 XSLT 转换。</span><span class="sxs-lookup"><span data-stu-id="19ad4-117">The following example shows how to enable scripting and perform an XSLT transformation.</span></span>

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

<span data-ttu-id="19ad4-118">有关详细信息，请参阅 [XSLT 安全注意事项](xslt-security-considerations.md)。</span><span class="sxs-lookup"><span data-stu-id="19ad4-118">For more information, see [XSLT Security Considerations](xslt-security-considerations.md).</span></span>

## <a name="new-features"></a><span data-ttu-id="19ad4-119">新增功能</span><span class="sxs-lookup"><span data-stu-id="19ad4-119">New Features</span></span>

### <a name="temporary-files"></a><span data-ttu-id="19ad4-120">临时文件</span><span class="sxs-lookup"><span data-stu-id="19ad4-120">Temporary Files</span></span>

<span data-ttu-id="19ad4-121">在 XSLT 处理过程中有时会生成临时文件。</span><span class="sxs-lookup"><span data-stu-id="19ad4-121">Temporary files are sometimes generated during XSLT processing.</span></span> <span data-ttu-id="19ad4-122">如果样式表包含脚本块或是在将调试设置设为 true 时进行编译的，则可能会在 %TEMP% 文件夹中创建临时文件。</span><span class="sxs-lookup"><span data-stu-id="19ad4-122">If a style sheet contains script blocks, or if it is compiled with the debug setting set to true, temporary files may be created in the %TEMP% folder.</span></span> <span data-ttu-id="19ad4-123">可能会存在由于计时问题而不删除某些临时文件的情况。</span><span class="sxs-lookup"><span data-stu-id="19ad4-123">There may be instances when some temporary files are not deleted due to timing issues.</span></span> <span data-ttu-id="19ad4-124">例如，如果文件正在由当前的 AppDomain 或调试器使用，则 <xref:System.CodeDom.Compiler.TempFileCollection> 对象的终结器将无法移除这些文件。</span><span class="sxs-lookup"><span data-stu-id="19ad4-124">For example, if the files are in use by the current AppDomain or by the debugger, the finalizer of the <xref:System.CodeDom.Compiler.TempFileCollection> object will not be able to remove them.</span></span>

<span data-ttu-id="19ad4-125"><xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> 属性可用于进行附加清理，以确保从客户端中移除所有临时文件。</span><span class="sxs-lookup"><span data-stu-id="19ad4-125">The <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> property can be used for additional cleanup to make sure that all temporary files are removed from the client.</span></span>

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a><span data-ttu-id="19ad4-126">对 xsl:output 元素和 XmlWriter 的支持</span><span class="sxs-lookup"><span data-stu-id="19ad4-126">Support for the xsl:output Element and XmlWriter</span></span>

<span data-ttu-id="19ad4-127">在将转换输出发送到 <xref:System.Xml.Xsl.XslTransform> 对象时，`xsl:output` 类忽略 <xref:System.Xml.XmlWriter> 设置。</span><span class="sxs-lookup"><span data-stu-id="19ad4-127">The <xref:System.Xml.Xsl.XslTransform> class ignored `xsl:output` settings when the transform output was sent to an <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="19ad4-128"><xref:System.Xml.Xsl.XslCompiledTransform> 类具有一个 <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> 属性，它可返回一个 <xref:System.Xml.XmlWriterSettings> 对象，该对象包含从样式表的 `xsl:output` 元素派生的输出信息。</span><span class="sxs-lookup"><span data-stu-id="19ad4-128">The <xref:System.Xml.Xsl.XslCompiledTransform> class has an <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> property that returns an <xref:System.Xml.XmlWriterSettings> object containing the output information derived from the `xsl:output` element of the style sheet.</span></span> <span data-ttu-id="19ad4-129"><xref:System.Xml.XmlWriterSettings> 对象用于创建具有正确设置的 <xref:System.Xml.XmlWriter> 对象，可将该对象传递给 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="19ad4-129">The <xref:System.Xml.XmlWriterSettings> object is used to create an <xref:System.Xml.XmlWriter> object with the correct settings that can be passed to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="19ad4-130">下面的 C# 代码阐释这一行为：</span><span class="sxs-lookup"><span data-stu-id="19ad4-130">The following C# code illustrates this behavior:</span></span>

```csharp
// Create the XslTransform object and load the style sheet.
XslCompiledTransform xslt = new XslCompiledTransform();
xslt.Load(stylesheet);

// Load the file to transform.
XPathDocument doc = new XPathDocument(filename);

// Create the writer.
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);

// Transform the file and send the output to the console.
xslt.Transform(doc, writer);
writer.Close();
```

### <a name="debug-option"></a><span data-ttu-id="19ad4-131">调试选项</span><span class="sxs-lookup"><span data-stu-id="19ad4-131">Debug Option</span></span>

<span data-ttu-id="19ad4-132"><xref:System.Xml.Xsl.XslCompiledTransform> 类可生成调试信息，让用户能够使用 Microsoft Visual Studio 调试器调试样式表。</span><span class="sxs-lookup"><span data-stu-id="19ad4-132">The <xref:System.Xml.Xsl.XslCompiledTransform> class can generate debug information, which enables you to debug the style sheet with the Microsoft Visual Studio Debugger.</span></span> <span data-ttu-id="19ad4-133">有关更多信息，请参见<xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>。</span><span class="sxs-lookup"><span data-stu-id="19ad4-133">See <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> for more information.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="19ad4-134">行为差异</span><span class="sxs-lookup"><span data-stu-id="19ad4-134">Behavioral Differences</span></span>

### <a name="transforming-to-an-xmlreader"></a><span data-ttu-id="19ad4-135">转换为 XmlReader</span><span class="sxs-lookup"><span data-stu-id="19ad4-135">Transforming to an XmlReader</span></span>

<span data-ttu-id="19ad4-136"><xref:System.Xml.Xsl.XslTransform> 类具有多个作为 <xref:System.Xml.XmlReader> 对象返回转换结果的 Transform 重载。</span><span class="sxs-lookup"><span data-stu-id="19ad4-136">The <xref:System.Xml.Xsl.XslTransform> class has several Transform overloads that return transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="19ad4-137">这些重载可用于将转换结果加载到内存表示形式（如 <xref:System.Xml.XmlDocument> 或 <xref:System.Xml.XPath.XPathDocument>），而不会增加对生成的 XML 树进行序列化和反序列化所造成的开销。</span><span class="sxs-lookup"><span data-stu-id="19ad4-137">These overloads can be used to load the transformation results into an in-memory representation (such as <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument>) without incurring the overhead of serialization and deserialization of the resulting XML tree.</span></span> <span data-ttu-id="19ad4-138">下面的 C# 代码演示如何将转换结果加载到 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="19ad4-138">The following C# code shows how to load the transformation results into an <xref:System.Xml.XmlDocument> object.</span></span>

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<span data-ttu-id="19ad4-139"><xref:System.Xml.Xsl.XslCompiledTransform> 类不支持转换为 <xref:System.Xml.XmlReader> 对象。</span><span class="sxs-lookup"><span data-stu-id="19ad4-139">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not support transforming to an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="19ad4-140">不过，通过使用 <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> 方法直接从 <xref:System.Xml.XmlWriter> 中加载生成的 XML 树，你可以执行类似操作。</span><span class="sxs-lookup"><span data-stu-id="19ad4-140">However, you can do something similar by using the <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> method to load the resulting XML tree directly from an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="19ad4-141">下面的 C# 代码演示如何使用 <xref:System.Xml.Xsl.XslCompiledTransform> 完成相同的任务。</span><span class="sxs-lookup"><span data-stu-id="19ad4-141">The following C# code shows how to accomplish the same task using <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a><span data-ttu-id="19ad4-142">任意行为</span><span class="sxs-lookup"><span data-stu-id="19ad4-142">Discretionary Behavior</span></span>

<span data-ttu-id="19ad4-143">W3C XSL 转换 (XSLT) 1.0 版建议中涉及到实现提供者可以在哪些方面确定如何处理某种情况。</span><span class="sxs-lookup"><span data-stu-id="19ad4-143">The W3C XSL Transformations (XSLT) Version 1.0 Recommendation includes areas in which the implementation provider may decide how to handle a situation.</span></span> <span data-ttu-id="19ad4-144">这些方面被认为是任意行为。</span><span class="sxs-lookup"><span data-stu-id="19ad4-144">These areas are considered to be discretionary behavior.</span></span> <span data-ttu-id="19ad4-145">在有些方面，<xref:System.Xml.Xsl.XslCompiledTransform> 行为不同于 <xref:System.Xml.Xsl.XslTransform> 类。</span><span class="sxs-lookup"><span data-stu-id="19ad4-145">There are several areas where the <xref:System.Xml.Xsl.XslCompiledTransform> behaves differently than the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="19ad4-146">有关详细信息，请参阅[可恢复的 XSLT 错误](recoverable-xslt-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="19ad4-146">For more information, see [Recoverable XSLT Errors](recoverable-xslt-errors.md).</span></span>

### <a name="extension-objects-and-script-functions"></a><span data-ttu-id="19ad4-147">扩展对象和脚本函数</span><span class="sxs-lookup"><span data-stu-id="19ad4-147">Extension Objects and Script Functions</span></span>

<span data-ttu-id="19ad4-148"><xref:System.Xml.Xsl.XslCompiledTransform> 介绍对使用脚本函数的两个新限制：</span><span class="sxs-lookup"><span data-stu-id="19ad4-148"><xref:System.Xml.Xsl.XslCompiledTransform> introduces two new restrictions on the use of script functions:</span></span>

- <span data-ttu-id="19ad4-149">从 XPath 表达式中只能调用公共方法。</span><span class="sxs-lookup"><span data-stu-id="19ad4-149">Only public methods may be called from XPath expressions.</span></span>

- <span data-ttu-id="19ad4-150">重载之间可以基于自变量数量进行区分。</span><span class="sxs-lookup"><span data-stu-id="19ad4-150">Overloads are distinguishable from each other based on the number of arguments.</span></span> <span data-ttu-id="19ad4-151">如果多个重载具有相同数量的参数，则将引发异常。</span><span class="sxs-lookup"><span data-stu-id="19ad4-151">If more than one overload has the same number of arguments, an exception will be raised.</span></span>

<span data-ttu-id="19ad4-152">在 <xref:System.Xml.Xsl.XslCompiledTransform> 中，脚本函数的绑定（方法名称查找）发生在编译时，当使用 <xref:System.Xml.Xsl.XslCompiledTransform> 加载由 XslTranform 使用的样式表时，这些样式表可能会引发异常。</span><span class="sxs-lookup"><span data-stu-id="19ad4-152">In <xref:System.Xml.Xsl.XslCompiledTransform>, a binding (method name lookup) to script functions occurs at compile time, and style sheets that worked with XslTransform may cause an exception when they are loaded with <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="19ad4-153"><xref:System.Xml.Xsl.XslCompiledTransform> 支持在 `msxsl:using` 元素中具有 `msxsl:assembly` 和 `msxsl:script` 子元素。</span><span class="sxs-lookup"><span data-stu-id="19ad4-153"><xref:System.Xml.Xsl.XslCompiledTransform> supports having `msxsl:using` and `msxsl:assembly` child elements within the `msxsl:script` element.</span></span> <span data-ttu-id="19ad4-154">`msxsl:using` 和 `msxsl:assembly` 元素用于声明其他命名空间和程序集，以便在脚本块中使用。</span><span class="sxs-lookup"><span data-stu-id="19ad4-154">The `msxsl:using` and `msxsl:assembly` elements are used to declare additional namespaces and assemblies for use in the script block.</span></span> <span data-ttu-id="19ad4-155">有关详细信息，请参阅[使用 msxsl:script 的脚本块](script-blocks-using-msxsl-script.md)。</span><span class="sxs-lookup"><span data-stu-id="19ad4-155">See [Script Blocks Using msxsl:script](script-blocks-using-msxsl-script.md) for more information.</span></span>

<span data-ttu-id="19ad4-156"><xref:System.Xml.Xsl.XslCompiledTransform> 禁止扩展对象具有相同数量的自变量的多个重载。</span><span class="sxs-lookup"><span data-stu-id="19ad4-156"><xref:System.Xml.Xsl.XslCompiledTransform> prohibits extension objects that have multiple overloads with the same number of arguments.</span></span>

### <a name="msxml-functions"></a><span data-ttu-id="19ad4-157">MSXML 函数</span><span class="sxs-lookup"><span data-stu-id="19ad4-157">MSXML Functions</span></span>

<span data-ttu-id="19ad4-158">已向 <xref:System.Xml.Xsl.XslCompiledTransform> 类添加对其他 MSXML 函数的支持。</span><span class="sxs-lookup"><span data-stu-id="19ad4-158">Support for additional MSXML functions have been added to the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="19ad4-159">下面的列表说明新增或改进功能：</span><span class="sxs-lookup"><span data-stu-id="19ad4-159">The following list describes new or improved functionality:</span></span>

- <span data-ttu-id="19ad4-160">msxsl:node-set：<xref:System.Xml.Xsl.XslTransform> 要求 [node-set Function](/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) 函数的参数是结果树片段。</span><span class="sxs-lookup"><span data-stu-id="19ad4-160">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> required the argument of the [node-set Function](/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) function to be a result tree fragment.</span></span> <span data-ttu-id="19ad4-161"><xref:System.Xml.Xsl.XslCompiledTransform> 类没有此需求。</span><span class="sxs-lookup"><span data-stu-id="19ad4-161">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have this requirement.</span></span>

- <span data-ttu-id="19ad4-162">msxsl:version:<xref:System.Xml.Xsl.XslCompiledTransform> 支持此函数。</span><span class="sxs-lookup"><span data-stu-id="19ad4-162">msxsl:version: This function is supported in <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

- <span data-ttu-id="19ad4-163">XPath 扩展函数：现在支持 [ms:string-compare Function](/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100))、[ms:utc Function](/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100))、[ms:namespace-uri Function](/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100))、[ms:local-name Function](/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100))、[ms:number Function](/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100))、[ms:format-date Function](/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)) 和 [ms:format-time Function](/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) 函数。</span><span class="sxs-lookup"><span data-stu-id="19ad4-163">XPath extension functions: The [ms:string-compare Function](/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [ms:utc Function](/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [ms:namespace-uri Function](/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [ms:local-name Function](/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [ms:number Function](/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [ms:format-date Function](/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)), and [ms:format-time Function](/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) functions are now supported.</span></span>

- <span data-ttu-id="19ad4-164">与架构相关的 XPath 扩展函数：<xref:System.Xml.Xsl.XslCompiledTransform> 不再支持这些函数。</span><span class="sxs-lookup"><span data-stu-id="19ad4-164">Schema-related XPath extension functions: These functions are not supported natively by <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span> <span data-ttu-id="19ad4-165">但是，它们可以作为扩展函数实现。</span><span class="sxs-lookup"><span data-stu-id="19ad4-165">However, they can be implemented as extension functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="19ad4-166">请参阅</span><span class="sxs-lookup"><span data-stu-id="19ad4-166">See also</span></span>

- [<span data-ttu-id="19ad4-167">XSLT 转换</span><span class="sxs-lookup"><span data-stu-id="19ad4-167">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="19ad4-168">使用 XslCompiledTransform 类</span><span class="sxs-lookup"><span data-stu-id="19ad4-168">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)
