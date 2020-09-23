---
title: 复合数据类型
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 842b74aa7cc99c8196fdfb1eb6c976d9e72a4fa4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077158"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="c1910-102">复合数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1910-102">Composite Data Types (Visual Basic)</span></span>

<span data-ttu-id="c1910-103">除了 Visual Basic 提供的基本数据类型之外，还可以组合不同类型的项来创建 *复合数据类型* ，例如结构、数组和类。</span><span class="sxs-lookup"><span data-stu-id="c1910-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="c1910-104">您可以从基本类型和其他复合类型构建复合数据类型。</span><span class="sxs-lookup"><span data-stu-id="c1910-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="c1910-105">例如，可以定义结构元素数组或包含数组成员的结构。</span><span class="sxs-lookup"><span data-stu-id="c1910-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="c1910-106">数据类型</span><span class="sxs-lookup"><span data-stu-id="c1910-106">Data Types</span></span>  

 <span data-ttu-id="c1910-107">复合类型不同于它的任何组件的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c1910-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="c1910-108">例如，元素数组的 `Integer` `Integer` 数据类型不是。</span><span class="sxs-lookup"><span data-stu-id="c1910-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="c1910-109">数组数据类型通常使用元素类型、括号和逗号来表示（如有必要）。</span><span class="sxs-lookup"><span data-stu-id="c1910-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="c1910-110">例如，一个元素的一维数组 `String` 表示为，一个二维 `String()` `Boolean` 元素数组表示为 `Boolean(,)` 。</span><span class="sxs-lookup"><span data-stu-id="c1910-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="c1910-111">结构类型</span><span class="sxs-lookup"><span data-stu-id="c1910-111">Structure Types</span></span>  

 <span data-ttu-id="c1910-112">没有一种数据类型包含所有结构。</span><span class="sxs-lookup"><span data-stu-id="c1910-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="c1910-113">相反，结构的每个定义都表示唯一的数据类型，即使两个结构以相同顺序定义相同的元素也是如此。</span><span class="sxs-lookup"><span data-stu-id="c1910-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="c1910-114">但是，如果创建相同结构的两个或多个实例，Visual Basic 会将它们视为相同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c1910-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="c1910-115">元组</span><span class="sxs-lookup"><span data-stu-id="c1910-115">Tuples</span></span>

<span data-ttu-id="c1910-116">元组是一种轻型结构，它包含两个或更多已预定义类型的字段。</span><span class="sxs-lookup"><span data-stu-id="c1910-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="c1910-117">从 Visual Basic 2017 开始支持元组。</span><span class="sxs-lookup"><span data-stu-id="c1910-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="c1910-118">元组通常用于从单个方法调用返回多个值，而无需通过引用传递自变量，也不需要在更高权重的类或结构中打包返回字段。</span><span class="sxs-lookup"><span data-stu-id="c1910-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="c1910-119">有关元组的详细信息，请参阅 [元组](tuples.md) 主题。</span><span class="sxs-lookup"><span data-stu-id="c1910-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="c1910-120">数组类型</span><span class="sxs-lookup"><span data-stu-id="c1910-120">Array Types</span></span>  

 <span data-ttu-id="c1910-121">没有一种数据类型包含所有数组。</span><span class="sxs-lookup"><span data-stu-id="c1910-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="c1910-122">数组的特定实例的数据类型由以下内容确定：</span><span class="sxs-lookup"><span data-stu-id="c1910-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
- <span data-ttu-id="c1910-123">成为数组的事实</span><span class="sxs-lookup"><span data-stu-id="c1910-123">The fact of being an array</span></span>  
  
- <span data-ttu-id="c1910-124">数组) 维度的排名 (</span><span class="sxs-lookup"><span data-stu-id="c1910-124">The rank (number of dimensions) of the array</span></span>  
  
- <span data-ttu-id="c1910-125">数组的元素类型</span><span class="sxs-lookup"><span data-stu-id="c1910-125">The element type of the array</span></span>  
  
 <span data-ttu-id="c1910-126">具体而言，给定维度的长度不是该实例的数据类型的一部分。</span><span class="sxs-lookup"><span data-stu-id="c1910-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="c1910-127">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="c1910-127">The following example illustrates this.</span></span>  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="c1910-128">在前面的示例中，数组变量 `arrayA` 和被 `arrayB` 视为具有相同的数据类型（ `Byte()` 即使它们被初始化为不同的长度）。</span><span class="sxs-lookup"><span data-stu-id="c1910-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="c1910-129">变量 `arrayB` 和 `arrayC` 不属于同一类型，因为它们的元素类型不同。</span><span class="sxs-lookup"><span data-stu-id="c1910-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="c1910-130">变量 `arrayC` 和 `arrayD` 不属于同一类型，因为它们的秩不同。</span><span class="sxs-lookup"><span data-stu-id="c1910-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="c1910-131">变量 `arrayD` 和 `arrayE` 具有相同的类型（ `Short(,)` ），因为它们的秩和元素类型是相同的，即使尚未 `arrayD` 初始化也是如此。</span><span class="sxs-lookup"><span data-stu-id="c1910-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="c1910-132">有关数组的详细信息，请参阅 [数组](../arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c1910-132">For more information on arrays, see [Arrays](../arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="c1910-133">类类型</span><span class="sxs-lookup"><span data-stu-id="c1910-133">Class Types</span></span>  

 <span data-ttu-id="c1910-134">没有一种数据类型包含所有类。</span><span class="sxs-lookup"><span data-stu-id="c1910-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="c1910-135">尽管一个类可以继承自另一个类，但每个类都是单独的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c1910-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="c1910-136">同一类的多个实例具有相同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c1910-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="c1910-137">如果您将一个类实例变量分配给另一个类，则不仅可以使用相同的数据类型，它们指向内存中的同一个类实例。</span><span class="sxs-lookup"><span data-stu-id="c1910-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="c1910-138">有关类的详细信息，请参阅 [对象和类](../objects-and-classes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c1910-138">For more information on classes, see [Objects and Classes](../objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1910-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="c1910-139">See also</span></span>

- [<span data-ttu-id="c1910-140">数据类型</span><span class="sxs-lookup"><span data-stu-id="c1910-140">Data Types</span></span>](index.md)
- [<span data-ttu-id="c1910-141">基本数据类型</span><span class="sxs-lookup"><span data-stu-id="c1910-141">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="c1910-142">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c1910-142">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="c1910-143">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="c1910-143">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="c1910-144">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="c1910-144">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="c1910-145">结构</span><span class="sxs-lookup"><span data-stu-id="c1910-145">Structures</span></span>](structures.md)
- [<span data-ttu-id="c1910-146">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="c1910-146">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="c1910-147">如何：在一个变量中保留多个值</span><span class="sxs-lookup"><span data-stu-id="c1910-147">How to: Hold More Than One Value in a Variable</span></span>](how-to-hold-more-than-one-value-in-a-variable.md)
