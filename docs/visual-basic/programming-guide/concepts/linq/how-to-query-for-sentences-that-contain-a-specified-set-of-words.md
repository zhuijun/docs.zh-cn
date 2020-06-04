---
title: 如何：查询包含一组指定词语的句子 (LINQ)
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: ce88bf001346f90eb9b08ca1ff14afc7dcb04fa0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397955"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a><span data-ttu-id="3109c-102">如何：查询包含一组指定词语的句子 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3109c-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="3109c-103">此示例演示如何在包含一组指定的词语的每个匹配项的文本文件中查找句子。</span><span class="sxs-lookup"><span data-stu-id="3109c-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="3109c-104">尽管此示例中的搜索词数组采用硬编码形式，但它也可在运行时以动态方式进行填充。</span><span class="sxs-lookup"><span data-stu-id="3109c-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="3109c-105">在此示例中，查询将返回包含单词“Historically,”、“data,”和“integrated”的句子。</span><span class="sxs-lookup"><span data-stu-id="3109c-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>

## <a name="example"></a><span data-ttu-id="3109c-106">示例</span><span class="sxs-lookup"><span data-stu-id="3109c-106">Example</span></span>

```vb
Class FindSentences

    Shared Sub Main()
        Dim text As String = "Historically, the world of data and the world of objects " &
        "have not been well integrated. Programmers work in C# or Visual Basic " &
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &
        "are tables, columns, rows, nodes, and separate languages for dealing with " &
        "them. Data types often require translation between the two worlds; there are " &
        "different standard functions. Because the object world has no notion of query, a " &
        "query can only be represented as a string without compile-time type checking or " &
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &
        "objects in memory is often tedious and error-prone."

        ' Split the text block into an array of sentences.
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})

        ' Define the search terms. This list could also be dynamically populated at runtime
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}

        ' Find sentences that contain all the terms in the wordsToMatch array
        ' Note that the number of terms to match is not specified at compile time
        Dim sentenceQuery = From sentence In sentences
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},
                                                   StringSplitOptions.RemoveEmptyEntries)
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()
                            Select sentence

        ' Execute the query
        For Each str As String In sentenceQuery
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Class
' Output:
' Historically, the world of data and the world of objects have not been well integrated
```

<span data-ttu-id="3109c-107">查询运行时首先将文本拆分成句子，然后将句子拆分成包含每个单词的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="3109c-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="3109c-108">对于每个数组，<xref:System.Linq.Enumerable.Distinct%2A> 方法将删除所有重复字词，然后查询将对字词数组和 `wordsToMatch` 数组执行 <xref:System.Linq.Enumerable.Intersect%2A> 操作。</span><span class="sxs-lookup"><span data-stu-id="3109c-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="3109c-109">如果相交数与 `wordsToMatch` 数组的计数相同，将在单词中找到所有单词并返回原始句子。</span><span class="sxs-lookup"><span data-stu-id="3109c-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>

<span data-ttu-id="3109c-110">在对 <xref:System.String.Split%2A> 的调用中，使用标点符号作为分隔符，以从字符串中删除标点符号。</span><span class="sxs-lookup"><span data-stu-id="3109c-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="3109c-111">如果你没有不这样做，则假如你有一个字符串 “Historically,”，该字符串不会与 `wordsToMatch` 数组中的“Historically”匹配。</span><span class="sxs-lookup"><span data-stu-id="3109c-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="3109c-112">根据在源文本中找到的标点类型，可能需要使用其他分隔符。</span><span class="sxs-lookup"><span data-stu-id="3109c-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="3109c-113">编译代码</span><span class="sxs-lookup"><span data-stu-id="3109c-113">Compile the code</span></span>

<span data-ttu-id="3109c-114">使用 `Imports` System. Linq 命名空间的语句创建 Visual Basic 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="3109c-114">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="3109c-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3109c-115">See also</span></span>

- [<span data-ttu-id="3109c-116">LINQ 和字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3109c-116">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
