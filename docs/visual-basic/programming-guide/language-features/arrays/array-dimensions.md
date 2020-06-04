---
title: 数组维度
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: f971f0c3693177adbcb8869d487e3ad41d49ddc2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413099"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="50f04-102">Array Dimensions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50f04-102">Array Dimensions in Visual Basic</span></span>

<span data-ttu-id="50f04-103">*维度*是可以改变数组元素规范的方向。</span><span class="sxs-lookup"><span data-stu-id="50f04-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="50f04-104">保存月份每一天的销售总额的数组有一个维度（月中的第几天）。</span><span class="sxs-lookup"><span data-stu-id="50f04-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="50f04-105">每个月的每一天都包含按部门列出的销售总额的数组有两个维度（部门号和月份日期）。</span><span class="sxs-lookup"><span data-stu-id="50f04-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="50f04-106">数组的维数称为 "*秩*"。</span><span class="sxs-lookup"><span data-stu-id="50f04-106">The number of dimensions an array has is called its *rank*.</span></span>

> [!NOTE]
> <span data-ttu-id="50f04-107">您可以使用 <xref:System.Array.Rank%2A> 属性来确定数组的维数。</span><span class="sxs-lookup"><span data-stu-id="50f04-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>

## <a name="working-with-dimensions"></a><span data-ttu-id="50f04-108">使用维度</span><span class="sxs-lookup"><span data-stu-id="50f04-108">Working with Dimensions</span></span>

<span data-ttu-id="50f04-109">您可以通过为数组的每个维度提供*索引*或*下标*来指定数组的元素。</span><span class="sxs-lookup"><span data-stu-id="50f04-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="50f04-110">元素是从索引0到该维度的最高索引的每个维度连续的。</span><span class="sxs-lookup"><span data-stu-id="50f04-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>

<span data-ttu-id="50f04-111">下图显示具有不同秩的数组的概念结构。</span><span class="sxs-lookup"><span data-stu-id="50f04-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="50f04-112">图中的每个元素都显示了访问它的索引值。</span><span class="sxs-lookup"><span data-stu-id="50f04-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="50f04-113">例如，您可以通过指定索引来访问二维数组的第二行的第一个元素 `(1, 0)` 。</span><span class="sxs-lookup"><span data-stu-id="50f04-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>

![显示一维数组的关系图。](./media/array-dimensions/one-dimensional-array.gif)

![显示二维数组的关系图。](./media/array-dimensions/two-dimensional-array.gif)

