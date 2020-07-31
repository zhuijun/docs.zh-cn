---
title: 如何查询字符串中的字符 (LINQ) (C#)
description: 可以使用 LINQ 将字符串作为字符序列进行查询。 此 C# 示例查询一个字符串以确定它所包含的数字数量。
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 3512be7c30843fcd8e881eab59761706a84a3ac8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104549"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="b9edc-104">如何查询字符串中的字符 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b9edc-104">How to query for characters in a string (LINQ) (C#)</span></span>
<span data-ttu-id="b9edc-105">因为 <xref:System.String> 类可实现泛型 <xref:System.Collections.Generic.IEnumerable%601> 接口，因此任何字符串都可以字符序列的形式进行查询。</span><span class="sxs-lookup"><span data-stu-id="b9edc-105">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="b9edc-106">但是，这不是 LINQ 的一般用法。</span><span class="sxs-lookup"><span data-stu-id="b9edc-106">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="b9edc-107">对于复杂的模式匹配操作，请使用 <xref:System.Text.RegularExpressions.Regex> 类。</span><span class="sxs-lookup"><span data-stu-id="b9edc-107">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9edc-108">示例</span><span class="sxs-lookup"><span data-stu-id="b9edc-108">Example</span></span>  
 <span data-ttu-id="b9edc-109">以下示例查询一个字符串以确定它所包含的数字数量。</span><span class="sxs-lookup"><span data-stu-id="b9edc-109">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="b9edc-110">请注意，在第一次执行此查询后将“重用”此查询。</span><span class="sxs-lookup"><span data-stu-id="b9edc-110">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="b9edc-111">这是可能的，因为查询本身并不存储任何实际的结果。</span><span class="sxs-lookup"><span data-stu-id="b9edc-111">This is possible because the query itself does not store any actual results.</span></span>  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9edc-112">编译代码</span><span class="sxs-lookup"><span data-stu-id="b9edc-112">Compiling the Code</span></span>  
 <span data-ttu-id="b9edc-113">使用 System.Linq 和 System.IO 命名空间的 `using` 指令创建 C# 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="b9edc-113">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9edc-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="b9edc-114">See also</span></span>

- [<span data-ttu-id="b9edc-115">LINQ 和字符串 (C#)</span><span class="sxs-lookup"><span data-stu-id="b9edc-115">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="b9edc-116">如何将 LINQ 查询与正则表达式合并 (C#)</span><span class="sxs-lookup"><span data-stu-id="b9edc-116">How to combine LINQ queries with regular expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
