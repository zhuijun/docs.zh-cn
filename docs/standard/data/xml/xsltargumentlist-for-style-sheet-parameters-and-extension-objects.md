---
title: 样式表参数和扩展对象的 XsltArgumentList
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
ms.openlocfilehash: 1c69a6e78207e146c8dbd6cdc252f27f36ab37a2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281695"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a><span data-ttu-id="6f215-102">样式表参数和扩展对象的 XsltArgumentList</span><span class="sxs-lookup"><span data-stu-id="6f215-102">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>
<span data-ttu-id="6f215-103"><xref:System.Xml.Xsl.XsltArgumentList> 类包含可扩展样式表语言转换 (XSLT) 参数和 XSLT 扩展对象。</span><span class="sxs-lookup"><span data-stu-id="6f215-103">The <xref:System.Xml.Xsl.XsltArgumentList> class contains Extensible Stylesheet Language for Transformations (XSLT) parameters and XSLT extension objects.</span></span> <span data-ttu-id="6f215-104">传入 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法后，这些参数和扩展对象可以从样式表中进行调用。</span><span class="sxs-lookup"><span data-stu-id="6f215-104">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f215-105"><xref:System.Xml.Xsl.XslTransform> 和 <xref:System.Xml.Xsl.XsltArgumentList> 类在 .NET Framework 2.0 中已过时。</span><span class="sxs-lookup"><span data-stu-id="6f215-105">The <xref:System.Xml.Xsl.XslTransform> and <xref:System.Xml.Xsl.XsltArgumentList> classes are obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="6f215-106">可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 类执行 XSLT 转换。</span><span class="sxs-lookup"><span data-stu-id="6f215-106">You can perform XSLT transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="6f215-107">请参阅[使用 XslCompiledTransform 类](using-the-xslcompiledtransform-class.md)和[从 XslTransform 类迁移](migrating-from-the-xsltransform-class.md)，以获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="6f215-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="6f215-108"><xref:System.Xml.Xsl.XsltArgumentList> 类包含 XSLT 参数和 XSLT 扩展对象。</span><span class="sxs-lookup"><span data-stu-id="6f215-108">The <xref:System.Xml.Xsl.XsltArgumentList> class contains XSLT parameters and XSLT extension objects.</span></span> <span data-ttu-id="6f215-109">传入 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法后，这些参数和扩展对象可以从样式表中进行调用。</span><span class="sxs-lookup"><span data-stu-id="6f215-109">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
 <span data-ttu-id="6f215-110">与使用嵌入脚本相比，传递对象具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="6f215-110">The following are advantages to passing an object rather than using an embedded script:</span></span>  
  
- <span data-ttu-id="6f215-111">改善了类的包装和重用。</span><span class="sxs-lookup"><span data-stu-id="6f215-111">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="6f215-112">使样式表可以更小而且更容易维护。</span><span class="sxs-lookup"><span data-stu-id="6f215-112">Allows style sheets to be smaller and more maintainable.</span></span>  
  
- <span data-ttu-id="6f215-113">支持对所属命名空间未在支持的 <xref:System> 命名空间集中定义的类调用方法。</span><span class="sxs-lookup"><span data-stu-id="6f215-113">Supports calling methods on classes belonging to namespaces other than those defined within the set of supported <xref:System> namespaces.</span></span>  
  
- <span data-ttu-id="6f215-114">支持使用 <xref:System.Xml.XPath.XPathNodeIterator> 将结果树片段传递到样式表。</span><span class="sxs-lookup"><span data-stu-id="6f215-114">Supports passing result tree fragments to the style sheet with the use of the <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
## <a name="xslt-style-sheet-parameters"></a><span data-ttu-id="6f215-115">XSLT 样式表参数</span><span class="sxs-lookup"><span data-stu-id="6f215-115">XSLT Style Sheet Parameters</span></span>  
 <span data-ttu-id="6f215-116">使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法将 XSLT 参数添加到 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>。</span><span class="sxs-lookup"><span data-stu-id="6f215-116">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="6f215-117">此时，限定名和命名空间统一资源标识符 (URI) 与参数对象关联。</span><span class="sxs-lookup"><span data-stu-id="6f215-117">A qualified name and namespace Uniform Resource Identifier (URI) are associated with the parameter object at that time.</span></span>  
  
 <span data-ttu-id="6f215-118">参数对象应对应于某个万维网联合会 (W3C) 类型。</span><span class="sxs-lookup"><span data-stu-id="6f215-118">The parameter object should correspond to a World Wide Web Consortium (W3C) type.</span></span> <span data-ttu-id="6f215-119">下表显示了相应的 W3C 类型、等效的 .NET Framework 类（类型），以及 W3C 类型是 XML 路径语言 (XPath) 类型还是 XSLT 类型。</span><span class="sxs-lookup"><span data-stu-id="6f215-119">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (type), and whether the W3C type is an XML Path Language (XPath) type or XSLT type.</span></span>  
  
