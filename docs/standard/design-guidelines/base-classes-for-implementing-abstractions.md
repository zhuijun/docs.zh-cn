---
title: 用于实现抽象的基类
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
ms.openlocfilehash: 6af63373b7cbb571265f14ac36028953525fcc7f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280564"
---
# <a name="base-classes-for-implementing-abstractions"></a><span data-ttu-id="2cc91-102">用于实现抽象的基类</span><span class="sxs-lookup"><span data-stu-id="2cc91-102">Base Classes for Implementing Abstractions</span></span>
<span data-ttu-id="2cc91-103">严格地说，当另一个类派生类时，该类将成为基类。</span><span class="sxs-lookup"><span data-stu-id="2cc91-103">Strictly speaking, a class becomes a base class when another class is derived from it.</span></span> <span data-ttu-id="2cc91-104">不过，在本部分中，基类是设计用于提供公共抽象的类，或用于其他类的类，通过继承来重用某些默认实现。</span><span class="sxs-lookup"><span data-stu-id="2cc91-104">For the purpose of this section, however, a base class is a class designed mainly to provide a common abstraction or for other classes to reuse some default implementation though inheritance.</span></span> <span data-ttu-id="2cc91-105">基类通常位于继承层次结构中，在层次结构的根下的抽象之间，还有几个自定义实现。</span><span class="sxs-lookup"><span data-stu-id="2cc91-105">Base classes usually sit in the middle of inheritance hierarchies, between an abstraction at the root of a hierarchy and several custom implementations at the bottom.</span></span>

 <span data-ttu-id="2cc91-106">它们充当实现抽象的实现帮助程序。</span><span class="sxs-lookup"><span data-stu-id="2cc91-106">They serve as implementation helpers for implementing abstractions.</span></span> <span data-ttu-id="2cc91-107">例如，用于项的有序集合的某个框架抽象是 <xref:System.Collections.Generic.IList%601> 接口。</span><span class="sxs-lookup"><span data-stu-id="2cc91-107">For example, one of the Framework’s abstractions for ordered collections of items is the <xref:System.Collections.Generic.IList%601> interface.</span></span> <span data-ttu-id="2cc91-108">实现并 <xref:System.Collections.Generic.IList%601> 不重要，因此，该框架提供了多个基类，如 <xref:System.Collections.ObjectModel.Collection%601> 和 <xref:System.Collections.ObjectModel.KeyedCollection%602> ，它们用作实现自定义集合的帮助器。</span><span class="sxs-lookup"><span data-stu-id="2cc91-108">Implementing <xref:System.Collections.Generic.IList%601> is not trivial, and therefore the Framework provides several base classes, such as <xref:System.Collections.ObjectModel.Collection%601> and <xref:System.Collections.ObjectModel.KeyedCollection%602>, which serve as helpers for implementing custom collections.</span></span>

 <span data-ttu-id="2cc91-109">基类通常不适合用作抽象，因为它们往往包含太多的实现。</span><span class="sxs-lookup"><span data-stu-id="2cc91-109">Base classes are usually not suited to serve as abstractions by themselves, because they tend to contain too much implementation.</span></span> <span data-ttu-id="2cc91-110">例如， `Collection<T>` 基类包含许多与实现非泛型接口的事实相关的实现 `IList` （以便更好地与非泛型集合集成），并且是指它是存储在其一个字段的内存中的项的集合。</span><span class="sxs-lookup"><span data-stu-id="2cc91-110">For example, the `Collection<T>` base class contains lots of implementation related to the fact that it implements the nongeneric `IList` interface (to integrate better with nongeneric collections) and to the fact that it is a collection of items stored in memory in one of its fields.</span></span>

 <span data-ttu-id="2cc91-111">正如前面所讨论的，基类可为需要实现抽象的用户提供宝贵的帮助，但同时也会有重大责任。</span><span class="sxs-lookup"><span data-stu-id="2cc91-111">As previously discussed, base classes can provide invaluable help for users who need to implement abstractions, but at the same time they can be a significant liability.</span></span> <span data-ttu-id="2cc91-112">它们添加了表面区域并增加了继承层次结构的深度，因此在概念上使框架复杂化。</span><span class="sxs-lookup"><span data-stu-id="2cc91-112">They add surface area and increase the depth of inheritance hierarchies and so conceptually complicate the framework.</span></span> <span data-ttu-id="2cc91-113">因此，仅当基类为框架用户提供重要值时，才应使用它们。</span><span class="sxs-lookup"><span data-stu-id="2cc91-113">Therefore, base classes should be used only if they provide significant value to the users of the framework.</span></span> <span data-ttu-id="2cc91-114">如果用户仅向框架的实施者提供值，则应避免使用这些值，在这种情况下，应强烈考虑委托给内部实现，而不是基类继承。</span><span class="sxs-lookup"><span data-stu-id="2cc91-114">They should be avoided if they provide value only to the implementers of the framework, in which case delegation to an internal implementation instead of inheritance from a base class should be strongly considered.</span></span>

 <span data-ttu-id="2cc91-115">✔️考虑使基类抽象，即使它们不包含任何抽象成员也是如此。</span><span class="sxs-lookup"><span data-stu-id="2cc91-115">✔️ CONSIDER making base classes abstract even if they don’t contain any abstract members.</span></span> <span data-ttu-id="2cc91-116">这就清楚地与用户沟通，该类专门用于从继承。</span><span class="sxs-lookup"><span data-stu-id="2cc91-116">This clearly communicates to the users that the class is designed solely to be inherited from.</span></span>

 <span data-ttu-id="2cc91-117">✔️考虑将基类置于不同于主线方案类型的命名空间中。</span><span class="sxs-lookup"><span data-stu-id="2cc91-117">✔️ CONSIDER placing base classes in a separate namespace from the mainline scenario types.</span></span> <span data-ttu-id="2cc91-118">按照定义，基类适用于高级扩展性方案，因此对于大多数用户来说并不重要。</span><span class="sxs-lookup"><span data-stu-id="2cc91-118">By definition, base classes are intended for advanced extensibility scenarios and therefore are not interesting to the majority of users.</span></span>

 <span data-ttu-id="2cc91-119">❌如果类应在公共 Api 中使用，请避免使用 "Base" 后缀命名基类。</span><span class="sxs-lookup"><span data-stu-id="2cc91-119">❌ AVOID naming base classes with a "Base" suffix if the class is intended for use in public APIs.</span></span>

 <span data-ttu-id="2cc91-120">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="2cc91-120">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="2cc91-121">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="2cc91-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2cc91-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2cc91-122">See also</span></span>

- [<span data-ttu-id="2cc91-123">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="2cc91-123">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="2cc91-124">扩展性设计</span><span class="sxs-lookup"><span data-stu-id="2cc91-124">Designing for Extensibility</span></span>](designing-for-extensibility.md)
