---
title: 成员设计准则
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: c323e7edd752a1f003bd3f5d81689aca0eaefd20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288987"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="8d6b0-102">成员设计准则</span><span class="sxs-lookup"><span data-stu-id="8d6b0-102">Member Design Guidelines</span></span>
<span data-ttu-id="8d6b0-103">方法、属性、事件、构造函数和字段统称为成员。</span><span class="sxs-lookup"><span data-stu-id="8d6b0-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="8d6b0-104">成员最终是指向框架的最终用户公开框架功能的方式。</span><span class="sxs-lookup"><span data-stu-id="8d6b0-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="8d6b0-105">成员可以为虚拟或非虚拟、具体或抽象、静态或实例，并可具有多个不同的可访问性范围。</span><span class="sxs-lookup"><span data-stu-id="8d6b0-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="8d6b0-106">所有这些组件都提供令人难以置信的表现力，但同时需要注意框架设计器的一部分。</span><span class="sxs-lookup"><span data-stu-id="8d6b0-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="8d6b0-107">本章提供设计任何类型的成员时应遵循的基本准则。</span><span class="sxs-lookup"><span data-stu-id="8d6b0-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d6b0-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="8d6b0-108">In This Section</span></span>  
 [<span data-ttu-id="8d6b0-109">成员重载</span><span class="sxs-lookup"><span data-stu-id="8d6b0-109">Member Overloading</span></span>](member-overloading.md)  
 [<span data-ttu-id="8d6b0-110">属性设计</span><span class="sxs-lookup"><span data-stu-id="8d6b0-110">Property Design</span></span>](property.md)  
 [<span data-ttu-id="8d6b0-111">构造函数设计</span><span class="sxs-lookup"><span data-stu-id="8d6b0-111">Constructor Design</span></span>](constructor.md)  
 [<span data-ttu-id="8d6b0-112">事件设计</span><span class="sxs-lookup"><span data-stu-id="8d6b0-112">Event Design</span></span>](event.md)  
 [<span data-ttu-id="8d6b0-113">现场设计</span><span class="sxs-lookup"><span data-stu-id="8d6b0-113">Field Design</span></span>](field.md)  
 [<span data-ttu-id="8d6b0-114">扩展方法</span><span class="sxs-lookup"><span data-stu-id="8d6b0-114">Extension Methods</span></span>](extension-methods.md)  
 [<span data-ttu-id="8d6b0-115">运算符重载</span><span class="sxs-lookup"><span data-stu-id="8d6b0-115">Operator Overloads</span></span>](operator-overloads.md)  
 [<span data-ttu-id="8d6b0-116">参数设计</span><span class="sxs-lookup"><span data-stu-id="8d6b0-116">Parameter Design</span></span>](parameter-design.md)  
 <span data-ttu-id="8d6b0-117">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="8d6b0-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8d6b0-118">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="8d6b0-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6b0-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d6b0-119">See also</span></span>

- [<span data-ttu-id="8d6b0-120">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="8d6b0-120">Framework Design Guidelines</span></span>](index.md)
