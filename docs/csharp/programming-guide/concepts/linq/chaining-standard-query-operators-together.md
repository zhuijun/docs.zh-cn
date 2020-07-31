---
title: 将标准查询运算符链接在一起 (C#)
description: 此示例演示使用 C# 也可以将标准查询运算符链接在一起。 查询不具体化中间结果。
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 41a7e4c7910c783d07181fe16254b0cac6902794
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104075"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="21546-104">将标准查询运算符链接在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="21546-104">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="21546-105">这是[教程：将查询链接在一起 (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) 教程中的最后一个主题。</span><span class="sxs-lookup"><span data-stu-id="21546-105">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="21546-106">标准查询运算符也可以链接在一起。</span><span class="sxs-lookup"><span data-stu-id="21546-106">The standard query operators can also be chained together.</span></span> <span data-ttu-id="21546-107">例如，您可以插入 <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 运算符，并且该运算符也可以以迟缓方式操作。</span><span class="sxs-lookup"><span data-stu-id="21546-107">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="21546-108">它不会具体化任何中间结果。</span><span class="sxs-lookup"><span data-stu-id="21546-108">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21546-109">示例</span><span class="sxs-lookup"><span data-stu-id="21546-109">Example</span></span>  
 <span data-ttu-id="21546-110">在此示例中，调用 <xref:System.Linq.Enumerable.Where%2A> 之前将调用 `ConvertCollectionToUpperCase` 方法。</span><span class="sxs-lookup"><span data-stu-id="21546-110">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="21546-111"><xref:System.Linq.Enumerable.Where%2A> 方法的操作方式与本教程前面示例中使用的迟缓方法 `ConvertCollectionToUpperCase` 和 `AppendString` 几乎完全相同。</span><span class="sxs-lookup"><span data-stu-id="21546-111">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="21546-112">区别之一是在本例中，<xref:System.Linq.Enumerable.Where%2A> 方法循环访问其源集合，确定第一项不传递谓词，然后获取传递谓词的下一项。</span><span class="sxs-lookup"><span data-stu-id="21546-112">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="21546-113">示例然后生成第二项。</span><span class="sxs-lookup"><span data-stu-id="21546-113">It then yields the second item.</span></span>  
  
 <span data-ttu-id="21546-114">但基本要旨是相同的：除非必要，否则不具体化中间集合。</span><span class="sxs-lookup"><span data-stu-id="21546-114">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="21546-115">在使用查询表达式时，会将查询表达式转换为对标准查询运算符的调用，这一原理同样适用。</span><span class="sxs-lookup"><span data-stu-id="21546-115">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="21546-116">本节中查询 Office Open XML 文档的所有示例都使用相同的原理。</span><span class="sxs-lookup"><span data-stu-id="21546-116">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="21546-117">延迟执行和迟缓计算是有效使用 LINQ（和 LINQ to XML）所必须理解的一些基础概念。</span><span class="sxs-lookup"><span data-stu-id="21546-117">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            where s.CompareTo("D") >= 0  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="21546-118">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="21546-118">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
