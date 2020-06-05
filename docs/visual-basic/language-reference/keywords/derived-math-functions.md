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
ms.openlocfilehash: 611f3d8faf2148b8a983467d9ace4fd6c18b30e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373873"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="d4566-102">派生的数学函数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4566-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="d4566-103">下表显示了可以从对象的内部数学函数派生的非内部数学函数 <xref:System.Math?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d4566-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="d4566-104">您可以通过将添加 `Imports System.Math` 到您的文件或项目来访问内部数学函数。</span><span class="sxs-lookup"><span data-stu-id="d4566-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="d4566-105">函数</span><span class="sxs-lookup"><span data-stu-id="d4566-105">Function</span></span>|<span data-ttu-id="d4566-106">派生等效项</span><span class="sxs-lookup"><span data-stu-id="d4566-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="d4566-107">正割（秒（x））</span><span class="sxs-lookup"><span data-stu-id="d4566-107">Secant (Sec(x))</span></span>|<span data-ttu-id="d4566-108">1/Cos （x）</span><span class="sxs-lookup"><span data-stu-id="d4566-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="d4566-109">余割（Csc （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="d4566-110">1/Sin （x）</span><span class="sxs-lookup"><span data-stu-id="d4566-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="d4566-111">余切（Ctan （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="d4566-112">1/Tan （x）</span><span class="sxs-lookup"><span data-stu-id="d4566-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="d4566-113">反正弦值（Asin （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="d4566-114">Atan （x/Sqrt （-x \* x + 1））</span><span class="sxs-lookup"><span data-stu-id="d4566-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="d4566-115">反余弦（Acos （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="d4566-116">Atan （-x/Sqrt （-x \* x + 1）） + 2 \* Atan （1）</span><span class="sxs-lookup"><span data-stu-id="d4566-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="d4566-117">反正割（Asec （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="d4566-118">2 \* Atan （1）– Atan （Sign （x）/Sqrt （x \* x –1））</span><span class="sxs-lookup"><span data-stu-id="d4566-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="d4566-119">反余割（Acsc （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="d4566-120">Atan （Sign （x）/Sqrt （x \* x –1））</span><span class="sxs-lookup"><span data-stu-id="d4566-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="d4566-121">反余切（Acot （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="d4566-122">2 \* Atan （1）-Atan （x）</span><span class="sxs-lookup"><span data-stu-id="d4566-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="d4566-123">双曲正弦值（Sinh （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="d4566-124">（Exp （x）– Exp （-x））/2</span><span class="sxs-lookup"><span data-stu-id="d4566-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="d4566-125">双曲余弦值（Cosh （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="d4566-126">（Exp （x） + Exp （-x））/2</span><span class="sxs-lookup"><span data-stu-id="d4566-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="d4566-127">双曲正切值（Tanh （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="d4566-128">（Exp （x）– Exp （-x））/（Exp （x） + Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="d4566-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="d4566-129">双曲正割（Sech （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="d4566-130">2/（Exp （x） + Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="d4566-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="d4566-131">双曲余割（Csch （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="d4566-132">2/（Exp （x）– Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="d4566-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="d4566-133">双曲余切（Coth （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="d4566-134">（Exp （x） + Exp （-x））/（Exp （x）– Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="d4566-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="d4566-135">反双曲正弦值（Asinh （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="d4566-136">Log （x + Sqrt （x \* x + 1））</span><span class="sxs-lookup"><span data-stu-id="d4566-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="d4566-137">反双曲余弦（Acosh （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="d4566-138">Log （x + Sqrt （x \* x –1））</span><span class="sxs-lookup"><span data-stu-id="d4566-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="d4566-139">反双曲正切值（Atanh （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="d4566-140">Log （（1 + x）/（1– x））/2</span><span class="sxs-lookup"><span data-stu-id="d4566-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="d4566-141">反双曲正割（AsecH （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="d4566-142">Log （（Sqrt （-x \* x + 1） + 1）/x）</span><span class="sxs-lookup"><span data-stu-id="d4566-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="d4566-143">反双曲余割（Acsch （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="d4566-144">Log （（Sign （x） \* Sqrt （x \* x + 1） + 1）/x）</span><span class="sxs-lookup"><span data-stu-id="d4566-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="d4566-145">反双曲余切（Acoth （x））</span><span class="sxs-lookup"><span data-stu-id="d4566-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="d4566-146">Log （（x + 1）/（x –1））/2</span><span class="sxs-lookup"><span data-stu-id="d4566-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4566-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4566-147">See also</span></span>

- [<span data-ttu-id="d4566-148">数学函数</span><span class="sxs-lookup"><span data-stu-id="d4566-148">Math Functions</span></span>](../functions/math-functions.md)
