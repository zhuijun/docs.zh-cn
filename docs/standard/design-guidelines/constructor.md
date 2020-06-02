---
title: 构造函数设计
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: a258bebac57258cc1e8fbe2d6b5ccce88cb28872
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280343"
---
# <a name="constructor-design"></a><span data-ttu-id="ad425-102">构造函数设计</span><span class="sxs-lookup"><span data-stu-id="ad425-102">Constructor Design</span></span>

<span data-ttu-id="ad425-103">有两种类型的构造函数：类型构造函数和实例构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="ad425-104">类型构造函数是静态的，在使用类型之前由 CLR 运行。</span><span class="sxs-lookup"><span data-stu-id="ad425-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="ad425-105">实例构造函数在创建类型的实例时运行。</span><span class="sxs-lookup"><span data-stu-id="ad425-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="ad425-106">类型构造函数不能采用任何参数。</span><span class="sxs-lookup"><span data-stu-id="ad425-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="ad425-107">实例构造函数可以。</span><span class="sxs-lookup"><span data-stu-id="ad425-107">Instance constructors can.</span></span> <span data-ttu-id="ad425-108">不采用任何参数的实例构造函数通常称为无参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="ad425-109">构造函数是创建类型的实例的最自然方式。</span><span class="sxs-lookup"><span data-stu-id="ad425-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="ad425-110">大多数开发人员会搜索并尝试使用构造函数，然后再考虑创建实例（如工厂方法）的备选方法。</span><span class="sxs-lookup"><span data-stu-id="ad425-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="ad425-111">✔️考虑提供简单、理想的默认构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="ad425-112">简单的构造函数包含非常少的参数，所有参数均为基元或枚举。</span><span class="sxs-lookup"><span data-stu-id="ad425-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="ad425-113">此类简单构造函数会提高框架的可用性。</span><span class="sxs-lookup"><span data-stu-id="ad425-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="ad425-114">如果所需操作的语义不会直接映射到新实例的构造，或者如果遵循构造函数设计准则非自然，则✔️考虑使用静态工厂方法而不是构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="ad425-115">✔️使用构造函数参数作为设置主属性的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="ad425-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="ad425-116">使用空的构造函数后跟某些属性集和使用具有多个参数的构造函数之间的语义不应存在任何差异。</span><span class="sxs-lookup"><span data-stu-id="ad425-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="ad425-117">如果构造函数参数仅用于设置属性，则✔️为构造函数参数和属性使用相同的名称。</span><span class="sxs-lookup"><span data-stu-id="ad425-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="ad425-118">此类参数和属性的唯一区别在于大小写形式。</span><span class="sxs-lookup"><span data-stu-id="ad425-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="ad425-119">✔️在构造函数中执行最少工作量。</span><span class="sxs-lookup"><span data-stu-id="ad425-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="ad425-120">除捕获构造函数参数外，构造函数不应执行太多工作。</span><span class="sxs-lookup"><span data-stu-id="ad425-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="ad425-121">任何其他处理的成本应延迟到必需的时间。</span><span class="sxs-lookup"><span data-stu-id="ad425-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="ad425-122">如果适合，✔️将从实例构造函数引发异常。</span><span class="sxs-lookup"><span data-stu-id="ad425-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="ad425-123">如果需要此类构造函数，✔️会在类中显式声明公共无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="ad425-124">如果未显式声明类型上的任何构造函数，则许多语言（如 c #）会自动添加一个公共的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="ad425-125">（抽象类获取受保护的构造函数。）</span><span class="sxs-lookup"><span data-stu-id="ad425-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="ad425-126">向类添加参数化构造函数会阻止编译器添加无参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="ad425-127">这通常会导致意外的重大更改。</span><span class="sxs-lookup"><span data-stu-id="ad425-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="ad425-128">❌避免在结构上显式定义无参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="ad425-129">这样可以更快地创建数组，因为如果没有定义无参数的构造函数，则不必在数组中的每个槽上运行它。</span><span class="sxs-lookup"><span data-stu-id="ad425-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="ad425-130">请注意，许多编译器（包括 c #）不允许结构出于此原因而提供无参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="ad425-131">❌避免在其构造函数中的对象上调用虚拟成员。</span><span class="sxs-lookup"><span data-stu-id="ad425-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="ad425-132">调用虚拟成员将导致调用最常派生的重写，即使派生程度最高的构造函数尚未完全运行也是如此。</span><span class="sxs-lookup"><span data-stu-id="ad425-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="ad425-133">类型构造函数指南</span><span class="sxs-lookup"><span data-stu-id="ad425-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="ad425-134">✔️使静态构造函数成为私有构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="ad425-135">静态构造函数（也称为类构造函数）用于初始化类型。</span><span class="sxs-lookup"><span data-stu-id="ad425-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="ad425-136">CLR 在创建该类型的第一个实例或调用该类型的任何静态成员之前调用静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="ad425-137">用户无法控制何时调用静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="ad425-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="ad425-138">如果静态构造函数不是私有，则它可由 CLR 以外的代码调用。</span><span class="sxs-lookup"><span data-stu-id="ad425-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="ad425-139">根据构造函数中执行的操作，这可能导致意外的行为。</span><span class="sxs-lookup"><span data-stu-id="ad425-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="ad425-140">C # 编译器强制静态构造函数是私有的。</span><span class="sxs-lookup"><span data-stu-id="ad425-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="ad425-141">❌不要从静态构造函数引发异常。</span><span class="sxs-lookup"><span data-stu-id="ad425-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="ad425-142">如果从类型构造函数引发异常，则类型在当前应用程序域中不可用。</span><span class="sxs-lookup"><span data-stu-id="ad425-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="ad425-143">✔️考虑以内联方式初始化静态字段，而不是显式使用静态构造函数，因为运行时能够优化没有显式定义的静态构造函数的类型的性能。</span><span class="sxs-lookup"><span data-stu-id="ad425-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="ad425-144">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="ad425-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="ad425-145">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="ad425-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ad425-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad425-146">See also</span></span>

- [<span data-ttu-id="ad425-147">成员设计准则</span><span class="sxs-lookup"><span data-stu-id="ad425-147">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="ad425-148">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="ad425-148">Framework Design Guidelines</span></span>](index.md)
