---
title: 依赖项属性
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: 476ef1bb1ac5ec1f551979c64a41cbae55c554bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280252"
---
# <a name="dependency-properties"></a><span data-ttu-id="7d057-102">依赖项属性</span><span class="sxs-lookup"><span data-stu-id="7d057-102">Dependency Properties</span></span>
<span data-ttu-id="7d057-103">依赖属性（DP）是常规属性，它将其值存储在属性存储中，而不是将其存储在类型变量（字段）中。</span><span class="sxs-lookup"><span data-stu-id="7d057-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>

 <span data-ttu-id="7d057-104">附加的依赖属性是作为静态 Get 和 Set 方法建模的一种依赖属性，它们表示 "属性"，描述对象及其容器之间的关系（例如， `Button` 对象在容器上的位置 `Panel` ）。</span><span class="sxs-lookup"><span data-stu-id="7d057-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>

 <span data-ttu-id="7d057-105">如果需要属性来支持 WPF 功能，如样式、触发器、数据绑定、动画、动态资源和继承，✔️提供依赖属性。</span><span class="sxs-lookup"><span data-stu-id="7d057-105">✔️ DO provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>

## <a name="dependency-property-design"></a><span data-ttu-id="7d057-106">依赖项属性设计</span><span class="sxs-lookup"><span data-stu-id="7d057-106">Dependency Property Design</span></span>
 <span data-ttu-id="7d057-107"><xref:System.Windows.DependencyObject>当实现依赖项属性时，✔️确实从或它的一个子类型继承。</span><span class="sxs-lookup"><span data-stu-id="7d057-107">✔️ DO inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="7d057-108">类型提供了一种非常有效的属性存储实现，并自动支持 WPF 数据绑定。</span><span class="sxs-lookup"><span data-stu-id="7d057-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>

 <span data-ttu-id="7d057-109">✔️ <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> 为每个依赖属性提供一个常规 CLR 属性和一个存储实例的公共静态只读字段。</span><span class="sxs-lookup"><span data-stu-id="7d057-109">✔️ DO provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>

 <span data-ttu-id="7d057-110">✔️通过调用实例方法和实现依赖项 <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> 属性 <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7d057-110">✔️ DO implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="7d057-111">✔️通过将属性的名称 suffixing 为 "属性"，来命名依赖属性静态字段。</span><span class="sxs-lookup"><span data-stu-id="7d057-111">✔️ DO name the dependency property static field by suffixing the name of the property with "Property."</span></span>

 <span data-ttu-id="7d057-112">❌不要在代码中显式设置依赖项属性的默认值;请改为在元数据中设置它们。</span><span class="sxs-lookup"><span data-stu-id="7d057-112">❌ DO NOT set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>

 <span data-ttu-id="7d057-113">如果显式设置了属性默认值，则可能会阻止某些隐式方式（如样式）设置该属性。</span><span class="sxs-lookup"><span data-stu-id="7d057-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>

 <span data-ttu-id="7d057-114">❌不要将代码放在属性访问器中，而不是标准代码访问静态字段。</span><span class="sxs-lookup"><span data-stu-id="7d057-114">❌ DO NOT put code in the property accessors other than the standard code to access the static field.</span></span>

 <span data-ttu-id="7d057-115">如果通过隐式方式（如样式）设置属性，则不会执行该代码，因为样式设置直接使用静态字段。</span><span class="sxs-lookup"><span data-stu-id="7d057-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>

 <span data-ttu-id="7d057-116">❌不要使用依赖项属性来存储安全数据。</span><span class="sxs-lookup"><span data-stu-id="7d057-116">❌ DO NOT use dependency properties to store secure data.</span></span> <span data-ttu-id="7d057-117">甚至可以公开访问专用依赖属性。</span><span class="sxs-lookup"><span data-stu-id="7d057-117">Even private dependency properties can be accessed publicly.</span></span>

