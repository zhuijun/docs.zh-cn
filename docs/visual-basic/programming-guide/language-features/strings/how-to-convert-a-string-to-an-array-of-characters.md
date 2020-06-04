---
title: 如何：将字符串转换为字符数组
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: eca8cd7be8da1f6149dadf1e9edeab5e5225ab9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360665"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="a0330-102">如何：在 Visual Basic 中将字符串转换为字符数组</span><span class="sxs-lookup"><span data-stu-id="a0330-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="a0330-103">有时，对字符串中的字符和这些字符在字符串中的位置（例如在分析字符串时）使用数据是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="a0330-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="a0330-104">此示例演示如何通过调用字符串的方法来获取字符串中的字符数组 <xref:System.String.ToCharArray%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a0330-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0330-105">示例</span><span class="sxs-lookup"><span data-stu-id="a0330-105">Example</span></span>  
 <span data-ttu-id="a0330-106">此示例演示如何将字符串拆分为 `Char` 数组，以及如何将字符串拆分为 `String` 其 Unicode 文本字符的数组。</span><span class="sxs-lookup"><span data-stu-id="a0330-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="a0330-107">此区别的原因是 Unicode 文本字符可以由两个或更多字符组成 `Char` （如代理项对或组合字符序列）。</span><span class="sxs-lookup"><span data-stu-id="a0330-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="a0330-108">有关详细信息，请参阅 <xref:System.Globalization.TextElementEnumerator> 和[Unicode 标准](https://www.unicode.org/standard/standard.html)。</span><span class="sxs-lookup"><span data-stu-id="a0330-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a><span data-ttu-id="a0330-109">示例</span><span class="sxs-lookup"><span data-stu-id="a0330-109">Example</span></span>  
 <span data-ttu-id="a0330-110">更难将字符串拆分为其 Unicode 文本字符，但如果需要有关字符串的可视化表示形式的信息，则这是必需的。</span><span class="sxs-lookup"><span data-stu-id="a0330-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="a0330-111">此示例使用 <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> 方法获取有关构成字符串的 Unicode 文本字符的信息。</span><span class="sxs-lookup"><span data-stu-id="a0330-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a><span data-ttu-id="a0330-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0330-112">See also</span></span>

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="a0330-113">如何：访问字符串中的字符</span><span class="sxs-lookup"><span data-stu-id="a0330-113">How to: Access Characters in Strings</span></span>](how-to-access-characters-in-strings.md)
- [<span data-ttu-id="a0330-114">Visual Basic 中字符串和其他数据类型间的转换</span><span class="sxs-lookup"><span data-stu-id="a0330-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="a0330-115">字符串</span><span class="sxs-lookup"><span data-stu-id="a0330-115">Strings</span></span>](index.md)
