---
title: 常量概述
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: f45cb12c6ef0f90b9c90190f30ce8600fec80947
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414513"
---
# <a name="constants-overview-visual-basic"></a><span data-ttu-id="92f76-102">常量概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92f76-102">Constants Overview (Visual Basic)</span></span>
<span data-ttu-id="92f76-103">常量是有意义的名称，用来代替不会更改的数字或字符串。</span><span class="sxs-lookup"><span data-stu-id="92f76-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="92f76-104">顾名思义，常数存储值在应用程序的整个执行过程中保持不变。</span><span class="sxs-lookup"><span data-stu-id="92f76-104">Constants store values that, as the name implies, remain the same throughout the execution of an application.</span></span> <span data-ttu-id="92f76-105">您可以通过使用常量极大地提高代码的可读性并使其更易于维护。</span><span class="sxs-lookup"><span data-stu-id="92f76-105">You can greatly improve the readability of your code and make it easier to maintain by using constants.</span></span> <span data-ttu-id="92f76-106">在包含重新出现的值的代码中使用它们，或依赖于某些难以记住或没有明显含义的数字的值。</span><span class="sxs-lookup"><span data-stu-id="92f76-106">Use them in code that contains values that reappear or that depends on certain numbers that are difficult to remember or have no obvious meaning.</span></span>  
  
## <a name="how-to-create-and-use-constants"></a><span data-ttu-id="92f76-107">如何创建和使用常量</span><span class="sxs-lookup"><span data-stu-id="92f76-107">How to Create and Use Constants</span></span>  
 <span data-ttu-id="92f76-108">Visual Basic 包含许多预定义的常量，主要用于打印和显示。</span><span class="sxs-lookup"><span data-stu-id="92f76-108">Visual Basic contains a number of predefined constants, mainly using for printing and displaying.</span></span> <span data-ttu-id="92f76-109">还可以使用语句创建自己的常量 `Const` ，使用与创建变量名称相同的准则。</span><span class="sxs-lookup"><span data-stu-id="92f76-109">You can also create your own constants with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="92f76-110">如果 `Option Strict` 为 `On` ，则必须显式声明常量类型。</span><span class="sxs-lookup"><span data-stu-id="92f76-110">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
 <span data-ttu-id="92f76-111">常量的作用域，它是在不限定其名称的情况下可引用它的所有代码的集合，与在同一位置声明的变量的作用域相同。</span><span class="sxs-lookup"><span data-stu-id="92f76-111">A constant's scope, which is the set of all code that can refer to it without qualifying its name, is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="92f76-112">若要创建一个存在于特定过程范围内的常量，请在该过程中将其声明为。</span><span class="sxs-lookup"><span data-stu-id="92f76-112">To create a constant that exists within the scope of a particular procedure, declare it inside that procedure.</span></span> <span data-ttu-id="92f76-113">若要创建可在整个应用程序中使用的常数，请 `Public` 在类的声明部分使用关键字进行声明。</span><span class="sxs-lookup"><span data-stu-id="92f76-113">To create a constant that is available throughout an application, declare it using the `Public` keyword in the declarations section of the class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92f76-114">尽管常量有点类似于变量，但您不能对其进行修改，也不能为变量赋值。</span><span class="sxs-lookup"><span data-stu-id="92f76-114">Although constants somewhat resemble variables, you cannot modify them or assign new values to them as you can to variables.</span></span>  
  
 <span data-ttu-id="92f76-115">您在代码中使用的常量可以由您所使用的控件或组件的对象模型定义，也可以是用户定义的（也就是说，您自己创建的）。</span><span class="sxs-lookup"><span data-stu-id="92f76-115">The constants you use in your code can be defined by the object model for controls or components you work with, or they can be user-defined (that is, those you create yourself).</span></span>  
  
