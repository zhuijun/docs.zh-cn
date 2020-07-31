---
title: 查找默认段落样式 (C#)
description: 了解如何使用 C# 中的 LINQ 处理 WordprocessingML 文档。 此示例查找文档中段落的默认样式。
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: e18bbbdbd5b2627c9ff4c3c3eedd84d7cb166a62
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103828"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="32c0f-104">查找默认段落样式 (C#)</span><span class="sxs-lookup"><span data-stu-id="32c0f-104">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="32c0f-105">在 WordprocessingML 文档中操作信息教程中的第一项任务是在文档中查找默认段落样式。</span><span class="sxs-lookup"><span data-stu-id="32c0f-105">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32c0f-106">示例</span><span class="sxs-lookup"><span data-stu-id="32c0f-106">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="32c0f-107">说明</span><span class="sxs-lookup"><span data-stu-id="32c0f-107">Description</span></span>  
 <span data-ttu-id="32c0f-108">下面的示例打开一个 Office Open XML WordprocessingML 文档，查找文档和包的样式部分，然后执行查找默认样式名称的查询。</span><span class="sxs-lookup"><span data-stu-id="32c0f-108">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="32c0f-109">有关 Office Open XML 文档包及其构成包的信息，请参阅 [Office Open XML WordprocessingML 文档的详细信息 (C#)](./wordprocessingml-document-with-styles.md)。</span><span class="sxs-lookup"><span data-stu-id="32c0f-109">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="32c0f-110">查询将查找名为 `w:style` 的节点，该节点具有值为“paragraph”的名为 `w:type` 的属性和值为“1”的名为 `w:default` 的属性。</span><span class="sxs-lookup"><span data-stu-id="32c0f-110">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="32c0f-111">由于将只有一个 XML 节点具有这些属性，因此查询使用 <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> 运算符将集合转换为单一实例。</span><span class="sxs-lookup"><span data-stu-id="32c0f-111">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="32c0f-112">然后，它获取名为 `w:styleId` 的属性的值。</span><span class="sxs-lookup"><span data-stu-id="32c0f-112">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="32c0f-113">本示例使用 WindowsBase 程序集中的类。</span><span class="sxs-lookup"><span data-stu-id="32c0f-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="32c0f-114">它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。</span><span class="sxs-lookup"><span data-stu-id="32c0f-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="32c0f-115">代码</span><span class="sxs-lookup"><span data-stu-id="32c0f-115">Code</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship =  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
          docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
// The following query finds all the paragraphs that have the default style.  
string defaultStyle =
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
Console.WriteLine("The default style is: {0}", defaultStyle);  
```  
  
### <a name="comments"></a><span data-ttu-id="32c0f-116">注释</span><span class="sxs-lookup"><span data-stu-id="32c0f-116">Comments</span></span>  
 <span data-ttu-id="32c0f-117">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="32c0f-117">This example produces the following output:</span></span>  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="32c0f-118">后续步骤</span><span class="sxs-lookup"><span data-stu-id="32c0f-118">Next Steps</span></span>  
 <span data-ttu-id="32c0f-119">下一个示例中将创建一个类似的查询，查找文档中的所有段落及其样式：</span><span class="sxs-lookup"><span data-stu-id="32c0f-119">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="32c0f-120">检索段落及其样式 (C#)</span><span class="sxs-lookup"><span data-stu-id="32c0f-120">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  
