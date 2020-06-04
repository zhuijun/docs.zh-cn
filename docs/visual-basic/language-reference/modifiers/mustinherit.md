---
title: MustInherit
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 84df7a5cfdad3b5bc6764675725a5d0cb402b0b7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396202"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="5df88-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5df88-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="5df88-103">指定类只能用作基类，并且不能直接从其创建对象。</span><span class="sxs-lookup"><span data-stu-id="5df88-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5df88-104">备注</span><span class="sxs-lookup"><span data-stu-id="5df88-104">Remarks</span></span>  
 <span data-ttu-id="5df88-105">*基类*（也称为*抽象类*）的目的是定义从其派生的所有类所共有的功能。</span><span class="sxs-lookup"><span data-stu-id="5df88-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="5df88-106">这会保存派生类，使其不必重新定义公共元素。</span><span class="sxs-lookup"><span data-stu-id="5df88-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="5df88-107">在某些情况下，这种通用功能不够完整，无法生成可用的对象，并且每个派生类都定义了缺少的功能。</span><span class="sxs-lookup"><span data-stu-id="5df88-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="5df88-108">在这种情况下，你希望使用代码仅在派生类中创建对象。</span><span class="sxs-lookup"><span data-stu-id="5df88-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="5df88-109">在 `MustInherit` 基类上使用可以强制执行此类。</span><span class="sxs-lookup"><span data-stu-id="5df88-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="5df88-110">类的另一种用法 `MustInherit` 是将变量限制为一组相关的类。</span><span class="sxs-lookup"><span data-stu-id="5df88-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="5df88-111">你可以定义一个基类，并从其派生所有这些相关的类。</span><span class="sxs-lookup"><span data-stu-id="5df88-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="5df88-112">基类不需要提供所有派生类共有的任何功能，但它可以充当用于向变量赋值的筛选器。</span><span class="sxs-lookup"><span data-stu-id="5df88-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="5df88-113">如果你使用的代码将变量声明为基类，则 Visual Basic 允许你仅将一个派生类中的对象分配给该变量。</span><span class="sxs-lookup"><span data-stu-id="5df88-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="5df88-114">.NET Framework 定义了多个类，其中包括、 `MustInherit` <xref:System.Array> <xref:System.Enum> 和 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="5df88-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="5df88-115"><xref:System.ValueType>是限制变量的基类的一个示例。</span><span class="sxs-lookup"><span data-stu-id="5df88-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="5df88-116">所有值类型都是从派生的 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="5df88-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="5df88-117">如果将变量声明为 <xref:System.ValueType> ，则只能将值类型分配给该变量。</span><span class="sxs-lookup"><span data-stu-id="5df88-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5df88-118">规则</span><span class="sxs-lookup"><span data-stu-id="5df88-118">Rules</span></span>  
  
- <span data-ttu-id="5df88-119">**声明上下文。**</span><span class="sxs-lookup"><span data-stu-id="5df88-119">**Declaration Context.**</span></span> <span data-ttu-id="5df88-120">`MustInherit`只能在语句中使用 `Class` 。</span><span class="sxs-lookup"><span data-stu-id="5df88-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
- <span data-ttu-id="5df88-121">**组合修饰符。**</span><span class="sxs-lookup"><span data-stu-id="5df88-121">**Combined Modifiers.**</span></span> <span data-ttu-id="5df88-122">不能 `MustInherit` `NotInheritable` 在同一声明中同时指定和。</span><span class="sxs-lookup"><span data-stu-id="5df88-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5df88-123">示例</span><span class="sxs-lookup"><span data-stu-id="5df88-123">Example</span></span>  
 <span data-ttu-id="5df88-124">下面的示例演示强制的继承和强制重写。</span><span class="sxs-lookup"><span data-stu-id="5df88-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="5df88-125">基类 `shape` 定义变量 `acrossLine` 。</span><span class="sxs-lookup"><span data-stu-id="5df88-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="5df88-126">类 `circle` 和 `square` 派生自 `shape` 。</span><span class="sxs-lookup"><span data-stu-id="5df88-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="5df88-127">它们继承的定义 `acrossLine` ，但必须定义函数， `area` 因为每种形状的计算都是不同的。</span><span class="sxs-lookup"><span data-stu-id="5df88-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="5df88-128">可以 `shape1` 将和声明 `shape2` 为类型 `shape` 。</span><span class="sxs-lookup"><span data-stu-id="5df88-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="5df88-129">但是，不能从创建对象， `shape` 因为它缺少函数的功能 `area` ，并被标记为 `MustInherit` 。</span><span class="sxs-lookup"><span data-stu-id="5df88-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="5df88-130">由于它们被声明为 `shape` ，因此，变量 `shape1` 和 `shape2` 仅限于派生类和中的 `circle` 对象 `square` 。</span><span class="sxs-lookup"><span data-stu-id="5df88-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="5df88-131">Visual Basic 不允许将任何其他对象分配给这些变量，这为你提供了高级别的类型安全性。</span><span class="sxs-lookup"><span data-stu-id="5df88-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="5df88-132">用法</span><span class="sxs-lookup"><span data-stu-id="5df88-132">Usage</span></span>  
 <span data-ttu-id="5df88-133">`MustInherit`可以在此上下文中使用修饰符：</span><span class="sxs-lookup"><span data-stu-id="5df88-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="5df88-134">Class 语句</span><span class="sxs-lookup"><span data-stu-id="5df88-134">Class Statement</span></span>](../statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5df88-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5df88-135">See also</span></span>

- [<span data-ttu-id="5df88-136">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="5df88-136">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="5df88-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="5df88-137">NotInheritable</span></span>](notinheritable.md)
- [<span data-ttu-id="5df88-138">关键字</span><span class="sxs-lookup"><span data-stu-id="5df88-138">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="5df88-139">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="5df88-139">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
