---
title: 如何：访问字符串中的字符
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 4ea37c4393a8ece5513327b22c6c0ba4b027c781
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059179"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="6d634-102">如何：在 Visual Basic 中访问字符串中的字符</span><span class="sxs-lookup"><span data-stu-id="6d634-102">How to: Access Characters in Strings in Visual Basic</span></span>

<span data-ttu-id="6d634-103">此示例演示如何使用 <xref:System.String.Chars%2A> 属性访问字符串中指定位置处的字符。</span><span class="sxs-lookup"><span data-stu-id="6d634-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d634-104">示例</span><span class="sxs-lookup"><span data-stu-id="6d634-104">Example</span></span>  

 <span data-ttu-id="6d634-105">有时，请在字符串中包含有关字符串中的字符和这些字符的位置的数据。</span><span class="sxs-lookup"><span data-stu-id="6d634-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="6d634-106">你可以将字符串视为)  (实例的字符数组 `Char` ; 你可以通过属性引用该字符的索引来检索特定字符 <xref:System.String.Chars%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6d634-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="6d634-107">`index`属性的参数 <xref:System.String.Chars%2A> 是从零开始的。</span><span class="sxs-lookup"><span data-stu-id="6d634-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6d634-108">可靠编程</span><span class="sxs-lookup"><span data-stu-id="6d634-108">Robust Programming</span></span>  

 <span data-ttu-id="6d634-109"><xref:System.String.Chars%2A>属性返回指定位置处的字符。</span><span class="sxs-lookup"><span data-stu-id="6d634-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="6d634-110">但是，某些 Unicode 字符可以由多个字符表示。</span><span class="sxs-lookup"><span data-stu-id="6d634-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="6d634-111">有关如何使用 Unicode 字符的详细信息，请参阅 [如何：将字符串转换为字符数组](how-to-convert-a-string-to-an-array-of-characters.md)。</span><span class="sxs-lookup"><span data-stu-id="6d634-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="6d634-112"><xref:System.String.Chars%2A> <xref:System.IndexOutOfRangeException> 如果 `index` 参数大于或等于字符串的长度，则属性引发异常; 如果小于零，则引发异常。</span><span class="sxs-lookup"><span data-stu-id="6d634-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d634-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="6d634-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="6d634-114">如何：将字符串转换为字符数组</span><span class="sxs-lookup"><span data-stu-id="6d634-114">How to: Convert a String to an Array of Characters</span></span>](how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="6d634-115">Visual Basic 中字符串和其他数据类型间的转换</span><span class="sxs-lookup"><span data-stu-id="6d634-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="6d634-116">字符串</span><span class="sxs-lookup"><span data-stu-id="6d634-116">Strings</span></span>](index.md)
