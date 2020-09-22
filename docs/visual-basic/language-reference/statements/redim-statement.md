---
title: ReDim 语句
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: 17bc806f2e92c61f1dd7425de40b1a68f926a583
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872023"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="d6957-102">ReDim 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6957-102">ReDim Statement (Visual Basic)</span></span>

<span data-ttu-id="d6957-103">为数组变量重新分配存储空间。</span><span class="sxs-lookup"><span data-stu-id="d6957-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6957-104">语法</span><span class="sxs-lookup"><span data-stu-id="d6957-104">Syntax</span></span>  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d6957-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="d6957-105">Parts</span></span>  
  
|<span data-ttu-id="d6957-106">术语</span><span class="sxs-lookup"><span data-stu-id="d6957-106">Term</span></span>|<span data-ttu-id="d6957-107">定义</span><span class="sxs-lookup"><span data-stu-id="d6957-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="d6957-108">可选。</span><span class="sxs-lookup"><span data-stu-id="d6957-108">Optional.</span></span> <span data-ttu-id="d6957-109">修饰符，当仅更改最后一个维度的大小时，用来保留现有数组中的数据。</span><span class="sxs-lookup"><span data-stu-id="d6957-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="d6957-110">必需。</span><span class="sxs-lookup"><span data-stu-id="d6957-110">Required.</span></span> <span data-ttu-id="d6957-111">数组变量的名称。</span><span class="sxs-lookup"><span data-stu-id="d6957-111">Name of the array variable.</span></span> <span data-ttu-id="d6957-112">请参阅 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="d6957-112">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="d6957-113">必需。</span><span class="sxs-lookup"><span data-stu-id="d6957-113">Required.</span></span> <span data-ttu-id="d6957-114">列出重新定义的数组各个维度的边界。</span><span class="sxs-lookup"><span data-stu-id="d6957-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6957-115">备注</span><span class="sxs-lookup"><span data-stu-id="d6957-115">Remarks</span></span>  

 <span data-ttu-id="d6957-116">可以使用 `ReDim` 语句来更改某个已声明数组的一个或多个维度的大小。</span><span class="sxs-lookup"><span data-stu-id="d6957-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="d6957-117">如果数组较大，并且你不再需要它的某些元素，`ReDim`可通过减少数组大小来释放内存。</span><span class="sxs-lookup"><span data-stu-id="d6957-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="d6957-118">另一方面，如果数组需要更多元素，也可使用 `ReDim` 进行添加。</span><span class="sxs-lookup"><span data-stu-id="d6957-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="d6957-119">`ReDim` 语句仅供数组使用。</span><span class="sxs-lookup"><span data-stu-id="d6957-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="d6957-120">它对标量（仅包含单个值的变量）、集合或结构无效。</span><span class="sxs-lookup"><span data-stu-id="d6957-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="d6957-121">请注意，如果将变量声明为 `Array` 类型，则 `ReDim` 语句将没有足够的类型信息来创建新数组。</span><span class="sxs-lookup"><span data-stu-id="d6957-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="d6957-122">仅可在过程级别使用 `ReDim` 。</span><span class="sxs-lookup"><span data-stu-id="d6957-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="d6957-123">因此，变量的声明上下文必须是过程；而不能是源文件、命名空间、接口、类、结构、模块或块。</span><span class="sxs-lookup"><span data-stu-id="d6957-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="d6957-124">有关详细信息，请参阅[声明上下文和默认访问级别](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d6957-124">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d6957-125">规则</span><span class="sxs-lookup"><span data-stu-id="d6957-125">Rules</span></span>  
  
- <span data-ttu-id="d6957-126">**多个变量。**</span><span class="sxs-lookup"><span data-stu-id="d6957-126">**Multiple Variables.**</span></span> <span data-ttu-id="d6957-127">可以在同一声明语句中调整多个数组变量的大小， `name` 并 `boundlist` 为每个变量指定和部分。</span><span class="sxs-lookup"><span data-stu-id="d6957-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="d6957-128">以逗号分隔多个变量。</span><span class="sxs-lookup"><span data-stu-id="d6957-128">Multiple variables are separated by commas.</span></span>  
  
- <span data-ttu-id="d6957-129">**数组界限。**</span><span class="sxs-lookup"><span data-stu-id="d6957-129">**Array Bounds.**</span></span> <span data-ttu-id="d6957-130">中的每个条目 `boundlist` 都可以指定该维度的下限和上限。</span><span class="sxs-lookup"><span data-stu-id="d6957-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="d6957-131">下边界始终为 0（零）。</span><span class="sxs-lookup"><span data-stu-id="d6957-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="d6957-132">上边界是该维度可能的最大索引值，而不是维度的长度（即上边界加 1）。</span><span class="sxs-lookup"><span data-stu-id="d6957-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="d6957-133">每个维度的索引都可能在 0 到其上边界值之间变动。</span><span class="sxs-lookup"><span data-stu-id="d6957-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="d6957-134">`boundlist` 中的维数必须与数组的原始维数（秩）相匹配。</span><span class="sxs-lookup"><span data-stu-id="d6957-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
- <span data-ttu-id="d6957-135">**数据类型。**</span><span class="sxs-lookup"><span data-stu-id="d6957-135">**Data Types.**</span></span> <span data-ttu-id="d6957-136">`ReDim`语句无法更改数组变量或其元素的数据类型。</span><span class="sxs-lookup"><span data-stu-id="d6957-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
- <span data-ttu-id="d6957-137">**起始.**</span><span class="sxs-lookup"><span data-stu-id="d6957-137">**Initialization.**</span></span> <span data-ttu-id="d6957-138">`ReDim`语句不能为数组元素提供新的初始化值。</span><span class="sxs-lookup"><span data-stu-id="d6957-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
- <span data-ttu-id="d6957-139">**级别.**</span><span class="sxs-lookup"><span data-stu-id="d6957-139">**Rank.**</span></span> <span data-ttu-id="d6957-140">`ReDim` 语句无法更改数组的秩（维数）。</span><span class="sxs-lookup"><span data-stu-id="d6957-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
- <span data-ttu-id="d6957-141">**使用 Preserve 重设大小。**</span><span class="sxs-lookup"><span data-stu-id="d6957-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="d6957-142">如果使用 `Preserve` ，则只能调整数组最后一个维度的大小。</span><span class="sxs-lookup"><span data-stu-id="d6957-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="d6957-143">对于其他每个维度，必须指定现有数组的边界。</span><span class="sxs-lookup"><span data-stu-id="d6957-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="d6957-144">例如，如果数组只有一个维度，则可以重设该维度的大小并依然保留数组的所有内容，因为你更改的是最后一个也是唯一的维度。</span><span class="sxs-lookup"><span data-stu-id="d6957-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="d6957-145">但是，如果数组具有两个或更多维度，则使用 `Preserve` 只能重设最后一个维度的大小。</span><span class="sxs-lookup"><span data-stu-id="d6957-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
- <span data-ttu-id="d6957-146">**属性.**</span><span class="sxs-lookup"><span data-stu-id="d6957-146">**Properties.**</span></span> <span data-ttu-id="d6957-147">可以 `ReDim` 在保存值数组的属性上使用。</span><span class="sxs-lookup"><span data-stu-id="d6957-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="d6957-148">行为</span><span class="sxs-lookup"><span data-stu-id="d6957-148">Behavior</span></span>  
  
- <span data-ttu-id="d6957-149">**数组替换。**</span><span class="sxs-lookup"><span data-stu-id="d6957-149">**Array Replacement.**</span></span> <span data-ttu-id="d6957-150">`ReDim` 释放现有数组，并创建一个具有相同秩的新数组。</span><span class="sxs-lookup"><span data-stu-id="d6957-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="d6957-151">新数组将替换数组变量中已释放的数组。</span><span class="sxs-lookup"><span data-stu-id="d6957-151">The new array replaces the released array in the array variable.</span></span>  
  
- <span data-ttu-id="d6957-152">**在不使用 Preserve 的情况下初始化。**</span><span class="sxs-lookup"><span data-stu-id="d6957-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="d6957-153">如果不指定，则 `Preserve` `ReDim` 通过使用其数据类型的默认值来初始化新数组的元素。</span><span class="sxs-lookup"><span data-stu-id="d6957-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
- <span data-ttu-id="d6957-154">**使用 Preserve 初始化。**</span><span class="sxs-lookup"><span data-stu-id="d6957-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="d6957-155">如果指定 `Preserve` ，则 Visual Basic 会将元素从现有数组复制到新数组。</span><span class="sxs-lookup"><span data-stu-id="d6957-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6957-156">示例</span><span class="sxs-lookup"><span data-stu-id="d6957-156">Example</span></span>  

 <span data-ttu-id="d6957-157">下面的示例将增加某个动态数组最后一个维度的大小（不会丢失数组中的任何现有数据），然后减小该大小（会有部分数据丢失）。</span><span class="sxs-lookup"><span data-stu-id="d6957-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="d6957-158">最后，它会将大小重新减小到其原始值，并重新初始化所有数组元素。</span><span class="sxs-lookup"><span data-stu-id="d6957-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="d6957-159">`Dim` 语句创建具有三个维度的新数组。</span><span class="sxs-lookup"><span data-stu-id="d6957-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="d6957-160">为每个维度声明的边界为 10，因此每个维度的数组索引的范围介于 0 到 10 之间。</span><span class="sxs-lookup"><span data-stu-id="d6957-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="d6957-161">在下面的讨论中，三个维度分别被称为层、行和列。</span><span class="sxs-lookup"><span data-stu-id="d6957-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="d6957-162">第一个 `ReDim` 创建一个新数组，该数组将替换变量 `intArray` 中的现有数组。</span><span class="sxs-lookup"><span data-stu-id="d6957-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="d6957-163">`ReDim` 将所有元素从现有数组复制到新数组中。</span><span class="sxs-lookup"><span data-stu-id="d6957-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="d6957-164">它还向每一层中每一行的末尾添加 10 列，并将这些新列中的元素初始化为 0（数组的元素类型 `Integer` 的默认值）。</span><span class="sxs-lookup"><span data-stu-id="d6957-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="d6957-165">第二个 `ReDim` 创建另一个新数组并复制所有适合的元素。</span><span class="sxs-lookup"><span data-stu-id="d6957-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="d6957-166">但是，每一层的每一行的末尾丢失了 5 列。</span><span class="sxs-lookup"><span data-stu-id="d6957-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="d6957-167">如果不再使用这些列，这不是问题。</span><span class="sxs-lookup"><span data-stu-id="d6957-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="d6957-168">减小大型数组的大小可以释放不再需要的内存。</span><span class="sxs-lookup"><span data-stu-id="d6957-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="d6957-169">第三个 `ReDim` 创建另一个新数组，同时从每一层中每一行的末尾删除另外 5 列。</span><span class="sxs-lookup"><span data-stu-id="d6957-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="d6957-170">这一次它不会复制任何现有元素。</span><span class="sxs-lookup"><span data-stu-id="d6957-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="d6957-171">此语句将数组恢复为其原始大小。</span><span class="sxs-lookup"><span data-stu-id="d6957-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="d6957-172">由于该语句不包括 `Preserve` 修饰符，因此它将所有数组元素设置为其原始默认值。</span><span class="sxs-lookup"><span data-stu-id="d6957-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="d6957-173">有关其他示例，请参阅 [数组](../../programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d6957-173">For additional examples, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6957-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6957-174">See also</span></span>

- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="d6957-175">Const 语句</span><span class="sxs-lookup"><span data-stu-id="d6957-175">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="d6957-176">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="d6957-176">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="d6957-177">Erase 语句</span><span class="sxs-lookup"><span data-stu-id="d6957-177">Erase Statement</span></span>](erase-statement.md)
- [<span data-ttu-id="d6957-178">没</span><span class="sxs-lookup"><span data-stu-id="d6957-178">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="d6957-179">数组</span><span class="sxs-lookup"><span data-stu-id="d6957-179">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
