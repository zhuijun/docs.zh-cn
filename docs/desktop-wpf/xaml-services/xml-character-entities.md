---
title: XML 字符实体和 XAML
ms.date: 03/30/2017
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
ms.openlocfilehash: 1ba99cda512bc5e18c646b09f26672a39c1cf53c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548187"
---
# <a name="xml-character-entities-and-xaml"></a><span data-ttu-id="1ea54-102">XML 字符实体和 XAML</span><span class="sxs-lookup"><span data-stu-id="1ea54-102">XML Character Entities and XAML</span></span>

<span data-ttu-id="1ea54-103">XAML 使用在 XML 中为特殊字符定义的字符实体。</span><span class="sxs-lookup"><span data-stu-id="1ea54-103">XAML uses character entities defined in XML for special characters.</span></span> <span data-ttu-id="1ea54-104">本主题介绍一些特定的字符实体和 XAML 中其他 XML 概念的一般注意事项。</span><span class="sxs-lookup"><span data-stu-id="1ea54-104">This topic describes some specific character entities and general considerations for other XML concepts in XAML.</span></span>

## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a><span data-ttu-id="1ea54-105">XAML 独有的字符实体和转义问题</span><span class="sxs-lookup"><span data-stu-id="1ea54-105">Character Entities and Escaping Issues That Are Unique to XAML</span></span>

<span data-ttu-id="1ea54-106">XAML 标记通常使用相同的字符实体和在 XML 中定义的转义序列。</span><span class="sxs-lookup"><span data-stu-id="1ea54-106">XAML markup typically uses the same character entities and escape sequences that are defined in XML.</span></span>

