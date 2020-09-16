---
title: x:Subclass 指令
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: b888ef73d1678fd37c984e4bb223f24e5b65d2cc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540714"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="343d9-102">x:Subclass 指令</span><span class="sxs-lookup"><span data-stu-id="343d9-102">x:Subclass Directive</span></span>

<span data-ttu-id="343d9-103">如果 `x:Class` 还提供了，则修改 XAML 标记编译行为。</span><span class="sxs-lookup"><span data-stu-id="343d9-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="343d9-104">不是创建基于的分部类，而是将 `x:Class` 提供的 `x:Class` 作为中间类创建，然后提供的派生类应基于 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="343d9-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="343d9-105">XAML 属性用法</span><span class="sxs-lookup"><span data-stu-id="343d9-105">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="343d9-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="343d9-106">XAML Values</span></span>

|||
|-|-|
|`namespace`|<span data-ttu-id="343d9-107">可选。</span><span class="sxs-lookup"><span data-stu-id="343d9-107">Optional.</span></span> <span data-ttu-id="343d9-108">指定包含的 CLR 命名空间 `classname` 。</span><span class="sxs-lookup"><span data-stu-id="343d9-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="343d9-109">如果 `namespace` 指定了，则 ( 一个点。 ) 分隔 `namespace` 和 `classname` 。</span><span class="sxs-lookup"><span data-stu-id="343d9-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|
|`classname`|<span data-ttu-id="343d9-110">必需。</span><span class="sxs-lookup"><span data-stu-id="343d9-110">Required.</span></span> <span data-ttu-id="343d9-111">指定用于连接加载的 XAML 的分部类的 CLR 名称和该 XAML 的代码隐藏。</span><span class="sxs-lookup"><span data-stu-id="343d9-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="343d9-112">请参阅“备注”。</span><span class="sxs-lookup"><span data-stu-id="343d9-112">See Remarks.</span></span>|
|`subclassNamespace`|<span data-ttu-id="343d9-113">可选。</span><span class="sxs-lookup"><span data-stu-id="343d9-113">Optional.</span></span> <span data-ttu-id="343d9-114">`namespace`如果每个命名空间都可以解析另一个，则可以与不同。</span><span class="sxs-lookup"><span data-stu-id="343d9-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="343d9-115">指定包含的 CLR 命名空间 `subclassName` 。</span><span class="sxs-lookup"><span data-stu-id="343d9-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="343d9-116">如果 `subclassName` 指定了，则 ( 一个点。 ) 分隔 `subclassNamespace` 和 `subclassName` 。</span><span class="sxs-lookup"><span data-stu-id="343d9-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|
|`subclassName`|<span data-ttu-id="343d9-117">必需。</span><span class="sxs-lookup"><span data-stu-id="343d9-117">Required.</span></span> <span data-ttu-id="343d9-118">指定子类的 CLR 名称。</span><span class="sxs-lookup"><span data-stu-id="343d9-118">Specifies the CLR name of the subclass.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="343d9-119">依赖项</span><span class="sxs-lookup"><span data-stu-id="343d9-119">Dependencies</span></span>

