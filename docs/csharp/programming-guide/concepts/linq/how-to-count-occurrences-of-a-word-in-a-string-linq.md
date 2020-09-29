---
title: 如何对某个词在字符串中出现的次数进行计数 (LINQ) (C#)
description: 此示例演示如何使用 C# 中的 LINQ 查询对指定词在字符串中出现的次数进行计数。 首先，它使用拆分方法来创建字符数组。
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: b354947c59747e49b5f3d099ebc3ea891fb4af90
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159067"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a><span data-ttu-id="30046-104">如何对某个词在字符串中出现的次数进行计数 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="30046-104">How to count occurrences of a word in a string (LINQ) (C#)</span></span>

<span data-ttu-id="30046-105">此示例演示如何使用 LINQ 查询对指定词在字符串中出现的次数进行计数。</span><span class="sxs-lookup"><span data-stu-id="30046-105">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="30046-106">请注意，若要执行计数，首先需调用 <xref:System.String.Split%2A> 方法来创建词数组。</span><span class="sxs-lookup"><span data-stu-id="30046-106">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="30046-107"><xref:System.String.Split%2A> 方法存在性能开销。</span><span class="sxs-lookup"><span data-stu-id="30046-107">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="30046-108">如果只需要统计字符串的字数，则应考虑改用 <xref:System.Text.RegularExpressions.Regex.Matches%2A> 或 <xref:System.String.IndexOf%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="30046-108">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="30046-109">但是，如果性能不是关键问题，或者已拆分句子以对其执行其他类型的查询，则使用 LINQ 来计数词或短语同样有意义。</span><span class="sxs-lookup"><span data-stu-id="30046-109">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30046-110">示例</span><span class="sxs-lookup"><span data-stu-id="30046-110">Example</span></span>  
  
```csharp  
class CountWords  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects" +  
          @" have not been well integrated. Programmers work in C# or Visual Basic" +  
          @" and also in SQL or XQuery. On the one side are concepts such as classes," +  
          @" objects, fields, inheritance, and .NET APIs. On the other side" +  
          @" are tables, columns, rows, nodes, and separate languages for dealing with" +  
          @" them. Data types often require translation between the two worlds; there are" +  
          @" different standard functions. Because the object world has no notion of query, a" +  
          @" query can only be represented as a string without compile-time type checking or" +  
          @" IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" +  
          @" objects in memory is often tedious and error-prone.";  
  
        string searchTerm = "data";  
  
        //Convert the string into an array of words  
        string[] source = text.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' }, StringSplitOptions.RemoveEmptyEntries);  
  
        // Create the query.  Use ToLowerInvariant to match "data" and "Data"
        var matchQuery = from word in source  
                         where word.ToLowerInvariant() == searchTerm.ToLowerInvariant()  
                         select word;  
  
        // Count the matches, which executes the query.  
        int wordCount = matchQuery.Count();  
        Console.WriteLine("{0} occurrences(s) of the search term \"{1}\" were found.", wordCount, searchTerm);  
  
        // Keep console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
   3 occurrences(s) of the search term "data" were found.  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="30046-111">编译代码</span><span class="sxs-lookup"><span data-stu-id="30046-111">Compiling the Code</span></span>  

 <span data-ttu-id="30046-112">使用 System.Linq 和 System.IO 命名空间的 `using` 指令创建 C# 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="30046-112">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30046-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="30046-113">See also</span></span>

- [<span data-ttu-id="30046-114">LINQ 和字符串 (C#)</span><span class="sxs-lookup"><span data-stu-id="30046-114">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
