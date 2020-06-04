---
title: Imports 语句-XML 命名空间
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: a3184d68b0e4cdff5d4296a5a638e22b4e83bcde
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404532"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="a8b7e-102">Imports 语句（XML 命名空间）</span><span class="sxs-lookup"><span data-stu-id="a8b7e-102">Imports Statement (XML Namespace)</span></span>

<span data-ttu-id="a8b7e-103">导入用于 XML 文本和 XML 轴属性的 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8b7e-104">语法</span><span class="sxs-lookup"><span data-stu-id="a8b7e-104">Syntax</span></span>

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a><span data-ttu-id="a8b7e-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="a8b7e-105">Parts</span></span>

`xmlNamespacePrefix`  
<span data-ttu-id="a8b7e-106">可选。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-106">Optional.</span></span> <span data-ttu-id="a8b7e-107">XML 元素和特性可以引用的字符串 `xmlNamespaceName` 。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="a8b7e-108">如果未 `xmlNamespacePrefix` 提供，则导入的 xml 命名空间为默认的 xml 命名空间。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="a8b7e-109">必须是有效的 XML 标识符。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="a8b7e-110">有关详细信息，请参阅已[声明的 XML 元素和属性的名称](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-110">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>

`xmlNamespaceName`  
<span data-ttu-id="a8b7e-111">必需。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-111">Required.</span></span> <span data-ttu-id="a8b7e-112">标识要导入的 XML 命名空间的字符串。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-112">The string identifying the XML namespace being imported.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8b7e-113">备注</span><span class="sxs-lookup"><span data-stu-id="a8b7e-113">Remarks</span></span>

<span data-ttu-id="a8b7e-114">可以使用 `Imports` 语句来定义可用于 xml 文本和 xml 轴属性的全局 XML 命名空间，或用作传递给运算符的参数 `GetXmlNamespace` 。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="a8b7e-115">（有关使用 `Imports` 语句导入可用于在代码中使用类型名称的别名的信息，请参阅[Imports 语句（.Net 命名空间和类型）](imports-statement-net-namespace-and-type.md)。）使用语句声明 XML 命名空间的语法与 `Imports` XML 中使用的语法相同。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="a8b7e-116">因此，您可以复制 XML 文件中的命名空间声明，并在语句中使用它 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>

<span data-ttu-id="a8b7e-117">如果要重复创建来自相同命名空间的 XML 元素，XML 命名空间前缀会很有用。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="a8b7e-118">使用语句声明的 XML 命名空间前缀 `Imports` 是全局性的，因为它可用于文件中的所有代码。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="a8b7e-119">当你创建 XML 元素文本以及访问 XML 轴属性时，可以使用此方法。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="a8b7e-120">有关详细信息，请参阅[XML 元素文本](../xml-literals/xml-element-literal.md)和[xml 轴属性](../xml-axis/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-120">For more information, see [XML Element Literal](../xml-literals/xml-element-literal.md) and [XML Axis Properties](../xml-axis/index.md).</span></span>

<span data-ttu-id="a8b7e-121">如果定义不带命名空间前缀的全局 XML 命名空间（例如 `Imports <xmlns="http://SomeNameSpace>"` ），则该命名空间将被视为默认的 xml 命名空间。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="a8b7e-122">默认的 XML 命名空间用于未显式指定命名空间的任何 XML 元素文本或 XML 特性轴属性。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="a8b7e-123">如果指定的命名空间为空命名空间，则也会使用默认命名空间（即 `xmlns=""` ）。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="a8b7e-124">默认的 XML 命名空间不适用于 XML 文本中的 XML 特性或没有命名空间的 XML 特性轴属性。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>

<span data-ttu-id="a8b7e-125">在 XML 文本中定义的 XML 命名空间称为*本地 xml 命名空间*，其优先级高于作为全局语句定义的 xml 命名空间 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="a8b7e-126">语句定义的 XML 命名空间 `Imports` 优先于为 Visual Basic 项目导入的 xml 命名空间。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="a8b7e-127">如果 XML 文本定义了 XML 命名空间，则该本地命名空间不适用于嵌入的表达式。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>

<span data-ttu-id="a8b7e-128">全局 XML 命名空间遵循与 .NET Framework 命名空间相同的作用域和定义规则。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="a8b7e-129">因此，可以在 `Imports` 可导入 .NET Framework 命名空间的任何位置包含语句来定义全局 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="a8b7e-130">这包括代码文件和项目级别导入的命名空间。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="a8b7e-131">有关项目级别导入命名空间的信息，请参阅[引用页、项目设计器（Visual Basic）](/visualstudio/ide/reference/references-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="a8b7e-132">每个源文件可以包含任意多个 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="a8b7e-133">它们必须遵循选项声明，如 `Option Strict` 语句，它们必须位于编程元素声明（如或语句）之前 `Module` `Class` 。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>

## <a name="example"></a><span data-ttu-id="a8b7e-134">示例</span><span class="sxs-lookup"><span data-stu-id="a8b7e-134">Example</span></span>

<span data-ttu-id="a8b7e-135">下面的示例导入使用前缀标识的默认 XML 命名空间和 XML 命名空间 `ns` 。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="a8b7e-136">然后创建使用这两个命名空间的 XML 文本。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-136">It then creates XML literals that use both namespaces.</span></span>

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

<span data-ttu-id="a8b7e-137">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="a8b7e-137">This code displays the following text:</span></span>

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a><span data-ttu-id="a8b7e-138">示例</span><span class="sxs-lookup"><span data-stu-id="a8b7e-138">Example</span></span>

<span data-ttu-id="a8b7e-139">下面的示例导入 XML 命名空间前缀 `ns` 。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="a8b7e-140">然后，它创建一个使用命名空间前缀的 XML 文本，并显示该元素的最终形式。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="a8b7e-141">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="a8b7e-141">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="a8b7e-142">请注意，编译器将 XML 命名空间前缀从全局前缀转换为本地前缀定义。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>

## <a name="example"></a><span data-ttu-id="a8b7e-143">示例</span><span class="sxs-lookup"><span data-stu-id="a8b7e-143">Example</span></span>

<span data-ttu-id="a8b7e-144">下面的示例导入 XML 命名空间前缀 `ns` 。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="a8b7e-145">然后它使用该命名空间前缀来创建 XML 文本并访问具有限定名称 `ns:name` 的第一个子节点。</span><span class="sxs-lookup"><span data-stu-id="a8b7e-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

<span data-ttu-id="a8b7e-146">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="a8b7e-146">This code displays the following text:</span></span>

`Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="a8b7e-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8b7e-147">See also</span></span>

- [<span data-ttu-id="a8b7e-148">XML 元素文本</span><span class="sxs-lookup"><span data-stu-id="a8b7e-148">XML Element Literal</span></span>](../xml-literals/xml-element-literal.md)
- [<span data-ttu-id="a8b7e-149">XML 轴属性</span><span class="sxs-lookup"><span data-stu-id="a8b7e-149">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="a8b7e-150">已声明的 XML 元素和属性的名称</span><span class="sxs-lookup"><span data-stu-id="a8b7e-150">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="a8b7e-151">GetXmlNamespace 运算符</span><span class="sxs-lookup"><span data-stu-id="a8b7e-151">GetXmlNamespace Operator</span></span>](../operators/getxmlnamespace-operator.md)
