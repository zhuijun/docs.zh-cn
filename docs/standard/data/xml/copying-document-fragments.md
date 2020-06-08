---
title: 复制文档片段
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: cf424bbe-81b7-40d2-9978-9b727da94d80
ms.openlocfilehash: 7838a4b48c0a5fb43676275e8266f80b800e07bf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291300"
---
# <a name="copying-document-fragments"></a><span data-ttu-id="137a7-102">复制文档片段</span><span class="sxs-lookup"><span data-stu-id="137a7-102">Copying Document Fragments</span></span>
<span data-ttu-id="137a7-103">可以先创建 XmlDocumentFragment  节点，再在它下面添加节点。</span><span class="sxs-lookup"><span data-stu-id="137a7-103">You can create an **XmlDocumentFragment** node and then add nodes under it.</span></span> <span data-ttu-id="137a7-104">如果使用 InsertNode  方法插入 XmlDocumentFragment  ，不会复制 XmlDocumentFragment  节点，但会在 XML 文档对象模型 (DOM) 中插入它的子节点。</span><span class="sxs-lookup"><span data-stu-id="137a7-104">When the **XmlDocumentFragment** is inserted with the **InsertNode** method, the **XmlDocumentFragment** node is not copied, but its child nodes are inserted in the XML Document Object Model (DOM).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137a7-105">请参阅</span><span class="sxs-lookup"><span data-stu-id="137a7-105">See also</span></span>

- [<span data-ttu-id="137a7-106">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="137a7-106">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
