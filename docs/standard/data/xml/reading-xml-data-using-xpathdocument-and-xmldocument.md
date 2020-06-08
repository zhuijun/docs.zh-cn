---
title: 使用 XPathDocument 和 XmlDocument 读取 XML 数据
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
ms.openlocfilehash: da1cb81c819e55f572e9faaabef4dd49ee7397de
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288675"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a><span data-ttu-id="52809-102">使用 XPathDocument 和 XmlDocument 读取 XML 数据</span><span class="sxs-lookup"><span data-stu-id="52809-102">Reading XML Data using XPathDocument and XmlDocument</span></span>
<span data-ttu-id="52809-103">可以通过两种方式读取 <xref:System.Xml.XPath?displayProperty=nameWithType> 命名空间中的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="52809-103">There are two ways to read an XML document in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="52809-104">一种方式是使用只读 <xref:System.Xml.XPath.XPathDocument> 类读取 XML 文档，另一种方式是使用 <xref:System.Xml.XmlDocument> 命名空间中可编辑的 <xref:System.Xml?displayProperty=nameWithType> 类读取 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="52809-104">One is to read an XML document using the read-only <xref:System.Xml.XPath.XPathDocument> class and the other is to read an XML document using the editable <xref:System.Xml.XmlDocument> class in the <xref:System.Xml?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a><span data-ttu-id="52809-105">使用 XPathDocument 类读取 XML 文档</span><span class="sxs-lookup"><span data-stu-id="52809-105">Reading XML Documents using the XPathDocument Class</span></span>  
 <span data-ttu-id="52809-106"><xref:System.Xml.XPath.XPathDocument> 类使用 XPath 数据模型提供 XML 文档在内存中的快速只读表示形式。</span><span class="sxs-lookup"><span data-stu-id="52809-106">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="52809-107"><xref:System.Xml.XPath.XPathDocument> 类的实例使用其六个构造函数之一创建。</span><span class="sxs-lookup"><span data-stu-id="52809-107">Instances of the <xref:System.Xml.XPath.XPathDocument> class are created using one of its six constructors.</span></span> <span data-ttu-id="52809-108">通过这些构造函数，可以使用 <xref:System.IO.Stream>、<xref:System.IO.TextReader> 或 <xref:System.Xml.XmlReader> 对象以及 XML 文件的 `string` 路径来读取 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="52809-108">These constructors allow you to read an XML document using a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="52809-109">以下示例说明如何使用 <xref:System.Xml.XPath.XPathDocument> 类的 `string` 构造函数来读取 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="52809-109">The following example illustrates using the <xref:System.Xml.XPath.XPathDocument> class's `string` constructor to read an XML document.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a><span data-ttu-id="52809-110">使用 XmlDocument 类读取 XML 文档</span><span class="sxs-lookup"><span data-stu-id="52809-110">Reading XML Documents using the XmlDocument Class</span></span>  
 <span data-ttu-id="52809-111"><xref:System.Xml.XmlDocument> 类是实现 W3C 文档对象模型 (DOM) 级别 1 核心和核心 DOM 级别 2 的 XML 文档在内存中的可编辑表示形式。</span><span class="sxs-lookup"><span data-stu-id="52809-111">The <xref:System.Xml.XmlDocument> class is an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="52809-112"><xref:System.Xml.XmlDocument> 类的实例使用其三个构造函数之一创建。</span><span class="sxs-lookup"><span data-stu-id="52809-112">Instances of the <xref:System.Xml.XmlDocument> class are created using one of its three constructors.</span></span> <span data-ttu-id="52809-113">可以通过调用没有参数的 <xref:System.Xml.XmlDocument> 类构造函数，创建新的空 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="52809-113">You can create a new, empty <xref:System.Xml.XmlDocument> object by calling the <xref:System.Xml.XmlDocument> class constructor with no parameters.</span></span> <span data-ttu-id="52809-114">在调用了构造函数之后，使用 <xref:System.Xml.XmlDocument.Load%2A> 方法以及 XML 文件的 <xref:System.Xml.XmlDocument> 路径将 XML 数据从 <xref:System.IO.Stream>、<xref:System.IO.TextReader> 或 <xref:System.Xml.XmlReader> 对象加载到新的 `string` 对象中。</span><span class="sxs-lookup"><span data-stu-id="52809-114">After calling the constructor, use the <xref:System.Xml.XmlDocument.Load%2A> method to load XML data into the new <xref:System.Xml.XmlDocument> object from a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="52809-115">以下示例说明如何使用没有参数的 <xref:System.Xml.XmlDocument> 类构造函数以及 <xref:System.Xml.XmlDocument.Load%2A> 方法来读取 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="52809-115">The following example illustrates using the <xref:System.Xml.XmlDocument> class constructor with no parameters and the <xref:System.Xml.XmlDocument.Load%2A> method to read an XML document.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a><span data-ttu-id="52809-116">确定 XML 文档的编码</span><span class="sxs-lookup"><span data-stu-id="52809-116">Determining the Encoding of an XML Document</span></span>  
 <span data-ttu-id="52809-117"><xref:System.Xml.XmlReader> 对象可以用于读取 XML 文档并创建 <xref:System.Xml.XPath.XPathDocument> 和 <xref:System.Xml.XmlDocument> 对象，如前面各节所示。</span><span class="sxs-lookup"><span data-stu-id="52809-117">An <xref:System.Xml.XmlReader> object can be used to read an XML document and to create <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> objects as shown in the previous sections.</span></span> <span data-ttu-id="52809-118">但是，<xref:System.Xml.XmlReader> 对象可能会读取未编码的数据，因此，不会提供任何编码信息。</span><span class="sxs-lookup"><span data-stu-id="52809-118">However, an <xref:System.Xml.XmlReader> object may read data that is not encoded and as a result does not provide any encoding information.</span></span>  
  
 <span data-ttu-id="52809-119"><xref:System.Xml.XmlTextReader> 类从 <xref:System.Xml.XmlReader> 类继承，使用其 <xref:System.Xml.XmlTextReader.Encoding%2A> 属性提供编码信息，并且可以用于创建 <xref:System.Xml.XPath.XPathDocument> 对象或 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="52809-119">The <xref:System.Xml.XmlTextReader> class inherits from the <xref:System.Xml.XmlReader> class, provides encoding information using its <xref:System.Xml.XmlTextReader.Encoding%2A> property, and can be used to create an <xref:System.Xml.XPath.XPathDocument> object or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="52809-120">有关 <xref:System.Xml.XmlTextReader> 类提供的编码信息的更多信息，请参见 <xref:System.Xml.XmlTextReader.Encoding%2A> 类参考文档中的 <xref:System.Xml.XmlTextReader> 属性。</span><span class="sxs-lookup"><span data-stu-id="52809-120">For more information about the encoding information provided by the <xref:System.Xml.XmlTextReader> class, see the <xref:System.Xml.XmlTextReader.Encoding%2A> property in the <xref:System.Xml.XmlTextReader> class reference documentation.</span></span>  
  
