---
title: 类型转换
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
ms.openlocfilehash: ee8700ea757cee9c20e2598de029f54ae33a7114
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090152"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="9a7b3-102">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="9a7b3-102">Type Conversions in Visual Basic</span></span>

<span data-ttu-id="9a7b3-103">将值从一种数据类型更改为另一种类型的过程称为 *转换*。</span><span class="sxs-lookup"><span data-stu-id="9a7b3-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="9a7b3-104">转换可以是 *扩大* 或 *收缩*转换，具体取决于所涉及的类型的数据容量。</span><span class="sxs-lookup"><span data-stu-id="9a7b3-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="9a7b3-105">它们也是 *隐式* 或 *显式*的，具体取决于源代码中的语法。</span><span class="sxs-lookup"><span data-stu-id="9a7b3-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a7b3-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="9a7b3-106">In This Section</span></span>  

 [<span data-ttu-id="9a7b3-107">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="9a7b3-107">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)  
 <span data-ttu-id="9a7b3-108">说明按照目标类型是否可以保存数据进行分类的转换。</span><span class="sxs-lookup"><span data-stu-id="9a7b3-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="9a7b3-109">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="9a7b3-109">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)  
 <span data-ttu-id="9a7b3-110">讨论 Visual Basic 自动执行这些转换的分类转换。</span><span class="sxs-lookup"><span data-stu-id="9a7b3-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="9a7b3-111">字符串和其他类型之间的转换</span><span class="sxs-lookup"><span data-stu-id="9a7b3-111">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="9a7b3-112">说明如何在字符串与数字、 `Boolean` 或日期/时间值之间进行转换。</span><span class="sxs-lookup"><span data-stu-id="9a7b3-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="9a7b3-113">如何：在 Visual Basic 中将一个对象转换为其他类型</span><span class="sxs-lookup"><span data-stu-id="9a7b3-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="9a7b3-114">说明如何将变量转换 `Object` 为任何其他数据类型。</span><span class="sxs-lookup"><span data-stu-id="9a7b3-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="9a7b3-115">数组转换</span><span class="sxs-lookup"><span data-stu-id="9a7b3-115">Array Conversions</span></span>](array-conversions.md)  
 <span data-ttu-id="9a7b3-116">逐步介绍在不同数据类型的数组之间进行转换的过程。</span><span class="sxs-lookup"><span data-stu-id="9a7b3-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a7b3-117">相关章节</span><span class="sxs-lookup"><span data-stu-id="9a7b3-117">Related Sections</span></span>  

 [<span data-ttu-id="9a7b3-118">数据类型</span><span class="sxs-lookup"><span data-stu-id="9a7b3-118">Data Types</span></span>](index.md)  
 <span data-ttu-id="9a7b3-119">介绍 Visual Basic 数据类型，并说明如何使用它们。</span><span class="sxs-lookup"><span data-stu-id="9a7b3-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="9a7b3-120">数据类型</span><span class="sxs-lookup"><span data-stu-id="9a7b3-120">Data Types</span></span>](../../../language-reference/data-types/index.md)  
 <span data-ttu-id="9a7b3-121">列出 Visual Basic 提供的基本数据类型。</span><span class="sxs-lookup"><span data-stu-id="9a7b3-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="9a7b3-122">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="9a7b3-122">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)  
 <span data-ttu-id="9a7b3-123">讨论在使用数据类型时可能出现的一些常见问题。</span><span class="sxs-lookup"><span data-stu-id="9a7b3-123">Discusses some common problems that can arise when working with data types.</span></span>
