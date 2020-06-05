---
title: 分析 XML
ms.date: 07/20/2015
ms.assetid: 5bcbd7e2-d9f1-4c8f-80d6-39915fe17bd1
ms.openlocfilehash: 3517a0925e886dcd3d2d7860be606c4e44127cd6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406854"
---
# <a name="parsing-xml-visual-basic"></a><span data-ttu-id="39f35-102">分析 XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="39f35-102">Parsing XML (Visual Basic)</span></span>
<span data-ttu-id="39f35-103">本节中的主题介绍如何分析 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="39f35-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39f35-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="39f35-104">In This Section</span></span>  
  
|<span data-ttu-id="39f35-105">主题</span><span class="sxs-lookup"><span data-stu-id="39f35-105">Topic</span></span>|<span data-ttu-id="39f35-106">说明</span><span class="sxs-lookup"><span data-stu-id="39f35-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="39f35-107">如何：分析字符串（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="39f35-107">How to: Parse a String (Visual Basic)</span></span>](how-to-parse-a-string.md)|<span data-ttu-id="39f35-108">演示如何分析字符串从而创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="39f35-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="39f35-109">如何：从文件加载 XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="39f35-109">How to: Load XML from a File (Visual Basic)</span></span>](how-to-load-xml-from-a-file.md)|<span data-ttu-id="39f35-110">演示如何使用 <xref:System.Xml.Linq.XElement.Load%2A> 方法从 URI 加载 XML。</span><span class="sxs-lookup"><span data-stu-id="39f35-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="39f35-111">在加载或分析 XML 时保留空白</span><span class="sxs-lookup"><span data-stu-id="39f35-111">Preserving White Space while Loading or Parsing XML</span></span>](preserving-white-space-while-loading-or-parsing-xml.md)|<span data-ttu-id="39f35-112">介绍如何在加载 XML 树时控制 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的空白行为。</span><span class="sxs-lookup"><span data-stu-id="39f35-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="39f35-113">如何：捕捉分析错误（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="39f35-113">How to: Catch Parsing Errors (Visual Basic)</span></span>](how-to-catch-parsing-errors.md)|<span data-ttu-id="39f35-114">演示如何检测格式不正确或无效的 XML。</span><span class="sxs-lookup"><span data-stu-id="39f35-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="39f35-115">如何：从 XmlReader 创建树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="39f35-115">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>](how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="39f35-116">演示如何从 <xref:System.Xml.XmlReader> 直接创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="39f35-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="39f35-117">如何：从 XmlReader 流式处理 XML 片段（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="39f35-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>](how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="39f35-118">演示如何使用 <xref:System.Xml.XmlReader> 对 XML 片段进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="39f35-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="39f35-119">如果必须处理很大的 XML 文件，将整个 XML 树加载到内存可能不可行。</span><span class="sxs-lookup"><span data-stu-id="39f35-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="39f35-120">这时，可以对 XML 片段进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="39f35-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39f35-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39f35-121">See also</span></span>

- [<span data-ttu-id="39f35-122">创建 XML 树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="39f35-122">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