|<span data-ttu-id="6f215-120">W3C 类型</span><span class="sxs-lookup"><span data-stu-id="6f215-120">W3C Type</span></span>|<span data-ttu-id="6f215-121">相当的 .NET Framework 类（类型）</span><span class="sxs-lookup"><span data-stu-id="6f215-121">Equivalent .NET Framework class (type)</span></span>|<span data-ttu-id="6f215-122">XPath 类型还是 XSLT 类型</span><span class="sxs-lookup"><span data-stu-id="6f215-122">XPath type or XSLT type</span></span>|  
|--------------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="6f215-123">String</span><span class="sxs-lookup"><span data-stu-id="6f215-123">String</span></span>|<span data-ttu-id="6f215-124">System.String</span><span class="sxs-lookup"><span data-stu-id="6f215-124">System.String</span></span>|<span data-ttu-id="6f215-125">XPath</span><span class="sxs-lookup"><span data-stu-id="6f215-125">XPath</span></span>|  
|<span data-ttu-id="6f215-126">Boolean</span><span class="sxs-lookup"><span data-stu-id="6f215-126">Boolean</span></span>|<span data-ttu-id="6f215-127">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="6f215-127">System.Boolean</span></span>|<span data-ttu-id="6f215-128">XPath</span><span class="sxs-lookup"><span data-stu-id="6f215-128">XPath</span></span>|  
|<span data-ttu-id="6f215-129">数字</span><span class="sxs-lookup"><span data-stu-id="6f215-129">Number</span></span>|<span data-ttu-id="6f215-130">System.Double</span><span class="sxs-lookup"><span data-stu-id="6f215-130">System.Double</span></span>|<span data-ttu-id="6f215-131">XPath</span><span class="sxs-lookup"><span data-stu-id="6f215-131">XPath</span></span>|  
|<span data-ttu-id="6f215-132">Result Tree Fragment</span><span class="sxs-lookup"><span data-stu-id="6f215-132">Result Tree Fragment</span></span>|<span data-ttu-id="6f215-133">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6f215-133">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="6f215-134">XSLT</span><span class="sxs-lookup"><span data-stu-id="6f215-134">XSLT</span></span>|  
|<span data-ttu-id="6f215-135">Node Set</span><span class="sxs-lookup"><span data-stu-id="6f215-135">Node Set</span></span>|<span data-ttu-id="6f215-136">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="6f215-136">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="6f215-137">XPath</span><span class="sxs-lookup"><span data-stu-id="6f215-137">XPath</span></span>|  
  
 <span data-ttu-id="6f215-138">如果参数对象不属于上述类，将根据需要被强制指定为 Double 或 String（以适用的为准）。</span><span class="sxs-lookup"><span data-stu-id="6f215-138">If the parameter object is not one of the above classes, it is forced to either a Double or String, as appropriate.</span></span> <span data-ttu-id="6f215-139">Int16、UInt16、Int32、UInt32、Int64、UInt64、Single 和 Decimal 类型被强制指定为 Double。</span><span class="sxs-lookup"><span data-stu-id="6f215-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, Single and Decimal types are forced to a Double.</span></span> <span data-ttu-id="6f215-140">所有其他类型均被用 `ToString` 方法强制指定为 String。</span><span class="sxs-lookup"><span data-stu-id="6f215-140">All other types are forced to a String using the `ToString` method.</span></span>  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a><span data-ttu-id="6f215-141">要使用 XSLT 参数，用户需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6f215-141">To use the XSLT parameter, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="6f215-142">创建 <xref:System.Xml.Xsl.XsltArgumentList> 并使用 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> 添加对象。</span><span class="sxs-lookup"><span data-stu-id="6f215-142">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the objects using <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span></span>  
  
2. <span data-ttu-id="6f215-143">从样式表调用参数。</span><span class="sxs-lookup"><span data-stu-id="6f215-143">Call the parameters from the style sheet.</span></span>  
  
