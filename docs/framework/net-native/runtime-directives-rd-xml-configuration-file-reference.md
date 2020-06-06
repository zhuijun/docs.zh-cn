---
title: 运行时指令 (rd.xml) 配置文件引用
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "76738406"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="1d367-102">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="1d367-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="1d367-103">运行时指令 (.rd.xml) 文件是一个 XML 配置文件，它指定了指定程序元素是否适用于反射。</span><span class="sxs-lookup"><span data-stu-id="1d367-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="1d367-104">运行时指令文件的示例如下所示：</span><span class="sxs-lookup"><span data-stu-id="1d367-104">Here’s an example of a runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />
    <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />
    <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />
    <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />

    <Namespace Name="System.Collections.ObjectModel" >
      <TypeInstantiation Name="ObservableCollection"
            Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />
      <TypeInstantiation Name="ReadOnlyObservableCollection"
            Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />
    </Namespace>
  </Application>
</Directives>
```

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="1d367-105">运行时指令文件的结构</span><span class="sxs-lookup"><span data-stu-id="1d367-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="1d367-106">运行时指令文件使用 `http://schemas.microsoft.com/netfx/2013/01/metadata` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="1d367-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="1d367-107">根元素为 [Directives](directives-element-net-native.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="1d367-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="1d367-108">它可以包含零个或更多个 [Library](library-element-net-native.md) 元素，以及零个或一个 [Application](application-element-net-native.md) 元素，如以下结构中所示。</span><span class="sxs-lookup"><span data-stu-id="1d367-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="1d367-109">[Application](application-element-net-native.md) 元素的特性可定义应用程序范围的运行时反射策略，或可充当子元素的容器。</span><span class="sxs-lookup"><span data-stu-id="1d367-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="1d367-110">而 [Library](library-element-net-native.md) 元素则仅仅是一个容器。</span><span class="sxs-lookup"><span data-stu-id="1d367-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="1d367-111">[Application](application-element-net-native.md) 和 [Library](library-element-net-native.md) 元素的子级定义了适用于反射的类型、方法、字段、属性和事件。</span><span class="sxs-lookup"><span data-stu-id="1d367-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="1d367-112">有关引用信息，请从以下结构中选择元素或参阅[运行时指令元素](runtime-directive-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d367-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="1d367-113">在以下层次结构中，省略号表示递归结构。</span><span class="sxs-lookup"><span data-stu-id="1d367-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="1d367-114">括号中的信息表明元素是可选项还是必需项，以及如果使用该元素，将允许多少个实例（一个或多个）。</span><span class="sxs-lookup"><span data-stu-id="1d367-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