<span data-ttu-id="343d9-120">还必须在同一对象上提供[X：Class 指令](xclass-directive.md)，该对象必须是 XAML 生产的根元素。</span><span class="sxs-lookup"><span data-stu-id="343d9-120">[x:Class Directive](xclass-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>

## <a name="remarks"></a><span data-ttu-id="343d9-121">备注</span><span class="sxs-lookup"><span data-stu-id="343d9-121">Remarks</span></span>

<span data-ttu-id="343d9-122">`x:Subclass` 用法主要用于不支持分部类声明的语言。</span><span class="sxs-lookup"><span data-stu-id="343d9-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>

<span data-ttu-id="343d9-123">用作的类 `x:Subclass` 不能是嵌套类，并且 `x:Subclass` 必须引用根对象，如 "依赖项" 一节中所述。</span><span class="sxs-lookup"><span data-stu-id="343d9-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>

<span data-ttu-id="343d9-124">否则， `x:Subclass` .NET XAML 服务实现未定义的概念含义。</span><span class="sxs-lookup"><span data-stu-id="343d9-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET XAML Services implementation.</span></span> <span data-ttu-id="343d9-125">这是因为 .NET XAML 服务行为未指定 XAML 标记和支持代码的连接总体编程模型。</span><span class="sxs-lookup"><span data-stu-id="343d9-125">This is because .NET XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="343d9-126">与和相关的进一步概念的实现 `x:Class` `x:Subclass` 由使用编程模型或应用程序模型的特定框架执行，用于定义如何连接 XAML 标记、编译的标记和基于 CLR 的代码隐藏。</span><span class="sxs-lookup"><span data-stu-id="343d9-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="343d9-127">每个框架可能有自己的生成操作，这些操作可实现某些行为，或必须包含在生成环境中的特定组件。</span><span class="sxs-lookup"><span data-stu-id="343d9-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="343d9-128">在框架中，生成操作还会根据用于代码隐藏的特定 CLR 语言而有所不同。</span><span class="sxs-lookup"><span data-stu-id="343d9-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="343d9-129">WPF 用法说明</span><span class="sxs-lookup"><span data-stu-id="343d9-129">WPF Usage Notes</span></span>

<span data-ttu-id="343d9-130">`x:Subclass` 可以位于页根上，也可以位于 <xref:System.Windows.Application> 应用程序定义中已有的根上 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="343d9-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="343d9-131">`x:Subclass`在页或应用程序根目录之外的任何元素上进行声明，或在不存在的位置进行声明 `x:Class` 会导致编译时错误。</span><span class="sxs-lookup"><span data-stu-id="343d9-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>

<span data-ttu-id="343d9-132">创建适用于方案的派生类非常 `x:Subclass` 复杂。</span><span class="sxs-lookup"><span data-stu-id="343d9-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="343d9-133">你可能需要检查中间文件 (项目的 obj 文件夹中生成的文件（通过标记编译），其名称将 .xaml 文件名合并) 。</span><span class="sxs-lookup"><span data-stu-id="343d9-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="343d9-134">这些中间文件可帮助您在已编译的应用程序的已联接分部类中确定某些编程构造的源。</span><span class="sxs-lookup"><span data-stu-id="343d9-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>

<span data-ttu-id="343d9-135">派生类中的事件处理程序必须 `internal override` `Friend Overrides` 在 Microsoft Visual Basic) 中 (，以便覆盖在编译期间在中间类中创建的处理程序的存根。</span><span class="sxs-lookup"><span data-stu-id="343d9-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="343d9-136">否则，派生类实现将隐藏中间类实现)  (隐藏，并且不调用中间类处理程序。</span><span class="sxs-lookup"><span data-stu-id="343d9-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>

<span data-ttu-id="343d9-137">如果同时定义 `x:Class` 和 `x:Subclass` ，则不需要为所引用的类提供任何实现 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="343d9-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="343d9-138">只需通过属性为其指定一个名称， `x:Class` 以便编译器对于在中间文件中创建的类有一些指导， (编译器在这种情况下不选择默认名称) 。</span><span class="sxs-lookup"><span data-stu-id="343d9-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="343d9-139">您可以为 `x:Class` 类提供实现; 但是，这并不是使用和的典型方案 `x:Class` `x:Subclass` 。</span><span class="sxs-lookup"><span data-stu-id="343d9-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>

## <a name="see-also"></a><span data-ttu-id="343d9-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="343d9-140">See also</span></span>

- [<span data-ttu-id="343d9-141">x:Class 指令</span><span class="sxs-lookup"><span data-stu-id="343d9-141">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="343d9-142">XAML 及 WPF 的自定义类</span><span class="sxs-lookup"><span data-stu-id="343d9-142">XAML and Custom Classes for WPF</span></span>](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
