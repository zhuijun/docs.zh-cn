---
title: 如何：从 Char 值的数组创建字符串
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 08ad2f1c9455853e92533a7f00726c73b6adb87e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071152"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="18356-102">如何：从 Char 值的数组创建字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18356-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>

<span data-ttu-id="18356-103">此示例从单个字符创建字符串 "abcd"。</span><span class="sxs-lookup"><span data-stu-id="18356-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18356-104">示例</span><span class="sxs-lookup"><span data-stu-id="18356-104">Example</span></span>  

 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="18356-105">编译代码</span><span class="sxs-lookup"><span data-stu-id="18356-105">Compile the code</span></span>  

 <span data-ttu-id="18356-106">此方法没有特殊要求。</span><span class="sxs-lookup"><span data-stu-id="18356-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="18356-107">语法 `"a"c` （其中单个 `c` 字符后跟引号中的单个字符）用于创建字符文本。</span><span class="sxs-lookup"><span data-stu-id="18356-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="18356-108">可靠编程</span><span class="sxs-lookup"><span data-stu-id="18356-108">Robust Programming</span></span>  

 <span data-ttu-id="18356-109">Null 字符 (等效于 `Chr(0)` 字符串中的) 在使用字符串时导致意外的结果。</span><span class="sxs-lookup"><span data-stu-id="18356-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="18356-110">字符串中将包含 null 字符，但在某些情况下，将不会显示空字符后面的字符。</span><span class="sxs-lookup"><span data-stu-id="18356-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18356-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="18356-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="18356-112">Char 数据类型</span><span class="sxs-lookup"><span data-stu-id="18356-112">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="18356-113">数据类型</span><span class="sxs-lookup"><span data-stu-id="18356-113">Data Types</span></span>](../data-types/index.md)
