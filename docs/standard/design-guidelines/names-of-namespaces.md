---
title: 命名空间的名称
description: 使用这些准则来命名命名空间，作为设计扩展和与 .NET 库交互的库的指南的一部分。
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: e435e0281165b4a9f12bbccbeb10401b57375dcb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290196"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="245b3-103">命名空间的名称</span><span class="sxs-lookup"><span data-stu-id="245b3-103">Names of Namespaces</span></span>
<span data-ttu-id="245b3-104">与其他命名准则一样，命名命名空间的目标是为程序员创建足够的清晰度，使其能够立即了解命名空间的内容。</span><span class="sxs-lookup"><span data-stu-id="245b3-104">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="245b3-105">以下模板指定命名空间的一般规则：</span><span class="sxs-lookup"><span data-stu-id="245b3-105">The following template specifies the general rule for naming namespaces:</span></span>

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 <span data-ttu-id="245b3-106">下面是一些示例：</span><span class="sxs-lookup"><span data-stu-id="245b3-106">The following are examples:</span></span>

 <span data-ttu-id="245b3-107">`Fabrikam.Math` `Litware.Security`</span><span class="sxs-lookup"><span data-stu-id="245b3-107">`Fabrikam.Math` `Litware.Security`</span></span>

 <span data-ttu-id="245b3-108">✔️使用公司名称作为命名空间名称的前缀，以防不同公司的命名空间具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="245b3-108">✔️ DO prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>

 <span data-ttu-id="245b3-109">✔️在命名空间名称的第二级使用稳定的独立于版本的产品名称。</span><span class="sxs-lookup"><span data-stu-id="245b3-109">✔️ DO use a stable, version-independent product name at the second level of a namespace name.</span></span>

 <span data-ttu-id="245b3-110">❌不要使用组织层次结构作为命名空间层次结构中的名称的基础，因为公司内的组名通常是短期的。</span><span class="sxs-lookup"><span data-stu-id="245b3-110">❌ DO NOT use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="245b3-111">围绕一组相关技术组织命名空间的层次结构。</span><span class="sxs-lookup"><span data-stu-id="245b3-111">Organize the hierarchy of namespaces around groups of related technologies.</span></span>

 <span data-ttu-id="245b3-112">✔️使用 PascalCasing，并使用句点分隔命名空间组件（例如 `Microsoft.Office.PowerPoint` ）。</span><span class="sxs-lookup"><span data-stu-id="245b3-112">✔️ DO use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="245b3-113">如果品牌采用 nontraditional 大小写，则应遵循品牌定义的大小写，即使它与常规命名空间大小写不符。</span><span class="sxs-lookup"><span data-stu-id="245b3-113">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>

 <span data-ttu-id="245b3-114">✔️考虑在适当的情况下使用复数命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="245b3-114">✔️ CONSIDER using plural namespace names where appropriate.</span></span>

 <span data-ttu-id="245b3-115">例如，使用 `System.Collections` 而不是 `System.Collection`。</span><span class="sxs-lookup"><span data-stu-id="245b3-115">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="245b3-116">不过，品牌名称和首字母缩写是此规则的例外情况。</span><span class="sxs-lookup"><span data-stu-id="245b3-116">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="245b3-117">例如，使用 `System.IO` 而不是 `System.IOs`。</span><span class="sxs-lookup"><span data-stu-id="245b3-117">For example, use `System.IO` instead of `System.IOs`.</span></span>

 <span data-ttu-id="245b3-118">❌命名空间和该命名空间中的类型不要使用相同的名称。</span><span class="sxs-lookup"><span data-stu-id="245b3-118">❌ DO NOT use the same name for a namespace and a type in that namespace.</span></span>

 <span data-ttu-id="245b3-119">例如，不要将 `Debug` 用作命名空间名称，并 `Debug` 在同一命名空间中提供名为的类。</span><span class="sxs-lookup"><span data-stu-id="245b3-119">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="245b3-120">一些编译器需要完全限定此类类型。</span><span class="sxs-lookup"><span data-stu-id="245b3-120">Several compilers require such types to be fully qualified.</span></span>

### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="245b3-121">命名空间和类型名称冲突</span><span class="sxs-lookup"><span data-stu-id="245b3-121">Namespaces and Type Name Conflicts</span></span>
 <span data-ttu-id="245b3-122">❌不要引入泛型类型名称 `Element` ，例如、、 `Node` `Log` 和 `Message` 。</span><span class="sxs-lookup"><span data-stu-id="245b3-122">❌ DO NOT introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>

 <span data-ttu-id="245b3-123">很多情况下，这样做会导致在常见方案中发生类型名称冲突。</span><span class="sxs-lookup"><span data-stu-id="245b3-123">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="245b3-124">应限定泛型类型名称（ `FormElement` 、 `XmlNode` 、 `EventLog` 、 `SoapMessage` ）。</span><span class="sxs-lookup"><span data-stu-id="245b3-124">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>

 <span data-ttu-id="245b3-125">为避免不同类别的命名空间的类型名称冲突，有一些特定的准则。</span><span class="sxs-lookup"><span data-stu-id="245b3-125">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>

