---
title: AttributeUsage
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 677d49aba38801f2adf42cc745983af30b3eddc5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400727"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="d294d-102">AttributeUsage （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d294d-102">AttributeUsage (Visual Basic)</span></span>

<span data-ttu-id="d294d-103">确定如何使用自定义特性类。</span><span class="sxs-lookup"><span data-stu-id="d294d-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="d294d-104">`AttributeUsage` 是一个特性，可应用于自定义特性定义，以控制如何应用新特性。</span><span class="sxs-lookup"><span data-stu-id="d294d-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="d294d-105">在显式应用时的默认设置如下：</span><span class="sxs-lookup"><span data-stu-id="d294d-105">The default settings look like this when applied explicitly:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="d294d-106">在此示例中，`NewAttribute` 类可应用于任何特性的代码实体，但只能对每个实体应用一次。</span><span class="sxs-lookup"><span data-stu-id="d294d-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="d294d-107">当应用于基类时，它由派生类继承。</span><span class="sxs-lookup"><span data-stu-id="d294d-107">It is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="d294d-108">`AllowMultiple` 和 `Inherited` 参数是可选的，因而此代码具有相同的效果：</span><span class="sxs-lookup"><span data-stu-id="d294d-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="d294d-109">第一个 `AttributeUsage` 参数必须是 <xref:System.AttributeTargets> 枚举的一个或多个元素。</span><span class="sxs-lookup"><span data-stu-id="d294d-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="d294d-110">可将多个目标类型与 OR 运算符链接在一起，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d294d-110">Multiple target types can be linked together with the OR operator, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

<span data-ttu-id="d294d-111">如果 `AllowMultiple` 参数设置为 `true`，则结果特性可多次应用于单个实体，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d294d-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

<span data-ttu-id="d294d-112">在本例中，`MultiUseAttr` 可重复应用，因为 `AllowMultiple` 设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="d294d-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="d294d-113">所显示的两种用于应用多个特性的格式均有效。</span><span class="sxs-lookup"><span data-stu-id="d294d-113">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="d294d-114">如果 `Inherited` 设置为 `false`，那么特性不会由派生自已特性化的类的类继承。</span><span class="sxs-lookup"><span data-stu-id="d294d-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="d294d-115">例如：</span><span class="sxs-lookup"><span data-stu-id="d294d-115">For example:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>
Class Attr1
    Inherits Attribute
End Class

<Attr1()>
Class BClass

End Class

Class DClass
    Inherits BClass
End Class
```

<span data-ttu-id="d294d-116">在本例中，`Attr1` 不会通过继承应用于 `DClass`。</span><span class="sxs-lookup"><span data-stu-id="d294d-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="d294d-117">备注</span><span class="sxs-lookup"><span data-stu-id="d294d-117">Remarks</span></span>

<span data-ttu-id="d294d-118">`AttributeUsage` 特性是单次使用的特性 -- 它无法应用于同一个类超过一次。</span><span class="sxs-lookup"><span data-stu-id="d294d-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="d294d-119">`AttributeUsage` 是 <xref:System.AttributeUsageAttribute> 的别名。</span><span class="sxs-lookup"><span data-stu-id="d294d-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="d294d-120">有关详细信息，请参阅[使用反射访问特性 (Visual Basic)](accessing-attributes-by-using-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="d294d-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="d294d-121">示例</span><span class="sxs-lookup"><span data-stu-id="d294d-121">Example</span></span>

<span data-ttu-id="d294d-122">以下示例演示 `Inherited` 和 `AllowMultiple` 参数对 `AttributeUsage` 特性的影响，以及如何枚举应用于类的自定义特性。</span><span class="sxs-lookup"><span data-stu-id="d294d-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

```vb
' Create some custom attributes:
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>
Class A1
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class)>
Class A2
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>
Class A3
    Inherits System.Attribute
End Class

' Apply custom attributes to classes:
<A1(), A2()>
Class BaseClass

End Class

<A3(), A3()>
Class DerivedClass
    Inherits BaseClass
End Class

Public Class TestAttributeUsage
    Sub Main()
        Dim b As New BaseClass
        Dim d As New DerivedClass
        ' Display custom attributes for each class.
        Console.WriteLine("Attributes on Base Class:")
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)

        For Each attr In attrs
            Console.WriteLine(attr)
        Next

        Console.WriteLine("Attributes on Derived Class:")
        attrs = d.GetType().GetCustomAttributes(True)
        For Each attr In attrs
            Console.WriteLine(attr)
        Next
    End Sub
End Class
```

## <a name="sample-output"></a><span data-ttu-id="d294d-123">示例输出</span><span class="sxs-lookup"><span data-stu-id="d294d-123">Sample Output</span></span>

```console
Attributes on Base Class:
A1
A2
Attributes on Derived Class:
A3
A3
A2
```

## <a name="see-also"></a><span data-ttu-id="d294d-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d294d-124">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="d294d-125">Visual Basic 编程指南</span><span class="sxs-lookup"><span data-stu-id="d294d-125">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="d294d-126">特性</span><span class="sxs-lookup"><span data-stu-id="d294d-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="d294d-127">反射 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d294d-127">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="d294d-128">特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d294d-128">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="d294d-129">创建自定义特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d294d-129">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="d294d-130">使用反射访问特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d294d-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
