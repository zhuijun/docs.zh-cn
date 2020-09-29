---
title: 如何使用 LINQ 查询 ArrayList (C#)
description: 此示例使用 LINQ 对 C# 中的 ArrayList 进行查询。 必须声明范围变量的类型，以反映集合中对象的类型。
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: 278c05cfc864ee4f53e1215a2acb739efd87f8b1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153997"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="c1ddb-104">如何使用 LINQ 查询 ArrayList (C#)</span><span class="sxs-lookup"><span data-stu-id="c1ddb-104">How to query an ArrayList with LINQ (C#)</span></span>

<span data-ttu-id="c1ddb-105">如果使用 LINQ 来查询非泛型 <xref:System.Collections.IEnumerable> 集合（例如 <xref:System.Collections.ArrayList>），必须显式声明范围变量的类型，以反映集合中对象的特定类型。</span><span class="sxs-lookup"><span data-stu-id="c1ddb-105">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="c1ddb-106">例如，如果有 `Student` 对象的 <xref:System.Collections.ArrayList>，那么 [from 子句](../../../language-reference/keywords/from-clause.md)应如下所示：</span><span class="sxs-lookup"><span data-stu-id="c1ddb-106">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 <span data-ttu-id="c1ddb-107">通过指定范围变量的类型，可将 <xref:System.Collections.ArrayList> 中的每项强制转换为 `Student`。</span><span class="sxs-lookup"><span data-stu-id="c1ddb-107">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="c1ddb-108">在查询表达式中使用显式类型范围变量等效于调用 <xref:System.Linq.Enumerable.Cast%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c1ddb-108">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="c1ddb-109">如果无法执行指定的强制转换，<xref:System.Linq.Enumerable.Cast%2A> 将引发异常。</span><span class="sxs-lookup"><span data-stu-id="c1ddb-109"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="c1ddb-110"><xref:System.Linq.Enumerable.Cast%2A> 和 <xref:System.Linq.Enumerable.OfType%2A> 是两个标准查询运算符方法，可对非泛型 <xref:System.Collections.IEnumerable> 类型执行操作。</span><span class="sxs-lookup"><span data-stu-id="c1ddb-110"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="c1ddb-111">有关详细信息，请参阅 [LINQ 查询操作中的类型关系](./type-relationships-in-linq-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="c1ddb-111">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1ddb-112">示例</span><span class="sxs-lookup"><span data-stu-id="c1ddb-112">Example</span></span>  

 <span data-ttu-id="c1ddb-113">下面的示例演示对 <xref:System.Collections.ArrayList> 的简单查询。</span><span class="sxs-lookup"><span data-stu-id="c1ddb-113">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="c1ddb-114">请注意，本示例在代码调用 <xref:System.Collections.ArrayList.Add%2A> 方法时使用对象初始值设定项，但这不是必需的。</span><span class="sxs-lookup"><span data-stu-id="c1ddb-114">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using System.Linq;  
  
namespace NonGenericLINQ  
{  
    public class Student  
    {  
        public string FirstName { get; set; }  
        public string LastName { get; set; }  
        public int[] Scores { get; set; }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ArrayList arrList = new ArrayList();  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Svetlana", LastName = "Omelchenko", Scores = new int[] { 98, 92, 81, 60 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Claire", LastName = "O’Donnell", Scores = new int[] { 75, 84, 91, 39 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Sven", LastName = "Mortensen", Scores = new int[] { 88, 94, 65, 91 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Cesar", LastName = "Garcia", Scores = new int[] { 97, 89, 85, 82 }  
                    });  
  
            var query = from Student student in arrList  
                        where student.Scores[0] > 95  
                        select student;  
  
            foreach (Student s in query)  
                Console.WriteLine(s.LastName + ": " + s.Scores[0]);  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
}  
/* Output:
    Omelchenko: 98  
    Garcia: 97  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1ddb-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="c1ddb-115">See also</span></span>

- [<span data-ttu-id="c1ddb-116">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="c1ddb-116">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
