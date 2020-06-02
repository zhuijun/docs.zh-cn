---
title: 命名准则
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
ms.openlocfilehash: 1b137be60f4c8c1c7cf1fa1f807841d4bc209089
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290170"
---
# <a name="naming-guidelines"></a><span data-ttu-id="159c7-102">命名准则</span><span class="sxs-lookup"><span data-stu-id="159c7-102">Naming Guidelines</span></span>
<span data-ttu-id="159c7-103">在框架开发中采用一致的命名约定集可能是框架可用性的主要贡献。</span><span class="sxs-lookup"><span data-stu-id="159c7-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="159c7-104">它允许很多开发人员对广泛分隔的项目使用框架。</span><span class="sxs-lookup"><span data-stu-id="159c7-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="159c7-105">除了表单的一致性以外，框架元素的名称也必须易于理解，并且必须传达每个元素的功能。</span><span class="sxs-lookup"><span data-stu-id="159c7-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="159c7-106">本章的目的是提供一组一致的命名约定，以使开发人员能够立即了解名称。</span><span class="sxs-lookup"><span data-stu-id="159c7-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="159c7-107">尽管采用这些命名约定作为一般代码开发准则会使代码的命名更为一致，但你只需要将它们应用到公开公开的 Api （公共或受保护类型和成员以及显式实现的接口）。</span><span class="sxs-lookup"><span data-stu-id="159c7-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="159c7-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="159c7-108">In This Section</span></span>  
 [<span data-ttu-id="159c7-109">大小写约定</span><span class="sxs-lookup"><span data-stu-id="159c7-109">Capitalization Conventions</span></span>](capitalization-conventions.md)  
 [<span data-ttu-id="159c7-110">通用命名约定</span><span class="sxs-lookup"><span data-stu-id="159c7-110">General Naming Conventions</span></span>](general-naming-conventions.md)  
 [<span data-ttu-id="159c7-111">程序集和 Dll 的名称</span><span class="sxs-lookup"><span data-stu-id="159c7-111">Names of Assemblies and DLLs</span></span>](names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="159c7-112">命名空间的名称</span><span class="sxs-lookup"><span data-stu-id="159c7-112">Names of Namespaces</span></span>](names-of-namespaces.md)  
 [<span data-ttu-id="159c7-113">类、结构和接口的名称</span><span class="sxs-lookup"><span data-stu-id="159c7-113">Names of Classes, Structs, and Interfaces</span></span>](names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="159c7-114">类型成员的名称</span><span class="sxs-lookup"><span data-stu-id="159c7-114">Names of Type Members</span></span>](names-of-type-members.md)  
 [<span data-ttu-id="159c7-115">命名参数</span><span class="sxs-lookup"><span data-stu-id="159c7-115">Naming Parameters</span></span>](naming-parameters.md)  
 [<span data-ttu-id="159c7-116">命名资源</span><span class="sxs-lookup"><span data-stu-id="159c7-116">Naming Resources</span></span>](naming-resources.md)  
 <span data-ttu-id="159c7-117">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="159c7-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="159c7-118">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="159c7-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="159c7-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="159c7-119">See also</span></span>

- [<span data-ttu-id="159c7-120">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="159c7-120">Framework Design Guidelines</span></span>](index.md)
