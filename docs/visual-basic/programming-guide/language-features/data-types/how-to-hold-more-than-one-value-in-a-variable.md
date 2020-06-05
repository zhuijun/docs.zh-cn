---
title: 如何：在一个变量中保留多个值
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 399c5909ee6988f96bcc85260b0401f3bd18a0f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393891"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="e12f5-102">如何：在一个变量中保存多个值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e12f5-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="e12f5-103">如果将变量声明为*复合数据类型*，则该变量包含多个值。</span><span class="sxs-lookup"><span data-stu-id="e12f5-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="e12f5-104">[复合数据类型](composite-data-types.md)包括结构、数组和类。</span><span class="sxs-lookup"><span data-stu-id="e12f5-104">[Composite Data Types](composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="e12f5-105">复合数据类型的变量可以包含基本数据类型和其他复合类型的组合。</span><span class="sxs-lookup"><span data-stu-id="e12f5-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="e12f5-106">结构和类可以保存代码以及数据。</span><span class="sxs-lookup"><span data-stu-id="e12f5-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="e12f5-107">在一个变量中保存多个值</span><span class="sxs-lookup"><span data-stu-id="e12f5-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="e12f5-108">确定要为变量使用哪种复合数据类型。</span><span class="sxs-lookup"><span data-stu-id="e12f5-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="e12f5-109">如果尚未定义复合数据类型，请对其进行定义，使变量可以使用它。</span><span class="sxs-lookup"><span data-stu-id="e12f5-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="e12f5-110">使用[结构语句](../../../language-reference/statements/structure-statement.md)定义结构。</span><span class="sxs-lookup"><span data-stu-id="e12f5-110">Define a structure with a [Structure Statement](../../../language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="e12f5-111">定义带有[Dim 语句](../../../language-reference/statements/dim-statement.md)的数组。</span><span class="sxs-lookup"><span data-stu-id="e12f5-111">Define an array with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="e12f5-112">使用[类语句](../../../language-reference/statements/class-statement.md)定义类。</span><span class="sxs-lookup"><span data-stu-id="e12f5-112">Define a class with a [Class Statement](../../../language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="e12f5-113">使用语句声明变量 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="e12f5-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="e12f5-114">使用子句的变量名称 `As` 。</span><span class="sxs-lookup"><span data-stu-id="e12f5-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="e12f5-115">在关键字后跟 `As` 适当的复合数据类型的名称。</span><span class="sxs-lookup"><span data-stu-id="e12f5-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="e12f5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e12f5-116">See also</span></span>

- [<span data-ttu-id="e12f5-117">数据类型</span><span class="sxs-lookup"><span data-stu-id="e12f5-117">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="e12f5-118">类型字符</span><span class="sxs-lookup"><span data-stu-id="e12f5-118">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="e12f5-119">复合数据类型</span><span class="sxs-lookup"><span data-stu-id="e12f5-119">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="e12f5-120">结构</span><span class="sxs-lookup"><span data-stu-id="e12f5-120">Structures</span></span>](structures.md)
- [<span data-ttu-id="e12f5-121">数组</span><span class="sxs-lookup"><span data-stu-id="e12f5-121">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="e12f5-122">对象和类</span><span class="sxs-lookup"><span data-stu-id="e12f5-122">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="e12f5-123">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="e12f5-123">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