- <span data-ttu-id="245b3-126">**应用程序模型命名空间**</span><span class="sxs-lookup"><span data-stu-id="245b3-126">**Application model namespaces**</span></span>

     <span data-ttu-id="245b3-127">属于单个应用程序模型的命名空间经常一起使用，但几乎不能与其他应用程序模型的命名空间一起使用。</span><span class="sxs-lookup"><span data-stu-id="245b3-127">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="245b3-128">例如， <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空间非常少与 <xref:System.Web.UI?displayProperty=nameWithType> 命名空间一起使用。</span><span class="sxs-lookup"><span data-stu-id="245b3-128">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="245b3-129">下面列出了众所周知的应用程序模型命名空间组：</span><span class="sxs-lookup"><span data-stu-id="245b3-129">The following is a list of well-known application model namespace groups:</span></span>

     <span data-ttu-id="245b3-130">`System.Windows*` `System.Web.UI*`</span><span class="sxs-lookup"><span data-stu-id="245b3-130">`System.Windows*` `System.Web.UI*`</span></span>

     <span data-ttu-id="245b3-131">❌不要为单个应用程序模型中的命名空间中的类型指定相同的名称。</span><span class="sxs-lookup"><span data-stu-id="245b3-131">❌ DO NOT give the same name to types in namespaces within a single application model.</span></span>

     <span data-ttu-id="245b3-132">例如，不要将名为的类型添加 `Page` 到 <xref:System.Web.UI.Adapters?displayProperty=nameWithType> 命名空间，因为该 <xref:System.Web.UI?displayProperty=nameWithType> 命名空间已经包含一个名为的类型 `Page` 。</span><span class="sxs-lookup"><span data-stu-id="245b3-132">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>

- <span data-ttu-id="245b3-133">**基础结构命名空间**</span><span class="sxs-lookup"><span data-stu-id="245b3-133">**Infrastructure namespaces**</span></span>

     <span data-ttu-id="245b3-134">此组包含在开发常见应用程序期间很少导入的命名空间。</span><span class="sxs-lookup"><span data-stu-id="245b3-134">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="245b3-135">例如， `.Design` 命名空间主要在开发编程工具时使用。</span><span class="sxs-lookup"><span data-stu-id="245b3-135">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="245b3-136">避免与这些命名空间中的类型冲突并不重要。</span><span class="sxs-lookup"><span data-stu-id="245b3-136">Avoiding conflicts with types in these namespaces is not critical.</span></span>

- <span data-ttu-id="245b3-137">**核心命名空间**</span><span class="sxs-lookup"><span data-stu-id="245b3-137">**Core namespaces**</span></span>

     <span data-ttu-id="245b3-138">核心命名空间包括所有 `System` 命名空间（不包括应用程序模型的命名空间和基础结构命名空间）。</span><span class="sxs-lookup"><span data-stu-id="245b3-138">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="245b3-139">核心命名空间包括、、、 `System` `System.IO` `System.Xml` 和 `System.Net` 。</span><span class="sxs-lookup"><span data-stu-id="245b3-139">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>

     <span data-ttu-id="245b3-140">❌不要提供会与核心命名空间中的任何类型冲突的类型名称。</span><span class="sxs-lookup"><span data-stu-id="245b3-140">❌ DO NOT give types names that would conflict with any type in the Core namespaces.</span></span>

     <span data-ttu-id="245b3-141">例如，永远不要将 `Stream` 用作类型名称。</span><span class="sxs-lookup"><span data-stu-id="245b3-141">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="245b3-142">它会与 <xref:System.IO.Stream?displayProperty=nameWithType> 非常常用的类型冲突。</span><span class="sxs-lookup"><span data-stu-id="245b3-142">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>

- <span data-ttu-id="245b3-143">**技术命名空间组**</span><span class="sxs-lookup"><span data-stu-id="245b3-143">**Technology namespace groups**</span></span>

     <span data-ttu-id="245b3-144">此类别包含具有相同的前两个命名空间节点的所有命名空间 `(<Company>.<Technology>*` ，例如 `Microsoft.Build.Utilities` 和 `Microsoft.Build.Tasks` 。</span><span class="sxs-lookup"><span data-stu-id="245b3-144">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="245b3-145">属于单个技术的类型不会相互冲突，这一点非常重要。</span><span class="sxs-lookup"><span data-stu-id="245b3-145">It is important that types belonging to a single technology do not conflict with each other.</span></span>

     <span data-ttu-id="245b3-146">❌不要分配会与单个技术中的其他类型冲突的类型名称。</span><span class="sxs-lookup"><span data-stu-id="245b3-146">❌ DO NOT assign type names that would conflict with other types within a single technology.</span></span>

     <span data-ttu-id="245b3-147">❌请勿引入技术命名空间中的类型与应用程序模型命名空间中的类型之间的类型名称冲突（除非该技术不打算与应用程序模型一起使用）。</span><span class="sxs-lookup"><span data-stu-id="245b3-147">❌ DO NOT introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>

 <span data-ttu-id="245b3-148">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="245b3-148">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="245b3-149">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="245b3-149">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="245b3-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="245b3-150">See also</span></span>

- [<span data-ttu-id="245b3-151">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="245b3-151">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="245b3-152">命名准则</span><span class="sxs-lookup"><span data-stu-id="245b3-152">Naming Guidelines</span></span>](naming-guidelines.md)
