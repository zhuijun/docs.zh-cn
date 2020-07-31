---
title: 一维数组 - C# 编程指南
description: 使用 C# 中的 new 运算符创建一维数组，该运算符指定数组元素类型和元素数目。
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: ada01262d57cbfebc8bfa1a5fee0639a10db5a4b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474587"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="2da13-103">一维数组（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="2da13-103">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="2da13-104">使用 [new](../../language-reference/operators/new-operator.md) 运算符创建一维数组，该运算符指定数组元素类型和元素数目。</span><span class="sxs-lookup"><span data-stu-id="2da13-104">You create a single-dimensional array using the [new](../../language-reference/operators/new-operator.md) operator specifying the array element type and the number of elements.</span></span> <span data-ttu-id="2da13-105">以下示例声明一个包含五个整数的数组：</span><span class="sxs-lookup"><span data-stu-id="2da13-105">The following example declares an array of five integers:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

<span data-ttu-id="2da13-106">此数组包含从 `array[0]` 到 `array[4]` 的元素。</span><span class="sxs-lookup"><span data-stu-id="2da13-106">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="2da13-107">数组元素将初始化为元素类型的默认值，`0` 代表整数。</span><span class="sxs-lookup"><span data-stu-id="2da13-107">The elements of the array are initialized to the default value of the element type, `0` for integers.</span></span>

<span data-ttu-id="2da13-108">数组可以存储指定的任何元素类型，如声明字符串数组的下例所示：</span><span class="sxs-lookup"><span data-stu-id="2da13-108">Arrays can store any element type you specify, such as the following example that declares an array of strings:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a><span data-ttu-id="2da13-109">数组初始化</span><span class="sxs-lookup"><span data-stu-id="2da13-109">Array Initialization</span></span>

<span data-ttu-id="2da13-110">可以在声明数组时初始化数组的元素。</span><span class="sxs-lookup"><span data-stu-id="2da13-110">You can initialize the elements of an array when you declare the array.</span></span> <span data-ttu-id="2da13-111">不需要长度说明符，因为可以根据初始化列表中的元素数量推断得出。</span><span class="sxs-lookup"><span data-stu-id="2da13-111">The length specifier isn't needed because it's inferred by the number of elements in the initialization list.</span></span> <span data-ttu-id="2da13-112">例如：</span><span class="sxs-lookup"><span data-stu-id="2da13-112">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

<span data-ttu-id="2da13-113">下面的代码显示一个字符串数组的声明，其中每个数组元素都由一天的名称初始化：</span><span class="sxs-lookup"><span data-stu-id="2da13-113">The following code shows a declaration of a string array where each array element is initialized by a name of a day:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
<span data-ttu-id="2da13-114">在声明时初始化数组时，可以避免使用 `new` 表达式和数组类型，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="2da13-114">You can avoid the `new` expression and the array type when you initialize an array upon declaration, as shown in the following code.</span></span> <span data-ttu-id="2da13-115">这称为[隐式类型化数组](implicitly-typed-arrays.md)：</span><span class="sxs-lookup"><span data-stu-id="2da13-115">This is called an [implicitly typed array](implicitly-typed-arrays.md):</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

<span data-ttu-id="2da13-116">可以在尚未创建数组变量的情况下声明数组变量，但必须使用 `new` 运算符向此变量分配新数组。</span><span class="sxs-lookup"><span data-stu-id="2da13-116">You can declare an array variable without creating it, but you must use the `new` operator when you assign a new array to this variable.</span></span> <span data-ttu-id="2da13-117">例如：</span><span class="sxs-lookup"><span data-stu-id="2da13-117">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="2da13-118">值类型和引用类型数组</span><span class="sxs-lookup"><span data-stu-id="2da13-118">Value Type and Reference Type Arrays</span></span>

<span data-ttu-id="2da13-119">请考虑以下数组声明：</span><span class="sxs-lookup"><span data-stu-id="2da13-119">Consider the following array declaration:</span></span>  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

<span data-ttu-id="2da13-120">此语句的结果取决于 `SomeType` 是值类型还是引用类型。</span><span class="sxs-lookup"><span data-stu-id="2da13-120">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="2da13-121">如果它是值类型，该语句将创建一个 10 个元素的数组，其中每个元素的类型都为 `SomeType`。</span><span class="sxs-lookup"><span data-stu-id="2da13-121">If it's a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="2da13-122">如果 `SomeType` 是引用类型，该语句将创建一个 10 个元素的数组，其中每个元素都将被初始化为空引用。</span><span class="sxs-lookup"><span data-stu-id="2da13-122">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span> <span data-ttu-id="2da13-123">在两个实例中，元素均初始化为元素类型的默认值。</span><span class="sxs-lookup"><span data-stu-id="2da13-123">In both instances, the elements are initialized to the default value for the element type.</span></span> <span data-ttu-id="2da13-124">有关值类型和引用类型的详细信息，请参阅[值类型](../../language-reference/builtin-types/value-types.md)和[引用类型](../../language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2da13-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2da13-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="2da13-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="2da13-126">数组</span><span class="sxs-lookup"><span data-stu-id="2da13-126">Arrays</span></span>](./index.md)
- [<span data-ttu-id="2da13-127">多维数组</span><span class="sxs-lookup"><span data-stu-id="2da13-127">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="2da13-128">交错数组</span><span class="sxs-lookup"><span data-stu-id="2da13-128">Jagged Arrays</span></span>](./jagged-arrays.md)
