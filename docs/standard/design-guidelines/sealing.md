---
title: 密封
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: a54c68efb4ac114fe0e5a5712eca877bef35c103
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290105"
---
# <a name="sealing"></a><span data-ttu-id="d8448-102">密封</span><span class="sxs-lookup"><span data-stu-id="d8448-102">Sealing</span></span>
<span data-ttu-id="d8448-103">面向对象的框架的一项功能是，开发人员可以采用框架设计器无法预料的方式对其进行扩展和自定义。</span><span class="sxs-lookup"><span data-stu-id="d8448-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="d8448-104">这是可扩展设计的强大功能和危险。</span><span class="sxs-lookup"><span data-stu-id="d8448-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="d8448-105">当你设计框架时，这一点非常重要，需要在需要时认真设计扩展性，并在有风险时限制扩展性。</span><span class="sxs-lookup"><span data-stu-id="d8448-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>

 <span data-ttu-id="d8448-106">阻止扩展性的强大机制是密封的。</span><span class="sxs-lookup"><span data-stu-id="d8448-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="d8448-107">可以密封类或单个成员。</span><span class="sxs-lookup"><span data-stu-id="d8448-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="d8448-108">密封类可防止用户从类继承。</span><span class="sxs-lookup"><span data-stu-id="d8448-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="d8448-109">密封成员可防止用户重写特定成员。</span><span class="sxs-lookup"><span data-stu-id="d8448-109">Sealing a member prevents users from overriding a particular member.</span></span>

 <span data-ttu-id="d8448-110">❌不要密封类，无需采取充分的理由。</span><span class="sxs-lookup"><span data-stu-id="d8448-110">❌ DO NOT seal classes without having a good reason to do so.</span></span>

 <span data-ttu-id="d8448-111">密封类，因为您不能认为扩展性方案不是一个好的原因。</span><span class="sxs-lookup"><span data-stu-id="d8448-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="d8448-112">出于各种 nonobvious 原因（如添加便利成员），框架用户喜欢从类继承。</span><span class="sxs-lookup"><span data-stu-id="d8448-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="d8448-113">有关用户要从类型继承的 nonobvious 原因的示例，请参阅未[密封类](unsealed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="d8448-113">See [Unsealed Classes](unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>

 <span data-ttu-id="d8448-114">密封类的合理原因包括：</span><span class="sxs-lookup"><span data-stu-id="d8448-114">Good reasons for sealing a class include the following:</span></span>

- <span data-ttu-id="d8448-115">类是静态类。</span><span class="sxs-lookup"><span data-stu-id="d8448-115">The class is a static class.</span></span> <span data-ttu-id="d8448-116">请参阅[静态类设计](static-class.md)。</span><span class="sxs-lookup"><span data-stu-id="d8448-116">See [Static Class Design](static-class.md).</span></span>

- <span data-ttu-id="d8448-117">类在继承的受保护成员中存储安全敏感机密。</span><span class="sxs-lookup"><span data-stu-id="d8448-117">The class stores security-sensitive secrets in inherited protected members.</span></span>

- <span data-ttu-id="d8448-118">类继承多个虚拟成员，并分别对它们进行密封的开销超过了使类不密封的好处。</span><span class="sxs-lookup"><span data-stu-id="d8448-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>

- <span data-ttu-id="d8448-119">类是需要非常快速的运行时查找的属性。</span><span class="sxs-lookup"><span data-stu-id="d8448-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="d8448-120">密封属性比非密封属性略高。</span><span class="sxs-lookup"><span data-stu-id="d8448-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="d8448-121">请参阅[特性](attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="d8448-121">See [Attributes](attributes.md).</span></span>

 <span data-ttu-id="d8448-122">❌不要在密封类型中声明受保护成员或虚拟成员。</span><span class="sxs-lookup"><span data-stu-id="d8448-122">❌ DO NOT declare protected or virtual members on sealed types.</span></span>

 <span data-ttu-id="d8448-123">按照定义，不能从继承密封类型。</span><span class="sxs-lookup"><span data-stu-id="d8448-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="d8448-124">这意味着不能在密封类型上调用受保护成员，并且不能重写密封类型上的虚方法。</span><span class="sxs-lookup"><span data-stu-id="d8448-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>

 <span data-ttu-id="d8448-125">✔️考虑密封重写的成员。</span><span class="sxs-lookup"><span data-stu-id="d8448-125">✔️ CONSIDER sealing members that you override.</span></span>

 <span data-ttu-id="d8448-126">引入虚拟成员（在[虚拟成员](virtual-members.md)中讨论）可能会产生的问题也适用于重写，尽管稍微略低一些。</span><span class="sxs-lookup"><span data-stu-id="d8448-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="d8448-127">密封替代会阻止从继承层次结构中的该点开始的这些问题。</span><span class="sxs-lookup"><span data-stu-id="d8448-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>

 <span data-ttu-id="d8448-128">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="d8448-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="d8448-129">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="d8448-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d8448-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8448-130">See also</span></span>

- [<span data-ttu-id="d8448-131">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="d8448-131">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="d8448-132">扩展性设计</span><span class="sxs-lookup"><span data-stu-id="d8448-132">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="d8448-133">未密封类</span><span class="sxs-lookup"><span data-stu-id="d8448-133">Unsealed Classes</span></span>](unsealed-classes.md)
