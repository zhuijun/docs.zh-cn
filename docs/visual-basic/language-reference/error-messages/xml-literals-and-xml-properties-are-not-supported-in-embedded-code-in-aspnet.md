---
title: ASP.NET 中的嵌入式代码不支持 XML 文本和 XML 属性
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 861677636f9a73015b26efec30df728d07fbdf72
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870205"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="4a976-102">ASP.NET 中的嵌入式代码不支持 XML 文本和 XML 属性</span><span class="sxs-lookup"><span data-stu-id="4a976-102">XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>

<span data-ttu-id="4a976-103">ASP.NET 中的嵌入式代码不支持 XML 文本和 XML 属性。</span><span class="sxs-lookup"><span data-stu-id="4a976-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="4a976-104">若要使用 XML 功能，请将代码移到代码隐藏。</span><span class="sxs-lookup"><span data-stu-id="4a976-104">To use XML features, move the code to code-behind.</span></span>  
  
 <span data-ttu-id="4a976-105">在嵌入代码中定义 XML 文本或 XML 轴属性， (`<%= =>` 在 ASP.NET 文件中) 。</span><span class="sxs-lookup"><span data-stu-id="4a976-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>  
  
 <span data-ttu-id="4a976-106">**错误 ID：** BC31200</span><span class="sxs-lookup"><span data-stu-id="4a976-106">**Error ID:** BC31200</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4a976-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="4a976-107">To correct this error</span></span>  
  
- <span data-ttu-id="4a976-108">将包括 XML 文本或 XML 轴属性的代码移到 ASP.NET 代码隐藏文件中。</span><span class="sxs-lookup"><span data-stu-id="4a976-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a976-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4a976-109">See also</span></span>

- [<span data-ttu-id="4a976-110">XML 文本</span><span class="sxs-lookup"><span data-stu-id="4a976-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="4a976-111">XML 轴属性</span><span class="sxs-lookup"><span data-stu-id="4a976-111">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="4a976-112">XML</span><span class="sxs-lookup"><span data-stu-id="4a976-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)