<span data-ttu-id="1ea54-107">主要的例外是大括号（{ 和 }）在 XAML 中具有意义，因为这些字符通知 XAML 处理器必须将括在大括号中的字符序列解释为标记扩展。</span><span class="sxs-lookup"><span data-stu-id="1ea54-107">The main exception is that braces ({ and }) have significance in XAML because these characters inform a XAML processor that a character sequence enclosed by braces must be interpreted as a markup extension.</span></span> <span data-ttu-id="1ea54-108">有关标记扩展的详细信息，请参阅 [Markup Extensions for XAML Overview](markup-extensions-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea54-108">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

<span data-ttu-id="1ea54-109">但是，你仍可通过使用特定于 XAML（而非 XML）的转义序列将大括号显示为原义字符。</span><span class="sxs-lookup"><span data-stu-id="1ea54-109">However, you can still display the braces as literal characters by using an escape sequence that is particular to XAML instead of XML.</span></span> <span data-ttu-id="1ea54-110">有关详细信息，请参阅[ {} 转义序列标记扩展](escape-sequence-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea54-110">For more information, see [{} Escape Sequence - Markup Extension](escape-sequence-markup-extension.md).</span></span>

<span data-ttu-id="1ea54-111">请注意，在 \\ 以字符串形式处理时，反斜杠 () 不需要使用转义序列。</span><span class="sxs-lookup"><span data-stu-id="1ea54-111">Note that a backslash (\\) does not require an escape sequence when it is handled as a string.</span></span>

## <a name="xml-character-entities"></a><span data-ttu-id="1ea54-112">XML 字符实体</span><span class="sxs-lookup"><span data-stu-id="1ea54-112">XML Character Entities</span></span>

<span data-ttu-id="1ea54-113">如前所述，通常用于编写 XAML 标记的大多数字符实体和转义序列都由 XML 定义。</span><span class="sxs-lookup"><span data-stu-id="1ea54-113">As mentioned previously, most character entities and escape sequences that are typically used to write XAML markup are defined by XML.</span></span> <span data-ttu-id="1ea54-114">本主题不提供这些实体的完整列表；实体的详细参考可在外部文档（如 XML 规范）中找到。</span><span class="sxs-lookup"><span data-stu-id="1ea54-114">This topic does not provide the complete list of these entities; a detailed reference for the entities can be found in external documentation, such as in XML specifications.</span></span> <span data-ttu-id="1ea54-115">但是，为方便起见，本主题列出了一些常在 XAML 标记中使用的特定 XML 字符实体。</span><span class="sxs-lookup"><span data-stu-id="1ea54-115">However, for convenience, this topic lists some of the specific XML character entities that are typically used in XAML markup.</span></span>

|<span data-ttu-id="1ea54-116">字符</span><span class="sxs-lookup"><span data-stu-id="1ea54-116">Character</span></span>|<span data-ttu-id="1ea54-117">实体</span><span class="sxs-lookup"><span data-stu-id="1ea54-117">Entity</span></span>|<span data-ttu-id="1ea54-118">说明</span><span class="sxs-lookup"><span data-stu-id="1ea54-118">Notes</span></span>|
|---------------|------------|-----------|
|<span data-ttu-id="1ea54-119">&（与号）</span><span class="sxs-lookup"><span data-stu-id="1ea54-119">& (ampersand)</span></span>|<span data-ttu-id="1ea54-120">\&amp;</span><span class="sxs-lookup"><span data-stu-id="1ea54-120">\&amp;</span></span>|<span data-ttu-id="1ea54-121">必须用于属性值和元素内容两者。</span><span class="sxs-lookup"><span data-stu-id="1ea54-121">Must be used both for attribute values and for content of an element.</span></span>|
|<span data-ttu-id="1ea54-122">> (大于号) </span><span class="sxs-lookup"><span data-stu-id="1ea54-122">> (greater-than character)</span></span>|<span data-ttu-id="1ea54-123">\&gt;</span><span class="sxs-lookup"><span data-stu-id="1ea54-123">\&gt;</span></span>|<span data-ttu-id="1ea54-124">必须用于属性值，但只要 < 不在该元素之前，就可以接受 > 作为元素的内容。</span><span class="sxs-lookup"><span data-stu-id="1ea54-124">Must be used for an attribute value, but > is acceptable as the content of an element as long as < does not precede it.</span></span>|
|<span data-ttu-id="1ea54-125">< (小于号) </span><span class="sxs-lookup"><span data-stu-id="1ea54-125">< (less-than character)</span></span>|<span data-ttu-id="1ea54-126">\&lt;</span><span class="sxs-lookup"><span data-stu-id="1ea54-126">\&lt;</span></span>|<span data-ttu-id="1ea54-127">必须用于属性值，但不 \< is acceptable as the content of an element as long as > 跟随。</span><span class="sxs-lookup"><span data-stu-id="1ea54-127">Must be used for an attribute value, but \< is acceptable as the content of an element as long as > does not follow it.</span></span>|
|<span data-ttu-id="1ea54-128">"（直双引号）</span><span class="sxs-lookup"><span data-stu-id="1ea54-128">" (straight quotation mark)</span></span>|<span data-ttu-id="1ea54-129">\&quot;</span><span class="sxs-lookup"><span data-stu-id="1ea54-129">\&quot;</span></span>|<span data-ttu-id="1ea54-130">必须用于属性值，但直双引号 (") 可作为元素内容。</span><span class="sxs-lookup"><span data-stu-id="1ea54-130">Must be used for an attribute value, but a straight quotation mark (") is acceptable as the content of an element.</span></span> <span data-ttu-id="1ea54-131">请注意，属性值可能括在直单引号 (') 或直双引号 (") 内；首先出现的字符定义属性值的引号，另一个引号则可用作值内部的文字。</span><span class="sxs-lookup"><span data-stu-id="1ea54-131">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|
|<span data-ttu-id="1ea54-132">'（直单引号）</span><span class="sxs-lookup"><span data-stu-id="1ea54-132">' (single straight quotation mark)</span></span>|<span data-ttu-id="1ea54-133">\&apos;</span><span class="sxs-lookup"><span data-stu-id="1ea54-133">\&apos;</span></span>|<span data-ttu-id="1ea54-134">必须用于属性值，但直单引号 (') 可作为元素内容。</span><span class="sxs-lookup"><span data-stu-id="1ea54-134">Must be used for an attribute value, but a single straight quotation mark (') is acceptable as the content of an element.</span></span> <span data-ttu-id="1ea54-135">请注意，属性值可能括在直单引号 (') 或直双引号 (") 内；首先出现的字符定义属性值的引号，另一个引号则可用作值内部的文字。</span><span class="sxs-lookup"><span data-stu-id="1ea54-135">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|
|<span data-ttu-id="1ea54-136">（数字字符映射）</span><span class="sxs-lookup"><span data-stu-id="1ea54-136">(numeric character mappings)</span></span>|<span data-ttu-id="1ea54-137">&#*[integer]*;或 & # x *[hex]*;</span><span class="sxs-lookup"><span data-stu-id="1ea54-137">&#*[integer]*; or &#x *[hex]*;</span></span>|<span data-ttu-id="1ea54-138">XAML 支持向处于活动状态的编码的数字字符映射。</span><span class="sxs-lookup"><span data-stu-id="1ea54-138">XAML supports numeric character mappings into the encoding that is active.</span></span>|
|<span data-ttu-id="1ea54-139">（不间断空格）</span><span class="sxs-lookup"><span data-stu-id="1ea54-139">(nonbreaking space)</span></span>|<span data-ttu-id="1ea54-140">&\#160; (假设 UTF-8 编码) </span><span class="sxs-lookup"><span data-stu-id="1ea54-140">&\#160; (assuming UTF-8 encoding)</span></span>|<span data-ttu-id="1ea54-141">对于流文档元素或采用文本（如 WPF <xref:System.Windows.Controls.TextBox>）的元素，不间断空格没有超出标记范围进行规范化，甚至是对于 `xml:space="default"` 也是如此。</span><span class="sxs-lookup"><span data-stu-id="1ea54-141">For flow document elements, or elements that take text such as the WPF <xref:System.Windows.Controls.TextBox>, nonbreaking spaces are not normalized out of the markup, even for `xml:space="default"`.</span></span> <span data-ttu-id="1ea54-142"> (有关详细信息，请参阅 [XAML 中的空白处理](white-space-processing.md)。 ) </span><span class="sxs-lookup"><span data-stu-id="1ea54-142">(For more information, see [White-space processing in XAML](white-space-processing.md).)</span></span>|

## <a name="xml-comment-format"></a><span data-ttu-id="1ea54-143">XML 注释格式</span><span class="sxs-lookup"><span data-stu-id="1ea54-143">XML Comment Format</span></span>

<span data-ttu-id="1ea54-144">XAML 使用 XML 注释格式：注释的开头为 `<!--`，注释的结尾为 `-->,` 且序列 `--` 不能出现在注释中。</span><span class="sxs-lookup"><span data-stu-id="1ea54-144">XAML uses the XML comment format: the start of the comment is `<!--`, the end of comment is `-->,` and the sequence `--` must not occur within the comment.</span></span>

## <a name="xml-processing-instructions"></a><span data-ttu-id="1ea54-145">XML 处理指令</span><span class="sxs-lookup"><span data-stu-id="1ea54-145">XML Processing Instructions</span></span>

<span data-ttu-id="1ea54-146">XAML 根据 XML 规范处理 XML 处理指令，该规范说明必须传递指令。</span><span class="sxs-lookup"><span data-stu-id="1ea54-146">XAML handles XML processing instructions according to XML specifications, which state that the instructions must be passed through.</span></span> <span data-ttu-id="1ea54-147">.NET XAML 服务中的 XAML 处理不使用任何处理指令。</span><span class="sxs-lookup"><span data-stu-id="1ea54-147">XAML processing in .NET XAML Services  does not use any processing instructions.</span></span> <span data-ttu-id="1ea54-148">使用 XAML 的其他现有框架也不会使用 XAML 中的处理指令。</span><span class="sxs-lookup"><span data-stu-id="1ea54-148">Other existing frameworks that use XAML also do not use processing instructions from XAML.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ea54-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="1ea54-149">See also</span></span>

- [<span data-ttu-id="1ea54-150">XAML 概述 (WPF)</span><span class="sxs-lookup"><span data-stu-id="1ea54-150">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="1ea54-151">标记扩展和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="1ea54-151">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [<span data-ttu-id="1ea54-152">XamlName 语法</span><span class="sxs-lookup"><span data-stu-id="1ea54-152">XamlName Grammar</span></span>](xamlname-grammar.md)
- [<span data-ttu-id="1ea54-153">XAML 中的空白处理</span><span class="sxs-lookup"><span data-stu-id="1ea54-153">White-space processing in XAML</span></span>](white-space-processing.md)
