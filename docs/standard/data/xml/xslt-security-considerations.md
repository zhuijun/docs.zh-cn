---
title: XSLT 安全注意事项
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
ms.openlocfilehash: 81db764016607ebe6facfc530dbb2bac8e6b8cfe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282502"
---
# <a name="xslt-security-considerations"></a><span data-ttu-id="13f5c-102">XSLT 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="13f5c-102">XSLT Security Considerations</span></span>
<span data-ttu-id="13f5c-103">XSLT 语言具有一组丰富的功能，为您带来强大的功能和灵活性。</span><span class="sxs-lookup"><span data-stu-id="13f5c-103">The XSLT language has a rich set of features that give you a great deal of power and flexibility.</span></span> <span data-ttu-id="13f5c-104">其中的许多功能尽管非常有用，但是也可能会被外部源利用。</span><span class="sxs-lookup"><span data-stu-id="13f5c-104">It includes many features that, while useful, could also be exploited by outside sources.</span></span> <span data-ttu-id="13f5c-105">为了安全地使用 XSLT，必须了解在使用 XSLT 时出现的安全问题类型以及可以用于缓解这些风险的基本策略。</span><span class="sxs-lookup"><span data-stu-id="13f5c-105">In order to use XSLT safely, you must understand the types of security issues that arise when using XSLT, and the basic strategies that you can employ to mitigate these risks.</span></span>  
  
## <a name="xslt-extensions"></a><span data-ttu-id="13f5c-106">XSLT 扩展</span><span class="sxs-lookup"><span data-stu-id="13f5c-106">XSLT Extensions</span></span>  
 <span data-ttu-id="13f5c-107">两种常用的 XSLT 扩展是样式表脚本和扩展对象。</span><span class="sxs-lookup"><span data-stu-id="13f5c-107">Two popular XSLT extensions are style sheet scripting and extension objects.</span></span> <span data-ttu-id="13f5c-108">这些扩展允许 XSLT 处理器执行代码。</span><span class="sxs-lookup"><span data-stu-id="13f5c-108">These extensions allow the XSLT processor to execute code.</span></span>  
  
- <span data-ttu-id="13f5c-109">扩展对象为 XSL 转换添加编程功能。</span><span class="sxs-lookup"><span data-stu-id="13f5c-109">Extension objects add programming capabilities to XSL transformations.</span></span>  
  
- <span data-ttu-id="13f5c-110">脚本可以使用 `msxsl:script` 扩展元素嵌入样式表。</span><span class="sxs-lookup"><span data-stu-id="13f5c-110">Scripts can be embedded in the style sheet using the `msxsl:script` extension element.</span></span>  
  
### <a name="extension-objects"></a><span data-ttu-id="13f5c-111">扩展对象</span><span class="sxs-lookup"><span data-stu-id="13f5c-111">Extension Objects</span></span>  
 <span data-ttu-id="13f5c-112">扩展对象使用 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法添加。</span><span class="sxs-lookup"><span data-stu-id="13f5c-112">Extension objects are added using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="13f5c-113">支持扩展对象要求具有 FullTrust 权限集。</span><span class="sxs-lookup"><span data-stu-id="13f5c-113">The FullTrust permission set is required to support extension objects.</span></span> <span data-ttu-id="13f5c-114">这样可以确保在执行扩展对象代码时，不会发生权限升级。</span><span class="sxs-lookup"><span data-stu-id="13f5c-114">This ensures that elevation of permissions does not happen when extension object code is executed.</span></span> <span data-ttu-id="13f5c-115">如果在没有 FullTrust 权限的情况下尝试调用 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法，将引发安全异常。</span><span class="sxs-lookup"><span data-stu-id="13f5c-115">Attempting to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method without FullTrust permissions results in a security exception being thrown.</span></span>  
  
### <a name="style-sheet-scripts"></a><span data-ttu-id="13f5c-116">样式表脚本</span><span class="sxs-lookup"><span data-stu-id="13f5c-116">Style Sheet Scripts</span></span>  
 <span data-ttu-id="13f5c-117">脚本可以使用 `msxsl:script` 扩展元素嵌入样式表。</span><span class="sxs-lookup"><span data-stu-id="13f5c-117">Scripts can be embedded in a style sheet using the `msxsl:script` extension element.</span></span> <span data-ttu-id="13f5c-118">脚本支持是 <xref:System.Xml.Xsl.XslCompiledTransform> 类上的一项可选功能，默认情况下禁用该功能。</span><span class="sxs-lookup"><span data-stu-id="13f5c-118">Script support is an optional feature on the <xref:System.Xml.Xsl.XslCompiledTransform> class that is disabled by default.</span></span> <span data-ttu-id="13f5c-119">通过将 <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> 属性设置为 `true` 并将 <xref:System.Xml.Xsl.XsltSettings> 对象传递给 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法，可以启用脚本。</span><span class="sxs-lookup"><span data-stu-id="13f5c-119">Scripting can be enabled by setting the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> property to `true` and passing the <xref:System.Xml.Xsl.XsltSettings> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
