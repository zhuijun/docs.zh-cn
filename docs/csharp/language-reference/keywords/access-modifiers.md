---
description: 访问修饰符 - C# 参考
title: 访问修饰符 - C# 参考
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: e941fc673c508f10863ee49b6544d6886bd594a3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168811"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="3d4a6-103">访问修饰符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="3d4a6-103">Access Modifiers (C# Reference)</span></span>

<span data-ttu-id="3d4a6-104">访问修饰符是关键字，用于指定成员或类型已声明的可访问性。</span><span class="sxs-lookup"><span data-stu-id="3d4a6-104">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="3d4a6-105">本部分介绍四个访问修饰符：</span><span class="sxs-lookup"><span data-stu-id="3d4a6-105">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="3d4a6-106">可使用访问修饰符指定以下六个可访问性级别：</span><span class="sxs-lookup"><span data-stu-id="3d4a6-106">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="3d4a6-107">[`public`](public.md)：访问不受限制。</span><span class="sxs-lookup"><span data-stu-id="3d4a6-107">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="3d4a6-108">[`protected`](protected.md)：访问限于包含类或派生自包含类的类型。</span><span class="sxs-lookup"><span data-stu-id="3d4a6-108">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="3d4a6-109">[`internal`](internal.md)：访问限于当前程序集。</span><span class="sxs-lookup"><span data-stu-id="3d4a6-109">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="3d4a6-110">[`protected internal`](protected-internal.md)：访问限于当前程序集或派生自包含类的类型。</span><span class="sxs-lookup"><span data-stu-id="3d4a6-110">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="3d4a6-111">[`private`](private.md)：访问限于包含类。</span><span class="sxs-lookup"><span data-stu-id="3d4a6-111">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="3d4a6-112">[`private protected`](private-protected.md)：访问限于包含类或当前程序集中派生自包含类的类型。</span><span class="sxs-lookup"><span data-stu-id="3d4a6-112">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="3d4a6-113">本部分还介绍以下内容：</span><span class="sxs-lookup"><span data-stu-id="3d4a6-113">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="3d4a6-114">[可访问性级别](./accessibility-levels.md)：使用四种访问修饰符，声明六个可访问性级别。</span><span class="sxs-lookup"><span data-stu-id="3d4a6-114">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="3d4a6-115">[可访问性域](./accessibility-domain.md)：指定可在程序段中的何处引用成员。</span><span class="sxs-lookup"><span data-stu-id="3d4a6-115">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="3d4a6-116">[对使用可访问性级别的限制](./restrictions-on-using-accessibility-levels.md)：概括对使用已声明的可访问性级别的限制。</span><span class="sxs-lookup"><span data-stu-id="3d4a6-116">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4a6-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="3d4a6-117">See also</span></span>

- [<span data-ttu-id="3d4a6-118">C# 参考</span><span class="sxs-lookup"><span data-stu-id="3d4a6-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3d4a6-119">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="3d4a6-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3d4a6-120">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="3d4a6-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="3d4a6-121">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="3d4a6-121">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="3d4a6-122">访问关键字</span><span class="sxs-lookup"><span data-stu-id="3d4a6-122">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="3d4a6-123">修饰符</span><span class="sxs-lookup"><span data-stu-id="3d4a6-123">Modifiers</span></span>](index.md)
