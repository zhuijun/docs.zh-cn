---
title: 使用 msxsl:script 的脚本块
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
ms.openlocfilehash: e65308f097e81d844cb04b1ebd5cbcdd8a3aadad
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291989"
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="a178e-102">使用 msxsl:script 的脚本块</span><span class="sxs-lookup"><span data-stu-id="a178e-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="a178e-103"><xref:System.Xml.Xsl.XslCompiledTransform> 类使用 `msxsl:script` 元素支持嵌入的脚本。</span><span class="sxs-lookup"><span data-stu-id="a178e-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="a178e-104">在加载样式表式，任何已定义的函数将通过代码文档对象模型 (CodeDOM) 编译为 Microsoft 中间语言 (MSIL) 并在运行时执行。</span><span class="sxs-lookup"><span data-stu-id="a178e-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="a178e-105">从嵌入的脚本块生成的程序集比为样式表生成的程序集独立。</span><span class="sxs-lookup"><span data-stu-id="a178e-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="a178e-106">启用 XSLT 脚本</span><span class="sxs-lookup"><span data-stu-id="a178e-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="a178e-107">支持嵌入式脚本是 <xref:System.Xml.Xsl.XslCompiledTransform> 类上可选的 XSLT 设置。</span><span class="sxs-lookup"><span data-stu-id="a178e-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="a178e-108">默认情况下禁用脚本支持。</span><span class="sxs-lookup"><span data-stu-id="a178e-108">Script support is disabled by default.</span></span> <span data-ttu-id="a178e-109">要启用脚本支持，创建一个 <xref:System.Xml.Xsl.XsltSettings> 对象，将 <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> 属性设置为 `true`，然后将该对象传递给 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a178e-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a178e-110">只有要求脚本支持并且处于完全可信的环境下时，才应启用 XSLT 脚本。</span><span class="sxs-lookup"><span data-stu-id="a178e-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="a178e-111">msxsl:script 元素定义</span><span class="sxs-lookup"><span data-stu-id="a178e-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="a178e-112">`msxsl:script` 元素是 Microsoft 对 XSLT 1.0 建议的扩展，包括以下定义：</span><span class="sxs-lookup"><span data-stu-id="a178e-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="a178e-113">`msxsl` 前缀绑定到 `urn:schemas-microsoft-com:xslt` 命名空间 URI 上。</span><span class="sxs-lookup"><span data-stu-id="a178e-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="a178e-114">样式表必须包括 `xmlns:msxsl=urn:schemas-microsoft-com:xslt` 命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="a178e-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="a178e-115">`language` 属性是可选项。</span><span class="sxs-lookup"><span data-stu-id="a178e-115">The `language` attribute is optional.</span></span> <span data-ttu-id="a178e-116">属性值是嵌入式代码块的代码语言。</span><span class="sxs-lookup"><span data-stu-id="a178e-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="a178e-117">该语言使用 <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> 方法映射到相应的 CodeDOM 编译器。</span><span class="sxs-lookup"><span data-stu-id="a178e-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a178e-118"><xref:System.Xml.Xsl.XslCompiledTransform> 类可以支持任何 Microsoft .NET 语言，假定在计算机上已安装了相应的提供程序并且已在 machine.config 文件的 system.codedom 部分进行注册。</span><span class="sxs-lookup"><span data-stu-id="a178e-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="a178e-119">如果未指定 `language` 属性，则默认语言为 JScript。</span><span class="sxs-lookup"><span data-stu-id="a178e-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="a178e-120">语言名称不区分大小写，所以“JavaScript”和“javascript”等效。</span><span class="sxs-lookup"><span data-stu-id="a178e-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="a178e-121">`implements-prefix` 属性是必选项。</span><span class="sxs-lookup"><span data-stu-id="a178e-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="a178e-122">此属性用于声明命名空间并将其与脚本块关联。</span><span class="sxs-lookup"><span data-stu-id="a178e-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="a178e-123">此属性的值是表示命名空间的前缀。</span><span class="sxs-lookup"><span data-stu-id="a178e-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="a178e-124">此前缀可以在样式表中的某一位置定义。</span><span class="sxs-lookup"><span data-stu-id="a178e-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a178e-125">当使用 `msxsl:script` 元素时，强烈建议无论使用何种语言，都应将脚本放置在 CDATA 节内。</span><span class="sxs-lookup"><span data-stu-id="a178e-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="a178e-126">因为脚本可以包含给定语言的运算符、标识符或分隔符，如果不包含在 CDATA 节中，可能会错误地作为 XML 解释。</span><span class="sxs-lookup"><span data-stu-id="a178e-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="a178e-127">以下 XML 显示可以放入代码的 CDATA 节的模板。</span><span class="sxs-lookup"><span data-stu-id="a178e-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="a178e-128">脚本函数</span><span class="sxs-lookup"><span data-stu-id="a178e-128">Script Functions</span></span>  
 <span data-ttu-id="a178e-129">函数可以在 `msxsl:script` 元素内声明。</span><span class="sxs-lookup"><span data-stu-id="a178e-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="a178e-130">声明函数时，该函数包含在脚本块中。</span><span class="sxs-lookup"><span data-stu-id="a178e-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="a178e-131">样式表可以包含多个脚本块，每个脚本块彼此独立运行。</span><span class="sxs-lookup"><span data-stu-id="a178e-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="a178e-132">也就是说，如果在脚本块的内部执行，则无法调用在其他脚本块中定义的函数，除非该脚本块声明为具有同一命名空间和同一脚本语言。</span><span class="sxs-lookup"><span data-stu-id="a178e-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="a178e-133">由于每个脚本块都可以使用自己的语言，因此脚本块的分析将遵照语言分析器的语法规则进行，我们建议您使用适合所使用语言的语法。</span><span class="sxs-lookup"><span data-stu-id="a178e-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="a178e-134">例如，如果在 Microsoft C# 脚本块中，请使用 C# 注释语法。</span><span class="sxs-lookup"><span data-stu-id="a178e-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="a178e-135">为函数提供的参数和返回值可以是任意类型。</span><span class="sxs-lookup"><span data-stu-id="a178e-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="a178e-136">因为 W3C XPath 类型是公共语言运行库 (CLR) 类型的子集，所以，对不属于 XPath 类型的类型进行类型转换。</span><span class="sxs-lookup"><span data-stu-id="a178e-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="a178e-137">下表显示相应的 W3C 类型和等效的 CLR 类型。</span><span class="sxs-lookup"><span data-stu-id="a178e-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="a178e-138">W3C 类型</span><span class="sxs-lookup"><span data-stu-id="a178e-138">W3C type</span></span>|<span data-ttu-id="a178e-139">CLR 类型</span><span class="sxs-lookup"><span data-stu-id="a178e-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="a178e-140">CLR 数字类型转换为 <xref:System.Double>。</span><span class="sxs-lookup"><span data-stu-id="a178e-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="a178e-141"><xref:System.DateTime> 类型转换为 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="a178e-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="a178e-142"><xref:System.Xml.XPath.IXPathNavigable> 类型转换为 <xref:System.Xml.XPath.XPathNavigator>。</span><span class="sxs-lookup"><span data-stu-id="a178e-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="a178e-143">XPathNavigator[]  转换为 <xref:System.Xml.XPath.XPathNodeIterator>。</span><span class="sxs-lookup"><span data-stu-id="a178e-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="a178e-144">所有其他类型均将引发错误。</span><span class="sxs-lookup"><span data-stu-id="a178e-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="a178e-145">导入命名空间和程序集</span><span class="sxs-lookup"><span data-stu-id="a178e-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="a178e-146"><xref:System.Xml.Xsl.XslCompiledTransform> 类预定义了一组程序集和命名空间，默认情况下，通过 `msxsl:script` 元素支持这些程序集和命名空间。</span><span class="sxs-lookup"><span data-stu-id="a178e-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="a178e-147">但是，可以通过在 `msxsl:script` 块中导入程序集和命名空间，使用属于不在预定义列表中的某个命名空间的类和成员。</span><span class="sxs-lookup"><span data-stu-id="a178e-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="a178e-148">程序集</span><span class="sxs-lookup"><span data-stu-id="a178e-148">Assemblies</span></span>  
 <span data-ttu-id="a178e-149">默认情况下引用下列两个程序集：</span><span class="sxs-lookup"><span data-stu-id="a178e-149">The following two assemblies are referenced by default:</span></span>  
  
