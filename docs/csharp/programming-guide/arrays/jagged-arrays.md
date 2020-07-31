---
title: 交错数组 - C# 编程指南
description: C# 中的交错数组是一个数组，其元素为不同维度和大小的数组。 了解如何声明、初始化和访问交错数组。
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 40da9fbda34aef4e69ebf2ae20485e883b79f871
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474678"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="64900-104">交错数组（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="64900-104">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="64900-105">交错数组是元素为数组的数组。</span><span class="sxs-lookup"><span data-stu-id="64900-105">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="64900-106">交错数组元素的维度和大小可以不同。</span><span class="sxs-lookup"><span data-stu-id="64900-106">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="64900-107">交错数组有时称为“数组的数组”。</span><span class="sxs-lookup"><span data-stu-id="64900-107">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="64900-108">以下示例说明如何声明、初始化和访问交错数组。</span><span class="sxs-lookup"><span data-stu-id="64900-108">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="64900-109">下面声明一个具有三个元素的一维数组，其中每个元素都是一维整数数组：</span><span class="sxs-lookup"><span data-stu-id="64900-109">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="64900-110">必须初始化 `jaggedArray` 的元素后才可使用它。</span><span class="sxs-lookup"><span data-stu-id="64900-110">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="64900-111">可按下方操作初始化元素：</span><span class="sxs-lookup"><span data-stu-id="64900-111">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="64900-112">每个元素都是一维整数数组。</span><span class="sxs-lookup"><span data-stu-id="64900-112">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="64900-113">第一个元素是由 5 个整数组成的数组，第二个是由 4 个整数组成的数组，而第三个是由 2 个整数组成的数组。</span><span class="sxs-lookup"><span data-stu-id="64900-113">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="64900-114">也可使用初始化表达式通过值来填充数组元素，这种情况下不需要数组大小。</span><span class="sxs-lookup"><span data-stu-id="64900-114">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="64900-115">例如：</span><span class="sxs-lookup"><span data-stu-id="64900-115">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="64900-116">还可在声明数组时将其初始化，如：</span><span class="sxs-lookup"><span data-stu-id="64900-116">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="64900-117">可以使用下面的缩写形式。</span><span class="sxs-lookup"><span data-stu-id="64900-117">You can use the following shorthand form.</span></span> <span data-ttu-id="64900-118">请注意：不能从元素初始化中省略 `new` 运算符，因为不存在元素的默认初始化：</span><span class="sxs-lookup"><span data-stu-id="64900-118">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="64900-119">交错数组是数组的数组，因此其元素为引用类型且被初始化为 `null`。</span><span class="sxs-lookup"><span data-stu-id="64900-119">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="64900-120">可以如下例所示访问个别数组元素：</span><span class="sxs-lookup"><span data-stu-id="64900-120">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="64900-121">可以混合使用交错数组和多维数组。</span><span class="sxs-lookup"><span data-stu-id="64900-121">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="64900-122">下面声明和初始化一个包含大小不同的三个二维数组元素的一维交错数组。</span><span class="sxs-lookup"><span data-stu-id="64900-122">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="64900-123">有关二维数组的详细信息，请参阅[多维数组](./multidimensional-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="64900-123">For more information about two-dimensional arrays, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="64900-124">可以如本例所示访问个别元素，示例显示第一个数组的元素 `[1,0]` 的值（值为 `5`）：</span><span class="sxs-lookup"><span data-stu-id="64900-124">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="64900-125">方法 `Length` 返回包含在交错数组中的数组的数目。</span><span class="sxs-lookup"><span data-stu-id="64900-125">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="64900-126">例如，假定已声明了前一个数组，则此行：</span><span class="sxs-lookup"><span data-stu-id="64900-126">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="64900-127">返回值 3。</span><span class="sxs-lookup"><span data-stu-id="64900-127">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64900-128">示例</span><span class="sxs-lookup"><span data-stu-id="64900-128">Example</span></span>

 <span data-ttu-id="64900-129">本例生成一个数组，该数组的元素为数组自身。</span><span class="sxs-lookup"><span data-stu-id="64900-129">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="64900-130">每一个数组元素都有不同的大小。</span><span class="sxs-lookup"><span data-stu-id="64900-130">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="64900-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="64900-131">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="64900-132">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="64900-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="64900-133">数组</span><span class="sxs-lookup"><span data-stu-id="64900-133">Arrays</span></span>](./index.md)
- [<span data-ttu-id="64900-134">一维数组</span><span class="sxs-lookup"><span data-stu-id="64900-134">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="64900-135">多维数组</span><span class="sxs-lookup"><span data-stu-id="64900-135">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
