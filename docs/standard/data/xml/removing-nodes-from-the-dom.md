---
title: 从 DOM 中移除节点
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: 5df95700bb1e84aa5f3adcc752b2314dc964477b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288636"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="2efb0-102">从 DOM 中移除节点</span><span class="sxs-lookup"><span data-stu-id="2efb0-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="2efb0-103">若要移除 XML 文档对象模型 (DOM) 中的节点，请使用 <xref:System.Xml.XmlNode.RemoveChild%2A> 方法移除特定节点。</span><span class="sxs-lookup"><span data-stu-id="2efb0-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="2efb0-104">在移除节点时，方法将移除属于所移除节点的子树；即如果不是叶节点。</span><span class="sxs-lookup"><span data-stu-id="2efb0-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="2efb0-105">要移除 DOM 中的多个节点，请使用 <xref:System.Xml.XmlNode.RemoveAll%2A> 方法移除当前节点的所有子级和属性（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="2efb0-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="2efb0-106">如果使用的是 <xref:System.Xml.XmlNamedNodeMap>，可以使用 <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> 方法移除节点。</span><span class="sxs-lookup"><span data-stu-id="2efb0-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="2efb0-107">若要删除属性，请参阅[删除 DOM 中元素节点的属性](removing-attributes-from-an-element-node-in-the-dom.md)。</span><span class="sxs-lookup"><span data-stu-id="2efb0-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2efb0-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="2efb0-108">See also</span></span>

- [<span data-ttu-id="2efb0-109">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="2efb0-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
