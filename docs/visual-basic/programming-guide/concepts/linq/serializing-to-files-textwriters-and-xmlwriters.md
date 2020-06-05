---
title: 序列化到文件、Textwriter 和 XmlWriters3
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: d8b929ef02b8fd9c6a9f29ea997a754699a6e1c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403558"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="0cad4-102">序列化为文件、TextWriter 和 XmlWriter</span><span class="sxs-lookup"><span data-stu-id="0cad4-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="0cad4-103">可以将 XML 树序列化为 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="0cad4-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="0cad4-104">可以使用 <xref:System.Xml.Linq.XDocument> 方法，将任何 XML 组件（包括 <xref:System.Xml.Linq.XElement> 和 `ToString`）序列化为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="0cad4-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="0cad4-105">在序列化为字符串时，如果要禁止格式化，可以使用 <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="0cad4-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="0cad4-106">序列化为文件时，默认行为是格式化（缩进）生成的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="0cad4-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="0cad4-107">缩进时，不会保留 XML 树中无意义的空白。</span><span class="sxs-lookup"><span data-stu-id="0cad4-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="0cad4-108">若要使用格式化方式进行序列化，请使用不将 <xref:System.Xml.Linq.SaveOptions> 作为参数的以下方法的重载之一：</span><span class="sxs-lookup"><span data-stu-id="0cad4-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="0cad4-109">如果要选择不在 XML 树中缩进，并保留无意义空白，请使用将 <xref:System.Xml.Linq.SaveOptions> 作为参数的以下方法的重载之一：</span><span class="sxs-lookup"><span data-stu-id="0cad4-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="0cad4-110">有关示例，请参见相应的参考主题。</span><span class="sxs-lookup"><span data-stu-id="0cad4-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cad4-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0cad4-111">See also</span></span>

- [<span data-ttu-id="0cad4-112">序列化 XML 树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0cad4-112">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
