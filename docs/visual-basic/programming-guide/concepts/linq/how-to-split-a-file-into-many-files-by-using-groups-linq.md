---
title: 如何：使用组将一个文件拆分成多个文件 (LINQ)
ms.date: 07/20/2015
ms.assetid: 5e8b2a2b-0b1d-4933-8a2b-03e91dfaf77f
ms.openlocfilehash: f6b11ab4b4fe11dbf1cb4cf07654b5ef3f6785ad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397708"
---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-visual-basic"></a><span data-ttu-id="6189c-102">如何：使用组将一个文件拆分成多个文件（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6189c-102">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="6189c-103">此示例演示一种进行以下操作的方法：合并两个文件的内容，然后创建一组以新方式整理数据的新文件。</span><span class="sxs-lookup"><span data-stu-id="6189c-103">This example shows one way to merge the contents of two files and then create a set of new files that organize the data in a new way.</span></span>

### <a name="to-create-the-data-files"></a><span data-ttu-id="6189c-104">创建数据文件</span><span class="sxs-lookup"><span data-stu-id="6189c-104">To create the data files</span></span>

1. <span data-ttu-id="6189c-105">将下面的姓名复制到名为 names1.txt 的文本文件，然后将此文件保存到项目文件夹：</span><span class="sxs-lookup"><span data-stu-id="6189c-105">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>

    ```text
    Bankov, Peter
    Holm, Michael
    Garcia, Hugo
    Potra, Cristina
    Noriega, Fabricio
    Aw, Kam Foo
    Beebe, Ann
    Toyoshima, Tim
    Guy, Wey Yuan
    Garcia, Debra
    ```

2. <span data-ttu-id="6189c-106">将下面的姓名复制到名为 names2.txt 的文本文件，然后将此文件保存到项目文件夹：注意这两个文件有一些共同的姓名。</span><span class="sxs-lookup"><span data-stu-id="6189c-106">Copy these names into a text file that is named names2.txt and save it in your project folder: Note that the two files have some names in common.</span></span>

    ```text
    Liu, Jinghao
    Bankov, Peter
    Holm, Michael
    Garcia, Hugo
    Beebe, Ann
    Gilchrist, Beth
    Myrcha, Jacek
    Giakoumakis, Leo
    McLin, Nkenge
    El Yassir, Mehdi
    ```

## <a name="example"></a><span data-ttu-id="6189c-107">示例</span><span class="sxs-lookup"><span data-stu-id="6189c-107">Example</span></span>

```vb
Class SplitWithGroups

    Shared Sub Main()

        Dim fileA As String() = System.IO.File.ReadAllLines("../../../names1.txt")
        Dim fileB As String() = System.IO.File.ReadAllLines("../../../names2.txt")

        ' Concatenate and remove duplicate names based on
        Dim mergeQuery As IEnumerable(Of String) = fileA.Union(fileB)

        ' Group the names by the first letter in the last name
        Dim groupQuery = From name In mergeQuery
                     Let n = name.Split(New Char() {","})
                     Order By n(0)
                     Group By groupKey = n(0)(0)
                     Into groupName = Group

        ' Create a new file for each group that was created
        ' Note that nested foreach loops are required to access
        ' individual items with each group.
        For Each gGroup In groupQuery
            Dim fileName As String = "..'..'..'testFile_" & gGroup.groupKey & ".txt"
            Dim sw As New System.IO.StreamWriter(fileName)
            Console.WriteLine(gGroup.groupKey)
            For Each item In gGroup.groupName
                Console.WriteLine("   " & item.name)
                sw.WriteLine(item.name)
            Next
            sw.Close()
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Files have been written. Press any key to exit.")
        Console.ReadKey()

    End Sub
End Class
' Console Output:
' A
'    Aw, Kam Foo
' B
'    Bankov, Peter
'    Beebe, Ann
' E
'    El Yassir, Mehdi
' G
'    Garcia, Hugo
'    Garcia, Debra
'    Giakoumakis, Leo
'    Gilchrist, Beth
'    Guy, Wey Yuan
' H
'    Holm, Michael
' L
'    Liu, Jinghao
' M
'    McLin, Nkenge
'    Myrcha, Jacek
' N
'    Noriega, Fabricio
' P
'    Potra, Cristina
' T
'    Toyoshima, Tim
```

<span data-ttu-id="6189c-108">对于与数据文件位于同一文件夹中的每个组，程序将为这些组编写单独的文件。</span><span class="sxs-lookup"><span data-stu-id="6189c-108">The program writes a separate file for each group in the same folder as the data files.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="6189c-109">编译代码</span><span class="sxs-lookup"><span data-stu-id="6189c-109">Compile the code</span></span>

<span data-ttu-id="6189c-110">使用 `Imports` System. Linq 命名空间的语句创建 Visual Basic 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="6189c-110">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="6189c-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6189c-111">See also</span></span>

- [<span data-ttu-id="6189c-112">LINQ 和字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6189c-112">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="6189c-113">LINQ 和文件目录 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6189c-113">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