- <span data-ttu-id="a178e-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="a178e-150">System.dll</span></span>  
  
- <span data-ttu-id="a178e-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="a178e-151">System.Xml.dll</span></span>  
  
- <span data-ttu-id="a178e-152">Microsoft.VisualBasic.dll（如果脚本语言为 VB）</span><span class="sxs-lookup"><span data-stu-id="a178e-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="a178e-153">可以使用 `msxsl:assembly` 元素导入其他程序集。</span><span class="sxs-lookup"><span data-stu-id="a178e-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="a178e-154">包括在编译样式表时的程序集。</span><span class="sxs-lookup"><span data-stu-id="a178e-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="a178e-155">`msxsl:assembly` 元素具有以下定义：</span><span class="sxs-lookup"><span data-stu-id="a178e-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="a178e-156">`name` 属性包含程序集的名称，`href` 属性包含程序集的路径。</span><span class="sxs-lookup"><span data-stu-id="a178e-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="a178e-157">程序集名称可以是全名，例如“System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089”，也可以是缩写名称，例如“System.Web”。</span><span class="sxs-lookup"><span data-stu-id="a178e-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="a178e-158">命名空间</span><span class="sxs-lookup"><span data-stu-id="a178e-158">Namespaces</span></span>  
 <span data-ttu-id="a178e-159">默认情况下包括下列命名空间：</span><span class="sxs-lookup"><span data-stu-id="a178e-159">The following namespaces are included by default:</span></span>  
  
