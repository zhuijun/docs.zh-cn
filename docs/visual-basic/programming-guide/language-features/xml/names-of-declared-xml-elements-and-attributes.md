---
title: 已声明的 XML 元素和属性的名称
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 2142674c3de4c5ac9e806c1328daa3efb697beb9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085615"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="cdf85-102">已声明的 XML 元素和特性的名称 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cdf85-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>

<span data-ttu-id="cdf85-103">本主题提供了在 XML 文本中命名 XML 元素和属性的 Visual Basic 准则。</span><span class="sxs-lookup"><span data-stu-id="cdf85-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="cdf85-104">在 XML 文本中，可以指定本地名称或限定名称。</span><span class="sxs-lookup"><span data-stu-id="cdf85-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="cdf85-105">限定名由 XML 命名空间前缀、冒号和本地名称组成。</span><span class="sxs-lookup"><span data-stu-id="cdf85-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="cdf85-106">有关 XML 命名空间前缀的详细信息，请参阅 [Xml 元素文本](../../../language-reference/xml-literals/xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="cdf85-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="cdf85-107">规则</span><span class="sxs-lookup"><span data-stu-id="cdf85-107">Rules</span></span>  

 <span data-ttu-id="cdf85-108">Visual Basic 中的元素或属性的本地名称必须遵循以下规则。</span><span class="sxs-lookup"><span data-stu-id="cdf85-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
- <span data-ttu-id="cdf85-109">它可以从命名空间开始。</span><span class="sxs-lookup"><span data-stu-id="cdf85-109">It can begin with a namespace.</span></span> <span data-ttu-id="cdf85-110">它必须以字母字符或下划线开头 (`_`) 。</span><span class="sxs-lookup"><span data-stu-id="cdf85-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="cdf85-111">它必须只包含字母字符、十进制数字、下划线、句点 ( ) 和连字符 ( ) 。</span><span class="sxs-lookup"><span data-stu-id="cdf85-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
- <span data-ttu-id="cdf85-112">长度不得超过1024个字符。</span><span class="sxs-lookup"><span data-stu-id="cdf85-112">It must not be more than 1,024 characters long.</span></span>  
  
- <span data-ttu-id="cdf85-113">名称中出现的冒号指示命名空间分界。</span><span class="sxs-lookup"><span data-stu-id="cdf85-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="cdf85-114">因此，您可以使用冒号来指定特定名称的 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="cdf85-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="cdf85-115">此外，还应遵循以下准则。</span><span class="sxs-lookup"><span data-stu-id="cdf85-115">In addition, you should adhere to the following guideline.</span></span>  
  
- <span data-ttu-id="cdf85-116">XML 1.0 规范保留以字符串 "XML" 开头、大小写不同的所有名称。</span><span class="sxs-lookup"><span data-stu-id="cdf85-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="cdf85-117">因此，请不要将这些名称用于元素和属性名称。</span><span class="sxs-lookup"><span data-stu-id="cdf85-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="cdf85-118">名称长度准则</span><span class="sxs-lookup"><span data-stu-id="cdf85-118">Name Length Guidelines</span></span>  

 <span data-ttu-id="cdf85-119">在实际情况下，名称应尽可能简短，同时仍能清楚地确定元素的性质。</span><span class="sxs-lookup"><span data-stu-id="cdf85-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="cdf85-120">这可以提高代码的可读性，并减少行长度和源文件大小。</span><span class="sxs-lookup"><span data-stu-id="cdf85-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="cdf85-121">但是，名称不应太短，因为它不能充分描述元素或代码如何使用它。</span><span class="sxs-lookup"><span data-stu-id="cdf85-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="cdf85-122">这对于代码的可读性非常重要。</span><span class="sxs-lookup"><span data-stu-id="cdf85-122">This is important for the readability of your code.</span></span> <span data-ttu-id="cdf85-123">如果其他人正在尝试理解它，或者你在写入它后你需要很长的时间，则适当的元素名称可节省时间。</span><span class="sxs-lookup"><span data-stu-id="cdf85-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="cdf85-124">名称区分大小写</span><span class="sxs-lookup"><span data-stu-id="cdf85-124">Case Sensitivity in Names</span></span>  

 <span data-ttu-id="cdf85-125">XML 元素名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="cdf85-125">XML element names are case sensitive.</span></span> <span data-ttu-id="cdf85-126">这意味着，当 Visual Basic 编译器仅对字母大小写不同的两个名称进行比较时，它会将它们解释为不同的名称。</span><span class="sxs-lookup"><span data-stu-id="cdf85-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="cdf85-127">例如，它将 `ABC` 和 `abc` 引用为单独的元素。</span><span class="sxs-lookup"><span data-stu-id="cdf85-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="cdf85-128">XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="cdf85-128">XML Namespaces</span></span>  

 <span data-ttu-id="cdf85-129">创建 XML 元素文本时，可以指定元素名称的 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="cdf85-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="cdf85-130">有关详细信息，请参阅 [XML 元素文本](../../../language-reference/xml-literals/xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="cdf85-130">For more information, see [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf85-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="cdf85-131">See also</span></span>

- [<span data-ttu-id="cdf85-132">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="cdf85-132">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="cdf85-133">XML 元素文本</span><span class="sxs-lookup"><span data-stu-id="cdf85-133">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
