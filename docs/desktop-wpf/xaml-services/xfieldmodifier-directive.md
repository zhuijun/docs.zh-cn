---
title: x:FieldModifier 指令
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 4e67a6dac49b8d6a7d316526f99a1519b08fd68b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554470"
---
# <a name="xfieldmodifier-directive"></a><span data-ttu-id="40500-102">x:FieldModifier 指令</span><span class="sxs-lookup"><span data-stu-id="40500-102">x:FieldModifier Directive</span></span>
<span data-ttu-id="40500-103">修改 XAML 编译行为，以便使用 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> access 而不是默认行为来定义命名对象引用的字段 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="40500-103">Modifies XAML compilation behavior so that fields for named object references are defined with <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> access instead of the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> default behavior.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="40500-104">XAML 属性用法</span><span class="sxs-lookup"><span data-stu-id="40500-104">XAML Attribute Usage</span></span>

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a><span data-ttu-id="40500-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="40500-105">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="40500-106">*公共*</span><span class="sxs-lookup"><span data-stu-id="40500-106">*Public*</span></span>|<span data-ttu-id="40500-107">传递给指定的确切字符串 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 与 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 不同，具体取决于所使用的代码隐藏编程语言。</span><span class="sxs-lookup"><span data-stu-id="40500-107">The exact string you pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that is used.</span></span> <span data-ttu-id="40500-108">请参阅“备注”。</span><span class="sxs-lookup"><span data-stu-id="40500-108">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="40500-109">依赖项</span><span class="sxs-lookup"><span data-stu-id="40500-109">Dependencies</span></span>

 <span data-ttu-id="40500-110">如果 XAML 生产使用 `x:FieldModifier` 任意位置，则该 xaml 生产的根元素必须声明 [x：Class 指令](xclass-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="40500-110">If a XAML production uses `x:FieldModifier` anywhere, the root element of that XAML production must declare an [x:Class Directive](xclass-directive.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="40500-111">备注</span><span class="sxs-lookup"><span data-stu-id="40500-111">Remarks</span></span>

<span data-ttu-id="40500-112">`x:FieldModifier` 与声明类或其成员的常规访问级别无关。</span><span class="sxs-lookup"><span data-stu-id="40500-112">`x:FieldModifier` is not relevant for declaring the general access level of a class or its members.</span></span> <span data-ttu-id="40500-113">当处理作为 XAML 生产一部分的特定 XAML 对象时，此方法仅适用于 XAML 处理行为，并成为可在应用程序的对象图中访问的对象。</span><span class="sxs-lookup"><span data-stu-id="40500-113">It is relevant only for XAML-processing behavior when a particular XAML object that is part of a XAML production is processed, and becomes an object that is potentially accessible in the object graph of an application.</span></span> <span data-ttu-id="40500-114">默认情况下，此类对象的字段引用保持为私有，这会阻止控件使用者直接修改对象图。</span><span class="sxs-lookup"><span data-stu-id="40500-114">By default, the field reference for such an object is kept private, which prevents control consumers from modifying the object graph directly.</span></span> <span data-ttu-id="40500-115">相反，控件使用者应该使用由编程模型启用的标准模式（如通过获取布局根、子元素集合、专用公共属性等）来修改对象关系图。</span><span class="sxs-lookup"><span data-stu-id="40500-115">Instead, control consumers are expected to modify the object graph by using standard patterns that are enabled by programming models, such as by obtaining the layout root, the child element collections, the dedicated public properties, and so on.</span></span>

<span data-ttu-id="40500-116">特性的值 `x:FieldModifier` 因编程语言而异，其用途在特定框架中可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="40500-116">The value for the `x:FieldModifier` attribute varies by programming language, and its purpose can vary in specific frameworks.</span></span> <span data-ttu-id="40500-117">要使用的字符串取决于每种语言如何实现其 <xref:System.CodeDom.Compiler.CodeDomProvider> 和返回的类型转换器，以定义和的 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 含义 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ，以及该语言是否区分大小写。</span><span class="sxs-lookup"><span data-stu-id="40500-117">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="40500-118">对于 c #，要传递的要传递的字符串 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 为 `public` 。</span><span class="sxs-lookup"><span data-stu-id="40500-118">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `public`.</span></span>

- <span data-ttu-id="40500-119">对于 Microsoft Visual Basic .NET，要传递的字符串为 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> `Public` 。</span><span class="sxs-lookup"><span data-stu-id="40500-119">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `Public`.</span></span>

- <span data-ttu-id="40500-120">对于 c + +/CLI，当前不存在 XAML 的目标;因此，传递的字符串未定义。</span><span class="sxs-lookup"><span data-stu-id="40500-120">For C++/CLI, no targets for XAML currently exist; therefore, the string to pass is undefined.</span></span>

<span data-ttu-id="40500-121">你还可以在 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> Visual Basic 中指定 (`internal` c # 中 `Friend`) 但指定 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 非常罕见，因为 `NotPublic` 行为已是默认值。</span><span class="sxs-lookup"><span data-stu-id="40500-121">You can also specify <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` in C#, `Friend` in Visual Basic) but specifying <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is unusual because `NotPublic` as the behavior is already the default.</span></span>

<span data-ttu-id="40500-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 是默认行为，因为编译 XAML 的程序集之外的代码很少需要访问 XAML 创建的元素。</span><span class="sxs-lookup"><span data-stu-id="40500-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is the default behavior because it is infrequent that code outside the assembly that compiled the XAML needs access to a XAML-created element.</span></span> <span data-ttu-id="40500-123">WPF 安全体系结构与 XAML 编译行为一起不会声明将元素实例存储为公共的字段，除非您专门将设置 `x:FieldModifier` 为允许公共访问。</span><span class="sxs-lookup"><span data-stu-id="40500-123">WPF security architecture together with XAML compilation behavior will not declare fields that store element instances as public, unless you specifically set the `x:FieldModifier` to allow public access.</span></span>

<span data-ttu-id="40500-124">`x:FieldModifier` 仅适用于具有 [X：Name 指令](xname-directive.md) 的元素，因为该名称用于在其公开后引用字段。</span><span class="sxs-lookup"><span data-stu-id="40500-124">`x:FieldModifier` is only relevant for elements with an [x:Name Directive](xname-directive.md) because that name is used to reference the field after it is public.</span></span>

<span data-ttu-id="40500-125">默认情况下，根元素的分部类是公共的;但是，可以使用 [X:ClassModifier 指令](xclassmodifier-directive.md)使其成为非公共的。</span><span class="sxs-lookup"><span data-stu-id="40500-125">By default, the partial class for the root element is public; however, you can make it nonpublic by using the [x:ClassModifier Directive](xclassmodifier-directive.md).</span></span> <span data-ttu-id="40500-126">[X:ClassModifier 指令](xclassmodifier-directive.md)还会影响 root 元素类的实例的访问级别。</span><span class="sxs-lookup"><span data-stu-id="40500-126">The [x:ClassModifier Directive](xclassmodifier-directive.md) also affects the access level of the instance of the root element class.</span></span> <span data-ttu-id="40500-127">你可以将 `x:Name` 和置于 `x:FieldModifier` 根元素上，但这只会生成根元素的公共字段副本，其真正的根元素类访问级别仍由 [x:ClassModifier 指令](xclassmodifier-directive.md)控制。</span><span class="sxs-lookup"><span data-stu-id="40500-127">You can put both `x:Name` and `x:FieldModifier` on the root element, but this only makes a public field copy of the root element, with the true root element class access level still controlled by [x:ClassModifier Directive](xclassmodifier-directive.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40500-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="40500-128">See also</span></span>

- [<span data-ttu-id="40500-129">XAML 及 WPF 的自定义类</span><span class="sxs-lookup"><span data-stu-id="40500-129">XAML and Custom Classes for WPF</span></span>](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
- [<span data-ttu-id="40500-130">WPF 中的代码隐藏和 XAML</span><span class="sxs-lookup"><span data-stu-id="40500-130">Code-Behind and XAML in WPF</span></span>](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [<span data-ttu-id="40500-131">x:Name 指令</span><span class="sxs-lookup"><span data-stu-id="40500-131">x:Name Directive</span></span>](xname-directive.md)
- <span data-ttu-id="40500-132">[Building a WPF Application (WPF)](/dotnet/desktop/wpf/app-development/building-a-wpf-application-wpf)（生成 WPF 应用程序 (WPF)）</span><span class="sxs-lookup"><span data-stu-id="40500-132">[Building a WPF Application (WPF)](/dotnet/desktop/wpf/app-development/building-a-wpf-application-wpf)</span></span>
- [<span data-ttu-id="40500-133">x:ClassModifier 指令</span><span class="sxs-lookup"><span data-stu-id="40500-133">x:ClassModifier Directive</span></span>](xclassmodifier-directive.md)
