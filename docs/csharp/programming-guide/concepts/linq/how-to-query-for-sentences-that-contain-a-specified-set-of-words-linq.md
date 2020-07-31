---
title: 如何查询包含一组指定词语的句子 (LINQ) (C#)
description: 了解如何使用 C# 中的 LINQ 在包含一组词语的每个匹配项的文本文件中查找句子，这些词语可在运行时进行填充。
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: c334c7948f19fb857709ff04a83e1dae56fc69da
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104524"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="d91bb-103">如何查询包含一组指定词语的句子 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d91bb-103">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>
<span data-ttu-id="d91bb-104">此示例演示如何在包含一组指定的词语的每个匹配项的文本文件中查找句子。</span><span class="sxs-lookup"><span data-stu-id="d91bb-104">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="d91bb-105">尽管此示例中的搜索词数组采用硬编码形式，但它也可在运行时以动态方式进行填充。</span><span class="sxs-lookup"><span data-stu-id="d91bb-105">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="d91bb-106">在此示例中，查询将返回包含单词“Historically,”、“data,”和“integrated”的句子。</span><span class="sxs-lookup"><span data-stu-id="d91bb-106">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="d91bb-107">示例</span><span class="sxs-lookup"><span data-stu-id="d91bb-107">Example</span></span>  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET Framework APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 <span data-ttu-id="d91bb-108">查询运行时首先将文本拆分成句子，然后将句子拆分成包含每个单词的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="d91bb-108">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="d91bb-109">对于每个数组，<xref:System.Linq.Enumerable.Distinct%2A> 方法将删除所有重复字词，然后查询将对字词数组和 `wordsToMatch` 数组执行 <xref:System.Linq.Enumerable.Intersect%2A> 操作。</span><span class="sxs-lookup"><span data-stu-id="d91bb-109">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="d91bb-110">如果相交数与 `wordsToMatch` 数组的计数相同，将在单词中找到所有单词并返回原始句子。</span><span class="sxs-lookup"><span data-stu-id="d91bb-110">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="d91bb-111">在对 <xref:System.String.Split%2A> 的调用中，使用标点符号作为分隔符，以从字符串中删除标点符号。</span><span class="sxs-lookup"><span data-stu-id="d91bb-111">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="d91bb-112">如果你没有不这样做，则假如你有一个字符串 “Historically,”，该字符串不会与 `wordsToMatch` 数组中的“Historically”匹配。</span><span class="sxs-lookup"><span data-stu-id="d91bb-112">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="d91bb-113">根据在源文本中找到的标点类型，可能需要使用其他分隔符。</span><span class="sxs-lookup"><span data-stu-id="d91bb-113">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d91bb-114">编译代码</span><span class="sxs-lookup"><span data-stu-id="d91bb-114">Compiling the Code</span></span>  
<span data-ttu-id="d91bb-115">使用 System.Linq 和 System.IO 命名空间的 `using` 指令创建 C# 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="d91bb-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="d91bb-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="d91bb-116">See also</span></span>

- [<span data-ttu-id="d91bb-117">LINQ 和字符串 (C#)</span><span class="sxs-lookup"><span data-stu-id="d91bb-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
