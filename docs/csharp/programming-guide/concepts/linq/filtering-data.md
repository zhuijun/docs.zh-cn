---
title: 筛选数据 (C#)
description: 筛选（也称为选择）根据条件限制结果。 了解 C# 中的 LINQ 执行筛选的标准查询运算符方法。
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: f9f6d691da73b566e5135f6692c87ba3a8978005
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103924"
---
# <a name="filtering-data-c"></a><span data-ttu-id="d0dd8-104">筛选数据 (C#)</span><span class="sxs-lookup"><span data-stu-id="d0dd8-104">Filtering Data (C#)</span></span>
<span data-ttu-id="d0dd8-105">筛选是指将结果集限制为仅包含满足指定条件的元素的操作。</span><span class="sxs-lookup"><span data-stu-id="d0dd8-105">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="d0dd8-106">它也称为选定内容。</span><span class="sxs-lookup"><span data-stu-id="d0dd8-106">It is also known as selection.</span></span>  
  
 <span data-ttu-id="d0dd8-107">下图演示了对字符序列进行筛选的结果。</span><span class="sxs-lookup"><span data-stu-id="d0dd8-107">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="d0dd8-108">筛选操作的谓词指定字符必须为“A”。</span><span class="sxs-lookup"><span data-stu-id="d0dd8-108">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![显示 LINQ 筛选操作的图表](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="d0dd8-110">下面一节列出了执行所选内容的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="d0dd8-110">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0dd8-111">方法</span><span class="sxs-lookup"><span data-stu-id="d0dd8-111">Methods</span></span>  
  
|<span data-ttu-id="d0dd8-112">方法名</span><span class="sxs-lookup"><span data-stu-id="d0dd8-112">Method Name</span></span>|<span data-ttu-id="d0dd8-113">描述</span><span class="sxs-lookup"><span data-stu-id="d0dd8-113">Description</span></span>|<span data-ttu-id="d0dd8-114">C# 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="d0dd8-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="d0dd8-115">详细信息</span><span class="sxs-lookup"><span data-stu-id="d0dd8-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d0dd8-116">OfType</span><span class="sxs-lookup"><span data-stu-id="d0dd8-116">OfType</span></span>|<span data-ttu-id="d0dd8-117">根据其转换为特定类型的能力选择值。</span><span class="sxs-lookup"><span data-stu-id="d0dd8-117">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="d0dd8-118">不适用。</span><span class="sxs-lookup"><span data-stu-id="d0dd8-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0dd8-119">Where</span><span class="sxs-lookup"><span data-stu-id="d0dd8-119">Where</span></span>|<span data-ttu-id="d0dd8-120">选择基于谓词函数的值。</span><span class="sxs-lookup"><span data-stu-id="d0dd8-120">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="d0dd8-121">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="d0dd8-121">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="d0dd8-122">以下示例使用 `where` 子句从数组中筛选具有特定长度的字符串。</span><span class="sxs-lookup"><span data-stu-id="d0dd8-122">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0dd8-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="d0dd8-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="d0dd8-124">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="d0dd8-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="d0dd8-125">where 子句</span><span class="sxs-lookup"><span data-stu-id="d0dd8-125">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="d0dd8-126">在运行时动态指定谓词筛选器</span><span class="sxs-lookup"><span data-stu-id="d0dd8-126">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="d0dd8-127">如何使用反射查询程序集的元数据 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d0dd8-127">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="d0dd8-128">如何查询具有指定特性或名称的文件 (C#)</span><span class="sxs-lookup"><span data-stu-id="d0dd8-128">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="d0dd8-129">如何按任意词或字段对文本数据进行排序或筛选 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d0dd8-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
