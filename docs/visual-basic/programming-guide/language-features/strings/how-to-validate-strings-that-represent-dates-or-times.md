---
title: 如何：验证表示日期或时间的字符串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5d153ac29039375386b3cd5f03609b1e4bd1d5bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410562"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="9059e-102">如何：验证表示日期或时间的字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9059e-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="9059e-103">下面的代码示例设置一个 `Boolean` 值，该值指示字符串是否表示有效的日期或时间。</span><span class="sxs-lookup"><span data-stu-id="9059e-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9059e-104">示例</span><span class="sxs-lookup"><span data-stu-id="9059e-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="9059e-105">编译代码</span><span class="sxs-lookup"><span data-stu-id="9059e-105">Compile the code</span></span>  
 <span data-ttu-id="9059e-106">`("01/01/03")`将和替换为 `"9:30 PM"` 要验证的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="9059e-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="9059e-107">您可以使用 `String` 变量或返回字符串的方法（如）将字符串替换为另一个硬编码字符串 `InputBox` 。</span><span class="sxs-lookup"><span data-stu-id="9059e-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9059e-108">可靠编程</span><span class="sxs-lookup"><span data-stu-id="9059e-108">Robust Programming</span></span>  
 <span data-ttu-id="9059e-109">使用此方法在尝试将转换为变量之前验证字符串 `String` `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="9059e-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="9059e-110">首先检查日期或时间，您可以避免在运行时生成异常。</span><span class="sxs-lookup"><span data-stu-id="9059e-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9059e-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9059e-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="9059e-112">验证字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9059e-112">Validating Strings in Visual Basic</span></span>](validating-strings.md)
