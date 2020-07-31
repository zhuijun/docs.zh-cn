---
title: 如何在查询中返回元素属性的子集 - C# 编程指南
description: 了解如何在以 C# 编写的查询表达式中使用匿名类型，以返回每个源元素的某些属性。
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 882d94bc82527c14bd6c038f4bf574c2211b9089
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864366"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="9b85d-103">如何在查询中返回元素属性的子集（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="9b85d-103">How to return subsets of element properties in a query (C# Programming Guide)</span></span>
<span data-ttu-id="9b85d-104">当下列两个条件都满足时，可在查询表达式中使用匿名类型：</span><span class="sxs-lookup"><span data-stu-id="9b85d-104">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="9b85d-105">只想返回每个源元素的某些属性。</span><span class="sxs-lookup"><span data-stu-id="9b85d-105">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="9b85d-106">无需在执行查询的方法的范围之外存储查询结果。</span><span class="sxs-lookup"><span data-stu-id="9b85d-106">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="9b85d-107">如果只想从每个源元素中返回一个属性或字段，则只需在 `select` 子句中使用点运算符。</span><span class="sxs-lookup"><span data-stu-id="9b85d-107">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="9b85d-108">例如，若要只返回每个 `student` 的 `ID`，可以按如下方式编写 `select` 子句：</span><span class="sxs-lookup"><span data-stu-id="9b85d-108">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="9b85d-109">示例</span><span class="sxs-lookup"><span data-stu-id="9b85d-109">Example</span></span>  
 <span data-ttu-id="9b85d-110">下面的示例演示如何使用匿名类型只返回每个源元素的符合指定条件的属性子集。</span><span class="sxs-lookup"><span data-stu-id="9b85d-110">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="9b85d-111">请注意，如果未指定名称，匿名类型会使用源元素的名称作为其属性名称。</span><span class="sxs-lookup"><span data-stu-id="9b85d-111">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="9b85d-112">若要为匿名类型中的属性指定新名称，请按如下方式编写 `select` 语句：</span><span class="sxs-lookup"><span data-stu-id="9b85d-112">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="9b85d-113">如果在上一个示例中这样做，则 `Console.WriteLine` 语句也必须更改：</span><span class="sxs-lookup"><span data-stu-id="9b85d-113">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b85d-114">编译代码</span><span class="sxs-lookup"><span data-stu-id="9b85d-114">Compiling the Code</span></span>  
  
<span data-ttu-id="9b85d-115">要运行此代码，请使用 System.Linq 的 `using` 指令将该类复制并粘贴到 C# 控制台应用程序中。</span><span class="sxs-lookup"><span data-stu-id="9b85d-115">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9b85d-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="9b85d-116">See also</span></span>

- [<span data-ttu-id="9b85d-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="9b85d-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9b85d-118">匿名类型</span><span class="sxs-lookup"><span data-stu-id="9b85d-118">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="9b85d-119">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="9b85d-119">LINQ in C#</span></span>](../../linq/index.md)
