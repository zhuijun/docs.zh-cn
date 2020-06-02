---
title: 扩展性设计
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 406c15b6ce42b637ed1bbb61761d05e040995579
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280239"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="548eb-102">扩展性设计</span><span class="sxs-lookup"><span data-stu-id="548eb-102">Designing for Extensibility</span></span>
<span data-ttu-id="548eb-103">设计框架的一个重要方面是确保已认真考虑框架的扩展性。</span><span class="sxs-lookup"><span data-stu-id="548eb-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="548eb-104">这需要您了解与各种扩展性机制相关的成本和好处。</span><span class="sxs-lookup"><span data-stu-id="548eb-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="548eb-105">本章可帮助您确定哪些可扩展性机制（子类、事件、虚拟成员、回调等）可以最大程度地满足您的框架的要求。</span><span class="sxs-lookup"><span data-stu-id="548eb-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="548eb-106">可以通过多种方式在框架中提供可扩展性。</span><span class="sxs-lookup"><span data-stu-id="548eb-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="548eb-107">它们的范围不太强大，但成本较低，且成本较高，但成本较高。</span><span class="sxs-lookup"><span data-stu-id="548eb-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="548eb-108">对于任何给定的扩展性要求，你应选择满足要求的成本最低的扩展性机制。</span><span class="sxs-lookup"><span data-stu-id="548eb-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="548eb-109">请记住，稍后可以添加更多的扩展性，但不会引入重大更改。</span><span class="sxs-lookup"><span data-stu-id="548eb-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="548eb-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="548eb-110">In This Section</span></span>  
 [<span data-ttu-id="548eb-111">未密封类</span><span class="sxs-lookup"><span data-stu-id="548eb-111">Unsealed Classes</span></span>](unsealed-classes.md)  
 [<span data-ttu-id="548eb-112">受保护成员</span><span class="sxs-lookup"><span data-stu-id="548eb-112">Protected Members</span></span>](protected-members.md)  
 [<span data-ttu-id="548eb-113">事件和回调</span><span class="sxs-lookup"><span data-stu-id="548eb-113">Events and Callbacks</span></span>](events-and-callbacks.md)  
 [<span data-ttu-id="548eb-114">虚拟成员</span><span class="sxs-lookup"><span data-stu-id="548eb-114">Virtual Members</span></span>](virtual-members.md)  
 [<span data-ttu-id="548eb-115">抽象（抽象类型和接口）</span><span class="sxs-lookup"><span data-stu-id="548eb-115">Abstractions (Abstract Types and Interfaces)</span></span>](abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="548eb-116">用于实现抽象的基类</span><span class="sxs-lookup"><span data-stu-id="548eb-116">Base Classes for Implementing Abstractions</span></span>](base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="548eb-117">密封</span><span class="sxs-lookup"><span data-stu-id="548eb-117">Sealing</span></span>](sealing.md)  
 <span data-ttu-id="548eb-118">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="548eb-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="548eb-119">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="548eb-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548eb-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="548eb-120">See also</span></span>

- [<span data-ttu-id="548eb-121">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="548eb-121">Framework Design Guidelines</span></span>](index.md)
