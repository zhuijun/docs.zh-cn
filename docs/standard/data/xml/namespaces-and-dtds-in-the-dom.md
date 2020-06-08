---
title: DOM 中的命名空间和 DTD
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
ms.openlocfilehash: 748be66c255aa018fb3e1ed541c6e5a92775408c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288779"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="cff7f-102">DOM 中的命名空间和 DTD</span><span class="sxs-lookup"><span data-stu-id="cff7f-102">Namespaces and DTDs in the DOM</span></span>
<span data-ttu-id="cff7f-103">文档类型定义 (DTD) 使命名空间支持变得很复杂。</span><span class="sxs-lookup"><span data-stu-id="cff7f-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="cff7f-104">例如，在下面的 XML 中，默认属性的名称中包含冒号。</span><span class="sxs-lookup"><span data-stu-id="cff7f-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="cff7f-105">如果允许使用此构造，则可采用下列解析：</span><span class="sxs-lookup"><span data-stu-id="cff7f-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
- <span data-ttu-id="cff7f-106">`x:` 被视为命名空间前缀，但此前缀必须可以使用 `xmlns:x` 命名空间声明来解析，而该声明必须也存在于 DTD 中的某个位置。</span><span class="sxs-lookup"><span data-stu-id="cff7f-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="cff7f-107">将此前缀映射到实例文档中的其他内容是错误的。</span><span class="sxs-lookup"><span data-stu-id="cff7f-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
- <span data-ttu-id="cff7f-108">`x:` 被视为命名空间前缀，但此前缀总是在实例元素的上下文中解析。</span><span class="sxs-lookup"><span data-stu-id="cff7f-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="cff7f-109">这意味着根据出现 `item` 元素的命名空间范围，此前缀实际上可映射到其他命名空间统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="cff7f-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="cff7f-110">此行为比前一个项目符号中给定的解析更容易预知，但存在其他复杂的后果，这是因为它要求将默认属性具体化。</span><span class="sxs-lookup"><span data-stu-id="cff7f-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
- <span data-ttu-id="cff7f-111">忽略冒号，因为它在 DTD 中，且属性名为 `x:y`，没有前缀，也没有命名空间 URI。</span><span class="sxs-lookup"><span data-stu-id="cff7f-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
- <span data-ttu-id="cff7f-112">默认属性中的冒号引发异常，表明 DTD 内部不支持在名称中使用冒号。</span><span class="sxs-lookup"><span data-stu-id="cff7f-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="cff7f-113">这导致可预知的行为，但意味着不能加载多个万维网联合会 (W3C) 已发布的 DTD。</span><span class="sxs-lookup"><span data-stu-id="cff7f-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
- <span data-ttu-id="cff7f-114">当用户请求 DTD 验证时，对整个文档的命名空间支持将被关闭。</span><span class="sxs-lookup"><span data-stu-id="cff7f-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="cff7f-115">这使得可以加载 W3C DTD 并产生可预知的行为。</span><span class="sxs-lookup"><span data-stu-id="cff7f-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="cff7f-116">Microsoft .NET Framework 中的 XML 实现第二个选项，以最大限度地提升 W3C 兼容性。</span><span class="sxs-lookup"><span data-stu-id="cff7f-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff7f-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="cff7f-117">See also</span></span>

- [<span data-ttu-id="cff7f-118">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="cff7f-118">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
