---
title: 如何：使用 LINQ 查询 ArrayList
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: b7b75e017fb314b5e5998b743dbf922f34fd9b7c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396462"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="72df7-102">如何：使用 LINQ 查询 ArrayList （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="72df7-102">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>

<span data-ttu-id="72df7-103">如果使用 LINQ 来查询非泛型 <xref:System.Collections.IEnumerable> 集合（例如 <xref:System.Collections.ArrayList>），必须显式声明范围变量的类型，以反映集合中对象的特定类型。</span><span class="sxs-lookup"><span data-stu-id="72df7-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="72df7-104">例如，如果有 <xref:System.Collections.ArrayList> 对象的，那么 `Student` [from 子句](../../../language-reference/queries/from-clause.md)应如下所示：</span><span class="sxs-lookup"><span data-stu-id="72df7-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../language-reference/queries/from-clause.md) should look like this:</span></span>

```vb
Dim query = From student As Student In arrList
'...
```

<span data-ttu-id="72df7-105">通过指定范围变量的类型，可将 <xref:System.Collections.ArrayList> 中的每项强制转换为 `Student`。</span><span class="sxs-lookup"><span data-stu-id="72df7-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>

<span data-ttu-id="72df7-106">在查询表达式中使用显式类型范围变量等效于调用 <xref:System.Linq.Enumerable.Cast%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="72df7-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="72df7-107">如果无法执行指定的强制转换，<xref:System.Linq.Enumerable.Cast%2A> 将引发异常。</span><span class="sxs-lookup"><span data-stu-id="72df7-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="72df7-108"><xref:System.Linq.Enumerable.Cast%2A> 和 <xref:System.Linq.Enumerable.OfType%2A> 是两个标准查询运算符方法，可对非泛型 <xref:System.Collections.IEnumerable> 类型执行操作。</span><span class="sxs-lookup"><span data-stu-id="72df7-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="72df7-109">在 Visual Basic 中，必须对 <xref:System.Linq.Enumerable.Cast%2A> 数据源显式调用方法，以确保特定范围变量类型。</span><span class="sxs-lookup"><span data-stu-id="72df7-109">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="72df7-110">有关详细信息，请参阅[查询操作中的类型关系（Visual Basic）](type-relationships-in-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="72df7-110">For more information, see [Type Relationships in Query Operations (Visual Basic)](type-relationships-in-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="72df7-111">示例</span><span class="sxs-lookup"><span data-stu-id="72df7-111">Example</span></span>

<span data-ttu-id="72df7-112">下面的示例演示对 <xref:System.Collections.ArrayList> 的简单查询。</span><span class="sxs-lookup"><span data-stu-id="72df7-112">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="72df7-113">请注意，本示例在代码调用 <xref:System.Collections.ArrayList.Add%2A> 方法时使用对象初始值设定项，但这不是必需的。</span><span class="sxs-lookup"><span data-stu-id="72df7-113">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>

```vb
Imports System.Collections
Imports System.Linq

Module Module1

    Public Class Student
        Public Property FirstName As String
        Public Property LastName As String
        Public Property Scores As Integer()
    End Class

    Sub Main()

        Dim student1 As New Student With {.FirstName = "Svetlana",
                                     .LastName = "Omelchenko",
                                     .Scores = New Integer() {98, 92, 81, 60}}
        Dim student2 As New Student With {.FirstName = "Claire",
                                    .LastName = "O'Donnell",
                                    .Scores = New Integer() {75, 84, 91, 39}}
        Dim student3 As New Student With {.FirstName = "Cesar",
                                    .LastName = "Garcia",
                                    .Scores = New Integer() {97, 89, 85, 82}}
        Dim student4 As New Student With {.FirstName = "Sven",
                                    .LastName = "Mortensen",
                                    .Scores = New Integer() {88, 94, 65, 91}}

        Dim arrList As New ArrayList()
        arrList.Add(student1)
        arrList.Add(student2)
        arrList.Add(student3)
        arrList.Add(student4)

        ' Use an explicit type for non-generic collections
        Dim query = From student As Student In arrList
                    Where student.Scores(0) > 95
                    Select student

        For Each student As Student In query
            Console.WriteLine(student.LastName & ": " & student.Scores(0))
        Next
        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Module
' Output:
'   Omelchenko: 98
'   Garcia: 97
```

## <a name="see-also"></a><span data-ttu-id="72df7-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72df7-114">See also</span></span>

- [<span data-ttu-id="72df7-115">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72df7-115">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
