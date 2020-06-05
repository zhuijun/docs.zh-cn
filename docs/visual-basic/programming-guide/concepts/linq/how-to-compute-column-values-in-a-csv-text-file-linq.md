---
title: 如何：在 CSV 文本文件中计算列值 (LINQ)
ms.date: 07/20/2015
ms.assetid: 88b2b9f3-c82e-41f3-b1b4-26ede5973a02
ms.openlocfilehash: 679d53787b1392181696c05e0327ca1b1b910015
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357499"
---
# <a name="how-to-compute-column-values-in-a-csv-text-file-linq-visual-basic"></a><span data-ttu-id="960e7-102">如何：在 CSV 文本文件中计算列值（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="960e7-102">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="960e7-103">此示例演示如何对 .csv 文件的列执行 Sum、Average、Min 和 Max 等聚合计算。</span><span class="sxs-lookup"><span data-stu-id="960e7-103">This example shows how to perform aggregate computations such as Sum, Average, Min, and Max on the columns of a .csv file.</span></span> <span data-ttu-id="960e7-104">此处所示的示例原则可以应用于其他类型的结构化文本。</span><span class="sxs-lookup"><span data-stu-id="960e7-104">The example principles that are shown here can be applied to other types of structured text.</span></span>

### <a name="to-create-the-source-file"></a><span data-ttu-id="960e7-105">创建源文件</span><span class="sxs-lookup"><span data-stu-id="960e7-105">To create the source file</span></span>

1. <span data-ttu-id="960e7-106">将以下行复制到名为 scores.csv 的文件，并将文件保存到项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="960e7-106">Copy the following lines into a file that is named scores.csv and save it in your project folder.</span></span> <span data-ttu-id="960e7-107">假定第一列表示学生 ID，后面几列表示四次考试的分数。</span><span class="sxs-lookup"><span data-stu-id="960e7-107">Assume that the first column represents a student ID, and subsequent columns represent scores from four exams.</span></span>

    ```csv
    111, 97, 92, 81, 60
    112, 75, 84, 91, 39
    113, 88, 94, 65, 91
    114, 97, 89, 85, 82
    115, 35, 72, 91, 70
    116, 99, 86, 90, 94
    117, 93, 92, 80, 87
    118, 92, 90, 83, 78
    119, 68, 79, 88, 92
    120, 99, 82, 81, 79
    121, 96, 85, 91, 60
    122, 94, 92, 91, 91
    ```

## <a name="example"></a><span data-ttu-id="960e7-108">示例</span><span class="sxs-lookup"><span data-stu-id="960e7-108">Example</span></span>

```vb
Class SumColumns

    Public Shared Sub Main()

        Dim lines As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' Specifies the column to compute
        ' This value could be passed in at runtime.
        Dim exam = 3

        ' Spreadsheet format:
        ' Student ID    Exam#1  Exam#2  Exam#3  Exam#4
        ' 111,          97,     92,     81,     60
        ' one is added to skip over the first column
        ' which holds the student ID.
        SumColumn(lines, exam + 1)
        Console.WriteLine()
        MultiColumns(lines)

        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit...")
        Console.ReadKey()

    End Sub

    Shared Sub SumColumn(ByVal lines As IEnumerable(Of String), ByVal col As Integer)

        ' This query performs two steps:
        ' split the string into a string array
        ' convert the specified element to
        ' integer and select it.
        Dim columnQuery = From line In lines
                           Let x = line.Split(",")
                           Select Convert.ToInt32(x(col))

        ' Execute and cache the results for performance.
        ' Only needed with very large files.
        Dim results = columnQuery.ToList()

        ' Perform aggregate calculations
        ' on the column specified by col.
        Dim avgScore = Aggregate score In results Into Average(score)
        Dim minScore = Aggregate score In results Into Min(score)
        Dim maxScore = Aggregate score In results Into Max(score)

        Console.WriteLine("Single Column Query:")
        Console.WriteLine("Exam #{0}: Average:{1:##.##} High Score:{2} Low Score:{3}",
                     col, avgScore, maxScore, minScore)

    End Sub

    Shared Sub MultiColumns(ByVal lines As IEnumerable(Of String))

        Console.WriteLine("Multi Column Query:")

        ' Create the query. It will produce nested sequences.
        ' multiColQuery performs these steps:
        ' 1) convert the string to a string array
        ' 2) skip over the "Student ID" column and take the rest
        ' 3) convert each field to an int and select that
        '    entire sequence as one row in the results.
        Dim multiColQuery = From line In lines
                            Let fields = line.Split(",")
                            Select From str In fields Skip 1
                                        Select Convert.ToInt32(str)

        Dim results = multiColQuery.ToList()

        ' Find out how many columns we have.
        Dim columnCount = results(0).Count()

        ' Perform aggregate calculations on each column.
        ' One loop for each score column in scores.
        ' We can use a for loop because we have already
        ' executed the multiColQuery in the call to ToList.

        For j As Integer = 0 To columnCount - 1
            Dim column = j
            Dim res2 = From row In results
                       Select row.ElementAt(column)

            ' Perform aggregate calculations
            ' on the column specified by col.
            Dim avgScore = Aggregate score In res2 Into Average(score)
            Dim minScore = Aggregate score In res2 Into Min(score)
            Dim maxScore = Aggregate score In res2 Into Max(score)

            ' Add 1 to column numbers because exams in this course start with #1
            Console.WriteLine("Exam #{0} Average: {1:##.##} High Score: {2} Low Score: {3}",
                              column + 1, avgScore, maxScore, minScore)

        Next
    End Sub

End Class
' Output:
' Single Column Query:
' Exam #4: Average:76.92 High Score:94 Low Score:39

' Multi Column Query:
' Exam #1 Average: 86.08 High Score: 99 Low Score: 35
' Exam #2 Average: 86.42 High Score: 94 Low Score: 72
' Exam #3 Average: 84.75 High Score: 91 Low Score: 65
' Exam #4 Average: 76.92 High Score: 94 Low Score: 39
```

<span data-ttu-id="960e7-109">查询的工作原理是使用 <xref:System.String.Split%2A> 方法将每一行文本转换为数组。</span><span class="sxs-lookup"><span data-stu-id="960e7-109">The query works by using the <xref:System.String.Split%2A> method to convert each line of text into an array.</span></span> <span data-ttu-id="960e7-110">每个数组元素表示一列。</span><span class="sxs-lookup"><span data-stu-id="960e7-110">Each array element represents a column.</span></span> <span data-ttu-id="960e7-111">最后，每一列中的文本都转换为其数字表示形式。</span><span class="sxs-lookup"><span data-stu-id="960e7-111">Finally, the text in each column is converted to its numeric representation.</span></span> <span data-ttu-id="960e7-112">如果文件是制表符分隔文件，只需将 `Split` 方法中的参数更新为 `\t`。</span><span class="sxs-lookup"><span data-stu-id="960e7-112">If your file is a tab-separated file, just update the argument in the `Split` method to `\t`.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="960e7-113">编译代码</span><span class="sxs-lookup"><span data-stu-id="960e7-113">Compile the code</span></span>

<span data-ttu-id="960e7-114">使用 `Imports` System. Linq 命名空间的语句创建 Visual Basic 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="960e7-114">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="960e7-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="960e7-115">See also</span></span>

- [<span data-ttu-id="960e7-116">LINQ 和字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="960e7-116">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="960e7-117">LINQ 和文件目录 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="960e7-117">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