![显示三维数组的关系图。](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a><span data-ttu-id="50f04-117">一个维度</span><span class="sxs-lookup"><span data-stu-id="50f04-117">One Dimension</span></span>

<span data-ttu-id="50f04-118">许多数组只有一个维度，例如每个年龄段的人员数。</span><span class="sxs-lookup"><span data-stu-id="50f04-118">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="50f04-119">指定元素的唯一要求是该元素保留计数的期限。</span><span class="sxs-lookup"><span data-stu-id="50f04-119">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="50f04-120">因此，此类数组只使用一个索引。</span><span class="sxs-lookup"><span data-stu-id="50f04-120">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="50f04-121">下面的示例声明一个变量，用于保存 age 0 到120的*一维*期限计数。</span><span class="sxs-lookup"><span data-stu-id="50f04-121">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a><span data-ttu-id="50f04-122">两个维度</span><span class="sxs-lookup"><span data-stu-id="50f04-122">Two Dimensions</span></span>

<span data-ttu-id="50f04-123">某些阵列有两个维度，例如每个校园建筑的每个楼层的办公室数。</span><span class="sxs-lookup"><span data-stu-id="50f04-123">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="50f04-124">元素的规范要求生成号和楼层，每个元素都包含建筑物和地面的组合的计数。</span><span class="sxs-lookup"><span data-stu-id="50f04-124">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="50f04-125">因此，此类数组使用两个索引。</span><span class="sxs-lookup"><span data-stu-id="50f04-125">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="50f04-126">下面的示例声明一个变量，用于保存办公室计数的二维*数组*（即建筑物0到40，地面0到5）。</span><span class="sxs-lookup"><span data-stu-id="50f04-126">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>

```vb
Dim officeCounts(40, 5) As Byte
```

<span data-ttu-id="50f04-127">二维数组也称为*矩形数组*。</span><span class="sxs-lookup"><span data-stu-id="50f04-127">A two-dimensional array is also called a *rectangular array*.</span></span>

### <a name="three-dimensions"></a><span data-ttu-id="50f04-128">三个维度</span><span class="sxs-lookup"><span data-stu-id="50f04-128">Three Dimensions</span></span>

<span data-ttu-id="50f04-129">几个数组具有三个维度，如三维空间中的值。</span><span class="sxs-lookup"><span data-stu-id="50f04-129">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="50f04-130">此类数组使用三个索引，在此示例中，表示物理空间的 x、y 和 z 坐标。</span><span class="sxs-lookup"><span data-stu-id="50f04-130">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="50f04-131">下面的示例声明一个变量，以便在三维卷中的各个点上保存一*维*的空气温度。</span><span class="sxs-lookup"><span data-stu-id="50f04-131">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a><span data-ttu-id="50f04-132">超过三个维度</span><span class="sxs-lookup"><span data-stu-id="50f04-132">More than Three Dimensions</span></span>

<span data-ttu-id="50f04-133">尽管数组最多可以有32个维度，但这种情况很少超过三个。</span><span class="sxs-lookup"><span data-stu-id="50f04-133">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>

> [!NOTE]
> <span data-ttu-id="50f04-134">将维度添加到数组时，数组所需的总存储量会大幅增加，因此请谨慎使用多维数组。</span><span class="sxs-lookup"><span data-stu-id="50f04-134">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>

## <a name="using-different-dimensions"></a><span data-ttu-id="50f04-135">使用不同尺寸</span><span class="sxs-lookup"><span data-stu-id="50f04-135">Using Different Dimensions</span></span>

<span data-ttu-id="50f04-136">假设您想要跟踪当月每一天的销售总额。</span><span class="sxs-lookup"><span data-stu-id="50f04-136">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="50f04-137">您可以声明一个包含31个元素的一维数组，每个月对应一个元素，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="50f04-137">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>

```vb
Dim salesAmounts(30) As Double
```

<span data-ttu-id="50f04-138">现在，假设您想要跟踪每个月的每一天的相同信息，而不是一年中的每个月。</span><span class="sxs-lookup"><span data-stu-id="50f04-138">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="50f04-139">您可以声明一个二维数组，其中包含12个行（对于月份）和31个列（表示天数），如下例所示。</span><span class="sxs-lookup"><span data-stu-id="50f04-139">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>

```vb
Dim salesAmounts(11, 30) As Double
```

<span data-ttu-id="50f04-140">现在假设您决定让数组保存超过一年的信息。</span><span class="sxs-lookup"><span data-stu-id="50f04-140">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="50f04-141">如果要跟踪5年的销售额，则可以使用5个层、12行和31列声明一个三维数组，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="50f04-141">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>

```vb
Dim salesAmounts(4, 11, 30) As Double
```

<span data-ttu-id="50f04-142">请注意，由于每个索引的最大值均为0，因此，每个维度的 `salesAmounts` 被声明为小于该维度所需的长度。</span><span class="sxs-lookup"><span data-stu-id="50f04-142">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="50f04-143">另请注意，数组的大小随每个新维度的增加而增加。</span><span class="sxs-lookup"><span data-stu-id="50f04-143">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="50f04-144">上述示例中的三个大小分别为31、372和1860个元素。</span><span class="sxs-lookup"><span data-stu-id="50f04-144">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="50f04-145">无需使用 `Dim` 语句或子句即可创建数组 `New` 。</span><span class="sxs-lookup"><span data-stu-id="50f04-145">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="50f04-146">例如，您可以调用 <xref:System.Array.CreateInstance%2A> 方法，或其他组件可以通过此方式传递您的代码。</span><span class="sxs-lookup"><span data-stu-id="50f04-146">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="50f04-147">此类数组可以具有0以外的下限。</span><span class="sxs-lookup"><span data-stu-id="50f04-147">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="50f04-148">您始终可以通过使用方法或函数测试某个维度的下限 <xref:System.Array.GetLowerBound%2A> `LBound` 。</span><span class="sxs-lookup"><span data-stu-id="50f04-148">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="50f04-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50f04-149">See also</span></span>

- [<span data-ttu-id="50f04-150">数组</span><span class="sxs-lookup"><span data-stu-id="50f04-150">Arrays</span></span>](index.md)
- [<span data-ttu-id="50f04-151">数组疑难解答</span><span class="sxs-lookup"><span data-stu-id="50f04-151">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
