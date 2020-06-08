---
title: 更改命名空间前缀属性
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: b817a68ff9789be414118ff4c1a3d88ca3ea9f01
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290910"
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="134c4-102">更改命名空间前缀属性</span><span class="sxs-lookup"><span data-stu-id="134c4-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="134c4-103">使用 XmlNode  类，可以更改与给定节点关联的命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="134c4-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="134c4-104">例如，下面的代码显示所更改元素的前缀。</span><span class="sxs-lookup"><span data-stu-id="134c4-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="134c4-105">**输出**</span><span class="sxs-lookup"><span data-stu-id="134c4-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="134c4-106">更改节点的前缀不会更改节点的命名空间。</span><span class="sxs-lookup"><span data-stu-id="134c4-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="134c4-107">命名空间只能在创建节点时设置。</span><span class="sxs-lookup"><span data-stu-id="134c4-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="134c4-108">当保持树时，可能需要在外部保存新的命名空间属性，以满足所设置的前缀的需要。</span><span class="sxs-lookup"><span data-stu-id="134c4-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="134c4-109">如果无法创建新的命名空间，则更改此前缀以使节点保留其本地名称和命名空间。</span><span class="sxs-lookup"><span data-stu-id="134c4-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="134c4-110">下面的示例显示所添加的命名空间属性。</span><span class="sxs-lookup"><span data-stu-id="134c4-110">The following example shows a namespace attribute being added.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="134c4-111">**输出**</span><span class="sxs-lookup"><span data-stu-id="134c4-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="134c4-112">如果树由于 doc.InnerXml  调用而暂留到字符串，添加的 `xmlns:a='123'` 属性是为了暂留 `test` 元素的命名空间。</span><span class="sxs-lookup"><span data-stu-id="134c4-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="134c4-113">以前为 `'123'`，并保持为 `'123'`。</span><span class="sxs-lookup"><span data-stu-id="134c4-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="134c4-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="134c4-114">See also</span></span>

- [<span data-ttu-id="134c4-115">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="134c4-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
