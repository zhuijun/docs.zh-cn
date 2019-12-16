---
title: "string（C# 参考）"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- string
- string_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 56847aad4cb8b0427594a299df2306d21675506b
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="string-c-reference"></a><span data-ttu-id="01bea-102">string（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="01bea-102">string (C# Reference)</span></span>
<span data-ttu-id="01bea-103">`string` 类型表示零个或多个 Unicode 字符的序列。</span><span class="sxs-lookup"><span data-stu-id="01bea-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="01bea-104">`string` 是 .NET Framework 中 <xref:System.String> 的别名。</span><span class="sxs-lookup"><span data-stu-id="01bea-104">`string` is an alias for <xref:System.String> in the .NET Framework.</span></span>  
  
 <span data-ttu-id="01bea-105">尽管 `string` 为引用类型，定义相等运算符（`==` 和 `!=`）是为了比较 `string` 对象（而不是引用）的值。</span><span class="sxs-lookup"><span data-stu-id="01bea-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="01bea-106">这使得对字符串相等性的测试更为直观。</span><span class="sxs-lookup"><span data-stu-id="01bea-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="01bea-107">例如：</span><span class="sxs-lookup"><span data-stu-id="01bea-107">For example:</span></span>  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 <span data-ttu-id="01bea-108">此时将显示“True”，然后显示“False”，因为字符串的内容是相等的，但 `a` 和 `b` 并不指代同一字符串实例。</span><span class="sxs-lookup"><span data-stu-id="01bea-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>  
  
 <span data-ttu-id="01bea-109">+ 运算符可连接字符串：</span><span class="sxs-lookup"><span data-stu-id="01bea-109">The + operator concatenates strings:</span></span>  
  
```csharp  
string a = "good " + "morning";  
```  
  
 <span data-ttu-id="01bea-110">这将创建包含“good morning”的字符串对象。</span><span class="sxs-lookup"><span data-stu-id="01bea-110">This creates a string object that contains "good morning".</span></span>  
  
 <span data-ttu-id="01bea-111">字符串是不可变的，即：字符串对象在创建后，尽管从语法上看似乎可以更改其内容，但事实上并不可行。</span><span class="sxs-lookup"><span data-stu-id="01bea-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="01bea-112">例如，编写此代码时，编译器实际上会创建一个新的字符串对象来保存新的字符序列，且该新对象将赋给 b。</span><span class="sxs-lookup"><span data-stu-id="01bea-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="01bea-113">然后，字符串“h”便可进行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="01bea-113">The string "h" is then eligible for garbage collection.</span></span>  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 <span data-ttu-id="01bea-114">[] 运算符可用于只读访问 `string` 的个别字符：</span><span class="sxs-lookup"><span data-stu-id="01bea-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 <span data-ttu-id="01bea-115">字符串文本属于类型 `string` 且可编写为两种形式，带引号和 @-quoted。</span><span class="sxs-lookup"><span data-stu-id="01bea-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="01bea-116">带引号字符串括在双引号 (") 内。</span><span class="sxs-lookup"><span data-stu-id="01bea-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>  
  
```csharp  
"good morning"  // a string literal  
```  
  
 <span data-ttu-id="01bea-117">字符串文本可包含任何字符文本。</span><span class="sxs-lookup"><span data-stu-id="01bea-117">String literals can contain any character literal.</span></span> <span data-ttu-id="01bea-118">包括转义序列。</span><span class="sxs-lookup"><span data-stu-id="01bea-118">Escape sequences are included.</span></span> <span data-ttu-id="01bea-119">下面的示例使用转义序列 `\\` 表示反斜杠，使用 `\u0066` 表示字母 f，以及使用 `\n` 表示换行符。</span><span class="sxs-lookup"><span data-stu-id="01bea-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>  
  
```  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  <span data-ttu-id="01bea-120">转义码 `\udddd`（其中 `dddd` 是一个四位数字）表示 Unicode 字符 U+`dddd`。</span><span class="sxs-lookup"><span data-stu-id="01bea-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="01bea-121">另外，还可识别八位 Unicode 转义码：`\Udddddddd`。</span><span class="sxs-lookup"><span data-stu-id="01bea-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>  
  
 <span data-ttu-id="01bea-122">逐字字符串文本以 @ 开头，并且也括在双引号内。</span><span class="sxs-lookup"><span data-stu-id="01bea-122">Verbatim string literals start with @ and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="01bea-123">例如: </span><span class="sxs-lookup"><span data-stu-id="01bea-123">For example:</span></span>  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 <span data-ttu-id="01bea-124">逐字字符串的优点是不处理转义序列，这样就可轻松编写完全限定的文件名等：</span><span class="sxs-lookup"><span data-stu-id="01bea-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 <span data-ttu-id="01bea-125">若要在 @-quoted 字符串中包含双引号，双倍添加即可：</span><span class="sxs-lookup"><span data-stu-id="01bea-125">To include a double quotation mark in an @-quoted string, double it:</span></span>  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 <span data-ttu-id="01bea-126">另一种 @ 符号用法是使用属于 C# 关键字的引用 ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) 标识符。</span><span class="sxs-lookup"><span data-stu-id="01bea-126">Another use of the @ symbol is to use referenced ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) identifiers that are C# keywords.</span></span>  
  
 <span data-ttu-id="01bea-127">有关 C# 中的字符串的详细信息，请参阅[字符串](../../../csharp/programming-guide/strings/index.md)。</span><span class="sxs-lookup"><span data-stu-id="01bea-127">For more information about strings in C#, see [Strings](../../../csharp/programming-guide/strings/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01bea-128">示例</span><span class="sxs-lookup"><span data-stu-id="01bea-128">Example</span></span>  
 <span data-ttu-id="01bea-129">[!code-cs[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="01bea-129">[!code-cs[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="01bea-130">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="01bea-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="01bea-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="01bea-131">See Also</span></span>  
 <span data-ttu-id="01bea-132">[C# 参考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="01bea-132">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="01bea-133">[C# 编程指南](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="01bea-133">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="01bea-134">[Best Practices for Using Strings](../../../standard/base-types/best-practices-strings.md) （有关使用字符串的最佳做法）</span><span class="sxs-lookup"><span data-stu-id="01bea-134">[Best Practices for Using Strings](../../../standard/base-types/best-practices-strings.md) </span></span>  
 <span data-ttu-id="01bea-135">[C# 关键字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="01bea-135">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="01bea-136">[C# 编程指南](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="01bea-136">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="01bea-137">[引用类型](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="01bea-137">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 <span data-ttu-id="01bea-138">[值类型](../../../csharp/language-reference/keywords/value-types.md) </span><span class="sxs-lookup"><span data-stu-id="01bea-138">[Value Types](../../../csharp/language-reference/keywords/value-types.md) </span></span>  
 <span data-ttu-id="01bea-139">[基本字符串操作](../../../standard/base-types/basic-string-operations.md) </span><span class="sxs-lookup"><span data-stu-id="01bea-139">[Basic String Operations](../../../standard/base-types/basic-string-operations.md) </span></span>  
 <span data-ttu-id="01bea-140">[创建新字符串](../../../standard/base-types/creating-new.md) </span><span class="sxs-lookup"><span data-stu-id="01bea-140">[Creating New Strings](../../../standard/base-types/creating-new.md) </span></span>  
 [<span data-ttu-id="01bea-141">设置数值结果表的格式</span><span class="sxs-lookup"><span data-stu-id="01bea-141">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
