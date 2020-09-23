---
title: 常数和文本数据类型
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 03d693653cd166bbf1096031f1a864b492e2e896
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086291"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="ec02e-102">常量和 Literal 数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec02e-102">Constant and Literal Data Types (Visual Basic)</span></span>

<span data-ttu-id="ec02e-103">文本是一个值，它表示为自身，而不是作为变量的值或表达式的结果，如数字3或字符串 "Hello"。</span><span class="sxs-lookup"><span data-stu-id="ec02e-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="ec02e-104">常量是有意义的名称，用于代替文本，并在整个程序中保留此相同的值，而不是变量（其值可能会更改）。</span><span class="sxs-lookup"><span data-stu-id="ec02e-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="ec02e-105">如果 [选项推断](../../../language-reference/statements/option-infer-statement.md) 为 `Off` ，且 [option Strict](../../../language-reference/statements/option-strict-statement.md) 为 `On` ，则必须使用数据类型显式声明所有常量。</span><span class="sxs-lookup"><span data-stu-id="ec02e-105">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="ec02e-106">在下面的示例中，的数据类型 `MyByte` 显式声明为数据类型 `Byte` ：</span><span class="sxs-lookup"><span data-stu-id="ec02e-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 <span data-ttu-id="ec02e-107">当 `Option Infer` 为 `On` 或 `Option Strict` 时 `Off` ，可以声明常量，而无需使用子句指定数据类型 `As` 。</span><span class="sxs-lookup"><span data-stu-id="ec02e-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="ec02e-108">编译器将确定表达式的类型的常量类型。</span><span class="sxs-lookup"><span data-stu-id="ec02e-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="ec02e-109">默认情况下，将数值转换为 `Integer` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="ec02e-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="ec02e-110">浮点数字的默认数据类型为 `Double` ，关键字 `True` 和 `False` 指定 `Boolean` 常量。</span><span class="sxs-lookup"><span data-stu-id="ec02e-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="ec02e-111">文本和类型强制</span><span class="sxs-lookup"><span data-stu-id="ec02e-111">Literals and Type Coercion</span></span>  

 <span data-ttu-id="ec02e-112">在某些情况下，可能需要将文本强制用于特定的数据类型;例如，将特别大的整数文本值分配给类型的变量时 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="ec02e-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="ec02e-113">下面的示例生成错误：</span><span class="sxs-lookup"><span data-stu-id="ec02e-113">The following example produces an error:</span></span>  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="ec02e-114">此错误是由文本的表示形式导致的。</span><span class="sxs-lookup"><span data-stu-id="ec02e-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="ec02e-115">`Decimal`数据类型可以保存此大值，但文本隐式表示为 `Long` ，不能为。</span><span class="sxs-lookup"><span data-stu-id="ec02e-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="ec02e-116">可以通过两种方式将文本强制转换为特定数据类型：向其追加类型字符，或将其放在封闭字符内。</span><span class="sxs-lookup"><span data-stu-id="ec02e-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="ec02e-117">类型字符或封闭字符必须紧跟在文本之前和/或之后，无需任何插入空格或任何类型的字符。</span><span class="sxs-lookup"><span data-stu-id="ec02e-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="ec02e-118">若要使上面的示例正常运行，可以将 `D` 类型字符追加到文本中，这会使其表示为 `Decimal` ：</span><span class="sxs-lookup"><span data-stu-id="ec02e-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 <span data-ttu-id="ec02e-119">下面的示例演示类型字符和封闭字符的正确用法：</span><span class="sxs-lookup"><span data-stu-id="ec02e-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 <span data-ttu-id="ec02e-120">下表显示 Visual Basic 中可用的封闭字符和类型字符。</span><span class="sxs-lookup"><span data-stu-id="ec02e-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="ec02e-121">数据类型</span><span class="sxs-lookup"><span data-stu-id="ec02e-121">Data type</span></span>|<span data-ttu-id="ec02e-122">封闭字符</span><span class="sxs-lookup"><span data-stu-id="ec02e-122">Enclosing character</span></span>|<span data-ttu-id="ec02e-123">追加的类型字符</span><span class="sxs-lookup"><span data-stu-id="ec02e-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="ec02e-124">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-124">(none)</span></span>|<span data-ttu-id="ec02e-125">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="ec02e-126">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-126">(none)</span></span>|<span data-ttu-id="ec02e-127">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="ec02e-128">"</span><span class="sxs-lookup"><span data-stu-id="ec02e-128">"</span></span>|<span data-ttu-id="ec02e-129">C</span><span class="sxs-lookup"><span data-stu-id="ec02e-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="ec02e-130">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="ec02e-131">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-131">(none)</span></span>|<span data-ttu-id="ec02e-132">D 或@</span><span class="sxs-lookup"><span data-stu-id="ec02e-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="ec02e-133">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-133">(none)</span></span>|<span data-ttu-id="ec02e-134">R 或#</span><span class="sxs-lookup"><span data-stu-id="ec02e-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="ec02e-135">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-135">(none)</span></span>|<span data-ttu-id="ec02e-136">I 或%</span><span class="sxs-lookup"><span data-stu-id="ec02e-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="ec02e-137">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-137">(none)</span></span>|<span data-ttu-id="ec02e-138">L 或 &</span><span class="sxs-lookup"><span data-stu-id="ec02e-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="ec02e-139">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-139">(none)</span></span>|<span data-ttu-id="ec02e-140">S</span><span class="sxs-lookup"><span data-stu-id="ec02e-140">S</span></span>|  
|`Single`|<span data-ttu-id="ec02e-141">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-141">(none)</span></span>|<span data-ttu-id="ec02e-142">F 或！</span><span class="sxs-lookup"><span data-stu-id="ec02e-142">F or !</span></span>|  
|`String`|<span data-ttu-id="ec02e-143">"</span><span class="sxs-lookup"><span data-stu-id="ec02e-143">"</span></span>|<span data-ttu-id="ec02e-144">（无）</span><span class="sxs-lookup"><span data-stu-id="ec02e-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec02e-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="ec02e-145">See also</span></span>

- [<span data-ttu-id="ec02e-146">用户定义常数</span><span class="sxs-lookup"><span data-stu-id="ec02e-146">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="ec02e-147">如何：声明常量</span><span class="sxs-lookup"><span data-stu-id="ec02e-147">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="ec02e-148">常量概述</span><span class="sxs-lookup"><span data-stu-id="ec02e-148">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="ec02e-149">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="ec02e-149">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="ec02e-150">Option Explicit 语句</span><span class="sxs-lookup"><span data-stu-id="ec02e-150">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="ec02e-151">枚举概述</span><span class="sxs-lookup"><span data-stu-id="ec02e-151">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="ec02e-152">如何：声明枚举</span><span class="sxs-lookup"><span data-stu-id="ec02e-152">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="ec02e-153">枚举和名称限定</span><span class="sxs-lookup"><span data-stu-id="ec02e-153">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="ec02e-154">数据类型</span><span class="sxs-lookup"><span data-stu-id="ec02e-154">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="ec02e-155">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="ec02e-155">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
