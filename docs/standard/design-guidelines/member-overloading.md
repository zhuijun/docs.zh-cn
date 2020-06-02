---
title: 成员重载
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: 6a2cd6d4dd293a7f4a408e1ee97a125c9454be41
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289000"
---
# <a name="member-overloading"></a><span data-ttu-id="4cf13-102">成员重载</span><span class="sxs-lookup"><span data-stu-id="4cf13-102">Member Overloading</span></span>
<span data-ttu-id="4cf13-103">成员重载意味着在同一类型上创建两个或多个成员，这些成员仅在参数的数量或类型中不同，但具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="4cf13-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="4cf13-104">例如，在下面的中，将 `WriteLine` 重载方法：</span><span class="sxs-lookup"><span data-stu-id="4cf13-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="4cf13-105">由于只有方法、构造函数和索引属性可以有参数，因此只能重载这些成员。</span><span class="sxs-lookup"><span data-stu-id="4cf13-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="4cf13-106">重载是提高可重用库的可用性、生产力和可读性的最重要方法之一。</span><span class="sxs-lookup"><span data-stu-id="4cf13-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="4cf13-107">参数数量重载使您可以提供更简单的构造函数和方法版本。</span><span class="sxs-lookup"><span data-stu-id="4cf13-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="4cf13-108">使用参数类型的重载，可以为在所选的不同类型集上执行相同操作的成员使用相同的成员名称。</span><span class="sxs-lookup"><span data-stu-id="4cf13-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="4cf13-109">✔️尝试使用描述性参数名称来指示较短重载使用的默认值。</span><span class="sxs-lookup"><span data-stu-id="4cf13-109">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="4cf13-110">❌避免在重载中随意改变参数名称。</span><span class="sxs-lookup"><span data-stu-id="4cf13-110">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="4cf13-111">如果一个重载中的参数表示与另一个重载中的参数相同的输入，则这些参数应具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="4cf13-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="4cf13-112">❌避免在重载成员的参数顺序中不一致。</span><span class="sxs-lookup"><span data-stu-id="4cf13-112">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="4cf13-113">具有相同名称的参数应出现在所有重载的同一位置。</span><span class="sxs-lookup"><span data-stu-id="4cf13-113">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="4cf13-114">✔️仅使最长重载虚拟（如果需要可扩展性）。</span><span class="sxs-lookup"><span data-stu-id="4cf13-114">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="4cf13-115">更短的重载只需调用更长的重载。</span><span class="sxs-lookup"><span data-stu-id="4cf13-115">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="4cf13-116">❌不要使用 `ref` 或 `out` 修饰符重载成员。</span><span class="sxs-lookup"><span data-stu-id="4cf13-116">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="4cf13-117">某些语言无法解析对重载的调用。</span><span class="sxs-lookup"><span data-stu-id="4cf13-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="4cf13-118">此外，此类重载通常具有完全不同的语义，但可能不应作为重载，而是使用两种不同的方法。</span><span class="sxs-lookup"><span data-stu-id="4cf13-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="4cf13-119">❌不要让重载的参数的位置和类型与语义不同。</span><span class="sxs-lookup"><span data-stu-id="4cf13-119">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="4cf13-120">`null`对于可选参数，✔️允许传递。</span><span class="sxs-lookup"><span data-stu-id="4cf13-120">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="4cf13-121">✔️确实使用成员重载，而不是使用默认参数定义成员。</span><span class="sxs-lookup"><span data-stu-id="4cf13-121">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="4cf13-122">默认参数不符合 CLS。</span><span class="sxs-lookup"><span data-stu-id="4cf13-122">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="4cf13-123">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="4cf13-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="4cf13-124">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="4cf13-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="4cf13-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4cf13-125">See also</span></span>

- [<span data-ttu-id="4cf13-126">成员设计准则</span><span class="sxs-lookup"><span data-stu-id="4cf13-126">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="4cf13-127">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="4cf13-127">Framework Design Guidelines</span></span>](index.md)
