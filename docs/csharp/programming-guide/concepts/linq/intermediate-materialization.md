---
title: 中间具体化 (C#)
description: 此 C# 示例显示了中间具体化，其中查询使 AppendString 在生成第一项之前枚举其整个源。
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 30951aaeea261efbd414205bcc54b63106324344
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165720"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="6b2ed-103">中间具体化 (C#)</span><span class="sxs-lookup"><span data-stu-id="6b2ed-103">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="6b2ed-104">有时，稍不小心就会导致查询中的集合过早具体化，从而显著改变应用程序的内存和性能配置文件。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-104">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="6b2ed-105">有些标准查询运算符会在生成单个元素之前导致其源集合具体化。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-105">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="6b2ed-106">例如，<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> 首先循环访问其整个源集合，然后对所有项排序，最后生成第一项。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-106">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="6b2ed-107">这意味着获取排序集合中的第一项需要高开销；其后的每一项不需要高开销。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-107">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="6b2ed-108">这样做很有意义：该查询运算符将不可能以其他方式操作。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-108">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b2ed-109">示例</span><span class="sxs-lookup"><span data-stu-id="6b2ed-109">Example</span></span>  
 <span data-ttu-id="6b2ed-110">本示例改自上一示例。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-110">This example alters the previous example.</span></span> <span data-ttu-id="6b2ed-111">`AppendString` 方法在循环访问源之前调用 <xref:System.Linq.Enumerable.ToList%2A>。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-111">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="6b2ed-112">这将导致具体化。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-112">This causes materialization.</span></span>  
  
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
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
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
  
 <span data-ttu-id="6b2ed-113">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="6b2ed-113">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 <span data-ttu-id="6b2ed-114">在此示例中，您可以看到，对 <xref:System.Linq.Enumerable.ToList%2A> 的调用会导致 `AppendString` 生成第一项之前枚举其整个源。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-114">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="6b2ed-115">如果源是一个大数组，这将显著改变应用程序的内存配置文件。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-115">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="6b2ed-116">标准查询运算符也可以链接在一起。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-116">Standard query operators can also be chained together.</span></span> <span data-ttu-id="6b2ed-117">本教程的最后一个主题将对此进行说明。</span><span class="sxs-lookup"><span data-stu-id="6b2ed-117">The final topic in this tutorial illustrates this.</span></span>  
  
- [<span data-ttu-id="6b2ed-118">将标准查询运算符链接在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="6b2ed-118">Chaining Standard Query Operators Together (C#)</span></span>](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b2ed-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="6b2ed-119">See also</span></span>

- [<span data-ttu-id="6b2ed-120">教程：将查询链接在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="6b2ed-120">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
