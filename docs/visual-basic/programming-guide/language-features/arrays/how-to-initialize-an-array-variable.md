---
title: 如何：初始化数组变量
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 7feaf71fa1c59c24aa751f2b9e28328d47ba357c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413061"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="e0bce-102">如何：在 Visual Basic 中初始化数组变量</span><span class="sxs-lookup"><span data-stu-id="e0bce-102">How to: Initialize an Array Variable in Visual Basic</span></span>
<span data-ttu-id="e0bce-103">通过在子句中包含数组文本 `New` 并指定数组的初始值来初始化数组变量。</span><span class="sxs-lookup"><span data-stu-id="e0bce-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="e0bce-104">可以指定类型，也可以允许从数组文本中的值推断。</span><span class="sxs-lookup"><span data-stu-id="e0bce-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="e0bce-105">有关如何推断类型的详细信息，请参阅[数组](index.md)中的 "使用初始值填充数组"。</span><span class="sxs-lookup"><span data-stu-id="e0bce-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="e0bce-106">使用数组文本初始化数组变量</span><span class="sxs-lookup"><span data-stu-id="e0bce-106">To initialize an array variable by using an array literal</span></span>  
  
- <span data-ttu-id="e0bce-107">在子句中 `New` 或在分配数组值时，在大括号（）中提供元素值 `{}` 。</span><span class="sxs-lookup"><span data-stu-id="e0bce-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="e0bce-108">下面的示例演示多个声明、创建和初始化一个变量以包含具有类型的元素的数组的方式 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="e0bce-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     <span data-ttu-id="e0bce-109">执行每个语句后，创建的数组的长度为3，索引0到索引2的元素包含初始值。</span><span class="sxs-lookup"><span data-stu-id="e0bce-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="e0bce-110">如果同时提供上限和值，则必须为从索引0到上限的每个元素包含一个值。</span><span class="sxs-lookup"><span data-stu-id="e0bce-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="e0bce-111">请注意，如果在数组文本中提供元素值，则无需指定索引上限。</span><span class="sxs-lookup"><span data-stu-id="e0bce-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="e0bce-112">如果未指定上限，则将根据数组文本中的值的数目推断数组的大小。</span><span class="sxs-lookup"><span data-stu-id="e0bce-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="e0bce-113">使用数组文本初始化多维数组变量</span><span class="sxs-lookup"><span data-stu-id="e0bce-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
- <span data-ttu-id="e0bce-114">将值嵌套在大括号内的大括号（ `{}` ）内。</span><span class="sxs-lookup"><span data-stu-id="e0bce-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="e0bce-115">确保嵌套的数组文本都推导为相同类型和长度的数组。</span><span class="sxs-lookup"><span data-stu-id="e0bce-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="e0bce-116">下面的代码示例演示了多维数组初始化的几个示例。</span><span class="sxs-lookup"><span data-stu-id="e0bce-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- <span data-ttu-id="e0bce-117">可以显式指定数组界限，或将其保留，让编译器根据数组文本中的值推断数组界限。</span><span class="sxs-lookup"><span data-stu-id="e0bce-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="e0bce-118">如果同时提供上限和值，则必须在每个维度的索引0到上限中包含每个元素的值。</span><span class="sxs-lookup"><span data-stu-id="e0bce-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="e0bce-119">下面的示例演示多个声明、创建和初始化一个变量以包含包含类型为的元素的二维数组的方法。`Short`</span><span class="sxs-lookup"><span data-stu-id="e0bce-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     <span data-ttu-id="e0bce-120">执行每个语句后，创建的数组包含六个具有索引、、、、和的已初始化元素 `(0,0)` `(0,1)` `(0,2)` `(1,0)` `(1,1)` `(1,2)` 。</span><span class="sxs-lookup"><span data-stu-id="e0bce-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="e0bce-121">每个数组位置都包含值 `10` 。</span><span class="sxs-lookup"><span data-stu-id="e0bce-121">Each array location contains the value `10`.</span></span>  
  
- <span data-ttu-id="e0bce-122">下面的示例循环访问一个多维数组。</span><span class="sxs-lookup"><span data-stu-id="e0bce-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="e0bce-123">在 Visual Basic 编写的 Windows 控制台应用程序中，将代码粘贴到方法中 `Sub Main()` 。</span><span class="sxs-lookup"><span data-stu-id="e0bce-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="e0bce-124">最后一个注释显示输出。</span><span class="sxs-lookup"><span data-stu-id="e0bce-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="e0bce-125">使用数组文本初始化交错数组变量</span><span class="sxs-lookup"><span data-stu-id="e0bce-125">To initialize a jagged array variable by using array literals</span></span>  
  
- <span data-ttu-id="e0bce-126">将对象值嵌套在大括号（ `{}` ）中。</span><span class="sxs-lookup"><span data-stu-id="e0bce-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="e0bce-127">尽管还可以嵌套指定不同长度数组的数组文本（对于交错数组），但请确保嵌套的数组文本括在括号（ `()` ）中。</span><span class="sxs-lookup"><span data-stu-id="e0bce-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="e0bce-128">圆括号会强制计算嵌套的数组文本，并将生成的数组用作交错数组的初始值。</span><span class="sxs-lookup"><span data-stu-id="e0bce-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="e0bce-129">下面的代码示例演示了交错数组初始化的两个示例。</span><span class="sxs-lookup"><span data-stu-id="e0bce-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- <span data-ttu-id="e0bce-130">下面的示例循环访问交错数组。</span><span class="sxs-lookup"><span data-stu-id="e0bce-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="e0bce-131">在 Visual Basic 编写的 Windows 控制台应用程序中，将代码粘贴到方法中 `Sub Main()` 。</span><span class="sxs-lookup"><span data-stu-id="e0bce-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="e0bce-132">代码中的最后一个注释显示输出。</span><span class="sxs-lookup"><span data-stu-id="e0bce-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="e0bce-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0bce-133">See also</span></span>

- [<span data-ttu-id="e0bce-134">数组</span><span class="sxs-lookup"><span data-stu-id="e0bce-134">Arrays</span></span>](index.md)
- [<span data-ttu-id="e0bce-135">数组疑难解答</span><span class="sxs-lookup"><span data-stu-id="e0bce-135">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
