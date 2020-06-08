---
title: 命名空间对包含元素和属性的新节点的实体引用扩展的影响
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 05ec622f09106978281cd3e6f0a82f13703c2097
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288805"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="b4e73-102">命名空间对包含元素和属性的新节点的实体引用扩展的影响</span><span class="sxs-lookup"><span data-stu-id="b4e73-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="b4e73-103">由于实体声明的内容可以包含几乎所有内容，因此该内容有可能包含像 `<!ENTITY aname "<elem>test</elem>">` 这样的元素。</span><span class="sxs-lookup"><span data-stu-id="b4e73-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="b4e73-104">分析 XML 时，`&aname;` 在分析时不用其替换内容扩展。</span><span class="sxs-lookup"><span data-stu-id="b4e73-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="b4e73-105">不执行 XML 扩展的原因在于对元素的命名空间解析只有在将节点放入文档中时才发生。</span><span class="sxs-lookup"><span data-stu-id="b4e73-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="b4e73-106">在此之前，并不知道范围中存在哪个命名空间。</span><span class="sxs-lookup"><span data-stu-id="b4e73-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="b4e73-107">将节点放入文档中后，将进行命名空间解析，生成的实体内容将被分析为相应节点。</span><span class="sxs-lookup"><span data-stu-id="b4e73-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4e73-108">新创建的实体引用节点进行扩展后，该扩展永远不会再次进行。</span><span class="sxs-lookup"><span data-stu-id="b4e73-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="b4e73-109">因此，在元素的替换文本中使用的命名空间将在设置父节点时绑定。</span><span class="sxs-lookup"><span data-stu-id="b4e73-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="b4e73-110">然而，命名空间可能会对现有实体引用节点（将它们删除并插入其他位置时）或用 CloneNode  方法克隆的实体引用节点变化。</span><span class="sxs-lookup"><span data-stu-id="b4e73-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4e73-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="b4e73-111">See also</span></span>

- [<span data-ttu-id="b4e73-112">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="b4e73-112">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
