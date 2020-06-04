---
title: 该上下文中不支持可以为 null 的类型推理
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409382"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="240a9-102">该上下文中不支持可以为 null 的类型推理</span><span class="sxs-lookup"><span data-stu-id="240a9-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="240a9-103">值类型和结构可以声明为 null。</span><span class="sxs-lookup"><span data-stu-id="240a9-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="240a9-104">但是，不能将可为 null 的声明与类型推理结合使用。</span><span class="sxs-lookup"><span data-stu-id="240a9-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="240a9-105">下面的示例将导致此错误。</span><span class="sxs-lookup"><span data-stu-id="240a9-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="240a9-106">**错误 ID：** BC36629</span><span class="sxs-lookup"><span data-stu-id="240a9-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="240a9-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="240a9-107">To correct this error</span></span>  
  
- <span data-ttu-id="240a9-108">使用 `As` 子句将变量声明为可以为 null 的值类型。</span><span class="sxs-lookup"><span data-stu-id="240a9-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="240a9-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="240a9-109">See also</span></span>

- [<span data-ttu-id="240a9-110">可以为 null 的值类型</span><span class="sxs-lookup"><span data-stu-id="240a9-110">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="240a9-111">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="240a9-111">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
