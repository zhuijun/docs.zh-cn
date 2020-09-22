---
title: XPath 命名空间浏览
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: bad5e1245c7f48c114bd2a1809822cc131dad75a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551954"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="6d2d7-102">XPath 命名空间浏览</span><span class="sxs-lookup"><span data-stu-id="6d2d7-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="6d2d7-103">要对 XML 文档使用 XPath 查询，必须正确定位 XML 命名空间以及命名空间中包含的元素。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="6d2d7-104">命名空间可防止在多个上下文中使用名称时可能产生的混淆情况；例如，名称 `ID` 可能引用与 XML 文档的不同元素相关联的多个标识符。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="6d2d7-105">命名空间语法指定了 URI、名称和前缀，可区分 XML 文档的各个元素。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="6d2d7-106">本主题中的示例演示了通过 <xref:System.Xml.XPath.XPathNavigator> 在浏览 XML 文档时使用前缀。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="6d2d7-107">有关命名空间和语法的详细信息，请参阅 [XML 文件：了解 XML 命名空间](/previous-versions/dotnet/articles/bb986013(v=msdn.10))。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="6d2d7-108">命名空间声明</span><span class="sxs-lookup"><span data-stu-id="6d2d7-108">Namespace Declarations</span></span>  
 <span data-ttu-id="6d2d7-109">命名空间声明使得在使用 <xref:System.Xml.XPath.XPathNavigator> 的实例时，很容易区分和定位 XML 文档的各个元素。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="6d2d7-110">命名空间前缀提供了一种简化的语法，用来定位命名空间。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="6d2d7-111">前缀由以下形式定义：`<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` 在此语法中，前缀“`e`”是命名空间的正式 URI 的缩写。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="6d2d7-112">使用此语法可以将 `Body` 元素标识为 `Envelope` 命名空间的成员：`e:Body`。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="6d2d7-113">在下一节的浏览示例中，下面的 XML 文档将用作 `response.xml`。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="6d2d7-114">通过命名空间前缀进行浏览</span><span class="sxs-lookup"><span data-stu-id="6d2d7-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="6d2d7-115">本节中的代码使用 <xref:System.Xml.XPath.XPathNavigator> 和 <xref:System.Xml.XmlNamespaceManager> 对象，从前一节的 XML 文档中选择 `Search` 元素。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="6d2d7-116">查询 `xpath` 对路径中的每个元素都包含了命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="6d2d7-117">指定包含每个元素的命名空间的精确标识，可确保通过 `Search` 方法正确浏览至 <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> 元素。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```csharp  
using (XmlReader reader = XmlReader.Create("response.xml"))  
{  
    XPathDocument doc = new XPathDocument(reader);  
    XPathNavigator nav = doc.CreateNavigator();
  
    XmlNamespaceManager nsmgr = new XmlNamespaceManager(nav.NameTable);  
    nsmgr.AddNamespace("e", @"http://schemas.xmlsoap.org/soap/envelope/");  
    nsmgr.AddNamespace("s", @"http://schemas.microsoft.com/v1/Search");  
    nsmgr.AddNamespace("r", @"http://schemas.microsoft.com/v1/Search/metadata");  
    nsmgr.AddNamespace("i", @"http://www.w3.org/2001/XMLSchema-instance");  
  
    string xpath = "/e:Envelope/e:Body/s:Search";  
  
    XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
    Console.WriteLine("Element Prefix:" + element.Prefix +
    " Local name:" + element.LocalName);  
    Console.WriteLine("Namespace URI: " + element.NamespaceURI);  
}  
```  
  
 <span data-ttu-id="6d2d7-118">完全限定的命名空间和名称的精确度不仅仅是一种方便。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="6d2d7-119">对前面的示例中的文档定义和代码进行一项小实验，可以验证如果不使用完全限定的元素名称进行浏览，就会引发异常。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="6d2d7-120">例如，元素定义为 `<Search xmlns="http://schemas.microsoft.com/v1/Search">`，而查询字符串 `xpath = "/s:Envelope/s:Body/Search";` 没有对 `Search` 元素使用命名空间前缀，则此查询将返回 `null`，而不是 `Search` 元素。</span><span class="sxs-lookup"><span data-stu-id="6d2d7-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2d7-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="6d2d7-121">See also</span></span>

- [<span data-ttu-id="6d2d7-122">使用 XPathNavigator 访问 XML 数据</span><span class="sxs-lookup"><span data-stu-id="6d2d7-122">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="6d2d7-123">使用 XPathNavigator 选择、计算和匹配 XML 数据</span><span class="sxs-lookup"><span data-stu-id="6d2d7-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
