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
ms.openlocfilehash: a8a8d7898e52077fef47b91172e34ad50d7f54e7
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075208"
---
# <a name="common-tasks-performed-with-visual-basic-operators"></a><span data-ttu-id="39e43-102">使用 Visual Basic 运算符执行的常规任务</span><span class="sxs-lookup"><span data-stu-id="39e43-102">Common Tasks Performed with Visual Basic Operators</span></span>

<span data-ttu-id="39e43-103">运算符执行涉及一个或多个称为 *操作数*的表达式的许多常见任务。</span><span class="sxs-lookup"><span data-stu-id="39e43-103">Operators perform many common tasks involving one or more expressions called *operands*.</span></span>  
  
## <a name="arithmetic-and-bit-shift-tasks"></a><span data-ttu-id="39e43-104">算术和移位任务</span><span class="sxs-lookup"><span data-stu-id="39e43-104">Arithmetic and Bit-shift Tasks</span></span>  

 <span data-ttu-id="39e43-105">下表总结了可用的算术和移位运算。</span><span class="sxs-lookup"><span data-stu-id="39e43-105">The following table summarizes the available arithmetic and bit-shift operations.</span></span>  
  
|<span data-ttu-id="39e43-106">功能</span><span class="sxs-lookup"><span data-stu-id="39e43-106">To</span></span>|<span data-ttu-id="39e43-107">查看</span><span class="sxs-lookup"><span data-stu-id="39e43-107">See</span></span>|  
|---|---|  
|<span data-ttu-id="39e43-108">向另一个数值添加一个数值</span><span class="sxs-lookup"><span data-stu-id="39e43-108">Add one numeric value to another</span></span>|[<span data-ttu-id="39e43-109">+ 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-109">+ Operator</span></span>](../../../language-reference/operators/addition-operator.md)|  
|<span data-ttu-id="39e43-110">从一个数值中减去另一个数值</span><span class="sxs-lookup"><span data-stu-id="39e43-110">Subtract one numeric value from another</span></span>|[<span data-ttu-id="39e43-111">-Operator (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="39e43-111">- Operator (Visual Basic)</span></span>](../../../language-reference/operators/subtraction-operator.md)|  
|<span data-ttu-id="39e43-112">反转数值的符号</span><span class="sxs-lookup"><span data-stu-id="39e43-112">Reverse the sign of a numeric value</span></span>|[<span data-ttu-id="39e43-113">-Operator (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="39e43-113">- Operator (Visual Basic)</span></span>](../../../language-reference/operators/subtraction-operator.md)|  
|<span data-ttu-id="39e43-114">将一个数值乘以另一个数值</span><span class="sxs-lookup"><span data-stu-id="39e43-114">Multiply one numeric value by another</span></span>|[<span data-ttu-id="39e43-115">\* 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-115">\* Operator</span></span>](../../../language-reference/operators/multiplication-operator.md)|  
|<span data-ttu-id="39e43-116">将一个数值除以另一个数值</span><span class="sxs-lookup"><span data-stu-id="39e43-116">Divide one numeric value into another</span></span>|[<span data-ttu-id="39e43-117">/Operator (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="39e43-117">/ Operator (Visual Basic)</span></span>](../../../language-reference/operators/floating-point-division-operator.md)|  
|<span data-ttu-id="39e43-118">查找一个数值除以另 (一个数值的商，而不包含余数) </span><span class="sxs-lookup"><span data-stu-id="39e43-118">Find the quotient of one numeric value divided by another (without the remainder)</span></span>|[<span data-ttu-id="39e43-119">\ 运算符 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="39e43-119">\ Operator (Visual Basic)</span></span>](../../../language-reference/operators/integer-division-operator.md)|  
|<span data-ttu-id="39e43-120">查找一个数值除以另一个数值相除后的余数 (不包含商) </span><span class="sxs-lookup"><span data-stu-id="39e43-120">Find the remainder of one numeric value divided by another (without the quotient)</span></span>|[<span data-ttu-id="39e43-121">Mod 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-121">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)|  
|<span data-ttu-id="39e43-122">向一个数值增加另一个数值</span><span class="sxs-lookup"><span data-stu-id="39e43-122">Raise one numeric value to the power of another</span></span>|[<span data-ttu-id="39e43-123">^ 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-123">^ Operator</span></span>](../../../language-reference/operators/exponentiation-operator.md)|  
|<span data-ttu-id="39e43-124">将数值的位模式向左移动</span><span class="sxs-lookup"><span data-stu-id="39e43-124">Shift the bit pattern of a numeric value to the left</span></span>|[<span data-ttu-id="39e43-125"><\< 操作员</span><span class="sxs-lookup"><span data-stu-id="39e43-125"><\< Operator</span></span>](../../../language-reference/operators/left-shift-operator.md)|  
|<span data-ttu-id="39e43-126">将数值的位模式向右移位</span><span class="sxs-lookup"><span data-stu-id="39e43-126">Shift the bit pattern of a numeric value to the right</span></span>|[<span data-ttu-id="39e43-127">>> 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-127">>> Operator</span></span>](../../../language-reference/operators/right-shift-operator.md)|  
  
## <a name="comparison-tasks"></a><span data-ttu-id="39e43-128">比较任务</span><span class="sxs-lookup"><span data-stu-id="39e43-128">Comparison Tasks</span></span>  

 <span data-ttu-id="39e43-129">下表总结了可用的比较运算。</span><span class="sxs-lookup"><span data-stu-id="39e43-129">The following table summarizes the available comparison operations.</span></span>  
  
|<span data-ttu-id="39e43-130">功能</span><span class="sxs-lookup"><span data-stu-id="39e43-130">To</span></span>|<span data-ttu-id="39e43-131">查看</span><span class="sxs-lookup"><span data-stu-id="39e43-131">See</span></span>|  
|---|---|  
|<span data-ttu-id="39e43-132">确定两个值是否相等</span><span class="sxs-lookup"><span data-stu-id="39e43-132">Determine whether two values are equal</span></span>|<span data-ttu-id="39e43-133">`=` 运算符 [在 Visual Basic 中 (比较运算符](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="39e43-133">`=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="39e43-134">确定两个值是否不相等</span><span class="sxs-lookup"><span data-stu-id="39e43-134">Determine whether two values are unequal</span></span>|<span data-ttu-id="39e43-135">`<>` 运算符 [在 Visual Basic 中 (比较运算符](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="39e43-135">`<>` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="39e43-136">确定一个值是否小于另一个值</span><span class="sxs-lookup"><span data-stu-id="39e43-136">Determine whether one value is less than another</span></span>|<span data-ttu-id="39e43-137">`<` 运算符 [在 Visual Basic 中 (比较运算符](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="39e43-137">`<` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="39e43-138">确定一个值是否大于另一个值</span><span class="sxs-lookup"><span data-stu-id="39e43-138">Determine whether one value is greater than another</span></span>|<span data-ttu-id="39e43-139">`>` 运算符 [在 Visual Basic 中 (比较运算符](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="39e43-139">`>` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="39e43-140">确定一个值是否小于或等于另一个值</span><span class="sxs-lookup"><span data-stu-id="39e43-140">Determine whether one value is less than or equal to another</span></span>|<span data-ttu-id="39e43-141">`<=` 运算符 [在 Visual Basic 中 (比较运算符](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="39e43-141">`<=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="39e43-142">确定一个值是否大于或等于另一个值</span><span class="sxs-lookup"><span data-stu-id="39e43-142">Determine whether one value is greater than or equal to another</span></span>|<span data-ttu-id="39e43-143">`>=` 运算符 [在 Visual Basic 中 (比较运算符](comparison-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="39e43-143">`>=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="39e43-144">确定两个对象变量是否引用相同的对象实例</span><span class="sxs-lookup"><span data-stu-id="39e43-144">Determine whether two object variables refer to the same object instance</span></span>|[<span data-ttu-id="39e43-145">Is 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-145">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)|  
|<span data-ttu-id="39e43-146">确定两个对象变量是否引用不同的对象实例</span><span class="sxs-lookup"><span data-stu-id="39e43-146">Determine whether two object variables refer to different object instances</span></span>|[<span data-ttu-id="39e43-147">IsNot 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-147">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)|  
|<span data-ttu-id="39e43-148">确定对象是否为特定类型</span><span class="sxs-lookup"><span data-stu-id="39e43-148">Determine whether an object is of a specific type</span></span>|[<span data-ttu-id="39e43-149">TypeOf 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-149">TypeOf Operator</span></span>](../../../language-reference/operators/typeof-operator.md)|  
  
## <a name="concatenation-tasks"></a><span data-ttu-id="39e43-150">串联任务</span><span class="sxs-lookup"><span data-stu-id="39e43-150">Concatenation Tasks</span></span>  

 <span data-ttu-id="39e43-151">下表总结了可用的串联运算。</span><span class="sxs-lookup"><span data-stu-id="39e43-151">The following table summarizes the available concatenation operations.</span></span>  
  
|<span data-ttu-id="39e43-152">功能</span><span class="sxs-lookup"><span data-stu-id="39e43-152">To</span></span>|<span data-ttu-id="39e43-153">查看</span><span class="sxs-lookup"><span data-stu-id="39e43-153">See</span></span>|  
|---|---|  
|<span data-ttu-id="39e43-154">将多个字符串联接为一个字符串</span><span class="sxs-lookup"><span data-stu-id="39e43-154">Join multiple strings into a single string</span></span>|<span data-ttu-id="39e43-155">`&` 运算符 [在 Visual Basic 中 (串联运算符](concatenation-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="39e43-155">`&` Operator ([Concatenation Operators in Visual Basic](concatenation-operators.md))</span></span>|  
|<span data-ttu-id="39e43-156">用字符串值联接数值</span><span class="sxs-lookup"><span data-stu-id="39e43-156">Join numeric values with string values</span></span>|<span data-ttu-id="39e43-157">`+` 运算符 [在 Visual Basic 中 (串联运算符](concatenation-operators.md)) </span><span class="sxs-lookup"><span data-stu-id="39e43-157">`+` Operator ([Concatenation Operators in Visual Basic](concatenation-operators.md))</span></span>|  
  
## <a name="logical-and-bitwise-tasks"></a><span data-ttu-id="39e43-158">逻辑和按位任务</span><span class="sxs-lookup"><span data-stu-id="39e43-158">Logical and Bitwise Tasks</span></span>  

 <span data-ttu-id="39e43-159">下表总结了可用的逻辑和按位运算。</span><span class="sxs-lookup"><span data-stu-id="39e43-159">The following table summarizes the available logical and bitwise operations.</span></span>  
  
|<span data-ttu-id="39e43-160">功能</span><span class="sxs-lookup"><span data-stu-id="39e43-160">To</span></span>|<span data-ttu-id="39e43-161">查看</span><span class="sxs-lookup"><span data-stu-id="39e43-161">See</span></span>|  
|---|---|  
|<span data-ttu-id="39e43-162">对布尔值执行逻辑非运算</span><span class="sxs-lookup"><span data-stu-id="39e43-162">Perform logical negation on a Boolean value</span></span>|[<span data-ttu-id="39e43-163">Not 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-163">Not Operator</span></span>](../../../language-reference/operators/not-operator.md)|  
|<span data-ttu-id="39e43-164">对两个布尔值执行逻辑与运算</span><span class="sxs-lookup"><span data-stu-id="39e43-164">Perform logical conjunction on two Boolean values</span></span>|[<span data-ttu-id="39e43-165">And 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-165">And Operator</span></span>](../../../language-reference/operators/and-operator.md)|  
|<span data-ttu-id="39e43-166">对两个布尔值执行包含逻辑析取</span><span class="sxs-lookup"><span data-stu-id="39e43-166">Perform inclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="39e43-167">Or 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-167">Or Operator</span></span>](../../../language-reference/operators/or-operator.md)|  
|<span data-ttu-id="39e43-168">对两个布尔值执行独占逻辑析取</span><span class="sxs-lookup"><span data-stu-id="39e43-168">Perform exclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="39e43-169">Xor 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-169">Xor Operator</span></span>](../../../language-reference/operators/xor-operator.md)|  
|<span data-ttu-id="39e43-170">对两个布尔值执行短路逻辑与运算</span><span class="sxs-lookup"><span data-stu-id="39e43-170">Perform short-circuited logical conjunction on two Boolean values</span></span>|[<span data-ttu-id="39e43-171">AndAlso 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-171">AndAlso Operator</span></span>](../../../language-reference/operators/andalso-operator.md)|  
|<span data-ttu-id="39e43-172">对两个布尔值执行短路包含逻辑析取</span><span class="sxs-lookup"><span data-stu-id="39e43-172">Perform short-circuited inclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="39e43-173">OrElse 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-173">OrElse Operator</span></span>](../../../language-reference/operators/orelse-operator.md)|  
|<span data-ttu-id="39e43-174">对两个整数值执行按位逻辑与运算</span><span class="sxs-lookup"><span data-stu-id="39e43-174">Perform bit-by-bit logical conjunction on two integral values</span></span>|[<span data-ttu-id="39e43-175">And 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-175">And Operator</span></span>](../../../language-reference/operators/and-operator.md)|  
|<span data-ttu-id="39e43-176">对两个整数值执行逐位包含逻辑析取</span><span class="sxs-lookup"><span data-stu-id="39e43-176">Perform bit-by-bit inclusive logical disjunction on two integral values</span></span>|[<span data-ttu-id="39e43-177">Or 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-177">Or Operator</span></span>](../../../language-reference/operators/or-operator.md)|  
|<span data-ttu-id="39e43-178">对两个整数值执行按位异或逻辑析取</span><span class="sxs-lookup"><span data-stu-id="39e43-178">Perform bit-by-bit exclusive logical disjunction on two integral values</span></span>|[<span data-ttu-id="39e43-179">Xor 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-179">Xor Operator</span></span>](../../../language-reference/operators/xor-operator.md)|  
|<span data-ttu-id="39e43-180">对整数值执行按位逻辑求反</span><span class="sxs-lookup"><span data-stu-id="39e43-180">Perform bit-by-bit logical negation on an integral value</span></span>|[<span data-ttu-id="39e43-181">Not 运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-181">Not Operator</span></span>](../../../language-reference/operators/not-operator.md)|  
  
## <a name="see-also"></a><span data-ttu-id="39e43-182">请参阅</span><span class="sxs-lookup"><span data-stu-id="39e43-182">See also</span></span>

- [<span data-ttu-id="39e43-183">运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="39e43-183">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="39e43-184">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="39e43-184">Operators Listed by Functionality</span></span>](../../../language-reference/operators/operators-listed-by-functionality.md)
