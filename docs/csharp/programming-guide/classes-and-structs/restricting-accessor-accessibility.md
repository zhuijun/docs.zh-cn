---
title: 限制访问器可访问性 - C# 编程指南
description: 默认情况下，C# 中属性的 get 和 set 访问器与它们所属的属性在具有相同的可见性或访问级别。 你可以限制访问。
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: be7be4fc67a9a6f62a71f8473d6daa1fac49e842
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199024"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="d2993-104">限制访问器可访问性（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="d2993-104">Restricting Accessor Accessibility (C# Programming Guide)</span></span>

<span data-ttu-id="d2993-105">属性或索引器的 [get](../../language-reference/keywords/get.md) 和 [set](../../language-reference/keywords/set.md) 部分称为访问器。</span><span class="sxs-lookup"><span data-stu-id="d2993-105">The [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="d2993-106">默认情况下，这些访问器具有与其所属属性或索引器相同的可见性或访问级别。</span><span class="sxs-lookup"><span data-stu-id="d2993-106">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="d2993-107">有关详细信息，请参阅[可访问性级别](../../language-reference/keywords/accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d2993-107">For more information, see [accessibility levels](../../language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="d2993-108">不过，有时限制对其中某个访问器的访问是有益的。</span><span class="sxs-lookup"><span data-stu-id="d2993-108">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="d2993-109">通常是在保持 `get` 访问器可公开访问的情况下，限制 `set` 访问器的可访问性。</span><span class="sxs-lookup"><span data-stu-id="d2993-109">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="d2993-110">例如：</span><span class="sxs-lookup"><span data-stu-id="d2993-110">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="d2993-111">在此示例中，名为 `Name` 的属性定义 `get` 访问器和 `set` 访问器。</span><span class="sxs-lookup"><span data-stu-id="d2993-111">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="d2993-112">`get` 访问器接收该属性本身的可访问性级别（此示例中为 `public`），而对于 `set` 访问器，则通过对该访问器本身应用 [protected](../../language-reference/keywords/protected.md) 访问修饰符来进行显式限制。</span><span class="sxs-lookup"><span data-stu-id="d2993-112">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="d2993-113">对访问器的访问修饰符的限制</span><span class="sxs-lookup"><span data-stu-id="d2993-113">Restrictions on Access Modifiers on Accessors</span></span>  

 <span data-ttu-id="d2993-114">对属性或索引器使用访问修饰符受以下条件的制约：</span><span class="sxs-lookup"><span data-stu-id="d2993-114">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
- <span data-ttu-id="d2993-115">不能对接口或显式[接口](../../language-reference/keywords/interface.md)成员实现使用访问器修饰符。</span><span class="sxs-lookup"><span data-stu-id="d2993-115">You cannot use accessor modifiers on an interface or an explicit [interface](../../language-reference/keywords/interface.md) member implementation.</span></span>  
  
- <span data-ttu-id="d2993-116">仅当属性或索引器同时具有 `set` 和 `get` 访问器时，才能使用访问器修饰符。</span><span class="sxs-lookup"><span data-stu-id="d2993-116">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="d2993-117">这种情况下，只允许对其中一个访问器使用修饰符。</span><span class="sxs-lookup"><span data-stu-id="d2993-117">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
- <span data-ttu-id="d2993-118">如果属性或索引器具有 [override](../../language-reference/keywords/override.md) 修饰符，则访问器修饰符必须与重写的访问器的访问器（如有）匹配。</span><span class="sxs-lookup"><span data-stu-id="d2993-118">If the property or indexer has an [override](../../language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
- <span data-ttu-id="d2993-119">访问器的可访问性级别必须比属性或索引器本身的可访问性级别具有更严格的限制。</span><span class="sxs-lookup"><span data-stu-id="d2993-119">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="d2993-120">重写访问器的访问修饰符</span><span class="sxs-lookup"><span data-stu-id="d2993-120">Access Modifiers on Overriding Accessors</span></span>  

 <span data-ttu-id="d2993-121">重写属性或索引器时，被重写的访问器对重写代码而言必须是可访问的。</span><span class="sxs-lookup"><span data-stu-id="d2993-121">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="d2993-122">此外，属性/索引器及其访问器的可访问性都必须与相应的被重写属性/索引器及其访问器匹配。</span><span class="sxs-lookup"><span data-stu-id="d2993-122">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="d2993-123">例如：</span><span class="sxs-lookup"><span data-stu-id="d2993-123">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="d2993-124">实现接口</span><span class="sxs-lookup"><span data-stu-id="d2993-124">Implementing Interfaces</span></span>  

 <span data-ttu-id="d2993-125">使用访问器实现接口时，访问器不一定有访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="d2993-125">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="d2993-126">但如果使用一个访问器（如 `get`）实现接口，则另一个访问器可以具有访问修饰符，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="d2993-126">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="d2993-127">访问器可访问性域</span><span class="sxs-lookup"><span data-stu-id="d2993-127">Accessor Accessibility Domain</span></span>  

 <span data-ttu-id="d2993-128">如果对访问器使用访问修饰符，则访问器的[可访问性域](../../language-reference/keywords/accessibility-domain.md)由该修饰符确定。</span><span class="sxs-lookup"><span data-stu-id="d2993-128">If you use an access modifier on the accessor, the [accessibility domain](../../language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="d2993-129">如果未对访问器使用访问修饰符，则访问器的可访问性域由属性或索引器的可访问性级别确定。</span><span class="sxs-lookup"><span data-stu-id="d2993-129">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2993-130">示例</span><span class="sxs-lookup"><span data-stu-id="d2993-130">Example</span></span>  

 <span data-ttu-id="d2993-131">下面的示例包含三个类：`BaseClass`、`DerivedClass` 和 `MainClass`。</span><span class="sxs-lookup"><span data-stu-id="d2993-131">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="d2993-132">每个类的 `BaseClass`、`Name` 和 `Id` 都有两个属性。</span><span class="sxs-lookup"><span data-stu-id="d2993-132">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="d2993-133">该示例演示在使用限制性访问修饰符（如 [protected](../../language-reference/keywords/protected.md) 或 [private](../../language-reference/keywords/private.md)）时，`BaseClass` 的 `Id` 属性如何隐藏 `DerivedClass` 的 `Id` 属性。</span><span class="sxs-lookup"><span data-stu-id="d2993-133">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../language-reference/keywords/protected.md) or [private](../../language-reference/keywords/private.md).</span></span> <span data-ttu-id="d2993-134">因此，向该属性赋值时将调用 `BaseClass` 类中的属性。</span><span class="sxs-lookup"><span data-stu-id="d2993-134">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="d2993-135">将访问修饰符替换为 [public](../../language-reference/keywords/public.md) 将使该属性可供访问。</span><span class="sxs-lookup"><span data-stu-id="d2993-135">Replacing the access modifier by [public](../../language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="d2993-136">该示例还演示 `DerivedClass` 中 `Name` 属性上 `set` 访问器的限制性访问修饰符（如 `private` 或 `protected`）如何防止对该访问器的访问，并在向它赋值时生成错误。</span><span class="sxs-lookup"><span data-stu-id="d2993-136">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="d2993-137">注释</span><span class="sxs-lookup"><span data-stu-id="d2993-137">Comments</span></span>  

 <span data-ttu-id="d2993-138">注意，如果将声明 `new private string Id` 替换为 `new public string Id`，则得到如下输出：</span><span class="sxs-lookup"><span data-stu-id="d2993-138">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="d2993-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="d2993-139">See also</span></span>

- [<span data-ttu-id="d2993-140">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="d2993-140">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d2993-141">属性</span><span class="sxs-lookup"><span data-stu-id="d2993-141">Properties</span></span>](./properties.md)
- [<span data-ttu-id="d2993-142">索引器</span><span class="sxs-lookup"><span data-stu-id="d2993-142">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="d2993-143">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="d2993-143">Access Modifiers</span></span>](./access-modifiers.md)
