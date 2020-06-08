---
title: 加载 DOM 时的空白和有效空白处理
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: 520d965737b82fda082aa44029f2a4042d948deb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281762"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="96f91-102">加载 DOM 时的空白和有效空白处理</span><span class="sxs-lookup"><span data-stu-id="96f91-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="96f91-103">加载文档时，可以将选项设置为暂留空格，并在文档树中创建 XmlWhitespace  节点。</span><span class="sxs-lookup"><span data-stu-id="96f91-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="96f91-104">若要创建空格节点，请将 PreserveWhitespace  属性设置为 true。</span><span class="sxs-lookup"><span data-stu-id="96f91-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="96f91-105">如果将此属性设置为默认值 false  ，不会创建空格节点。</span><span class="sxs-lookup"><span data-stu-id="96f91-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="96f91-106">无论 PreserveWhitespace  标志的设置如何，始终暂留重要的空格节点，并且始终在内存中创建 XmlSignificantWhitespace  节点来表示此数据。</span><span class="sxs-lookup"><span data-stu-id="96f91-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="96f91-107">如果文档是从读取器加载，仅当 XmlTextReader  上的 WhitespaceHandling  属性未设置为 WhitespaceHandling.None  时，XmlDocument  类的 PreserveWhitespace  标志属性设置才会影响 XmlWhitespace  的创建。</span><span class="sxs-lookup"><span data-stu-id="96f91-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="96f91-108">读取器上的 WhitespaceHandling  属性值优先于 XmlDocument  上的此标志设置。</span><span class="sxs-lookup"><span data-stu-id="96f91-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="96f91-109">若要详细了解 XmlSignificantWhitespace  ，请参阅 <xref:System.Xml.XmlSignificantWhitespace>。</span><span class="sxs-lookup"><span data-stu-id="96f91-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f91-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="96f91-110">See also</span></span>

- [<span data-ttu-id="96f91-111">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="96f91-111">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
