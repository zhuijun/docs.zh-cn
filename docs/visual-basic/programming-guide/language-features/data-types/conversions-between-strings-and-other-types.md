---
title: 字符串和其他类型之间的转换
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 823931f7d6beb8218e8b99d4a8d45716b7214304
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077145"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="671e7-102">字符串和其他类型之间的转换 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="671e7-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>

<span data-ttu-id="671e7-103">您可以将数字、 `Boolean` 或日期/时间值转换为 `String` 。</span><span class="sxs-lookup"><span data-stu-id="671e7-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="671e7-104">您还可以反向转换（从字符串值转换为数字， `Boolean` 或），前提是 `Date` 字符串的内容可以解释为目标数据类型的有效值。</span><span class="sxs-lookup"><span data-stu-id="671e7-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="671e7-105">如果无法运行，则会发生运行时错误。</span><span class="sxs-lookup"><span data-stu-id="671e7-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="671e7-106">所有这些分配的转换均为任意方向，均为收缩转换。</span><span class="sxs-lookup"><span data-stu-id="671e7-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="671e7-107">应使用类型转换关键字 (、、、、、、、、、、、、、 `CBool` `CByte` `CDate` `CDbl` `CDec` `CInt` `CLng` `CSByte` `CShort` `CSng` `CStr` `CUInt` `CULng` `CUShort` 和 `CType`) 。</span><span class="sxs-lookup"><span data-stu-id="671e7-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="671e7-108"><xref:Microsoft.VisualBasic.Strings.Format%2A>和 <xref:Microsoft.VisualBasic.Conversion.Val%2A> 函数使你可以更进一步控制字符串和数字之间的转换。</span><span class="sxs-lookup"><span data-stu-id="671e7-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="671e7-109">如果已定义类或结构，则可以定义 `String` 与类或结构的类型之间的类型转换运算符。</span><span class="sxs-lookup"><span data-stu-id="671e7-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="671e7-110">有关更多信息，请参见 [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="671e7-110">For more information, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="671e7-111">将数字转换为字符串</span><span class="sxs-lookup"><span data-stu-id="671e7-111">Conversion of Numbers to Strings</span></span>  

 <span data-ttu-id="671e7-112">您可以使用 `Format` 函数将数字转换为带格式的字符串，该字符串不仅可以包含适当的数字，还可以包含格式符号 `$` ，如) 、千位分隔符或 *数字分组 (符号* （例如 `,`) ）和小数点分隔符 (（如) ） (`.` 。</span><span class="sxs-lookup"><span data-stu-id="671e7-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="671e7-113">`Format`根据 Windows**控制面板**中指定的**区域选项**设置自动使用适当的符号。</span><span class="sxs-lookup"><span data-stu-id="671e7-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="671e7-114">请注意，串联 (`&`) 运算符可以隐式将数字转换为字符串，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="671e7-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="671e7-115">将字符串转换为数字</span><span class="sxs-lookup"><span data-stu-id="671e7-115">Conversion of Strings to Numbers</span></span>  

 <span data-ttu-id="671e7-116">您可以使用 `Val` 函数将字符串中的数字显式转换为数字。</span><span class="sxs-lookup"><span data-stu-id="671e7-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="671e7-117">`Val` 读取字符串，直到遇到数字、空格、制表符、换行符或句点以外的字符。</span><span class="sxs-lookup"><span data-stu-id="671e7-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="671e7-118">序列 "&O" 和 "&H" 改变数值系统的基数，并终止扫描。</span><span class="sxs-lookup"><span data-stu-id="671e7-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="671e7-119">在停止读取之前，会 `Val` 将所有合适的字符转换为数值。</span><span class="sxs-lookup"><span data-stu-id="671e7-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="671e7-120">例如，下面的语句返回值 `141.825` 。</span><span class="sxs-lookup"><span data-stu-id="671e7-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="671e7-121">当 Visual Basic 将字符串转换为数值时，它将使用 Windows**控制面板**中指定的 "**区域选项**" 设置来解释千位分隔符、小数点分隔符和货币符号。</span><span class="sxs-lookup"><span data-stu-id="671e7-121">When Visual Basic converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="671e7-122">这意味着，转换可能会在一个设置中失败，而不是另一个设置。</span><span class="sxs-lookup"><span data-stu-id="671e7-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="671e7-123">例如， `"$14.20"` 在英语 (美国) 区域设置，而不是任何法语区域设置。</span><span class="sxs-lookup"><span data-stu-id="671e7-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="671e7-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="671e7-124">See also</span></span>

- [<span data-ttu-id="671e7-125">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="671e7-125">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="671e7-126">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="671e7-126">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="671e7-127">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="671e7-127">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="671e7-128">如何：在 Visual Basic 中将一个对象转换为其他类型</span><span class="sxs-lookup"><span data-stu-id="671e7-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="671e7-129">数组转换</span><span class="sxs-lookup"><span data-stu-id="671e7-129">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="671e7-130">数据类型</span><span class="sxs-lookup"><span data-stu-id="671e7-130">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="671e7-131">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="671e7-131">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="671e7-132">开发全球化和本地化应用</span><span class="sxs-lookup"><span data-stu-id="671e7-132">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
