---
title: 类型设计准则
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 17bd300277a039818a3d563c8f2d5f99eb2fc68d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289559"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="71c5a-102">类型设计准则</span><span class="sxs-lookup"><span data-stu-id="71c5a-102">Type Design Guidelines</span></span>
<span data-ttu-id="71c5a-103">从 CLR 的角度来看，只有两类类型：引用类型和值类型，但对于框架设计的讨论，我们将类型分成多个逻辑组，每个逻辑组都有自己的特定设计规则。</span><span class="sxs-lookup"><span data-stu-id="71c5a-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>

 <span data-ttu-id="71c5a-104">类是引用类型的一般情况。</span><span class="sxs-lookup"><span data-stu-id="71c5a-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="71c5a-105">它们构成大多数框架中的类型。</span><span class="sxs-lookup"><span data-stu-id="71c5a-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="71c5a-106">类在其支持的丰富、面向对象的功能集方面欠其普及。</span><span class="sxs-lookup"><span data-stu-id="71c5a-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="71c5a-107">基类和抽象类是与扩展性相关的特殊逻辑组。</span><span class="sxs-lookup"><span data-stu-id="71c5a-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>

 <span data-ttu-id="71c5a-108">接口是可以由引用类型和值类型实现的类型。</span><span class="sxs-lookup"><span data-stu-id="71c5a-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="71c5a-109">因此，它们可以充当引用类型和值类型的多态层次结构的根。</span><span class="sxs-lookup"><span data-stu-id="71c5a-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="71c5a-110">此外，接口还可用于模拟多个继承，而 CLR 并不本机支持此方法。</span><span class="sxs-lookup"><span data-stu-id="71c5a-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>

 <span data-ttu-id="71c5a-111">结构是值类型的一般事例，应为类似于语言基元的小型简单类型保留。</span><span class="sxs-lookup"><span data-stu-id="71c5a-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>

 <span data-ttu-id="71c5a-112">枚举是值类型的一种特殊情况，用于定义短值集，如一周中的几天、控制台颜色等。</span><span class="sxs-lookup"><span data-stu-id="71c5a-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>

 <span data-ttu-id="71c5a-113">静态类是用于静态成员的容器的类型。</span><span class="sxs-lookup"><span data-stu-id="71c5a-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="71c5a-114">它们通常用于提供其他操作的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="71c5a-114">They are commonly used to provide shortcuts to other operations.</span></span>

 <span data-ttu-id="71c5a-115">委托、异常、特性、数组和集合都是专用于特定用途的引用类型的特殊情况，本指南中的其他地方讨论了用于设计和使用的准则。</span><span class="sxs-lookup"><span data-stu-id="71c5a-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>

 <span data-ttu-id="71c5a-116">✔️确保每个类型都是一组定义完善的相关成员，而不只是一个随机的无关功能集合。</span><span class="sxs-lookup"><span data-stu-id="71c5a-116">✔️ DO ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="71c5a-117">本节内容</span><span class="sxs-lookup"><span data-stu-id="71c5a-117">In This Section</span></span>
 <span data-ttu-id="71c5a-118">[在类和结构之间选择](choosing-between-class-and-struct.md)[抽象类设计](abstract-class.md)[静态类设计](static-class.md)[接口设计](interface.md)[结构设计](struct.md)[枚举设计](enum.md)[嵌套类型](nested-types.md)*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="71c5a-118">[Choosing Between Class and Struct](choosing-between-class-and-struct.md) [Abstract Class Design](abstract-class.md) [Static Class Design](static-class.md) [Interface Design](interface.md) [Struct Design](struct.md) [Enum Design](enum.md) [Nested Types](nested-types.md) *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="71c5a-119">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="71c5a-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="71c5a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71c5a-120">See also</span></span>

- [<span data-ttu-id="71c5a-121">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="71c5a-121">Framework Design Guidelines</span></span>](index.md)
