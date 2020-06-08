---
title: 在 XSLT 处理期间解析外部资源
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: d38aea1a54c93b00ec14c6aac7ed11ceba288f7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291495"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="6bcbc-102">在 XSLT 处理期间解析外部资源</span><span class="sxs-lookup"><span data-stu-id="6bcbc-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="6bcbc-103">XSLT 转换过程中会有几个场合需要解析外部资源。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="6bcbc-104">使用 XmlResolver 类</span><span class="sxs-lookup"><span data-stu-id="6bcbc-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="6bcbc-105"><xref:System.Xml.XmlResolver> 类用于解析外部资源。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="6bcbc-106">下表说明在 XSLT 处理期间 <xref:System.Xml.XmlResolver> 参与的时间。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="6bcbc-107">XSLT 任务</span><span class="sxs-lookup"><span data-stu-id="6bcbc-107">XSLT task</span></span>|<span data-ttu-id="6bcbc-108">XmlResolver 的用途</span><span class="sxs-lookup"><span data-stu-id="6bcbc-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="6bcbc-109">编译样式表。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-109">Compile the style sheet.</span></span>|<span data-ttu-id="6bcbc-110">解析样式表的 URI。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="6bcbc-111">－和－</span><span class="sxs-lookup"><span data-stu-id="6bcbc-111">-and-</span></span><br /><br /> <span data-ttu-id="6bcbc-112">解析任何 `xsl:import` 或 `xsl:include` 元素中的 URI 引用。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="6bcbc-113">执行样式表。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-113">Execute the style sheet.</span></span>|<span data-ttu-id="6bcbc-114">解析上下文文档的 URI。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="6bcbc-115">－和－</span><span class="sxs-lookup"><span data-stu-id="6bcbc-115">-and-</span></span><br /><br /> <span data-ttu-id="6bcbc-116">解析任何 XSLT `document()` 函数中的 URI 引用。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="6bcbc-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 和 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法包括使用 <xref:System.Xml.XmlResolver> 对象作为一个参数的重载。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="6bcbc-118">如果未指定 <xref:System.Xml.XmlResolver>，将使用没有用户凭据的默认 <xref:System.Xml.XmlUrlResolver>。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="6bcbc-119">下表说明可能需要指定 <xref:System.Xml.XmlResolver> 对象的情况：</span><span class="sxs-lookup"><span data-stu-id="6bcbc-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="6bcbc-120">如果 XSLT 进程需要访问要求进行身份验证的网络资源，可以使用具有必要的凭据的 <xref:System.Xml.XmlResolver>。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="6bcbc-121">如果要限制 XSLT 进程可以访问的资源，可以使用具有正确权限集的 <xref:System.Xml.XmlSecureResolver>。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="6bcbc-122">如果需要打开自己无法控制的或不可信的资源，请使用 <xref:System.Xml.XmlSecureResolver> 类。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="6bcbc-123">如果要自定义行为，可以实现自己的 <xref:System.Xml.XmlResolver> 类并使用该类解析资源。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="6bcbc-124">如果要确保不访问任何外部资源，可以为 `null` 自变量指定 <xref:System.Xml.XmlResolver>。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bcbc-125">示例</span><span class="sxs-lookup"><span data-stu-id="6bcbc-125">Example</span></span>  
 <span data-ttu-id="6bcbc-126">以下示例编译存储在网络资源上的样式表。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="6bcbc-127"><xref:System.Xml.XmlUrlResolver> 对象指定访问该样式表所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="6bcbc-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="6bcbc-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="6bcbc-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="6bcbc-129">XSLT 转换</span><span class="sxs-lookup"><span data-stu-id="6bcbc-129">XSLT Transformations</span></span>](xslt-transformations.md)
