---
title: 框架设计准则
description: 请参阅框架设计准则，用于设计扩展和与 .NET 交互的库，以确保 API 一致性和易用性。
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 17998adb1d18579f6763a80a82944e742e284e4e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769062"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="6f981-103">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="6f981-103">Framework Design Guidelines</span></span>
<span data-ttu-id="6f981-104">本部分提供了有关设计扩展和与 .NET Framework 进行交互的库的指南。</span><span class="sxs-lookup"><span data-stu-id="6f981-104">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="6f981-105">其目标是通过提供与用于开发的编程语言无关的统一编程模型，来帮助库设计人员确保 API 一致性和易用性。</span><span class="sxs-lookup"><span data-stu-id="6f981-105">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="6f981-106">建议在开发扩展 .NET Framework 的类和组件时遵循这些设计指导原则。</span><span class="sxs-lookup"><span data-stu-id="6f981-106">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="6f981-107">不一致的库设计会对开发人员工作效率产生负面影响，并防止采用。</span><span class="sxs-lookup"><span data-stu-id="6f981-107">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="6f981-108">本指南被组织为简单的建议，其前缀为 `Do` 、、 `Consider` `Avoid` 和 `Do not` 。</span><span class="sxs-lookup"><span data-stu-id="6f981-108">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="6f981-109">这些准则旨在帮助类库设计人员了解不同解决方案之间的权衡。</span><span class="sxs-lookup"><span data-stu-id="6f981-109">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="6f981-110">在某些情况下，良好的库设计需要你违反这些设计准则。</span><span class="sxs-lookup"><span data-stu-id="6f981-110">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="6f981-111">这种情况应该很少见，因此您有一个清晰且引人注目的决策理由。</span><span class="sxs-lookup"><span data-stu-id="6f981-111">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="6f981-112">这些指导原则摘录内容于本书*框架设计指南：约定、惯例和模式，适用于可重复使用的 .Net 库第2版*，通过 Krzysztof Cwalina 和 Brad Abrams。</span><span class="sxs-lookup"><span data-stu-id="6f981-112">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f981-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="6f981-113">In This Section</span></span>  
 [<span data-ttu-id="6f981-114">命名准则</span><span class="sxs-lookup"><span data-stu-id="6f981-114">Naming Guidelines</span></span>](naming-guidelines.md)  
 <span data-ttu-id="6f981-115">提供用于命名类库中的程序集、命名空间、类型和成员的准则。</span><span class="sxs-lookup"><span data-stu-id="6f981-115">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="6f981-116">类型设计准则</span><span class="sxs-lookup"><span data-stu-id="6f981-116">Type Design Guidelines</span></span>](type.md)  
 <span data-ttu-id="6f981-117">提供使用静态和抽象类、接口、枚举、结构和其他类型的指导原则。</span><span class="sxs-lookup"><span data-stu-id="6f981-117">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="6f981-118">成员设计准则</span><span class="sxs-lookup"><span data-stu-id="6f981-118">Member Design Guidelines</span></span>](member.md)  
 <span data-ttu-id="6f981-119">提供设计和使用属性、方法、构造函数、字段、事件、运算符和参数的准则。</span><span class="sxs-lookup"><span data-stu-id="6f981-119">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="6f981-120">扩展性设计</span><span class="sxs-lookup"><span data-stu-id="6f981-120">Designing for Extensibility</span></span>](designing-for-extensibility.md)  
 <span data-ttu-id="6f981-121">讨论扩展性机制（如子类化、使用事件、虚拟成员和回调），并说明如何选择最能满足框架要求的机制。</span><span class="sxs-lookup"><span data-stu-id="6f981-121">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="6f981-122">异常设计准则</span><span class="sxs-lookup"><span data-stu-id="6f981-122">Design Guidelines for Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="6f981-123">介绍设计、引发和捕获异常的设计准则。</span><span class="sxs-lookup"><span data-stu-id="6f981-123">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="6f981-124">使用准则</span><span class="sxs-lookup"><span data-stu-id="6f981-124">Usage Guidelines</span></span>](usage-guidelines.md)  
 <span data-ttu-id="6f981-125">介绍使用常见类型（如数组、特性和集合、支持序列化和重载相等运算符）的准则。</span><span class="sxs-lookup"><span data-stu-id="6f981-125">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="6f981-126">常见设计模式</span><span class="sxs-lookup"><span data-stu-id="6f981-126">Common Design Patterns</span></span>](common-design-patterns.md)  
 <span data-ttu-id="6f981-127">提供有关选择和实现依赖项属性的准则。</span><span class="sxs-lookup"><span data-stu-id="6f981-127">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="6f981-128">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="6f981-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6f981-129">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="6f981-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f981-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f981-130">See also</span></span>

- [<span data-ttu-id="6f981-131">概述</span><span class="sxs-lookup"><span data-stu-id="6f981-131">Overview</span></span>](../../framework/get-started/overview.md)
- [<span data-ttu-id="6f981-132">开发指南</span><span class="sxs-lookup"><span data-stu-id="6f981-132">Development Guide</span></span>](../../framework/development-guide.md)
