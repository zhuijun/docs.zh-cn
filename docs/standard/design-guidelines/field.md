---
title: 字段设计
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 3a5ae985ab161899fbb5e96f9b0ef0cfa90b957c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289741"
---
# <a name="field-design"></a><span data-ttu-id="117da-102">字段设计</span><span class="sxs-lookup"><span data-stu-id="117da-102">Field Design</span></span>
<span data-ttu-id="117da-103">封装原则是面向对象的设计中最重要的概念之一。</span><span class="sxs-lookup"><span data-stu-id="117da-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="117da-104">此原则表明，存储在对象中的数据应只能访问该对象。</span><span class="sxs-lookup"><span data-stu-id="117da-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>

 <span data-ttu-id="117da-105">解释此原则的一种有用方法是说，应设计一个类型，以便在不中断类型成员的代码的情况下，对该类型的字段进行更改（名称或类型更改）。</span><span class="sxs-lookup"><span data-stu-id="117da-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="117da-106">此解释会立即表示所有字段都必须是私有的。</span><span class="sxs-lookup"><span data-stu-id="117da-106">This interpretation immediately implies that all fields must be private.</span></span>

 <span data-ttu-id="117da-107">我们从此严格限制中排除了常量和静态只读字段，因为此类字段（几乎按定义）从不需要更改。</span><span class="sxs-lookup"><span data-stu-id="117da-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>

 <span data-ttu-id="117da-108">❌不要提供公共或受保护的实例字段。</span><span class="sxs-lookup"><span data-stu-id="117da-108">❌ DO NOT provide instance fields that are public or protected.</span></span>

 <span data-ttu-id="117da-109">应提供用于访问字段的属性，而不是将其设为公共或受保护。</span><span class="sxs-lookup"><span data-stu-id="117da-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>

 <span data-ttu-id="117da-110">✔️对永远不会更改的常量使用常量字段。</span><span class="sxs-lookup"><span data-stu-id="117da-110">✔️ DO use constant fields for constants that will never change.</span></span>

 <span data-ttu-id="117da-111">编译器会直接将常量字段的值直接引入到调用代码。</span><span class="sxs-lookup"><span data-stu-id="117da-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="117da-112">因此，可能永远不会更改常量值，而不会带来中断兼容性的风险。</span><span class="sxs-lookup"><span data-stu-id="117da-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>

 <span data-ttu-id="117da-113">✔️ `readonly` 对预定义对象实例使用公共静态字段。</span><span class="sxs-lookup"><span data-stu-id="117da-113">✔️ DO use public static `readonly` fields for predefined object instances.</span></span>

 <span data-ttu-id="117da-114">如果有类型的预定义实例，请将它们声明为类型本身的公共只读静态字段。</span><span class="sxs-lookup"><span data-stu-id="117da-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>

 <span data-ttu-id="117da-115">❌不要将可变类型的实例分配给 `readonly` 字段。</span><span class="sxs-lookup"><span data-stu-id="117da-115">❌ DO NOT assign instances of mutable types to `readonly` fields.</span></span>

 <span data-ttu-id="117da-116">可变类型是具有实例的类型，这些实例可在实例化后进行修改。</span><span class="sxs-lookup"><span data-stu-id="117da-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="117da-117">例如，数组、大多数集合和流都是可变类型，但 <xref:System.Int32?displayProperty=nameWithType> 、 <xref:System.Uri?displayProperty=nameWithType> 和 <xref:System.String?displayProperty=nameWithType> 都是不可变的。</span><span class="sxs-lookup"><span data-stu-id="117da-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="117da-118">引用类型字段上的只读修饰符可防止替换存储在字段中的实例，但它不会通过调用更改实例的成员来防止修改字段的实例数据。</span><span class="sxs-lookup"><span data-stu-id="117da-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>

 <span data-ttu-id="117da-119">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="117da-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="117da-120">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="117da-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="117da-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="117da-121">See also</span></span>

- [<span data-ttu-id="117da-122">成员设计准则</span><span class="sxs-lookup"><span data-stu-id="117da-122">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="117da-123">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="117da-123">Framework Design Guidelines</span></span>](index.md)
