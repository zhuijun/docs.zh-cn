---
title: “Is”要求具有引用类型的操作数，但此操作数的值类型为“<typename>”。
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: daf9724fef81b4d7adb4f571ee950723aec09d8d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873918"
---
# <a name="is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="0a487-102">“Is”要求具有引用类型的操作数，但此操作数的值类型为“\<typename>”。</span><span class="sxs-lookup"><span data-stu-id="0a487-102">'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>

<span data-ttu-id="0a487-103">`Is`比较运算符确定两个对象变量是否引用相同的实例。</span><span class="sxs-lookup"><span data-stu-id="0a487-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="0a487-104">没有为值类型定义此比较。</span><span class="sxs-lookup"><span data-stu-id="0a487-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="0a487-105">**错误 ID：** BC30020</span><span class="sxs-lookup"><span data-stu-id="0a487-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a487-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="0a487-106">To correct this error</span></span>  
  
- <span data-ttu-id="0a487-107">使用适当的算术比较运算符或 `Like` 运算符比较两个值类型。</span><span class="sxs-lookup"><span data-stu-id="0a487-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a487-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a487-108">See also</span></span>

- [<span data-ttu-id="0a487-109">Is 运算符</span><span class="sxs-lookup"><span data-stu-id="0a487-109">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="0a487-110">Like 运算符</span><span class="sxs-lookup"><span data-stu-id="0a487-110">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="0a487-111">比较运算符</span><span class="sxs-lookup"><span data-stu-id="0a487-111">Comparison Operators</span></span>](../operators/comparison-operators.md)
