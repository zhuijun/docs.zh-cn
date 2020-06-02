---
title: 扩展方法
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 77c012d7838ae2fa1f62163bc58520db67c64ce5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289754"
---
# <a name="extension-methods"></a><span data-ttu-id="e5ed3-102">扩展方法</span><span class="sxs-lookup"><span data-stu-id="e5ed3-102">Extension methods</span></span>

<span data-ttu-id="e5ed3-103">扩展方法是一项语言功能，允许使用实例方法调用语法来调用静态方法。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-103">Extension methods are a language feature that allows static methods to be called using instance-method call syntax.</span></span> <span data-ttu-id="e5ed3-104">这些方法必须至少采用一个参数，该参数表示方法要操作的实例。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-104">These methods must take at least one parameter, which represents the instance the method is to operate on.</span></span>

 <span data-ttu-id="e5ed3-105">定义扩展方法的类称为 "发起方" 类，并且必须声明为 `static` 。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-105">The class that defines an extension method is referred to as the "sponsor" class, and it must be declared as `static`.</span></span> <span data-ttu-id="e5ed3-106">若要使用扩展方法，必须导入用于定义主办方类的命名空间。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-106">To use extension methods, you must import the namespace that defines the sponsor class.</span></span>

 <span data-ttu-id="e5ed3-107">❌避免过度利用扩展方法，特别是对于不属于您的类型。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-107">❌ AVOID overuse of extension methods, especially on types you don't own.</span></span>

 <span data-ttu-id="e5ed3-108">如果你有自己的源代码，请考虑改用正则实例方法。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-108">If you do own source code of a type, consider using regular instance methods instead.</span></span> <span data-ttu-id="e5ed3-109">如果你没有源代码，并且想要添加方法，请务必小心。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-109">If you don't own the source code and you want to add a method, be very careful.</span></span> <span data-ttu-id="e5ed3-110">使用扩展方法可能会打乱未设计为具有这些方法的类型的 Api。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-110">Liberal use of extension methods has the potential of cluttering APIs of types that were not designed to have these methods.</span></span>

 <span data-ttu-id="e5ed3-111">✔️考虑在以下任何情况下使用扩展方法：</span><span class="sxs-lookup"><span data-stu-id="e5ed3-111">✔️ CONSIDER using extension methods in any of the following scenarios:</span></span>

- <span data-ttu-id="e5ed3-112">若要提供与接口的每个实现相关的帮助器功能，如果可以使用核心接口编写所述的功能。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-112">To provide helper functionality relevant to every implementation of an interface, if said functionality can be written in terms of the core interface.</span></span> <span data-ttu-id="e5ed3-113">这是因为不能以其他方式将具体实现分配给接口。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-113">This is because concrete implementations cannot otherwise be assigned to interfaces.</span></span> <span data-ttu-id="e5ed3-114">例如，LINQ to Objects 运算符实现为所有类型的扩展方法 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-114">For example, the LINQ to Objects operators are implemented as extension methods for all <xref:System.Collections.Generic.IEnumerable%601> types.</span></span> <span data-ttu-id="e5ed3-115">因此，任何 `IEnumerable<>` 实现都会自动启用 LINQ。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-115">Thus, any `IEnumerable<>` implementation is automatically LINQ-enabled.</span></span>

