---
title: 相等运算符
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: bd36b98af25db2921c164ac359188997d379a270
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280045"
---
# <a name="equality-operators"></a><span data-ttu-id="fb4c3-102">相等运算符</span><span class="sxs-lookup"><span data-stu-id="fb4c3-102">Equality Operators</span></span>
<span data-ttu-id="fb4c3-103">本节讨论重载相等运算符并将 `operator==` 和 `operator!=` 作为相等运算符引用。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="fb4c3-104">❌不要重载某个相等运算符而不是另一个相等运算符。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-104">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="fb4c3-105">✔️确保 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 和相等运算符具有完全相同的语义和类似的性能特征。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-105">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="fb4c3-106">这通常意味着在 `Object.Equals` 重载相等运算符时需要重写。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="fb4c3-107">❌避免从相等运算符引发异常。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-107">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="fb4c3-108">例如，如果其中一个参数为 null 而不是引发，则返回 false `NullReferenceException` 。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="fb4c3-109">值类型上的相等运算符</span><span class="sxs-lookup"><span data-stu-id="fb4c3-109">Equality Operators on Value Types</span></span>
 <span data-ttu-id="fb4c3-110">✔️如果相等性是有意义的，则对值类型重载相等运算符。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-110">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="fb4c3-111">在大多数编程语言中，值类型没有的默认实现 `operator==` 。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="fb4c3-112">引用类型上的相等运算符</span><span class="sxs-lookup"><span data-stu-id="fb4c3-112">Equality Operators on Reference Types</span></span>
 <span data-ttu-id="fb4c3-113">❌避免对可变引用类型重载相等运算符。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-113">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="fb4c3-114">许多语言具有用于引用类型的内置相等运算符。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="fb4c3-115">内置运算符通常实现引用相等性，而当默认行为更改为值相等性时，很多开发人员都很惊讶。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="fb4c3-116">对于不可变的引用类型，此问题将得到缓解，因为不可变性使发现引用相等性和值相等性之间的差异变得更加困难。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="fb4c3-117">❌如果实现的速度远远低于引用相等性，请避免对引用类型重载相等运算符。</span><span class="sxs-lookup"><span data-stu-id="fb4c3-117">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="fb4c3-118">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="fb4c3-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="fb4c3-119">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="fb4c3-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="fb4c3-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb4c3-120">See also</span></span>

- [<span data-ttu-id="fb4c3-121">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="fb4c3-121">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="fb4c3-122">使用准则</span><span class="sxs-lookup"><span data-stu-id="fb4c3-122">Usage Guidelines</span></span>](usage-guidelines.md)
