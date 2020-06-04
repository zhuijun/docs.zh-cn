---
title: 常量和枚举
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- Visual Basic code, constants
- constants [Visual Basic]
- object libraries, Object Browser
- Visual Basic code, enumerations
- declaring constants [Visual Basic], enumerations
- naming conventions [Visual Basic], constants
- Visual Basic code, improving readability with constants
ms.assetid: c8aba36e-fa47-4a33-8b68-cb2009218270
ms.openlocfilehash: 7d15c46c0f6bb00c23dd98e464f61a5f94b0773a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414397"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="64d37-102">Visual Basic 中的常量和枚举</span><span class="sxs-lookup"><span data-stu-id="64d37-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="64d37-103">常量是使用有意义的名称代替不会发生更改的值的方法。</span><span class="sxs-lookup"><span data-stu-id="64d37-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="64d37-104">顾名思义，常量存储在应用程序的执行过程中保持不变的值。</span><span class="sxs-lookup"><span data-stu-id="64d37-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="64d37-105">可以使用常量提供有意义的名称（而非数字），提高代码的可读性。</span><span class="sxs-lookup"><span data-stu-id="64d37-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="64d37-106">枚举提供了使用相关常量集以及将常量值与名称相关联的一个便捷方法。</span><span class="sxs-lookup"><span data-stu-id="64d37-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="64d37-107">例如，可以为一组与星期几相关联的整数常量声明一个枚举，然后在代码中使用星期几的名称而不是整数值。</span><span class="sxs-lookup"><span data-stu-id="64d37-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64d37-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="64d37-108">In This Section</span></span>  
  
|<span data-ttu-id="64d37-109">术语</span><span class="sxs-lookup"><span data-stu-id="64d37-109">Term</span></span>|<span data-ttu-id="64d37-110">定义</span><span class="sxs-lookup"><span data-stu-id="64d37-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="64d37-111">常量概述</span><span class="sxs-lookup"><span data-stu-id="64d37-111">Constants Overview</span></span>](constants-overview.md)|<span data-ttu-id="64d37-112">本节中的主题介绍常量及其用法。</span><span class="sxs-lookup"><span data-stu-id="64d37-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="64d37-113">枚举概述</span><span class="sxs-lookup"><span data-stu-id="64d37-113">Enumerations Overview</span></span>](enumerations-overview.md)|<span data-ttu-id="64d37-114">本节中的主题介绍枚举及其用法。</span><span class="sxs-lookup"><span data-stu-id="64d37-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="64d37-115">相关章节</span><span class="sxs-lookup"><span data-stu-id="64d37-115">Related Sections</span></span>  
  
|<span data-ttu-id="64d37-116">术语</span><span class="sxs-lookup"><span data-stu-id="64d37-116">Term</span></span>|<span data-ttu-id="64d37-117">定义</span><span class="sxs-lookup"><span data-stu-id="64d37-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="64d37-118">Const 语句</span><span class="sxs-lookup"><span data-stu-id="64d37-118">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)|<span data-ttu-id="64d37-119">介绍用于声明常量的 `Const` 语句。</span><span class="sxs-lookup"><span data-stu-id="64d37-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="64d37-120">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="64d37-120">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)|<span data-ttu-id="64d37-121">介绍用于创建枚举的 `Enum` 语句。</span><span class="sxs-lookup"><span data-stu-id="64d37-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="64d37-122">Option Explicit 语句</span><span class="sxs-lookup"><span data-stu-id="64d37-122">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="64d37-123">介绍在模块级使用的 `Option Explicit` 语句，该语句强制显式声明该模块中的所有变量。</span><span class="sxs-lookup"><span data-stu-id="64d37-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="64d37-124">Option Infer 语句</span><span class="sxs-lookup"><span data-stu-id="64d37-124">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)|<span data-ttu-id="64d37-125">介绍 `Option Infer` 语句，该语句允许在声明变量时使用本地类型推断。</span><span class="sxs-lookup"><span data-stu-id="64d37-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="64d37-126">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="64d37-126">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)|<span data-ttu-id="64d37-127">介绍 `Option Strict` 语句，该语句将隐式数据类型转换限制为仅进行扩大转换，禁止后期绑定，并且禁止导致 `Object` 类型的隐式类型化。</span><span class="sxs-lookup"><span data-stu-id="64d37-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
