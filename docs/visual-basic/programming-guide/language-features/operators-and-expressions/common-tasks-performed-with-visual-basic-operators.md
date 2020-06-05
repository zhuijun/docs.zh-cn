---
title: 使用 Visual Basic 运算符执行的常规任务
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], logical
- operators [Visual Basic], string concatenation
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- operators [Visual Basic], arithmetic
- operators [Visual Basic], string comparison
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- operators [Visual Basic], comparison
- operators [Visual Basic], short-circuiting logical
ms.assetid: d181afe5-fafa-460f-a13b-81203f6f4587
ms.openlocfilehash: 62ced7f2048ae41c7ea4c9d62c0ff0a903c37856
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388915"
---
# <a name="common-tasks-performed-with-visual-basic-operators"></a><span data-ttu-id="1c37d-102">使用 Visual Basic 运算符执行的常规任务</span><span class="sxs-lookup"><span data-stu-id="1c37d-102">Common Tasks Performed with Visual Basic Operators</span></span>
<span data-ttu-id="1c37d-103">运算符执行涉及一个或多个称为*操作数*的表达式的许多常见任务。</span><span class="sxs-lookup"><span data-stu-id="1c37d-103">Operators perform many common tasks involving one or more expressions called *operands*.</span></span>  
  
## <a name="arithmetic-and-bit-shift-tasks"></a><span data-ttu-id="1c37d-104">算术和移位任务</span><span class="sxs-lookup"><span data-stu-id="1c37d-104">Arithmetic and Bit-shift Tasks</span></span>  
 <span data-ttu-id="1c37d-105">下表总结了可用的算术和移位运算。</span><span class="sxs-lookup"><span data-stu-id="1c37d-105">The following table summarizes the available arithmetic and bit-shift operations.</span></span>  
  