## <a name="creating-xpathnavigator-objects"></a><span data-ttu-id="52809-121">创建 XPathNavigator 对象</span><span class="sxs-lookup"><span data-stu-id="52809-121">Creating XPathNavigator Objects</span></span>  
 <span data-ttu-id="52809-122">在将 XML 文档读入 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 对象之后，可以创建一个 <xref:System.Xml.XPath.XPathNavigator> 对象，以选择、计算、浏览和（在有些情况下）编辑基础 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="52809-122">After you have read an XML document into either an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, you can create an <xref:System.Xml.XPath.XPathNavigator> object to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="52809-123">除了 <xref:System.Xml.XPath.XPathDocument> 类之外，<xref:System.Xml.XmlDocument> 和 <xref:System.Xml.XmlNode> 类也实现了 <xref:System.Xml.XPath.IXPathNavigable> 命名空间的 <xref:System.Xml.XPath?displayProperty=nameWithType> 接口。</span><span class="sxs-lookup"><span data-stu-id="52809-123">Both the <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> classes, in addition to the <xref:System.Xml.XmlNode> class, implement the <xref:System.Xml.XPath.IXPathNavigable> interface of the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="52809-124">因此，所有三个类均提供返回 <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> 对象的 <xref:System.Xml.XPath.XPathNavigator> 方法。</span><span class="sxs-lookup"><span data-stu-id="52809-124">As a result, all three classes provide a <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> method that returns an <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a><span data-ttu-id="52809-125">使用 XPathNavigator 类编辑 XML 文档</span><span class="sxs-lookup"><span data-stu-id="52809-125">Editing XML Documents using the XPathNavigator Class</span></span>  
 <span data-ttu-id="52809-126">除了选择、计算和浏览 XML 数据之外，在有些情况下，<xref:System.Xml.XPath.XPathNavigator> 类还可以用于编辑 XML 文档，这取决于创建文档的对象。</span><span class="sxs-lookup"><span data-stu-id="52809-126">In addition to selecting, evaluating, and navigating XML data, the <xref:System.Xml.XPath.XPathNavigator> class can be used to edit an XML document in some cases, based on the object that created it.</span></span>  
  
 <span data-ttu-id="52809-127"><xref:System.Xml.XPath.XPathDocument> 类为只读类，而 <xref:System.Xml.XmlDocument> 类是可编辑的类，因此，从 <xref:System.Xml.XPath.XPathNavigator> 对象创建的 <xref:System.Xml.XPath.XPathDocument> 对象不能用于编辑 XML 文档，而从 <xref:System.Xml.XmlDocument> 对象创建的对象可以编辑。</span><span class="sxs-lookup"><span data-stu-id="52809-127">The <xref:System.Xml.XPath.XPathDocument> class is read-only while the <xref:System.Xml.XmlDocument> class is editable and as a result, <xref:System.Xml.XPath.XPathNavigator> objects created from an <xref:System.Xml.XPath.XPathDocument> object cannot be used to edit an XML document while those created from an <xref:System.Xml.XmlDocument> object can.</span></span> <span data-ttu-id="52809-128"><xref:System.Xml.XPath.XPathDocument> 类只能用于读取 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="52809-128">The <xref:System.Xml.XPath.XPathDocument> class should be used to read an XML document only.</span></span> <span data-ttu-id="52809-129">如果需要编辑 XML 文档，或要求访问 <xref:System.Xml.XmlDocument> 类提供的其他功能（例如事件处理），应使用 <xref:System.Xml.XmlDocument> 类。</span><span class="sxs-lookup"><span data-stu-id="52809-129">In cases where you need to edit an XML document, or require access to the additional functionality provided by the <xref:System.Xml.XmlDocument> class, like event handling, the <xref:System.Xml.XmlDocument> class should be used.</span></span>  
  
 <span data-ttu-id="52809-130"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 类的 <xref:System.Xml.XPath.XPathNavigator> 属性指定 <xref:System.Xml.XPath.XPathNavigator> 对象是否可以编辑 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="52809-130">The <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class specifies if an <xref:System.Xml.XPath.XPathNavigator> object may edit XML data.</span></span>  
  
 <span data-ttu-id="52809-131">下表说明了每个类的 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="52809-131">The following table describes the value of the <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property for each class.</span></span>  
  
|<span data-ttu-id="52809-132"><xref:System.Xml.XPath.IXPathNavigable> 实现</span><span class="sxs-lookup"><span data-stu-id="52809-132"><xref:System.Xml.XPath.IXPathNavigable> Implementation</span></span>|<span data-ttu-id="52809-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 值</span><span class="sxs-lookup"><span data-stu-id="52809-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Value</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a><span data-ttu-id="52809-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="52809-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="52809-135">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="52809-135">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="52809-136">使用 XPathNavigator 访问 XML 数据</span><span class="sxs-lookup"><span data-stu-id="52809-136">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="52809-137">使用 XPathNavigator 编辑 XML 数据</span><span class="sxs-lookup"><span data-stu-id="52809-137">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="52809-138">使用 XPathNavigator 验证架构</span><span class="sxs-lookup"><span data-stu-id="52809-138">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
