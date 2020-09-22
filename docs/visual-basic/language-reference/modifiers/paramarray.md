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
ms.openlocfilehash: baf9303101eea9eed27e8a4eee9e04d255c798e9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867830"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="65b78-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65b78-102">ParamArray (Visual Basic)</span></span>

<span data-ttu-id="65b78-103">指定过程参数采用指定类型的可选元素数组。</span><span class="sxs-lookup"><span data-stu-id="65b78-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="65b78-104">`ParamArray` 只能在参数列表的最后一个参数上使用。</span><span class="sxs-lookup"><span data-stu-id="65b78-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65b78-105">备注</span><span class="sxs-lookup"><span data-stu-id="65b78-105">Remarks</span></span>  

 <span data-ttu-id="65b78-106">`ParamArray` 允许将任意数量的参数传递给过程。</span><span class="sxs-lookup"><span data-stu-id="65b78-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="65b78-107">`ParamArray`始终使用[ByVal](byval.md)声明参数。</span><span class="sxs-lookup"><span data-stu-id="65b78-107">A `ParamArray` parameter is always declared using [ByVal](byval.md).</span></span>  
  
 <span data-ttu-id="65b78-108">可以通过以下方式向参数提供一个或多个参数 `ParamArray` ：传递适当数据类型的数组、以逗号分隔的值列表，或根本不提供任何参数。</span><span class="sxs-lookup"><span data-stu-id="65b78-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="65b78-109">有关详细信息，请参阅 [参数数组](../../programming-guide/language-features/procedures/parameter-arrays.md)中的 "调用 ParamArray"。</span><span class="sxs-lookup"><span data-stu-id="65b78-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="65b78-110">无论何时处理可能会无限大的阵列，都有 overrunning 应用程序的一些内部容量的风险。</span><span class="sxs-lookup"><span data-stu-id="65b78-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="65b78-111">如果接受来自调用代码的参数数组，则应测试其长度，如果应用程序太大，则应采取适当的措施。</span><span class="sxs-lookup"><span data-stu-id="65b78-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="65b78-112">`ParamArray` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="65b78-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="65b78-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="65b78-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="65b78-114">Function 语句</span><span class="sxs-lookup"><span data-stu-id="65b78-114">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="65b78-115">Property Statement</span><span class="sxs-lookup"><span data-stu-id="65b78-115">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="65b78-116">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="65b78-116">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="65b78-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65b78-117">See also</span></span>

- [<span data-ttu-id="65b78-118">关键字</span><span class="sxs-lookup"><span data-stu-id="65b78-118">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="65b78-119">参数数组</span><span class="sxs-lookup"><span data-stu-id="65b78-119">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
