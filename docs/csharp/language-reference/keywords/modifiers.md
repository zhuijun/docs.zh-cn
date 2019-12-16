---
title: "修饰符（C# 参考）"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- keywords [C#], modifiers
- modifiers [C#]
ms.assetid: c96691dd-b357-49ec-b5ae-03ca214fadfb
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e2e7e5e3907ac9bb66676e749ddd55a8ac4836c
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="modifiers-c-reference"></a><span data-ttu-id="30b68-102">修饰符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="30b68-102">Modifiers (C# Reference)</span></span>
<span data-ttu-id="30b68-103">修饰符用于修改类型和类型成员的声明。</span><span class="sxs-lookup"><span data-stu-id="30b68-103">Modifiers are used to modify declarations of types and type members.</span></span> <span data-ttu-id="30b68-104">本节介绍 C# 修饰符。</span><span class="sxs-lookup"><span data-stu-id="30b68-104">This section introduces the C# modifiers.</span></span>  
  
|<span data-ttu-id="30b68-105">修饰符</span><span class="sxs-lookup"><span data-stu-id="30b68-105">Modifier</span></span>|<span data-ttu-id="30b68-106">目标</span><span class="sxs-lookup"><span data-stu-id="30b68-106">Purpose</span></span>|  
|--------------|-------------|  
|[<span data-ttu-id="30b68-107">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="30b68-107">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)<br /><br /> <span data-ttu-id="30b68-108">-   [public](../../../csharp/language-reference/keywords/public.md)</span><span class="sxs-lookup"><span data-stu-id="30b68-108">-   [public](../../../csharp/language-reference/keywords/public.md)</span></span><br /><span data-ttu-id="30b68-109">-   [private](../../../csharp/language-reference/keywords/private.md)</span><span class="sxs-lookup"><span data-stu-id="30b68-109">-   [private](../../../csharp/language-reference/keywords/private.md)</span></span><br /><span data-ttu-id="30b68-110">-   [internal](../../../csharp/language-reference/keywords/internal.md)</span><span class="sxs-lookup"><span data-stu-id="30b68-110">-   [internal](../../../csharp/language-reference/keywords/internal.md)</span></span><br /><span data-ttu-id="30b68-111">-   [protected](../../../csharp/language-reference/keywords/protected.md)</span><span class="sxs-lookup"><span data-stu-id="30b68-111">-   [protected](../../../csharp/language-reference/keywords/protected.md)</span></span>|<span data-ttu-id="30b68-112">指定声明的类型和类型成员的可访问性。</span><span class="sxs-lookup"><span data-stu-id="30b68-112">Specifies the declared accessibility of types and type members.</span></span>|  
|[<span data-ttu-id="30b68-113">abstract</span><span class="sxs-lookup"><span data-stu-id="30b68-113">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="30b68-114">指示某个类只能是其他类的基类。</span><span class="sxs-lookup"><span data-stu-id="30b68-114">Indicates that a class is intended only to be a base class of other classes.</span></span>|  
|[<span data-ttu-id="30b68-115">async</span><span class="sxs-lookup"><span data-stu-id="30b68-115">async</span></span>](../../../csharp/language-reference/keywords/async.md)|<span data-ttu-id="30b68-116">指示修改后的方法、lambda 表达式或匿名方法是异步的。</span><span class="sxs-lookup"><span data-stu-id="30b68-116">Indicates that the modified method, lambda expression, or anonymous method is asynchronous.</span></span>|  
|[<span data-ttu-id="30b68-117">const</span><span class="sxs-lookup"><span data-stu-id="30b68-117">const</span></span>](../../../csharp/language-reference/keywords/const.md)|<span data-ttu-id="30b68-118">指定无法修改字段或局部变量的值。</span><span class="sxs-lookup"><span data-stu-id="30b68-118">Specifies that the value of the field or the local variable cannot be modified.</span></span>|  
|[<span data-ttu-id="30b68-119">事件</span><span class="sxs-lookup"><span data-stu-id="30b68-119">event</span></span>](../../../csharp/language-reference/keywords/event.md)|<span data-ttu-id="30b68-120">声明事件。</span><span class="sxs-lookup"><span data-stu-id="30b68-120">Declares an event.</span></span>|  
|[<span data-ttu-id="30b68-121">extern</span><span class="sxs-lookup"><span data-stu-id="30b68-121">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)|<span data-ttu-id="30b68-122">指示在外部实现方法。</span><span class="sxs-lookup"><span data-stu-id="30b68-122">Indicates that the method is implemented externally.</span></span>|  
|[<span data-ttu-id="30b68-123">new</span><span class="sxs-lookup"><span data-stu-id="30b68-123">new</span></span>](../../../csharp/language-reference/keywords/new.md)|<span data-ttu-id="30b68-124">显式隐藏继承自基类的成员。</span><span class="sxs-lookup"><span data-stu-id="30b68-124">Explicitly hides a member inherited from a base class.</span></span>|  
|[<span data-ttu-id="30b68-125">替代</span><span class="sxs-lookup"><span data-stu-id="30b68-125">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="30b68-126">提供从基类继承的虚拟成员的新实现。</span><span class="sxs-lookup"><span data-stu-id="30b68-126">Provides a new implementation of a virtual member inherited from a base class.</span></span>|  
|[<span data-ttu-id="30b68-127">partial</span><span class="sxs-lookup"><span data-stu-id="30b68-127">partial</span></span>](../../../csharp/language-reference/keywords/partial-type.md)|<span data-ttu-id="30b68-128">在同一程序集中定义分部类、结构和方法。</span><span class="sxs-lookup"><span data-stu-id="30b68-128">Defines partial classes, structs and methods throughout the same assembly.</span></span>|  
|[<span data-ttu-id="30b68-129">只读</span><span class="sxs-lookup"><span data-stu-id="30b68-129">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)|<span data-ttu-id="30b68-130">声明一个字段，该字段只能赋值为该声明的一部分或者在同一个类的构造函数中。</span><span class="sxs-lookup"><span data-stu-id="30b68-130">Declares a field that can only be assigned values as part of the declaration or in a constructor in the same class.</span></span>|  
|[<span data-ttu-id="30b68-131">sealed</span><span class="sxs-lookup"><span data-stu-id="30b68-131">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)|<span data-ttu-id="30b68-132">指定无法继承类。</span><span class="sxs-lookup"><span data-stu-id="30b68-132">Specifies that a class cannot be inherited.</span></span>|  
|[<span data-ttu-id="30b68-133">static</span><span class="sxs-lookup"><span data-stu-id="30b68-133">static</span></span>](../../../csharp/language-reference/keywords/static.md)|<span data-ttu-id="30b68-134">声明属于类型本身而不是特定对象的成员。</span><span class="sxs-lookup"><span data-stu-id="30b68-134">Declares a member that belongs to the type itself instead of to a specific object.</span></span>|  
|[<span data-ttu-id="30b68-135">unsafe</span><span class="sxs-lookup"><span data-stu-id="30b68-135">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)|<span data-ttu-id="30b68-136">声明不安全的上下文。</span><span class="sxs-lookup"><span data-stu-id="30b68-136">Declares an unsafe context.</span></span>|  
|[<span data-ttu-id="30b68-137">virtual</span><span class="sxs-lookup"><span data-stu-id="30b68-137">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="30b68-138">在派生类中声明其实现可由重写成员更改的方法或访问器。</span><span class="sxs-lookup"><span data-stu-id="30b68-138">Declares a method or an accessor whose implementation can be changed by an overriding member in a derived class.</span></span>|  
|[<span data-ttu-id="30b68-139">volatile</span><span class="sxs-lookup"><span data-stu-id="30b68-139">volatile</span></span>](../../../csharp/language-reference/keywords/volatile.md)|<span data-ttu-id="30b68-140">指示字段可在程序中由操作系统、硬件或并发执行线程等项修改。</span><span class="sxs-lookup"><span data-stu-id="30b68-140">Indicates that a field can be modified in the program by something such as the operating system, the hardware, or a concurrently executing thread.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30b68-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30b68-141">See Also</span></span>  
 <span data-ttu-id="30b68-142">[C# 参考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="30b68-142">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="30b68-143">[C# 编程指南](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="30b68-143">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="30b68-144">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="30b68-144">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
