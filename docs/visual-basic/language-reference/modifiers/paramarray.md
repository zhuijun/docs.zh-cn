---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: e3c24818ea87884a0dd9b42c604e13e16ca6d3d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391815"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="09443-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09443-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="09443-103">指定过程参数采用指定类型的可选元素数组。</span><span class="sxs-lookup"><span data-stu-id="09443-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="09443-104">`ParamArray`只能在参数列表的最后一个参数上使用。</span><span class="sxs-lookup"><span data-stu-id="09443-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09443-105">备注</span><span class="sxs-lookup"><span data-stu-id="09443-105">Remarks</span></span>  
 <span data-ttu-id="09443-106">`ParamArray`允许将任意数量的参数传递给过程。</span><span class="sxs-lookup"><span data-stu-id="09443-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="09443-107">`ParamArray`始终使用[ByVal](byval.md)声明参数。</span><span class="sxs-lookup"><span data-stu-id="09443-107">A `ParamArray` parameter is always declared using [ByVal](byval.md).</span></span>  
  
 <span data-ttu-id="09443-108">可以通过以下方式向参数提供一个或多个参数 `ParamArray` ：传递适当数据类型的数组、以逗号分隔的值列表，或根本不提供任何参数。</span><span class="sxs-lookup"><span data-stu-id="09443-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="09443-109">有关详细信息，请参阅[参数数组](../../programming-guide/language-features/procedures/parameter-arrays.md)中的 "调用 ParamArray"。</span><span class="sxs-lookup"><span data-stu-id="09443-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="09443-110">无论何时处理可能会无限大的阵列，都有 overrunning 应用程序的一些内部容量的风险。</span><span class="sxs-lookup"><span data-stu-id="09443-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="09443-111">如果接受来自调用代码的参数数组，则应测试其长度，如果应用程序太大，则应采取适当的措施。</span><span class="sxs-lookup"><span data-stu-id="09443-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="09443-112">`ParamArray` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="09443-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="09443-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="09443-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="09443-114">Function 语句</span><span class="sxs-lookup"><span data-stu-id="09443-114">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="09443-115">Property Statement</span><span class="sxs-lookup"><span data-stu-id="09443-115">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="09443-116">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="09443-116">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="09443-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09443-117">See also</span></span>

- [<span data-ttu-id="09443-118">关键字</span><span class="sxs-lookup"><span data-stu-id="09443-118">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="09443-119">参数数组</span><span class="sxs-lookup"><span data-stu-id="09443-119">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
