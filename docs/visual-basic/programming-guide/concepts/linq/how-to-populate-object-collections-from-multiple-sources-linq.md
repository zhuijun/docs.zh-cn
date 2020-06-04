---
title: 如何：从多个源填充对象集合 (LINQ)
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 9c6d8ff5165bf886d8aad87b64305819e65361ab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396514"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="5979e-102">如何：从多个源填充对象集合（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5979e-102">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="5979e-103">本示例演示如何将来自不同源的数据合并到一系列新的类型。</span><span class="sxs-lookup"><span data-stu-id="5979e-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="5979e-104">请勿尝试将内存中数据或文件系统中的数据与仍在数据库中的数据进行联接。</span><span class="sxs-lookup"><span data-stu-id="5979e-104">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="5979e-105">这种跨域联接可能产生未定义的结果，因为可能为数据库查询和其他类型的源定义了联接操作的不同方式。</span><span class="sxs-lookup"><span data-stu-id="5979e-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="5979e-106">此外，如果数据库中的数据量足够大，这样的操作还存在可能导致内存不足的异常的风险。</span><span class="sxs-lookup"><span data-stu-id="5979e-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="5979e-107">若要将数据库中的数据联接到内存数据，首先对数据库查询调用 `ToList` 或 `ToArray`，然后对返回的集合执行联接。</span><span class="sxs-lookup"><span data-stu-id="5979e-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="5979e-108">创建数据文件</span><span class="sxs-lookup"><span data-stu-id="5979e-108">To create the data file</span></span>

- <span data-ttu-id="5979e-109">按照[如何：联接不同文件的内容（LINQ）（Visual Basic）](how-to-join-content-from-dissimilar-files-linq.md)中的说明，将名称 .csv 和分数 .csv 文件复制到项目文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5979e-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="5979e-110">示例</span><span class="sxs-lookup"><span data-stu-id="5979e-110">Example</span></span>

<span data-ttu-id="5979e-111">下面的示例演示如何使用命名类型 `Student` 存储来自两个内存字符串集合（模拟 .csv 格式的电子表格数据）的合并数据。</span><span class="sxs-lookup"><span data-stu-id="5979e-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="5979e-112">第一个字符串集合代表学生姓名和 ID，第二个集合代表学生 ID（在第一列）和四次考试分数。</span><span class="sxs-lookup"><span data-stu-id="5979e-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="5979e-113">此 ID 用作外键。</span><span class="sxs-lookup"><span data-stu-id="5979e-113">The ID is used as the foreign key.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Linq

Class Student
    Public FirstName As String
    Public LastName As String
    Public ID As Integer
    Public ExamScores As List(Of Integer)
End Class

Class PopulateCollection

    Shared Sub Main()

        ' Merge content from spreadsheets into a list of Student objects.

        ' These data files are defined in How to: Join Content from
        ' Dissimilar Files (LINQ).

        ' Each line of names.csv consists of a last name, a first name, and an
        ' ID number, separated by commas. For example, Omelchenko,Svetlana,111
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")

        ' Each line of scores.csv consists of an ID number and four test
        ' scores, separated by commas. For example, 111, 97, 92, 81, 60
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' The following query merges the content of two dissimilar spreadsheets
        ' based on common ID values.
        ' Multiple From clauses are used instead of a Join clause
        ' in order to store the results of scoreLine.Split.
        ' Note the dynamic creation of a list of integers for the
        ' ExamScores member. The first item is skipped in the split string
        ' because it is the student ID, not an exam score.
        Dim queryNamesScores = From nameLine In names
                          Let splitName = nameLine.Split(New Char() {","})
                          From scoreLine In scores
                          Let splitScoreLine = scoreLine.Split(New Char() {","})
                          Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
                          Select New Student() With {
                               .FirstName = splitName(1), .LastName = splitName(0), .ID = splitName(2),
                               .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                                             Select Convert.ToInt32(scoreAsText)).ToList()}

        ' Optional. Store the query results for faster access in future
        ' queries. This could be useful with very large data files.
        Dim students As List(Of Student) = queryNamesScores.ToList()

        ' Display each student's name and exam score average.
        For Each s In students
            Console.WriteLine("The average score of " & s.FirstName & " " &
                              s.LastName & " is " & s.ExamScores.Average())
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class

' Output:
' The average score of Svetlana Omelchenko is 82.5
' The average score of Claire O'Donnell is 72.25
' The average score of Sven Mortensen is 84.5
' The average score of Cesar Garcia is 88.25
' The average score of Debra Garcia is 67
' The average score of Fadi Fakhouri is 92.25
' The average score of Hanying Feng is 88
' The average score of Hugo Garcia is 85.75
' The average score of Lance Tucker is 81.75
' The average score of Terry Adams is 85.25
' The average score of Eugene Zabokritski is 83
' The average score of Michael Tucker is 92
```

<span data-ttu-id="5979e-114">在[Select 子句](../../../language-reference/queries/select-clause.md)子句中，对象初始值设定项用于 `Student` 通过使用这两个源中的数据实例化每个新对象。</span><span class="sxs-lookup"><span data-stu-id="5979e-114">In the [Select Clause](../../../language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="5979e-115">如果不需要存储查询的结果，那么和命名类型相比，匿名类型使用起来更方便。</span><span class="sxs-lookup"><span data-stu-id="5979e-115">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="5979e-116">如果在执行查询的方法外部传递查询结果，则需要使用命名类型。</span><span class="sxs-lookup"><span data-stu-id="5979e-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="5979e-117">下面的示例执行与前面的示例相同的任务，但使用的是匿名类型，而不是命名类型：</span><span class="sxs-lookup"><span data-stu-id="5979e-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>

```vb
' Merge the data by using an anonymous type.
' Note the dynamic creation of a list of integers for the
' ExamScores member. We skip 1 because the first string
' in the array is the student ID, not an exam score.
Dim queryNamesScores2 =
    From nameLine In names
    Let splitName = nameLine.Split(New Char() {","})
    From scoreLine In scores
    Let splitScoreLine = scoreLine.Split(New Char() {","})
    Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
    Select New With
           {.Last = splitName(0),
            .First = splitName(1),
            .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                           Select Convert.ToInt32(scoreAsText)).ToList()}

' Display each student's name and exam score average.
For Each s In queryNamesScores2
    Console.WriteLine("The average score of " & s.First & " " &
                      s.Last & " is " & s.ExamScores.Average())
Next
```

## <a name="see-also"></a><span data-ttu-id="5979e-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5979e-118">See also</span></span>

- [<span data-ttu-id="5979e-119">LINQ 和字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5979e-119">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
