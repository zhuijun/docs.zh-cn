---
title: Widening
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 14e0b026f4fc3b0bf202ea643a28d6f1a7df2b7c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867651"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="915b4-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="915b4-102">Widening (Visual Basic)</span></span>

<span data-ttu-id="915b4-103">指示转换运算符 (`CType`) 将类或结构转换为可以保存原始类或结构的所有可能值的类型。</span><span class="sxs-lookup"><span data-stu-id="915b4-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="915b4-104">用扩大关键字转换</span><span class="sxs-lookup"><span data-stu-id="915b4-104">Converting with the Widening Keyword</span></span>  

 <span data-ttu-id="915b4-105">除了之外，转换过程必须指定 `Public Shared` `Widening` 。</span><span class="sxs-lookup"><span data-stu-id="915b4-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="915b4-106">扩大转换始终会在运行时成功，不会导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="915b4-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="915b4-107">示例包括 `Single` 对 `Double` `Char` `String` 其基类型的、向和派生的类型。</span><span class="sxs-lookup"><span data-stu-id="915b4-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="915b4-108">由于派生类型包含基类型的所有成员，因此是最新的转换，因此是基类型的实例。</span><span class="sxs-lookup"><span data-stu-id="915b4-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="915b4-109">使用代码不必使用 `CType` 进行扩大转换，即使 `Option Strict` 是 `On` 。</span><span class="sxs-lookup"><span data-stu-id="915b4-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="915b4-110">`Widening`关键字可以在此上下文中使用：</span><span class="sxs-lookup"><span data-stu-id="915b4-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="915b4-111">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="915b4-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="915b4-112">有关扩展和收缩转换运算符的定义示例，请参阅 [如何：定义转换运算符](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="915b4-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915b4-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="915b4-113">See also</span></span>

- [<span data-ttu-id="915b4-114">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="915b4-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="915b4-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="915b4-115">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="915b4-116">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="915b4-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="915b4-117">如何：定义运算符</span><span class="sxs-lookup"><span data-stu-id="915b4-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="915b4-118">CType Function</span><span class="sxs-lookup"><span data-stu-id="915b4-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="915b4-119">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="915b4-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="915b4-120">如何：定义转换运算符</span><span class="sxs-lookup"><span data-stu-id="915b4-120">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
