---
title: 嵌套类型
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: a3b090b39e1e907826551ed152d4eece4885ce41
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290131"
---
# <a name="nested-types"></a><span data-ttu-id="ddabc-102">嵌套类型</span><span class="sxs-lookup"><span data-stu-id="ddabc-102">Nested Types</span></span>
<span data-ttu-id="ddabc-103">嵌套类型是在另一种类型的作用域内定义的类型，称为封闭类型。</span><span class="sxs-lookup"><span data-stu-id="ddabc-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="ddabc-104">嵌套类型可以访问其封闭类型的所有成员。</span><span class="sxs-lookup"><span data-stu-id="ddabc-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="ddabc-105">例如，它可以访问在封闭类型中定义的私有字段，还可以访问在封闭类型的所有祖先中定义的受保护字段。</span><span class="sxs-lookup"><span data-stu-id="ddabc-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>

 <span data-ttu-id="ddabc-106">一般而言，应慎用嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="ddabc-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="ddabc-107">其原因有若干：</span><span class="sxs-lookup"><span data-stu-id="ddabc-107">There are several reasons for this.</span></span> <span data-ttu-id="ddabc-108">有些开发人员并不完全熟悉该概念。</span><span class="sxs-lookup"><span data-stu-id="ddabc-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="ddabc-109">例如，这些开发人员可能遇到声明嵌套类型变量的语法问题。</span><span class="sxs-lookup"><span data-stu-id="ddabc-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="ddabc-110">嵌套类型也与它们的封闭类型紧密耦合，因此不适合用作通用类型。</span><span class="sxs-lookup"><span data-stu-id="ddabc-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>

 <span data-ttu-id="ddabc-111">嵌套类型最适合用于建模其封闭类型的实现细节。</span><span class="sxs-lookup"><span data-stu-id="ddabc-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="ddabc-112">最终用户极少需要声明嵌套类型的变量，几乎不应显式实例化嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="ddabc-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="ddabc-113">例如，集合的枚举器可以是该集合的嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="ddabc-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="ddabc-114">枚举器通常通过其封闭类型进行实例化，由于许多语言支持 foreach 语句，因此枚举器变量很少需要由最终用户声明。</span><span class="sxs-lookup"><span data-stu-id="ddabc-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>

 <span data-ttu-id="ddabc-115">如果嵌套类型与其外部类型之间的关系是需要成员可访问性语义，✔️确实使用嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="ddabc-115">✔️ DO use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>

 <span data-ttu-id="ddabc-116">❌不要使用公共嵌套类型作为逻辑分组构造;为此使用命名空间。</span><span class="sxs-lookup"><span data-stu-id="ddabc-116">❌ DO NOT use public nested types as a logical grouping construct; use namespaces for this.</span></span>

 <span data-ttu-id="ddabc-117">❌避免公开公开的嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="ddabc-117">❌ AVOID publicly exposed nested types.</span></span> <span data-ttu-id="ddabc-118">唯一的例外是，只需在很少的情况下（如子类化或其他高级自定义方案）声明嵌套类型的变量。</span><span class="sxs-lookup"><span data-stu-id="ddabc-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>

 <span data-ttu-id="ddabc-119">❌如果类型可能在包含类型的外部引用，请不要使用嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="ddabc-119">❌ DO NOT use nested types if the type is likely to be referenced outside of the containing type.</span></span>

 <span data-ttu-id="ddabc-120">例如，传递给在类上定义的方法的枚举不应定义为类中的嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="ddabc-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>

 <span data-ttu-id="ddabc-121">❌如果嵌套类型需要通过客户端代码进行实例化，请不要使用嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="ddabc-121">❌ DO NOT use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="ddabc-122">如果某个类型具有公共构造函数，则它可能不会嵌套。</span><span class="sxs-lookup"><span data-stu-id="ddabc-122">If a type has a public constructor, it should probably not be nested.</span></span>

 <span data-ttu-id="ddabc-123">如果可实例化类型，则似乎指示类型在框架中具有一个位置（你可以创建它、使用它，并在不使用外部类型的情况下销毁它），因此不应进行嵌套。</span><span class="sxs-lookup"><span data-stu-id="ddabc-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="ddabc-124">不应将内部类型广泛地在外部类型的外部重用，无需任何与外部类型的关系。</span><span class="sxs-lookup"><span data-stu-id="ddabc-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>

 <span data-ttu-id="ddabc-125">❌不要将嵌套类型定义为接口的成员。</span><span class="sxs-lookup"><span data-stu-id="ddabc-125">❌ DO NOT define a nested type as a member of an interface.</span></span> <span data-ttu-id="ddabc-126">许多语言不支持这种构造。</span><span class="sxs-lookup"><span data-stu-id="ddabc-126">Many languages do not support such a construct.</span></span>

 <span data-ttu-id="ddabc-127">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="ddabc-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ddabc-128">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="ddabc-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ddabc-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ddabc-129">See also</span></span>

- [<span data-ttu-id="ddabc-130">类型设计准则</span><span class="sxs-lookup"><span data-stu-id="ddabc-130">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="ddabc-131">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="ddabc-131">Framework Design Guidelines</span></span>](index.md)
