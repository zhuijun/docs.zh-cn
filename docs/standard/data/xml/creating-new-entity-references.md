---
title: 创建新实体引用
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
ms.openlocfilehash: 7c94d121d00c169f0d74bc9b12c8710fb6055250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283346"
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="f0d9f-102">创建新实体引用</span><span class="sxs-lookup"><span data-stu-id="f0d9f-102">Creating New Entity References</span></span>
<span data-ttu-id="f0d9f-103">CreateEntityReference  方法新建 XmlEntityReference  节点。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="f0d9f-104">XML 文档对象模型 (DOM) 查看是否已声明了引用的实体名称。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="f0d9f-105">如果已声明，从实体声明节点复制 XmlEntityReference  节点的子节点。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="f0d9f-106">如果没有匹配的实体声明，则附加一个空的文本节点作为实体引用节点的唯一子级。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="f0d9f-107">由于 XmlEntityReference  节点的子节点是其他节点的副本，因此这些子节点是只读的，无法修改。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="f0d9f-108">当复制节点时，在实体引用所处的范围内可能存在一个命名空间。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="f0d9f-109">此命名空间影响生成的任何元素或属性节点的配置。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0d9f-110">仅当将 EntityReference  节点插入文档时，DOM 才将子节点添加到 EntityReference  。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="f0d9f-111">新建的 EntityReference  节点没有子节点。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="f0d9f-112">尽管 XmlDataDocument  是 XmlDocument  的派生类，但 XmlDataDocument  不支持创建实体引用。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="f0d9f-113">这是因为 EntityReference  子级是只读的。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="f0d9f-114">EntityReference  节点的子级可以跨越多个区域。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="f0d9f-115">在这种情况下，行中与包含 EntityReference  一部分的区域关联的部分是只读的。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d9f-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="f0d9f-116">See also</span></span>

- [<span data-ttu-id="f0d9f-117">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="f0d9f-117">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
