---
title: 抽象类设计
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: e6a5923f293ed536fb272f6fe6c805067aede0ab
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280772"
---
# <a name="abstract-class-design"></a><span data-ttu-id="de522-102">抽象类设计</span><span class="sxs-lookup"><span data-stu-id="de522-102">Abstract Class Design</span></span>

<span data-ttu-id="de522-103">❌不要在抽象类型中定义公共或受保护的内部构造函数。</span><span class="sxs-lookup"><span data-stu-id="de522-103">❌ DO NOT define public or protected internal constructors in abstract types.</span></span>

 <span data-ttu-id="de522-104">仅当用户需要创建类型的实例时，构造函数才应该是公共的。</span><span class="sxs-lookup"><span data-stu-id="de522-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="de522-105">由于不能创建抽象类型的实例，因此具有公共构造函数的抽象类型会错误地设计并且误导用户。</span><span class="sxs-lookup"><span data-stu-id="de522-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>

 <span data-ttu-id="de522-106">✔️在抽象类中定义受保护的或内部构造函数。</span><span class="sxs-lookup"><span data-stu-id="de522-106">✔️ DO define a protected or an internal constructor in abstract classes.</span></span>

 <span data-ttu-id="de522-107">受保护的构造函数更常见，只允许基类在创建子类型时进行自己的初始化。</span><span class="sxs-lookup"><span data-stu-id="de522-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>

 <span data-ttu-id="de522-108">内部构造函数可用于将抽象类的具体实现限制为定义类的程序集。</span><span class="sxs-lookup"><span data-stu-id="de522-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>

 <span data-ttu-id="de522-109">✔️提供至少一种从你发运的每个抽象类继承的具体类型。</span><span class="sxs-lookup"><span data-stu-id="de522-109">✔️ DO provide at least one concrete type that inherits from each abstract class that you ship.</span></span>

 <span data-ttu-id="de522-110">这样做有助于验证抽象类的设计。</span><span class="sxs-lookup"><span data-stu-id="de522-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="de522-111">例如， <xref:System.IO.FileStream?displayProperty=nameWithType> 是 <xref:System.IO.Stream?displayProperty=nameWithType> 抽象类的实现。</span><span class="sxs-lookup"><span data-stu-id="de522-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>

 <span data-ttu-id="de522-112">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="de522-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="de522-113">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="de522-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="de522-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de522-114">See also</span></span>

- [<span data-ttu-id="de522-115">类型设计准则</span><span class="sxs-lookup"><span data-stu-id="de522-115">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="de522-116">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="de522-116">Framework Design Guidelines</span></span>](index.md)
