---
title: 将数组作为参数传递 - C# 编程指南
description: C# 中的数组可以作为实参传递给方法形参。 由于数组是引用类型，因此方法可以更改元素的值。
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 68f174421e56e2cf082fe670f93c4f6627d7c17b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474626"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="f6fc8-104">将数组作为参数传递（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="f6fc8-104">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="f6fc8-105">数组可以作为实参传递给方法形参。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-105">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="f6fc8-106">由于数组是引用类型，因此方法可以更改元素的值。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-106">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="f6fc8-107">将一维数组作为参数传递</span><span class="sxs-lookup"><span data-stu-id="f6fc8-107">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="f6fc8-108">可将初始化的一维数组传递给方法。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-108">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="f6fc8-109">例如，下列语句将一个数组发送给了 Print 方法。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-109">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="f6fc8-110">下面的代码演示 Print 方法的部分实现。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-110">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="f6fc8-111">可在同一步骤中初始化并传递新数组，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-111">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="f6fc8-112">示例</span><span class="sxs-lookup"><span data-stu-id="f6fc8-112">Example</span></span>

<span data-ttu-id="f6fc8-113">在下面的示例中，先初始化一个字符串数组，然后将其作为参数传递给字符串的 `DisplayArray` 方法。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-113">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="f6fc8-114">该方法将显示数组的元素。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-114">The method displays the elements of the array.</span></span> <span data-ttu-id="f6fc8-115">接下来，`ChangeArray` 方法会反转数组元素，然后由 `ChangeArrayElements` 方法修改该数组的前三个元素。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-115">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="f6fc8-116">每个方法返回后，`DisplayArray` 方法会显示按值传递数组不会阻止对数组元素的更改。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-116">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="f6fc8-117">将多维数组作为参数传递</span><span class="sxs-lookup"><span data-stu-id="f6fc8-117">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="f6fc8-118">通过与传递一维数组相同的方式，向方法传递初始化的多维数组。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-118">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="f6fc8-119">下列代码演示了 Print 方法的部分声明（该方法接受将二维数组作为其参数）。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-119">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="f6fc8-120">可在一个步骤中初始化并传递新数组，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="f6fc8-120">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="f6fc8-121">示例</span><span class="sxs-lookup"><span data-stu-id="f6fc8-121">Example</span></span>

<span data-ttu-id="f6fc8-122">在下列示例中，初始化一个整数的二维数组，并将其传递至 `Print2DArray` 方法。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="f6fc8-123">该方法将显示数组的元素。</span><span class="sxs-lookup"><span data-stu-id="f6fc8-123">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="f6fc8-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="f6fc8-124">See also</span></span>

- [<span data-ttu-id="f6fc8-125">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="f6fc8-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f6fc8-126">数组</span><span class="sxs-lookup"><span data-stu-id="f6fc8-126">Arrays</span></span>](index.md)
- [<span data-ttu-id="f6fc8-127">一维数组</span><span class="sxs-lookup"><span data-stu-id="f6fc8-127">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="f6fc8-128">多维数组</span><span class="sxs-lookup"><span data-stu-id="f6fc8-128">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="f6fc8-129">交错数组</span><span class="sxs-lookup"><span data-stu-id="f6fc8-129">Jagged Arrays</span></span>](jagged-arrays.md)
