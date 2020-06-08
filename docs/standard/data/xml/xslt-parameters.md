---
title: XSLT 参数
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: 7651360b375071c48ba0d23b64881ac794e51e86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282527"
---
# <a name="xslt-parameters"></a><span data-ttu-id="5da28-102">XSLT 参数</span><span class="sxs-lookup"><span data-stu-id="5da28-102">XSLT Parameters</span></span>
<span data-ttu-id="5da28-103">使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法将 XSLT 参数添加到 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>。</span><span class="sxs-lookup"><span data-stu-id="5da28-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="5da28-104">此时，限定名和命名空间 URI 与参数对象关联。</span><span class="sxs-lookup"><span data-stu-id="5da28-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="5da28-105">使用 XSLT 参数</span><span class="sxs-lookup"><span data-stu-id="5da28-105">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="5da28-106">创建 <xref:System.Xml.Xsl.XsltArgumentList> 对象并使用 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> 方法添加参数。</span><span class="sxs-lookup"><span data-stu-id="5da28-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="5da28-107">从样式表调用参数。</span><span class="sxs-lookup"><span data-stu-id="5da28-107">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="5da28-108">将 <xref:System.Xml.Xsl.XsltArgumentList> 对象传递给 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5da28-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="5da28-109">参数类型</span><span class="sxs-lookup"><span data-stu-id="5da28-109">Parameter Types</span></span>  
 <span data-ttu-id="5da28-110">参数对象应对应于某种 W3C 类型。</span><span class="sxs-lookup"><span data-stu-id="5da28-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="5da28-111">下表显示了相应的 W3C 类型、等效的 Microsoft .NET 类（类型），以及 W3C 类型是 XPath 类型还是 XSLT 类型。</span><span class="sxs-lookup"><span data-stu-id="5da28-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="5da28-112">W3C 类型</span><span class="sxs-lookup"><span data-stu-id="5da28-112">W3C type</span></span>|<span data-ttu-id="5da28-113">等效的 .NET 类（类型）</span><span class="sxs-lookup"><span data-stu-id="5da28-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="5da28-114">XPath 还是 XSLT 类型</span><span class="sxs-lookup"><span data-stu-id="5da28-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="5da28-115">XPath</span><span class="sxs-lookup"><span data-stu-id="5da28-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="5da28-116">XPath</span><span class="sxs-lookup"><span data-stu-id="5da28-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="5da28-117">XPath</span><span class="sxs-lookup"><span data-stu-id="5da28-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="5da28-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="5da28-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="5da28-119">XPath</span><span class="sxs-lookup"><span data-stu-id="5da28-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="5da28-120">**XPathNavigator[]**</span><span class="sxs-lookup"><span data-stu-id="5da28-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="5da28-121">XPath</span><span class="sxs-lookup"><span data-stu-id="5da28-121">XPath</span></span>|  
  
 <span data-ttu-id="5da28-122">\*等效于包含单个节点的节点集。</span><span class="sxs-lookup"><span data-stu-id="5da28-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="5da28-123">如果参数对象不属于上述某个类，将根据下列规则进行转换。</span><span class="sxs-lookup"><span data-stu-id="5da28-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="5da28-124">公共语言运行库 (CLR) 数字类型转换为 <xref:System.Double>。</span><span class="sxs-lookup"><span data-stu-id="5da28-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="5da28-125"><xref:System.DateTime> 类型转换为 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="5da28-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="5da28-126"><xref:System.Xml.XPath.IXPathNavigable> 类型转换为 <xref:System.Xml.XPath.XPathNavigator>。</span><span class="sxs-lookup"><span data-stu-id="5da28-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="5da28-127">XPathNavigator[]  转换为 <xref:System.Xml.XPath.XPathNodeIterator>。</span><span class="sxs-lookup"><span data-stu-id="5da28-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="5da28-128">所有其他类型均将引发错误。</span><span class="sxs-lookup"><span data-stu-id="5da28-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5da28-129">示例</span><span class="sxs-lookup"><span data-stu-id="5da28-129">Example</span></span>  
 <span data-ttu-id="5da28-130">下面的示例使用 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> 方法创建一个参数来保存计算的折扣日期。</span><span class="sxs-lookup"><span data-stu-id="5da28-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="5da28-131">折扣日期计算为从订单日期算起的 20 天时间。</span><span class="sxs-lookup"><span data-stu-id="5da28-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="5da28-132">输入</span><span class="sxs-lookup"><span data-stu-id="5da28-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="5da28-133">order.xml</span><span class="sxs-lookup"><span data-stu-id="5da28-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="5da28-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="5da28-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="5da28-135">Output</span><span class="sxs-lookup"><span data-stu-id="5da28-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5da28-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="5da28-136">See also</span></span>

- [<span data-ttu-id="5da28-137">XSLT 转换</span><span class="sxs-lookup"><span data-stu-id="5da28-137">XSLT Transformations</span></span>](xslt-transformations.md)
