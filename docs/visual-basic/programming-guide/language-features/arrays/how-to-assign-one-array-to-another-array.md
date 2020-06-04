---
title: 如何：将一个数组赋给另一个数组
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: c38def1ba9f3720bc760d6f6e4264510c884c930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413074"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="98b2d-102">如何：将一个数组赋给另一个数组 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98b2d-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="98b2d-103">由于数组是对象，因此可以在赋值语句（如其他对象类型）中使用它们。</span><span class="sxs-lookup"><span data-stu-id="98b2d-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="98b2d-104">数组变量包含指向数组元素构成的数据的指针、秩和长度信息，并且赋值仅复制此指针。</span><span class="sxs-lookup"><span data-stu-id="98b2d-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="98b2d-105">将一个数组赋给另一个数组</span><span class="sxs-lookup"><span data-stu-id="98b2d-105">To assign one array to another array</span></span>

1. <span data-ttu-id="98b2d-106">确保两个数组具有相同的秩（维数）和兼容的元素数据类型。</span><span class="sxs-lookup"><span data-stu-id="98b2d-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="98b2d-107">使用标准赋值语句将源数组分配给目标数组。</span><span class="sxs-lookup"><span data-stu-id="98b2d-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="98b2d-108">不要在数组名称后面加上括号。</span><span class="sxs-lookup"><span data-stu-id="98b2d-108">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="98b2d-109">将一个数组分配到另一个数组时，下列规则适用：</span><span class="sxs-lookup"><span data-stu-id="98b2d-109">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="98b2d-110">**秩相等。**</span><span class="sxs-lookup"><span data-stu-id="98b2d-110">**Equal Ranks.**</span></span> <span data-ttu-id="98b2d-111">目标数组的秩（维数）必须与源数组的秩相同。</span><span class="sxs-lookup"><span data-stu-id="98b2d-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="98b2d-112">如果两个数组的秩相等，则维度不需要相等。</span><span class="sxs-lookup"><span data-stu-id="98b2d-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="98b2d-113">给定维度中的元素数在赋值期间可能会更改。</span><span class="sxs-lookup"><span data-stu-id="98b2d-113">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="98b2d-114">**元素类型。**</span><span class="sxs-lookup"><span data-stu-id="98b2d-114">**Element Types.**</span></span> <span data-ttu-id="98b2d-115">这两个数组都必须具有*引用类型*元素，或者两个数组都必须具有*值类型*元素。</span><span class="sxs-lookup"><span data-stu-id="98b2d-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="98b2d-116">有关详细信息，请参阅[值类型和引用类型](../data-types/value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="98b2d-116">For more information, see [Value Types and Reference Types](../data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="98b2d-117">如果两个数组都具有值类型元素，则元素数据类型必须完全相同。</span><span class="sxs-lookup"><span data-stu-id="98b2d-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="98b2d-118">唯一的例外是，你可以将元素数组分配 `Enum` 给该的基类型的数组 `Enum` 。</span><span class="sxs-lookup"><span data-stu-id="98b2d-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="98b2d-119">如果两个数组都具有引用类型元素，则源元素类型必须派生自目标元素类型。</span><span class="sxs-lookup"><span data-stu-id="98b2d-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="98b2d-120">在这种情况下，两个数组与它们的元素具有相同的继承关系。</span><span class="sxs-lookup"><span data-stu-id="98b2d-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="98b2d-121">这称为*数组协方差*。</span><span class="sxs-lookup"><span data-stu-id="98b2d-121">This is called *array covariance*.</span></span>

<span data-ttu-id="98b2d-122">如果违反上述规则（例如，如果数据类型不兼容或秩不相等），编译器将报告错误。</span><span class="sxs-lookup"><span data-stu-id="98b2d-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="98b2d-123">您可以在代码中添加错误处理，以确保在尝试赋值之前数组是兼容的。</span><span class="sxs-lookup"><span data-stu-id="98b2d-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="98b2d-124">如果要避免引发异常，还可以使用[TryCast 运算符](../../../language-reference/operators/trycast-operator.md)关键字。</span><span class="sxs-lookup"><span data-stu-id="98b2d-124">You can also use the [TryCast Operator](../../../language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="98b2d-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98b2d-125">See also</span></span>

- [<span data-ttu-id="98b2d-126">数组</span><span class="sxs-lookup"><span data-stu-id="98b2d-126">Arrays</span></span>](index.md)
- [<span data-ttu-id="98b2d-127">数组疑难解答</span><span class="sxs-lookup"><span data-stu-id="98b2d-127">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="98b2d-128">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="98b2d-128">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="98b2d-129">数组转换</span><span class="sxs-lookup"><span data-stu-id="98b2d-129">Array Conversions</span></span>](../data-types/array-conversions.md)
