---
title: 以零起始的字符串访问与以一起始的字符串访问
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 91d3fb9d7bfdf3d5af27fc6499583640946a802f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072283"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="1f575-102">从 0 开始与从 1 开始的字符串访问 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f575-102">Zero-based vs. One-based String Access in Visual Basic</span></span>

<span data-ttu-id="1f575-103">本主题比较 Visual Basic 和 .NET Framework 如何提供对字符串中的字符的访问。</span><span class="sxs-lookup"><span data-stu-id="1f575-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="1f575-104">.NET Framework 始终提供对字符串中的字符的从零开始的访问，而 Visual Basic 提供从零开始的和基于的访问（具体取决于函数）。</span><span class="sxs-lookup"><span data-stu-id="1f575-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="1f575-105">从1开始</span><span class="sxs-lookup"><span data-stu-id="1f575-105">One-Based</span></span>  

 <span data-ttu-id="1f575-106">有关基于一个 Visual Basic 函数的示例，请考虑 `Mid` 函数。</span><span class="sxs-lookup"><span data-stu-id="1f575-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="1f575-107">它采用一个参数，该参数指示子字符串的起始字符位置（从位置1开始）。</span><span class="sxs-lookup"><span data-stu-id="1f575-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="1f575-108">.NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法采用字符串中的字符的索引，子字符串将从位置0开始。</span><span class="sxs-lookup"><span data-stu-id="1f575-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="1f575-109">因此，如果您有字符串 "ABCDE...Z"，则每个字符的编号为1、2、3、4、5和函数一起使用 `Mid` ，但0、1、2、3、4用于 <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="1f575-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="1f575-110">从零开始</span><span class="sxs-lookup"><span data-stu-id="1f575-110">Zero-Based</span></span>  

 <span data-ttu-id="1f575-111">有关从零开始的 Visual Basic 函数的示例，请考虑 `Split` 函数。</span><span class="sxs-lookup"><span data-stu-id="1f575-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="1f575-112">它拆分字符串并返回包含子字符串的数组。</span><span class="sxs-lookup"><span data-stu-id="1f575-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="1f575-113">.NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> 方法还拆分字符串并返回包含子字符串的数组。</span><span class="sxs-lookup"><span data-stu-id="1f575-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="1f575-114">由于 `Split` 函数和 <xref:System.String.Split%2A> 方法返回 .NET Framework 数组，因此它们必须是从零开始的。</span><span class="sxs-lookup"><span data-stu-id="1f575-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f575-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="1f575-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="1f575-116">字符串介绍 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f575-116">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
