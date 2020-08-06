---
title: 如何确定字符串是否表示数值 - C# 编程指南
description: 了解如何确定字符串是否为指定数值类型的有效表示形式。 查看代码示例和其他资源。
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: c248c6c54de493ab06a833fc525252fa812d60da
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381744"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="14831-104">如何确定字符串是否表示数值（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="14831-104">How to determine whether a string represents a numeric value (C# Programming Guide)</span></span>
<span data-ttu-id="14831-105">若要确定字符串是否是指定数值类型的有效表示形式，请使用由所有基元数值类型以及如 <xref:System.DateTime> 和 <xref:System.Net.IPAddress> 等类型实现的静态 `TryParse` 方法。</span><span class="sxs-lookup"><span data-stu-id="14831-105">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="14831-106">以下示例演示如何确定“108”是否为有效的 [int](../../language-reference/builtin-types/integral-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="14831-106">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="14831-107">如果该字符串包含非数字字符，或者数值对于指定的特定类型而言太大或太小，则 `TryParse` 将返回 false 并将 out 参数设置为零。</span><span class="sxs-lookup"><span data-stu-id="14831-107">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="14831-108">否则，它将返回 true 并将 out 参数设置为字符串的数值。</span><span class="sxs-lookup"><span data-stu-id="14831-108">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14831-109">字符串可能仅包含数字字符，但对于你使用的 `TryParse` 方法的类型仍然无效。</span><span class="sxs-lookup"><span data-stu-id="14831-109">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="14831-110">例如，“256”不是 `byte` 的有效值，但对 `int` 有效。</span><span class="sxs-lookup"><span data-stu-id="14831-110">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="14831-111">“98.6”不是 `int` 的有效值，但它是有效的 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="14831-111">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14831-112">示例</span><span class="sxs-lookup"><span data-stu-id="14831-112">Example</span></span>  
 <span data-ttu-id="14831-113">以下示例演示如何对 `long`、`byte` 和 `decimal` 值的字符串表示形式使用 `TryParse`。</span><span class="sxs-lookup"><span data-stu-id="14831-113">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="14831-114">可靠编程</span><span class="sxs-lookup"><span data-stu-id="14831-114">Robust Programming</span></span>  
 <span data-ttu-id="14831-115">基元数值类型还实现 `Parse` 静态方法，如果字符串不是有效数字，该方法将引发异常。</span><span class="sxs-lookup"><span data-stu-id="14831-115">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="14831-116">`TryParse` 通常更高效，因为如果数值无效，它仅返回 false。</span><span class="sxs-lookup"><span data-stu-id="14831-116">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="14831-117">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="14831-117">.NET Security</span></span>  
 <span data-ttu-id="14831-118">请务必使用 `TryParse` 或 `Parse` 方法验证控件（如文本框和组合框）中的用户输入。</span><span class="sxs-lookup"><span data-stu-id="14831-118">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14831-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="14831-119">See also</span></span>

- [<span data-ttu-id="14831-120">如何将字节数组转换为 int</span><span class="sxs-lookup"><span data-stu-id="14831-120">How to convert a byte array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="14831-121">如何将字符串转换为数字</span><span class="sxs-lookup"><span data-stu-id="14831-121">How to convert a string to a number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="14831-122">如何在十六进制字符串与数值类型之间转换</span><span class="sxs-lookup"><span data-stu-id="14831-122">How to convert between hexadecimal strings and numeric types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="14831-123">分析数值字符串</span><span class="sxs-lookup"><span data-stu-id="14831-123">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="14831-124">格式设置类型</span><span class="sxs-lookup"><span data-stu-id="14831-124">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