## <a name="attached-dependency-property-design"></a><span data-ttu-id="7d057-118">附加的依赖属性设计</span><span class="sxs-lookup"><span data-stu-id="7d057-118">Attached Dependency Property Design</span></span>
 <span data-ttu-id="7d057-119">上一部分中所述的依赖项属性表示声明类型的内部属性;例如， `Text` 属性是声明它的的属性 `TextButton` 。</span><span class="sxs-lookup"><span data-stu-id="7d057-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="7d057-120">特殊类型的依赖项属性是附加的依赖属性。</span><span class="sxs-lookup"><span data-stu-id="7d057-120">A special kind of dependency property is the attached dependency property.</span></span>

 <span data-ttu-id="7d057-121">附加属性的典型示例是 <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="7d057-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7d057-122">属性表示按钮的（而不是网格的）列位置，但它仅在按钮包含在网格中时才相关，因此它通过网格 "附加" 到按钮。</span><span class="sxs-lookup"><span data-stu-id="7d057-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 <span data-ttu-id="7d057-123">附加属性的定义与常规依赖属性的定义大致相同，不同之处在于访问器由静态 Get 和 Set 方法表示：</span><span class="sxs-lookup"><span data-stu-id="7d057-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a><span data-ttu-id="7d057-124">依赖属性验证</span><span class="sxs-lookup"><span data-stu-id="7d057-124">Dependency Property Validation</span></span>
 <span data-ttu-id="7d057-125">属性通常实现称为 "验证"。</span><span class="sxs-lookup"><span data-stu-id="7d057-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="7d057-126">尝试更改属性的值时，将执行验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="7d057-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>

 <span data-ttu-id="7d057-127">可惜依赖属性访问器不能包含任意验证代码。</span><span class="sxs-lookup"><span data-stu-id="7d057-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="7d057-128">相反，需要在属性注册期间指定依赖属性验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="7d057-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>

 <span data-ttu-id="7d057-129">❌不要在属性的访问器中放置依赖属性验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="7d057-129">❌ DO NOT put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="7d057-130">而是将验证回调传递给 `DependencyProperty.Register` 方法。</span><span class="sxs-lookup"><span data-stu-id="7d057-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>

## <a name="dependency-property-change-notifications"></a><span data-ttu-id="7d057-131">依赖属性更改通知</span><span class="sxs-lookup"><span data-stu-id="7d057-131">Dependency Property Change Notifications</span></span>
 <span data-ttu-id="7d057-132">❌不要在依赖属性访问器中实现更改通知逻辑。</span><span class="sxs-lookup"><span data-stu-id="7d057-132">❌ DO NOT implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="7d057-133">依赖属性具有内置的更改通知功能，该功能必须通过向提供更改通知回调来使用 <xref:System.Windows.PropertyMetadata> 。</span><span class="sxs-lookup"><span data-stu-id="7d057-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>

## <a name="dependency-property-value-coercion"></a><span data-ttu-id="7d057-134">依赖项属性值强制</span><span class="sxs-lookup"><span data-stu-id="7d057-134">Dependency Property Value Coercion</span></span>
 <span data-ttu-id="7d057-135">在实际修改属性存储区之前，由 setter 修改了向属性 setter 提供的值时，会发生属性强制。</span><span class="sxs-lookup"><span data-stu-id="7d057-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>

 <span data-ttu-id="7d057-136">❌不要在依赖属性访问器中实现强制逻辑。</span><span class="sxs-lookup"><span data-stu-id="7d057-136">❌ DO NOT implement coercion logic in dependency property accessors.</span></span>

 <span data-ttu-id="7d057-137">依赖属性具有内置强制功能，可通过向提供强制回调来使用 `PropertyMetadata` 。</span><span class="sxs-lookup"><span data-stu-id="7d057-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>

 <span data-ttu-id="7d057-138">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="7d057-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="7d057-139">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="7d057-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7d057-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d057-140">See also</span></span>

- [<span data-ttu-id="7d057-141">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="7d057-141">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="7d057-142">常见设计模式</span><span class="sxs-lookup"><span data-stu-id="7d057-142">Common Design Patterns</span></span>](common-design-patterns.md)