- <span data-ttu-id="e5ed3-116">当实例方法会引入某个类型的依赖项时，但此类依赖项会破坏依赖项管理规则。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-116">When an instance method would introduce a dependency on some type, but such a dependency would break dependency management rules.</span></span> <span data-ttu-id="e5ed3-117">例如，从到的依赖 <xref:System.String> 项 <xref:System.Uri?displayProperty=nameWithType> 可能不是必需的，因此， `String.ToUri()` `System.Uri` 从依赖项管理的角度来看，返回的实例方法将是错误的设计。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-117">For example, a dependency from <xref:System.String> to <xref:System.Uri?displayProperty=nameWithType> is probably not desirable, and so `String.ToUri()` instance method returning `System.Uri` would be the wrong design from a dependency management perspective.</span></span> <span data-ttu-id="e5ed3-118">静态扩展方法 `Uri.ToUri(this string str)` 返回 `System.Uri` 的设计是一个更好的设计。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-118">A static extension method `Uri.ToUri(this string str)` returning `System.Uri` would be a much better design.</span></span>

 <span data-ttu-id="e5ed3-119">❌避免在上定义扩展方法 <xref:System.Object?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-119">❌ AVOID defining extension methods on <xref:System.Object?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="e5ed3-120">Visual Basic 用户将无法使用扩展方法语法对对象引用调用此类方法。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-120">Visual Basic users will not be able to call such methods on object references using the extension method syntax.</span></span> <span data-ttu-id="e5ed3-121">在 Visual Basic 中，将引用声明为 `Object` 会强制其上的所有方法调用都是后期绑定的（这意味着调用的实际成员是在运行时确定的。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-121">In Visual Basic, declaring a reference as `Object` forces all method invocations on it to be late bound (which means the actual member called is determined at run time).</span></span> <span data-ttu-id="e5ed3-122">绑定到扩展方法在编译时（早期绑定）确定。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-122">Bindings to extension methods are determined at compile time (early bound).</span></span>

 <span data-ttu-id="e5ed3-123">此指导原则适用于存在相同绑定行为或不支持扩展方法的其他语言。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-123">This guideline applies to other languages where the same binding behavior is present or where extension methods are not supported.</span></span>

 <span data-ttu-id="e5ed3-124">❌不要将扩展方法放在与扩展类型相同的命名空间中，除非它用于向接口添加方法或用于依赖项管理。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-124">❌ DO NOT put extension methods in the same namespace as the extended type unless it is for adding methods to interfaces or for dependency management.</span></span>

 <span data-ttu-id="e5ed3-125">❌避免定义具有相同签名的两个或多个扩展方法，即使它们驻留在不同的命名空间中。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-125">❌ AVOID defining two or more extension methods with the same signature, even if they reside in different namespaces.</span></span>

 <span data-ttu-id="e5ed3-126">如果类型是一个接口，则✔️考虑在与扩展类型相同的命名空间中定义扩展方法，并且在大多数或所有情况下都使用扩展方法。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-126">✔️ CONSIDER defining extension methods in the same namespace as the extended type if the type is an interface and if the extension methods are meant to be used in most or all cases.</span></span>

 <span data-ttu-id="e5ed3-127">❌不要定义实现通常与其他功能关联的命名空间中的功能的扩展方法。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-127">❌ DO NOT define extension methods implementing a feature in namespaces normally associated with other features.</span></span> <span data-ttu-id="e5ed3-128">而应在与它们所属的功能关联的命名空间中进行定义。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-128">Instead, define them in the namespace associated with the feature they belong to.</span></span>

 <span data-ttu-id="e5ed3-129">❌避免命名空间专用于扩展方法（例如 "Extension"）的命名空间。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-129">❌ AVOID generic naming of namespaces dedicated to extension methods (e.g., "Extensions").</span></span> <span data-ttu-id="e5ed3-130">请改用描述性名称（例如，"路由"）。</span><span class="sxs-lookup"><span data-stu-id="e5ed3-130">Use a descriptive name (e.g., "Routing") instead.</span></span>

 <span data-ttu-id="e5ed3-131">*部分 &copy; 2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="e5ed3-131">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e5ed3-132">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="e5ed3-132">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e5ed3-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5ed3-133">See also</span></span>

- [<span data-ttu-id="e5ed3-134">成员设计准则</span><span class="sxs-lookup"><span data-stu-id="e5ed3-134">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="e5ed3-135">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="e5ed3-135">Framework Design Guidelines</span></span>](index.md)