- <span data-ttu-id="a178e-160">System</span><span class="sxs-lookup"><span data-stu-id="a178e-160">System</span></span>  
  
- <span data-ttu-id="a178e-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="a178e-161">System.Collection</span></span>  
  
- <span data-ttu-id="a178e-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="a178e-162">System.Text</span></span>  
  
- <span data-ttu-id="a178e-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="a178e-163">System.Text.RegularExpressions</span></span>  
  
- <span data-ttu-id="a178e-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="a178e-164">System.Xml</span></span>  
  
- <span data-ttu-id="a178e-165">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="a178e-165">System.Xml.Xsl</span></span>  
  
- <span data-ttu-id="a178e-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="a178e-166">System.Xml.XPath</span></span>  
  
- <span data-ttu-id="a178e-167">Microsoft.VisualBasic（如果脚本语言为 VB）</span><span class="sxs-lookup"><span data-stu-id="a178e-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="a178e-168">可以使用 `namespace` 属性添加对其他命名空间的支持。</span><span class="sxs-lookup"><span data-stu-id="a178e-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="a178e-169">属性值是命名空间的名称。</span><span class="sxs-lookup"><span data-stu-id="a178e-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="a178e-170">示例</span><span class="sxs-lookup"><span data-stu-id="a178e-170">Example</span></span>  
 <span data-ttu-id="a178e-171">已知圆的半径，下面的示例使用嵌入脚本计算圆的周长。</span><span class="sxs-lookup"><span data-stu-id="a178e-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="a178e-172">number.xml</span><span class="sxs-lookup"><span data-stu-id="a178e-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="a178e-173">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="a178e-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="a178e-174">Output</span><span class="sxs-lookup"><span data-stu-id="a178e-174">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a178e-175">请参阅</span><span class="sxs-lookup"><span data-stu-id="a178e-175">See also</span></span>

- [<span data-ttu-id="a178e-176">XSLT 转换</span><span class="sxs-lookup"><span data-stu-id="a178e-176">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="a178e-177">动态源代码生成和编译</span><span class="sxs-lookup"><span data-stu-id="a178e-177">Dynamic Source Code Generation and Compilation</span></span>](../../../framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