## <a name="compile-time-and-run-time-constants"></a><span data-ttu-id="92f76-116">编译时和运行时常量</span><span class="sxs-lookup"><span data-stu-id="92f76-116">Compile-time and Run-time Constants</span></span>  
 <span data-ttu-id="92f76-117">编译时常量是在编译代码时计算的，而运行时常量只能在应用程序运行时进行计算。</span><span class="sxs-lookup"><span data-stu-id="92f76-117">A compile-time constant is computed at the time the code is compiled, while a run-time constant can only be computed while the application is running.</span></span> <span data-ttu-id="92f76-118">每次应用程序运行时，编译时常量都将具有相同的值，而每次运行时常量可能会更改。</span><span class="sxs-lookup"><span data-stu-id="92f76-118">A compile-time constant will have the same value each time an application runs, while a run-time constant may change each time.</span></span> <span data-ttu-id="92f76-119">对于数组界限、case 表达式或枚举器初始值设定项等事例，编译时常量是必需的。</span><span class="sxs-lookup"><span data-stu-id="92f76-119">Compile-time constants are required for cases such as array bounds, case expressions, or enumerator initializers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92f76-120">本节内容</span><span class="sxs-lookup"><span data-stu-id="92f76-120">In This Section</span></span>  
  
|<span data-ttu-id="92f76-121">定义</span><span class="sxs-lookup"><span data-stu-id="92f76-121">Definition</span></span>|<span data-ttu-id="92f76-122">术语</span><span class="sxs-lookup"><span data-stu-id="92f76-122">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="92f76-123">如何：声明常量</span><span class="sxs-lookup"><span data-stu-id="92f76-123">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)|<span data-ttu-id="92f76-124">说明如何使用 `Const` 语句声明常量并设置其值; 通过声明常量，可为该值指定有意义的名称。</span><span class="sxs-lookup"><span data-stu-id="92f76-124">Explains how to use the `Const` statement to declare a constant and set its value; by declaring a constant, you assign a meaningful name to the value.</span></span>|  
|[<span data-ttu-id="92f76-125">用户定义常数</span><span class="sxs-lookup"><span data-stu-id="92f76-125">User-Defined Constants</span></span>](user-defined-constants.md)|<span data-ttu-id="92f76-126">介绍如何创建自己的常量，包括有关范围的信息以及如何避免循环引用。</span><span class="sxs-lookup"><span data-stu-id="92f76-126">Describes how to create your own constants, including information on scoping and how to avoid circular references.</span></span>|  
|[<span data-ttu-id="92f76-127">常数和文本数据类型</span><span class="sxs-lookup"><span data-stu-id="92f76-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)|<span data-ttu-id="92f76-128">提供有关 Visual Basic 编译器如何在关闭时初始化常量的信息 `Option Explicit` 。</span><span class="sxs-lookup"><span data-stu-id="92f76-128">Provides information on how the Visual Basic compiler initializes constants when `Option Explicit` is turned off.</span></span>|  
|[<span data-ttu-id="92f76-129">如何：将相关的常量值组合在一起</span><span class="sxs-lookup"><span data-stu-id="92f76-129">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)|<span data-ttu-id="92f76-130">演示如何对相关的常量值进行分组。</span><span class="sxs-lookup"><span data-stu-id="92f76-130">Demonstrates how to group constant values that are related.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="92f76-131">参考</span><span class="sxs-lookup"><span data-stu-id="92f76-131">Reference</span></span>  
  
|<span data-ttu-id="92f76-132">定义</span><span class="sxs-lookup"><span data-stu-id="92f76-132">Definition</span></span>|<span data-ttu-id="92f76-133">术语</span><span class="sxs-lookup"><span data-stu-id="92f76-133">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="92f76-134">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="92f76-134">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)|<span data-ttu-id="92f76-135">列出由 Visual Basic 预定义的常量。</span><span class="sxs-lookup"><span data-stu-id="92f76-135">Lists the constants predefined by Visual Basic.</span></span>|  
|[<span data-ttu-id="92f76-136">Const 语句</span><span class="sxs-lookup"><span data-stu-id="92f76-136">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)|<span data-ttu-id="92f76-137">描述 `Const` 语句及其用法。</span><span class="sxs-lookup"><span data-stu-id="92f76-137">Describes the `Const` statement and its use.</span></span>|  
|[<span data-ttu-id="92f76-138">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="92f76-138">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)|<span data-ttu-id="92f76-139">描述 `Option Strict` 语句及其用法。</span><span class="sxs-lookup"><span data-stu-id="92f76-139">Describes the `Option Strict` statement and its use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92f76-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92f76-140">See also</span></span>

- [<span data-ttu-id="92f76-141">枚举概述</span><span class="sxs-lookup"><span data-stu-id="92f76-141">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="92f76-142">如何：在 Visual Basic 中初始化数组变量</span><span class="sxs-lookup"><span data-stu-id="92f76-142">How to: Initialize an Array Variable in Visual Basic</span></span>](../arrays/how-to-initialize-an-array-variable.md)
