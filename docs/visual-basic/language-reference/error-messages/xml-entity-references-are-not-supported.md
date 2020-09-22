---
title: 不支持 XML 实体引用
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: 470e5577654ce8b6bbc2732a41c130a85ddc96e5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874990"
---
# <a name="xml-entity-references-are-not-supported"></a><span data-ttu-id="88e03-102">不支持 XML 实体引用</span><span class="sxs-lookup"><span data-stu-id="88e03-102">XML entity references are not supported</span></span>

<span data-ttu-id="88e03-103">例如，在 `©` xml 1.0 规范中未定义的)  (实体引用包含为 xml 文本值。</span><span class="sxs-lookup"><span data-stu-id="88e03-103">An entity reference (for example, `©`) that is not defined in the XML 1.0 specification is included as a value for an XML literal.</span></span> <span data-ttu-id="88e03-104">`&` `"` `<` `>` Xml 文本中仅支持、、、和 `'` xml 实体引用。</span><span class="sxs-lookup"><span data-stu-id="88e03-104">Only `&`, `"`, `<`, `>`, and `'` XML entity references are supported in XML literals.</span></span>  
  
 <span data-ttu-id="88e03-105">**错误 ID：** BC31180</span><span class="sxs-lookup"><span data-stu-id="88e03-105">**Error ID:** BC31180</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="88e03-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="88e03-106">To correct this error</span></span>  
  
- <span data-ttu-id="88e03-107">删除不受支持的实体引用。</span><span class="sxs-lookup"><span data-stu-id="88e03-107">Remove the unsupported entity reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e03-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="88e03-108">See also</span></span>

- [<span data-ttu-id="88e03-109">XML 文本和 XML 1.0 规范</span><span class="sxs-lookup"><span data-stu-id="88e03-109">XML Literals and the XML 1.0 Specification</span></span>](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [<span data-ttu-id="88e03-110">XML 文本</span><span class="sxs-lookup"><span data-stu-id="88e03-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="88e03-111">XML</span><span class="sxs-lookup"><span data-stu-id="88e03-111">XML</span></span>](../../programming-guide/language-features/xml/index.md)
