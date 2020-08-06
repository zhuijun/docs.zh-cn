---
title: 在加载或分析 XML 时保留空白
description: 了解如何在加载或分析 XML 时控制空白行为，尤其是填充 XML 树的方法的行为。
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 3c044937d38f9f89ebc114af3eddbf5116c392ad
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302836"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a><span data-ttu-id="8b417-103">在加载或分析 XML 时保留空白</span><span class="sxs-lookup"><span data-stu-id="8b417-103">Preserving White Space while Loading or Parsing XML</span></span>
<span data-ttu-id="8b417-104">本主题介绍了如何控制 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的空白符行为。</span><span class="sxs-lookup"><span data-stu-id="8b417-104">This topic describes how to control the white-space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="8b417-105">一种常用情况是读取缩进的 XML，在内存中创建一个没有任何空白文本节点（即不保留空白）的 XML 树，对该 XML 执行某些操作，然后保存带缩进的 XML。</span><span class="sxs-lookup"><span data-stu-id="8b417-105">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="8b417-106">在序列化带格式的 XML 时，只保留 XML 树中有意义的空白。</span><span class="sxs-lookup"><span data-stu-id="8b417-106">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="8b417-107">这是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的默认行为。</span><span class="sxs-lookup"><span data-stu-id="8b417-107">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="8b417-108">另一个常见的情况是读取和修改已经有意缩进的 XML。</span><span class="sxs-lookup"><span data-stu-id="8b417-108">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="8b417-109">您可能不想以任何方式更改这种缩进。</span><span class="sxs-lookup"><span data-stu-id="8b417-109">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="8b417-110">若要在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中执行此操作，您要在加载或解析 XML 时保留空白，并在序列化 XML 时禁用格式设置。</span><span class="sxs-lookup"><span data-stu-id="8b417-110">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="8b417-111">本主题介绍了填充 XML 树的方法的空白符行为。</span><span class="sxs-lookup"><span data-stu-id="8b417-111">This topic describes the white-space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="8b417-112">有关序列化 XML 树时如何控制空白的信息，请参阅[在序列化时保留空白](./preserving-white-space-while-serializing.md)。</span><span class="sxs-lookup"><span data-stu-id="8b417-112">For information about controlling white space when you serialize XML trees, see [Preserving White Space While Serializing](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="8b417-113">用于填充 XML 树的方法的行为</span><span class="sxs-lookup"><span data-stu-id="8b417-113">Behavior of Methods that Populate XML Trees</span></span>  
 <span data-ttu-id="8b417-114"><xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 类中的以下方法用于填充 XML 树。</span><span class="sxs-lookup"><span data-stu-id="8b417-114">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="8b417-115">可以从文件、<xref:System.IO.TextReader>、<xref:System.Xml.XmlReader> 或字符串填充 XML 树：</span><span class="sxs-lookup"><span data-stu-id="8b417-115">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="8b417-116">如果方法不采用 <xref:System.Xml.Linq.LoadOptions> 作为参数，则该方法将不会保留无意义的空白。</span><span class="sxs-lookup"><span data-stu-id="8b417-116">If the method does not take <xref:System.Xml.Linq.LoadOptions> as an argument, the method will not preserve insignificant white space.</span></span>  
  
 <span data-ttu-id="8b417-117">在多数情况下，如果方法采用 <xref:System.Xml.Linq.LoadOptions> 作为参数，则您可以选择保留无意义的空白作为 XML 树中的文本节点。</span><span class="sxs-lookup"><span data-stu-id="8b417-117">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="8b417-118">但如果方法从 <xref:System.Xml.XmlReader> 中加载 XML，则 <xref:System.Xml.XmlReader> 将确定是否保留空白。</span><span class="sxs-lookup"><span data-stu-id="8b417-118">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="8b417-119">设置 <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> 不会有影响。</span><span class="sxs-lookup"><span data-stu-id="8b417-119">Setting <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> will have no effect.</span></span>  
  
 <span data-ttu-id="8b417-120">使用这些方法时，如果保留空白，则会将无意义的空白插入到 XML 树中作为 <xref:System.Xml.Linq.XText> 节点。</span><span class="sxs-lookup"><span data-stu-id="8b417-120">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="8b417-121">如果不保留空白，则不会插入文本节点。</span><span class="sxs-lookup"><span data-stu-id="8b417-121">If white space is not preserved, text nodes are not inserted.</span></span>  
  
 <span data-ttu-id="8b417-122">您可以使用 <xref:System.Xml.XmlWriter> 创建一个 XML 树。</span><span class="sxs-lookup"><span data-stu-id="8b417-122">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="8b417-123">写入到 <xref:System.Xml.XmlWriter> 的节点会在树中进行填充。</span><span class="sxs-lookup"><span data-stu-id="8b417-123">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="8b417-124">但在使用此方法生成 XML 树时，不管节点是否为空白或是否为无意义的空白，都将保留所有节点。</span><span class="sxs-lookup"><span data-stu-id="8b417-124">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>  
  