3. <span data-ttu-id="6f215-144">将 <xref:System.Xml.Xsl.XsltArgumentList> 传递到 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6f215-144">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="6f215-145">示例</span><span class="sxs-lookup"><span data-stu-id="6f215-145">Example</span></span>  
 <span data-ttu-id="6f215-146">下面的示例使用 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> 方法创建一个参数来保存计算的折扣日期。</span><span class="sxs-lookup"><span data-stu-id="6f215-146">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold a calculated discount date.</span></span> <span data-ttu-id="6f215-147">折扣日期计算为从订单日期算起的 20 天时间。</span><span class="sxs-lookup"><span data-stu-id="6f215-147">The discount date is calculated to be 20 days from the order date.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
    writer.Close()  
  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="6f215-148">输入</span><span class="sxs-lookup"><span data-stu-id="6f215-148">Input</span></span>  
 <span data-ttu-id="6f215-149">order.xml</span><span class="sxs-lookup"><span data-stu-id="6f215-149">order.xml</span></span>  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 <span data-ttu-id="6f215-150">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="6f215-150">discount.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="6f215-151">Output</span><span class="sxs-lookup"><span data-stu-id="6f215-151">Output</span></span>  
  
```xml  
<order>  
   <total>36.9</total>
   15% discount if paid by: 5/6/2001 5:01:15 PM
</order>  
```  
  
## <a name="xslt-extension-objects"></a><span data-ttu-id="6f215-152">XSLT 扩展对象</span><span class="sxs-lookup"><span data-stu-id="6f215-152">XSLT Extension Objects</span></span>  
 <span data-ttu-id="6f215-153">使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法将 XSLT 扩展对象添加到 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>。</span><span class="sxs-lookup"><span data-stu-id="6f215-153">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="6f215-154">此时，限定名和命名空间 URI 与扩展对象关联。</span><span class="sxs-lookup"><span data-stu-id="6f215-154">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
 <span data-ttu-id="6f215-155">添加对象时，<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 的调用方在安全策略中必须是完全受信任的。</span><span class="sxs-lookup"><span data-stu-id="6f215-155">When an object is added, the caller of the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> must be fully trusted in the security policy.</span></span> <span data-ttu-id="6f215-156">如果调用方不是完全受信任的，则添加操作将失败。</span><span class="sxs-lookup"><span data-stu-id="6f215-156">If the caller is semi-trusted, the addition will fail.</span></span>  
  
 <span data-ttu-id="6f215-157">尽管对象已成功添加，但不能保证执行将成功。</span><span class="sxs-lookup"><span data-stu-id="6f215-157">Though an object is added successfully, it does not guarantee that the execution will be successful.</span></span> <span data-ttu-id="6f215-158">调用 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法时，将针对在 <xref:System.Xml.Xsl.XslTransform.Load%2A> 时提供的证据来计算权限，并将权限集分配给整个转换过程。</span><span class="sxs-lookup"><span data-stu-id="6f215-158">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at <xref:System.Xml.Xsl.XslTransform.Load%2A> time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="6f215-159">如果一个扩展对象尝试启动一个操作，而该操作需要权限集中所没有的权限，就会引发异常。</span><span class="sxs-lookup"><span data-stu-id="6f215-159">If an extension object attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
 <span data-ttu-id="6f215-160">从扩展对象返回的数据类型是四种 XPath 基本数据类型之一：数字、字符串、布尔值或节点集。</span><span class="sxs-lookup"><span data-stu-id="6f215-160">The data types returned from extension objects are one of the four basic XPath data types of number, string, Boolean, and node set.</span></span>  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a><span data-ttu-id="6f215-161">要使用 XSLT 扩展对象，用户需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6f215-161">To use the XSLT extension object, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="6f215-162">创建 <xref:System.Xml.Xsl.XsltArgumentList> 并使用 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 添加扩展对象。</span><span class="sxs-lookup"><span data-stu-id="6f215-162">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span></span>  
  
2. <span data-ttu-id="6f215-163">从样式表调用扩展对象。</span><span class="sxs-lookup"><span data-stu-id="6f215-163">Invoke the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="6f215-164">将 <xref:System.Xml.Xsl.XsltArgumentList> 传递到 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6f215-164">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="6f215-165">示例</span><span class="sxs-lookup"><span data-stu-id="6f215-165">Example</span></span>  
 <span data-ttu-id="6f215-166">已知圆的半径，下面的示例计算圆的周长。</span><span class="sxs-lookup"><span data-stu-id="6f215-166">The following example calculates the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="6f215-167">输入</span><span class="sxs-lookup"><span data-stu-id="6f215-167">Input</span></span>  
 <span data-ttu-id="6f215-168">number.xml</span><span class="sxs-lookup"><span data-stu-id="6f215-168">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>
```  
  
 <span data-ttu-id="6f215-169">circle.xsl</span><span class="sxs-lookup"><span data-stu-id="6f215-169">circle.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="6f215-170">Output</span><span class="sxs-lookup"><span data-stu-id="6f215-170">Output</span></span>  
 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a><span data-ttu-id="6f215-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="6f215-171">See also</span></span>

- [<span data-ttu-id="6f215-172">XslTransform 类实现 XSLT 处理器</span><span class="sxs-lookup"><span data-stu-id="6f215-172">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
