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
# <a name="derived-math-functions-visual-basic"></a>派生的数学函数 (Visual Basic)
下表显示了可以从对象的内部数学函数派生的非内部数学函数 <xref:System.Math?displayProperty=nameWithType> 。 您可以通过将添加 `Imports System.Math` 到您的文件或项目来访问内部数学函数。  
  
|函数|派生等效项|  
|--------------|-------------------------|  
|正割（秒（x））|1/Cos （x）|  
|余割（Csc （x））|1/Sin （x）|  
|余切（Ctan （x））|1/Tan （x）|  
|反正弦值（Asin （x））|Atan （x/Sqrt （-x * x + 1））|  
|反余弦（Acos （x））|Atan （-x/Sqrt （-x * x + 1）） + 2 \* Atan （1）|  
|反正割（Asec （x））|2 * Atan （1）– Atan （Sign （x）/Sqrt （x \* x –1））|  
|反余割（Acsc （x））|Atan （Sign （x）/Sqrt （x * x –1））|  
|反余切（Acot （x））|2 * Atan （1）-Atan （x）|  
|双曲正弦值（Sinh （x））|（Exp （x）– Exp （-x））/2|  
|双曲余弦值（Cosh （x））|（Exp （x） + Exp （-x））/2|  
|双曲正切值（Tanh （x））|（Exp （x）– Exp （-x））/（Exp （x） + Exp （-x））|  
|双曲正割（Sech （x））|2/（Exp （x） + Exp （-x））|  
|双曲余割（Csch （x））|2/（Exp （x）– Exp （-x））|  
|双曲余切（Coth （x））|（Exp （x） + Exp （-x））/（Exp （x）– Exp （-x））|  
|反双曲正弦值（Asinh （x））|Log （x + Sqrt （x * x + 1））|  
|反双曲余弦（Acosh （x））|Log （x + Sqrt （x * x –1））|  
|反双曲正切值（Atanh （x））|Log （（1 + x）/（1– x））/2|  
|反双曲正割（AsecH （x））|Log （（Sqrt （-x * x + 1） + 1）/x）|  
|反双曲余割（Acsch （x））|Log （（Sign （x） * Sqrt （x \* x + 1） + 1）/x）|  
|反双曲余切（Acoth （x））|Log （（x + 1）/（x –1））/2|  
  
## <a name="see-also"></a>另请参阅

- [数学函数](../functions/math-functions.md)
