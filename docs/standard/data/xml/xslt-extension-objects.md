---
title: XSLT 扩展对象
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: ff50cbb561f9da5ea0877ded1de6fd3d5c424a7e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555954"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="71829-102">XSLT 扩展对象</span><span class="sxs-lookup"><span data-stu-id="71829-102">XSLT Extension Objects</span></span>
<span data-ttu-id="71829-103">扩展对象用于扩展样式表的功能。</span><span class="sxs-lookup"><span data-stu-id="71829-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="71829-104">扩展对象通过 <xref:System.Xml.Xsl.XsltArgumentList> 类来维护。</span><span class="sxs-lookup"><span data-stu-id="71829-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="71829-105">与使用嵌入脚本相比，使用扩展对象具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="71829-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
- <span data-ttu-id="71829-106">改善了类的包装和重用。</span><span class="sxs-lookup"><span data-stu-id="71829-106">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="71829-107">使样式表可以更小而且更容易维护。</span><span class="sxs-lookup"><span data-stu-id="71829-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="71829-108">使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法将 XSLT 扩展对象添加到 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 对象。</span><span class="sxs-lookup"><span data-stu-id="71829-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="71829-109">此时，限定名和命名空间 URI 与扩展对象关联。</span><span class="sxs-lookup"><span data-stu-id="71829-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71829-110">调用 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法要求具有 FullTrust 权限集。</span><span class="sxs-lookup"><span data-stu-id="71829-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="71829-111">有关详细信息，请参阅[代码访问安全性](../../../framework/misc/code-access-security.md)和[命名权限集](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="71829-111">For more information, see [Code Access Security](../../../framework/misc/code-access-security.md) and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="71829-112">从扩展对象返回的数据类型是四种 XPath 基本数据类型之一：`number`、`string`、`Boolean` 和 `node set`。</span><span class="sxs-lookup"><span data-stu-id="71829-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="71829-113">任何使用 `params` 关键字定义的方法允许传递未指定的参数数目，<xref:System.Xml.Xsl.XslCompiledTransform> 类目前不支持。</span><span class="sxs-lookup"><span data-stu-id="71829-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="71829-114">利用通过 `params` 关键字定义的方法的 XSLT 样式表也无法正确使用。</span><span class="sxs-lookup"><span data-stu-id="71829-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="71829-115">有关详细信息，请参阅 [params](../../../csharp/language-reference/keywords/params.md)。</span><span class="sxs-lookup"><span data-stu-id="71829-115">For details, see [params](../../../csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="71829-116">使用 XSLT 扩展对象</span><span class="sxs-lookup"><span data-stu-id="71829-116">To use an XSLT extension object</span></span>  
  
1. <span data-ttu-id="71829-117">创建 <xref:System.Xml.Xsl.XsltArgumentList> 对象并使用 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法添加扩展对象。</span><span class="sxs-lookup"><span data-stu-id="71829-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2. <span data-ttu-id="71829-118">从样式表调用扩展对象。</span><span class="sxs-lookup"><span data-stu-id="71829-118">Call the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="71829-119">将 <xref:System.Xml.Xsl.XsltArgumentList> 对象传递给 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="71829-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71829-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="71829-120">See also</span></span>

- [<span data-ttu-id="71829-121">XSLT 转换</span><span class="sxs-lookup"><span data-stu-id="71829-121">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="71829-122">XSLT 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="71829-122">XSLT Security Considerations</span></span>](xslt-security-considerations.md)