- <span data-ttu-id="1d367-115">[Directives](directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="1d367-115">[Directives](directives-element-net-native.md) [1:1]</span></span>
  - <span data-ttu-id="1d367-116">[Application](application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="1d367-116">[Application](application-element-net-native.md) [0:1]</span></span>
    - <span data-ttu-id="1d367-117">[Assembly](assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-117">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-118">[命名空间](namespace-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-118">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-119">.</span><span class="sxs-lookup"><span data-stu-id="1d367-119">.</span></span> <span data-ttu-id="1d367-120">.</span><span class="sxs-lookup"><span data-stu-id="1d367-120">.</span></span>
      - <span data-ttu-id="1d367-121">[类型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-121">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-122">.</span><span class="sxs-lookup"><span data-stu-id="1d367-122">.</span></span> <span data-ttu-id="1d367-123">.</span><span class="sxs-lookup"><span data-stu-id="1d367-123">.</span></span>
      - <span data-ttu-id="1d367-124">[类型实例化](typeinstantiation-element-net-native.md)（构造泛型类型） [0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-124">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="1d367-125">.</span><span class="sxs-lookup"><span data-stu-id="1d367-125">.</span></span> <span data-ttu-id="1d367-126">.</span><span class="sxs-lookup"><span data-stu-id="1d367-126">.</span></span>
    - <span data-ttu-id="1d367-127">[Namespace](namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-127">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-128">[命名空间](namespace-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-128">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-129">.</span><span class="sxs-lookup"><span data-stu-id="1d367-129">.</span></span> <span data-ttu-id="1d367-130">.</span><span class="sxs-lookup"><span data-stu-id="1d367-130">.</span></span>
      - <span data-ttu-id="1d367-131">[类型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-131">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-132">.</span><span class="sxs-lookup"><span data-stu-id="1d367-132">.</span></span> <span data-ttu-id="1d367-133">.</span><span class="sxs-lookup"><span data-stu-id="1d367-133">.</span></span>
      - <span data-ttu-id="1d367-134">[类型实例化](typeinstantiation-element-net-native.md)（构造泛型类型） [0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-134">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="1d367-135">.</span><span class="sxs-lookup"><span data-stu-id="1d367-135">.</span></span> <span data-ttu-id="1d367-136">.</span><span class="sxs-lookup"><span data-stu-id="1d367-136">.</span></span>
    - <span data-ttu-id="1d367-137">[Type](type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-137">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-138">[Subtypes](subtypes-element-net-native.md)（包含类型的子类）[O:1]</span><span class="sxs-lookup"><span data-stu-id="1d367-138">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="1d367-139">[类型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-139">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-140">.</span><span class="sxs-lookup"><span data-stu-id="1d367-140">.</span></span> <span data-ttu-id="1d367-141">.</span><span class="sxs-lookup"><span data-stu-id="1d367-141">.</span></span>
      - <span data-ttu-id="1d367-142">[类型实例化](typeinstantiation-element-net-native.md)（构造泛型类型） [0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="1d367-143">.</span><span class="sxs-lookup"><span data-stu-id="1d367-143">.</span></span> <span data-ttu-id="1d367-144">.</span><span class="sxs-lookup"><span data-stu-id="1d367-144">.</span></span>
      - <span data-ttu-id="1d367-145">[AttributeImplies](attributeimplies-element-net-native.md)（包含类型是一种特性）[O:1]</span><span class="sxs-lookup"><span data-stu-id="1d367-145">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="1d367-146">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-146">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-147">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-147">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="1d367-148">[Parameter](parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-148">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="1d367-149">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-149">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="1d367-150">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-150">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-151">[MethodInstantiation](methodinstantiation-element-net-native.md)（构造泛型方法）[0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-151">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="1d367-152">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-152">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-153">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-153">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-154">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-154">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="1d367-155">[TypeInstantiation](typeinstantiation-element-net-native.md)（构造泛型类型）[0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-155">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="1d367-156">[类型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-156">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-157">.</span><span class="sxs-lookup"><span data-stu-id="1d367-157">.</span></span> <span data-ttu-id="1d367-158">.</span><span class="sxs-lookup"><span data-stu-id="1d367-158">.</span></span>
      - <span data-ttu-id="1d367-159">[类型实例化](typeinstantiation-element-net-native.md)（构造泛型类型） [0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-159">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="1d367-160">.</span><span class="sxs-lookup"><span data-stu-id="1d367-160">.</span></span> <span data-ttu-id="1d367-161">.</span><span class="sxs-lookup"><span data-stu-id="1d367-161">.</span></span>
      - <span data-ttu-id="1d367-162">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-162">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="1d367-163">[Parameter](parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-163">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="1d367-164">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-164">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="1d367-165">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-165">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-166">[MethodInstantiation](methodinstantiation-element-net-native.md)（构造泛型方法）[0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-166">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="1d367-167">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-167">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-168">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-168">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-169">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-169">[Event](event-element-net-native.md) [0:M]</span></span>
  - <span data-ttu-id="1d367-170">[Library](library-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-170">[Library](library-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="1d367-171">[Assembly](assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-171">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-172">[命名空间](namespace-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-172">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-173">.</span><span class="sxs-lookup"><span data-stu-id="1d367-173">.</span></span> <span data-ttu-id="1d367-174">.</span><span class="sxs-lookup"><span data-stu-id="1d367-174">.</span></span>
      - <span data-ttu-id="1d367-175">[类型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-175">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-176">.</span><span class="sxs-lookup"><span data-stu-id="1d367-176">.</span></span> <span data-ttu-id="1d367-177">.</span><span class="sxs-lookup"><span data-stu-id="1d367-177">.</span></span>
      - <span data-ttu-id="1d367-178">[类型实例化](typeinstantiation-element-net-native.md)（构造泛型类型） [0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-178">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="1d367-179">.</span><span class="sxs-lookup"><span data-stu-id="1d367-179">.</span></span> <span data-ttu-id="1d367-180">.</span><span class="sxs-lookup"><span data-stu-id="1d367-180">.</span></span>
    - <span data-ttu-id="1d367-181">[Namespace](namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-181">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-182">[命名空间](namespace-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-182">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-183">.</span><span class="sxs-lookup"><span data-stu-id="1d367-183">.</span></span> <span data-ttu-id="1d367-184">.</span><span class="sxs-lookup"><span data-stu-id="1d367-184">.</span></span>
      - <span data-ttu-id="1d367-185">[类型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-185">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-186">.</span><span class="sxs-lookup"><span data-stu-id="1d367-186">.</span></span> <span data-ttu-id="1d367-187">.</span><span class="sxs-lookup"><span data-stu-id="1d367-187">.</span></span>
      - <span data-ttu-id="1d367-188">[类型实例化](typeinstantiation-element-net-native.md)（构造泛型类型） [0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-188">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="1d367-189">.</span><span class="sxs-lookup"><span data-stu-id="1d367-189">.</span></span> <span data-ttu-id="1d367-190">.</span><span class="sxs-lookup"><span data-stu-id="1d367-190">.</span></span>
    - <span data-ttu-id="1d367-191">[Type](type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-191">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-192">[Subtypes](subtypes-element-net-native.md)（包含类型的子类）[O:1]</span><span class="sxs-lookup"><span data-stu-id="1d367-192">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="1d367-193">[类型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-193">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-194">.</span><span class="sxs-lookup"><span data-stu-id="1d367-194">.</span></span> <span data-ttu-id="1d367-195">.</span><span class="sxs-lookup"><span data-stu-id="1d367-195">.</span></span>
      - <span data-ttu-id="1d367-196">[类型实例化](typeinstantiation-element-net-native.md)（构造泛型类型） [0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-196">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="1d367-197">.</span><span class="sxs-lookup"><span data-stu-id="1d367-197">.</span></span> <span data-ttu-id="1d367-198">.</span><span class="sxs-lookup"><span data-stu-id="1d367-198">.</span></span>
      - <span data-ttu-id="1d367-199">[AttributeImplies](attributeimplies-element-net-native.md)（包含类型是一种特性）[O:1]</span><span class="sxs-lookup"><span data-stu-id="1d367-199">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="1d367-200">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-200">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-201">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-201">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-202">[MethodInstantiation](methodinstantiation-element-net-native.md)（构造泛型方法）[0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-202">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="1d367-203">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-203">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-204">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-204">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-205">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-205">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="1d367-206">[TypeInstantiation](typeinstantiation-element-net-native.md)（构造泛型类型）[0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-206">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="1d367-207">[类型](type-element-net-native.md)[0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-207">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="1d367-208">.</span><span class="sxs-lookup"><span data-stu-id="1d367-208">.</span></span> <span data-ttu-id="1d367-209">.</span><span class="sxs-lookup"><span data-stu-id="1d367-209">.</span></span>
      - <span data-ttu-id="1d367-210">[类型实例化](typeinstantiation-element-net-native.md)（构造泛型类型） [0： M]。</span><span class="sxs-lookup"><span data-stu-id="1d367-210">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="1d367-211">.</span><span class="sxs-lookup"><span data-stu-id="1d367-211">.</span></span> <span data-ttu-id="1d367-212">.</span><span class="sxs-lookup"><span data-stu-id="1d367-212">.</span></span>
      - <span data-ttu-id="1d367-213">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-213">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-214">[MethodInstantiation](methodinstantiation-element-net-native.md)（构造泛型方法）[0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-214">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="1d367-215">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-215">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-216">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-216">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="1d367-217">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="1d367-217">[Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="1d367-218">[Application](application-element-net-native.md) 元素可以不具任何属性，也可以具备在[“运行时指令和策略”部分](#Directives)中所讨论的策略属性。</span><span class="sxs-lookup"><span data-stu-id="1d367-218">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="1d367-219">[Library`Name` 元素具有单个属性 ](library-element-net-native.md)，该属性指定了库名或程序集名（不带文件扩展名）。</span><span class="sxs-lookup"><span data-stu-id="1d367-219">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="1d367-220">例如，以下 [Library](library-element-net-native.md) 元素适用于名为 Extensions.dll 的程序集。</span><span class="sxs-lookup"><span data-stu-id="1d367-220">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <!-- Child elements go here -->
  </Application>
  <Library Name="Extensions">
     <!-- Child elements go here -->
  </Library>
</Directives>
```

<a name="Directives"></a>

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="1d367-221">运行时指令和策略</span><span class="sxs-lookup"><span data-stu-id="1d367-221">Runtime directives and policy</span></span>

<span data-ttu-id="1d367-222">[Application](application-element-net-native.md) 元素本身以及 [Library](library-element-net-native.md) 和 [Application](application-element-net-native.md) 元素的子元素表示策略，也就是说，它们定义了应用可将反射应用于程序元素的方式。</span><span class="sxs-lookup"><span data-stu-id="1d367-222">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="1d367-223">策略类型由元素属性定义（例如，`Serialize`）。</span><span class="sxs-lookup"><span data-stu-id="1d367-223">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="1d367-224">策略值由属性值定义（例如，`Serialize="Required"`）。</span><span class="sxs-lookup"><span data-stu-id="1d367-224">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="1d367-225">任何由元素属性指定的策略均适用于未对该策略指定值的子元素。</span><span class="sxs-lookup"><span data-stu-id="1d367-225">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="1d367-226">例如，如果策略由 [Type](type-element-net-native.md) 元素指定，则该策略适用于包含的所有尚未显式指定策略的类型和成员。</span><span class="sxs-lookup"><span data-stu-id="1d367-226">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="1d367-227">可通过 [Application](application-element-net-native.md)、[Assembly](assembly-element-net-native.md)、[AttributeImplies](attributeimplies-element-net-native.md)、[Namespace](namespace-element-net-native.md)、[Subtypes](subtypes-element-net-native.md) 和 [Type](type-element-net-native.md) 元素表示的策略有别于可针对每个成员表示的策略（通过 [Method](method-element-net-native.md)、[Property](property-element-net-native.md)、[Field](field-element-net-native.md) 和 [Event](event-element-net-native.md) 元素来表示）。</span><span class="sxs-lookup"><span data-stu-id="1d367-227">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="1d367-228">为程序集、命名空间和类型指定策略</span><span class="sxs-lookup"><span data-stu-id="1d367-228">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="1d367-229">[Application](application-element-net-native.md)、[Assembly](assembly-element-net-native.md)、[AttributeImplies](attributeimplies-element-net-native.md)、[Namespace](namespace-element-net-native.md)、[Subtypes](subtypes-element-net-native.md) 和 [Type](type-element-net-native.md) 元素支持下列策略类型：</span><span class="sxs-lookup"><span data-stu-id="1d367-229">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="1d367-230">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="1d367-230">`Activate`.</span></span> <span data-ttu-id="1d367-231">控制运行时对构造函数的访问，以启用实例激活。</span><span class="sxs-lookup"><span data-stu-id="1d367-231">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="1d367-232">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="1d367-232">`Browse`.</span></span> <span data-ttu-id="1d367-233">控制对有关程序元素信息的查询，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="1d367-233">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="1d367-234">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="1d367-234">`Dynamic`.</span></span> <span data-ttu-id="1d367-235">控制运行时对所有类型成员的访问，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="1d367-235">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="1d367-236">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="1d367-236">`Serialize`.</span></span> <span data-ttu-id="1d367-237">控制运行时对构造函数、字段和属性的访问，以便通过 Newtonsoft JSON 序列化程序等第三方库实现类型实例的序列化。</span><span class="sxs-lookup"><span data-stu-id="1d367-237">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="1d367-238">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="1d367-238">`DataContractSerializer`.</span></span> <span data-ttu-id="1d367-239">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 类的序列化策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-239">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="1d367-240">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="1d367-240">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="1d367-241">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 类的 JSON 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-241">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="1d367-242">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="1d367-242">`XmlSerializer`.</span></span> <span data-ttu-id="1d367-243">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 类的 XML 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-243">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="1d367-244">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="1d367-244">`MarshalObject`.</span></span> <span data-ttu-id="1d367-245">控制将引用类型封送到 WinRT 和 COM 的策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-245">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="1d367-246">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="1d367-246">`MarshalDelegate`.</span></span> <span data-ttu-id="1d367-247">控制将委托类型作为函数指针封送到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-247">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="1d367-248">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="1d367-248">`MarshalStructure` .</span></span> <span data-ttu-id="1d367-249">控制封送结构到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-249">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="1d367-250">与这些策略类型有关的设置如下：</span><span class="sxs-lookup"><span data-stu-id="1d367-250">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="1d367-251">`All`.</span><span class="sxs-lookup"><span data-stu-id="1d367-251">`All`.</span></span> <span data-ttu-id="1d367-252">为工具链未删除的所有类型和成员启用策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-252">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="1d367-253">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="1d367-253">`Auto`.</span></span> <span data-ttu-id="1d367-254">使用默认行为。</span><span class="sxs-lookup"><span data-stu-id="1d367-254">Use the default behavior.</span></span> <span data-ttu-id="1d367-255">（未指定策略等同于将该策略设置为 `Auto`，除非该策略被替代，例如被父元素替代。）</span><span class="sxs-lookup"><span data-stu-id="1d367-255">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="1d367-256">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="1d367-256">`Excluded`.</span></span> <span data-ttu-id="1d367-257">禁用程序元素策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-257">Disable the policy for the program element.</span></span>

- <span data-ttu-id="1d367-258">`Public`.</span><span class="sxs-lookup"><span data-stu-id="1d367-258">`Public`.</span></span> <span data-ttu-id="1d367-259">启用公共类型或成员策略，除非工具链确定该成员为多余并因此将其删除。</span><span class="sxs-lookup"><span data-stu-id="1d367-259">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="1d367-260">（在后一种情况下，你必须使用 `Required Public`，以确保该成员已被保留并且具有反射功能。）</span><span class="sxs-lookup"><span data-stu-id="1d367-260">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="1d367-261">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="1d367-261">`PublicAndInternal`.</span></span> <span data-ttu-id="1d367-262">如果工具链未将公共和内部类型或成员删除，则为它们启用策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-262">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="1d367-263">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="1d367-263">`Required Public`.</span></span> <span data-ttu-id="1d367-264">不管公共类型和成员是否处于占用状态，工具链均须将它们保留下来，并为它们启用策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-264">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="1d367-265">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="1d367-265">`Required PublicAndInternal`.</span></span> <span data-ttu-id="1d367-266">不管公共和内部类型和成员是否处于占用状态，工具链均须将它们保留下来，并为它们启用策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-266">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="1d367-267">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="1d367-267">`Required All`.</span></span> <span data-ttu-id="1d367-268">不管所有类型和成员是否处于占用状态，工具链均须将它们保留下来，并为它们启用策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-268">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="1d367-269">例如，以下运行时指令文件为程序集 DataClasses.dll 中的所有类型和成员定义了策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-269">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="1d367-270">借此可以实现对所有公共属性的序列化反射；可实现对所有类型和类型成员进行浏览；可实现对所有类型的激活（由于具有 `Dynamic` 属性）；还可实现对所有公共类型和成员的反射。</span><span class="sxs-lookup"><span data-stu-id="1d367-270">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"
                Browse="All" Activate="PublicAndInternal"
                Dynamic="Public"  />
   </Application>
   <Library Name="UtilityLibrary">
     <!-- Child elements go here -->
   </Library>
</Directives>
```

### <a name="specifying-policy-for-members"></a><span data-ttu-id="1d367-271">为成员指定策略</span><span class="sxs-lookup"><span data-stu-id="1d367-271">Specifying policy for members</span></span>

<span data-ttu-id="1d367-272">[Property](property-element-net-native.md) 和 [Field](field-element-net-native.md) 元素支持下列策略类型：</span><span class="sxs-lookup"><span data-stu-id="1d367-272">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="1d367-273">`Browse` - 控制查询有关此成员的信息，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="1d367-273">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="1d367-274">`Dynamic` - 控制运行时访问所有类型的成员，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="1d367-274">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="1d367-275">还控制查询有关包含类型的信息。</span><span class="sxs-lookup"><span data-stu-id="1d367-275">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="1d367-276">`Serialize` - 控制运行时访问成员，以便通过 Newtonsoft JSON 序列化程序等库实现类型实例的序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="1d367-276">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="1d367-277">此策略可应用于构造函数、字段和属性。</span><span class="sxs-lookup"><span data-stu-id="1d367-277">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="1d367-278">[Method](method-element-net-native.md) 和 [Event](event-element-net-native.md) 元素支持下列策略类型：</span><span class="sxs-lookup"><span data-stu-id="1d367-278">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="1d367-279">`Browse` - 控制查询有关此成员的信息，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="1d367-279">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="1d367-280">`Dynamic` - 控制运行时访问所有类型的成员，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="1d367-280">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="1d367-281">还控制查询有关包含类型的信息。</span><span class="sxs-lookup"><span data-stu-id="1d367-281">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="1d367-282">与这些策略类型有关的设置如下：</span><span class="sxs-lookup"><span data-stu-id="1d367-282">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="1d367-283">`Auto` - 使用默认行为。</span><span class="sxs-lookup"><span data-stu-id="1d367-283">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="1d367-284">（未指定策略等同于将该策略设置为 `Auto`，除非某些内容将该策略替代。）</span><span class="sxs-lookup"><span data-stu-id="1d367-284">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="1d367-285">`Excluded` - 始终不包括成员的元数据。</span><span class="sxs-lookup"><span data-stu-id="1d367-285">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="1d367-286">`Included` - 如果输出中存在父类型，则启用策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-286">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="1d367-287">`Required` - 即便该成员显示为未使用，工具链也必须将它保留下来，并为它启用策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-287">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="1d367-288">运行时指令文件语义</span><span class="sxs-lookup"><span data-stu-id="1d367-288">Runtime directives file semantics</span></span>

<span data-ttu-id="1d367-289">可同时为较高级别和较低级别元素定义策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-289">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="1d367-290">例如，我们可为程序集以及其中包含的一些类型定义策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-290">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="1d367-291">如果无法表示特定的较低级别元素，则说明该元素继承了其父级的策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-291">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="1d367-292">例如，如果存在 `Assembly` 元素却不存在 `Type` 元素，则说明在 `Assembly` 中指定的策略适用于数据集中的每一个类型。</span><span class="sxs-lookup"><span data-stu-id="1d367-292">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="1d367-293">多个元素也可将策略应用到同一个程序元素。</span><span class="sxs-lookup"><span data-stu-id="1d367-293">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="1d367-294">例如，不同的 [Assembly](assembly-element-net-native.md) 元素可能会以不同的方式为同一个数据集定义同一个策略元素。</span><span class="sxs-lookup"><span data-stu-id="1d367-294">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="1d367-295">以下部分将分别说明在下列情况下应如何处理特定类型策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-295">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="1d367-296">泛型类型或方法的一个 [Type](type-element-net-native.md) 或 [Method](method-element-net-native.md) 元素将它的策略应用到所有不具备自身策略的实例化。</span><span class="sxs-lookup"><span data-stu-id="1d367-296">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="1d367-297">例如，为 `Type` 指定了策略的 <xref:System.Collections.Generic.List%601> 元素适用于该泛型类型的所有构造实例，除非 `List<Int32>` 元素将其替代为特殊构造的泛型类型（例如 `TypeInstantiation`）。</span><span class="sxs-lookup"><span data-stu-id="1d367-297">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="1d367-298">否则，元素将为指定的程序元素定义策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-298">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="1d367-299">元素不明确时，引擎将查找匹配项，如果发现完全匹配就将使用该条匹配。</span><span class="sxs-lookup"><span data-stu-id="1d367-299">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="1d367-300">如果发现多条匹配，将出现警告或错误。</span><span class="sxs-lookup"><span data-stu-id="1d367-300">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="1d367-301">如果两条指令将策略应用于同一个程序元素</span><span class="sxs-lookup"><span data-stu-id="1d367-301">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="1d367-302">如果不同运行时指令文件中的两个元素尝试将同一程序元素（例如程序集或类型）的同一策略类型设置为不同的值，则解决冲突的方法如下：</span><span class="sxs-lookup"><span data-stu-id="1d367-302">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="1d367-303">如果存在 `Excluded` 元素，则该元素优先。</span><span class="sxs-lookup"><span data-stu-id="1d367-303">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="1d367-304">`Required` 优先于非 `Required`。</span><span class="sxs-lookup"><span data-stu-id="1d367-304">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="1d367-305">`All` 优先于 `PublicAndInternal`，而后者又优先于 `Public`。</span><span class="sxs-lookup"><span data-stu-id="1d367-305">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="1d367-306">任何显式设置均优先于 `Auto`。</span><span class="sxs-lookup"><span data-stu-id="1d367-306">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="1d367-307">例如，如果单个项目包含以下两种运行时指令文件，DataClasses.dll 的序列化策略将设置为 `Required Public` 和 `All`。</span><span class="sxs-lookup"><span data-stu-id="1d367-307">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="1d367-308">在此情况下，序列化策略将被处理为 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="1d367-308">In this case, the serialization policy would be resolved as `Required All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"/>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="All" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

<span data-ttu-id="1d367-309">但如果单个运行时指令文件中的两个指令尝试设置同一程序元素的同一策略类型，则 XML Scheme Definition 工具将显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="1d367-309">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="1d367-310">如果子元素和父元素应用的是同一策略类型</span><span class="sxs-lookup"><span data-stu-id="1d367-310">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="1d367-311">子元素将替代其父元素，包括 `Excluded` 设置。</span><span class="sxs-lookup"><span data-stu-id="1d367-311">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="1d367-312">你想要指定 `Auto` 的主要原因就是要执行替代操作。</span><span class="sxs-lookup"><span data-stu-id="1d367-312">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="1d367-313">在以下示例中，`DataClasses` 中所有内容（`DataClasses.ViewModels` 中不含这些内容）的序列化策略设置将为 `Required Public`，而 `DataClasses` 和 `DataClasses.ViewModels` 中所有内容的序列化策略设置将为 `All`。</span><span class="sxs-lookup"><span data-stu-id="1d367-313">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="1d367-314">如果开放式泛型元素和已实例化的元素应用的是同一策略类型</span><span class="sxs-lookup"><span data-stu-id="1d367-314">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="1d367-315">在以下示例中，只有当引擎出于其他原因提供 `Dictionary<int,int>` 策略时（亦可为默认行为），才会为 `Browse` 分配 `Browse` 策略；<xref:System.Collections.Generic.Dictionary%602> 的所有其他实例化将具有所有可浏览的成员。</span><span class="sxs-lookup"><span data-stu-id="1d367-315">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
      <Namespace Name="DataClasses.Generics" />
      <Type Name="Dictionary" Browse="All" />
      <TypeInstantiation Name="Dictionary"
                         Arguments="System.Int32,System.Int32" Browse="Auto" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="how-policy-is-inferred"></a><span data-ttu-id="1d367-316">如何推断出策略</span><span class="sxs-lookup"><span data-stu-id="1d367-316">How policy is inferred</span></span>

<span data-ttu-id="1d367-317">每个策略类型均具有一组不同的规则，这些规则决定了该策略类型的存在如何对其他构造造成影响。</span><span class="sxs-lookup"><span data-stu-id="1d367-317">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="1d367-318">“浏览”策略的效果</span><span class="sxs-lookup"><span data-stu-id="1d367-318">The effect of Browse policy</span></span>

<span data-ttu-id="1d367-319">将 `Browse` 策略应用于类型涉及下列策略更改：</span><span class="sxs-lookup"><span data-stu-id="1d367-319">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="1d367-320">类型的基类型标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-320">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-321">如果类型为实例化泛型类型，则该类型的未实例化版本将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-322">如果类型为委托类型，则针对该类型的 `Invoke` 方法将标有 `Dynamic` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-322">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="1d367-323">每个类型接口将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-323">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-324">应用于类型的每个属性类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-324">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-325">如果类型为泛型，则每个约束类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-325">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-326">如果类型为泛型，则实例化该类型所采用的类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-326">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="1d367-327">将 `Browse` 策略应用于方法涉及下列策略更改：</span><span class="sxs-lookup"><span data-stu-id="1d367-327">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="1d367-328">方法的每个参数类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-328">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-329">方法的返回类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-329">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-330">方法的包含类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-330">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-331">如果方法为实例化泛型方法，则未实例化泛型方法将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-331">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-332">应用于方法的每个属性类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-332">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-333">如果方法为泛型，则每个约束类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-333">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-334">如果方法为泛型，则实例化该方法所采用的类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-334">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="1d367-335">将 `Browse` 策略应用于字段涉及下列策略更改：</span><span class="sxs-lookup"><span data-stu-id="1d367-335">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="1d367-336">应用于字段的每个属性类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-336">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-337">字段类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-337">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-338">字段从属的类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-338">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="1d367-339">“动态”策略的效果</span><span class="sxs-lookup"><span data-stu-id="1d367-339">The effect of Dynamic policy</span></span>

<span data-ttu-id="1d367-340">将 `Dynamic` 策略应用于类型涉及下列策略更改：</span><span class="sxs-lookup"><span data-stu-id="1d367-340">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="1d367-341">类型的基类型标有 `Dynamic` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-341">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="1d367-342">如果类型为实例化泛型类型，则该类型的未实例化版本将标有 `Dynamic` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-342">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="1d367-343">如果类型为委托类型，则针对该类型的 `Invoke` 方法将标有 `Dynamic` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-343">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="1d367-344">每个类型接口将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-344">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-345">应用于类型的每个属性类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-345">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-346">如果类型为泛型，则每个约束类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-346">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-347">如果类型为泛型，则实例化该类型所采用的类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-347">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="1d367-348">将 `Dynamic` 策略应用于方法涉及下列策略更改：</span><span class="sxs-lookup"><span data-stu-id="1d367-348">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="1d367-349">方法的每个参数类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-349">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-350">方法的返回类型将标有 `Dynamic` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-350">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="1d367-351">方法的包含类型将标有 `Dynamic` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-351">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="1d367-352">如果方法为实例化泛型方法，则未实例化泛型方法将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-352">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-353">应用于方法的每个属性类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-353">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-354">如果方法为泛型，则每个约束类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-354">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-355">如果方法为泛型，则实例化该方法所采用的类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-355">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-356">`MethodInfo.Invoke` 可调用方法，并且可通过 <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> 进行委托创建。</span><span class="sxs-lookup"><span data-stu-id="1d367-356">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1d367-357">将 `Dynamic` 策略应用于字段涉及下列策略更改：</span><span class="sxs-lookup"><span data-stu-id="1d367-357">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="1d367-358">应用于字段的每个属性类型将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-358">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-359">字段类型将标有 `Dynamic` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-359">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="1d367-360">字段从属的类型将标有 `Dynamic` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-360">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="1d367-361">“激活”策略的效果</span><span class="sxs-lookup"><span data-stu-id="1d367-361">The effect of Activation policy</span></span>

<span data-ttu-id="1d367-362">将“激活”策略应用于类型涉及下列策略更改：</span><span class="sxs-lookup"><span data-stu-id="1d367-362">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="1d367-363">如果类型为实例化泛型类型，则该类型的未实例化版本将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-363">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-364">如果类型为委托类型，则针对该类型的 `Invoke` 方法将标有 `Dynamic` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-364">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="1d367-365">类型的构造函数标有 `Activation` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-365">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="1d367-366">将 `Activation` 策略应用于方法涉及下列策略更改：</span><span class="sxs-lookup"><span data-stu-id="1d367-366">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="1d367-367"><xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> 和 <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 方法可调用构造函数。</span><span class="sxs-lookup"><span data-stu-id="1d367-367">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="1d367-368">对于方法而言，`Activation` 策略仅会影响构造函数。</span><span class="sxs-lookup"><span data-stu-id="1d367-368">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="1d367-369">将 `Activation` 策略应用于字段未产生任何效果。</span><span class="sxs-lookup"><span data-stu-id="1d367-369">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="1d367-370">“序列化”策略的效果</span><span class="sxs-lookup"><span data-stu-id="1d367-370">The effect of Serialize policy</span></span>

<span data-ttu-id="1d367-371">`Serialize` 策略可启用基于反射的常用序列化程序。</span><span class="sxs-lookup"><span data-stu-id="1d367-371">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="1d367-372">但由于 Microsoft 不清楚非 Microsoft 序列化程序的确切反射访问模式，该策略可能无法完全生效。</span><span class="sxs-lookup"><span data-stu-id="1d367-372">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="1d367-373">将 `Serialize` 策略应用于类型涉及下列策略更改：</span><span class="sxs-lookup"><span data-stu-id="1d367-373">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="1d367-374">类型的基类型标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-374">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="1d367-375">如果类型为实例化泛型类型，则该类型的未实例化版本将标有 `Browse` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-375">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="1d367-376">如果类型为委托类型，则针对该类型的 `Invoke` 方法将标有 `Dynamic` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-376">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="1d367-377">如果类型为枚举，则类型数组将标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-377">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="1d367-378">如果类型实施 <xref:System.Collections.Generic.IEnumerable%601>，则 `T` 将标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-378">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="1d367-379">如果类型为 <xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.Generic.IList%601>、<xref:System.Collections.Generic.ICollection%601>、<xref:System.Collections.Generic.IReadOnlyCollection%601>或 <xref:System.Collections.Generic.IReadOnlyList%601>，则 `T[]` 和 <xref:System.Collections.Generic.List%601> 将标有 `Serialize` 策略，但接口类型的所有成员均未标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-379">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="1d367-380">如果类型为 <xref:System.Collections.Generic.List%601>，则该类型的所有成员均未标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-380">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="1d367-381">如果类型为 <xref:System.Collections.Generic.IDictionary%602>，则 <xref:System.Collections.Generic.Dictionary%602> 将标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-381">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="1d367-382">但该类型的所有成员均未标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-382">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="1d367-383">如果类型为 <xref:System.Collections.Generic.Dictionary%602>，则该类型的所有成员均未标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-383">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="1d367-384">如果类型实施 <xref:System.Collections.Generic.IDictionary%602>，则 `TKey` 和 `TValue` 均标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-384">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="1d367-385">每个构造函数、属性访问器和字段均标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-385">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="1d367-386">将 `Serialize` 策略应用于方法涉及下列策略更改：</span><span class="sxs-lookup"><span data-stu-id="1d367-386">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="1d367-387">包含类型将标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-387">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="1d367-388">方法的返回类型将标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-388">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="1d367-389">将 `Serialize` 策略应用于字段涉及下列策略更改：</span><span class="sxs-lookup"><span data-stu-id="1d367-389">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="1d367-390">包含类型将标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-390">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="1d367-391">字段类型将标有 `Serialize` 策略。</span><span class="sxs-lookup"><span data-stu-id="1d367-391">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="1d367-392">XmlSerializer、DataContractSerializer 和 DataContractJsonSerializer 策略的影响</span><span class="sxs-lookup"><span data-stu-id="1d367-392">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="1d367-393">与用于 `Serialize` 基于反射的序列化程序的策略不同， <xref:System.Xml.Serialization.XmlSerializer> 、 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 策略用于启用一组对 .NET Native 工具链已知的序列化程序。</span><span class="sxs-lookup"><span data-stu-id="1d367-393">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="1d367-394">这些序列化程序并非通过反射实施，但却按照与确定可反射类型的设置类似的方式来确定可在运行时实现序列化的类型的设置。</span><span class="sxs-lookup"><span data-stu-id="1d367-394">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="1d367-395">将这些策略之一应用于类型，该类型便可借助匹配的序列化程序实现序列化。</span><span class="sxs-lookup"><span data-stu-id="1d367-395">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="1d367-396">同样，任何序列化引擎可静态确定为需要序列化的类型也可实现序列化。</span><span class="sxs-lookup"><span data-stu-id="1d367-396">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="1d367-397">这些策略对方法或字段无效。</span><span class="sxs-lookup"><span data-stu-id="1d367-397">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="1d367-398">有关详细信息，请参阅[将 Windows 应用商店应用迁移到 .NET Native](migrating-your-windows-store-app-to-net-native.md) 中的“序列化程序的差异”一节。</span><span class="sxs-lookup"><span data-stu-id="1d367-398">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d367-399">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d367-399">See also</span></span>

- [<span data-ttu-id="1d367-400">运行时指令元素</span><span class="sxs-lookup"><span data-stu-id="1d367-400">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="1d367-401">反射和 .NET Native</span><span class="sxs-lookup"><span data-stu-id="1d367-401">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
