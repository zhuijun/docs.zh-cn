---
title: 类型成员的名称
description: 了解在 .NET 中命名类型成员的准则，如方法、属性、事件和字段。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: de613673989bd174ac80adda566d04600059642d
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662493"
---
# <a name="names-of-type-members"></a><span data-ttu-id="78cba-103">类型成员的名称</span><span class="sxs-lookup"><span data-stu-id="78cba-103">Names of Type Members</span></span>
<span data-ttu-id="78cba-104">类型由以下成员构成：方法、属性、事件、构造函数和字段。</span><span class="sxs-lookup"><span data-stu-id="78cba-104">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="78cba-105">以下各节介绍命名类型成员的准则。</span><span class="sxs-lookup"><span data-stu-id="78cba-105">The following sections describe guidelines for naming type members.</span></span>

## <a name="names-of-methods"></a><span data-ttu-id="78cba-106">方法的名称</span><span class="sxs-lookup"><span data-stu-id="78cba-106">Names of Methods</span></span>
 <span data-ttu-id="78cba-107">方法是执行操作的方式，设计准则要求方法名称为谓词或谓词短语。</span><span class="sxs-lookup"><span data-stu-id="78cba-107">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="78cba-108">遵循此准则，还有利于区分方法名称与属性和类型名称，后者为名词或形容词性短语。</span><span class="sxs-lookup"><span data-stu-id="78cba-108">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>

 <span data-ttu-id="78cba-109">✔️为谓词或谓词短语指定方法名称。</span><span class="sxs-lookup"><span data-stu-id="78cba-109">✔️ DO give methods names that are verbs or verb phrases.</span></span>

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a><span data-ttu-id="78cba-110">属性的名称</span><span class="sxs-lookup"><span data-stu-id="78cba-110">Names of Properties</span></span>
 <span data-ttu-id="78cba-111">与其他成员不同，应向属性给定名词性短语或形容词性名称。</span><span class="sxs-lookup"><span data-stu-id="78cba-111">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="78cba-112">这是因为属性是指数据，属性的名称应反映这一点。</span><span class="sxs-lookup"><span data-stu-id="78cba-112">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="78cba-113">属性名称总是采用帕斯卡大小写。</span><span class="sxs-lookup"><span data-stu-id="78cba-113">PascalCasing is always used for property names.</span></span>

 <span data-ttu-id="78cba-114">✔️使用名词、名词短语或形容词名称属性。</span><span class="sxs-lookup"><span data-stu-id="78cba-114">✔️ DO name properties using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="78cba-115">❌没有与 "Get" 方法的名称相匹配的属性，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="78cba-115">❌ DO NOT have properties that match the name of "Get" methods as in the following example:</span></span>

 <span data-ttu-id="78cba-116">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span><span class="sxs-lookup"><span data-stu-id="78cba-116">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span></span>

 <span data-ttu-id="78cba-117">此模式通常意味着该属性事实上是一种方法。</span><span class="sxs-lookup"><span data-stu-id="78cba-117">This pattern typically indicates that the property should really be a method.</span></span>

 <span data-ttu-id="78cba-118">✔️使用一个复数短语来描述集合中的项，而不是使用后跟 "List" 或 "Collection" 的短语来命名集合属性。</span><span class="sxs-lookup"><span data-stu-id="78cba-118">✔️ DO name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection".</span></span>

 <span data-ttu-id="78cba-119">✔️使用赞成短语（ `CanSeek` 而不是）命名布尔属性 `CantSeek` 。</span><span class="sxs-lookup"><span data-stu-id="78cba-119">✔️ DO name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="78cba-120">或者，还可以在布尔属性前面添加 "Is"、"Can" 或 "has" 前缀，但前提是在它添加值的位置。</span><span class="sxs-lookup"><span data-stu-id="78cba-120">Optionally, you can also prefix Boolean properties with "Is", "Can", or "Has", but only where it adds value.</span></span>

 <span data-ttu-id="78cba-121">✔️考虑为属性提供与其类型相同的名称。</span><span class="sxs-lookup"><span data-stu-id="78cba-121">✔️ CONSIDER giving a property the same name as its type.</span></span>

 <span data-ttu-id="78cba-122">例如，以下属性可正确获取和设置名为 `Color` 的枚举值，因此属性名为 `Color`：</span><span class="sxs-lookup"><span data-stu-id="78cba-122">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a><span data-ttu-id="78cba-123">事件的名称</span><span class="sxs-lookup"><span data-stu-id="78cba-123">Names of Events</span></span>
 <span data-ttu-id="78cba-124">事件始终指操作，可以是即将发生的，也可以是已经发生的。</span><span class="sxs-lookup"><span data-stu-id="78cba-124">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="78cba-125">因此，对于方法，事件用谓词命名，并用谓词时态指示引发事件的时间。</span><span class="sxs-lookup"><span data-stu-id="78cba-125">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>

 <span data-ttu-id="78cba-126">✔️使用动词或动词短语来命名事件。</span><span class="sxs-lookup"><span data-stu-id="78cba-126">✔️ DO name events with a verb or a verb phrase.</span></span>

 <span data-ttu-id="78cba-127">示例包括`Clicked`、`Painting` 和 `DroppedDown`。</span><span class="sxs-lookup"><span data-stu-id="78cba-127">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>

 <span data-ttu-id="78cba-128">✔️使用现有的和过去的时态为事件名称提供前后的概念。</span><span class="sxs-lookup"><span data-stu-id="78cba-128">✔️ DO give events names with a concept of before and after, using the present and past tenses.</span></span>

 <span data-ttu-id="78cba-129">例如，在窗口关闭前引发的关闭事件可命名为 `Closing`，而在窗口关闭后后引发的关闭事件可命名为 `Closed`。</span><span class="sxs-lookup"><span data-stu-id="78cba-129">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>

 <span data-ttu-id="78cba-130">❌不要使用 "Before" 或 "After" 前缀或 postfixes 来指示前和后事件。</span><span class="sxs-lookup"><span data-stu-id="78cba-130">❌ DO NOT use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="78cba-131">请如上所示使用现在时和过去时。</span><span class="sxs-lookup"><span data-stu-id="78cba-131">Use present and past tenses as just described.</span></span>

 <span data-ttu-id="78cba-132">✔️使用 "EventHandler" 后缀来命名事件处理程序（用作事件类型的委托），如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="78cba-132">✔️ DO name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 <span data-ttu-id="78cba-133">✔️确实要 `sender` `e` 在事件处理程序中使用两个名为和的参数。</span><span class="sxs-lookup"><span data-stu-id="78cba-133">✔️ DO use two parameters named `sender` and `e` in event handlers.</span></span>

 <span data-ttu-id="78cba-134">sender 参数表示引发事件的对象。</span><span class="sxs-lookup"><span data-stu-id="78cba-134">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="78cba-135">sender 参数的类型通常是 `object`，即使可以使用更具体的类型。</span><span class="sxs-lookup"><span data-stu-id="78cba-135">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>

 <span data-ttu-id="78cba-136">✔️用 "EventArgs" 后缀命名事件参数类。</span><span class="sxs-lookup"><span data-stu-id="78cba-136">✔️ DO name event argument classes with the "EventArgs" suffix.</span></span>

