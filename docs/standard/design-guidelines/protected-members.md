---
title: 受保护的成员
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: afcb92e48996d594fcedc5b579922b179f754b9d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286114"
---
# <a name="protected-members"></a><span data-ttu-id="e0d00-102">受保护的成员</span><span class="sxs-lookup"><span data-stu-id="e0d00-102">Protected Members</span></span>
<span data-ttu-id="e0d00-103">受保护的成员不提供任何可扩展性，但它们可以通过创建更强大的子类进行扩展。</span><span class="sxs-lookup"><span data-stu-id="e0d00-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="e0d00-104">它们可用于公开高级自定义项选项，而不会使主公共接口复杂化。</span><span class="sxs-lookup"><span data-stu-id="e0d00-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="e0d00-105">框架设计人员需要小心处理受保护的成员，因为名称 "protected" 可以提供虚假的安全性理解。</span><span class="sxs-lookup"><span data-stu-id="e0d00-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="e0d00-106">任何人都可以为未密封的类提供子类并访问受保护的成员，因此用于公共成员的所有相同的防御性编码方法都适用于受保护的成员。</span><span class="sxs-lookup"><span data-stu-id="e0d00-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="e0d00-107">✔️考虑使用受保护的成员进行高级自定义。</span><span class="sxs-lookup"><span data-stu-id="e0d00-107">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="e0d00-108">✔️将未密封类中的受保护成员视为公共的，目的是为了实现安全、文档和兼容性分析。</span><span class="sxs-lookup"><span data-stu-id="e0d00-108">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="e0d00-109">任何人都可以从类继承并访问受保护的成员。</span><span class="sxs-lookup"><span data-stu-id="e0d00-109">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="e0d00-110">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="e0d00-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e0d00-111">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="e0d00-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e0d00-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0d00-112">See also</span></span>

- [<span data-ttu-id="e0d00-113">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="e0d00-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="e0d00-114">扩展性设计</span><span class="sxs-lookup"><span data-stu-id="e0d00-114">Designing for Extensibility</span></span>](designing-for-extensibility.md)