|<span data-ttu-id="1c37d-106">功能</span><span class="sxs-lookup"><span data-stu-id="1c37d-106">To</span></span>|<span data-ttu-id="1c37d-107">查看</span><span class="sxs-lookup"><span data-stu-id="1c37d-107">See</span></span>|  
|---|---|  
|<span data-ttu-id="1c37d-108">向另一个数值添加一个数值</span><span class="sxs-lookup"><span data-stu-id="1c37d-108">Add one numeric value to another</span></span>|[<span data-ttu-id="1c37d-109">+ 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-109">+ Operator</span></span>](../../../language-reference/operators/addition-operator.md)|  
|<span data-ttu-id="1c37d-110">从一个数值中减去另一个数值</span><span class="sxs-lookup"><span data-stu-id="1c37d-110">Subtract one numeric value from another</span></span>|[<span data-ttu-id="1c37d-111">-Operator （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1c37d-111">- Operator (Visual Basic)</span></span>](../../../language-reference/operators/subtraction-operator.md)|  
|<span data-ttu-id="1c37d-112">反转数值的符号</span><span class="sxs-lookup"><span data-stu-id="1c37d-112">Reverse the sign of a numeric value</span></span>|[<span data-ttu-id="1c37d-113">-Operator （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1c37d-113">- Operator (Visual Basic)</span></span>](../../../language-reference/operators/subtraction-operator.md)|  
|<span data-ttu-id="1c37d-114">将一个数值乘以另一个数值</span><span class="sxs-lookup"><span data-stu-id="1c37d-114">Multiply one numeric value by another</span></span>|[<span data-ttu-id="1c37d-115">\* 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-115">\* Operator</span></span>](../../../language-reference/operators/multiplication-operator.md)|  
|<span data-ttu-id="1c37d-116">将一个数值除以另一个数值</span><span class="sxs-lookup"><span data-stu-id="1c37d-116">Divide one numeric value into another</span></span>|[<span data-ttu-id="1c37d-117">/ 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c37d-117">/ Operator (Visual Basic)</span></span>](../../../language-reference/operators/floating-point-division-operator.md)|  
|<span data-ttu-id="1c37d-118">查找一个数值除以另一个数值的商（没有余数）</span><span class="sxs-lookup"><span data-stu-id="1c37d-118">Find the quotient of one numeric value divided by another (without the remainder)</span></span>|[<span data-ttu-id="1c37d-119">\ 运算符（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1c37d-119">\ Operator (Visual Basic)</span></span>](../../../language-reference/operators/integer-division-operator.md)|  
|<span data-ttu-id="1c37d-120">查找一个数值除以另一个数值的余数（不含商）</span><span class="sxs-lookup"><span data-stu-id="1c37d-120">Find the remainder of one numeric value divided by another (without the quotient)</span></span>|[<span data-ttu-id="1c37d-121">Mod 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-121">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)|  
|<span data-ttu-id="1c37d-122">向一个数值增加另一个数值</span><span class="sxs-lookup"><span data-stu-id="1c37d-122">Raise one numeric value to the power of another</span></span>|[<span data-ttu-id="1c37d-123">^ 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-123">^ Operator</span></span>](../../../language-reference/operators/exponentiation-operator.md)|  
|<span data-ttu-id="1c37d-124">将数值的位模式向左移动</span><span class="sxs-lookup"><span data-stu-id="1c37d-124">Shift the bit pattern of a numeric value to the left</span></span>|[<span data-ttu-id="1c37d-125"><\<操作员</span><span class="sxs-lookup"><span data-stu-id="1c37d-125"><\< Operator</span></span>](../../../language-reference/operators/left-shift-operator.md)|  
|<span data-ttu-id="1c37d-126">将数值的位模式向右移位</span><span class="sxs-lookup"><span data-stu-id="1c37d-126">Shift the bit pattern of a numeric value to the right</span></span>|[<span data-ttu-id="1c37d-127">>> 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-127">>> Operator</span></span>](../../../language-reference/operators/right-shift-operator.md)|  
  
## <a name="comparison-tasks"></a><span data-ttu-id="1c37d-128">比较任务</span><span class="sxs-lookup"><span data-stu-id="1c37d-128">Comparison Tasks</span></span>  
 <span data-ttu-id="1c37d-129">下表总结了可用的比较运算。</span><span class="sxs-lookup"><span data-stu-id="1c37d-129">The following table summarizes the available comparison operations.</span></span>  
  
|<span data-ttu-id="1c37d-130">功能</span><span class="sxs-lookup"><span data-stu-id="1c37d-130">To</span></span>|<span data-ttu-id="1c37d-131">查看</span><span class="sxs-lookup"><span data-stu-id="1c37d-131">See</span></span>|  
|---|---|  
|<span data-ttu-id="1c37d-132">确定两个值是否相等</span><span class="sxs-lookup"><span data-stu-id="1c37d-132">Determine whether two values are equal</span></span>|<span data-ttu-id="1c37d-133">`=`运算符（[Visual Basic 中的比较运算符](comparison-operators.md)）</span><span class="sxs-lookup"><span data-stu-id="1c37d-133">`=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="1c37d-134">确定两个值是否不相等</span><span class="sxs-lookup"><span data-stu-id="1c37d-134">Determine whether two values are unequal</span></span>|<span data-ttu-id="1c37d-135">`<>`运算符（[Visual Basic 中的比较运算符](comparison-operators.md)）</span><span class="sxs-lookup"><span data-stu-id="1c37d-135">`<>` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="1c37d-136">确定一个值是否小于另一个值</span><span class="sxs-lookup"><span data-stu-id="1c37d-136">Determine whether one value is less than another</span></span>|<span data-ttu-id="1c37d-137">`<`运算符（[Visual Basic 中的比较运算符](comparison-operators.md)）</span><span class="sxs-lookup"><span data-stu-id="1c37d-137">`<` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="1c37d-138">确定一个值是否大于另一个值</span><span class="sxs-lookup"><span data-stu-id="1c37d-138">Determine whether one value is greater than another</span></span>|<span data-ttu-id="1c37d-139">`>`运算符（[Visual Basic 中的比较运算符](comparison-operators.md)）</span><span class="sxs-lookup"><span data-stu-id="1c37d-139">`>` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="1c37d-140">确定一个值是否小于或等于另一个值</span><span class="sxs-lookup"><span data-stu-id="1c37d-140">Determine whether one value is less than or equal to another</span></span>|<span data-ttu-id="1c37d-141">`<=`运算符（[Visual Basic 中的比较运算符](comparison-operators.md)）</span><span class="sxs-lookup"><span data-stu-id="1c37d-141">`<=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="1c37d-142">确定一个值是否大于或等于另一个值</span><span class="sxs-lookup"><span data-stu-id="1c37d-142">Determine whether one value is greater than or equal to another</span></span>|<span data-ttu-id="1c37d-143">`>=`运算符（[Visual Basic 中的比较运算符](comparison-operators.md)）</span><span class="sxs-lookup"><span data-stu-id="1c37d-143">`>=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="1c37d-144">确定两个对象变量是否引用相同的对象实例</span><span class="sxs-lookup"><span data-stu-id="1c37d-144">Determine whether two object variables refer to the same object instance</span></span>|[<span data-ttu-id="1c37d-145">Is 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-145">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)|  
|<span data-ttu-id="1c37d-146">确定两个对象变量是否引用不同的对象实例</span><span class="sxs-lookup"><span data-stu-id="1c37d-146">Determine whether two object variables refer to different object instances</span></span>|[<span data-ttu-id="1c37d-147">IsNot 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-147">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)|  
|<span data-ttu-id="1c37d-148">确定对象是否为特定类型</span><span class="sxs-lookup"><span data-stu-id="1c37d-148">Determine whether an object is of a specific type</span></span>|[<span data-ttu-id="1c37d-149">TypeOf 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-149">TypeOf Operator</span></span>](../../../language-reference/operators/typeof-operator.md)|  
  
## <a name="concatenation-tasks"></a><span data-ttu-id="1c37d-150">串联任务</span><span class="sxs-lookup"><span data-stu-id="1c37d-150">Concatenation Tasks</span></span>  
 <span data-ttu-id="1c37d-151">下表总结了可用的串联运算。</span><span class="sxs-lookup"><span data-stu-id="1c37d-151">The following table summarizes the available concatenation operations.</span></span>  
  
|<span data-ttu-id="1c37d-152">功能</span><span class="sxs-lookup"><span data-stu-id="1c37d-152">To</span></span>|<span data-ttu-id="1c37d-153">查看</span><span class="sxs-lookup"><span data-stu-id="1c37d-153">See</span></span>|  
|---|---|  
|<span data-ttu-id="1c37d-154">将多个字符串联接为一个字符串</span><span class="sxs-lookup"><span data-stu-id="1c37d-154">Join multiple strings into a single string</span></span>|<span data-ttu-id="1c37d-155">`&`运算符（[Visual Basic 中的串联运算符](concatenation-operators.md)）</span><span class="sxs-lookup"><span data-stu-id="1c37d-155">`&` Operator ([Concatenation Operators in Visual Basic](concatenation-operators.md))</span></span>|  
|<span data-ttu-id="1c37d-156">用字符串值联接数值</span><span class="sxs-lookup"><span data-stu-id="1c37d-156">Join numeric values with string values</span></span>|<span data-ttu-id="1c37d-157">`+`运算符（[Visual Basic 中的串联运算符](concatenation-operators.md)）</span><span class="sxs-lookup"><span data-stu-id="1c37d-157">`+` Operator ([Concatenation Operators in Visual Basic](concatenation-operators.md))</span></span>|  
  
## <a name="logical-and-bitwise-tasks"></a><span data-ttu-id="1c37d-158">逻辑和按位任务</span><span class="sxs-lookup"><span data-stu-id="1c37d-158">Logical and Bitwise Tasks</span></span>  
 <span data-ttu-id="1c37d-159">下表总结了可用的逻辑和按位运算。</span><span class="sxs-lookup"><span data-stu-id="1c37d-159">The following table summarizes the available logical and bitwise operations.</span></span>  
  
|<span data-ttu-id="1c37d-160">功能</span><span class="sxs-lookup"><span data-stu-id="1c37d-160">To</span></span>|<span data-ttu-id="1c37d-161">查看</span><span class="sxs-lookup"><span data-stu-id="1c37d-161">See</span></span>|  
|---|---|  
|<span data-ttu-id="1c37d-162">对布尔值执行逻辑非运算</span><span class="sxs-lookup"><span data-stu-id="1c37d-162">Perform logical negation on a Boolean value</span></span>|[<span data-ttu-id="1c37d-163">Not 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-163">Not Operator</span></span>](../../../language-reference/operators/not-operator.md)|  
|<span data-ttu-id="1c37d-164">对两个布尔值执行逻辑与运算</span><span class="sxs-lookup"><span data-stu-id="1c37d-164">Perform logical conjunction on two Boolean values</span></span>|[<span data-ttu-id="1c37d-165">And 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-165">And Operator</span></span>](../../../language-reference/operators/and-operator.md)|  
|<span data-ttu-id="1c37d-166">对两个布尔值执行包含逻辑析取</span><span class="sxs-lookup"><span data-stu-id="1c37d-166">Perform inclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="1c37d-167">Or 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-167">Or Operator</span></span>](../../../language-reference/operators/or-operator.md)|  
|<span data-ttu-id="1c37d-168">对两个布尔值执行独占逻辑析取</span><span class="sxs-lookup"><span data-stu-id="1c37d-168">Perform exclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="1c37d-169">Xor 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-169">Xor Operator</span></span>](../../../language-reference/operators/xor-operator.md)|  
|<span data-ttu-id="1c37d-170">对两个布尔值执行短路逻辑与运算</span><span class="sxs-lookup"><span data-stu-id="1c37d-170">Perform short-circuited logical conjunction on two Boolean values</span></span>|[<span data-ttu-id="1c37d-171">AndAlso 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-171">AndAlso Operator</span></span>](../../../language-reference/operators/andalso-operator.md)|  
|<span data-ttu-id="1c37d-172">对两个布尔值执行短路包含逻辑析取</span><span class="sxs-lookup"><span data-stu-id="1c37d-172">Perform short-circuited inclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="1c37d-173">OrElse 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-173">OrElse Operator</span></span>](../../../language-reference/operators/orelse-operator.md)|  
|<span data-ttu-id="1c37d-174">对两个整数值执行按位逻辑与运算</span><span class="sxs-lookup"><span data-stu-id="1c37d-174">Perform bit-by-bit logical conjunction on two integral values</span></span>|[<span data-ttu-id="1c37d-175">And 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-175">And Operator</span></span>](../../../language-reference/operators/and-operator.md)|  
|<span data-ttu-id="1c37d-176">对两个整数值执行逐位包含逻辑析取</span><span class="sxs-lookup"><span data-stu-id="1c37d-176">Perform bit-by-bit inclusive logical disjunction on two integral values</span></span>|[<span data-ttu-id="1c37d-177">Or 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-177">Or Operator</span></span>](../../../language-reference/operators/or-operator.md)|  
|<span data-ttu-id="1c37d-178">对两个整数值执行按位异或逻辑析取</span><span class="sxs-lookup"><span data-stu-id="1c37d-178">Perform bit-by-bit exclusive logical disjunction on two integral values</span></span>|[<span data-ttu-id="1c37d-179">Xor 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-179">Xor Operator</span></span>](../../../language-reference/operators/xor-operator.md)|  
|<span data-ttu-id="1c37d-180">对整数值执行按位逻辑求反</span><span class="sxs-lookup"><span data-stu-id="1c37d-180">Perform bit-by-bit logical negation on an integral value</span></span>|[<span data-ttu-id="1c37d-181">Not 运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-181">Not Operator</span></span>](../../../language-reference/operators/not-operator.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1c37d-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c37d-182">See also</span></span>

- [<span data-ttu-id="1c37d-183">运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="1c37d-183">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="1c37d-184">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="1c37d-184">Operators Listed by Functionality</span></span>](../../../language-reference/operators/operators-listed-by-functionality.md)
