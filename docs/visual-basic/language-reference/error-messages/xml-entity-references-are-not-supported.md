---
title: 不支持 XML 实体引用
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: ae997d853a93999a3b29215ea1257da7a1d48c84
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406451"
---
# <a name="xml-entity-references-are-not-supported"></a><span data-ttu-id="2dcde-102">不支持 XML 实体引用</span><span class="sxs-lookup"><span data-stu-id="2dcde-102">XML entity references are not supported</span></span>
<span data-ttu-id="2dcde-103">`©`Xml 1.0 规范中未定义的实体引用（例如，）作为 xml 文本值包含在内。</span><span class="sxs-lookup"><span data-stu-id="2dcde-103">An entity reference (for example, `©`) that is not defined in the XML 1.0 specification is included as a value for an XML literal.</span></span> <span data-ttu-id="2dcde-104">`&` `"` `<` `>` Xml 文本中仅支持、、、和 `'` xml 实体引用。</span><span class="sxs-lookup"><span data-stu-id="2dcde-104">Only `&`, `"`, `<`, `>`, and `'` XML entity references are supported in XML literals.</span></span>  
  
 <span data-ttu-id="2dcde-105">**错误 ID：** BC31180</span><span class="sxs-lookup"><span data-stu-id="2dcde-105">**Error ID:** BC31180</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2dcde-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="2dcde-106">To correct this error</span></span>  
  
- <span data-ttu-id="2dcde-107">删除不受支持的实体引用。</span><span class="sxs-lookup"><span data-stu-id="2dcde-107">Remove the unsupported entity reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dcde-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2dcde-108">See also</span></span>

- [<span data-ttu-id="2dcde-109">XML 文本和 XML 1.0 规范</span><span class="sxs-lookup"><span data-stu-id="2dcde-109">XML Literals and the XML 1.0 Specification</span></span>](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [<span data-ttu-id="2dcde-110">XML 文本</span><span class="sxs-lookup"><span data-stu-id="2dcde-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="2dcde-111">XML</span><span class="sxs-lookup"><span data-stu-id="2dcde-111">XML</span></span>](../../programming-guide/language-features/xml/index.md)
