---
title: 在 Serializing2 时保留空白
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: e9b73089830bf7e6cb0ea9e469bf667f12c571d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396397"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="44bf4-102">在序列化时保留空白</span><span class="sxs-lookup"><span data-stu-id="44bf4-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="44bf4-103">本主题描述在序列化 XML 树时如何控制空白。</span><span class="sxs-lookup"><span data-stu-id="44bf4-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="44bf4-104">一种常用情况是读取缩进的 XML，在内存中创建一个没有任何空白文本节点（即不保留空白）的 XML 树，对该 XML 执行某些操作，然后保存带缩进的 XML。</span><span class="sxs-lookup"><span data-stu-id="44bf4-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="44bf4-105">在序列化带格式的 XML 时，只保留 XML 树中有意义的空白。</span><span class="sxs-lookup"><span data-stu-id="44bf4-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="44bf4-106">这是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的默认行为。</span><span class="sxs-lookup"><span data-stu-id="44bf4-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="44bf4-107">另一个常见的情况是读取和修改已经有意缩进的 XML。</span><span class="sxs-lookup"><span data-stu-id="44bf4-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="44bf4-108">您可能不想以任何方式更改这种缩进。</span><span class="sxs-lookup"><span data-stu-id="44bf4-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="44bf4-109">若要在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中执行此操作，您要在加载或解析 XML 时保留空白，并在序列化 XML 时禁用格式设置。</span><span class="sxs-lookup"><span data-stu-id="44bf4-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="44bf4-110">用于序列化 XML 树的方法的空白行为</span><span class="sxs-lookup"><span data-stu-id="44bf4-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="44bf4-111"><xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 类中的以下方法用于序列化 XML 树。</span><span class="sxs-lookup"><span data-stu-id="44bf4-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="44bf4-112">可以将 XML 树序列化为文件、<xref:System.IO.TextReader> 或 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="44bf4-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="44bf4-113">`ToString` 方法序列化为字符串。</span><span class="sxs-lookup"><span data-stu-id="44bf4-113">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="44bf4-114">XElement.ToString()</span><span class="sxs-lookup"><span data-stu-id="44bf4-114">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="44bf4-115">XDocument.ToString()</span><span class="sxs-lookup"><span data-stu-id="44bf4-115">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="44bf4-116">如果方法不接受 <xref:System.Xml.Linq.SaveOptions> 作为参数，那么该方法将格式化（缩进）序列化的 XML。</span><span class="sxs-lookup"><span data-stu-id="44bf4-116">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="44bf4-117">在这种情况下，将丢弃 XML 树中所有无意义的空白。</span><span class="sxs-lookup"><span data-stu-id="44bf4-117">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="44bf4-118">如果方法接受 <xref:System.Xml.Linq.SaveOptions> 作为参数，那么您可以指定不格式化（缩进）序列化的 XML。</span><span class="sxs-lookup"><span data-stu-id="44bf4-118">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="44bf4-119">在这种情况下，将保留 XML 树中的所有空白。</span><span class="sxs-lookup"><span data-stu-id="44bf4-119">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44bf4-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44bf4-120">See also</span></span>

- [<span data-ttu-id="44bf4-121">序列化 XML 树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="44bf4-121">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