## <a name="names-of-fields"></a><span data-ttu-id="78cba-137">字段的名称</span><span class="sxs-lookup"><span data-stu-id="78cba-137">Names of Fields</span></span>
 <span data-ttu-id="78cba-138">字段命名准则适用于静态公开字段和受保护的字段。</span><span class="sxs-lookup"><span data-stu-id="78cba-138">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="78cba-139">原则不涉及内部和专用字段，而[成员设计准则](member.md)不允许使用公开字段或受保护的实例字段。</span><span class="sxs-lookup"><span data-stu-id="78cba-139">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](member.md).</span></span>

 <span data-ttu-id="78cba-140">✔️在字段名称中使用 PascalCasing。</span><span class="sxs-lookup"><span data-stu-id="78cba-140">✔️ DO use PascalCasing in field names.</span></span>

 <span data-ttu-id="78cba-141">✔️使用名词、名词短语或形容词来命名字段。</span><span class="sxs-lookup"><span data-stu-id="78cba-141">✔️ DO name fields using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="78cba-142">❌不要对字段名称使用前缀。</span><span class="sxs-lookup"><span data-stu-id="78cba-142">❌ DO NOT use a prefix for field names.</span></span>

 <span data-ttu-id="78cba-143">例如，请勿使用“g_”或“s_”来指示静态字段。</span><span class="sxs-lookup"><span data-stu-id="78cba-143">For example, do not use "g_" or "s_" to indicate static fields.</span></span>

 <span data-ttu-id="78cba-144">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="78cba-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="78cba-145">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="78cba-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="78cba-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78cba-146">See also</span></span>

- [<span data-ttu-id="78cba-147">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="78cba-147">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="78cba-148">命名准则</span><span class="sxs-lookup"><span data-stu-id="78cba-148">Naming Guidelines</span></span>](naming-guidelines.md)
