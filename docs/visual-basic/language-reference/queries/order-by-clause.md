---
title: Order By 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 05fa720237f4b0185b5c07217362c99b5dbf4303
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869786"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="c43bd-102">Order By 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c43bd-102">Order By Clause (Visual Basic)</span></span>

<span data-ttu-id="c43bd-103">指定查询结果的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c43bd-104">语法</span><span class="sxs-lookup"><span data-stu-id="c43bd-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="c43bd-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="c43bd-105">Parts</span></span>  

 `orderExp1`  
 <span data-ttu-id="c43bd-106">必需。</span><span class="sxs-lookup"><span data-stu-id="c43bd-106">Required.</span></span> <span data-ttu-id="c43bd-107">当前查询结果中的一个或多个字段，用于确定如何对返回的值进行排序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="c43bd-108">字段名称必须用逗号分隔 (，) 。</span><span class="sxs-lookup"><span data-stu-id="c43bd-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="c43bd-109">您可以使用或关键字，将每个字段标识为按升序或降序排序 `Ascending` `Descending` 。</span><span class="sxs-lookup"><span data-stu-id="c43bd-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="c43bd-110">如果未 `Ascending` `Descending` 指定 or 关键字，则默认排序顺序为升序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="c43bd-111">排序顺序字段的优先级从左到右。</span><span class="sxs-lookup"><span data-stu-id="c43bd-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c43bd-112">备注</span><span class="sxs-lookup"><span data-stu-id="c43bd-112">Remarks</span></span>  

 <span data-ttu-id="c43bd-113">您可以使用 `Order By` 子句对查询结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="c43bd-114">`Order By`子句只能根据当前作用域的范围变量对结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="c43bd-115">例如， `Select` 子句在查询表达式中引入了新的作用域，该作用域具有新的迭代变量。</span><span class="sxs-lookup"><span data-stu-id="c43bd-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="c43bd-116">在查询中的子句之前定义的范围变量在 `Select` 子句之后不可用 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="c43bd-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="c43bd-117">因此，如果要按子句中不提供的字段对结果进行排序 `Select` ，则必须将子句放在 `Order By` `Select` 子句之前。</span><span class="sxs-lookup"><span data-stu-id="c43bd-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="c43bd-118">需要执行此操作的一个示例是，如果要按不作为结果的一部分返回的字段对查询进行排序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="c43bd-119">字段的升序和降序由接口的数据类型的实现确定 <xref:System.IComparable> 。</span><span class="sxs-lookup"><span data-stu-id="c43bd-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="c43bd-120">如果数据类型未实现 <xref:System.IComparable> 接口，则忽略排序顺序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c43bd-121">示例</span><span class="sxs-lookup"><span data-stu-id="c43bd-121">Example</span></span>  

 <span data-ttu-id="c43bd-122">下面的查询表达式使用 `From` 子句为集合声明范围变量 `book` `books` 。</span><span class="sxs-lookup"><span data-stu-id="c43bd-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="c43bd-123">`Order By`子句按照默认)  (按升序对查询结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="c43bd-124">价格相同的书籍按标题的升序排序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="c43bd-125">`Select`子句选择 `Title` 和 `Price` 属性作为查询返回的值。</span><span class="sxs-lookup"><span data-stu-id="c43bd-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="c43bd-126">示例</span><span class="sxs-lookup"><span data-stu-id="c43bd-126">Example</span></span>  

 <span data-ttu-id="c43bd-127">下面的查询表达式使用 `Order By` 子句按照价格以降序对查询结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="c43bd-128">价格相同的书籍按标题的升序排序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="c43bd-129">示例</span><span class="sxs-lookup"><span data-stu-id="c43bd-129">Example</span></span>  

 <span data-ttu-id="c43bd-130">下面的查询表达式使用 `Select` 子句来选择书名、价格、发布日期和作者。</span><span class="sxs-lookup"><span data-stu-id="c43bd-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="c43bd-131">然后，它将 `Title` 填充 `Price` `PublishDate` 新范围的范围变量的、、和 `Author` 字段。</span><span class="sxs-lookup"><span data-stu-id="c43bd-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="c43bd-132">`Order By`子句按作者姓名、书籍标题和价格对新范围变量进行排序。</span><span class="sxs-lookup"><span data-stu-id="c43bd-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="c43bd-133">每列按默认顺序排序 (升序) 。</span><span class="sxs-lookup"><span data-stu-id="c43bd-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="c43bd-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c43bd-134">See also</span></span>

- [<span data-ttu-id="c43bd-135">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="c43bd-135">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c43bd-136">查询</span><span class="sxs-lookup"><span data-stu-id="c43bd-136">Queries</span></span>](index.md)
- [<span data-ttu-id="c43bd-137">Select 子句</span><span class="sxs-lookup"><span data-stu-id="c43bd-137">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="c43bd-138">From 子句</span><span class="sxs-lookup"><span data-stu-id="c43bd-138">From Clause</span></span>](from-clause.md)
