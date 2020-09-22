---
title: 派生的数学函数
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: f84b1ef18ef2a924bb2e47da85ecbb51f982873a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869027"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="40ec3-102">派生的数学函数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40ec3-102">Derived Math Functions (Visual Basic)</span></span>

<span data-ttu-id="40ec3-103">下表显示了可以从对象的内部数学函数派生的非内部数学函数 <xref:System.Math?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="40ec3-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="40ec3-104">您可以通过将添加 `Imports System.Math` 到您的文件或项目来访问内部数学函数。</span><span class="sxs-lookup"><span data-stu-id="40ec3-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="40ec3-105">函数</span><span class="sxs-lookup"><span data-stu-id="40ec3-105">Function</span></span>|<span data-ttu-id="40ec3-106">派生等效项</span><span class="sxs-lookup"><span data-stu-id="40ec3-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="40ec3-107">正割 (秒 (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-107">Secant (Sec(x))</span></span>|<span data-ttu-id="40ec3-108">1/Cos (x) </span><span class="sxs-lookup"><span data-stu-id="40ec3-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="40ec3-109">余割 (Csc (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="40ec3-110">1/Sin (x) </span><span class="sxs-lookup"><span data-stu-id="40ec3-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="40ec3-111">余切 (Ctan (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="40ec3-112">1/Tan (x) </span><span class="sxs-lookup"><span data-stu-id="40ec3-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="40ec3-113">反正弦 (Asin (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="40ec3-114">Atan (x/Sqrt (-x \* x + 1) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="40ec3-115">反余弦 (Acos (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="40ec3-116">Atan (-x/Sqrt (-x \* x + 1) # A3 + 2 \* Atan (1) </span><span class="sxs-lookup"><span data-stu-id="40ec3-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="40ec3-117">反割 (Asec (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="40ec3-118">2 \* Atan (1) – Atan (号 (x) /Sqrt (x \* x – 1) # A7</span><span class="sxs-lookup"><span data-stu-id="40ec3-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="40ec3-119">反向余割 (Acsc (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="40ec3-120">Atan (Sign (x) /Sqrt (x \* x – 1) # A5</span><span class="sxs-lookup"><span data-stu-id="40ec3-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="40ec3-121">反余切 (Acot (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="40ec3-122">2 \* Atan (1) -Atan (x) </span><span class="sxs-lookup"><span data-stu-id="40ec3-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="40ec3-123">双曲正弦 (Sinh (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="40ec3-124"> (Exp (x) – Exp (-x) # A5/2</span><span class="sxs-lookup"><span data-stu-id="40ec3-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="40ec3-125">双曲余弦 (Cosh (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="40ec3-126"> (Exp (x) + Exp (-x) # A5/2</span><span class="sxs-lookup"><span data-stu-id="40ec3-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="40ec3-127"> (Tanh (x 的双曲正切值) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="40ec3-128"> (Exp (x) – Exp (-x) # A5/ (Exp (x) + Exp (-x) # A11</span><span class="sxs-lookup"><span data-stu-id="40ec3-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="40ec3-129">双曲正则 (Sech (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="40ec3-130">2/ (Exp (x) + Exp (-x) # A5</span><span class="sxs-lookup"><span data-stu-id="40ec3-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="40ec3-131">双曲余割 (Csch (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="40ec3-132">2/ (Exp (x) – Exp (-x) # A5</span><span class="sxs-lookup"><span data-stu-id="40ec3-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="40ec3-133">双曲余切 (Coth (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="40ec3-134"> (Exp (x) + Exp (-x) # A5/ (Exp (x) – Exp (-x) # A11</span><span class="sxs-lookup"><span data-stu-id="40ec3-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="40ec3-135">反双曲正弦 (Asinh (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="40ec3-136">记录 (x + Sqrt (x \* x + 1) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="40ec3-137">反双曲余弦 (Acosh (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="40ec3-138">记录 (x + Sqrt (x \* x – 1) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="40ec3-139">反双曲正切值 (Atanh (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="40ec3-140">日志 ( # B1 1 + x) / (1 – x) # A5/2</span><span class="sxs-lookup"><span data-stu-id="40ec3-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="40ec3-141">反双曲正割 (AsecH (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="40ec3-142">日志 ( # B1 Sqrt (-x \* x + 1) + 1) /x) </span><span class="sxs-lookup"><span data-stu-id="40ec3-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="40ec3-143">反双曲余割 (Acsch (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="40ec3-144">日志 ( # B1 Sign (x) \* Sqrt (x \* x + 1) + 1) /x) </span><span class="sxs-lookup"><span data-stu-id="40ec3-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="40ec3-145">反双曲余切 (Acoth (x) # A3</span><span class="sxs-lookup"><span data-stu-id="40ec3-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="40ec3-146">日志 ( # B1 x + 1) / (x – 1) # A5/2</span><span class="sxs-lookup"><span data-stu-id="40ec3-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40ec3-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40ec3-147">See also</span></span>

- [<span data-ttu-id="40ec3-148">数学函数</span><span class="sxs-lookup"><span data-stu-id="40ec3-148">Math Functions</span></span>](../functions/math-functions.md)
