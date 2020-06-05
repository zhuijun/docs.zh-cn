---
title: 如何：捕捉分析错误
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: c0b46d7df270dd6f081a0c736b6978088cfbd9c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375143"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="d6faf-102">如何：捕捉分析错误（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d6faf-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="d6faf-103">本主题演示如何检测格式不正确或无效的 XML。</span><span class="sxs-lookup"><span data-stu-id="d6faf-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d6faf-104">通过使用 <xref:System.Xml.XmlReader> 实现。</span><span class="sxs-lookup"><span data-stu-id="d6faf-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d6faf-105">如果将格式不正确或无效的 XML 传递给 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，则基础 <xref:System.Xml.XmlReader> 类将引发异常。</span><span class="sxs-lookup"><span data-stu-id="d6faf-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="d6faf-106">用于分析 XML 的各种方法（如 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>）不会捕捉异常；应用程序可以捕捉异常。</span><span class="sxs-lookup"><span data-stu-id="d6faf-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="d6faf-107">请注意，如果使用 XML 文本，则无法获取分析错误。</span><span class="sxs-lookup"><span data-stu-id="d6faf-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="d6faf-108">Visual Basic 编译器将捕捉格式不正确或无效的 XML 错误。</span><span class="sxs-lookup"><span data-stu-id="d6faf-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6faf-109">示例</span><span class="sxs-lookup"><span data-stu-id="d6faf-109">Example</span></span>  
 <span data-ttu-id="d6faf-110">下面的代码尝试分析无效的 XML：</span><span class="sxs-lookup"><span data-stu-id="d6faf-110">The following code tries to parse invalid XML:</span></span>  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 <span data-ttu-id="d6faf-111">运行此代码时，会引发以下异常：</span><span class="sxs-lookup"><span data-stu-id="d6faf-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="d6faf-112">有关 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 和 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 方法可能会引发的异常的更多信息，请参见 <xref:System.Xml.XmlReader> 文档。</span><span class="sxs-lookup"><span data-stu-id="d6faf-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6faf-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6faf-113">See also</span></span>

- [<span data-ttu-id="d6faf-114">分析 XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d6faf-114">Parsing XML (Visual Basic)</span></span>](parsing-xml.md)
