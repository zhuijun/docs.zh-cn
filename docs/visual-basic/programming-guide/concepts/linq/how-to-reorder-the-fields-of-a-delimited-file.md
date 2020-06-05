---
title: 如何：重新排列带分隔符的文件的字段 (LINQ)
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: 6f87374978425e0d51542c6eceda23697d7a3a67
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397890"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a><span data-ttu-id="d5251-102">如何：重新排列带分隔符的文件的字段（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d5251-102">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="d5251-103">逗号分隔值 (CSV) 文件是一种文本文件，通常用于存储电子表格数据或其他由行和列表示的表格数据。</span><span class="sxs-lookup"><span data-stu-id="d5251-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="d5251-104">通过使用 <xref:System.String.Split%2A> 方法分隔字段，可以非常轻松地使用 LINQ 来查询和操作 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="d5251-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="d5251-105">事实上，可以使用此技术来重新排列任何结构化文本行部分；此技术不局限于 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="d5251-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>

<span data-ttu-id="d5251-106">在下面的示例中，假设有三列分别代表学生的“姓氏”、“名字”和“ID”。</span><span class="sxs-lookup"><span data-stu-id="d5251-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="d5251-107">这些字段基于学生的姓氏按字母顺序排列。</span><span class="sxs-lookup"><span data-stu-id="d5251-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="d5251-108">查询生成一个新序列，其中首先出现的是 ID 列，后面的第二列组合了学生的名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="d5251-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="d5251-109">根据 ID 字段重新排列各行。</span><span class="sxs-lookup"><span data-stu-id="d5251-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="d5251-110">结果保存到新文件，但不修改原始数据。</span><span class="sxs-lookup"><span data-stu-id="d5251-110">The results are saved into a new file and the original data is not modified.</span></span>

### <a name="to-create-the-data-file"></a><span data-ttu-id="d5251-111">创建数据文件</span><span class="sxs-lookup"><span data-stu-id="d5251-111">To create the data file</span></span>

1. <span data-ttu-id="d5251-112">将以下各行复制到名为 spreadsheet1.csv 的纯文本文件。</span><span class="sxs-lookup"><span data-stu-id="d5251-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="d5251-113">将此文件保存到项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="d5251-113">Save the file in your project folder.</span></span>

    ```csv
    Adams,Terry,120
    Fakhouri,Fadi,116
    Feng,Hanying,117
    Garcia,Cesar,114
    Garcia,Debra,115
    Garcia,Hugo,118
    Mortensen,Sven,113
    O'Donnell,Claire,112
    Omelchenko,Svetlana,111
    Tucker,Lance,119
    Tucker,Michael,122
    Zabokritski,Eugene,121
    ```

## <a name="example"></a><span data-ttu-id="d5251-114">示例</span><span class="sxs-lookup"><span data-stu-id="d5251-114">Example</span></span>

```vb
Class CSVFiles

    Shared Sub Main()

        ' Create the IEnumerable data source.
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")

        ' Execute the query. Put field 2 first, then
        ' reverse and combine fields 0 and 1 from the old field
        Dim lineQuery = From line In lines
                        Let x = line.Split(New Char() {","})
                        Order By x(2)
                        Select x(2) & ", " & (x(1) & " " & x(0))

        ' Execute the query and write out the new file. Note that WriteAllLines
        ' takes a string array, so ToArray is called on the query.
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())

        ' Keep console window open in debug mode.
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output to spreadsheet2.csv:
' 111, Svetlana Omelchenko
' 112, Claire O'Donnell
' 113, Sven Mortensen
' 114, Cesar Garcia
' 115, Debra Garcia
' 116, Fadi Fakhouri
' 117, Hanying Feng
' 118, Hugo Garcia
' 119, Lance Tucker
' 120, Terry Adams
' 121, Eugene Zabokritski
' 122, Michael Tucker
```

## <a name="see-also"></a><span data-ttu-id="d5251-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d5251-115">See also</span></span>

- [<span data-ttu-id="d5251-116">LINQ 和字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5251-116">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="d5251-117">LINQ 和文件目录 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5251-117">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
- [<span data-ttu-id="d5251-118">如何：从 CSV 文件生成 XML</span><span class="sxs-lookup"><span data-stu-id="d5251-118">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
