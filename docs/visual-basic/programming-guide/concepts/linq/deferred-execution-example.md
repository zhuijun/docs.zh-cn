---
title: 延迟执行示例
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 863b018b6047d61f6fb4a5c1ac68151ed69d24a1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410794"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="f78ad-102">延迟执行示例（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f78ad-102">Deferred Execution Example (Visual Basic)</span></span>

<span data-ttu-id="f78ad-103">本主题演示延迟执行和迟缓计算如何影响 LINQ to XML 查询的执行。</span><span class="sxs-lookup"><span data-stu-id="f78ad-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example"></a><span data-ttu-id="f78ad-104">示例</span><span class="sxs-lookup"><span data-stu-id="f78ad-104">Example</span></span>

<span data-ttu-id="f78ad-105">下面的示例演示使用采用延迟执行的扩展方法时的执行顺序。</span><span class="sxs-lookup"><span data-stu-id="f78ad-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="f78ad-106">此示例声明一个由三个字符串组成的数组。</span><span class="sxs-lookup"><span data-stu-id="f78ad-106">The example declares an array of three strings.</span></span> <span data-ttu-id="f78ad-107">然后，循环访问 `ConvertCollectionToUpperCase` 所返回的集合。</span><span class="sxs-lookup"><span data-stu-id="f78ad-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module Module1

    <Extension()>
    Private Iterator Function ConvertCollectionToUpperCase(
    ByVal source As IEnumerable(Of String)) _
    As IEnumerable(Of String)
        For Each str As String In source
            Console.WriteLine("ToUpper: source {0}", str)
            Yield str.ToUpper()
        Next
    End Function

    Sub Main()
        Dim stringArray = New String() {"abc", "def", "ghi"}

        Dim q = From str In stringArray.ConvertCollectionToUpperCase()
                Select str

        For Each Str As String In q
            Console.WriteLine("Main: str {0}", Str)
        Next
    End Sub

End Module
```

<span data-ttu-id="f78ad-108">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="f78ad-108">This example produces the following output:</span></span>

```console
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="f78ad-109">请注意，在循环访问 `ConvertCollectionToUpperCase` 所返回的集合时，每一项都从源字符串数组检索，并且在源字符串数组中检索下一项之前，被转换为大写形式。</span><span class="sxs-lookup"><span data-stu-id="f78ad-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="f78ad-110">可以看到，在 `foreach` 的 `Main` 循环中处理所返回集合的每一项之后，字符串数组才会完全转换为大写形式。</span><span class="sxs-lookup"><span data-stu-id="f78ad-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f78ad-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f78ad-111">See also</span></span>

- [<span data-ttu-id="f78ad-112">教程：延迟执行（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f78ad-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](tutorial-deferred-execution.md)
