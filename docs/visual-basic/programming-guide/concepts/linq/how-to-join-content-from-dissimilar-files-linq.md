---
title: 如何：联接不同文件中的内容 (LINQ)
ms.date: 06/27/2018
ms.assetid: e7530857-c467-41ea-9730-84e6b1065a4d
ms.openlocfilehash: 7dac73a16d0d3fbf409f58628bc5c69716dcee14
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398365"
---
# <a name="how-to-join-content-from-dissimilar-files-linq-visual-basic"></a><span data-ttu-id="41585-102">如何：联接不同文件的内容（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="41585-102">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="41585-103">本示例演示如何联接两个逗号分隔文件中的数据，这两个文件共享一个用作匹配键的公共值。</span><span class="sxs-lookup"><span data-stu-id="41585-103">This example shows how to join data from two comma-delimited files that share a common value that is used as a matching key.</span></span> <span data-ttu-id="41585-104">如果需要合并来自两个电子表格的数据，或者从一个电子表格和具有另一种格式的文件合并到一个新文件时，此技术很有用。</span><span class="sxs-lookup"><span data-stu-id="41585-104">This technique can be useful if you have to combine data from two spreadsheets, or from a spreadsheet and from a file that has another format, into a new file.</span></span> <span data-ttu-id="41585-105">可以修改此示例以用于任何类型的结构化文本。</span><span class="sxs-lookup"><span data-stu-id="41585-105">You can modify the example to work with any kind of structured text.</span></span>

## <a name="to-create-the-data-files"></a><span data-ttu-id="41585-106">创建数据文件</span><span class="sxs-lookup"><span data-stu-id="41585-106">To create the data files</span></span>

1. <span data-ttu-id="41585-107">将以下行复制到名为 scores.csv 的文件，并将文件保存到项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="41585-107">Copy the following lines into a file that is named scores.csv and save it to your project folder.</span></span> <span data-ttu-id="41585-108">此文件表示电子表格数据。</span><span class="sxs-lookup"><span data-stu-id="41585-108">The file represents spreadsheet data.</span></span> <span data-ttu-id="41585-109">第 1 列是学生的 ID，第 2 至 5 列是测验分数。</span><span class="sxs-lookup"><span data-stu-id="41585-109">Column 1 is the student's ID, and columns 2 through 5 are test scores.</span></span>

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

2. <span data-ttu-id="41585-110">将以下行复制到名为 names.csv 的文件，并将文件保存到项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="41585-110">Copy the following lines into a file that is named names.csv and save it to your project folder.</span></span> <span data-ttu-id="41585-111">此文件表示电子表格，其中包含学生的姓氏、名字和学生 ID。</span><span class="sxs-lookup"><span data-stu-id="41585-111">The file represents a spreadsheet that contains the student's last name, first name, and student ID.</span></span>

    ```csv
    Omelchenko,Svetlana,111
    O'Donnell,Claire,112
    Mortensen,Sven,113
    Garcia,Cesar,114
    Garcia,Debra,115
    Fakhouri,Fadi,116
    Feng,Hanying,117
    Garcia,Hugo,118
    Tucker,Lance,119
    Adams,Terry,120
    Zabokritski,Eugene,121
    Tucker,Michael,122
    ```

## <a name="example"></a><span data-ttu-id="41585-112">示例</span><span class="sxs-lookup"><span data-stu-id="41585-112">Example</span></span>

```vb
Imports System.Collections.Generic
Imports System.Linq

Class JoinStrings

    Shared Sub Main()

        ' Join content from spreadsheet files that contain
        ' related information. names.csv contains the student name
        ' plus an ID number. scores.csv contains the ID and a
        ' set of four test scores. The following query joins
        ' the scores to the student names by using ID as a
        ' matching key.

        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' Name:    Last[0],       First[1],  ID[2],     Grade Level[3]
        '          Omelchenko,    Svetlana,  111,       2
        ' Score:   StudentID[0],  Exam1[1]   Exam2[2],  Exam3[3],  Exam4[4]
        '          111,           97,        92,        81,        60

        ' This query joins two dissimilar spreadsheets based on common ID value.
        ' Multiple from clauses are used instead of a join clause
        ' in order to store results of id.Split.
        Dim scoreQuery1 = From name In names
                         Let n = name.Split(New Char() {","})
                            From id In scores
                            Let n2 = id.Split(New Char() {","})
                            Where Convert.ToInt32(n(2)) = Convert.ToInt32(n2(0))
                            Select n(0) & "," & n2(1) & "," & n2(2) & "," & n2(3) & "," &  n2(4)

        ' Pass a query variable to a Sub and execute it there.
        ' The query itself is unchanged.
        OutputQueryResults(scoreQuery1, "Merge two spreadsheets:")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

    Shared Sub OutputQueryResults(ByVal query As IEnumerable(Of String), ByVal message As String)

        Console.WriteLine(System.Environment.NewLine & message)
        For Each item As String In query
            Console.WriteLine(item)
        Next
        Console.WriteLine(query.Count & " total names in list")

    End Sub
End Class
' Output:
' Merge two spreadsheets:
' Omelchenko, 97, 92, 81, 60
' O'Donnell, 75, 84, 91, 39
' Mortensen, 88, 94, 65, 91
' Garcia, 97, 89, 85, 82
' Garcia, 35, 72, 91, 70
' Fakhouri, 99, 86, 90, 94
' Feng, 93, 92, 80, 87
' Garcia, 92, 90, 83, 78
' Tucker, 68, 79, 88, 92
' Adams, 99, 82, 81, 79
' Zabokritski, 96, 85, 91, 60
' Tucker, 94, 92, 91, 91
' 12 total names in list
```

## <a name="see-also"></a><span data-ttu-id="41585-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41585-113">See also</span></span>

- [<span data-ttu-id="41585-114">LINQ 和字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41585-114">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="41585-115">LINQ 和文件目录 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41585-115">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