#### <a name="guidelines"></a><span data-ttu-id="13f5c-120">准则</span><span class="sxs-lookup"><span data-stu-id="13f5c-120">Guidelines</span></span>  
 <span data-ttu-id="13f5c-121">只有样式表来自可信的源时，才应启用脚本。</span><span class="sxs-lookup"><span data-stu-id="13f5c-121">Enable scripting only when the style sheet comes from a trusted source.</span></span> <span data-ttu-id="13f5c-122">如果不能验证样式表的源，或者样式表不是来自可信的源，则为 XSLT 设置参数传入 `null`。</span><span class="sxs-lookup"><span data-stu-id="13f5c-122">If you cannot verify the source of the style sheet, or if the style sheet does not come from a trusted source, pass in `null` for the XSLT settings argument.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="13f5c-123">外部资源</span><span class="sxs-lookup"><span data-stu-id="13f5c-123">External Resources</span></span>  
 <span data-ttu-id="13f5c-124">如果处理器需要解析 URI 引用，XSLT 语言包括 `xsl:import`、`xsl:include` 或 `document()` 函数等功能。</span><span class="sxs-lookup"><span data-stu-id="13f5c-124">The XSLT language has features such as `xsl:import`, `xsl:include`, or the `document()` function, where the processor needs to resolve URI references.</span></span> <span data-ttu-id="13f5c-125"><xref:System.Xml.XmlResolver> 类用于解析外部资源。</span><span class="sxs-lookup"><span data-stu-id="13f5c-125">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="13f5c-126">在下列两种情况下，可能需要解析外部资源：</span><span class="sxs-lookup"><span data-stu-id="13f5c-126">External resources may need to be resolved in the following two cases:</span></span>  
  
- <span data-ttu-id="13f5c-127">在编译样式表时，<xref:System.Xml.XmlResolver> 用于解析 `xsl:import` 和 `xsl:include`。</span><span class="sxs-lookup"><span data-stu-id="13f5c-127">When compiling a style sheet, the <xref:System.Xml.XmlResolver> is used for `xsl:import` and `xsl:include` resolution.</span></span>  
  
- <span data-ttu-id="13f5c-128">在执行转换时，<xref:System.Xml.XmlResolver> 用于解析 `document()` 函数。</span><span class="sxs-lookup"><span data-stu-id="13f5c-128">When executing the transformation, the <xref:System.Xml.XmlResolver> is used to resolve the `document()` function.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="13f5c-129">默认情况下，`document()` 类禁用 <xref:System.Xml.Xsl.XslCompiledTransform> 函数。</span><span class="sxs-lookup"><span data-stu-id="13f5c-129">The `document()` function is disabled by default on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="13f5c-130">通过将 <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> 属性设置为 `true` 并将 <xref:System.Xml.Xsl.XsltSettings> 对象传递给 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法，可以启用此功能。</span><span class="sxs-lookup"><span data-stu-id="13f5c-130">This feature can be enabled by setting the <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> property to `true` and passing the <xref:System.Xml.Xsl.XsltSettings> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
 <span data-ttu-id="13f5c-131"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 和 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法均包括接受 <xref:System.Xml.XmlResolver> 作为一个参数的重载。</span><span class="sxs-lookup"><span data-stu-id="13f5c-131">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods each include overloads that accept an <xref:System.Xml.XmlResolver> as one of its arguments.</span></span> <span data-ttu-id="13f5c-132">如果未指定 <xref:System.Xml.XmlResolver>，将使用没有用户凭据的默认 <xref:System.Xml.XmlUrlResolver>。</span><span class="sxs-lookup"><span data-stu-id="13f5c-132">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
#### <a name="guidelines"></a><span data-ttu-id="13f5c-133">准则</span><span class="sxs-lookup"><span data-stu-id="13f5c-133">Guidelines</span></span>  
 <span data-ttu-id="13f5c-134">只有样式表来自可信的源时，才应启用 `document()` 函数。</span><span class="sxs-lookup"><span data-stu-id="13f5c-134">Enable the `document()` function only when the style sheet comes from a trusted source.</span></span>  
  
 <span data-ttu-id="13f5c-135">下表说明可能需要指定 <xref:System.Xml.XmlResolver> 对象的情况：</span><span class="sxs-lookup"><span data-stu-id="13f5c-135">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="13f5c-136">如果 XSLT 进程需要访问要求进行身份验证的网络资源，可以使用具有必要的凭据的 <xref:System.Xml.XmlResolver>。</span><span class="sxs-lookup"><span data-stu-id="13f5c-136">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="13f5c-137">如果要限制 XSLT 进程可以访问的资源，可以使用具有正确权限集的 <xref:System.Xml.XmlSecureResolver>。</span><span class="sxs-lookup"><span data-stu-id="13f5c-137">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="13f5c-138">如果需要打开自己无法控制的或不可信的资源，请使用 <xref:System.Xml.XmlSecureResolver> 类。</span><span class="sxs-lookup"><span data-stu-id="13f5c-138">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="13f5c-139">如果要自定义行为，可以实现自己的 <xref:System.Xml.XmlResolver> 类并使用该类解析资源。</span><span class="sxs-lookup"><span data-stu-id="13f5c-139">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="13f5c-140">如果要确保不访问任何外部资源，可以为 `null` 自变量指定 <xref:System.Xml.XmlResolver>。</span><span class="sxs-lookup"><span data-stu-id="13f5c-140">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f5c-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="13f5c-141">See also</span></span>

- [<span data-ttu-id="13f5c-142">XSLT 转换</span><span class="sxs-lookup"><span data-stu-id="13f5c-142">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="13f5c-143">在 XSLT 处理期间解析外部资源</span><span class="sxs-lookup"><span data-stu-id="13f5c-143">Resolving External Resources During XSLT Processing</span></span>](resolving-external-resources-during-xslt-processing.md)
- [<span data-ttu-id="13f5c-144">代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="13f5c-144">Code Access Security</span></span>](../../../framework/misc/code-access-security.md)
